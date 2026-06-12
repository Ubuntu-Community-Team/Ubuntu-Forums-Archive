---
title: "Unable to identify the drivers installed"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by jaish1974 on 2009-02-17
Hi,

I'm new to Linux, I'm trying to migrate from windows to Linux.I got a CD from UBUNTU - 8.10 desktop CD.I've installed the same in my Windows(dual Boot). I'm able to log into the system.But I'm not able to connect to the internet. I tried to check for the Drivers installed for my ethernet driver, but I'm not able to do so.When I try to check through the packages installed, it says for updates you need to connect to the internet.

I tried to check the ndiswrapper package again the same  message.

I've good experience in windows, where I can check wheter the drivers were properly installed or not, how to use the network manager and connect oto the internet.

But, its very difficult for me in this OS

Kindly guide me to resolve these issues

---

### Post by dzark on 2009-02-17
In the command line (Applications->Accessories->Terminal)

```
lspci | grep Network
```

Should tell you what network devices you have..

Are you unable to connect to networks with both ethernet & wifi? Ethernet support is pretty good on linux these days..

Before you boot back into linux, download & save to a linux readable drive, your windows wireless drivers... Ndiswrapper should be on the CD, but probably easier to download it from here [http://archive.ubuntu.com/ubuntu/pool/main/n/](http://archive.ubuntu.com/ubuntu/pool/main/n/)

---

### Post by nothingspecial on 2009-02-17
Do you know what wireless card you have. If not ```
lspci -v
``` will tell you.

Post the card back here.

---

