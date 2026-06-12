---
title: "Installation Problems with Ubuntu 7.10"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by spacefreak86 on 2008-02-11
Hi, I'm extremely new to Ubuntu (and Linux for that matter) and currently running it dual boot with Windows XP (seperate partition, separate hard drive even). So far I'm enjoying the new system, with the exception of one problem: I cannot get any wireless network to work.

I've spent the past five hours trying to get something to work to  no avail. Currently I'm posting from the XP side of my computer since it can connect to the internet.

I'm using a Linksys WUSB54G v4 USB network adapter to connect my desktop to the wireless router in the other room. I tried network manager but nothing shows up - it was for a bit, but then I did something trying to follow the tutorials on here and wiki and now all of the fields are blank across all four tabs. I'm almost scared to try anything else without messing it up further. I have at least figured out how to install the hardware drivers for the WUSB54G adapter, determined that it uses wlan0, and figured out what the "essid" key is so that I can use the WEP for it , so that much is set. Oh, and I'm currently running P4 process (i386 I believe its called).

Could someone walk me through this and help me try to get Ubuntu connected to the internet so that I'll be able to start downloading the extensions and programs to transition to Ubuntu? Thanks

---

### Post by digitalhillbilly on 2008-02-11
It sounds like the device is loaded. Why not try [wicd]("http://wicd.sourceforge.net/") to manage your connections. It will remove network-manager. Not a bad thing IMO since I use wicd on all my machines.

dh

---

### Post by spacefreak86 on 2008-02-11
One small problem with that. I didn't see a way to download the .deb file from the site, its saying just to point the Package Manager to that site. Normally not a problem, except that I have no internet capabilities other than wireless on my computer. I'm able to get on internet via my USB wireless network adapter on XP, but when I switch over to Ubuntu, I've lost internet connectability.

---

### Post by rustybronco on 2008-02-11
try...
[http://ubuntuforums.org/showpost.php?p=3609183&postcount=1](http://ubuntuforums.org/showpost.php?p=3609183&postcount=1)

---

### Post by spacefreak86 on 2008-02-11
Okay, so I tried d/l'ing wicd, except it told me it was conflicting with Network Manager. So I uninstalled network manager, and it still won't load. I'll try that next link with it.

---

### Post by rustybronco on 2008-02-11
Wicd should remove network manager when you install it.

---

### Post by spacefreak86 on 2008-02-11
Ha! Got it. That link is awesome. Thanks!

---

### Post by digitalhillbilly on 2008-02-11
yes it should.  Grab [wicd_1.4.1-all.deb  ]("http://downloads.sourceforge.net/wicd/wicd_1.4.1-all.deb?modtime=1199416037&big_mirror=0") from [https://sourceforge.net/project/showfiles.php?group_id=194573](https://sourceforge.net/project/showfiles.php?group_id=194573) . Try run it again and it should remove network manager.

Also here is a great set up instructions to connect manually. It's worth trying to ensure your driver is loaded and working. It also has a lot of great resources, commands, etc... [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)


dh

---

