---
title: "the magic invisible ubuntu.... GRRRRR"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by Tomcat_alley on 2011-03-25
Okay, searched everywhere, didnt find anything, but then its an odd thing so i dont know where to start searching really

Okay, so i have a Dell Latitude D430 on my lap, lovely little machine, i want to dual boot, so i have my Win 7 installed that it came with, and i downloaded ubuntu 10, created a usb, ran it from pendrive, its all working correctly, so i install it, given it 25GB of the 60GB HDD so it can stretch its legs, installation goes without a hitch, system must restart, it does.

Dell Bios page...

Straight into windows. odd, i think to myself, it hasn't given me the OS boot option... so i go into windows settings to have a look and the boot options aren't showing another OS. so i go into disk management, check out the HDD, and the partitions are there, showing as healthy... so wipe all of ubuntu, remerge the partitions, give windows back its old territory, restart, and begin from scratch... SAME THING

so i guess maybe my usb isnt working right, so i remake it, try again

SAME THING

so maybe its the ISO... so i download ubuntu netbook and try that

SAME THING

im currently making a Mint usb to try that but its starting to look like im missing something important, there doesn't seem to be anything in the BIOS about showing OS at the start... any idea's? the usb's have all worked if i select to run from USB, but the system just wont see the OS after installation

---

### Post by Dutch70 on 2011-03-25
Well, from your post it's hard to tell what you currently have on the computer, if anything. Did you delete it again to get it ready for Mint? if not, and you have it in a state that you're expecting it to boot, but it's not then...

Please boot up to your live cd/usb,  download the boot info script from the following link & save it to your desktop. 
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")
Then open a terminal (Cntrl+Alt+T) and run the following command...

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Open that file and copy/paste the info **between code tags** using the "#" symbol in the toolbar of your next post.

---

### Post by Quackers on 2011-03-25
How many primary partitions is Windows using at the moment? You may have 4 already, which means the installer is stopping you wreck your Windows system.

---

### Post by pl@yer on 2011-03-25
Anything in you cmos settings regarding protecting bios?

---

### Post by Tomcat_alley on 2011-03-25
Currently 3 partitions, windows is the largest, then the ubuntu, which obviously has set up the swap file partition,

yes, each time i tried i wiped all extra partitions, expanded the windows partition, and started again with just the windows partition

when i have installed ubuntu, i cant get into it at all, booting from the usb allows me to run it from there, but i dont seem to be able to access anything on the ubuntu partition from there either. 

i have installed Mint now, and that's running fine as its supposed to, it gives me the option of which OS to boot when I start up, and updates going in fine, so i'm guessing there's nothing im missing on the system that needs changing. its all very strange.

---

### Post by Jerry N on 2011-03-25
> **Tomcat_alley said:**
> Straight into windows. odd, i think to myself, it hasn't given me the OS boot option... so i go into windows settings to have a look and the boot options aren't showing another OS.

Windows does not recognize Linux at all and will not show a boot option for anything other than a Windows operating system.

Jerry

Edit:  If you have Mint running, you might as well stick with it.  It's just Ubuntu with a few additions and some of the rough edges smoothed off.  Ubuntu's forums apply to Mint as well and IMO are better than Mint's forums.

---

### Post by Tomcat_alley on 2011-03-25
Dutch70, thanks for that, i'm going to be wiping mint in a second, and trying ubuntu again, so ill post up the results once i have done that

---

### Post by Perfect Storm on 2011-03-25
> **Jerry N said:**
> Windows does not recognize Linux at all and will not show a boot option for anything other than a Windows operating system.

Jerry

Edit:  If you have Mint running, you might as well stick with it.  It's just Ubuntu with a few additions and some of the rough edges smoothed off.  Ubuntu's forums apply to Mint as well and IMO are better than Mint's forums.

Nope, Mint question goes to to Mint forum. This is policy of the forums. As long a distro have their own forum it's their you for eventual help etc.
This forum only support official canonical approved distros. 


[http://forums.linuxmint.com/](http://forums.linuxmint.com/)


regards
A.I. Dude
Ubuntu Forum Staff

---

