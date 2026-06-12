---
title: "Intel i915 VGA problem"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by icefist on 2008-12-03
Hello,
just around a week on ubuntu, researched for days but couldnt find a solution.

My resolution is ok, but even if I try to run Chess in 3D mode they crash without any message.

Here is my xorg.conf

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2704 1050
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Thanks

pS. also in the Multimedia Systems Selector in video section:

Default output
Plugin: Autodetect
Device:Unsupported

---

### Post by Thelasko on 2008-12-03
First, let me give you some background on xorg and the intel driver.

Back in the day, your display was configured using the xorg.conf file.  The xorg.conf file is still used, but is mostly obsolete.  I don't think your problem exists with xorg.conf.

You may have read some documents about the the 915resolution issues, and i810 drivers.  Those issues are all resolved by the current "intel" driver.

_Your issue and resolution:_

I don't think your driver is misconfigued.  The graphics card you have isn't very powerful and likely isn't capable of running Chess in 3D mode.  You can try making the graphics settings in the game as low as possible and see if that helps.

Did you try running the program from the terminal and read the output?

---

### Post by icefist on 2008-12-04
I cant switch it back to 2D mode because it crashes..

Running from terminal:

alex@alex-laptop:/usr/games$ glchess
Failed to load GGZ config
Using OpenGL:
VENDOR=Mesa Project
RENDERER=Software Rasterizer
VERSION=2.1 Mesa 7.2
EXTENSIONS=GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_fog_coord GL_EXT_gpu_program_parameters GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_shared_texture_palette GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_vertex_array GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ATI_blend_equation_separate GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_ATI_fragment_shader GL_ATI_separate_stencil GL_IBM_multimode_draw_arrays GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_program_debug GL_MESA_resize_buffers GL_MESA_texture_array GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_fragment_program GL_NV_light_max_exponent GL_NV_point_sprite GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGI_texture_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SGIX_shadow_ambient GL_SUN_multi_draw_arrays
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/glchess/gtkui/chessview.py", line 169, in __expose
    self.view.feedback.renderGL()
  File "/var/lib/python-support/python2.5/glchess/display.py", line 477, in renderGL
    self.scene.controller.render()
  File "/var/lib/python-support/python2.5/glchess/scene/opengl/opengl.py", line 341, in render
    self.drawPieces()
  File "/var/lib/python-support/python2.5/glchess/scene/opengl/opengl.py", line 864, in drawPieces
    piece.draw()
  File "/var/lib/python-support/python2.5/glchess/scene/opengl/opengl.py", line 109, in draw
    self.chessSet.drawPiece(self.name, state, self.scene)
  File "/var/lib/python-support/python2.5/glchess/scene/opengl/new_models.py", line 110, in drawPiece
    if glGetBoolean(GL_TEXTURE_2D):
  File "/usr/lib/python2.5/site-packages/PyOpenGL-3.0.0b6-py2.5.egg/OpenGL/wrapper.py", line 1631, in __call__
    return self.finalise()( *args, **named )
  File "/usr/lib/python2.5/site-packages/PyOpenGL-3.0.0b6-py2.5.egg/OpenGL/wrapper.py", line 683, in wrapperCall
    converter( pyArgs, index, self )
  File "/usr/lib/python2.5/site-packages/PyOpenGL-3.0.0b6-py2.5.egg/OpenGL/converters.py", line 195, in __call__
    return self.arrayType.zeros( self.getSize(pyArgs) )
  File "/usr/lib/python2.5/site-packages/PyOpenGL-3.0.0b6-py2.5.egg/OpenGL/arrays/arraydatatype.py", line 98, in zeros
    return cls.returnHandler().zeros( dims, typeCode or cls.typeConstant )
  File "/usr/lib/python2.5/site-packages/PyOpenGL-3.0.0b6-py2.5.egg/OpenGL/arrays/nones.py", line 32, in zeros
    raise TypeError( """Can't create NULL pointer filled with values""" )
TypeError: ("Can't create NULL pointer filled with values", 'Failure in cConverter <OpenGL.converters.SizedOutput object at 0x964572c>', [GL_TEXTURE_2D], 1, <OpenGL.wrapper.glGetIntegerv object at 0x965590c>)

sh: bug-buddy: not found
alex@alex-laptop:/usr/games$ glchess
Failed to load GGZ config
Using OpenGL:
VENDOR=Mesa Project
RENDERER=Software Rasterizer
VERSION=2.1 Mesa 7.2
EXTENSIONS=GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_fog_coord GL_EXT_gpu_program_parameters GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_shared_texture_palette GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_vertex_array GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ATI_blend_equation_separate GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_ATI_fragment_shader GL_ATI_separate_stencil GL_IBM_multimode_draw_arrays GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_program_debug GL_MESA_resize_buffers GL_MESA_texture_array GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_fragment_program GL_NV_light_max_exponent GL_NV_point_sprite GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGI_texture_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SGIX_shadow_ambient GL_SUN_multi_draw_arrays
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/glchess/gtkui/chessview.py", line 169, in __expose
    self.view.feedback.renderGL()
  File "/var/lib/python-support/python2.5/glchess/display.py", line 477, in renderGL
    self.scene.controller.render()
  File "/var/lib/python-support/python2.5/glchess/scene/opengl/opengl.py", line 341, in render
    self.drawPieces()
  File "/var/lib/python-support/python2.5/glchess/scene/opengl/opengl.py", line 864, in drawPieces
    piece.draw()
  File "/var/lib/python-support/python2.5/glchess/scene/opengl/opengl.py", line 109, in draw
    self.chessSet.drawPiece(self.name, state, self.scene)
  File "/var/lib/python-support/python2.5/glchess/scene/opengl/new_models.py", line 110, in drawPiece
    if glGetBoolean(GL_TEXTURE_2D):
  File "/usr/lib/python2.5/site-packages/PyOpenGL-3.0.0b6-py2.5.egg/OpenGL/wrapper.py", line 1631, in __call__
    return self.finalise()( *args, **named )
  File "/usr/lib/python2.5/site-packages/PyOpenGL-3.0.0b6-py2.5.egg/OpenGL/wrapper.py", line 683, in wrapperCall
    converter( pyArgs, index, self )
  File "/usr/lib/python2.5/site-packages/PyOpenGL-3.0.0b6-py2.5.egg/OpenGL/converters.py", line 195, in __call__
    return self.arrayType.zeros( self.getSize(pyArgs) )
  File "/usr/lib/python2.5/site-packages/PyOpenGL-3.0.0b6-py2.5.egg/OpenGL/arrays/arraydatatype.py", line 98, in zeros
    return cls.returnHandler().zeros( dims, typeCode or cls.typeConstant )
  File "/usr/lib/python2.5/site-packages/PyOpenGL-3.0.0b6-py2.5.egg/OpenGL/arrays/nones.py", line 32, in zeros
    raise TypeError( """Can't create NULL pointer filled with values""" )
TypeError: ("Can't create NULL pointer filled with values", 'Failure in cConverter <OpenGL.converters.SizedOutput object at 0xa2a672c>', [GL_TEXTURE_2D], 1, <OpenGL.wrapper.glGetIntegerv object at 0xa2b690c>)

sh: bug-buddy: not found

---

### Post by Thelasko on 2008-12-04
Are you using 8.04 (hardy) or 8.10 (intrepid)?

P.S. Do you have the "python-opengl" package installed?  I think you need this for 3d, but it's not installed by default.

---

### Post by icefist on 2008-12-09
> **Thelasko said:**
> Are you using 8.04 (hardy) or 8.10 (intrepid)?

P.S. Do you have the "python-opengl" package installed?  I think you need this for 3d, but it's not installed by default.


8.10

I had installed all the packages, because it was giving an error msg, after installation when I try to run chess no msg, but they crash without opening.

---

### Post by Thelasko on 2008-12-09
> **icefist said:**
> 8.10

I had installed all the packages, because it was giving an error msg, after installation when I try to run chess no msg, but they crash without opening.

That's weird that it crashes without giving an error message.  What we can try next is uninstalling the program and removing all of it's saved data.  Unfortunately, you will lose any saved games/data (only those that are used by the games package) in doing so.  We will do this with the "purge" commmand.

In the terminal enter:
```
sudo apt-get -y purge gnome-games
```

Then reinstall it:
```
sudo apt-get install gnome-games
```

See if that fixes it.

---

### Post by migolo on 2009-04-22
Hi there Im sorry for the date of this post but... I have the same problem... did you solve it?...

Thanks

Migolo

---

