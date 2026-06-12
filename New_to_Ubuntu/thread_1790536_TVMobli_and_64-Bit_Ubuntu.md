---
title: "TVMobli and 64-Bit Ubuntu"
date: 2011-06-25
forum: New to Ubuntu
---

### Post by movieguy1920 on 2011-06-25
First off, apologies, as I am very, very new to the world of Ubuntu.

When I was running MS Win, I used an app called TVMobli, a UPnP server. When I noticed they had Linux support I was overjoyed! According to their info it supports 32- and 64- bit Debian Linux, so it should work. I have downloaded the deb file several times. The file, tvmobili-debian-linux-i386.deb clearly says i386, and I am currently running 64-bit Ubuntu. After much searching online and within the forums I found that I had to install the 32-bit libraries, which I have done. Double click the deb file, open Ubuntu Software Center and Presto! Error message: Wrong architecture 'i386'.

Any thoughts?

---

### Post by Abir Valg on 2011-06-25
My thoughts would be if I am 100% sure that that 32-bit deb is compatible with 64-bit, I would modify the deb file and change the Architecture string i386 to (something like) x64.
I can't recall the procedure of modifying the deb. 
I would use my favorite search engine startpage.com to look that up

---

