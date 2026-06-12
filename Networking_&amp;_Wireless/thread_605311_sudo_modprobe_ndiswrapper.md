---
title: "sudo modprobe ndiswrapper"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by s3019293 on 2007-11-06
Hi all,

Whenever I log into my Ubuntu machine for some reason I always have to go through the following steps before Ubuntu picks up my wireless network...

1. Do a **sudo modprobe ndiswrapper** 
2. After running this command a msg will appear saying that **the application nm-applet wants access to the default keyring**. It asks for my password and I type it in.

Only after this will ubuntu find my wireless network.

Can anyone tell me what exactly is happening in these two steps and maybe how I can change my .profile script to ask Ubuntu to automatically perform these two steps?

Thanking you in advance

---

### Post by angelsguitar on 2007-11-07
HI.

Seems that the ndiswrapper is not loading at startup.  Just add the instruction "ndiswrapper" (without the commas) at the end of the /etc/modules file and reboot.

---

### Post by s3019293 on 2007-11-07
Thanks angelsguitar,

Well that takes care of me having to type in the **sudo modprobe ndiswrapper ** command however I am still prompted with the msg saying that the application nm-applet wants access to the default keyring asking me for my password? Any way to get around this?

---

### Post by spd106 on 2007-11-07
There's a workaround for this on the network manager help page in the wiki.
[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

Basically you need to install libpam-keyring and add a line the /etc/pam.d/gdm file.

This should not be a problem on 7.10, only on previous versions of Ubuntu.

---

### Post by s3019293 on 2007-11-08
Thanks...that worked like a treat

---

