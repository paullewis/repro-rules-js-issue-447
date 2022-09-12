load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "aspect_rules_js",
    sha256 = "db9f446752fe4100320cf8487e8fd476b9af0adf6b99b601bcfd70b289bb0598",
    strip_prefix = "rules_js-1.1.2",
    url = "https://github.com/aspect-build/rules_js/archive/refs/tags/v1.1.2.tar.gz",
)

http_archive(
    name = "aspect_rules_ts",
    sha256 = "b491ff46f8d9167986033552bdd7b39106fac5a1cbc4d5ea44582d3d71557519",
    strip_prefix = "rules_ts-1.0.0-rc2",
    url = "https://github.com/aspect-build/rules_ts/archive/refs/tags/v1.0.0-rc2.tar.gz",
)

http_archive(
    name = "aspect_rules_swc",
    sha256 = "55f84b06e8ea5ddce07077439c2197911acdf42c8416e464a7e77b9cf42f7184",
    strip_prefix = "rules_swc-0.17.0",
    url = "https://github.com/aspect-build/rules_swc/archive/refs/tags/v0.17.0.tar.gz",
)

http_archive(
    name = "aspect_bazel_lib",
    sha256 = "8ea64f13c6db68356355d6a97dced3d149e9cd7ba3ecb4112960586e914e466d",
    strip_prefix = "bazel-lib-1.11.1",
    url = "https://github.com/aspect-build/bazel-lib/archive/refs/tags/v1.11.1.tar.gz",
)

http_archive(
    name = "aspect_rules_esbuild",
    sha256 = "1e365451341ffb2490193292dfd9953f2ca009586c2381cb4dc08d01e48866b7",
    strip_prefix = "rules_esbuild-0.12.0",
    url = "https://github.com/aspect-build/rules_esbuild/archive/refs/tags/v0.12.0.tar.gz",
)

load("@aspect_bazel_lib//lib:repositories.bzl", "aspect_bazel_lib_dependencies")

aspect_bazel_lib_dependencies()

load("@aspect_rules_js//js:repositories.bzl", "rules_js_dependencies")

rules_js_dependencies()

load("@aspect_rules_ts//ts:repositories.bzl", "rules_ts_dependencies", TS_LATEST_VERSION = "LATEST_VERSION")

rules_ts_dependencies(ts_version = TS_LATEST_VERSION)

load("@aspect_rules_esbuild//esbuild:dependencies.bzl", "rules_esbuild_dependencies")

rules_esbuild_dependencies()

load("@rules_nodejs//nodejs:repositories.bzl", "DEFAULT_NODE_VERSION", "nodejs_register_toolchains")

nodejs_register_toolchains(
    name = "nodejs",
    node_version = DEFAULT_NODE_VERSION,
)

load("@aspect_rules_js//npm:npm_import.bzl", "npm_translate_lock")

npm_translate_lock(
    name = "npm",
    pnpm_lock = "//:pnpm-lock.yaml",
    verify_node_modules_ignored = "//:.bazelignore",
    warn_on_unqualified_tarball_url = True,
)

load("@npm//:repositories.bzl", "npm_repositories")

npm_repositories()

load("@aspect_rules_swc//swc:dependencies.bzl", "rules_swc_dependencies")

rules_swc_dependencies()

load("@aspect_rules_swc//swc:repositories.bzl", "swc_register_toolchains", SWC_LATEST_VERSION = "LATEST_VERSION")

swc_register_toolchains(
    name = "swc",
    swc_version = SWC_LATEST_VERSION,
)

load("@aspect_rules_esbuild//esbuild:repositories.bzl", "esbuild_register_toolchains", ESBUILD_LATEST_VERSION = "LATEST_VERSION")

esbuild_register_toolchains(
    name = "esbuild",
    esbuild_version = ESBUILD_LATEST_VERSION,
)
