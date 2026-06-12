---
title: "weird problem read carefully"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by vinayprabhushankar on 2011-05-03
Hi all,

Whenever I try to install an upgrade or new software and try to download the software my ubuntu by **default **downloads amd64 version. Note: I know mine is i686,64 bit but I am not sure why by default all software downloads is amd64. for instance to get google voice and chat [http://www.google.com/chat/video/thankyou.html?hl=en&platform=linux_](http://www.google.com/chat/video/thankyou.html?hl=en&platform=linux_)**ubuntu_x86_64** . the link says x86 but on downloading the .deb package is for amd64. There must be something making the default download amd64 right? or am i missing something. I have to go about a round about process of finding the download path using a proxy and then changing amd64 to i386 currently

---

### Post by silverglade00 on 2011-05-03
The name amd64 does not refer to AMD chips only. It also refers to Intel's mainstream desktop 64-bit chips. x86_64 means 64-bit for amd64 type chips. It does that by default because that is the proper package for your chip and version of Ubuntu. i386 is a 32-bit package, so you are going out of your way to install 32-bit packages on your 64-bit OS. While it will work, it could end up being a pain for you to maintain.

---

### Post by TeoBigusGeekus on 2011-05-03
The first 64bit processor was an AMD, so the name stuck.

---

### Post by v1ad on 2011-05-03
lol, that was amusing.

---

### Post by silverglade00 on 2011-05-03
That is one seriously awesome avatar TeoBigusGeekus! Very funny and very appropriate.

---

### Post by TeoBigusGeekus on 2011-05-03
Problem?

---

### Post by vinayprabhushankar on 2011-05-03
Thanks a ton for the reply...I get wrong architecture sometimes with the amd64 package but it installs when i install the i386. What could be the reason and how do I solve this?

---

### Post by silverglade00 on 2011-05-03
That is probably because packages can depend on each other. When they do, they want the same architecture. So if you installed 32-bit package X and now you want to install package Y that depends on package X, it will complain if you try to install 64-bit package Y. So when you went installing the 32-bit packages, you introduced a mixed set of architectures that will most likely get worse and worse as time goes by. There are ways to mix them successfully without these problems, but you have to set it up that way on purpose.

---

