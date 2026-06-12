---
title: "ngrok giving SIGILL: illegal instruction with kubuntu 16.04"
date: 2018-11-23
forum: Networking &amp; Wireless
---

### Post by rcwh on 2018-11-23
I have just installed with apt-get the client and server ngrok packages.
If I run any command (even help)

ngrok -h

I get 

SIGILL: illegal instruction
PC=0x812bed9

math.init·1()
        /usr/lib/go/src/pkg/math/pow10.go:34 +0x19 fp=0xb74a9f60
math.init()
        /usr/lib/go/src/pkg/math/unsafe.go:21 +0x3e fp=0xb74a9f64
reflect.init()
        /usr/lib/go/src/pkg/reflect/value.go:2528 +0x49 fp=0xb74a9f78
ngrok/client/assets.init()
        /build/buildd/ngrok-1.6+dfsg/src/ngrok/client/assets/assets_release.go:193 +0x44 fp=0xb74a9f90
ngrok/client.init()
        /build/buildd/ngrok-1.6+dfsg/src/ngrok/client/update_debug.go:11 +0x3e fp=0xb74a9f94
main.init()
        /build/buildd/ngrok-1.6+dfsg/src/ngrok/main/ngrok/ngrok.go:9 +0x3e fp=0xb74a9f98
runtime.main()
        /usr/lib/go/src/pkg/runtime/proc.c:213 +0xd6 fp=0xb74a9fcc
runtime.goexit()
        /usr/lib/go/src/pkg/runtime/proc.c:1394 fp=0xb74a9fd0

goroutine 2 [runnable]:
runtime.MHeap_Scavenger()
        /usr/lib/go/src/pkg/runtime/mheap.c:439
runtime.goexit()
        /usr/lib/go/src/pkg/runtime/proc.c:1394

eax     0x0
ebx     0x18a0e000
ecx     0x18a010a0
edx     0x1
edi     0x18a012b0
esi     0x80
ebp     0x18a0e000
esp     0xb74a9f5c
eip     0x812bed9
eflags  0x10206
cs      0x73
fs      0x0
gs      0x33

Can anyone advise me how I might fix this? I realise it seems to be pointing at a different package but wonder if this a know problem or something I have done that is silly.
My 16.04 is full up dated.

Thanks very much 
R Henderson

---

### Post by SeijiSensei on 2018-11-23
Looks like a bug to me.  It's probably supposed to be the SIG**K**ILL signal to the kernel.  You could try downloading the source code for the app and fixing it yourself or file a bug report.

---

