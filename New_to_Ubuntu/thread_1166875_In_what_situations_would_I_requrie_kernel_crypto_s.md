---
title: "In what situations would I requrie kernel crypto support"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by keratos on 2009-05-22
Just wondering in what situations would I require the kernel crypto support and associated modules during a custom kernel compile.

Any examples will do in order that I can get the thought process and decide whether I need any of them (I'd like to completely remove crypto from the kernel - not sure if I can/would want to)

Thanks.

---

### Post by alphacrucis2 on 2009-05-22
> **keratos said:**
> Just wondering in what situations would I require the kernel crypto support and associated modules during a custom kernel compile.

Any examples will do in order that I can get the thought process and decide whether I need any of them (I'd like to completely remove crypto from the kernel - not sure if I can/would want to)

Thanks.

Encryption is used by all sorts of things such as web browsers for https, VPN's, IPSec, ssh, keyrings maybe, Not sure if they all use the kernel crypto support though.

---

### Post by anewguy on 2009-05-22
I hope you don't mind me jumping into this thread - I don't mean to hijack it but instead just ask for expansion on the topic.

Does the LiveCD, such as for 9.04, include this crypto kernel by default?

Do you know if extra C or C++ header files are included, and if so,  what they might be?

I'm asking as we have a program in Windows that uses Microsoft's encryption/decryption techniques and I am all Linux so I would like to port it to Ubuntu.  So far the outputs don't match, and I'm wondering if this crypto kernal might help.

Thank you,
Dave :)

---

### Post by keratos on 2009-05-23
Not sure what you mean by "crypto kernel"

The kernel has (or rather it is possible to include or exclude crypto support for a number of algorithms) crypto.

9.04 has some cryptos enabled but you would need to specify which crypto algorithm you require before I can confirm whether it is in 9.04.

The alternative is to build your own kernel. It really is not that difficult. The *buntu stock kernels include support for every man and his dog in terms of hardware and drivers. It has to do this so that the linux O/S can boot regardless of what hardware one is using. Much akin to grabbing an Windows disc and expecting it to install on any machine. No different.

However, through building your own kernel, it is possible to remove all the bloat. I have done this for all my machines with great results. For example, nexiuz ran with 21fps before my mods. Now I get 46fps on 'Normal' settings. PlanetPenguinRacer from 34fps to 70fps. Not particularly good figures for the diehard gamer, but then again I'm not a diehard gamer. Just trying to demonstrate the benefits of custom kernels. I run kernel 2.6.30-rc4 with a heavy modded config tailored to my Toshiba laptop (A300-1J1).

---

### Post by HermanAB on 2009-05-23
You always need it.  Passwords are saved as hashes for example.  HTTPS requires it etc.

---

### Post by anewguy on 2009-05-23
I'll do some checking with my Windows friends to see if they can tell me exactly what is needed, but I think it is something like using MD5 with RC2 and chain block ciphers, and needing (myself) to know things like a crypto hash versus a cipher, etc..  I have to claim complete ignorance on all of it - I'm just trying to get the program working in Linux.

I'm assuming some of this is already included, as the process runs, it just generates different information from the Windows counterpart, and right now nobody is sure if it is the encryption techniques themselves or if it is just some sort of programming error.

Thanks in adavance!
Dave :)

---

### Post by keratos on 2009-05-23
> **HermanAB said:**
> You always need it.  Passwords are saved as hashes for example.  HTTPS requires it etc.

Not convinced, sorry.

Sure, hashes are integral, however, only specific cryptos are required - not all. For example, WEP uses CRC; P2P uses ED4. And so on. 

The linux kernel offers a myriad of algorithms. Not all will be required.

Ha, I'm answering my own question ! LoL

---

