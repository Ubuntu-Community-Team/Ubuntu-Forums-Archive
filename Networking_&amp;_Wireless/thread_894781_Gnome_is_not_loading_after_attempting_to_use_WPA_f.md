---
title: "Gnome is not loading after attempting to use WPA for wireless network"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by shaolinZ on 2008-08-19
Hi guys,

This is my first post on these forums although I've used them extensively before to troubleshoot issues I've had in the past. I've googled for about 2 hrs and searched this forum too and found absolutely nothing on the issue I'm currently having, which is driving me nuts... and forced me to boot back in windows :(. Anyways, here the issue I'm having:
[list]
[*]There was some issue or the other with the ethernet connection in the dorm here so I attempted login on to the wireless network instead. They use WPA for the encryption protocol but the defauly list available was only various WEPs and something else I've never seen before.
[*]So I tried a manual configuration instead to enter the WPA key for the network and after I attempted to connect, the connetion manager froze and would do absolutely nothing.
[*]I restarted Ubuntu but now when I attempt to log in, the orange screen doesn't go away and I can't access my Gnome desktop whatsoever. I tried using recovery mode which left me in command line, where I didn't really know what to do since I'm not even sure what's causing the issue with Gnome / Xserver here. I tried safe mode and still could not access my destop.
[*]I tried rebooting several times and killing xserver, but it did absolutely nothing. I do get this screen when I kill xserver and I googled using various terms in it to no success again.
[IMG]http://i117.photobucket.com/albums/o45/shaolinZ/fck.jpg[/IMG]
[/list]
I'm going absolutely nuts now and help would be greatly appreciated! I've used linux for at least a couple years now and switched to Ubuntu a few months ago. I love Ubuntu but this issue is incredibly frustrating. Plus all my play and work stuff is on my ext3 drive and my windows drive is too small to copy it too for purposes of backing up everything there I would need to assuming I reinstalled Ubuntu which I'm really not looking forward to (not to mention I'd loose all my data). Please help and thanks in advance.

EDIT: As you noticed, I took a picture of the screen with my digital camera and pasted the process that failed. It was stuck on the wpa_suppliment thingy forever so I finally "pulled the plug." I hope that's enough for you linux gurus to diagnose my problem here. Oh, the most annoying thing is that the ethernet is back up but my Ubuntu is screwed for now :(.

---

### Post by shaolinZ on 2008-08-19
I just realized I may have posted this in the wrong sub forum, feel free to move it to the approriate section mods. Sorry.

---

### Post by shaolinZ on 2008-08-19
Apparently it's a problem with daemon somewhere, avahi-daemon to be more specific. And I'm pretty sure now it has something to do with my iptables caused by the wpa_supplicant interface (crashing when I tried to use WPA). What I can't understand for the life of me is why it's causing my entire xsession / gnome to spaz out. Is everything packed in the kernel or something? I'm not very well versed in OS design etc, and am quite upset that something as stupid as trying to use a WPA would cause me so much trouble. =/ I downloaded and burned the live CD for 8.10 but there's no repair or "repair and upgrade" option readily available. I'm thinking of giving up on Ubuntu all together as this is fairly ridiculous, all this caused by a damn wireless manual config (gone so terribly wrong)!

EDIT: This is something I would expect from Winblows, not Linux.

---

### Post by shaolinZ on 2008-08-25
Thanks for the help guys :|.

---

