---
title: "How can i use Linksys N USB wireless adapter w/ Ubuntu?"
date: 2008-07-27
forum: Networking &amp; Wireless
---

### Post by Fatigoworld on 2008-07-27
I did some searches on this and found some info but I honestly don't understand any of it....at all.  I downloaded ndiswrapper and extracted it onto my desktop.  That is the farthest I got.  I do not know what a kernal is or how to install ndiswrapper or use it.  Also don't know how to find the directory that its in.  Really lost here.  Can someone explain how to do this in a way that someone who doesnt know ANYTHING about computers can understand and follow?  Thanks!!!

---

### Post by eram on 2008-07-27
alright, I just did this on my PC, so I'll see if I can help you. First you need to find and download the linksys windows driver for your adapter. Then since It appears you don't have much experience with tar balls, try installing the two .deb packages first available from [here]("http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.50-1ubuntu1_all.deb") and [here]("http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb").

After that, just install ndisgkt.

---

### Post by Fatigoworld on 2008-07-27
ok, so i downloaded and installed both .deb packages and ndisgtk.  i downloaded the windows drivers but i did not install those because i dont know how.  i rebooted my computer with the usb attached but i am assuming that i need to do something with the windows drivers or something else.  also is ndiswrapper supposed to be a program that you can open?  i dont see anything showing that it has installed.

can you tell me what else to do to get this working?  Thanks!!!

---

### Post by Fatigoworld on 2008-07-27
someone please help im using the internet at coffee shops until i can get this going!  Thanks!!!

---

### Post by eram on 2008-07-27
ok, so now, (I'm assuming you'r using Ubuntu 8.04) up on the toolbar, click System/Administration/Windows Wireless Drivers. Make sure your adapter is plugged in and click Install New Driver. A window will pop up asking you to locate the windows driver for it to install. Locate the .inf file, which in my case was in the drivers folder. You might have to browse through the folder that you downloaded to find the .inf file. Once you have located that, hit install! After that, you should have internet! My computer is going down  for the next few days. But let me know how it goes, and hopefully if you need help, some one else will be able to help.
Thanks!

---

### Post by eram on 2008-07-28
alright, I'm back, system maintenance went quickly. Have you gotten internet yet? Please let my know if anything is unclear to you, and I will try and explain it in a different way.

---

### Post by danschalow on 2009-07-17
okay, I have followed through all the instructions, and is is looking okay, I just get to the very end where I have clicked install, it says unable to see hardware present, however, once installed it says it does see the hardware. when I click to configure network it says could not find network configuration tool

Thanks for the help
Dan

---

