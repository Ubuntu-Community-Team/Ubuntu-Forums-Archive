---
title: "Need Help........  JVM crashes randomly on ubuntu 10.10"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by pals_spry on 2011-01-21
Dear All,


            I am working on Core Java project, where I am using several frames and timer. Whenever I am running my code sometimes it is giving some "JVM crash" error. I dont have much experience in ubuntu. 
I searched its solution on Internet but not able to solve yet.
            I am posting my error here....

# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb775a128, pid=1831, tid=2942770032
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_19-b02 mixed mode, sharing)
# Problematic frame:
# C  [libc.so.6+0x6f128]
#
# An error report file with more information is saved as hs_err_pid1831.log

Contents of hs_err_pid1831.log file :---

#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb775a128, pid=1831, tid=2942770032
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_19-b02 mixed mode, sharing)
# Problematic frame:
# C  [libc.so.6+0x6f128]
#

---------------  T H R E A D  ---------------

Current thread (0x09bbb89:  JavaThread "AWT-EventQueue-0" [_thread_in_native, id=1868]

siginfo:si_signo=11, si_errno=0, si_code=1, si_addr=0x0000000a

Registers:
EAX=0x00000002, EBX=0xb7844ff4, ECX=0x09cc30a8, EDX=0x00000060
ESP=0xaf67045c, EBP=0xaf6704c8, ESI=0xb7846448, EDI=0xb7846448
EIP=0xb775a128, CR2=0x0000000a, EFLAGS=0x00210246

Top of Stack: (sp=0xaf67045c)
0xaf67045c:   af670498 90b66038 00000000 90b65af0
0xaf67046c:   af670494 af6704b8 b78463f8 b7113ae4
0xaf67047c:   00000000 00000005 00000038 00000005
0xaf67048c:   00000024 b7821db0 b78463f8 b7821c7f
0xaf67049c:   b7821f8a 904de406 00000028 00000000
0xaf6704ac:   00000038 b78463c0 00000060 b78463f0
0xaf6704bc:   b7844ff4 b78463c0 00000020 af6704e8
0xaf6704cc:   b775bf33 00000010 00000003 09ccc3c8 

Instructions: (pc=0xb775a12
0xb775a118:   0c 89 75 e4 8b 71 08 3b 4e 0c 0f 85 7d 05 00 00
0xb775a128:   8b 78 08 39 cf 0f 85 72 05 00 00 81 79 04 ff 01 

Stack: [0xaf5f1000,0xaf672000),  sp=0xaf67045c,  free space=509k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [libc.so.6+0x6f128]
C  [libc.so.6+0x70f33]  __libc_malloc+0x63
C  [libxcb.so.1+0xa105]
C  [libxcb.so.1+0x7e2b]
C  [libxcb.so.1+0x9ca2]  xcb_wait_for_reply+0x142
C  [libX11.so.6+0x42016]  _XReply+0xe6
C  [libX11.so.6+0x1fc63]  _XGetWindowAttributes+0xc3
C  [libX11.so.6+0x1fde2]  XGetWindowAttributes+0x42
C  [libX11.so.6+0x6c8e6]
C  [libX11.so.6+0x6baf8]  _XimSetICDefaults+0xd8
C  [libX11.so.6+0x6bb4a]  _XimSetICDefaults+0x12a
C  [libX11.so.6+0x656d2]  _XimLocalCreateIC+0x2b2
C  [libX11.so.6+0x47bc9]  XCreateIC+0x49
C  [libmawt.so+0x18639]
C  [libmawt.so+0x18fc8]  Java_sun_awt_X11_XInputMethod_createXICNative+0xd8
j  sun.awt.X11.XInputMethod.createXICNative(J)Z+0
j  sun.awt.X11.XInputMethod.createXIC()Z+23
j  sun.awt.X11InputMethod.activate()V+74
j  sun.awt.im.InputContext.activateInputMethod(Z)V+169
j  sun.awt.im.InputContext.focusGained(Ljava/awt/ComponentV+129
j  sun.awt.im.InputContext.dispatchEvent(Ljava/awt/AWTEventV+100
j  sun.awt.im.InputMethodContext.dispatchEvent(Ljava/awt/AWTEventV+58
j  java.awt.Component.dispatchEventImpl(Ljava/awt/AWTEventV+294
j  java.awt.Container.dispatchEventImpl(Ljava/awt/AWTEventV+42
j  java.awt.Window.dispatchEventImpl(Ljava/awt/AWTEventV+19
j  java.awt.Component.dispatchEvent(Ljava/awt/AWTEventV+2
j  java.awt.KeyboardFocusManager.redispatchEvent(Ljava/awt/Component;Ljava/awt/AWTEventV+7
j  java.awt.DefaultKeyboardFocusManager.typeAheadAssertions(Ljava/awt/Component;Ljava/awt/AWTEventZ+304
j  java.awt.DefaultKeyboardFocusManager.dispatchEvent(Ljava/awt/AWTEventZ+918
j  java.awt.Component.dispatchEventImpl(Ljava/awt/AWTEventV+103
j  java.awt.Container.dispatchEventImpl(Ljava/awt/AWTEventV+42
j  java.awt.Window.dispatchEventImpl(Ljava/awt/AWTEventV+19
j  java.awt.Component.dispatchEvent(Ljava/awt/AWTEventV+2
j  sun.awt.X11.XWindow$1.run()V+61
j  java.awt.event.InvocationEvent.dispatch()V+47
j  java.awt.EventQueue.dispatchEvent(Ljava/awt/AWTEventV+26
j  java.awt.EventDispatchThread.pumpOneEventForHierarchy(ILjava/awt/ComponentZ+233
j  java.awt.EventDispatchThread.pumpEventsForHierarchy(ILjava/awt/Conditional;Ljava/awt/ComponentV+26
j  java.awt.EventDispatchThread.pumpEvents(ILjava/awt/ConditionalV+4
j  java.awt.EventDispatchThread.pumpEvents(Ljava/awt/ConditionalV+3
j  java.awt.EventDispatchThread.run()V+9
v  ~StubRoutines::call_stub
V  [libjvm.so+0x17b99c]
V  [libjvm.so+0x2906d8]
V  [libjvm.so+0x17b1f5]
V  [libjvm.so+0x17b28e]
V  [libjvm.so+0x1f31f5]
V  [libjvm.so+0x2fa333]
V  [libjvm.so+0x2912e8]
C  [libpthread.so.0+0x5cc9]

Java frames: (J=compiled Java code, j=interpreted, Vv=VM code)
j  sun.awt.X11.XInputMethod.createXICNative(J)Z+0
j  sun.awt.X11.XInputMethod.createXIC()Z+23
j  sun.awt.X11InputMethod.activate()V+74
j  sun.awt.im.InputContext.activateInputMethod(Z)V+169
j  sun.awt.im.InputContext.focusGained(Ljava/awt/ComponentV+129
j  sun.awt.im.InputContext.dispatchEvent(Ljava/awt/AWTEventV+100
j  sun.awt.im.InputMethodContext.dispatchEvent(Ljava/awt/AWTEventV+58
j  java.awt.Component.dispatchEventImpl(Ljava/awt/AWTEventV+294
j  java.awt.Container.dispatchEventImpl(Ljava/awt/AWTEventV+42
j  java.awt.Window.dispatchEventImpl(Ljava/awt/AWTEventV+19
j  java.awt.Component.dispatchEvent(Ljava/awt/AWTEventV+2
j  java.awt.KeyboardFocusManager.redispatchEvent(Ljava/awt/Component;Ljava/awt/AWTEventV+7
j  java.awt.DefaultKeyboardFocusManager.typeAheadAssertions(Ljava/awt/Component;Ljava/awt/AWTEventZ+304
j  java.awt.DefaultKeyboardFocusManager.dispatchEvent(Ljava/awt/AWTEventZ+918
j  java.awt.Component.dispatchEventImpl(Ljava/awt/AWTEventV+103
j  java.awt.Container.dispatchEventImpl(Ljava/awt/AWTEventV+42
j  java.awt.Window.dispatchEventImpl(Ljava/awt/AWTEventV+19
j  java.awt.Component.dispatchEvent(Ljava/awt/AWTEventV+2
j  sun.awt.X11.XWindow$1.run()V+61
j  java.awt.event.InvocationEvent.dispatch()V+47
j  java.awt.EventQueue.dispatchEvent(Ljava/awt/AWTEventV+26
j  java.awt.EventDispatchThread.pumpOneEventForHierarchy(ILjava/awt/ComponentZ+233
j  java.awt.EventDispatchThread.pumpEventsForHierarchy(ILjava/awt/Conditional;Ljava/awt/ComponentV+26
j  java.awt.EventDispatchThread.pumpEvents(ILjava/awt/ConditionalV+4
j  java.awt.EventDispatchThread.pumpEvents(Ljava/awt/ConditionalV+3
j  java.awt.EventDispatchThread.run()V+9
v  ~StubRoutines::call_stub

---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
=>0x09bbb898 JavaThread "AWT-EventQueue-0" [_thread_in_native, id=1868]
  0x09ca8a60 JavaThread "Thread-6" [_thread_in_native, id=1865]
  0x09cc2c98 JavaThread "Image Fetcher 0" daemon [_thread_blocked, id=1862]
  0x09dc4ca8 JavaThread "MySQL Statement Cancellation Timer" daemon [_thread_blocked, id=1845]
  0xafb009f8 JavaThread "DestroyJavaVM" [_thread_blocked, id=1831]
  0xafb004e0 JavaThread "TimerQueue" daemon [_thread_blocked, id=1844]
  0x09cef318 JavaThread "AWT-Shutdown" [_thread_blocked, id=1842]
  0x09ce5d70 JavaThread "AWT-XAWT" daemon [_thread_blocked, id=1840]
  0x09ccb558 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=1839]
  0x09b78438 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=1837]
  0x09b76fb8 JavaThread "CompilerThread0" daemon [_thread_blocked, id=1836]
  0x09b76020 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=1835]
  0x09b6f6f0 JavaThread "Finalizer" daemon [_thread_blocked, id=1834]
  0x09b6ea68 JavaThread "Reference Handler" daemon [_thread_blocked, id=1833]

Other Threads:
  0x09b6d5f8 VMThread [id=1832]
  0x09b799a8 WatcherThread [id=1838]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 def new generation   total 106368K, used 38427K [0x2e650000, 0x359b0000, 0x359b0000)
  eden space 94592K,  40% used [0x2e650000, 0x30bd6dd0, 0x342b0000)
  from space 11776K,   0% used [0x342b0000, 0x342b0000, 0x34e30000)
  to   space 11776K,   0% used [0x34e30000, 0x34e30000, 0x359b0000)
 tenured generation   total 1417856K, used 0K [0x359b0000, 0x8c250000, 0x8c250000)
   the space 1417856K,   0% used [0x359b0000, 0x359b0000, 0x359b0200, 0x8c250000)
 compacting perm gen  total 8192K, used 2375K [0x8c250000, 0x8ca50000, 0x90250000)
   the space 8192K,  28% used [0x8c250000, 0x8c4a1c08, 0x8c4a1e00, 0x8ca50000)
    ro space 8192K,  68% used [0x90250000, 0x907d4540, 0x907d4600, 0x90a50000)
    rw space 12288K,  48% used [0x90a50000, 0x910223d8, 0x91022400, 0x91650000)

Dynamic libraries:
08048000-08057000 r-xp 00000000 08:01 531226     /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/bin/java
08057000-08059000 rwxp 0000e000 08:01 531226     /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/bin/java
09b2b000-09e59000 rwxp 00000000 00:00 0          [heap]
2e650000-8ca50000 rwxp 00000000 00:00 0 
8ca50000-90250000 rwxp 00000000 00:00 0 
90250000-907d5000 r-xs 00001000 08:01 531573     /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/i386/client/classes.jsa
907d5000-90a50000 rwxp 00000000 00:00 0 
90a50000-91023000 rwxp 00586000 08:01 531573     /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/i386/client/classes.jsa
91023000-91650000 rwxp 00000000 00:00 0 
91650000-91721000 rwxp 00b59000 08:01 531573     /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/i386/client/classes.jsa
91721000-91a50000 rwxp 00000000 00:00 0 
91a50000-91a54000 r-xs 00c2a000 08:01 531573     /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/i386/client/classes.jsa
91a54000-91e50000 rwxp 00000000 00:00 0 
af3a7000-af463000 rwxs 00000000 00:04 1114125    /SYSV00000000 (deleted)
af4ef000-af4f2000 rwxp 00000000 00:00 0 
af4f2000-af570000 rwxp 00000000 00:00 0 
af570000-af573000 ---p 00000000 00:00 0 
af573000-af5f1000 rwxp 00000000 00:00 0 
af5f1000-af5f4000 ---p 00000000 00:00 0 
af5f4000-af672000 rwxp 00000000 00:00 0 
af672000-af675000 rwxp 00000000 00:00 0 
af675000-af6f3000 rwxp 00000000 00:00 0 
af6f3000-af71a000 r-xp 00000000 08:01 531278     /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/i386/libjpeg.so
af71a000-af71b000 rwxp 00026000 08:01 531278     /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/i386/libjpeg.so
af71b000-af721000 r-xp 00000000 08:01 4463268    /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/ext/libLinuxSerialParallel.so
af721000-af722000 rwxp 00005000 08:01 4463268    /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/ext/libLinuxSerialParallel.so
af722000-af725000 ---p 00000000 00:00 0 
af725000-af7a3000 rwxp 00000000 00:00 0 
af7a3000-af7a6000 ---p 00000000 00:00 0 
af7a6000-af824000 rwxp 00000000 00:00 0 
af864000-af86d000 r-xs 00000000 08:01 396759     /usr/share/fonts/X11/Type1/c0648bt_.pfb
af86d000-af886000 r-xs 00000000 08:01 397394     /usr/share/fonts/type1/gsfonts/b018012l.pfb
af886000-af89f000 r-xs 00000000 08:01 397448     /usr/share/fonts/type1/gsfonts/n021004l.pfb
af89f000-af8ba000 r-xs 00000000 08:01 397472     /usr/share/fonts/type1/gsfonts/p052004l.pfb
af8ba000-af8c4000 r-xs 00000000 08:01 396751     /usr/share/fonts/X11/Type1/c0583bt_.pfb
af8c4000-af8dd000 r-xs 00000000 08:01 397460     /usr/share/fonts/type1/gsfonts/n022004l.pfb
af8dd000-af8ee000 r-xs 00000000 08:01 397430     /usr/share/fonts/type1/gsfonts/n019024l.pfb
af8ee000-af905000 r-xs 00000000 08:01 397451     /usr/share/fonts/type1/gsfonts/n021023l.pfb
af905000-af915000 r-xs 00000000 08:01 397385     /usr/share/fonts/type1/gsfonts/a010015l.pfb
af915000-af930000 r-xs 00000000 08:01 397409     /usr/share/fonts/type1/gsfonts/c059016l.pfb
af930000-af941000 r-xs 00000000 08:01 397439     /usr/share/fonts/type1/gsfonts/n019063l.pfb
af941000-af95c000 r-xs 00000000 08:01 397475     /usr/share/fonts/type1/gsfonts/p052023l.pfb
af95c000-af965000 r-xs 00000000 08:01 396757     /usr/share/fonts/X11/Type1/c0633bt_.pfb
af965000-af96f000 r-xs 00000000 08:01 397487     /usr/share/fonts/type1/mathml/Symbol.pfb
af96f000-af979000 r-xs 00000000 08:01 396753     /usr/share/fonts/X11/Type1/c0611bt_.pfb
af979000-af991000 r-xs 00000000 08:01 397457     /usr/share/fonts/type1/gsfonts/n022003l.pfb
af991000-af9a5000 r-xs 00000000 08:01 397421     /usr/share/fonts/type1/gsfonts/n019003l.pfb
af9a5000-af9af000 r-xs 00000000 08:01 396747     /usr/share/fonts/X11/Type1/c0419bt_.pfb
af9af000-af9bf000 r-xs 00000000 08:01 397382     /usr/share/fonts/type1/gsfonts/a010013l.pfb
af9bf000-af9cf000 r-xs 00000000 08:01 397388     /usr/share/fonts/type1/gsfonts/a010033l.pfb
af9cf000-af9e6000 r-xs 00000000 08:01 397484     /usr/share/fonts/type1/gsfonts/z003034l.pfb
af9e6000-af9fb000 r-xs 00000000 08:01 397400     /usr/share/fonts/type1/gsfonts/b018032l.pfb
af9fb000-afa17000 r-xs 00000000 08:01 397478     /usr/share/fonts/type1/gsfonts/p052024l.pfb
afa17000-afa20000 r-xs 00000000 08:01 397481     /usr/share/fonts/type1/gsfonts/s050000l.pfb
afa20000-afa31000 r-xs 00000000 08:01 397427     /usr/share/fonts/type1/gsfonts/n019023l.pfb
afa31000-afa43000 r-xs 00000000 08:01 397433     /usr/share/fonts/type1/gsfonts/n019043l.pfb
afa43000-afa59000 r-xs 00000000 08:01 397454     /usr/share/fonts/type1/gsfonts/n021024l.pfb
afa59000-afa6f000 r-xs 00000000 08:01 397463     /usr/share/fonts/type1/gsfonts/n022023l.pfb
afa6f000-afa89000 r-xs 00000000 08:01 397406     /usr/share/fonts/type1/gsfonts/c059013l.pfb
afa89000-afa9b000 r-xs 00000000 08:01 397403     /usr/share/fonts/type1/gsfonts/b018035l.pfb
afa9b000-afaad000 r-xs 00000000 08:01 397436     /usr/share/fonts/type1/gsfonts/n019044l.pfb
afaad000-afac6000 r-xs 00000000 08:01 397445     /usr/share/fonts/type1/gsfonts/n021003l.pfb
afac6000-afad2000 r-xs 00000000 08:01 397418     /usr/share/fonts/type1/gsfonts/d050000l.pfb
afad2000-afae5000 r-xs 00000000 08:01 397442     /usr/share/fonts/type1/gsfonts/n019064l.pfb
afae5000-afb00000 r-xs 00000000 08:01 397469     /usr/share/fonts/type1/gsfonts/p052003l.pfb
afb00000-afb21000 rwxp 00000000 00:00 0 
afb21000-afc00000 ---p 00000000 00:00 0 
afc02000-afc09000 r-xs 00000000 08:01 4331755    /usr/lib/gconv/gconv-modules.cache
afc09000-afc12000 r-xs 00000000 08:01 396761     /usr/share/fonts/X11/Type1/c0649bt_.pfb
afc12000-afc1c000 r-xs 00000000 08:01 396749     /usr/share/fonts/X11/Type1/c0582bt_.pfb
afc1c000-afc32000 r-xs 00000000 08:01 397466     /usr/share/fonts/type1/gsfonts/n022024l.pfb
afc32000-afc3b000 r-xs 00000000 08:01 396755     /usr/share/fonts/X11/Type1/c0632bt_.pfb
afc3b000-afc4e000 r-xs 00000000 08:01 397397     /usr/share/fonts/type1/gsfonts/b018015l.pfb
afc4e000-afc5f000 r-xs 00000000 08:01 397391     /usr/share/fonts/type1/gsfonts/a010035l.pfb
afc5f000-afc71000 r-xs 00000000 08:01 397424     /usr/share/fonts/type1/gsfonts/n019004l.pfb
afc71000-afc89000 r-xs 00000000 08:01 397412     /usr/share/fonts/type1/gsfonts/c059033l.pfb
afc89000-afca1000 r-xs 00000000 08:01 397415     /usr/share/fonts/type1/gsfonts/c059036l.pfb
afca1000-afcb3000 r-xp 00000000 08:01 531260     /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/i386/libnet.so
afcb3000-afcb4000 rwxp 00011000 08:01 531260     /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/i386/libnet.so
afcb4000-afcb7000 rwxp 00000000 00:00 0 
afcb7000-afd35000 rwxp 00000000 00:00 0 
afd35000-afd38000 ---p 00000000 00:00 0 
afd38000-afdb6000 rwxp 00000000 00:00 0 
afdb6000-afdb9000 ---p 00000000 00:00 0 
afdb9000-afe37000 rwxp 00000000 00:00 0 
afe37000-afe3a000 ---p 00000000 00:00 0 
afe3a000-afeb8000 rwxp 00000000 00:00 0 
afeb8000-afebc000 r-xp 00000000 08:01 4328208    /usr/lib/libXfixes.so.3.1.0
afebc000-afebd000 r-xp 00003000 08:01 4328208    /usr/lib/libXfixes.so.3.1.0
afebd000-afebe000 rwxp 00004000 08:01 4328208    /usr/lib/libXfixes.so.3.1.0
afebe000-afec6000 r-xp 00000000 08:01 4328228    /usr/lib/libXrender.so.1.3.0
afec6000-afec7000 r-xp 00007000 08:01 4328228    /usr/lib/libXrender.so.1.3.0
afec7000-afec8000 rwxp 00008000 08:01 4328228    /usr/lib/libXrender.so.1.3.0
afec8000-afed0000 r-xp 00000000 08:01 4328200    /usr/lib/libXcursor.so.1.0.2
afed0000-afed1000 r-xp 00007000 08:01 4328200    /usr/lib/libXcursor.so.1.0.2
afed1000-afed2000 rwxp 00008000 08:01 4328200    /usr/lib/libXcursor.so.1.0.2
afed2000-afed5000 ---p 00000000 00:00 0 
afed5000-aff53000 rwxp 00000000 00:00 0 
aff53000-affcd000 r-xp 00000000 08:01 531277     /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/i386/libfontmanager.so
affcd000-affd7000 rwxp 0007a000 08:01 531277     /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/i386/libfontmanager.so
affd7000-affdb000 rwxp 00000000 00:00 0 
affdb000-affdf000 r-xp 00000000 08:01 4328204    /usr/lib/libXdmcp.so.6.0.0
affdf000-affe0000 r-xp 00003000 08:01 4328204    /usr/lib/libXdmcp.so.6.0.0
affe0000-affe1000 rwxp 00004000 08:01 4328204    /usr/lib/libXdmcp.so.6.0.0
affe1000-affe3000 r-xp 00000000 08:01 4328193    /usr/lib/libXau.so.6.0.0
affe3000-affe4000 r-xp 00001000 08:01 4328193    /usr/lib/libXau.so.6.0.0
affe4000-affe5000 rwxp 00002000 08:01 4328193    /usr/lib/libXau.so.6.0.0
affe5000-afffd000 r-xp 00000000 08:01 4329155    /usr/lib/libxcb.so.1.1.0
afffd000-afffe000 r-xp 00017000 08:01 4329155    /usr/lib/libxcb.so.1.1.0
afffe000-affff000 rwxp 00018000 08:01 4329155    /usr/lib/libxcb.so.1.1.0
affff000-b0118000 r-xp 00000000 08:01 4328189    /usr/lib/libX11.so.6.3.0
b0118000-b0119000 r-xp 00118000 08:01 4328189    /usr/lib/libX11.so.6.3.0
b0119000-b011b000 rwxp 00119000 08:01 4328189    /usr/lib/libX11.so.6.3.0
b011b000-b011c000 rwxp 00000000 00:00 0 
b011c000-b012a000 r-xp 00000000 08:01 4328206    /usr/lib/libXext.so.6.4.0
b012a000-b012b000 r-xp 0000d000 08:01 4328206    /usr/lib/libXext.so.6.4.0
b012b000-b012c000 rwxp 0000e000 08:01 4328206    /usr/lib/libXext.so.6.4.0
b0131000-b0138000 r-xp 00000000 08:01 531261     /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/i386/libnio.so
b0138000-b0139000 rwxp 00006000 08:01 531261     /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/i386/libnio.so
b0139000-b0167000 r-xp 00000000 08:01 531272     /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/i386/xawt/libmawt.so
b0167000-b016b000 rwxp 0002d000 08:01 531272     /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/i386/xawt/libmawt.so
b016b000-b0231000 r-xp 00000000 08:01 531267     /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/i386/libmlib_image.so
b0231000-b0232000 rwxp 000c5000 08:01 531267     /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/i386/libmlib_image.so
b0232000-b0291000 r-xp 00000000 08:01 531268     /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/i386/libawt.so
b0291000-b0297000 rwxp 0005f000 08:01 531268     /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/i386/libawt.so
b0297000-b02bb000 rwxp 00000000 00:00 0 
b02bb000-b02c9000 r-xs 00000000 08:01 2360029    /root/Desktop/DQMS_FD_Test.jar
b02c9000-b0329000 r-xs 00000000 08:01 2359854    /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/ext/log4j-1.2.15.jar
b0329000-b0338000 r-xs 00000000 08:01 4337241    /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/ext/commtest.jar
b0338000-b0363000 r-xs 00000000 08:01 4463171    /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/ext/sunpkcs11.jar
b0363000-b0f4e000 r-xs 00000000 08:01 2359484    /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/ext/tools.jar
b0f4e000-b0f5d000 r-xs 00000000 08:01 2359849    /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/ext/RXTXcomm.jar
b0f5d000-b101a000 r-xs 00000000 08:01 4463262    /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/ext/javax.jar
b101a000-b101d000 r-xs 00000000 08:01 4463167    /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/ext/dnsns.jar
b101d000-b10e3000 r-xs 00000000 08:01 4463168    /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/ext/localedata.jar
b10e3000-b1167000 r-xs 00000000 08:01 2359853    /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/ext/mysql-connector-java-5.0.7-bin.jar
b1167000-b118e000 r-xs 00000000 08:01 4463166    /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/ext/sunjce_provider.jar
b118e000-b12ad000 r-xs 00000000 08:01 4337242    /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/ext/ojdbc14.jar
b12ad000-b12ca000 r-xs 00000000 08:01 4337240    /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/ext/comm.jar
b12ca000-b12d8000 r-xs 00000000 08:01 2360029    /root/Desktop/DQMS_FD_Test.jar
b12d8000-b12d9000 ---p 00000000 00:00 0 
b12d9000-b1359000 rwxp 00000000 00:00 0 
b1359000-b135c000 ---p 00000000 00:00 0 
b135c000-b13da000 rwxp 00000000 00:00 0 
b13da000-b13dd000 ---p 00000000 00:00 0 
b13dd000-b145b000 rwxp 00000000 00:00 0 
b145b000-b145e000 ---p 00000000 00:00 0 
b145e000-b14dc000 rwxp 00000000 00:00 0 
b14dc000-b16dc000 r-xp 00000000 08:01 4332645    /usr/lib/locale/locale-archive
b16dc000-b16df000 ---p 00000000 00:00 0 
b16df000-b175d000 rwxp 00000000 00:00 0 
b175d000-b1760000 ---p 00000000 00:00 0 
b1760000-b17de000 rwxp 00000000 00:00 0 
b17de000-b17df000 ---p 00000000 00:00 0 
b17df000-b186b000 rwxp 00000000 00:00 0 
b186b000-b1887000 rwxp 00000000 00:00 0 
b1887000-b1e2e000 rwxp 00000000 00:00 0 
b1e2e000-b1e4a000 rwxp 00000000 00:00 0 
b1e4a000-b1e5a000 rwxp 00000000 00:00 0 
b1e5a000-b1ed5000 rwxp 00000000 00:00 0 
b1ed5000-b1ffd000 rwxp 00000000 00:00 0 
b1ffd000-b3ed5000 rwxp 00000000 00:00 0 
b3ed5000-b473b000 r-xs 00000000 08:01 4463170    /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/charsets.jar
b473b000-b4750000 r-xs 00000000 08:01 4463169    /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/jce.jar
b4750000-b47d5000 r-xs 00000000 08:01 4463164    /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/jsse.jar
b47d5000-b483f000 rwxp 00000000 00:00 0 
b483f000-b6e99000 r-xs 00000000 08:01 4463197    /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/rt.jar
b6e99000-b6ea8000 r-xp 00000000 08:01 531257     /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/i386/libzip.so
b6ea8000-b6eaa000 rwxp 0000e000 08:01 531257     /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/i386/libzip.so
b6eaa000-b6ecb000 r-xp 00000000 08:01 531256     /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/i386/libjava.so
b6ecb000-b6ecd000 rwxp 00020000 08:01 531256     /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/i386/libjava.so
b6ecd000-b6ed8000 r-xp 00000000 08:01 531255     /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/i386/libverify.so
b6ed8000-b6ed9000 rwxp 0000b000 08:01 531255     /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/i386/libverify.so
b6ed9000-b6ee3000 r-xp 00000000 08:01 3670127    /lib/libnss_files-2.12.1.so
b6ee3000-b6ee4000 r-xp 00009000 08:01 3670127    /lib/libnss_files-2.12.1.so
b6ee4000-b6ee5000 rwxp 0000a000 08:01 3670127    /lib/libnss_files-2.12.1.so
b6ee5000-b6eee000 r-xp 00000000 08:01 3670137    /lib/libnss_nis-2.12.1.so
b6eee000-b6eef000 r-xp 00008000 08:01 3670137    /lib/libnss_nis-2.12.1.so
b6eef000-b6ef0000 rwxp 00009000 08:01 3670137    /lib/libnss_nis-2.12.1.so
b6ef0000-b6ef6000 r-xp 00000000 08:01 3670123    /lib/libnss_compat-2.12.1.so
b6ef6000-b6ef7000 r-xp 00006000 08:01 3670123    /lib/libnss_compat-2.12.1.so
b6ef7000-b6ef8000 rwxp 00007000 08:01 3670123    /lib/libnss_compat-2.12.1.so
b6ef8000-b6f0b000 r-xp 00000000 08:01 3670121    /lib/libnsl-2.12.1.so
b6f0b000-b6f0c000 r-xp 00012000 08:01 3670121    /lib/libnsl-2.12.1.so
b6f0c000-b6f0d000 rwxp 00013000 08:01 3670121    /lib/libnsl-2.12.1.so
b6f0d000-b6f14000 rwxp 00000000 00:00 0 
b6f14000-b6f1c000 rwxs 00000000 08:01 664066     /tmp/hsperfdata_root/1831
b6f1c000-b6f40000 r-xp 00000000 08:01 3670110    /lib/libm-2.12.1.so
b6f40000-b6f41000 r-xp 00023000 08:01 3670110    /lib/libm-2.12.1.so
b6f41000-b6f42000 rwxp 00024000 08:01 3670110    /lib/libm-2.12.1.so
b6f42000-b72b5000 r-xp 00000000 08:01 531250     /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/i386/client/libjvm.so
b72b5000-b72d4000 rwxp 00372000 08:01 531250     /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/i386/client/libjvm.so
b72d4000-b76eb000 rwxp 00000000 00:00 0 
b76eb000-b7842000 r-xp 00000000 08:01 3670061    /lib/libc-2.12.1.so
b7842000-b7843000 ---p 00157000 08:01 3670061    /lib/libc-2.12.1.so
b7843000-b7845000 r-xp 00157000 08:01 3670061    /lib/libc-2.12.1.so
b7845000-b7846000 rwxp 00159000 08:01 3670061    /lib/libc-2.12.1.so
b7846000-b784a000 rwxp 00000000 00:00 0 
b784a000-b784c000 r-xp 00000000 08:01 3670075    /lib/libdl-2.12.1.so
b784c000-b784d000 r-xp 00001000 08:01 3670075    /lib/libdl-2.12.1.so
b784d000-b784e000 rwxp 00002000 08:01 3670075    /lib/libdl-2.12.1.so
b784e000-b7863000 r-xp 00000000 08:01 3670169    /lib/libpthread-2.12.1.so
b7863000-b7864000 ---p 00015000 08:01 3670169    /lib/libpthread-2.12.1.so
b7864000-b7865000 r-xp 00015000 08:01 3670169    /lib/libpthread-2.12.1.so
b7865000-b7866000 rwxp 00016000 08:01 3670169    /lib/libpthread-2.12.1.so
b7866000-b7868000 rwxp 00000000 00:00 0 
b786b000-b786c000 r-xp 0082e000 08:01 4332645    /usr/lib/locale/locale-archive
b786c000-b7872000 r-xp 00000000 08:01 531245     /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/i386/native_threads/libhpi.so
b7872000-b7873000 rwxp 00006000 08:01 531245     /usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/i386/native_threads/libhpi.so
b7873000-b7874000 rwxp 00000000 00:00 0 
b7874000-b7875000 r-xp 00000000 00:00 0 
b7875000-b7877000 rwxp 00000000 00:00 0 
b7877000-b7878000 r-xp 00000000 00:00 0          [vdso]
b7878000-b7894000 r-xp 00000000 08:01 3670037    /lib/ld-2.12.1.so
b7894000-b7895000 r-xp 0001b000 08:01 3670037    /lib/ld-2.12.1.so
b7895000-b7896000 rwxp 0001c000 08:01 3670037    /lib/ld-2.12.1.so
bfad3000-bfad6000 ---p 00000000 00:00 0 
bfad7000-bfcd3000 rwxp 00000000 00:00 0          [stack]

VM Arguments:
jvm_args: -Xmx1500M -Xms1500M
java_command: DQMS_FD_Test.jar
Launcher Type: SUN_STANDARD

Environment Variables:
CLASSPATH=.:/usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/ext/
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=root
LD_LIBRARY_PATH=/usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/i386/client:/usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/lib/i386:/usr/lib/jvm/java-1.5.0-sun-1.5.0.19/jre/../lib/i386
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x32c290], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x32c290], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x28f710], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: [libjvm.so+0x28f710], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x28f710], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x291b60], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x291590], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x291590], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x291590], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x291590], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:squeeze/sid

uname:Linux 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686
libc:glibc 2.12.1 NPTL 2.12.1 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:1.57 1.17 0.85

CPU:total 1 (cores per cpu 1, threads per core 1) family 15 model 1 stepping 2, cmov, cx8, fxsr, mmx, sse, sse2

Memory: 4k page, physical 1025712k(443072k free), swap 3069948k(3069948k free)

vm_info: Java HotSpot(TM) Client VM (1.5.0_19-b02) for linux-x86, built on May  4 2009 02:30:21 by java_re with gcc 3.2.1-7a (J2SE release)

Please if anybody know about it or need more details please write back to me.........
I am *eagerly  waiting* for any *reply.*
Thank You..

---

