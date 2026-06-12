---
title: "ndiswrapper help!"
date: 2006-08-29
forum: Networking &amp; Wireless
---

### Post by igul222 on 2006-08-29
i am trying to get my USB wirelles lan adapter to work under ubuntu, but there are no linux drivers available. my adapter is manufactured by intersil (i think?), and i can't find any info on the web about it at all (model name "usb-400"). I have windows drivers for it, and would like to try using ndiswrapper. I am a complete linux noob, how do i compile/install/get ndiswrapper working and use it with my windows driver?

---

### Post by jcano88184 on 2006-08-29
There are a couple of commands to help you:

$ lshw ...this will show all the hardware stuff in your computer, check the usb part

$ lsusb ... same like lshw, but more deep information about manufacturer ID

take note of the returned info and post here to help you.

---

### Post by haiku99 on 2006-08-29
see [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by igul222 on 2006-08-30
thanks, but i had to install windows to post this message, so I can't run lsusb. Will it produce accurate results on a live cd?

---

