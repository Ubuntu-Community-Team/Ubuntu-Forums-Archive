---
title: "How can I install a Crystal HD video decoder driver from source?"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by vtandback on 2010-06-06
Hi!
I am brand new to Ubuntu, installed yesterday on an eeepc 1005PR. It has a Broadcom Crystal HD video decoder that I can't get to work.

This page: [http://www.broadcom.com/support/crystal_hd/](http://www.broadcom.com/support/crystal_hd/) has drivers for the card. On Windows 7 it installed easily and worked great (meaning I was able to watch streaming HD video. Right now it's very jerky and skips). 

But for Linux there is just a source code.

How do I install from the source code? I've spent a long time searching this forum and the web and I can't figure it out.

Thanks so much for any help!

---

### Post by cleverbubbles123 on 2010-06-06
open terminal (applications->accessories->terminal). MAKE SURE THE FOLDER WITH THE SOURCE CODE IS ON YOUR DESKTOP.
in terminal, type: "cd Desktop" then "cd <the folder with the source code in it>" then          "sudo make" then "sudo make install" (all with no quotes):popcorn:

---

### Post by vtandback on 2010-06-06
thanks for the reply!

I just tried that and get this response:

```
make: *** No targets specified and no makefile found. Stop.
```

There is a makefile in the folder, I'm not sure what this means...

any ideas? thanks again!

---

### Post by aeiah on 2010-06-06
see what the readme file tells you. you may need to run ./configure first or something.

have you seen if synaptic has the drivers? that'll probably be easier. looks like there's a package in the ubuntu repositories called libcrystalhd1 stating:
"Crystal HD Video Decoder Drivers libraries"

---

### Post by robbiebravo on 2010-07-02
I'm having the same problem. I'v installed the libcrystalhd1 and licrystalhd1-dev form synaptic. does this mean the drivers are installed. when i look in lsmod I don't see the driver. any suggestions of getting this card to work in lucid?

---

### Post by Stillwellean on 2010-07-07
I had the same problem with the manual installation. You need to "sudo apt-get g++" before you can use the make command in this case.

---

