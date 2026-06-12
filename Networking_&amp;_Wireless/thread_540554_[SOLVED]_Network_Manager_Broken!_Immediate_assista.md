---
title: "[SOLVED] Network Manager Broken! Immediate assistance needed!"
date: 2007-09-01
forum: Networking &amp; Wireless
---

### Post by runemaste644 on 2007-09-01
I couldnt get on my wireless network after i attempted to make my internal wireless work. Then i used a wireless card and it insisted on using the bcm43xx driver, so i did
```

sudo dpkg-reconfigure network-manager

```
and now Network Manager wont start and nothing else will sense my wireless connection! How can i fix this? My internet works on Windows so i can use it to download stuff and view this.

HELP!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by moore.bryan on 2007-09-02
*dump network-manager for [wicd]("http://wicd.sourceforge.net/") and if that gives issues, post and we can work it out.*

---

### Post by runemaste644 on 2007-09-02
Thanks! ill try wicd. Anyway i just download it to winblows and it wont recgonize it, but when i boot into linux, it recgonizes it. Here i go, into Linux...

---

### Post by runemaste644 on 2007-09-02
It has conflicts with the existing network-manager when i try to install the debian package
](*,)](*,)](*,)](*,)](*,)](*,)](*,)](*,)

---

### Post by unisol on 2007-09-02
you have to uninstall networkmanager first. then install either wicd 1.3.1 or 1.3.3.you can try this forum for help with wicd:wicd.sourceforge.net/phpbb/

---

### Post by peebly on 2007-09-02
I followed the instructions in this link.

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by runemaste644 on 2007-09-02
Thanks! ill try that now! Lets hope it works...
:-)
Yikes! it wants to uninstall edubuntu-desktop

---

### Post by runemaste644 on 2007-09-02
Wait a second! i need something for wired too!!!:mad:

---

### Post by wickstopher on 2007-09-02
wicd works for wired networks, as well.  when you follow the instructions above, it gives you a .deb package for wicd which will automatically uninstall some unnecessary components, like network-manager.  it's nothing to worry about!

---

### Post by moore.bryan on 2007-09-02
> **runemaste644 said:**
> Thanks! ill try that now! Lets hope it works...
:-)
Yikes! it wants to uninstall edubuntu-desktop
*that's okay, it's just a "meta-package;" or, a package which doesn't really do anything but list other dependencies for dist-upgrades.*

---

### Post by runemaste644 on 2007-09-02
it still doesn't work. Can i fix it by re-installing by Wubi? Wold my /home be the same? Or rescue a broken system by Live CD? The thing pretends to work but doesn't actually work. Maybe editing my interfaces file? I dunno. Maybe starting all over again...:(

---

### Post by moore.bryan on 2007-09-02
*what are the outputs of ```
lspci
``` and ```
iwconfig
``` again?*

---

### Post by runemaste644 on 2007-09-02
Here. I used a flash drive to take the file to my desktop computer with Windoze X:p

---

### Post by runemaste644 on 2007-09-02
that means XP instead of X:p

---

### Post by runemaste644 on 2007-09-02
in other news: 
Ahh, back after some relaxing time in the BUMP thread

---

### Post by moore.bryan on 2007-09-02
*okay... and what about *```
sudo lshw -C network
```*i'm trying to figure-out the exact chipset for your wireless...*

---

### Post by runemaste644 on 2007-09-03
my chipset for my wireless is bcmwl5 (bcm43xx) and there is no driver available but im just wanting my internet to work for wired. Is there a way to undo a sudo dpkg-reconfigure to set network-manager to the way it was when i installed Ubuntu?

---

### Post by runemaste644 on 2007-09-03
Besides, a hardwire connection always does better

---

### Post by runemaste644 on 2007-09-03
Wait a second! i went here [http://ubuntuforums.org/showthread.php?t=390492](http://ubuntuforums.org/showthread.php?t=390492) and he said later he had to go through his process again to establish a connection! sudo dpkg-reconfigure network-manager messed him up too!!! Get me some .deb packages for network-manager and network-manager-gnome so i can try that out and see if i get  connection! It sounds like it will work...8-)

---

### Post by runemaste644 on 2007-09-03
aargh... i connected but when i tried ubuntuforums.org it gave me some stupid pshells thing. Anyway, i just needed to reinstall network-manager and network-manager-gnome and it works now:popcorn:

---

### Post by moore.bryan on 2007-09-03
> **runemaste644 said:**
> my chipset for my wireless is bcmwl5 (bcm43xx) and there is no driver available but im just wanting my internet to work for wired. Is there a way to undo a sudo dpkg-reconfigure to set network-manager to the way it was when i installed Ubuntu?
*according to all i've read, madwifi should work for that set just fine...*
> **runemaste644 said:**
> Besides, a hardwire connection always does better
[I]i completely agree, but the convenience of wireless is **so** appealing!  ;-)
[/I]

---

### Post by runemaste644 on 2007-09-03
yeah, i would think it would be convenient to have my internal wireless working (2 peices of hardware that i dont have working in linux yet: internal N wireless, and the MS-PRO and xD part of my card reader) But wired suits me for now. The problem is the bcm43xx-fwcutter doesnt work for bcmwl5 drivers. *goes to remove the Fix my internet! part of sig*

---

### Post by moore.bryan on 2007-09-03
*like i wrote, your network card **should** work with madwifi; it's strange it doesn't.  what didn't work about wicd?*

---

### Post by runemaste644 on 2007-09-03
i don't know. Just when i reinstalled network-manager it worked. What does madwifi do?

---

