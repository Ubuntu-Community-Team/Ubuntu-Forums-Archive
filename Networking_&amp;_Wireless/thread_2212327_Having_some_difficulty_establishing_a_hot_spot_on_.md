---
title: "Having some difficulty establishing a hot spot on Intel NUC"
date: 2014-03-20
forum: Networking &amp; Wireless
---

### Post by rich14 on 2014-03-20
Hi, I am relatively new to Ubuntu.  I am running on an Intel NUC DN2820FYKH and am trying to create a wifi hot spot.  When I try to do it through the network settings, I am unsuccessful.  However, I was able to create the hotspot through the terminal by installing the "sudo ap-hotspot start" command.  My issue is that when I restart my box, I need to re-install the command.  Is there any way I can permanently install this command and furthermore, set up the hot spot on start-up?  Thanks.

---

### Post by Dreamer Fithp Apprentice on 2014-03-21
You're not really "installing" it, just running it. I't's already installed. You should state exactly what flavor of Ubuntu you are running. All of them have either scripts (to which you can add commands, including commands to run other scripts) or folders where you can put *.desktop files and/or scripts, that will run at various times in the boot process. So you just need to pick a suitable one and add that command. I use plain Openbox under Saucy, while, since you don't say, I suspect you are using Unity and whatever window manager it comes with it so our choices won't be quite the same. Nevertheless, I think you could probably use /etc/rc.local. There probably are several other choices but I think this one is probably in all *buntus and has the advantage of running early as root without you having to enter a password. So edit that file and put ```
ap-hotspot start
```on a line by itself. The last line should probably remain as it is. So you could put that on the next to the last line like so:```
ap-hotspot start
exit 0
```To edit /etc/rc.local you will need to do so as root so, for instance:```
sudo gedit /etc/rc.local
```Note that I did not include a "sudo" before the "ap-hotspot start". I don't think it would hurt but it isn't needed. If for some reason this doesn't work try searching the subject of "ubuntu autostart programs" and try the same idea in one of the other places.

---

### Post by PartisanEntity on 2014-03-21
*Moving thread to Networking & Wireless Forum*

---

### Post by rich14 on 2014-03-25
Sorry, I was in Ubuntu 13.10, but this worked! Thank you very much!

---

