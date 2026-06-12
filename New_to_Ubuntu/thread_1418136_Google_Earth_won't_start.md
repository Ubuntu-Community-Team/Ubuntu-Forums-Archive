---
title: "Google Earth won't start"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by Kerkyros on 2010-02-28
I installed Google earth some time ago, but since the font was crappy I followed a tutorial where I changed some libraries links (I don't remember what it was exactly). 
After running GE in terminal I get an error:
```
cerber@cerber-desktop:~/google-earth$ ./googleearth
./googleearth-bin: ./libpng12.so.0: no version information available (required by ./libQtGui.so.4)
Google Earth has caught signal 11.

Stacktrace from glibc:
  ./googleearth-bin [0x804f403]
  ./googleearth-bin [0x804f916]
  [0xb7efb420]
  /home/cerber/google-earth/libevll.so(_ZN6proto219FileDescriptorProto10descriptorEv+0x16) [0xb2e409b6]
  /home/cerber/google-earth/libevll.so(_ZN6proto219FileDescriptorProtoC1Ev+0x1c) [0xb2e44a8c]
  /home/cerber/google-earth/libevll.so [0xb2e50ac9]
  /home/cerber/google-earth/libevll.so [0xb2ed4632]
  /home/cerber/google-earth/libevll.so [0xb2b8a765]
  /lib/ld-linux.so.2 [0xb7f099a0]
  /lib/ld-linux.so.2 [0xb7f09ad3]
  /lib/ld-linux.so.2 [0xb7f0d784]
  /lib/ld-linux.so.2 [0xb7f095d6]
  /lib/ld-linux.so.2 [0xb7f0cf5e]
  /lib/tls/i686/cmov/libdl.so.2 [0xb679ec19]
  /lib/ld-linux.so.2 [0xb7f095d6]
  /lib/tls/i686/cmov/libdl.so.2 [0xb679f2bc]
  /lib/tls/i686/cmov/libdl.so.2(dlopen+0x41) [0xb679eb51]
  ./libbase.so(_ZN5earth7Library4loadEb+0xcb) [0xb6c43fab]
  ./libapiloader.so(_ZN5earth4evll9ApiLoader4openERK7QString+0x6f) [0xb649394f]
  ./libapiloader.so(_ZN5earth4evll9ApiLoader15openWithMessageEP7QString+0xe7) [0xb6493ce7]
  ./libgoogleearth_lib.so(_ZN5earth6client11Application3runEv+0x13a) [0xb6e6e32a]
  ./googleearth-bin(main+0x2ba) [0x8050bea]
  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb6c9b450]
  ./googleearth-bin [0x804f231]




We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /home/cerber/.googleearth/crashlogs/crashlog-F721518E.txt

This bug report will be sent to Google automatically next time you run
 Google Earth. Its data, which contains no personal information, will help
 us correct problems without bothering you further. If you would rather
 this info not be transmitted, please delete the above file before running
 the program again. If you want bug reports to NEVER be sent, remove the
 above 'crashlogs' directory's read/write permissions.

```

---

### Post by theaaronc on 2010-02-28
> **Kerkyros said:**
> 

We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /home/cerber/.googleearth/crashlogs/crashlog-F721518E.txt




Have you checked the crashlog file for any info on the specifics of the crash?

---

