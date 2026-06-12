---
title: "Java Segfaults on Minecraft"
date: 2011-07-14
forum: New to Ubuntu
---

### Post by DarrenMR415 on 2011-07-14
This
```
java -jar ~/Desktop/minecraft.jar
```

Gets me to this. 

> darren@darren-laptop:~$ java -jar ~/Desktop/minecraft.jar
16 achievements
151 recipes
Setting user: slipmagt, -1411550721681694701
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x81066ef6, pid=9692, tid=2185231216
#
# JRE version: 6.0_26-b03
# Java VM: Java HotSpot(TM) Server VM (20.1-b02 mixed mode linux-x86 )
# Problematic frame:
# C  [libGL.so.1+0x65ef6]  XF86DRIQueryExtension+0x8e
#
# An error report file with more information is saved as:
# /home/darren/hs_err_pid9692.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
Aborted
darren@darren-laptop:~$ 

```
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x81066ef6, pid=9692, tid=2185231216
#
# JRE version: 6.0_26-b03
# Java VM: Java HotSpot(TM) Server VM (20.1-b02 mixed mode linux-x86 )
# Problematic frame:
# C  [libGL.so.1+0x65ef6]  XF86DRIQueryExtension+0x8e
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

---------------  T H R E A D  ---------------

Current thread (0x0a0e0400):  JavaThread "Minecraft main thread" daemon [_thread_in_native, id=9720, stack(0x823af000,0x82400000)]

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=1 (SEGV_MAPERR), si_addr=0x00000004

Registers:
EAX=0x00000041, EBX=0x09e478f8, ECX=0x09f88130, EDX=0x810b3d60
ESP=0x823fc9d4, EBP=0x09e46d30, ESI=0x00000000, EDI=0x00000001
EIP=0x81066ef6, EFLAGS=0x00210202, CR2=0x00000004

Top of Stack: (sp=0x823fc9d4)
0x823fc9d4:   b76329ae b7634ecd 00000000 00000000
0x823fc9e4:   0000000d 00000078 823fca0c 0000000d
0x823fc9f4:   00000064 00000001 09e46d30 00002000
0x823fca04:   09ddceac 810645d0 09e46d30 823fca50
0x823fca14:   823fca54 b771c3c0 00000020 b771c3f0
0x823fca24:   b771aff4 b771c3c0 823fea7c 09e23d38
0x823fca34:   bfdb4b3d 823fca68 b75f3932 bfdb4b3f
0x823fca44:   810920de 00000013 810920de 00000013 

Instructions: (pc=0x81066ef6)
0x81066ed6:   4d 6c 89 4d 64 b8 41 00 00 00 88 01 bf 01 00 00
0x81066ee6:   00 66 89 79 02 83 45 6c 04 83 45 60 01 8b 76 08
0x81066ef6:   0f b6 56 04 88 11 88 41 01 33 c9 8d 04 24 51 51
0x81066f06:   50 55 e8 a3 ff 59 02 83 c4 10 85 c0 75 1c 8b 85 

Register to memory mapping:

EAX=0x00000041 is an unknown value
EBX=0x09e478f8 is an unknown value
ECX=0x09f88130 is an unknown value
EDX=0x810b3d60: <offset 0xb2d60> in /usr/lib/fglrx/libGL.so.1 at 0x81001000
ESP=0x823fc9d4 is pointing into the stack for thread: 0x0a0e0400
EBP=0x09e46d30 is an unknown value
ESI=0x00000000 is an unknown value
EDI=0x00000001 is an unknown value


Stack: [0x823af000,0x82400000],  sp=0x823fc9d4,  free space=310k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [libGL.so.1+0x65ef6]  XF86DRIQueryExtension+0x8e

Java frames: (J=compiled Java code, j=interpreted, Vv=VM code)
j  org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(JILjava/nio/ByteBuffer;Lorg/lwjgl/opengl/PixelFormat;)V+0
j  org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(Lorg/lwjgl/opengl/PixelFormat;)V+24
j  org.lwjgl.opengl.LinuxDisplay.createPeerInfo(Lorg/lwjgl/opengl/PixelFormat;)Lorg/lwjgl/opengl/PeerInfo;+6
j  org.lwjgl.opengl.Display.create(Lorg/lwjgl/opengl/PixelFormat;Lorg/lwjgl/opengl/Drawable;Lorg/lwjgl/opengl/ContextAttribs;)V+55
j  org.lwjgl.opengl.Display.create(Lorg/lwjgl/opengl/PixelFormat;)V+9
j  org.lwjgl.opengl.Display.create()V+13
j  net.minecraft.client.Minecraft.a()V+135
j  net.minecraft.client.Minecraft.run()V+6
j  java.lang.Thread.run()V+11
v  ~StubRoutines::call_stub

---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
=>0x0a0e0400 JavaThread "Minecraft main thread" daemon [_thread_in_native, id=9720, stack(0x823af000,0x82400000)]
  0x0a0dfc00 JavaThread "Timer hack thread" daemon [_thread_blocked, id=9719, stack(0x812af000,0x81300000)]
  0x81eecc00 JavaThread "Keep-Alive-Timer" daemon [_thread_blocked, id=9716, stack(0x8262e000,0x8267f000)]
  0x09d9c800 JavaThread "DestroyJavaVM" [_thread_blocked, id=9694, stack(0xb6929000,0xb697a000)]
  0x839fb000 JavaThread "TimerQueue" daemon [_thread_blocked, id=9713, stack(0x8251b000,0x8256c000)]
  0x0a1c9000 JavaThread "AWT-EventQueue-0" [_thread_blocked, id=9709, stack(0x8258c000,0x825dd000)]
  0x0a1c8000 JavaThread "AWT-Shutdown" [_thread_blocked, id=9708, stack(0x825dd000,0x8262e000)]
  0x0a0d0c00 JavaThread "AWT-XAWT" daemon [_thread_in_native, id=9706, stack(0x83449000,0x8349a000)]
  0x0a078800 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=9705, stack(0x834c4000,0x83515000)]
  0x09e36800 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=9703, stack(0x83a09000,0x83a5a000)]
  0x09e34400 JavaThread "C2 CompilerThread1" daemon [_thread_blocked, id=9702, stack(0x8387f000,0x83900000)]
  0x09e31c00 JavaThread "C2 CompilerThread0" daemon [_thread_blocked, id=9701, stack(0x83a5a000,0x83adb000)]
  0x09e30400 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=9700, stack(0x83adb000,0x83b2c000)]
  0x09e1e000 JavaThread "Finalizer" daemon [_thread_blocked, id=9699, stack(0x83b6b000,0x83bbc000)]
  0x09e1c800 JavaThread "Reference Handler" daemon [_thread_blocked, id=9698, stack(0x83bbc000,0x83c0d000)]

Other Threads:
  0x09e18800 VMThread [stack: 0x83c0d000,0x83c8e000] [id=9697]
  0x83909000 WatcherThread [stack: 0x837fe000,0x8387f000] [id=9704]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 PSYoungGen      total 12992K, used 6263K [0xa5090000, 0xa5f00000, 0xb37e0000)
  eden space 11200K, 40% used [0xa5090000,0xa54f0688,0xa5b80000)
  from space 1792K, 99% used [0xa5b80000,0xa5d3d918,0xa5d40000)
  to   space 1792K, 0% used [0xa5d40000,0xa5d40000,0xa5f00000)
 PSOldGen        total 29568K, used 14571K [0x881e0000, 0x89ec0000, 0xa5090000)
  object space 29568K, 49% used [0x881e0000,0x8901acf0,0x89ec0000)
 PSPermGen       total 16384K, used 14688K [0x841e0000, 0x851e0000, 0x881e0000)
  object space 16384K, 89% used [0x841e0000,0x85038368,0x851e0000)

Code Cache  [0xb38a7000, 0xb3ae7000, 0xb68a7000)
 total_blobs=547 nmethods=291 adapters=210 free_code_cache=49274560 largest_free_block=7616

Dynamic libraries:
08048000-08052000 r-xp 00000000 08:01 23462626   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/bin/java
08052000-08053000 rwxp 00009000 08:01 23462626   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/bin/java
09d97000-0a857000 rwxp 00000000 00:00 0          [heap]
81001000-810a8000 r-xp 00000000 08:01 19137323   /usr/lib/fglrx/libGL.so.1.2
810a8000-810b2000 rwxp 000a7000 08:01 19137323   /usr/lib/fglrx/libGL.so.1.2
810b2000-810b7000 rwxp 00000000 00:00 0 
810b7000-8110e000 r-xp 00000000 08:01 16781996   /home/darren/.minecraft/bin/natives/liblwjgl.so
8110e000-8110f000 r-xp 00056000 08:01 16781996   /home/darren/.minecraft/bin/natives/liblwjgl.so
8110f000-81110000 rwxp 00057000 08:01 16781996   /home/darren/.minecraft/bin/natives/liblwjgl.so
81110000-81115000 r-xs 00033000 08:01 16781968   /home/darren/.minecraft/bin/jinput.jar
81115000-8111e000 r-xs 000ac000 08:01 16781966   /home/darren/.minecraft/bin/lwjgl.jar
8111e000-812af000 rwxs 00000000 00:04 14876708   /SYSV00000000 (deleted)
812af000-812b2000 ---p 00000000 00:00 0 
812b2000-81300000 rwxp 00000000 00:00 0 
81300000-813dd000 rwxp 00000000 00:00 0 
813dd000-81400000 ---p 00000000 00:00 0 
81415000-81432000 r-xp 00000000 08:01 19791955   /lib/libgcc_s.so.1
81432000-81433000 r-xp 0001c000 08:01 19791955   /lib/libgcc_s.so.1
81433000-81434000 rwxp 0001d000 08:01 19791955   /lib/libgcc_s.so.1
8144a000-8144d000 ---p 00000000 00:00 0 
8144d000-8149b000 rwxp 00000000 00:00 0 
8149b000-81500000 rwxs 00000000 00:04 14843938   /SYSV00000000 (deleted)
81500000-815bd000 rwxp 00000000 00:00 0 
815bd000-81600000 ---p 00000000 00:00 0 
81600000-816fd000 rwxp 00000000 00:00 0 
816fd000-81700000 ---p 00000000 00:00 0 
81700000-81800000 rwxp 00000000 00:00 0 
81813000-8181f000 r-xs 0015a000 08:01 16781994   /home/darren/.minecraft/bin/minecraft.jar
81824000-8182b000 r-xp 00000000 08:01 19137339   /usr/lib/fglrx/libatiuki.so.1.0
8182b000-8182c000 rwxp 00006000 08:01 19137339   /usr/lib/fglrx/libatiuki.so.1.0
8182c000-819bd000 rwxs 00000000 00:04 13729825   /SYSV00000000 (deleted)
819bd000-81a1d000 rwxs 00000000 00:04 13434912   /SYSV00000000 (deleted)
81a1d000-81c89000 rwxp 00000000 00:00 0 
81c89000-81c93000 r-xs 00000000 08:01 16544795   /usr/share/fonts/type1/mathml/Symbol.pfb
81c93000-81ca3000 r-xs 00000000 08:01 16544690   /usr/share/fonts/type1/gsfonts/a010013l.pfb
81ca3000-81cac000 r-xs 00000000 08:01 16544789   /usr/share/fonts/type1/gsfonts/s050000l.pfb
81cac000-81cb6000 r-xs 00000000 08:01 16544075   /usr/share/fonts/X11/Type1/c0582bt_.pfb
81cb6000-81cc7000 r-xs 00000000 08:01 16544735   /usr/share/fonts/type1/gsfonts/n019023l.pfb
81cc7000-81cd1000 r-xs 00000000 08:01 16544079   /usr/share/fonts/X11/Type1/c0611bt_.pfb
81cd1000-81ceb000 r-xs 00000000 08:01 16544714   /usr/share/fonts/type1/gsfonts/c059013l.pfb
81ceb000-81d07000 r-xs 00000000 08:01 16544786   /usr/share/fonts/type1/gsfonts/p052024l.pfb
81d07000-81d20000 r-xs 00000000 08:01 16544753   /usr/share/fonts/type1/gsfonts/n021003l.pfb
81d20000-81d31000 r-xs 00000000 08:01 16544738   /usr/share/fonts/type1/gsfonts/n019024l.pfb
81d31000-81d47000 r-xs 00000000 08:01 16544771   /usr/share/fonts/type1/gsfonts/n022023l.pfb
81d47000-81d5c000 r-xs 00000000 08:01 16544708   /usr/share/fonts/type1/gsfonts/b018032l.pfb
81d5c000-81d66000 r-xs 00000000 08:01 16544077   /usr/share/fonts/X11/Type1/c0583bt_.pfb
81d66000-81d7d000 r-xs 00000000 08:01 16544792   /usr/share/fonts/type1/gsfonts/z003034l.pfb
81d7d000-81d98000 r-xs 00000000 08:01 16544780   /usr/share/fonts/type1/gsfonts/p052004l.pfb
81d98000-81db3000 r-xs 00000000 08:01 16544783   /usr/share/fonts/type1/gsfonts/p052023l.pfb
81db3000-81dc3000 r-xs 00000000 08:01 16544693   /usr/share/fonts/type1/gsfonts/a010015l.pfb
81dc3000-81dd5000 r-xs 00000000 08:01 16544732   /usr/share/fonts/type1/gsfonts/n019004l.pfb
81dd5000-81de7000 r-xs 00000000 08:01 16544711   /usr/share/fonts/type1/gsfonts/b018035l.pfb
81de7000-81e00000 r-xs 00000000 08:01 16544702   /usr/share/fonts/type1/gsfonts/b018012l.pfb
81e00000-81eff000 rwxp 00000000 00:00 0 
81eff000-81f00000 ---p 00000000 00:00 0 
81f04000-81f17000 r-xs 00000000 08:01 16544705   /usr/share/fonts/type1/gsfonts/b018015l.pfb
81f17000-81f20000 r-xs 00000000 08:01 16544083   /usr/share/fonts/X11/Type1/c0633bt_.pfb
81f20000-81f3b000 r-xs 00000000 08:01 16544717   /usr/share/fonts/type1/gsfonts/c059016l.pfb
81f3b000-81f53000 r-xs 00000000 08:01 16544765   /usr/share/fonts/type1/gsfonts/n022003l.pfb
81f53000-81f6a000 r-xs 00000000 08:01 16544759   /usr/share/fonts/type1/gsfonts/n021023l.pfb
81f6a000-81f73000 r-xs 00000000 08:01 16544085   /usr/share/fonts/X11/Type1/c0648bt_.pfb
81f73000-81f8b000 r-xs 00000000 08:01 16544723   /usr/share/fonts/type1/gsfonts/c059036l.pfb
81f8b000-81fa1000 r-xs 00000000 08:01 16544774   /usr/share/fonts/type1/gsfonts/n022024l.pfb
81fa1000-81fad000 r-xs 00000000 08:01 16544726   /usr/share/fonts/type1/gsfonts/d050000l.pfb
81fad000-81fbd000 r-xs 00000000 08:01 16544696   /usr/share/fonts/type1/gsfonts/a010033l.pfb
81fbd000-81fd6000 r-xs 00000000 08:01 16544756   /usr/share/fonts/type1/gsfonts/n021004l.pfb
81fd6000-81fee000 r-xs 00000000 08:01 16544720   /usr/share/fonts/type1/gsfonts/c059033l.pfb
81fee000-82000000 r-xs 00000000 08:01 16544744   /usr/share/fonts/type1/gsfonts/n019044l.pfb
82000000-820ff000 rwxp 00000000 00:00 0 
820ff000-82100000 ---p 00000000 00:00 0 
82100000-821f9000 rwxp 00000000 00:00 0 
821f9000-82200000 ---p 00000000 00:00 0 
82200000-82300000 rwxp 00000000 00:00 0 
82301000-8230a000 r-xs 00000000 08:01 16544081   /usr/share/fonts/X11/Type1/c0632bt_.pfb
8230a000-8231b000 r-xs 00000000 08:01 16544699   /usr/share/fonts/type1/gsfonts/a010035l.pfb
8231b000-82334000 r-xs 00000000 08:01 16544768   /usr/share/fonts/type1/gsfonts/n022004l.pfb
82334000-8234f000 r-xs 00000000 08:01 16544777   /usr/share/fonts/type1/gsfonts/p052003l.pfb
8234f000-82361000 r-xs 00000000 08:01 16544741   /usr/share/fonts/type1/gsfonts/n019043l.pfb
82361000-82372000 r-xs 00000000 08:01 16544747   /usr/share/fonts/type1/gsfonts/n019063l.pfb
82372000-82388000 r-xs 00000000 08:01 16544762   /usr/share/fonts/type1/gsfonts/n021024l.pfb
82388000-8239c000 r-xs 00000000 08:01 16544729   /usr/share/fonts/type1/gsfonts/n019003l.pfb
8239c000-823af000 r-xs 00000000 08:01 16544750   /usr/share/fonts/type1/gsfonts/n019064l.pfb
823af000-823b2000 ---p 00000000 00:00 0 
823b2000-82400000 rwxp 00000000 00:00 0 
82400000-82500000 rwxp 00000000 00:00 0 
82506000-82507000 r-xp 00000000 08:01 23462678   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libjawt.so
82507000-82508000 rwxp 00000000 08:01 23462678   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libjawt.so
82508000-82512000 r-xs 00000000 08:01 16544073   /usr/share/fonts/X11/Type1/c0419bt_.pfb
82512000-8251b000 r-xs 00000000 08:01 16544087   /usr/share/fonts/X11/Type1/c0649bt_.pfb
8251b000-8251e000 ---p 00000000 00:00 0 
8251e000-8256c000 rwxp 00000000 00:00 0 
8256c000-82570000 r-xp 00000000 08:01 19792542   /lib/tls/i686/cmov/libnss_dns-2.11.1.so
82570000-82571000 r-xp 00004000 08:01 19792542   /lib/tls/i686/cmov/libnss_dns-2.11.1.so
82571000-82572000 rwxp 00005000 08:01 19792542   /lib/tls/i686/cmov/libnss_dns-2.11.1.so
82572000-82574000 r-xp 00000000 08:01 19791993   /lib/libnss_mdns4_minimal.so.2
82574000-82575000 r-xp 00001000 08:01 19791993   /lib/libnss_mdns4_minimal.so.2
82575000-82576000 rwxp 00002000 08:01 19791993   /lib/libnss_mdns4_minimal.so.2
82576000-82579000 r-xs 0001f000 08:01 16781992   /home/darren/.minecraft/bin/lwjgl_util.jar
82579000-8257d000 r-xs 000cb000 08:01 23462586   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/ext/localedata.jar
8257d000-82585000 r-xs 00115000 08:01 23462701   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/resources.jar
82585000-8258c000 r-xs 00094000 08:01 23462583   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/jsse.jar
8258c000-8258f000 ---p 00000000 00:00 0 
8258f000-825dd000 rwxp 00000000 00:00 0 
825dd000-825e0000 ---p 00000000 00:00 0 
825e0000-8262e000 rwxp 00000000 00:00 0 
8262e000-82631000 ---p 00000000 00:00 0 
82631000-8267f000 rwxp 00000000 00:00 0 
8267f000-82689000 r-xp 00000000 08:01 19796334   /lib/libudev.so.0.6.1
82689000-8268a000 r-xp 00009000 08:01 19796334   /lib/libudev.so.0.6.1
8268a000-8268b000 rwxp 0000a000 08:01 19796334   /lib/libudev.so.0.6.1
8268b000-8269f000 r-xp 00000000 08:01 16387742   /usr/lib/libgvfscommon.so.0.0.0
8269f000-826a0000 r-xp 00013000 08:01 16387742   /usr/lib/libgvfscommon.so.0.0.0
826a0000-826a1000 rwxp 00014000 08:01 16387742   /usr/lib/libgvfscommon.so.0.0.0
826a1000-826c5000 r-xp 00000000 08:01 16384524   /usr/lib/gio/modules/libgvfsdbus.so
826c5000-826c6000 r-xp 00023000 08:01 16384524   /usr/lib/gio/modules/libgvfsdbus.so
826c6000-826c7000 rwxp 00024000 08:01 16384524   /usr/lib/gio/modules/libgvfsdbus.so
826c7000-826fe000 r-xp 00000000 08:01 19791901   /lib/libdbus-1.so.3.4.0
826fe000-826ff000 r-xp 00036000 08:01 19791901   /lib/libdbus-1.so.3.4.0
826ff000-82700000 rwxp 00037000 08:01 19791901   /lib/libdbus-1.so.3.4.0
82700000-82739000 r-xp 00000000 08:01 16386286   /usr/lib/libibus.so.1.0.0
82739000-8273a000 r-xp 00039000 08:01 16386286   /usr/lib/libibus.so.1.0.0
8273a000-8273b000 rwxp 0003a000 08:01 16386286   /usr/lib/libibus.so.1.0.0
8273b000-8273e000 r-xs 00027000 08:01 23462584   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/ext/sunjce_provider.jar
8273e000-8274f000 r-xp 00000000 08:01 16384523   /usr/lib/gio/modules/libgioremote-volume-monitor.so
8274f000-82750000 r-xp 00011000 08:01 16384523   /usr/lib/gio/modules/libgioremote-volume-monitor.so
82750000-82751000 rwxp 00012000 08:01 16384523   /usr/lib/gio/modules/libgioremote-volume-monitor.so
82751000-82756000 r-xp 00000000 08:01 16389897   /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
82756000-82757000 r-xp 00004000 08:01 16389897   /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
82757000-82758000 rwxp 00005000 08:01 16389897   /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
82758000-827f0000 r-xp 00000000 08:01 16544654   /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
827f0000-827f2000 r-xp 00000000 08:01 16521938   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
827f2000-827f3000 r-xp 00001000 08:01 16521938   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
827f3000-827f4000 rwxp 00002000 08:01 16521938   /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
827f4000-827fb000 r-xp 00000000 08:01 23462657   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libnio.so
827fb000-827fc000 rwxp 00006000 08:01 23462657   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libnio.so
827fc000-82810000 r-xp 00000000 08:01 23462656   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libnet.so
82810000-82811000 rwxp 00013000 08:01 23462656   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libnet.so
82811000-82812000 r-xs 00000000 08:01 11414337   /var/cache/fontconfig/26de28bc8622bbc1fb67fd234c21975f-le32d4.cache-3
82812000-82813000 r-xs 00000000 08:01 11405613   /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
82813000-82819000 r-xs 00000000 08:01 11405610   /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
82819000-8281b000 r-xs 00000000 08:01 11405611   /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
8281b000-8281e000 r-xs 00000000 08:01 11405620   /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
8281e000-82824000 r-xs 00000000 08:01 11415424   /var/cache/fontconfig/401a5dd6b567794a1d18dd9342dfa604-le32d4.cache-3
82824000-82825000 r-xs 00000000 08:01 11405621   /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
82825000-82827000 r-xs 00000000 08:01 11415821   /var/cache/fontconfig/b5ea634b0fb353b8ea17632d1f9ef766-le32d4.cache-3
82827000-8282b000 r-xs 00000000 08:01 11415735   /var/cache/fontconfig/926e794c3d5e5dffcaf2fa83ef8d36c2-le32d4.cache-3
8282b000-8282e000 r-xs 00000000 08:01 11412726   /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
8282e000-8282f000 r-xs 00000000 08:01 11405604   /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
8282f000-82830000 r-xs 00000000 08:01 11405598   /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
82830000-82831000 r-xs 00000000 08:01 11405606   /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
82831000-82835000 r-xs 00000000 08:01 11405612   /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
82835000-82839000 r-xs 00000000 08:01 11415588   /var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-le32d4.cache-3
82839000-82840000 r-xs 00000000 08:01 11413514   /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
82840000-8284b000 r-xs 00000000 08:01 11414705   /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
8284b000-8284e000 r-xs 00000000 08:01 11405617   /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
8284e000-8284f000 r-xs 00000000 08:01 11415473   /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
8284f000-82871000 r-xs 00000000 08:01 11414163   /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-3
82871000-82897000 r-xp 00000000 08:01 16389887   /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
82897000-82898000 r-xp 00025000 08:01 16389887   /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
82898000-82899000 rwxp 00026000 08:01 16389887   /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
82899000-828a0000 r-xp 00000000 08:01 16386372   /usr/lib/libltdl.so.7.2.1
828a0000-828a1000 r-xp 00006000 08:01 16386372   /usr/lib/libltdl.so.7.2.1
828a1000-828a2000 rwxp 00007000 08:01 16386372   /usr/lib/libltdl.so.7.2.1
828a2000-828af000 r-xp 00000000 08:01 16386630   /usr/lib/libtdb.so.1.2.0
828af000-828b0000 r-xp 0000c000 08:01 16386630   /usr/lib/libtdb.so.1.2.0
828b0000-828b1000 rwxp 0000d000 08:01 16386630   /usr/lib/libtdb.so.1.2.0
828b1000-828d8000 r-xp 00000000 08:01 16386678   /usr/lib/libvorbis.so.0.4.3
828d8000-828d9000 r-xp 00026000 08:01 16386678   /usr/lib/libvorbis.so.0.4.3
828d9000-828da000 rwxp 00027000 08:01 16386678   /usr/lib/libvorbis.so.0.4.3
828da000-828e1000 r-xp 00000000 08:01 16386682   /usr/lib/libvorbisfile.so.3.3.2
828e1000-828e2000 r-xp 00006000 08:01 16386682   /usr/lib/libvorbisfile.so.3.3.2
828e2000-828e3000 rwxp 00007000 08:01 16386682   /usr/lib/libvorbisfile.so.3.3.2
828e3000-828f1000 r-xp 00000000 08:01 16385851   /usr/lib/libcanberra.so.0.2.1
828f1000-828f2000 r-xp 0000d000 08:01 16385851   /usr/lib/libcanberra.so.0.2.1
828f2000-828f3000 rwxp 0000e000 08:01 16385851   /usr/lib/libcanberra.so.0.2.1
828f3000-828f6000 r-xp 00000000 08:01 16385849   /usr/lib/libcanberra-gtk.so.0.1.5
828f6000-828f7000 r-xp 00003000 08:01 16385849   /usr/lib/libcanberra-gtk.so.0.1.5
828f7000-828f8000 rwxp 00004000 08:01 16385849   /usr/lib/libcanberra-gtk.so.0.1.5
828f8000-828fb000 r-xs 00013000 08:01 23462587   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/jce.jar
828fb000-82903000 r-xs 00000000 08:01 11405616   /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
82903000-8290b000 r-xs 00000000 08:01 11412576   /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
8290b000-8290e000 r-xs 00000000 08:01 11415001   /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
8290e000-82a2c000 r-xp 00000000 08:01 16390365   /usr/lib/locale/en_US.utf8/LC_COLLATE
82a2c000-82a50000 r-xp 00000000 08:01 19791948   /lib/libexpat.so.1.5.2
82a50000-82a52000 r-xp 00024000 08:01 19791948   /lib/libexpat.so.1.5.2
82a52000-82a53000 rwxp 00026000 08:01 19791948   /lib/libexpat.so.1.5.2
82a53000-82a6c000 r-xp 00000000 08:01 19792037   /lib/libselinux.so.1
82a6c000-82a6d000 r-xp 00018000 08:01 19792037   /lib/libselinux.so.1
82a6d000-82a6e000 rwxp 00019000 08:01 19792037   /lib/libselinux.so.1
82a6e000-82a7e000 r-xp 00000000 08:01 19795978   /lib/tls/i686/cmov/libresolv-2.11.1.so
82a7e000-82a7f000 r-xp 00010000 08:01 19795978   /lib/tls/i686/cmov/libresolv-2.11.1.so
82a7f000-82a80000 rwxp 00011000 08:01 19795978   /lib/tls/i686/cmov/libresolv-2.11.1.so
82a80000-82a82000 rwxp 00000000 00:00 0 
82a82000-82ab1000 r-xp 00000000 08:01 19792013   /lib/libpcre.so.3.12.1
82ab1000-82ab2000 r-xp 0002e000 08:01 19792013   /lib/libpcre.so.3.12.1
82ab2000-82ab3000 rwxp 0002f000 08:01 19792013   /lib/libpcre.so.3.12.1
82ab3000-82ab9000 r-xp 00000000 08:01 16386717   /usr/lib/libxcb-render.so.0.0.0
82ab9000-82aba000 r-xp 00005000 08:01 16386717   /usr/lib/libxcb-render.so.0.0.0
82aba000-82abb000 rwxp 00006000 08:01 16386717   /usr/lib/libxcb-render.so.0.0.0
82abb000-82ade000 r-xp 00000000 08:01 19792631   /lib/libpng12.so.0.42.0
82ade000-82adf000 r-xp 00022000 08:01 19792631   /lib/libpng12.so.0.42.0
82adf000-82ae0000 rwxp 00023000 08:01 19792631   /lib/libpng12.so.0.42.0
82ae0000-82af4000 r-xp 00000000 08:01 16385928   /usr/lib/libdirect-1.2.so.0.8.0
82af4000-82af5000 r-xp 00013000 08:01 16385928   /usr/lib/libdirect-1.2.so.0.8.0
82af5000-82af6000 rwxp 00014000 08:01 16385928   /usr/lib/libdirect-1.2.so.0.8.0
82af6000-82afe000 r-xp 00000000 08:01 16386039   /usr/lib/libfusion-1.2.so.0.8.0
82afe000-82aff000 r-xp 00007000 08:01 16386039   /usr/lib/libfusion-1.2.so.0.8.0
82aff000-82b00000 rwxp 00008000 08:01 16386039   /usr/lib/libfusion-1.2.so.0.8.0
82b00000-82b73000 r-xp 00000000 08:01 16385930   /usr/lib/libdirectfb-1.2.so.0.8.0
82b73000-82b74000 ---p 00073000 08:01 16385930   /usr/lib/libdirectfb-1.2.so.0.8.0
82b74000-82b75000 r-xp 00073000 08:01 16385930   /usr/lib/libdirectfb-1.2.so.0.8.0
82b75000-82b76000 rwxp 00074000 08:01 16385930   /usr/lib/libdirectfb-1.2.so.0.8.0
82b76000-82b77000 rwxp 00000000 00:00 0 
82b77000-82bce000 r-xp 00000000 08:01 16386494   /usr/lib/libpixman-1.so.0.16.4
82bce000-82bd0000 r-xp 00057000 08:01 16386494   /usr/lib/libpixman-1.so.0.16.4
82bd0000-82bd1000 rwxp 00059000 08:01 16386494   /usr/lib/libpixman-1.so.0.16.4
82bd1000-82c99000 r-xp 00000000 08:01 19792006   /lib/libglib-2.0.so.0.2400.1
82c99000-82c9a000 r-xp 000c7000 08:01 19792006   /lib/libglib-2.0.so.0.2400.1
82c9a000-82c9b000 rwxp 000c8000 08:01 19792006   /lib/libglib-2.0.so.0.2400.1
82c9b000-82cd8000 r-xp 00000000 08:01 16386357   /usr/lib/libgobject-2.0.so.0.2400.1
82cd8000-82cd9000 r-xp 0003c000 08:01 16386357   /usr/lib/libgobject-2.0.so.0.2400.1
82cd9000-82cda000 rwxp 0003d000 08:01 16386357   /usr/lib/libgobject-2.0.so.0.2400.1
82cda000-82d08000 r-xp 00000000 08:01 16386027   /usr/lib/libfontconfig.so.1.4.4
82d08000-82d09000 r-xp 0002d000 08:01 16386027   /usr/lib/libfontconfig.so.1.4.4
82d09000-82d0a000 rwxp 0002e000 08:01 16386027   /usr/lib/libfontconfig.so.1.4.4
82d0a000-82d1d000 r-xp 00000000 08:01 19792070   /lib/libz.so.1.2.3.3
82d1d000-82d1e000 r-xp 00012000 08:01 19792070   /lib/libz.so.1.2.3.3
82d1e000-82d1f000 rwxp 00013000 08:01 19792070   /lib/libz.so.1.2.3.3
82d1f000-82d90000 r-xp 00000000 08:01 16384070   /usr/lib/libfreetype.so.6.3.22
82d90000-82d94000 r-xp 00070000 08:01 16384070   /usr/lib/libfreetype.so.6.3.22
82d94000-82d95000 rwxp 00074000 08:01 16384070   /usr/lib/libfreetype.so.6.3.22
82d95000-82dd5000 r-xp 00000000 08:01 16384044   /usr/lib/libpango-1.0.so.0.2800.0
82dd5000-82dd6000 ---p 00040000 08:01 16384044   /usr/lib/libpango-1.0.so.0.2800.0
82dd6000-82dd7000 r-xp 00040000 08:01 16384044   /usr/lib/libpango-1.0.so.0.2800.0
82dd7000-82dd8000 rwxp 00041000 08:01 16384044   /usr/lib/libpango-1.0.so.0.2800.0
82dd8000-82dfd000 r-xp 00000000 08:01 16390255   /usr/lib/libpangoft2-1.0.so.0.2800.0
82dfd000-82dfe000 r-xp 00024000 08:01 16390255   /usr/lib/libpangoft2-1.0.so.0.2800.0
82dfe000-82dff000 rwxp 00025000 08:01 16390255   /usr/lib/libpangoft2-1.0.so.0.2800.0
82dff000-82e99000 r-xp 00000000 08:01 16387081   /usr/lib/libgio-2.0.so.0.2400.1
82e99000-82e9a000 ---p 0009a000 08:01 16387081   /usr/lib/libgio-2.0.so.0.2400.1
82e9a000-82e9b000 r-xp 0009a000 08:01 16387081   /usr/lib/libgio-2.0.so.0.2400.1
82e9b000-82e9c000 rwxp 0009b000 08:01 16387081   /usr/lib/libgio-2.0.so.0.2400.1
82e9c000-82e9d000 rwxp 00000000 00:00 0 
82e9d000-82f14000 r-xp 00000000 08:01 16385841   /usr/lib/libcairo.so.2.10800.10
82f14000-82f16000 r-xp 00076000 08:01 16385841   /usr/lib/libcairo.so.2.10800.10
82f16000-82f17000 rwxp 00078000 08:01 16385841   /usr/lib/libcairo.so.2.10800.10
82f17000-82faa000 r-xp 00000000 08:01 16389591   /usr/lib/libgdk-x11-2.0.so.0.2000.1
82faa000-82fac000 r-xp 00093000 08:01 16389591   /usr/lib/libgdk-x11-2.0.so.0.2000.1
82fac000-82fad000 rwxp 00095000 08:01 16389591   /usr/lib/libgdk-x11-2.0.so.0.2000.1
82fad000-8337a000 r-xp 00000000 08:01 16389590   /usr/lib/libgtk-x11-2.0.so.0.2000.1
8337a000-8337e000 r-xp 003cd000 08:01 16389590   /usr/lib/libgtk-x11-2.0.so.0.2000.1
8337e000-83380000 rwxp 003d1000 08:01 16389590   /usr/lib/libgtk-x11-2.0.so.0.2000.1
83380000-83382000 rwxp 00000000 00:00 0 
83382000-83383000 r-xs 00000000 08:01 11414337   /var/cache/fontconfig/26de28bc8622bbc1fb67fd234c21975f-le32d4.cache-3
83383000-83384000 r-xs 00000000 08:01 11405613   /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
83384000-8338a000 r-xs 00000000 08:01 11405610   /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
8338a000-8338c000 r-xs 00000000 08:01 11405611   /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
8338c000-8338f000 r-xs 00000000 08:01 11405620   /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
8338f000-83395000 r-xs 00000000 08:01 11415424   /var/cache/fontconfig/401a5dd6b567794a1d18dd9342dfa604-le32d4.cache-3
83395000-83396000 r-xs 00000000 08:01 11405621   /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
83396000-83398000 r-xs 00000000 08:01 11415821   /var/cache/fontconfig/b5ea634b0fb353b8ea17632d1f9ef766-le32d4.cache-3
83398000-8339c000 r-xs 00000000 08:01 11415735   /var/cache/fontconfig/926e794c3d5e5dffcaf2fa83ef8d36c2-le32d4.cache-3
8339c000-8339f000 r-xs 00000000 08:01 11412726   /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
8339f000-833a0000 r-xs 00000000 08:01 11405604   /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
833a0000-833a1000 r-xs 00000000 08:01 11405598   /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
833a1000-833a2000 r-xs 00000000 08:01 11405606   /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
833a2000-833a6000 r-xs 00000000 08:01 11405612   /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
833a6000-833aa000 r-xs 00000000 08:01 11415588   /var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-le32d4.cache-3
833aa000-833b1000 r-xs 00000000 08:01 11413514   /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
833b1000-833bc000 r-xs 00000000 08:01 11414705   /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
833bc000-833bf000 r-xs 00000000 08:01 11405617   /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
833bf000-833c0000 r-xs 00000000 08:01 11415473   /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
833c0000-833e2000 r-xs 00000000 08:01 11414163   /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-3
833e3000-833e6000 r-xp 00000000 08:01 16386715   /usr/lib/libxcb-render-util.so.0.0.0
833e6000-833e7000 r-xp 00002000 08:01 16386715   /usr/lib/libxcb-render-util.so.0.0.0
833e7000-833e8000 rwxp 00003000 08:01 16386715   /usr/lib/libxcb-render-util.so.0.0.0
833e8000-833ec000 r-xp 00000000 08:01 16387080   /usr/lib/libgthread-2.0.so.0.2400.1
833ec000-833ed000 r-xp 00003000 08:01 16387080   /usr/lib/libgthread-2.0.so.0.2400.1
833ed000-833ee000 rwxp 00004000 08:01 16387080   /usr/lib/libgthread-2.0.so.0.2400.1
833ee000-833f1000 r-xp 00000000 08:01 16387079   /usr/lib/libgmodule-2.0.so.0.2400.1
833f1000-833f2000 r-xp 00002000 08:01 16387079   /usr/lib/libgmodule-2.0.so.0.2400.1
833f2000-833f3000 rwxp 00003000 08:01 16387079   /usr/lib/libgmodule-2.0.so.0.2400.1
833f3000-8340c000 r-xp 00000000 08:01 16386668   /usr/lib/libatk-1.0.so.0.3009.1
8340c000-8340d000 ---p 00019000 08:01 16386668   /usr/lib/libatk-1.0.so.0.3009.1
8340d000-8340e000 r-xp 00019000 08:01 16386668   /usr/lib/libatk-1.0.so.0.3009.1
8340e000-8340f000 rwxp 0001a000 08:01 16386668   /usr/lib/libatk-1.0.so.0.3009.1
8340f000-83411000 r-xp 00000000 08:01 16385726   /usr/lib/libXdamage.so.1.1.0
83411000-83412000 r-xp 00001000 08:01 16385726   /usr/lib/libXdamage.so.1.1.0
83412000-83413000 rwxp 00002000 08:01 16385726   /usr/lib/libXdamage.so.1.1.0
83413000-83415000 r-xp 00000000 08:01 16385722   /usr/lib/libXcomposite.so.1.0.0
83415000-83416000 r-xp 00001000 08:01 16385722   /usr/lib/libXcomposite.so.1.0.0
83416000-83417000 rwxp 00002000 08:01 16385722   /usr/lib/libXcomposite.so.1.0.0
83417000-83421000 r-xp 00000000 08:01 16386761   /usr/lib/libpangocairo-1.0.so.0.2800.0
83421000-83422000 r-xp 00009000 08:01 16386761   /usr/lib/libpangocairo-1.0.so.0.2800.0
83422000-83423000 rwxp 0000a000 08:01 16386761   /usr/lib/libpangocairo-1.0.so.0.2800.0
83423000-8343b000 r-xp 00000000 08:01 16389592   /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
8343b000-8343c000 r-xp 00017000 08:01 16389592   /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
8343c000-8343d000 rwxp 00018000 08:01 16389592   /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
8343d000-83443000 r-xp 00000000 08:01 16385750   /usr/lib/libXrandr.so.2.2.0
83443000-83444000 r-xp 00005000 08:01 16385750   /usr/lib/libXrandr.so.2.2.0
83444000-83445000 rwxp 00006000 08:01 16385750   /usr/lib/libXrandr.so.2.2.0
83445000-83447000 r-xp 00000000 08:01 16385740   /usr/lib/libXinerama.so.1.0.0
83447000-83448000 r-xp 00001000 08:01 16385740   /usr/lib/libXinerama.so.1.0.0
83448000-83449000 rwxp 00002000 08:01 16385740   /usr/lib/libXinerama.so.1.0.0
83449000-8344c000 ---p 00000000 00:00 0 
8344c000-8349a000 rwxp 00000000 00:00 0 
8349a000-834a2000 r-xp 00000000 08:01 16385752   /usr/lib/libXrender.so.1.3.0
834a2000-834a3000 r-xp 00007000 08:01 16385752   /usr/lib/libXrender.so.1.3.0
834a3000-834a4000 rwxp 00008000 08:01 16385752   /usr/lib/libXrender.so.1.3.0
834a4000-834ac000 r-xp 00000000 08:01 16385724   /usr/lib/libXcursor.so.1.0.2
834ac000-834ad000 r-xp 00007000 08:01 16385724   /usr/lib/libXcursor.so.1.0.2
834ad000-834ae000 rwxp 00008000 08:01 16385724   /usr/lib/libXcursor.so.1.0.2
834ae000-834b3000 r-xp 00000000 08:01 16386448   /usr/lib/libogg.so.0.6.0
834b3000-834b4000 r-xp 00004000 08:01 16386448   /usr/lib/libogg.so.0.6.0
834b4000-834b5000 rwxp 00005000 08:01 16386448   /usr/lib/libogg.so.0.6.0
834b5000-834b9000 r-xp 00000000 08:01 16389931   /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
834b9000-834ba000 ---p 00004000 08:01 16389931   /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
834ba000-834bb000 r-xp 00004000 08:01 16389931   /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
834bb000-834bc000 rwxp 00005000 08:01 16389931   /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
834bc000-834bd000 r-xp 00000000 08:01 16390371   /usr/lib/locale/en_US.utf8/LC_NUMERIC
834bd000-834be000 r-xp 00000000 08:01 16393068   /usr/lib/locale/en_US.utf8/LC_TIME
834be000-834bf000 r-xp 00000000 08:01 16393069   /usr/lib/locale/en_US.utf8/LC_MONETARY
834bf000-834c0000 r-xp 00000000 08:01 16393070   /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
834c0000-834c1000 r-xp 00000000 08:01 16390814   /usr/lib/locale/en_US.utf8/LC_PAPER
834c1000-834c2000 r-xp 00000000 08:01 16390422   /usr/lib/locale/en_US.utf8/LC_NAME
834c2000-834c3000 r-xp 00000000 08:01 16393071   /usr/lib/locale/en_US.utf8/LC_ADDRESS
834c3000-834c4000 r-xp 00000000 08:01 16393072   /usr/lib/locale/en_US.utf8/LC_TELEPHONE
834c4000-834c7000 ---p 00000000 00:00 0 
834c7000-83515000 rwxp 00000000 00:00 0 
83515000-8358e000 r-xp 00000000 08:01 23462672   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libfontmanager.so
8358e000-83598000 rwxp 00078000 08:01 23462672   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libfontmanager.so
83598000-8359d000 rwxp 00000000 00:00 0 
8359d000-835b5000 r-xp 00000000 08:01 16386719   /usr/lib/libxcb.so.1.1.0
835b5000-835b6000 r-xp 00017000 08:01 16386719   /usr/lib/libxcb.so.1.1.0
835b6000-835b7000 rwxp 00018000 08:01 16386719   /usr/lib/libxcb.so.1.1.0
835b7000-835c3000 r-xp 00000000 08:01 16385738   /usr/lib/libXi.so.6.1.0
835c3000-835c4000 r-xp 0000c000 08:01 16385738   /usr/lib/libXi.so.6.1.0
835c4000-835c5000 rwxp 0000d000 08:01 16385738   /usr/lib/libXi.so.6.1.0
835c5000-836de000 r-xp 00000000 08:01 16385713   /usr/lib/libX11.so.6.3.0
836de000-836df000 r-xp 00118000 08:01 16385713   /usr/lib/libX11.so.6.3.0
836df000-836e1000 rwxp 00119000 08:01 16385713   /usr/lib/libX11.so.6.3.0
836e1000-836e2000 rwxp 00000000 00:00 0 
836e2000-836f0000 r-xp 00000000 08:01 16385730   /usr/lib/libXext.so.6.4.0
836f0000-836f1000 r-xp 0000d000 08:01 16385730   /usr/lib/libXext.so.6.4.0
836f1000-836f2000 rwxp 0000e000 08:01 16385730   /usr/lib/libXext.so.6.4.0
836f2000-836f6000 r-xp 00000000 08:01 16385732   /usr/lib/libXfixes.so.3.1.0
836f6000-836f7000 r-xp 00003000 08:01 16385732   /usr/lib/libXfixes.so.3.1.0
836f7000-836f8000 rwxp 00004000 08:01 16385732   /usr/lib/libXfixes.so.3.1.0
836f8000-83700000 r-xs 00000000 08:01 11405616   /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
83700000-83708000 r-xs 00000000 08:01 11412576   /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
83708000-8374b000 r-xp 00000000 08:01 23462669   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/xawt/libmawt.so
8374b000-8374d000 rwxp 00043000 08:01 23462669   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/xawt/libmawt.so
8374d000-8374e000 rwxp 00000000 00:00 0 
8374e000-837d3000 r-xp 00000000 08:01 23462667   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libawt.so
837d3000-837da000 rwxp 00085000 08:01 23462667   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libawt.so
837da000-837fe000 rwxp 00000000 00:00 0 
837fe000-837ff000 ---p 00000000 00:00 0 
837ff000-8387f000 rwxp 00000000 00:00 0 
8387f000-83882000 ---p 00000000 00:00 0 
83882000-83900000 rwxp 00000000 00:00 0 
83900000-83a00000 rwxp 00000000 00:00 0 
83a00000-83a03000 r-xs 00000000 08:01 11415001   /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
83a03000-83a07000 r-xp 00000000 08:01 16385728   /usr/lib/libXdmcp.so.6.0.0
83a07000-83a08000 r-xp 00003000 08:01 16385728   /usr/lib/libXdmcp.so.6.0.0
83a08000-83a09000 rwxp 00004000 08:01 16385728   /usr/lib/libXdmcp.so.6.0.0
83a09000-83a0c000 ---p 00000000 00:00 0 
83a0c000-83a5a000 rwxp 00000000 00:00 0 
83a5a000-83a5d000 ---p 00000000 00:00 0 
83a5d000-83adb000 rwxp 00000000 00:00 0 
83adb000-83ade000 ---p 00000000 00:00 0 
83ade000-83b2c000 rwxp 00000000 00:00 0 
83b2c000-83b6b000 r-xp 00000000 08:01 16390366   /usr/lib/locale/en_US.utf8/LC_CTYPE
83b6b000-83b6e000 ---p 00000000 00:00 0 
83b6e000-83bbc000 rwxp 00000000 00:00 0 
83bbc000-83bbf000 ---p 00000000 00:00 0 
83bbf000-83c0d000 rwxp 00000000 00:00 0 
83c0d000-83c0e000 ---p 00000000 00:00 0 
83c0e000-83cc2000 rwxp 00000000 00:00 0 
83cc2000-83e5a000 r-xs 03029000 08:01 23462811   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/rt.jar
83e5a000-83e5b000 ---p 00000000 00:00 0 
83e5b000-83edb000 rwxp 00000000 00:00 0 
83edb000-83edc000 ---p 00000000 00:00 0 
83edc000-83f64000 rwxp 00000000 00:00 0 
83f64000-83f7c000 rwxp 00000000 00:00 0 
83f7c000-83f8b000 rwxp 00000000 00:00 0 
83f8b000-84064000 rwxp 00000000 00:00 0 
84064000-8406c000 rwxp 00000000 00:00 0 
8406c000-84084000 rwxp 00000000 00:00 0 
84084000-84093000 rwxp 00000000 00:00 0 
84093000-8416b000 rwxp 00000000 00:00 0 
8416b000-84173000 rwxp 00000000 00:00 0 
84173000-841df000 rwxp 00000000 00:00 0 
841df000-851e0000 rwxp 00000000 00:00 0 
851e0000-881e0000 rwxp 00000000 00:00 0 
881e0000-89ec0000 rwxp 00000000 00:00 0 
89ec0000-a5090000 rwxp 00000000 00:00 0 
a5090000-a5f00000 rwxp 00000000 00:00 0 
a5f00000-b37e0000 rwxp 00000000 00:00 0 
b37e0000-b37e1000 r-xp 00000000 08:01 16390355   /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b37e1000-b37e5000 r-xp 00000000 08:01 16385758   /usr/lib/libXtst.so.6.1.0
b37e5000-b37e6000 r-xp 00003000 08:01 16385758   /usr/lib/libXtst.so.6.1.0
b37e6000-b37e7000 rwxp 00004000 08:01 16385758   /usr/lib/libXtst.so.6.1.0
b37e7000-b37f0000 rwxp 00000000 00:00 0 
b37f0000-b38a7000 rwxp 00000000 00:00 0 
b38a7000-b3ae7000 rwxp 00000000 00:00 0 
b3ae7000-b68a7000 rwxp 00000000 00:00 0 
b68a7000-b68b6000 r-xp 00000000 08:01 23462652   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libzip.so
b68b6000-b68b8000 rwxp 0000e000 08:01 23462652   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libzip.so
b68b8000-b68c2000 r-xp 00000000 08:01 19792548   /lib/tls/i686/cmov/libnss_files-2.11.1.so
b68c2000-b68c3000 r-xp 00009000 08:01 19792548   /lib/tls/i686/cmov/libnss_files-2.11.1.so
b68c3000-b68c4000 rwxp 0000a000 08:01 19792548   /lib/tls/i686/cmov/libnss_files-2.11.1.so
b68c4000-b68cc000 r-xp 00000000 08:01 19795974   /lib/tls/i686/cmov/libnss_nis-2.11.1.so
b68cc000-b68cd000 r-xp 00007000 08:01 19795974   /lib/tls/i686/cmov/libnss_nis-2.11.1.so
b68cd000-b68ce000 rwxp 00008000 08:01 19795974   /lib/tls/i686/cmov/libnss_nis-2.11.1.so
b68ce000-b68e1000 r-xp 00000000 08:01 19792509   /lib/tls/i686/cmov/libnsl-2.11.1.so
b68e1000-b68e2000 r-xp 00012000 08:01 19792509   /lib/tls/i686/cmov/libnsl-2.11.1.so
b68e2000-b68e3000 rwxp 00013000 08:01 19792509   /lib/tls/i686/cmov/libnsl-2.11.1.so
b68e3000-b68e5000 rwxp 00000000 00:00 0 
b68e5000-b68e6000 r-xp 00000000 08:01 16393073   /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b68e6000-b68e8000 r-xp 00000000 08:01 16385717   /usr/lib/libXau.so.6.0.0
b68e8000-b68e9000 r-xp 00001000 08:01 16385717   /usr/lib/libXau.so.6.0.0
b68e9000-b68ea000 rwxp 00002000 08:01 16385717   /usr/lib/libXau.so.6.0.0
b68ea000-b68ec000 r-xs 00014000 08:01 16909787   /home/darren/Desktop/minecraft.jar
b68ec000-b68f3000 r-xs 00000000 08:01 16388359   /usr/lib/gconv/gconv-modules.cache
b68f3000-b68fb000 rwxs 00000000 08:01 2097284    /tmp/hsperfdata_darren/9692
b68fb000-b691e000 r-xp 00000000 08:01 23462650   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libjava.so
b691e000-b6920000 rwxp 00023000 08:01 23462650   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libjava.so
b6920000-b6927000 r-xp 00000000 08:01 19795979   /lib/tls/i686/cmov/librt-2.11.1.so
b6927000-b6928000 r-xp 00006000 08:01 19795979   /lib/tls/i686/cmov/librt-2.11.1.so
b6928000-b6929000 rwxp 00007000 08:01 19795979   /lib/tls/i686/cmov/librt-2.11.1.so
b6929000-b692c000 ---p 00000000 00:00 0 
b692c000-b697a000 rwxp 00000000 00:00 0 
b697a000-b699e000 r-xp 00000000 08:01 19792507   /lib/tls/i686/cmov/libm-2.11.1.so
b699e000-b699f000 r-xp 00023000 08:01 19792507   /lib/tls/i686/cmov/libm-2.11.1.so
b699f000-b69a0000 rwxp 00024000 08:01 19792507   /lib/tls/i686/cmov/libm-2.11.1.so
b69a0000-b7152000 r-xp 00000000 08:01 23462640   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/server/libjvm.so
b7152000-b71a6000 rwxp 007b1000 08:01 23462640   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/server/libjvm.so
b71a6000-b75c5000 rwxp 00000000 00:00 0 
b75c5000-b7718000 r-xp 00000000 08:01 19792499   /lib/tls/i686/cmov/libc-2.11.1.so
b7718000-b7719000 ---p 00153000 08:01 19792499   /lib/tls/i686/cmov/libc-2.11.1.so
b7719000-b771b000 r-xp 00153000 08:01 19792499   /lib/tls/i686/cmov/libc-2.11.1.so
b771b000-b771c000 rwxp 00155000 08:01 19792499   /lib/tls/i686/cmov/libc-2.11.1.so
b771c000-b771f000 rwxp 00000000 00:00 0 
b771f000-b7721000 r-xp 00000000 08:01 19792506   /lib/tls/i686/cmov/libdl-2.11.1.so
b7721000-b7722000 r-xp 00001000 08:01 19792506   /lib/tls/i686/cmov/libdl-2.11.1.so
b7722000-b7723000 rwxp 00002000 08:01 19792506   /lib/tls/i686/cmov/libdl-2.11.1.so
b7723000-b772a000 r-xp 00000000 08:01 23462651   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/jli/libjli.so
b772a000-b772c000 rwxp 00006000 08:01 23462651   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/jli/libjli.so
b772c000-b772d000 rwxp 00000000 00:00 0 
b772d000-b7742000 r-xp 00000000 08:01 19795977   /lib/tls/i686/cmov/libpthread-2.11.1.so
b7742000-b7743000 r-xp 00014000 08:01 19795977   /lib/tls/i686/cmov/libpthread-2.11.1.so
b7743000-b7744000 rwxp 00015000 08:01 19795977   /lib/tls/i686/cmov/libpthread-2.11.1.so
b7744000-b7746000 rwxp 00000000 00:00 0 
b7746000-b774c000 r-xp 00000000 08:01 19792510   /lib/tls/i686/cmov/libnss_compat-2.11.1.so
b774c000-b774d000 r-xp 00006000 08:01 19792510   /lib/tls/i686/cmov/libnss_compat-2.11.1.so
b774d000-b774e000 rwxp 00007000 08:01 19792510   /lib/tls/i686/cmov/libnss_compat-2.11.1.so
b774e000-b774f000 rwxp 00000000 00:00 0 
b774f000-b7750000 r-xp 00000000 00:00 0 
b7750000-b775b000 r-xp 00000000 08:01 23462649   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libverify.so
b775b000-b775c000 rwxp 0000b000 08:01 23462649   /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/libverify.so
b775c000-b775e000 rwxp 00000000 00:00 0 
b775e000-b775f000 r-xp 00000000 00:00 0          [vdso]
b775f000-b777a000 r-xp 00000000 08:01 19792034   /lib/ld-2.11.1.so
b777a000-b777b000 r-xp 0001a000 08:01 19792034   /lib/ld-2.11.1.so
b777b000-b777c000 rwxp 0001b000 08:01 19792034   /lib/ld-2.11.1.so
bfda0000-bfdb5000 rwxp 00000000 00:00 0          [stack]

VM Arguments:
java_command: /home/darren/Desktop/minecraft.jar
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/home/darren/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=darren
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386/server:/usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/i386:/usr/lib/jvm/java-6-sun-1.6.0.26/jre/../lib/i386
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x725510], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x725510], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x5dff20], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: SIG_IGN, sa_mask[0]=0x00001000, sa_flags=0x10000000
SIGXFSZ: [libjvm.so+0x5dff20], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x5dff20], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x5e3160], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x5e2d40], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x5e2d40], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x5e2d40], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x5e2d40], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:squeeze/sid

uname:Linux 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:54:21 UTC 2011 i686
libc:glibc 2.11.1 NPTL 2.11.1 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:3.04 2.98 2.83

/proc/meminfo:
MemTotal:        2836252 kB
MemFree:          650996 kB
Buffers:          321812 kB
Cached:           840292 kB
SwapCached:            0 kB
Active:          1169348 kB
Inactive:         778680 kB
Active(anon):     585324 kB
Inactive(anon):   213640 kB
Active(file):     584024 kB
Inactive(file):   565040 kB
Unevictable:          44 kB
Mlocked:              16 kB
HighTotal:       1972460 kB
HighFree:         347076 kB
LowTotal:         863792 kB
LowFree:          303920 kB
SwapTotal:       8308728 kB
SwapFree:        8308728 kB
Dirty:               548 kB
Writeback:             0 kB
AnonPages:        785908 kB
Mapped:           148876 kB
Shmem:             12972 kB
Slab:             189472 kB
SReclaimable:     170964 kB
SUnreclaim:        18508 kB
KernelStack:        2584 kB
PageTables:         8676 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     9726852 kB
Committed_AS:    1564416 kB
VmallocTotal:     122880 kB
VmallocUsed:       21808 kB
VmallocChunk:      91652 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       12280 kB
DirectMap4M:      897024 kB


CPU:total 2 (2 cores per cpu, 1 threads per core) family 17 model 3 stepping 1, cmov, cx8, fxsr, mmx, sse, sse2, sse3, mmxext, 3dnow, 3dnowext

/proc/cpuinfo:
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 17
model		: 3
model name	: AMD Turion(tm) X2 Dual-Core Mobile RM-70
stepping	: 1
cpu MHz		: 500.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit
bogomips	: 3999.98
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 17
model		: 3
model name	: AMD Turion(tm) X2 Dual-Core Mobile RM-70
stepping	: 1
cpu MHz		: 500.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit
bogomips	: 3990.40
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate



Memory: 4k page, physical 2836252k(650996k free), swap 8308728k(8308728k free)

vm_info: Java HotSpot(TM) Server VM (20.1-b02) for linux-x86 JRE (1.6.0_26-b03), built on May  4 2011 01:04:10 by "java_re" with gcc 3.2.1-7a (J2SE release)

time: Thu Jul 14 09:09:48 2011
elapsed time: 13 seconds

```

---

### Post by DarrenMR415 on 2011-07-14
Also, I have absolutely no idea what any of this means.

This is the thread that got me to this point, [http://ubuntuforums.org/showthread.php?p=11046514#post11046514](http://ubuntuforums.org/showthread.php?p=11046514#post11046514)

---

### Post by mikejonesey on 2011-07-14
what java are you running; if i were to run something like a game i guess minecraft is, i would be running sun java, download the jdk and set java home to the jre inside...

---

### Post by DarrenMR415 on 2011-07-14
> **mikejonesey said:**
> what java are you running; if i were to run something like a game i guess minecraft is, i would be running sun java, download the jdk and set java home to the jre inside...

I am using sun jave, how do I set java home and the jre inside?  No clue what that means.

---

### Post by mikejonesey on 2011-07-14
probably already set then otherwise you wouldn be able to run; JAVA_HOME is a sys env variable;

echo $JAVA_HOME

if it's not set or uses another jre;

export JAVA_HOME=/usr/lib/sun/jdk1.5.0_22/jre
(my current jdk loc, your will be different...)

if you've installed with update alternatives;

update-alternatives --config java

---

### Post by DarrenMR415 on 2011-07-14
> **mikejonesey said:**
> probably already set then otherwise you wouldn be able to run; JAVA_HOME is a sys env variable;

echo $JAVA_HOME

if it's not set or uses another jre;

export JAVA_HOME=/usr/lib/sun/jdk1.5.0_22/jre
(my current jdk loc, your will be different...)

if you've installed with update alternatives;

update-alternatives --config java

Im trying my best to keep up, but I dont understand most of this.  I put in echo $JAVA_HOME, it returns a blank line, and brings the command line back.

---

### Post by mikejonesey on 2011-07-14
i can't see anything in the log that stikes as obvious; maybee google around the opengl extension... but idk

---

### Post by mikejonesey on 2011-07-14
> **DarrenMR415 said:**
> Im trying my best to keep up, but I dont understand most of this.  I put in echo $JAVA_HOME, it returns a blank line, and brings the command line back.

this means your system enviroment variable JAVA_HOME is not set to set it type;

export JAVA_HOME=(your jre dir here...)

to find your jre dir type;

sudo find / -type d -wholename *jdk*/jre

---

### Post by DarrenMR415 on 2011-07-14
```
darren@darren-laptop:~$ sudo find / -type d -wholename *jdk*/jre
/usr/lib/jvm/java-6-openjdk/jre
```

Do I then put in "export JAVA_HOME=/usr/lib/jvm/java-6-openjdk/jre" ?

---

### Post by mikejonesey on 2011-07-14
that's not a sun jre thats an open jre... you need to download one from sun...

update "oracle" even (bought over sun)...

---

### Post by DarrenMR415 on 2011-07-14
oh.  If I right click on the JAR the default is "Open with Sun Java 6 Runtime", if I go to Open With, then I have the option for "OpenJDK Java 6 runtime"  Both do the same thing when I try to run minecraft.

---

### Post by mikejonesey on 2011-07-14
hmm maybe both must be installed then but you only have the jdk for the open one, if both do the same thing it's probably not a problem with the java but a shared libary it uses eg opengl (graphic rendering)... have no idea how to help sorry...

---

### Post by pbrane on 2011-07-14
I play minecraft on ubuntu lucid. Here is a script that I used to set up sun java. Read the script and follow the comments.

You may have to change paths or file names depending on what you have installed from sun.

I also noticed how you are running minecraft is not correct. try this:
```

java -Xmx1024M -Xms1024M -cp ~/Desktop/minecraft.jar net.minecraft.LauncherFrame

```

Make sure that jar file is the minecraft launcher, and not the minecraft jar itself. It can be found at: [http://www.minecraft.net/download/minecraft.jar?v=1310675565107]("http://www.minecraft.net/download/minecraft.jar?v=1310675565107")

```

#!/bin/bash

# use sun-java instead of openjdk

# 1. Add the Canonical partner repository.
#sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"
# 2. Install Sun Java JRE.
#sudo apt-get update
#sudo apt-get install sun-java6-jre sun-java6-fonts sun-java6-plugin
# 3. Update system defaults to prefer Sun Java over OpenJDK.
sudo update-alternatives --set java /usr/lib/jvm/java-6-sun/jre/bin/java
sudo update-alternatives --set javaws /usr/lib/jvm/java-6-sun/jre/bin/javaws
sudo update-alternatives --set mozilla-javaplugin.so /usr/lib/jvm/java-6-sun/jre/lib/*/libnpjp2.so
# If that fails, manually choose them from a list. Always choose the option containing &#8220;java-6-sun&#8221;.
#sudo update-alternatives --config java
#sudo update-alternatives --config javaws
#sudo update-alternatives --config mozilla-javaplugin.so

```

```

#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x81066ef6, pid=9692, tid=2185231216
#
# JRE version: 6.0_26-b03
# Java VM: Java HotSpot(TM) Server VM (20.1-b02 mixed mode linux-x86 )
# Problematic frame:
# C  [libGL.so.1+0x65ef6]  **XF86DRIQueryExtension+0x8e**
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

```

in your error log the problem shows up as an OpenGL issue. Make sure you have OpenGL installed, i. e., your video card drivers, libMesa, DRI, etc. What graphics card do you have?

---

### Post by DarrenMR415 on 2011-07-14
Youre going to kill me... I uninstalled my graphics drivers, and reinstalled, and it works now. ATI/AMD proprietary drivers.

---

### Post by mikejonesey on 2011-07-14
lol cool

---

### Post by DarrenMR415 on 2011-07-15
Now I cannot adjust my brightness again.

---

