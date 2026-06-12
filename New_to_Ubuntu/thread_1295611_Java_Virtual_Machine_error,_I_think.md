---
title: "Java Virtual Machine error, I think?"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by Lil Josh on 2009-10-19
Ugh, I received this error message in a .txt file when I was searching places. Would anyone happen to know how to fix this on Ubuntu 8.04 Hardy?

```

#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x06234ef3, pid=12508, tid=2850413456
#
# Java VM: Java HotSpot(TM) Client VM (10.0-b22 mixed mode linux-x86)
# Problematic frame:
# V  [libjvm.so+0x234ef3]
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#

---------------  T H R E A D  ---------------

Current thread (0x08473000):  JavaThread "Thread-9" daemon [_thread_in_vm, id=12550, stack(0xa9e0d000,0xa9e5e000)]

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=1 (SEGV_MAPERR), si_addr=0x00000000

Registers:
EAX=0x00000000, EBX=0xa9e5c8b0, ECX=0x00000000, EDX=0x00000ffc
ESP=0xa9e5c8b0, EBP=0xa9e5c928, ESI=0x00000027, EDI=0x08473000
EIP=0x06234ef3, CR2=0x00000000, EFLAGS=0x00210246

Top of Stack: (sp=0xa9e5c8b0)
0xa9e5c8b0:   b7e3b23e 082697a8 a9e5c8d8 ffffffff
0xa9e5c8c0:   a9e5c900 00000000 a9e5c8e8 00000038
0xa9e5c8d0:   0000000a ab80f9e4 abb1a218 0623ce98
0xa9e5c8e0:   08473000 00000000 abb1a3d0 abb1a218
0xa9e5c8f0:   08473000 b7f56541 abb1a3d0 00000000
0xa9e5c900:   08473000 00000005 00000000 ab8105a3
0xa9e5c910:   00000037 ab80f000 00010f40 ab81fee0
0xa9e5c920:   00000027 a9f38b88 a9e5c948 ab81aa09 

Instructions: (pc=0x06234ef3)
0x06234ee3:   02 00 00 8b 45 10 8d 5d 88 c7 45 a8 0a 00 00 00
0x06234ef3:   8b 08 8d 75 14 8b 41 08 8b 51 0c 83 c2 1c 66 8b 

Stack: [0xa9e0d000,0xa9e5e000],  sp=0xa9e5c8b0,  free space=318k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
V  [libjvm.so+0x234ef3]
C  [libjavaplugin_jni.so+0xba09]  AcquireThreadPipe+0x39
C  [libjavaplugin_jni.so+0xc1ab]  SendJNIJSMessage+0x2bb
C  [libjavaplugin_jni.so+0xc69d]  Java_sun_plugin_javascript_navig5_JSObject_JSObjectInvoke+0x5d
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::StubRoutines (1)
V  [libjvm.so+0x21c5cd]
V  [libjvm.so+0x310748]
V  [libjvm.so+0x21bee0]
V  [libjvm.so+0x21bf6d]
V  [libjvm.so+0x28c175]
V  [libjvm.so+0x391f8d]
V  [libjvm.so+0x3113f9]
C  [libpthread.so.0+0x54c7]

Java frames: (J=compiled Java code, j=interpreted, Vv=VM code)
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::StubRoutines (1)

---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x082eac00 JavaThread "Java Sound Event Dispatcher" daemon [_thread_blocked, id=12565, stack(0xaa08e000,0xaa0df000)]
  0x084b5c00 JavaThread "Thread-11" daemon [_thread_blocked, id=12560, stack(0xa9eaf000,0xa9f00000)]
  0x0826ac00 JavaThread "Thread-10" daemon [_thread_blocked, id=12554, stack(0xaa88f000,0xaa8e0000)]
=>0x08473000 JavaThread "Thread-9" daemon [_thread_in_vm, id=12550, stack(0xa9e0d000,0xa9e5e000)]
  0x080d1400 JavaThread "Thread-8" daemon [_thread_blocked, id=12549, stack(0xaa73a000,0xaa78b000)]
  0x08288400 JavaThread "AWT-EventQueue-2" [_thread_blocked, id=12543, stack(0xaa78b000,0xaa7dc000)]
  0xabb5c800 JavaThread "TimerQueue" daemon [_thread_blocked, id=12540, stack(0xaa691000,0xaa6e2000)]
  0x08287400 JavaThread "thread applet-loader.class" [_thread_blocked, id=12537, stack(0xaa7dc000,0xaa82d000)]
  0xabbd9c00 JavaThread "AWT-EventQueue-0" [_thread_blocked, id=12531, stack(0xaa6e2000,0xaa733000)]
  0xabb6f800 JavaThread "Thread-2" [_thread_blocked, id=12527, stack(0xaa8e0000,0xaa931000)]
  0x08422000 JavaThread "ConsoleWriterThread" daemon [_thread_blocked, id=12525, stack(0xaa991000,0xaa9e2000)]
  0xabbcf000 JavaThread "AWT-EventQueue-1" [_thread_blocked, id=12524, stack(0xaa9e2000,0xaaa33000)]
  0xabbc8c00 JavaThread "AWT-Shutdown" [_thread_blocked, id=12523, stack(0xab4dc000,0xab52d000)]
  0xabbc8000 JavaThread "traceMsgQueueThread" daemon [_thread_blocked, id=12520, stack(0xab52d000,0xab57e000)]
  0xabbbd000 JavaThread "CacheCleanUpThread" daemon [_thread_blocked, id=12519, stack(0xab57e000,0xab5cf000)]
  0xabbbc400 JavaThread "CacheMemoryCleanUpThread" [_thread_blocked, id=12518, stack(0xab5cf000,0xab620000)]
  0xabbb1400 JavaThread "AWT-XAWT" daemon [_thread_in_native, id=12517, stack(0xab6ae000,0xab6ff000)]
  0xabb72400 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=12516, stack(0xab723000,0xab774000)]
  0xabb00c00 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=12514, stack(0xabaaf000,0xabb00000)]
  0x080b7c00 JavaThread "CompilerThread0" daemon [_thread_blocked, id=12513, stack(0xabc1e000,0xabc9f000)]
  0x080b6800 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=12512, stack(0xabc9f000,0xabcf0000)]
  0x080a6000 JavaThread "Finalizer" daemon [_thread_blocked, id=12511, stack(0xabd36000,0xabd87000)]
  0x080a1c00 JavaThread "Reference Handler" daemon [_thread_blocked, id=12510, stack(0xabd87000,0xabdd8000)]
  0x08052400 JavaThread "main" [_thread_in_native, id=12508, stack(0xbfc3e000,0xbfc8e000)]

Other Threads:
  0x0809e800 VMThread [stack: 0xabdd8000,0xabe59000] [id=12509]
  0xabb02400 WatcherThread [stack: 0xaba2e000,0xabaaf000] [id=12515]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 def new generation   total 1856K, used 1429K [0xac0a0000, 0xac2a0000, 0xac580000)
  eden space 1664K,  74% used [0xac0a0000, 0xac1d5540, 0xac240000)
  from space 192K,  99% used [0xac240000, 0xac26fff8, 0xac270000)
  to   space 192K,   0% used [0xac270000, 0xac270000, 0xac2a0000)
 tenured generation   total 23700K, used 21371K [0xac580000, 0xadca5000, 0xb00a0000)
   the space 23700K,  90% used [0xac580000, 0xada5ed90, 0xada5ee00, 0xadca5000)
 compacting perm gen  total 15872K, used 15668K [0xb00a0000, 0xb1020000, 0xb40a0000)
   the space 15872K,  98% used [0xb00a0000, 0xb0fed238, 0xb0fed400, 0xb1020000)
No shared spaces configured.

Dynamic libraries:
06000000-0641b000 r-xp 00000000 08:02 23558      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/client/libjvm.so
0641b000-06435000 rwxp 0041a000 08:02 23558      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/client/libjvm.so
06435000-06855000 rwxp 06435000 00:00 0 
08048000-0804b000 r-xp 00000000 08:02 23389      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/bin/java_vm
0804b000-0804c000 rwxp 00002000 08:02 23389      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/bin/java_vm
0804c000-089d7000 rwxp 0804c000 00:00 0          [heap]
a9400000-a95c8000 rwxp a9400000 00:00 0 
a95c8000-a9600000 ---p a95c8000 00:00 0 
a9600000-a9800000 rwxp a9600000 00:00 0 
a9800000-a98ff000 rwxp a9800000 00:00 0 
a98ff000-a9900000 ---p a98ff000 00:00 0 
a9900000-a99ff000 rwxp a9900000 00:00 0 
a99ff000-a9a00000 ---p a99ff000 00:00 0 
a9a00000-a9b00000 rwxp a9a00000 00:00 0 
a9b42000-a9d56000 rwxs 00000000 00:09 917520     /SYSV00000000 (deleted)
a9d56000-a9e09000 r-xp 00000000 08:02 8495       /usr/lib/libasound.so.2.0.0
a9e09000-a9e0d000 rwxp 000b2000 08:02 8495       /usr/lib/libasound.so.2.0.0
a9e0d000-a9e10000 ---p a9e0d000 00:00 0 
a9e10000-a9e5e000 rwxp a9e10000 00:00 0 
a9e5e000-a9e61000 rwxp a9e5e000 00:00 0 
a9e61000-a9eaf000 rwxp a9e61000 00:00 0 
a9eaf000-a9eb2000 ---p a9eaf000 00:00 0 
a9eb2000-aa000000 rwxp a9eb2000 00:00 0 
aa00d000-aa03b000 r-xp 00000000 08:02 23588      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libjsound.so
aa03b000-aa03c000 rwxp 0002e000 08:02 23588      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libjsound.so
aa03c000-aa03d000 rwxp aa03c000 00:00 0 
aa03d000-aa040000 rwxp aa03d000 00:00 0 
aa040000-aa08e000 rwxp aa040000 00:00 0 
aa08e000-aa091000 ---p aa08e000 00:00 0 
aa091000-aa0df000 rwxp aa091000 00:00 0 
aa2c5000-aa691000 rwxp aa2c5000 00:00 0 
aa691000-aa694000 ---p aa691000 00:00 0 
aa694000-aa6e2000 rwxp aa694000 00:00 0 
aa6e2000-aa6e5000 ---p aa6e2000 00:00 0 
aa6e5000-aa733000 rwxp aa6e5000 00:00 0 
aa73a000-aa73d000 ---p aa73a000 00:00 0 
aa73d000-aa78b000 rwxp aa73d000 00:00 0 
aa78b000-aa78e000 ---p aa78b000 00:00 0 
aa78e000-aa7dc000 rwxp aa78e000 00:00 0 
aa7dc000-aa7df000 ---p aa7dc000 00:00 0 
aa7df000-aa82d000 rwxp aa7df000 00:00 0 
aa82d000-aa83c000 r-xp 00000000 08:02 2825       /lib/libresolv-2.7.so
aa83c000-aa83e000 rwxp 0000e000 08:02 2825       /lib/libresolv-2.7.so
aa83e000-aa840000 rwxp aa83e000 00:00 0 
aa840000-aa844000 r-xp 00000000 08:02 2793       /lib/libnss_dns-2.7.so
aa844000-aa846000 rwxp 00003000 08:02 2793       /lib/libnss_dns-2.7.so
aa846000-aa848000 r-xp 00000000 08:02 2801       /lib/libnss_mdns4_minimal.so.2
aa848000-aa849000 rwxp 00001000 08:02 2801       /lib/libnss_mdns4_minimal.so.2
aa855000-aa863000 r-xp 00000000 08:02 23589      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libjsoundalsa.so
aa863000-aa864000 rwxp 0000e000 08:02 23589      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libjsoundalsa.so
aa864000-aa87d000 r-xp 00000000 08:02 23602      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libunpack.so
aa87d000-aa881000 rwxp 00018000 08:02 23602      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libunpack.so
aa881000-aa885000 rwxp aa881000 00:00 0 
aa885000-aa88c000 r-xs 00110000 08:02 23697      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/resources.jar
aa88c000-aa88e000 r-xs 00007000 08:02 167732     /home/gabe/.java/deployment/cache/6.0/50/3c5eb672-3152a98b
aa88e000-aa88f000 rwxp aa88e000 00:00 0 
aa88f000-aa892000 ---p aa88f000 00:00 0 
aa892000-aa8e0000 rwxp aa892000 00:00 0 
aa8e0000-aa8e3000 ---p aa8e0000 00:00 0 
aa8e3000-aa931000 rwxp aa8e3000 00:00 0 
aa931000-aa991000 rwxs 00000000 00:09 819215     /SYSV00000000 (deleted)
aa991000-aa994000 ---p aa991000 00:00 0 
aa994000-aa9e2000 rwxp aa994000 00:00 0 
aa9e2000-aa9e5000 ---p aa9e2000 00:00 0 
aa9e5000-aab37000 rwxp aa9e5000 00:00 0 
aab37000-aab39000 r-xp 00000000 08:02 20877      /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
aab39000-aab3a000 rwxp 00001000 08:02 20877      /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
aab3a000-aabcb000 r-xp 00000000 08:02 29326      /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
aabcb000-aabd2000 r-xp 00000000 08:02 23595      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libnio.so
aabd2000-aabd3000 rwxp 00006000 08:02 23595      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libnio.so
aabd3000-aabe6000 r-xp 00000000 08:02 23594      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libnet.so
aabe6000-aabe7000 rwxp 00013000 08:02 23594      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libnet.so
aabe7000-aabed000 r-xs 00000000 08:02 101606     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
aabed000-aabf0000 r-xs 00000000 08:02 101616     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
aabf0000-aabf2000 r-xs 00000000 08:02 101601     /var/cache/fontconfig/52728cdc49031813f272d4aa720952ff-x86.cache-2
aabf2000-aabf3000 r-xs 00000000 08:02 101608     /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
aabf3000-aabf6000 r-xs 00000000 08:02 101607     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
aabf6000-aabfd000 r-xs 00000000 08:02 101603     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
aabfd000-aac00000 r-xs 00000000 08:02 101613     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
aac00000-aac08000 r-xs 00000000 08:02 101617     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
aac08000-aac10000 r-xs 00000000 08:02 101594     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
aac10000-aac13000 r-xs 00000000 08:02 101614     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
aac13000-aac1a000 r-xs 00000000 08:02 101611     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
aac1a000-aac1f000 r-xs 00000000 08:02 101595     /var/cache/fontconfig/105b9c7e6f0a4f82d8c9b6e39c52c6f9-x86.cache-2
aac1f000-aac25000 r-xs 00000000 08:02 101593     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
aac25000-aac35000 r-xp 00000000 08:02 8967       /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
aac35000-aac36000 rwxp 0000f000 08:02 8967       /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
aac36000-aad17000 r-xp 00000000 08:02 9127       /usr/lib/locale/en_US.utf8/LC_COLLATE
aad17000-aad37000 r-xp 00000000 08:02 20592      /usr/lib/libexpat.so.1.5.2
aad37000-aad39000 rwxp 0001f000 08:02 20592      /usr/lib/libexpat.so.1.5.2
aad39000-aad43000 r-xp 00000000 08:02 2772       /lib/libgcc_s.so.1
aad43000-aad44000 rwxp 0000a000 08:02 2772       /lib/libgcc_s.so.1
aad44000-aae2b000 r-xp 00000000 08:02 12094      /usr/lib/libstdc++.so.6.0.9
aae2b000-aae2e000 r-xp 000e7000 08:02 12094      /usr/lib/libstdc++.so.6.0.9
aae2e000-aae30000 rwxp 000ea000 08:02 12094      /usr/lib/libstdc++.so.6.0.9
aae30000-aae36000 rwxp aae30000 00:00 0 
aae36000-aae5e000 r-xp 00000000 08:02 10792      /usr/lib/libpixman-1.so.0.10.0
aae5e000-aae5f000 rwxp 00028000 08:02 10792      /usr/lib/libpixman-1.so.0.10.0
aae5f000-aae81000 r-xp 00000000 08:02 12088      /usr/lib/libpng12.so.0.15.0
aae81000-aae82000 rwxp 00021000 08:02 12088      /usr/lib/libpng12.so.0.15.0
aae82000-aaea9000 r-xp 00000000 08:02 11946      /usr/lib/libpcre.so.3.12.1
aaea9000-aaeaa000 rwxp 00026000 08:02 11946      /usr/lib/libpcre.so.3.12.1
aaeaa000-aaec0000 r-xp 00000000 08:02 2829       /lib/libselinux.so.1
aaec0000-aaec2000 rwxp 00015000 08:02 2829       /lib/libselinux.so.1
aaec2000-aaed6000 r-xp 00000000 08:02 11960      /usr/lib/libz.so.1.2.3.3
aaed6000-aaed7000 rwxp 00013000 08:02 11960      /usr/lib/libz.so.1.2.3.3
aaed7000-aaf41000 r-xp 00000000 08:02 20538      /usr/lib/libfreetype.so.6.3.16
aaf41000-aaf45000 rwxp 00069000 08:02 20538      /usr/lib/libfreetype.so.6.3.16
aaf45000-aaf6c000 r-xp 00000000 08:02 22702      /usr/lib/libpangoft2-1.0.so.0.2002.3
aaf6c000-aaf6d000 rwxp 00026000 08:02 22702      /usr/lib/libpangoft2-1.0.so.0.2002.3
aaf6d000-aaf73000 r-xp 00000000 08:02 21965      /usr/lib/libXrandr.so.2.1.0
aaf73000-aaf74000 rwxp 00005000 08:02 21965      /usr/lib/libXrandr.so.2.1.0
aaf74000-aaf9c000 r-xp 00000000 08:02 22289      /usr/lib/libfontconfig.so.1.3.0
aaf9c000-aaf9d000 rwxp 00028000 08:02 22289      /usr/lib/libfontconfig.so.1.3.0
aaf9d000-aaff8000 r-xp 00000000 08:02 10095      /usr/lib/libcairo.so.2.17.3
aaff8000-aaffa000 rwxp 0005b000 08:02 10095      /usr/lib/libcairo.so.2.17.3
aaffa000-ab0a7000 r-xp 00000000 08:02 20690      /usr/lib/libglib-2.0.so.0.1600.4
ab0a7000-ab0a8000 rwxp 000ad000 08:02 20690      /usr/lib/libglib-2.0.so.0.1600.4
ab0a8000-ab0ab000 r-xp 00000000 08:02 22154      /usr/lib/libgmodule-2.0.so.0.1600.4
ab0ab000-ab0ac000 rwxp 00002000 08:02 22154      /usr/lib/libgmodule-2.0.so.0.1600.4
ab0ac000-ab0e5000 r-xp 00000000 08:02 21744      /usr/lib/libgobject-2.0.so.0.1600.4
ab0e5000-ab0e6000 rwxp 00039000 08:02 21744      /usr/lib/libgobject-2.0.so.0.1600.4
ab0e6000-ab120000 r-xp 00000000 08:02 22765      /usr/lib/libpango-1.0.so.0.2002.3
ab120000-ab122000 rwxp 00039000 08:02 22765      /usr/lib/libpango-1.0.so.0.2002.3
ab122000-ab19f000 r-xp 00000000 08:02 20564      /usr/lib/libgdk-x11-2.0.so.0.1200.9
ab19f000-ab1a2000 rwxp 0007c000 08:02 20564      /usr/lib/libgdk-x11-2.0.so.0.1200.9
ab1a2000-ab4d5000 r-xp 00000000 08:02 7672       /usr/lib/libgtk-x11-2.0.so.0.1200.9
ab4d5000-ab4db000 rwxp 00333000 08:02 7672       /usr/lib/libgtk-x11-2.0.so.0.1200.9
ab4db000-ab4dc000 rwxp ab4db000 00:00 0 
ab4dc000-ab4df000 ---p ab4dc000 00:00 0 
ab4df000-ab52d000 rwxp ab4df000 00:00 0 
ab52d000-ab530000 ---p ab52d000 00:00 0 
ab530000-ab57e000 rwxp ab530000 00:00 0 
ab57e000-ab581000 ---p ab57e000 00:00 0 
ab581000-ab5cf000 rwxp ab581000 00:00 0 
ab5cf000-ab5d2000 ---p ab5cf000 00:00 0 
ab5d2000-ab620000 rwxp ab5d2000 00:00 0 
ab620000-ab626000 r-xs 00000000 08:02 101606     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
ab626000-ab629000 r-xs 00000000 08:02 101616     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
ab629000-ab62b000 r-xs 00000000 08:02 101601     /var/cache/fontconfig/52728cdc49031813f272d4aa720952ff-x86.cache-2
ab62b000-ab62c000 r-xs 00000000 08:02 101608     /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
ab62c000-ab62d000 r-xs 00000000 08:02 101600     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
ab62d000-ab630000 r-xs 00000000 08:02 101607     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
ab630000-ab637000 r-xs 00000000 08:02 101603     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
ab637000-ab63a000 r-xs 00000000 08:02 101613     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
ab63a000-ab642000 r-xs 00000000 08:02 101617     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
ab642000-ab64a000 r-xs 00000000 08:02 101594     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
ab64a000-ab64b000 r-xs 00000000 08:02 101598     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
ab64b000-ab64e000 r-xs 00000000 08:02 101614     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
ab64e000-ab655000 r-xs 00000000 08:02 101611     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
ab655000-ab657000 r-xp 00000000 08:02 8908       /usr/lib/libXinerama.so.1.0.0
ab657000-ab658000 rwxp 00001000 08:02 8908       /usr/lib/libXinerama.so.1.0.0
ab658000-ab66f000 r-xp 00000000 08:02 11562      /usr/lib/libatk-1.0.so.0.2209.1
ab66f000-ab671000 rwxp 00016000 08:02 11562      /usr/lib/libatk-1.0.so.0.2209.1
ab671000-ab673000 r-xp 00000000 08:02 21758      /usr/lib/libXdamage.so.1.1.0
ab673000-ab674000 rwxp 00001000 08:02 21758      /usr/lib/libXdamage.so.1.1.0
ab674000-ab676000 r-xp 00000000 08:02 23159      /usr/lib/libXcomposite.so.1.0.0
ab676000-ab677000 rwxp 00001000 08:02 23159      /usr/lib/libXcomposite.so.1.0.0
ab677000-ab67f000 r-xp 00000000 08:02 21961      /usr/lib/libpangocairo-1.0.so.0.2002.3
ab67f000-ab680000 rwxp 00008000 08:02 21961      /usr/lib/libpangocairo-1.0.so.0.2002.3
ab680000-ab696000 r-xp 00000000 08:02 12040      /usr/lib/libgdk_pixbuf-2.0.so.0.1200.9
ab696000-ab697000 rwxp 00016000 08:02 12040      /usr/lib/libgdk_pixbuf-2.0.so.0.1200.9
ab697000-ab6a8000 r-xp 00000000 08:02 23569      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libdeploy.so
ab6a8000-ab6aa000 rwxp 00010000 08:02 23569      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libdeploy.so
ab6aa000-ab6ae000 rwxp ab6aa000 00:00 0 
ab6ae000-ab6b1000 ---p ab6ae000 00:00 0 
ab6b1000-ab6ff000 rwxp ab6b1000 00:00 0 
ab6ff000-ab703000 r-xp 00000000 08:02 21790      /usr/lib/libXfixes.so.3.1.0
ab703000-ab704000 rwxp 00003000 08:02 21790      /usr/lib/libXfixes.so.3.1.0
ab704000-ab70c000 r-xp 00000000 08:02 22176      /usr/lib/libXrender.so.1.3.0
ab70c000-ab70d000 rwxp 00007000 08:02 22176      /usr/lib/libXrender.so.1.3.0
ab70d000-ab715000 r-xp 00000000 08:02 21757      /usr/lib/libXcursor.so.1.0.2
ab715000-ab716000 rwxp 00007000 08:02 21757      /usr/lib/libXcursor.so.1.0.2
ab716000-ab717000 r-xs 00000000 08:02 101600     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
ab717000-ab718000 r-xs 00000000 08:02 101598     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
ab718000-ab71a000 r-xs 00000000 08:02 111466     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
ab71a000-ab71b000 r-xp 00000000 08:02 9135       /usr/lib/locale/en_US.utf8/LC_NUMERIC
ab71b000-ab71c000 r-xp 00000000 08:02 9225       /usr/lib/locale/en_US.utf8/LC_TIME
ab71c000-ab71d000 r-xp 00000000 08:02 9223       /usr/lib/locale/en_US.utf8/LC_MONETARY
ab71d000-ab71e000 r-xp 00000000 08:02 9132       /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
ab71e000-ab71f000 r-xp 00000000 08:02 9154       /usr/lib/locale/en_US.utf8/LC_PAPER
ab71f000-ab720000 r-xp 00000000 08:02 9171       /usr/lib/locale/en_US.utf8/LC_NAME
ab720000-ab721000 r-xp 00000000 08:02 9219       /usr/lib/locale/en_US.utf8/LC_ADDRESS
ab721000-ab722000 r-xp 00000000 08:02 9224       /usr/lib/locale/en_US.utf8/LC_TELEPHONE
ab722000-ab723000 r-xp 00000000 08:02 9221       /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
ab723000-ab726000 ---p ab723000 00:00 0 
ab726000-ab774000 rwxp ab726000 00:00 0 
ab774000-ab7f2000 r-xp 00000000 08:02 23571      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libfontmanager.so
ab7f2000-ab7fc000 rwxp 0007e000 08:02 23571      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libfontmanager.so
ab7fc000-ab801000 rwxp ab7fc000 00:00 0 
ab801000-ab80f000 r-xs 00286000 08:02 23432      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/deploy.jar
ab80f000-ab81f000 r-xp 00000000 08:02 23581      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libjavaplugin_jni.so
ab81f000-ab821000 rwxp 00010000 08:02 23581      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libjavaplugin_jni.so
ab821000-ab834000 rwxp ab821000 00:00 0 
ab834000-ab838000 r-xp 00000000 08:02 8896       /usr/lib/libXdmcp.so.6.0.0
ab838000-ab839000 rwxp 00003000 08:02 8896       /usr/lib/libXdmcp.so.6.0.0
ab839000-ab84f000 r-xp 00000000 08:02 10805      /usr/lib/libxcb.so.1.0.0
ab84f000-ab850000 rwxp 00015000 08:02 10805      /usr/lib/libxcb.so.1.0.0
ab850000-ab851000 r-xp 00000000 08:02 10804      /usr/lib/libxcb-xlib.so.0.0.0
ab851000-ab852000 rwxp 00000000 08:02 10804      /usr/lib/libxcb-xlib.so.0.0.0
ab852000-ab933000 r-xp 00000000 08:02 21967      /usr/lib/libX11.so.6.2.0
ab933000-ab936000 rwxp 000e1000 08:02 21967      /usr/lib/libX11.so.6.2.0
ab936000-ab943000 r-xp 00000000 08:02 16389      /usr/lib/libXext.so.6.4.0
ab943000-ab944000 rwxp 0000d000 08:02 16389      /usr/lib/libXext.so.6.4.0
ab944000-ab985000 r-xp 00000000 08:02 23614      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/xawt/libmawt.so
ab985000-ab988000 rwxp 00040000 08:02 23614      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/xawt/libmawt.so
ab988000-aba03000 r-xp 00000000 08:02 23566      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libawt.so
aba03000-aba0a000 rwxp 0007b000 08:02 23566      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libawt.so
aba0a000-aba2e000 rwxp aba0a000 00:00 0 
aba2e000-aba2f000 ---p aba2e000 00:00 0 
aba2f000-abaaf000 rwxp aba2f000 00:00 0 
abaaf000-abab2000 ---p abaaf000 00:00 0 
abab2000-abbee000 rwxp abab2000 00:00 0 
abbee000-abc00000 ---p abbee000 00:00 0 
abc00000-abc07000 r-xp 00000000 08:02 20855      /usr/lib/libXi.so.6.0.0
abc07000-abc08000 rwxp 00006000 08:02 20855      /usr/lib/libXi.so.6.0.0
abc08000-abc0d000 r-xs 00000000 08:02 101595     /var/cache/fontconfig/105b9c7e6f0a4f82d8c9b6e39c52c6f9-x86.cache-2
abc0d000-abc13000 r-xs 00000000 08:02 101593     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
abc13000-abc15000 r-xs 00000000 08:02 111466     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
abc15000-abc1e000 r-xs 000e2000 08:02 23694      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/plugin.jar
abc1e000-abc21000 ---p abc1e000 00:00 0 
abc21000-abc9f000 rwxp abc21000 00:00 0 
abc9f000-abca2000 ---p abc9f000 00:00 0 
abca2000-abcf0000 rwxp abca2000 00:00 0 
abcf0000-abcf7000 r-xs 00000000 08:02 16651      /usr/lib/gconv/gconv-modules.cache
abcf7000-abd36000 r-xp 00000000 08:02 9128       /usr/lib/locale/en_US.utf8/LC_CTYPE
abd36000-abd39000 ---p abd36000 00:00 0 
abd39000-abd87000 rwxp abd39000 00:00 0 
abd87000-abd8a000 ---p abd87000 00:00 0 
abd8a000-abdd8000 rwxp abd8a000 00:00 0 
abdd8000-abdd9000 ---p abdd8000 00:00 0 
abdd9000-abe8b000 rwxp abdd9000 00:00 0 
abe8b000-ac016000 r-xs 02df0000 08:02 23698      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/rt.jar
ac016000-ac01e000 rwxp ac016000 00:00 0 
ac01e000-ac037000 rwxp ac01e000 00:00 0 
ac037000-ac043000 rwxp ac037000 00:00 0 
ac043000-ac055000 rwxp ac043000 00:00 0 
ac055000-ac056000 rwxp ac055000 00:00 0 
ac056000-ac057000 rwxp ac056000 00:00 0 
ac057000-ac064000 rwxp ac057000 00:00 0 
ac064000-ac075000 rwxp ac064000 00:00 0 
ac075000-ac07d000 rwxp ac075000 00:00 0 
ac07d000-ac09f000 rwxp ac07d000 00:00 0 
ac09f000-ac2a0000 rwxp ac09f000 00:00 0 
ac2a0000-ac580000 rwxp ac2a0000 00:00 0 
ac580000-adca5000 rwxp ac580000 00:00 0 
adca5000-b00a0000 rwxp adca5000 00:00 0 
b00a0000-b1020000 rwxp b00a0000 00:00 0 
b1020000-b5ca0000 rwxp b1020000 00:00 0 
b5ca0000-b5cab000 rwxp b5ca0000 00:00 0 
b5cab000-b5d20000 rwxp b5cab000 00:00 0 
b5d20000-b5fc8000 rwxp b5d20000 00:00 0 
b5fc8000-b7d20000 rwxp b5fc8000 00:00 0 
b7d20000-b7d2f000 r-xp 00000000 08:02 23604      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libzip.so
b7d2f000-b7d31000 rwxp 0000e000 08:02 23604      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libzip.so
b7d31000-b7d54000 r-xp 00000000 08:02 23579      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libjava.so
b7d54000-b7d56000 rwxp 00023000 08:02 23579      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libjava.so
b7d56000-b7d61000 r-xp 00000000 08:02 23603      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libverify.so
b7d61000-b7d62000 rwxp 0000b000 08:02 23603      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libverify.so
b7d62000-b7d6b000 r-xp 00000000 08:02 2795       /lib/libnss_files-2.7.so
b7d6b000-b7d6d000 rwxp 00008000 08:02 2795       /lib/libnss_files-2.7.so
b7d6d000-b7d75000 r-xp 00000000 08:02 2805       /lib/libnss_nis-2.7.so
b7d75000-b7d77000 rwxp 00007000 08:02 2805       /lib/libnss_nis-2.7.so
b7d77000-b7d7d000 r-xp 00000000 08:02 2791       /lib/libnss_compat-2.7.so
b7d7d000-b7d7f000 rwxp 00005000 08:02 2791       /lib/libnss_compat-2.7.so
b7d7f000-b7d91000 r-xp 00000000 08:02 2789       /lib/libnsl-2.7.so
b7d91000-b7d93000 rwxp 00011000 08:02 2789       /lib/libnsl-2.7.so
b7d93000-b7d95000 rwxp b7d93000 00:00 0 
b7d95000-b7d99000 r-xp 00000000 08:02 20819      /usr/lib/libXtst.so.6.1.0
b7d99000-b7d9a000 rwxp 00004000 08:02 20819      /usr/lib/libXtst.so.6.1.0
b7d9a000-b7da2000 rwxs 00000000 08:02 167590     /tmp/hsperfdata_gabe/12508
b7da2000-b7da9000 r-xp 00000000 08:02 2827       /lib/librt-2.7.so
b7da9000-b7dab000 rwxp 00006000 08:02 2827       /lib/librt-2.7.so
b7dab000-b7dcf000 r-xp 00000000 08:02 2782       /lib/libm-2.7.so
b7dcf000-b7dd1000 rwxp 00023000 08:02 2782       /lib/libm-2.7.so
b7dd1000-b7dd2000 rwxp b7dd1000 00:00 0 
b7dd2000-b7f15000 r-xp 00000000 08:02 2747       /lib/libc-2.7.so
b7f15000-b7f16000 r-xp 00143000 08:02 2747       /lib/libc-2.7.so
b7f16000-b7f18000 rwxp 00144000 08:02 2747       /lib/libc-2.7.so
b7f18000-b7f1b000 rwxp b7f18000 00:00 0 
b7f1b000-b7f1d000 r-xp 00000000 08:02 2764       /lib/libdl-2.7.so
b7f1d000-b7f1f000 rwxp 00001000 08:02 2764       /lib/libdl-2.7.so
b7f1f000-b7f20000 rwxp b7f1f000 00:00 0 
b7f20000-b7f34000 r-xp 00000000 08:02 2821       /lib/libpthread-2.7.so
b7f34000-b7f36000 rwxp 00013000 08:02 2821       /lib/libpthread-2.7.so
b7f36000-b7f38000 rwxp b7f36000 00:00 0 
b7f38000-b7f39000 r-xp 00000000 08:02 9220       /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7f39000-b7f3b000 r-xp 00000000 08:02 20809      /usr/lib/libXau.so.6.0.0
b7f3b000-b7f3c000 rwxp 00001000 08:02 20809      /usr/lib/libXau.so.6.0.0
b7f3c000-b7f42000 r-xp 00000000 08:02 23608      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/native_threads/libhpi.so
b7f42000-b7f43000 rwxp 00006000 08:02 23608      /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/native_threads/libhpi.so
b7f43000-b7f44000 rwxp b7f43000 00:00 0 
b7f44000-b7f45000 r-xp b7f44000 00:00 0 
b7f45000-b7f47000 rwxp b7f45000 00:00 0 
b7f47000-b7f48000 r-xp b7f47000 00:00 0          [vdso]
b7f48000-b7f64000 r-xp 00000000 08:02 2727       /lib/ld-2.7.so
b7f64000-b7f66000 rwxp 0001b000 08:02 2727       /lib/ld-2.7.so
bfc3e000-bfc41000 ---p bfc3e000 00:00 0 
bfc41000-bfc8e000 rw-p bffb3000 00:00 0          [stack]

VM Arguments:
jvm_args: -DtrustProxy=true -Xverify:remote -Xbootclasspath/a:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/plugin.jar:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/deploy.jar:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/javaplugin_l10n.jar -Djavaplugin.lib=/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libjavaplugin_jni.so -Dmozilla.workaround=true -Djavaplugin.nodotversion=160_06 -Djavaplugin.version=1.6.0_06 -Djavaplugin.vm.options=-DtrustProxy=true -Xverify:remote -Djava.class.path=/usr/lib/jvm/java-6-sun-1.6.0.06/jre/classes -Xbootclasspath/a:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/plugin.jar:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/deploy.jar:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/javaplugin_l10n.jar -Djavaplugin.lib=/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libjavaplugin_jni.so -Dmozilla.workaround=true -Djavaplugin.nodotversion=160_06 -Djavaplugin.version=1.6.0_06  
java_command: <unknown>
Launcher Type: generic

Environment Variables:
JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.06/jre
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=gabe
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/client:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x3be710], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x3be710], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x30f810], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: [libjvm.so+0x30f810], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGXFSZ: [libjvm.so+0x30f810], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x30f810], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x311850], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x3115f0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x3115f0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x3115f0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x3115f0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:lenny/sid

uname:Linux 2.6.24-19-lpia #1 SMP Mon Nov 3 15:25:26 UTC 2008 i686
libc:glibc 2.7 NPTL 2.7 
rlimit: STACK 8192k, CORE 0k, NPROC 4022, NOFILE 1024, AS infinity
load average:1.09 0.30 0.18

CPU:total 2 (1 cores per cpu, 2 threads per core) family 6 model 12 stepping 2, cmov, cx8, fxsr, mmx, sse, sse2, sse3, ssse3, ht

Memory: 4k page, physical 505080k(5168k free), swap 0k(0k free)

vm_info: Java HotSpot(TM) Client VM (10.0-b22) for linux-x86 JRE (1.6.0_06-b02), built on Mar 25 2008 00:39:19 by "java_re" with gcc 3.2.1-7a (J2SE release)

time: Sun Oct 18 21:33:18 2009
elapsed time: 31 seconds

```Thanks in advance.

---

### Post by Hospadar on 2009-10-19
What program were you using?
What were you doing?
Where is this file?
Was there an apparent symptom of this problem? What was it?

---

### Post by martrn on 2009-10-19
Fixing a java-virtual machine running lots of .jar/java files is in the Absolute Beginner Talk section ?

Try asking in the programming forum and ask about the java language.  I wouldn't expect any serious answers here but you could always start by explaining about virtual machines.  I have always wondered about the different paradigms of virtual machines and how they work.

---

### Post by pgar23 on 2009-10-19
> **martrn said:**
> Fixing a java-virtual machine running lots of .jar/java files is in the Absolute Beginner Talk section ?

Try asking in the programming forum and ask about the java language.  I wouldn't expect any serious answers here but you could always start by explaining about virtual machines.  I have always wondered about the different paradigms of virtual machines and how they work.


I second that. This should probably be posted in another forum, move to general help maybe. 

Anyways...I dont know much about Virtual machines, but just by glancing through your post, you might try RE-INSTALLING JAVA and make sure that it properly installs. If you have no problems, and it is a seamless installation and  then you run your VM again and you are still coming up with the same problem...Then post back for help.
```

Install Java plugins using the following command
 [INDENT]sudo apt-get install sun-java6-fonts sun-java6-jre sun-java6-plugin ubuntu-restricted-extras
```
[/INDENT]

---

