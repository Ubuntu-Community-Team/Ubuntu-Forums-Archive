---
title: "ubuntu 7.10 and Realtek RTL8187b wireless card"
date: 2008-02-27
forum: Networking &amp; Wireless
---

### Post by treymul on 2008-02-27
Hey guys, I am a new Linux user and I am having some problems getting ubuntu to see my wireless card.  Under device manager, this is what shows up:  RTL8187B_WLAN_Adapter.  lshw -C network shows only my ethernet card, no wireless.  I installed the adjusted drivers with ndiswrapper.  So now when i use ndiswrapper -l, i get:  net8187b : driver installed, device (OBDA:8197) present.  But nothing shows up under lshw.  I've been working on this for three solid days now and am about to give up on it all.  Anyone got any other ideas that i can try?

---

### Post by afterwego on 2008-02-27
First off if you should be using the Windows 98 driver with NDISwrapper. It is the only on at this point that is known to work.

Secondly if that doesn't help or your already doing that try this.

Open the net8187b.inf file you are using in a text editor

Search for:

```
;;****************************************************************************
;; IDs for 98SE/ME/2K/XP
;;****************************************************************************
[Realtek]
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8187&REV_0200
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8189&REV_0200

```

Change to:

```

;;****************************************************************************
;; IDs for 98SE/ME/2K/XP
;;****************************************************************************
[Realtek]
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8187&REV_0200
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8189&REV_0200
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8197&REV_0200

```

Reload the INF after that change.


I happen to have same card except mine is an 8189 and my second suggestion is actually pulled from somewhere else, but I can't seem to remember where. I have a post a couple of posts down in regards to my issues with the 8187b.

Good times!

---

### Post by treymul on 2008-02-27
Thanks for the reply.  That is the driver I installed and the changes that I have made.  The card still doesn't show up under any command other than ndiswrapper -l.  it does not show up under lshw or iwconfig.  I dont know what else to do.

---

### Post by treymul on 2008-02-28
bump

---

### Post by afterwego on 2008-03-01
Try issuing the following commands after loading the driver with ndiswrapper -i

```

sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m

```

Also add:

```

ndiswrapper

```

To the /etc/modules file. That will guarantee ndiswrapper is loading on startup.

Sorry if none of this is helpful. I'm just going through things I have tried in hopes that it helps others. :)

---

### Post by treymul on 2008-03-02
Thanks man, that did the trick. No more problems with wireless for me!

---

### Post by radtek on 2008-03-04
Thanks man! This worked like a charm for me too. Adding that line to the .inf was all I needed. I was beginning to despair.

---

### Post by afterwego on 2008-03-06
Have either of you seen any issues with dropped connections? Thats where I am sitting at this point. Are you using WEP or WPA?

---

### Post by lvleph on 2008-03-16
I am using wpa and I get dropped every couple of seconds.

---

### Post by lvleph on 2008-03-17
I am able to connect to unsecured connections, and maintain the connection without any troubles. However, wpa drops constantly. I have not checked wep as of yet.

---

