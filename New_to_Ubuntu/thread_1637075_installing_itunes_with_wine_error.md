---
title: "installing itunes with wine error"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by coolmego on 2010-12-04
**I am a beginner in linux and currently using Ubuntu10.10 and trying to install Itunes10 using wine but whenever i type "wine iTunesSetup.exe" in the terminal it shows the following command in the terminal..i have attached an "prt-sc"  image where you can see..**

---

### Post by owners4life5 on 2010-12-04
you have to navigate to where you downloaded the setup.exe file:

for example, if you saved it in the downloads folder, under the home folder, you would have to do this, where "user" is your username:

```
cd /home/user/Downloads
wine setup.exe
```

please reply if this doesn.t work

---

### Post by coolmego on 2010-12-04
ya thanx it worked..but now after installing it the itunes is not starting up..a pop out is coming saying about a fatal error...and in the terminal it is showing this...

shibu@shibu-HP-Pavilion-dv4-Notebook-PC:~$ wine ~/.wine/drive_c/Program\ Files/iTunes/iTunes.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation 0x4240000 0 0x32f690 4
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x173c98,0x173b98): stub
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000001 not handled
fixme:win:EnumDisplayDevicesW ((null),0,0x32e8dc,0x00000000), stub!
fixme:win:DisableProcessWindowsGhosting : stub
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x1000b4 0x00000000
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0xa7c7dd8,0xa7c7cd8): stub
fixme:advapi:GetCurrentHwProfileA (0x32e430) semi-stub
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:win:RegisterDeviceNotificationW (hwnd=0x1000b4, filter=0x32e620,flags=0x00000000) returns a fake device notification handle!
fixme:win:RegisterDeviceNotificationW (hwnd=0x1000b4, filter=0x32e618,flags=0x00000000) returns a fake device notification handle!
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x90094 0x00000000
Set args[3] to --parentPipe
fixme:service:EnumServicesStatusA 0xa824ff0 type=30 state=3 (nil) 0 0x32f0a8 0x32f0ac 0x32f0b4
fixme:service:EnumServicesStatusA 0xa824ff0 type=30 state=3 (nil) 0 0x32ef30 0x32ef34 0x32ef3c
fixme:service:EnumServicesStatusA 0xa825020 type=30 state=3 (nil) 0 0x32ef34 0x32ef38 0x32ef40
fixme:service:EnumServicesStatusA 0xa825020 type=30 state=3 (nil) 0 0x32e0d4 0x32e0d8 0x32e0e0
fixme:service:EnumServicesStatusA 0xa825020 type=30 state=3 (nil) 0 0x32e048 0x32e04c 0x32e054
fixme:service:EnumServicesStatusA 0xa825138 type=30 state=3 (nil) 0 0x32e048 0x32e04c 0x32e054
fixme:service:EnumServicesStatusA 0xa825138 type=30 state=3 (nil) 0 0x32e63c 0x32e640 0x32e648
fixme:service:EnumServicesStatusA 0xa825138 type=30 state=3 (nil) 0 0x32f048 0x32f04c 0x32f054
fixme:service:EnumServicesStatusA 0xa825138 type=30 state=3 (nil) 0 0x32f044 0x32f048 0x32f050
fixme:win:EnumDisplayDevicesW ((null),0,0x32d950,0x00000000), stub!
wine: Unhandled page fault on read access to 0xffffffff at address 0x21acd6c5 (thread 0081), starting debugger...
fixme:advapi:GetCurrentHwProfileA (0x33fbe0) semi-stub
Unhandled exception: page fault on read access to 0xffffffff in 32-bit code (0x21acd6c5).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:21acd6c5 ESP:0032cf1c EBP:00000001 EFLAGS:00010286(  R- --  I S - -P- )
 EAX:ffffffff EBX:00000000 ECX:7cd061a8 EDX:00000001
 ESI:7ce234e8 EDI:00000008
Stack dump:
0x0032cf1c:  00000000 7cd061a8 7ce234e8 00000001
0x0032cf2c:  682b53c0 682b3ff4 682b53c0 7cd061a8
0x0032cf3c:  00000000 00000001 00000001 00000000
0x0032cf4c:  7ce234e8 00000051 7cd86e5c 21acdbb6
0x0032cf5c:  00000000 7cd061a8 7ce234e8 00000001
0x0032cf6c:  000175f0 00000001 00000001 00000000
Backtrace:
0x21acd6c5: call	*%eax
Modules:
Module	Address			Debug info	Name (218 modules)
PE	  330000-  340000	Deferred        pthreadvc2
PE	  340000-  34e000	Deferred        libdispatch
PE	  3c0000-  3ea000	Deferred        avfoundationcf
PE	  400000-  d55000	Deferred        itunes
PE	  e70000- 149d000	Deferred        mediatoolbox
PE	 14a0000- 15e4000	Deferred        quartzcore
PE	 15f0000- 16bb000	Deferred        corefoundation
PE	 16c0000- 16dc000	Deferred        objc
PE	 16e0000- 17dd000	Deferred        icuin40
PE	 17e0000- 18c1000	Deferred        icuuc40
PE	 18d0000- 18e1000	Deferred        asl
PE	 18f0000- 1c94000	Deferred        coregraphics
PE	 1ca0000- 1cb3000	Deferred        zlib1
PE	 1cc0000- 1e00000	Deferred        corevideo
PE	 1e00000- 1f33000	Deferred        libxml2
PE	 1f40000- 1fd9000	Deferred        cfnetwork
PE	 1fe0000- 2043000	Deferred        sqlite3
PE	 2050000- 2437000	Deferred        coreaudiotoolbox
PE	 2440000- 248c000	Deferred        coremedia
PE	 2490000- 26c2000	Deferred        videotoolbox
PE	 26d0000- 2d82000	Deferred        webkit
PE	 2d90000- 2ef6000	Deferred        javascriptcore
PE	 2f00000- 319c000	Deferred        gnsdk_dsp
PE	 31a0000- 325e000	Deferred        gnsdk_sdkmanager
PE	 3260000- 3290000	Deferred        gnsdk_musicid
PE	 3290000- 32d1000	Deferred        gnsdk_submit
PE	 3de0000- 3e0e000	Deferred        qtcf
PE	 6240000- 625e000	Deferred        itunesregistry
PE	 6370000- 638f000	Deferred        ituneslocalized
PE	 64a0000- 64b7000	Deferred        itunes
PE	 6c30000- 6c68000	Deferred        corevideo.qtx
PE	 6d80000- 6dfe000	Deferred        quicktime3gppauthoring.qtx
PE	 6e00000- 6e20000	Deferred        quicktimeaudiosupport.qtx
PE	 7950000- 7b7e000	Deferred        quicktimeauthoring.qtx
PE	 7fd0000- 830a000	Deferred        quicktimeh264.qtx
PE	 8ba0000- 8bfb000	Deferred        quicktimestreamingauthoring.qtx
PE	 8d10000- 8d3d000	Deferred        quicktimestreamingextras.qtx
PE	 91f0000- a2fb000	Deferred        corefp
PE	 aac0000- abff000	Deferred        itunesmobiledevice
PE	16000000-16017000	Deferred        dnssd
ELF	20000000-200ba000	Deferred        comdlg32<elf>
  \-PE	20010000-200ba000	\               comdlg32
ELF	200ba000-200df000	Deferred        odbc32<elf>
  \-PE	200c0000-200df000	\               odbc32
ELF	200df000-200f3000	Deferred        lz32<elf>
  \-PE	200e0000-200f3000	\               lz32
ELF	200f3000-2010e000	Deferred        wsock32<elf>
  \-PE	20100000-2010e000	\               wsock32
ELF	2010e000-2019f000	Deferred        winmm<elf>
  \-PE	20120000-2019f000	\               winmm
ELF	2019f000-201d3000	Deferred        d3d9<elf>
  \-PE	201b0000-201d3000	\               d3d9
ELF	201d3000-201e9000	Deferred        psapi<elf>
  \-PE	201e0000-201e9000	\               psapi
ELF	201e9000-20242000	Deferred        riched20<elf>
  \-PE	201f0000-20242000	\               riched20
ELF	20242000-2024e000	Deferred        libavahi-common.so.3
ELF	2024e000-2025e000	Deferred        libavahi-client.so.3
ELF	2025e000-20282000	Deferred        libk5crypto.so.3
ELF	20282000-2028a000	Deferred        libkrb5support.so.0
ELF	2028a000-202cc000	Deferred        libpulse.so.0
ELF	202cc000-202d3000	Deferred        libogg.so.0
ELF	202d3000-202ec000	Deferred        msacm32<elf>
  \-PE	202e0000-202ec000	\               msacm32
ELF	202ec000-20344000	Deferred        ddraw<elf>
  \-PE	202f0000-20344000	\               ddraw
ELF	20344000-20370000	Deferred        secur32<elf>
  \-PE	20350000-20370000	\               secur32
ELF	20370000-2039a000	Deferred        netapi32<elf>
  \-PE	20380000-2039a000	\               netapi32
ELF	2039a000-203ae000	Deferred        cryptdll<elf>
  \-PE	203a0000-203ae000	\               cryptdll
ELF	203ae000-203cb000	Deferred        dxdiagn<elf>
  \-PE	203b0000-203cb000	\               dxdiagn
ELF	203fc000-20402000	Deferred        libasound_module_pcm_pulse.so
ELF	20a64000-20aff000	Deferred        libgnutls.so.26
ELF	21155000-2128d000	Deferred        wined3d<elf>
  \-PE	21160000-2128d000	\               wined3d
ELF	214dc000-214e5000	Deferred        librt.so.1
ELF	214e5000-22225000	Export          libglcore.so.1
ELF	23ef7000-23f41000	Deferred        libpulsecommon-0.9.21.so
ELF	26c73000-26cd8000	Deferred        gdiplus<elf>
  \-PE	26c80000-26cd8000	\               gdiplus
ELF	27f3a000-27fd6000	Deferred        crypt32<elf>
  \-PE	27f40000-27fd6000	\               crypt32
ELF	28d00000-28d4c000	Deferred        libflac.so.8
ELF	2b170000-2b1cd000	Deferred        setupapi<elf>
  \-PE	2b180000-2b1cd000	\               setupapi
ELF	30480000-3052e000	Deferred        libkrb5.so.3
ELF	309b7000-30a7d000	Deferred        libasound.so.2
ELF	332b4000-332b7000	Deferred        libx11-xcb.so.1
ELF	3457d000-345fd000	Deferred        msvcrt<elf>
  \-PE	34590000-345fd000	\               msvcrt
ELF	34846000-34862000	Deferred        libgcc_s.so.1
ELF	350b8000-350ce000	Deferred        midimap<elf>
  \-PE	350c0000-350ce000	\               midimap
ELF	3774c000-37760000	Deferred        msimg32<elf>
  \-PE	37750000-37760000	\               msimg32
ELF	3898f000-389be000	Deferred        libgssapi_krb5.so.2
ELF	3a6d4000-3a6fc000	Deferred        libvorbis.so.0
ELF	3d847000-3d8a2000	Deferred        wininet<elf>
  \-PE	3d850000-3d8a2000	\               wininet
ELF	3dc48000-3dc7a000	Deferred        wintrust<elf>
  \-PE	3dc50000-3dc7a000	\               wintrust
ELF	3e1c3000-3e2aa000	Deferred        oleaut32<elf>
  \-PE	3e1e0000-3e2aa000	\               oleaut32
ELF	3efb7000-3efee000	Deferred        winealsa<elf>
  \-PE	3efc0000-3efee000	\               winealsa
ELF	47e41000-47e46000	Deferred        libgpg-error.so.0
ELF	48b3c000-48b40000	Deferred        libkeyutils.so.1
ELF	48b52000-48b66000	Deferred        libresolv.so.2
PE	4ad00000-4ba5c000	Deferred        icudt40
ELF	4bfca000-4bfce000	Deferred        libcom_err.so.2
ELF	4c56c000-4c57a000	Deferred        libxi.so.6
ELF	4f2d3000-4f2f3000	Deferred        iphlpapi<elf>
  \-PE	4f2e0000-4f2f3000	\               iphlpapi
ELF	50c37000-50c5d000	Deferred        msacm32<elf>
  \-PE	50c40000-50c5d000	\               msacm32
ELF	51b07000-51b6f000	Deferred        libsndfile.so.1
ELF	5367b000-536a8000	Deferred        ws2_32<elf>
  \-PE	53680000-536a8000	\               ws2_32
ELF	55c45000-55c56000	Deferred        libtasn1.so.3
ELF	55e5e000-55ea6000	Deferred        dsound<elf>
  \-PE	55e60000-55ea6000	\               dsound
ELF	5664e000-56669000	Deferred        oleacc<elf>
  \-PE	56650000-56669000	\               oleacc
ELF	57b46000-57b90000	Deferred        libcups.so.2
ELF	5a1b8000-5a330000	Deferred        libvorbisenc.so.2
ELF	5a84c000-5a86f000	Deferred        mpr<elf>
  \-PE	5a850000-5a86f000	\               mpr
ELF	5bc81000-5bc86000	Deferred        libxcb-atom.so.1
ELF	5c533000-5c56a000	Deferred        winspool<elf>
  \-PE	5c540000-5c56a000	\               winspool
ELF	61b34000-61b70000	Deferred        libdbus-1.so.3
ELF	64f30000-64f32000	Deferred        libnvidia-tls.so.1
PE	66800000-673c1000	Deferred        quicktime.qts
PE	673d0000-674ac000	Deferred        quicktimestreaming.qtx
PE	67500000-675db000	Deferred        quicktimevr.qtx
PE	676d0000-677a0000	Deferred        quicktimeinternetextras.qtx
ELF	67867000-6787c000	Deferred        userenv<elf>
  \-PE	67870000-6787c000	\               userenv
PE	679d0000-67a23000	Deferred        quicktimecapture.qtx
PE	67a30000-67ac1000	Deferred        quicktimeeffects.qtx
PE	67ae0000-67bd5000	Deferred        quicktimeimage.qtx
PE	67be0000-67c62000	Deferred        quicktimemusic.qtx
PE	67c70000-67cea000	Deferred        quicktimempeg.qtx
PE	67cf0000-67d55000	Deferred        quicktimeessentials.qtx
PE	67d60000-67dba000	Deferred        quicktimempeg4.qtx
PE	67dc0000-67e52000	Deferred        quicktimempeg4authoring.qtx
PE	67e60000-67ebb000	Deferred        quicktime3gpp.qtx
ELF	67f1e000-67fc2000	Deferred        libgl.so.1
ELF	68000000-68140000	Deferred        libwine.so.1
ELF	68140000-6815a000	Deferred        libpthread.so.0
ELF	6815a000-682b8000	Deferred        libc.so.6
ELF	682b8000-682bc000	Deferred        libdl.so.2
ELF	682bc000-682e2000	Deferred        libm.so.6
ELF	682e2000-682f9000	Deferred        libnsl.so.1
ELF	682f9000-68304000	Deferred        libnss_nis.so.2
ELF	68304000-68310000	Deferred        libnss_files.so.2
ELF	68310000-68440000	Deferred        user32<elf>
  \-PE	68320000-68440000	\               user32
ELF	68440000-684cb000	Deferred        gdi32<elf>
  \-PE	68450000-684cb000	\               gdi32
ELF	684cb000-68525000	Deferred        advapi32<elf>
  \-PE	684e0000-68525000	\               advapi32
ELF	68525000-68702000	Deferred        shell32<elf>
  \-PE	68530000-68702000	\               shell32
ELF	68702000-68763000	Deferred        shlwapi<elf>
  \-PE	68710000-68763000	\               shlwapi
ELF	68763000-687da000	Deferred        libfreetype.so.6
ELF	687da000-687ef000	Deferred        libz.so.1
ELF	687ef000-6881f000	Deferred        libfontconfig.so.1
ELF	6881f000-68846000	Deferred        libexpat.so.1
ELF	68846000-6884f000	Deferred        libsm.so.6
ELF	6884f000-68868000	Deferred        libice.so.6
ELF	68868000-68878000	Deferred        libxext.so.6
ELF	68878000-6887d000	Deferred        libuuid.so.1
ELF	6887d000-68897000	Deferred        libxcb.so.1
ELF	68897000-6889b000	Deferred        libxau.so.6
ELF	6889b000-688a1000	Deferred        libxdmcp.so.6
ELF	688a1000-688c2000	Deferred        imm32<elf>
  \-PE	688b0000-688c2000	\               imm32
ELF	688c2000-688c6000	Deferred        libxinerama.so.1
ELF	688c6000-688cc000	Deferred        libxxf86vm.so.1
ELF	688cc000-688d6000	Deferred        libxrender.so.1
ELF	688d6000-688de000	Deferred        libxrandr.so.2
ELF	688de000-688e2000	Deferred        libxcomposite.so.1
ELF	688e2000-688e8000	Deferred        libxfixes.so.3
ELF	688e8000-688f2000	Deferred        libxcursor.so.1
ELF	688f2000-68926000	Deferred        uxtheme<elf>
  \-PE	68900000-68926000	\               uxtheme
ELF	68926000-68a24000	Deferred        ole32<elf>
  \-PE	68940000-68a24000	\               ole32
ELF	6a4e7000-6a4ef000	Deferred        libnss_compat.so.2
ELF	6a62e000-6a644000	Deferred        wtsapi32<elf>
  \-PE	6a630000-6a644000	\               wtsapi32
ELF	6dde0000-6de53000	Deferred        rpcrt4<elf>
  \-PE	6ddf0000-6de53000	\               rpcrt4
ELF	6f02d000-6f046000	Deferred        version<elf>
  \-PE	6f030000-6f046000	\               version
ELF	6f7a3000-6f7bc000	Deferred        imagehlp<elf>
  \-PE	6f7b0000-6f7bc000	\               imagehlp
ELF	71b08000-71bf3000	Deferred        comctl32<elf>
  \-PE	71b10000-71bf3000	\               comctl32
ELF	72cb9000-72cd7000	Deferred        ld-linux.so.2
ELF	72d96000-72e37000	Deferred        winex11<elf>
  \-PE	72da0000-72e37000	\               winex11
ELF	759d6000-75af3000	Deferred        libx11.so.6
ELF	75bcf000-75bd5000	Deferred        libxtst.so.6
ELF	76c73000-76c7c000	Deferred        libwrap.so.0
ELF	77e68000-77edc000	Deferred        libgcrypt.so.11
PE	78130000-781cb000	Deferred        msvcr80
ELF	7b800000-7b971000	Deferred        kernel32<elf>
  \-PE	7b810000-7b971000	\               kernel32
ELF	7bc00000-7bcb7000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
PE	7c420000-7c4a7000	Deferred        msvcp80
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
	0000008f    0
	0000008d    0
	00000032    0
	00000041    0
	00000014    0
	00000010    0
	0000000f    0
00000011 winedevice.exe
	00000016    0
	00000013    0
	00000012    0
00000017 explorer.exe
	00000018    0
0000003e mDNSResponder.exe
	00000042    0
	00000040    0
	0000003f    0
00000029 iPodService.exe
	0000005c    0
	0000001a    0
	00000021    0
	00000051    0
	0000004b    0
	0000006d    0
	00000033    0
	00000039    0
	0000003c    0
	0000001c    0
	00000015    0
	00000026    0
	0000000c    0
	0000000b    0
	0000000d    0
	0000002d    0
	00000047    0
	0000002b    0
	0000003d    0
	00000044    0
	00000038    0
	00000036    0
	00000024    0
	00000022    0
00000023 rpcss.exe
	00000087    0
	0000007f    0
	00000034    0
	00000037    0
	00000025    0
00000065 AppleMobileDeviceHelper.exe
	00000067    0
	00000009    0
	00000066    0
00000089 AppleMobileDeviceHelper.exe
	00000095    0
	00000094    0
	0000008a    0
0000007b (D) C:\Program Files\iTunes\iTunes.exe
	00000054    0
	0000001f    0
	0000003a    0
	00000028    0
	00000035    0
	00000053    0
	0000001d    0
	0000006c    0
	00000084   15
	00000080   15
	0000007d   15
	00000085    1
	00000071    2
	00000082    1
	0000007e    0
	0000006f    0
	00000081    0 <==
0000007c AppleMobileDeviceHelper.exe
	00000031    0
	0000004f    0
	0000008b    0
00000043 distnoted.exe
	00000074    0
	00000060    0
00000027 distnoted.exe
	0000007a    0
	0000004c    0
Backtrace:

what is this and why does it comes to be like that???
now what should i do..!!!

---

### Post by Baldrick_NZ on 2010-12-04
i think ul find itunes7 is the only version which works under wine. try installing play on linux instead, it has itunes7 ready installed.

---

### Post by coolmego on 2010-12-04
i tried by itunes7 but still aint working...i downloaded rhytmbox in .tar format and extracted it now dont know how to use it...

---

### Post by Verbeck on 2010-12-04
> **coolmego said:**
> i tried by itunes7 but still aint working...i downloaded rhytmbox in .tar format and extracted it now dont know how to use it...
why did you download rythmbox?its included in ubuntu by default
its in application>sound &video >rythmbox

---

### Post by coolmego on 2010-12-04
k..den can u tell me how to run the itunes..not able to do with both iTunes7 and 10..!!

---

### Post by themusicalduck on 2010-12-04
I don't know if you'll get very far running Itunes in Wine.

You could download playonlinux from the Software Centre and try installing it through there like Baldrick_NZ suggested.

But even better, try out other players like Banshee, Amarok, Clementine, Songbird and any others that are in the Software Centre.

---

### Post by andymorton on 2010-12-04
I wouldn't expect to be able to get itunes running properly on Ubuntu. You'd be much better off using Rhythmbox or Banshee and using the Ubuntu One Music Store to download songs. 

andy

---

