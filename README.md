# bazel-library

This is a bazel-library repo for [PublicCourse](https://github.com/ponyai/PublicCourse).

To build with bazel 2.2.0, you have to fix some issues.

## fix 1

Add three build parameters in //.bazelrc

```
build --crosstool_top=//common/toolchain:default
+ build --incompatible_new_actions_api=false
+ build --incompatible_disable_deprecated_attr_params=false
+ build --incompatible_use_python_toolchains=false
build --python_top=@python3
```
## fix 2

Modify library download URL in //WORKSPACE

```python
# eigen
pony_http_archive(
    name = "eigen",
    build_file = "utils/bazel/eigen.BUILD",
    sha256 = "39c6dccfe67f11855832a92dc59f559d494bd57b4feaac69dcb5f275363ae8a9",
    strip_prefix = "eigen",
    urls = ["https://raw.githubusercontent.com/zhuf21/bazel-library/main/eigen-3.3.7.zip"],
)

# GLM
pony_http_archive(
    name = "glm",
    build_file = "utils/bazel/glm.BUILD",
    sha256 = "9f9f520ec7fb8c20c69d6b398ed928a2448c6a3245cbedb8631a56a987c38660",
    strip_prefix = "glm",
    urls = [
        "https://raw.githubusercontent.com/zhuf21/bazel-library/main/glm-0.9.8.5.zip",
    ],
)
```
