---
title: "Creating a LAN network XP-Ubuntu"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by C-Sauron on 2009-09-13
Hi!

I have two computers: one with Windows XP Home Edition and another one with Ubuntu 9.04.

Both are connected to the Internet via the same router. The Ubuntu PC has a printer connected.

I want to make the computers visible to each other and I want to print documents using the Windows XP PC.

I've heard I need to create a LAN network between the two computers, but I don't know how. I've had some clumpsy attempts using Samba in Ubuntu and the tools which Windows XP includes for creating a LAN, but it doesn't work.

Can somebody help me, please? :)

---

### Post by K7522 on 2009-09-13
You are looking for Samba, it allows networking with Windows computers.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by mapes12 on 2009-09-13
IMHO you don't need Samba and all its configuration problem. This is how I did what you have asked:

Go into Control panel in XP and enable "File and print sharing". Then go to the folder you want to share. Right click and enable "sharing". If the user account where the share is located in XP is a Limited account then you may have problems. The account needs to be given Administrator permission. Bad security but that's not my fault.

Next, on the Ubu machine go into Synaptic and install pyNeighborhood. Once installed it will be an application you can select from Applications. Click it. First some tweaks:

PyNeighborhood - Edit>Preferences
- Mount folder change to /home/username (this saves root having to do everything).
- Then "Remove mount point after unmount" = tick
- Then "File Manager" tab - add Nautilus

Then in the left hand pain right click the globe and select "Scan"

This should find your shared windoze folders. Double click the one you want in the right hand pain. This mounts it. Then right click it and select Nautilus as the file browser. You can then transfer stuff between the 2 machines.

If you have followed the above and still have problems then in my experience the problem is always with the XP machine, not Ubu. XP can sometimes lead you into thinking folders are being shared when in fact they are not. Hence my comment about Limited windoze accounts. It took me 3 days to figure that one out.

---

### Post by K7522 on 2009-09-13
An excellent alternative, Mapes thanks for that. I really haven't had any troubles configuring Samba before, but that definitely is simple you have there.

---

### Post by oldfred on 2009-09-13
Samba instructions seem to work but the issue I have had with XP also was setting the share and setting the permissions. Top level directories did not always share. Under properties, sharing, check share this folder, and under permissions, check everything but full control. I thought full control would grant everything but usually that did not work.

I have had the same issues with windows xp to windows xp sharing also.

---

### Post by C-Sauron on 2009-09-13
Thank you for your answers :D

I've tried the mapes12 method, but it doesn't work for me :(. I don't know what I'm doing wrong. I follow all the steps and when it comes to scan the shared folders, it only appears a folder called INICIOMS on the left pain, which I've tried to scan (it starts scanning when I double click it) but it fails.

By the way, I've added Nautilus by typing the name, but I have to install it from Synaptic or something? :confused:

---

### Post by mapes12 on 2009-09-13
> **oldfred said:**
> Samba instructions seem to work but the issue I have had with XP also was setting the share and setting the permissions. Top level directories did not always share. Under properties, sharing, check share this folder, and under permissions, check everything but full control. I thought full control would grant everything but usually that did not work.

I have had the same issues with windows xp to windows xp sharing also.Hello oldfred

Yep, I've tested this time and again. Most people new to Ubu think that Ubu has a problem but, as you state, it's the MS box causing the problem.

---

### Post by mapes12 on 2009-09-13
> **C-Sauron said:**
> Thank you for your answers :D

I've tried the mapes12 method, but it doesn't work for me :(. I don't know what I'm doing wrong. I follow all the steps and when it comes to scan the shared folders, it only appears a folder called INICIOMS on the left pain, which I've tried to scan (it starts scanning when I double click it) but it fails.

By the way, I've added Nautilus by typing the name, but I have to install it from Synaptic or something? :confused:I guess INICOMS is your router. This means that windows is not sharing the folders you asked it to share because the scan stops at your router i.e. a windows issue, not Ubuntu's.

Nautilus is the main file browser in Ubu. Just type its name and that's it.

---

### Post by Jerry N on 2009-09-13
I don't see the problem.  Just share a resource on the Windows side, no problem there.  To see the share from Ubuntu, look at network places.  To share a folder from Ubuntu, tell it to share.  If the proper Samba drivers aren't in place, Ubuntu will prompt you to install them.  If you have given the proper access permissions, Windows should see the Ubuntu shares without difficulty.  With Ubuntu 7.04 and 7.10 I had to modify smb.conf but this is no longer necessary.  If you are using an Ubuntu derivative like Lubuntu, forget my comments - it probably won't work.  At least in my case, and with multiple Windows and Ubuntu (or Mint) machines in the network, everything works just fine.

Jerry

---

### Post by mapes12 on 2009-09-13
> I don't see the problem. Just share a resource on the Windows side, no problem there.That's the problem. Windows doesn't play ball.....b

---

### Post by Jerry N on 2009-09-13
I've never had a bit of problem with the Windows (XP) side of networking and sharing.  No problem at all with Ubuntu 9.04 and 9.10 or with LinuxMint 7.  I tried Lubuntu and didn't get sharing to work at all.  I think it could be shortsighted to automatically blame Windows if Windows and Ubuntu aren't talking to each other.

Jerry

---

### Post by C-Sauron on 2009-09-14
Finally, I managed to share the printer (which was my main objective) :). I didn't need to use Samba. I did that with CUPS, thanks to this website: 

[http://www.soygik.com/how-to-compartir-impresoras-en-red-ubuntu-da-servicio-a-windows/](http://www.soygik.com/how-to-compartir-impresoras-en-red-ubuntu-da-servicio-a-windows/)

It's in Spanish, if anyone need that information in English I can try to translate :P Just tell me.

Tomorrow I'll try to share folders, wish me luck :)

I like Ubuntu. I always had Windows XP and it never have given me any problems, but configuring Ubuntu properly is an interesting challenge :popcorn:
Thanks for all the answers:guitar:

---

