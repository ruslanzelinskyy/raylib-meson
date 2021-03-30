project('raylib', 'c',
	version : '2.0.1-alpha',
	license: 'Zlib'
)

add_project_arguments('-DPLATFORM_' + get_option('raylib_platform'),
	language: 'c'
)

glfw_proj = subproject('glfw')
glfw_dep = glfw_proj.get_variable('glfw_dep')
glfw_dependencies = glfw_proj.get_variable('dependencies')

raylib_dependencies = [glfw_dep, glfw_dependencies]
raylib_inc_dir = include_directories('raylib/src', 'raylib/src/external/glfw/deps')

raylib_lib = static_library('raylib', raylib_inc_dir,
	dependencies: raylib_dependencies,
	include_directories: raylib_inc_dir
)

raylib_dep = declare_dependency(
	include_directories: raylib_inc_dir,
	link_with: raylib_lib
)

if get_option('raylib_build_examples')
	examples_deps = [raylib_dep]
	executable('core_basic_window', 'raylib/examples/core/core_basic_window.c', dependencies: examples_deps)
endif
