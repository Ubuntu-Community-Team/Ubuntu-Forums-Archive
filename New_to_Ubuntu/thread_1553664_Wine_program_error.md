---
title: "Wine program error"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by al.adab on 2010-08-15
I have installed two programs through wine - same CD, one installation process (ie, they can't be installed separately). 

One works no problem. The other one - as I open it - gives me an error message (plz see screenshot). 

I found info here and there of similar error messages in relation to a bug, but no solution. 

Any idea?

---

### Post by Vaphell on 2010-08-15
run it from terminal to see some meaningful warnings/errors. Majority of linux apps describe their problems there.

do similar steps but put proper path and executable name.
```

cd ~/.wine/drive_c/Program\ Files/YourApp
wine your_app.exe

```

---

### Post by indra163 on 2011-04-28
i have same problem too...
and my error like this
> wine: cannot find L"C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\mscorsvw.exe"
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly
err:d3d:match_fbo_tex_update FBO status 0
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8A8_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8X8_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:d3d:check_fbo_compat Format WINED3DFMT_B5G6R5_UNORM rtInternal format is not supported as FBO color attachment.
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16_UNORM rtInternal format is not supported as FBO color attachment.
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16B16A16_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:win:EnumDisplayDevicesW ((null),0,0x1eff1f0,0x00000000), stub!
err:d3d:match_fbo_tex_update FBO status 0
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8A8_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8X8_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:d3d:check_fbo_compat Format WINED3DFMT_B5G6R5_UNORM rtInternal format is not supported as FBO color attachment.
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16_UNORM rtInternal format is not supported as FBO color attachment.
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16B16A16_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:win:EnumDisplayDevicesW ((null),0,0x1eff118,0x00000000), stub!
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x40066 0x00000000
err:d3d:match_fbo_tex_update FBO status 0
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8A8_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8X8_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:d3d:check_fbo_compat Format WINED3DFMT_B5G6R5_UNORM rtInternal format is not supported as FBO color attachment.
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16_UNORM rtInternal format is not supported as FBO color attachment.
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16B16A16_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:win:EnumDisplayDevicesW ((null),0,0x1eff838,0x00000000), stub!
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
err:wave:JACK_OpenWaveOutDevice jack server not running?
err:wave:wodOpen JACK_OpenWaveOutDevice(0) failed
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:win:RegisterDeviceNotificationA (hwnd=0x40066, filter=0x1effd14,flags=0x00000000) returns a fake device notification handle!
wine: Unhandled page fault on read access to 0x00000000 at address 0xf173b9 (thread 0009), starting debugger...
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
fixme:dbghelp:elf_search_auxv can't find symbol in module
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00f173b9).
fixme:dbghelp:elf_search_auxv can't find symbol in module
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:00f173b9 ESP:01effc34 EBP:00000001 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:025325ec ECX:0000000c EDX:01effc64
 ESI:025325e0 EDI:01effc58
Stack dump:
0x01effc34:  b4efd1cf 01979ae8 01977838 00000000
0x01effc44:  00000005 00c367c1 00000002 00000000
0x01effc54:  025325ec 00000000 00000002 000000ff
0x01effc64:  00000011 00000053 7bc494f0 7bc494f0
0x01effc74:  01effc80 005ae3ca 0165f060 01effcbc
0x01effc84:  005a9dd7 00000004 005a9dcf b4efd14b
Backtrace:
=>0 0x00f173b9 in pes2010 (+0xb173b9) (0x00000001)
  1 0x00000000 (0x00000000)
0x00f173b9: movl	0x0(%eax),%edx
Modules:
Module	Address			Debug info	Name (120 modules)
PE	  400000- 19f7000	Export          pes2010
PE	65340000-653d2000	Deferred        oleaut32
ELF	7b800000-7b8e7000	Deferred        kernel32<elf>
  \-PE	7b810000-7b8e7000	\               kernel32
ELF	7bc00000-7bcbb000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcbb000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7db18000-7db2d000	Deferred        midimap<elf>
  \-PE	7db20000-7db2d000	\               midimap
ELF	7db2d000-7db53000	Deferred        msacm32<elf>
  \-PE	7db30000-7db53000	\               msacm32
ELF	7db53000-7db6b000	Deferred        msacm32<elf>
  \-PE	7db60000-7db6b000	\               msacm32
ELF	7db6b000-7db86000	Deferred        winejack<elf>
  \-PE	7db70000-7db86000	\               winejack
ELF	7db86000-7db8f000	Deferred        librt.so.1
ELF	7db8f000-7db99000	Deferred        libdrm.so.2
ELF	7db99000-7db9c000	Deferred        libxdamage.so.1
ELF	7db9c000-7dc01000	Deferred        libgl.so.1
ELF	7dc01000-7dc75000	Deferred        libgcrypt.so.11
ELF	7dc75000-7dc85000	Deferred        libtasn1.so.3
ELF	7dc85000-7dd1d000	Deferred        libgnutls.so.26
ELF	7dd1d000-7dd36000	Deferred        libjack.so.0
ELF	7dd66000-7dd99000	Deferred        uxtheme<elf>
  \-PE	7dd70000-7dd99000	\               uxtheme
ELF	7ddc7000-7dde9000	Deferred        mpr<elf>
  \-PE	7ddd0000-7dde9000	\               mpr
ELF	7dde9000-7de4b000	Deferred        wininet<elf>
  \-PE	7ddf0000-7de4b000	\               wininet
ELF	7de4b000-7de85000	Deferred        dinput<elf>
  \-PE	7de50000-7de85000	\               dinput
ELF	7de85000-7de9f000	Deferred        dinput8<elf>
  \-PE	7de90000-7de9f000	\               dinput8
ELF	7de9f000-7df23000	Deferred        crypt32<elf>
  \-PE	7deb0000-7df23000	\               crypt32
ELF	7df23000-7df52000	Deferred        ws2_32<elf>
  \-PE	7df30000-7df52000	\               ws2_32
ELF	7df52000-7df7b000	Deferred        netapi32<elf>
  \-PE	7df60000-7df7b000	\               netapi32
ELF	7df7b000-7dfa6000	Deferred        secur32<elf>
  \-PE	7df80000-7dfa6000	\               secur32
ELF	7dfa6000-7e095000	Deferred        comctl32<elf>
  \-PE	7dfb0000-7e095000	\               comctl32
ELF	7e095000-7e0f8000	Deferred        shlwapi<elf>
  \-PE	7e0a0000-7e0f8000	\               shlwapi
ELF	7e0f8000-7e2bc000	Deferred        shell32<elf>
  \-PE	7e110000-7e2bc000	\               shell32
ELF	7e2bc000-7e2dc000	Deferred        iphlpapi<elf>
  \-PE	7e2c0000-7e2dc000	\               iphlpapi
ELF	7e2dc000-7e319000	Deferred        winmm<elf>
  \-PE	7e2e0000-7e319000	\               winmm
ELF	7e319000-7e361000	Deferred        dsound<elf>
  \-PE	7e320000-7e361000	\               dsound
ELF	7e361000-7e3bd000	Deferred        ddraw<elf>
  \-PE	7e370000-7e3bd000	\               ddraw
ELF	7e3bd000-7e4f2000	Deferred        wined3d<elf>
  \-PE	7e3d0000-7e4f2000	\               wined3d
ELF	7e4f2000-7e526000	Deferred        d3d9<elf>
  \-PE	7e500000-7e526000	\               d3d9
ELF	7e526000-7e52f000	Deferred        libxcursor.so.1
ELF	7e52f000-7e53c000	Deferred        libxi.so.6
ELF	7e53c000-7e541000	Deferred        libxfixes.so.3
ELF	7e541000-7e544000	Deferred        libxcomposite.so.1
ELF	7e544000-7e54b000	Deferred        libxrandr.so.2
ELF	7e54b000-7e554000	Deferred        libxrender.so.1
ELF	7e554000-7e559000	Deferred        libxxf86vm.so.1
ELF	7e559000-7e55c000	Deferred        libxinerama.so.1
ELF	7e55c000-7e57c000	Deferred        imm32<elf>
  \-PE	7e560000-7e57c000	\               imm32
ELF	7e57c000-7e581000	Deferred        libxdmcp.so.6
ELF	7e581000-7e584000	Deferred        libxau.so.6
ELF	7e584000-7e59d000	Deferred        libxcb.so.1
ELF	7e59d000-7e6ba000	Deferred        libx11.so.6
ELF	7e6ba000-7e6d1000	Deferred        libice.so.6
ELF	7e6d1000-7e6d9000	Deferred        libsm.so.6
ELF	7e6db000-7e6df000	Deferred        libgpg-error.so.0
ELF	7e6df000-7e6f3000	Deferred        libresolv.so.2
ELF	7e6f5000-7e79e000	Deferred        winex11<elf>
  \-PE	7e700000-7e79e000	\               winex11
ELF	7e7c3000-7e7e9000	Deferred        libexpat.so.1
ELF	7e7e9000-7e818000	Deferred        libfontconfig.so.1
ELF	7e818000-7e82c000	Deferred        libz.so.1
ELF	7e82c000-7e8a3000	Deferred        libfreetype.so.6
ELF	7e8a4000-7e8a8000	Deferred        libuuid.so.1
ELF	7e8a8000-7e8b7000	Deferred        libxext.so.6
ELF	7e8bf000-7e95d000	Deferred        krnl386.exe16.so
PE	7e8d0000-7e95d000	Deferred        krnl386.exe16
ELF	7e95d000-7e996000	Deferred        libncurses.so.5
ELF	7e99f000-7e9b2000	Deferred        comm.drv16.so
PE	7e9a0000-7e9b2000	Deferred        comm.drv16
ELF	7e9b2000-7ea26000	Deferred        rpcrt4<elf>
  \-PE	7e9c0000-7ea26000	\               rpcrt4
ELF	7ea26000-7ea3e000	Deferred        version<elf>
  \-PE	7ea30000-7ea3e000	\               version
ELF	7ea3e000-7eace000	Deferred        gdi32<elf>
  \-PE	7ea50000-7eace000	\               gdi32
ELF	7eace000-7ebfe000	Deferred        user32<elf>
  \-PE	7eae0000-7ebfe000	\               user32
ELF	7ebfe000-7ec59000	Deferred        advapi32<elf>
  \-PE	7ec10000-7ec59000	\               advapi32
ELF	7ec59000-7ed5d000	Deferred        ole32<elf>
  \-PE	7ec70000-7ed5d000	\               ole32
ELF	7ed5d000-7edb0000	Deferred        d3dcompiler_43<elf>
  \-PE	7ed70000-7edb0000	\               d3dcompiler_43
ELF	7edb0000-7edfb000	Deferred        d3dx9_36<elf>
  \-PE	7edc0000-7edfb000	\               d3dx9_36
ELF	7edfb000-7ee14000	Deferred        d3dx9_30<elf>
  \-PE	7ee00000-7ee14000	\               d3dx9_30
ELF	7ef89000-7ef95000	Deferred        libnss_files.so.2
ELF	7ef95000-7ef9f000	Deferred        libnss_nis.so.2
ELF	7ef9f000-7efb6000	Deferred        libnsl.so.1
ELF	7efb6000-7efbe000	Deferred        libnss_compat.so.2
ELF	7efbe000-7efe4000	Deferred        libm.so.6
ELF	7efe5000-7eff9000	Deferred        system.drv16.so
PE	7eff0000-7eff9000	Deferred        system.drv16
ELF	f74c3000-f74c7000	Deferred        libdl.so.2
ELF	f74c7000-f760e000	Deferred        libc.so.6
ELF	f760f000-f7628000	Deferred        libpthread.so.0
ELF	f7628000-f776a000	Deferred        libwine-unstable.so.1
ELF	f7788000-f77a6000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\KONAMI\Pro Evolution Soccer 2010\pes2010.exe
	0000002e    0
	0000002d    0
	0000002c    0
	0000002b    0
	0000002a    0
	00000029    0
	00000028    0
	00000027  -15
	00000026    1
	00000025    2
	00000024   15
	00000023    1
	00000022    1
	00000009    0 <==
0000000e services.exe
	0000001e    0
	0000001a    0
	00000017    0
	00000016    0
	00000010    0
	0000000f    0
00000013 winedevice.exe
	00000019    0
	00000018    0
	00000015    0
	00000014    0
0000001b plugplay.exe
	0000001f    0
	0000001d    0
	0000001c    0
00000020 explorer.exe
	00000021    0
Backtrace:
=>0 0x00f173b9 in pes2010 (+0xb173b9) (0x00000001)
  1 0x00000000 (0x00000000)

what must i to do??
thanks a lot

---

### Post by tahitiwibble on 2011-04-29
I had the same error message and if you go [here]("http://www.winehq.org/download/ubuntu") I think it might solve your problem as it did mine. For some reason the update manager wasn't giving me the latest version. Once the version 1.3 installed BINGO!

---

