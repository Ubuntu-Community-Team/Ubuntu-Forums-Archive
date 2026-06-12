---
title: "Those Funny Funguloids"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by nebu on 2009-02-08
I am using Ubuntu 8.10 64bit edition...... ho do i install those funny funguloids on my computer...... 


whenever i install it..... synaptic gives me an error saying......
> 
funguloids:
 Depends: ogre-plugins-cgprogrammanager  but it is not installable



how do i get around this...???...

---

### Post by Perfect Storm on 2009-02-08
It's a bit old, but see if it works (64-bit only);

---

### Post by nebu on 2009-02-08
when i run it.....

i get this 
```

Creating resource group General
Creating resource group Internal
Creating resource group Autodetect
SceneManagerFactory for type 'DefaultSceneManager' registered.
Registering ResourceManager for type Material
Registering ResourceManager for type Mesh
Registering ResourceManager for type Skeleton
MovableObjectFactory for type 'ParticleSystem' registered.
OverlayElementFactory for type Panel registered.
OverlayElementFactory for type BorderPanel registered.
OverlayElementFactory for type TextArea registered.
Registering ResourceManager for type Font
ArchiveFactory for archive type FileSystem registered.
ArchiveFactory for archive type Zip registered.
FreeImage version: 3.10.0
This program uses FreeImage, a free, open source image library supporting all common bitmap formats. See http://freeimage.sourceforge.net for details
Supported formats: bmp,ico,jpg,jif,jpeg,jpe,jng,koa,iff,lbm,mng,pbm,pbm,pcd,pcx,pgm,pgm,png,ppm,ppm,ras,tga,targa,tif,tiff,wap,wbmp,wbm,psd,cut,xbm,xpm,gif,hdr,g3,sgi,exr,j2k,j2c,jp2
DDS codec registering
Registering ResourceManager for type HighLevelGpuProgram
Registering ResourceManager for type Compositor
MovableObjectFactory for type 'Entity' registered.
MovableObjectFactory for type 'Light' registered.
MovableObjectFactory for type 'BillboardSet' registered.
MovableObjectFactory for type 'ManualObject' registered.
MovableObjectFactory for type 'BillboardChain' registered.
MovableObjectFactory for type 'RibbonTrail' registered.
Loading library /usr/lib/OGRE/RenderSystem_GL.so
Installing plugin: GL RenderSystem
OpenGL Rendering Subsystem created.
Plugin successfully installed
Loading library /usr/lib/OGRE/Plugin_ParticleFX.so
Installing plugin: ParticleFX
Particle Emitter Type 'Point' registered
Particle Emitter Type 'Box' registered
Particle Emitter Type 'Ellipsoid' registered
Particle Emitter Type 'Cylinder' registered
Particle Emitter Type 'Ring' registered
Particle Emitter Type 'HollowEllipsoid' registered
Particle Affector Type 'LinearForce' registered
Particle Affector Type 'ColourFader' registered
Particle Affector Type 'ColourFader2' registered
Particle Affector Type 'ColourImage' registered
Particle Affector Type 'ColourInterpolator' registered
Particle Affector Type 'Scaler' registered
Particle Affector Type 'Rotator' registered
Particle Affector Type 'DirectionRandomiser' registered
Particle Affector Type 'DeflectorPlane' registered
Plugin successfully installed
Loading library /usr/lib/OGRE/Plugin_BSPSceneManager.so
Installing plugin: BSP Scene Manager
Plugin successfully installed
Loading library /usr/lib/OGRE/Plugin_OctreeSceneManager.so
Installing plugin: Octree & Terrain Scene Manager
Plugin successfully installed
Loading library /usr/lib/OGRE/Plugin_EXRCodec.so
EXRCodec initialised
*-*-* OGRE Initialising
*-*-* Version 1.4.9 (Eihort)
ArchiveFactory for archive type MPK registered.
Creating resource group Bootstrap
Added resource location '/usr/share/games/funguloids/bootstrap.mpk' of type 'MPK' to resource group 'Bootstrap'
Added resource location '/usr/share/games/funguloids/music' of type 'FileSystem' to resource group 'General'
Added resource location '/usr/share/games/funguloids/icon' of type 'FileSystem' to resource group 'General'
Added resource location '/usr/share/games/funguloids/funguloids.mpk' of type 'MPK' to resource group 'General'
CPU Identifier & Features
-------------------------
 *   CPU ID: Unknown
-------------------------
******************************
*** Starting GLX Subsystem ***
******************************
GLRenderSystem::createRenderWindow "Those Funny Funguloids!", 1280x800 fullscreen  miscParams: FSAA=0 title=Those Funny Funguloids! 
GLXWindow::create
Parsing miscParams
GLXWindow::create -- Entering full screen mode
GLXWindow::create -- Best visual is 33
GL_VERSION = 1.4 Mesa 7.2
GL_VENDOR = Tungsten Graphics, Inc
GL_RENDERER = Mesa DRI Intel(R) 965GM 20061102
GL_EXTENSIONS = GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_packed_pixels GL_ATI_draw_buffers GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_NV_blend_square GL_NV_light_max_exponent GL_NV_point_sprite GL_NV_texgen_reflection GL_NV_texture_rectangle GL_NV_vertex_program GL_NV_vertex_program1_1 GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SUN_multi_draw_arrays 
***************************
*** GL Renderer Started ***
***************************
Registering ResourceManager for type GpuProgram
GL: Using framebuffer copy for rendering to textures (worst)
GL: Warning: RenderTexture size is restricted to size of framebuffer. If you are on Linux, consider using GLX instead of SDL.
RenderSystem capabilities
-------------------------
 * Hardware generation of mipmaps: yes
 * Texture blending: yes
 * Anisotropic texture filtering: no
 * Dot product texture operation: yes
 * Cube mapping: yes
 * Hardware stencil buffer: yes
   - Stencil depth: 8
   - Two sided stencil support: no
   - Wrap stencil values: yes
 * Hardware vertex / index buffers: no
 * Vertex programs: yes
   - Max vertex program version: arbvp1
 * Fragment programs: yes
   - Max fragment program version: arbfp1
 * Texture Compression: yes
   - DXT: no
   - VTC: no
 * Scissor Rectangle: yes
 * Hardware Occlusion Query: no
 * User clip planes: yes
 * VET_UBYTE4 vertex element type: yes
 * Infinite far plane projection: yes
 * Hardware render-to-texture: no
 * Floating point textures: no
 * Non-power-of-two textures: yes
 * Volume textures: yes
 * Multiple Render Targets: 1
 * Point Sprites: yes
 * Extended point parameters: yes
 * Max Point Size: 255
 * Vertex texture fetch: no
Registering ResourceManager for type Texture
ResourceBackgroundQueue - threading disabled
Particle Renderer Type 'billboard' registered
SceneManagerFactory for type 'BspSceneManager' registered.
Registering ResourceManager for type BspLevel
SceneManagerFactory for type 'OctreeSceneManager' registered.
SceneManagerFactory for type 'TerrainSceneManager' registered.
Creating viewport on target 'Those Funny Funguloids!', rendering from camera 'MainCam', relative dimensions L: 0.00 T: 0.00 W: 1.00 H: 1.00 ZOrder: 0
Parsing scripts for resource group Autodetect
Finished parsing scripts for resource group Autodetect
Parsing scripts for resource group Bootstrap
Parsing script OgreCore.material
Parsing script Vera.fontdef
Parsing script OgreDebugPanel.overlay
Texture: Border_Center.png: Loading 1 faces(PF_A8R8G8B8,256x128x1) with 5 hardware generated mipmaps from Image. Internal format is PF_A8R8G8B8,256x128x1.
Texture: Border.png: Loading 1 faces(PF_A8R8G8B8,256x256x1) with 5 hardware generated mipmaps from Image. Internal format is PF_A8R8G8B8,256x256x1.
Texture: Border_Break.png: Loading 1 faces(PF_A8R8G8B8,32x32x1) with 5 hardware generated mipmaps from Image. Internal format is PF_A8R8G8B8,32x32x1.
Font VeraBoldusing texture size 512x512
Info: Freetype returned null for character 160 in font VeraBold
Texture: VeraBoldTexture: Loading 1 faces(PF_BYTE_LA,512x512x1) with  hardware generated mipmaps from Image. Internal format is PF_BYTE_LA,512x512x1.
Finished parsing scripts for resource group Bootstrap
Parsing scripts for resource group General
Parsing script Examples.program
Parsing script StdQuad_vp.program
Parsing script BlackAndWhite.material
Parsing script Bloom.material
Parsing script display.material
Parsing script effect.material
Parsing script materials.material
Parsing script particles.material
Parsing script blackandwhite.compositor
Parsing script bloom.compositor
Parsing script menufont.fontdef
Parsing script base.particle
Parsing script blackhole.particle
Parsing script mushroom.particle
Parsing script player.particle
Parsing script whirler.particle
Parsing script wormball.particle
Parsing script display.overlay
Texture: PanelBorder_Center.png: Loading 1 faces(PF_A8R8G8B8,128x128x1) with 5 hardware generated mipmaps from Image. Internal format is PF_A8R8G8B8,128x128x1.
Texture: PanelBorder.png: Loading 1 faces(PF_A8R8G8B8,256x256x1) with 5 hardware generated mipmaps from Image. Internal format is PF_A8R8G8B8,256x256x1.
Font Verausing texture size 512x512
Info: Freetype returned null for character 160 in font Vera
Texture: VeraTexture: Loading 1 faces(PF_BYTE_LA,512x512x1) with  hardware generated mipmaps from Image. Internal format is PF_BYTE_LA,512x512x1.
Font VeraBoldItalicusing texture size 512x512
Info: Freetype returned null for character 160 in font VeraBoldItalic
Texture: VeraBoldItalicTexture: Loading 1 faces(PF_BYTE_LA,512x512x1) with  hardware generated mipmaps from Image. Internal format is PF_BYTE_LA,512x512x1.
Font VeraItalicusing texture size 512x512
Info: Freetype returned null for character 160 in font VeraItalic
Texture: VeraItalicTexture: Loading 1 faces(PF_BYTE_LA,512x512x1) with  hardware generated mipmaps from Image. Internal format is PF_BYTE_LA,512x512x1.
Parsing script effect.overlay
Texture: fieryglow.dds: Loading 1 faces(PF_B8G8R8,512x512x1) with 5 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,512x512x1.
Texture: fieryglow2.jpg: Loading 1 faces(PF_R8G8B8,256x256x1) with 5 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,256x256x1.
Texture: whiteglow.dds: Loading 1 faces(PF_B8G8R8,512x512x1) with 5 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,512x512x1.
Texture: whiteglow2.png: Loading 1 faces(PF_R8G8B8,256x256x1) with 5 hardware generated mipmaps from Image. Internal format is PF_X8R8G8B8,256x256x1.
Parsing script menu.overlay
Texture: menufont.png: Loading 1 faces(PF_A8R8G8B8,1024x1024x1) with  hardware generated mipmaps from Image. Internal format is PF_A8R8G8B8,1024x1024x1.
Texture: logo.dds: Loading 1 faces(PF_A8B8G8R8,512x256x1) with 9 custom mipmaps from Image. Internal format is PF_A8R8G8B8,512x256x1.
*** glibc detected *** funguloids: double free or corruption (!prev): 0x0000000001a07230 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f2edf57e938]
/lib/libc.so.6(cfree+0x76)[0x7f2edf580f86]
/usr/lib/libOgreMain-1.4.9.so(_ZN4Ogre5ImageD1Ev+0x26)[0x7f2ee1500bd6]
/usr/lib/OGRE/RenderSystem_GL.so[0x7f2edc8897f1]
/usr/lib/libOgreMain-1.4.9.so(_ZN4Ogre8Resource4loadEb+0xbd)[0x7f2ee15ef0bd]
/usr/lib/libOgreMain-1.4.9.so(_ZN4Ogre14TextureManager4loadERKSsS2_NS_11TextureTypeEifbNS_11PixelFormatE+0x130)[0x7f2ee1675770]
/usr/lib/libOgreMain-1.4.9.so(_ZNK4Ogre16TextureUnitState12ensureLoadedEm+0x118)[0x7f2ee1676b08]
/usr/lib/libOgreMain-1.4.9.so(_ZN4Ogre16TextureUnitState5_loadEv+0x3b)[0x7f2ee1676cfb]
/usr/lib/libOgreMain-1.4.9.so(_ZN4Ogre4Pass5_loadEv+0x2c)[0x7f2ee15c4d3c]
/usr/lib/libOgreMain-1.4.9.so(_ZN4Ogre9Technique5_loadEv+0x2c)[0x7f2ee166d7cc]
/usr/lib/libOgreMain-1.4.9.so(_ZN4Ogre8Material8loadImplEv+0x3c)[0x7f2ee15266ac]
/usr/lib/libOgreMain-1.4.9.so(_ZN4Ogre8Resource4loadEb+0xbd)[0x7f2ee15ef0bd]
/usr/lib/libOgreMain-1.4.9.so(_ZN4Ogre14OverlayElement15setMaterialNameERKSs+0xdf)[0x7f2ee159b28f]
/usr/lib/libOgreMain-1.4.9.so(_ZN4Ogre15StringInterface12setParameterERKSsS2_+0x1db)[0x7f2ee166772b]
/usr/lib/libOgreMain-1.4.9.so(_ZN4Ogre14OverlayManager18parseElementAttribERKSsPNS_7OverlayEPNS_14OverlayElementE+0x8e)[0x7f2ee15a0b8e]
/usr/lib/libOgreMain-1.4.9.so(_ZN4Ogre14OverlayManager15parseNewElementERNS_9SharedPtrINS_10DataStreamEEERSsS5_bPNS_7OverlayEbSsPNS_16OverlayContainerE+0x1a1)[0x7f2ee15a3891]
/usr/lib/libOgreMain-1.4.9.so(_ZN4Ogre14OverlayManager13parseChildrenERNS_9SharedPtrINS_10DataStreamEEERKSsPNS_7OverlayEbPNS_16OverlayContainerE+0x565)[0x7f2ee15a30f5]
/usr/lib/libOgreMain-1.4.9.so(_ZN4Ogre14OverlayManager11parseScriptERNS_9SharedPtrINS_10DataStreamEEERKSs+0x265)[0x7f2ee15a3c95]
/usr/lib/libOgreMain-1.4.9.so(_ZN4Ogre20ResourceGroupManager25parseResourceGroupScriptsEPNS0_13ResourceGroupE+0x460)[0x7f2ee15f2790]
/usr/lib/libOgreMain-1.4.9.so(_ZN4Ogre20ResourceGroupManager27initialiseAllResourceGroupsEv+0x57)[0x7f2ee15f29e7]
funguloids[0x42d655]
funguloids[0x415764]
/lib/libc.so.6(__libc_start_main+0xe6)[0x7f2edf523466]
funguloids(_ZNSt8ios_base4InitD1Ev+0x39)[0x409229]
======= Memory map: ========
00400000-00456000 r-xp 00000000 08:05 4098020                            /usr/games/funguloids
00655000-00656000 r--p 00055000 08:05 4098020                            /usr/games/funguloids
00656000-00657000 rw-p 00056000 08:05 4098020                            /usr/games/funguloids
00657000-006d8000 rw-p 00657000 00:00 0 
017ef000-01e28000 rw-p 017ef000 00:00 0                                  [heap]
7f2ed4000000-7f2ed4021000 rw-p 7f2ed4000000 00:00 0 
7f2ed4021000-7f2ed8000000 ---p 7f2ed4021000 00:00 0 
7f2eda12e000-7f2eda137000 r-xp 00000000 08:05 3484255                    /usr/lib/libXcursor.so.1.0.2
7f2eda137000-7f2eda337000 ---p 00009000 08:05 3484255                    /usr/lib/libXcursor.so.1.0.2
7f2eda337000-7f2eda338000 rw-p 00009000 08:05 3484255                    /usr/lib/libXcursor.so.1.0.2
7f2eda338000-7f2eda33e000 r-xp 00000000 08:05 3484215                    /usr/lib/libIlmThread.so.6.0.0
7f2eda33e000-7f2eda53d000 ---p 00006000 08:05 3484215                    /usr/lib/libIlmThread.so.6.0.0
7f2eda53d000-7f2eda53e000 r--p 00005000 08:05 3484215                    /usr/lib/libIlmThread.so.6.0.0
7f2eda53e000-7f2eda53f000 rw-p 00006000 08:05 3484215                    /usr/lib/libIlmThread.so.6.0.0
7f2eda53f000-7f2eda55a000 r-xp 00000000 08:05 3484211                    /usr/lib/libIex.so.6.0.0
7f2eda55a000-7f2eda759000 ---p 0001b000 08:05 3484211                    /usr/lib/libIex.so.6.0.0
7f2eda759000-7f2eda75d000 r--p 0001a000 08:05 3484211                    /usr/lib/libIex.so.6.0.0
7f2eda75d000-7f2eda75e000 rw-p 0001e000 08:05 3484211                    /usr/lib/libIex.so.6.0.0
7f2eda75e000-7f2eda7a0000 r-xp 00000000 08:05 3484202                    /usr/lib/libHalf.so.6.0.0
7f2eda7a0000-7f2eda99f000 ---p 00042000 08:05 3484202                    /usr/lib/libHalf.so.6.0.0
7f2eda99f000-7f2eda9a0000 r--p 00041000 08:05 3484202                    /usr/lib/libHalf.so.6.0.0
7f2eda9a0000-7f2eda9a1000 rw-p 00042000 08:05 3484202                    /usr/lib/libHalf.so.6.0.0
7f2eda9a1000-7f2eda9a5000 r-xp 00000000 08:05 3484217                    /usr/lib/libImath.so.6.0.0
7f2eda9a5000-7f2edaba5000 ---p 00004000 08:05 3484217                    /usr/lib/libImath.so.6.0.0
7f2edaba5000-7f2edaba6000 r--p 00004000 08:05 3484217                    /usr/lib/libImath.so.6.0.0
7f2edaba6000-7f2edaba7000 rw-p 00005000 08:05 3484217                    /usr/lib/libImath.so.6.0.0
7f2edaba7000-7f2edac61000 r-xp 00000000 08:05 3484213                    /usr/lib/libIlmImf.so.6.0.0
7f2edac61000-7f2edae60000 ---p 000ba000 08:05 3484213                    /usr/lib/libIlmImf.so.6.0.0
7f2edae60000-7f2edae63000 r--p 000b9000 08:05 3484213                    /usr/lib/libIlmImf.so.6.0.0
7f2edae63000-7f2edae64000 rw-p 000bc000 08:05 3484213                    /usr/lib/libIlmImf.so.6.0.0
7f2edae64000-7f2edae6c000 r-xp 00000000 08:05 4294130                    /usr/lib/OGRE/Plugin_EXRCodec.so
7f2edae6c000-7f2edb06b000 ---p 00008000 08:05 4294130                    /usr/lib/OGRE/Plugin_EXRCodec.so
7f2edb06b000-7f2edb06c000 r--p 00007000 08:05 4294130                    /usr/lib/OGRE/Plugin_EXRCodec.so
7f2edb06c000-7f2edb06d000 rw-p 00008000 08:05 4294130                    /usr/lib/OGRE/Plugin_EXRCodec.so
7f2edb06d000-7f2edb0b9000 r-xp 00000000 08:05 4294131                    /usr/lib/OGRE/Plugin_OctreeSceneManager.so
7f2edb0b9000-7f2edb2b8000 ---p 0004c000 08:05 4294131                    /usr/lib/OGRE/Plugin_OctreeSceneManager.so
7f2edb2b8000-7f2edb2bc000 r--p 0004b000 08:05 4294131                    /usr/lib/OGRE/Plugin_OctreeSceneManager.so
7f2edb2bc000-7f2edb2bd000 rw-p 0004f000 08:05 4294131                    /usr/lib/OGRE/Plugin_OctreeSceneManager.so
7f2edb2bd000-7f2edb2f9000 r-xp 00000000 08:05 4294129                    /usr/lib/OGRE/Plugin_BSPSceneManager.so
7f2edb2f9000-7f2edb4f8000 ---p 0003c000 08:05 4294129                    /usr/lib/OGRE/Plugin_BSPSceneManager.so
7f2edb4f8000-7f2edb4fa000 r--p 0003b000 08:05 4294129                    /usr/lib/OGRE/Plugin_BSPSceneManager.so
7f2edb4fa000-7f2edb4fb000 rw-p 0003d000 08:05 4294129                    /usr/lib/OGRE/Plugin_BSPSceneManager.so
7f2edb4fb000-7f2edb53c000 r-xp 00000000 08:05 4294132                    /usr/lib/OGRE/Plugin_ParticleFX.so
7f2edb53c000-7f2edb73b000 ---p 00041000 08:05 4294132                    /usr/lib/OGRE/Plugin_ParticleFX.so
7f2edb73b000-7f2edb73f000 r--p 00040000 08:05 4294132                    /usr/lib/OGRE/Plugin_ParticleFX.so
7f2edb73f000-7f2edb740000 rw-p 00044000 08:05 4294132                    /usr/lib/OGRE/Plugin_ParticleFX.so
7f2edb740000-7f2edb749000 r-xp 00000000 08:05 3484285                    /usr/lib/libXrender.so.1.3.0
7f2edb749000-7f2edb948000 ---p 00009000 08:05 3484285                    /usr/lib/libXrender.so.1.3.0
7f2edb948000-7f2edb949000 r--p 00008000 08:05 3484285                    /usr/lib/libXrender.so.1.3.0
7f2edb949000-7f2edb94a000 rw-p 00009000 08:05 3484285                    /usr/lib/libXrender.so.1.3.0
7f2edb94a000-7f2edb952000 r-xp 00000000 08:05 3484459                    /usr/lib/libdrm.so.2.3.1
7f2edb952000-7f2edbb51000 ---p 00008000 08:05 3484459                    /usr/lib/libdrm.so.2.3.1
7f2edbb51000-7f2edbb52000 r--p 00007000 08:05 3484459                    /usr/lib/libdrm.so.2.3.1
7f2edbb52000-7f2edbb53000 rw-p 00008000 08:05 3484459                    /usr/lib/libdrm.so.2.3.1
7f2edbb53000-7f2edbb58000 r-xp 00000000 08:05 3484265                    /usr/lib/libXfixes.so.3.1.0
7f2edbb58000-7f2edbd57000 ---p 00005000 08:05 3484265                    /usr/lib/libXfixes.so.3.1.0
7f2edbd57000-7f2edbd58000 rw-p 00004000 08:05 3484265                    /usr/lib/libXfixes.so.3.1.0
7f2edbd58000-7f2edbd5a000 r-xp 00000000 08:05 3484257                    /usr/lib/libXdamage.so.1.1.0
7f2edbd5a000-7f2edbf59000 ---p 00002000 08:05 3484257                    /usr/lib/libXdamage.so.1.1.0
7f2edbf59000-7f2edbf5a000 rw-p 00001000 08:05 3484257                    /usr/lib/libXdamage.so.1.1.0
7f2edbf5a000-7f2edbf5f000 r-xp 00000000 08:05 3484299                    /usr/lib/libXxf86vm.so.1.Aborted


```



and the thing doesnt run!!

---

### Post by Perfect Storm on 2009-02-08
Funguloids won't work with intel cards.

---

