---
title: "UNR Repository for Karmic Koala?"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by completeidiot on 2009-12-23
I was having trouble going from Win 7 to UNR....so long story short
I installed Karmic Koala. According to the wiki it seemed as though getting the UNR up and running via repositories once installed would be simple. It's unfortunately not simple enough. 
I'm running k.k. i want to run UNR 
Thanks

---

### Post by spiderbatdad on 2009-12-23
It is a different iso than 9.10 desktop.
[http://www.ubuntu.com/GetUbuntu/download-netbook](http://www.ubuntu.com/GetUbuntu/download-netbook)

---

### Post by completeidiot on 2009-12-23
I realize that...but i couldn't get that one to work...so i did the regular 9.10 install and not the UNR install. It said in the wiki that 
Ubuntu Netbook Remix (UNR) may be installed in several ways:
by first installing regular Ubuntu (version 8.04, 8.10, 9.04, or 9.10), then adding the UNR repository [4] and installing the relevant packages
So i decided to do so. Now I am stuck in regular Karmic Koala....and I need to be "adding the UNR repository [4] and installing the relevant packages...." But doing this so far has not been obvious...to me

---

### Post by spiderbatdad on 2009-12-23
ok. to add the repo it might be easiest from terminal:
```
sudo add-apt-repository ppa:netbook-remix-team/ppa
```Then , it looks like you add the packages manually from synaptic. I have never tried this method...find it unlikely it is supported, but I dont know. see here for package list: [https://launchpad.net/~netbook-remix-team/+archive/ppa](https://launchpad.net/~netbook-remix-team/+archive/ppa)

---

### Post by completeidiot on 2009-12-23
not supported makes me nervous...i wish it hadn't been in the wiki (as the first option i might add) if it was a crap way to do it

---

### Post by spiderbatdad on 2009-12-23
Maybe search the community documentation first before concluding unsupported, but the very idea of unr is to optimize and require less disk space. Adding it to a full desktop install doesn't make sense to me...updates and upgrades sound nightmarish with the two combined.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
A word of warning regarding the usb creator in karmic...Don't.
Follow a bootable usb tutorial or boot a live cd from 8.10 or 9.04 (on an external cdrom if necessary) and run usb creator from there...locating your source and destination. Make sure to highlight source with left click in the creator window after finding it, or it will write the live cd to your usb. :)

---

### Post by completeidiot on 2009-12-23
I think the version of win 7 i was running was preventing the unr install (i couldn't boot from disc, etc)...would it be a good idea to just start over with UNR right away before i get too much configured? If so what's the best way to do a downgraded reinstall?

---

### Post by spiderbatdad on 2009-12-23
Hmm. Be a little patient before leaping. I have seen some issues surrounding win 7 and UNR. Let's do a little research, and maybe someone else will chime in. Something with the mbr on win 7?
At the very least You'll want to delete and repartition the ubuntu installation you have with gparted live or gparted on a live cd. Though you can do all this during the installation of UNR by manually partitioning...delete /dev/sda3, or whatever your primary linux partition (leave the swap) then add a primary partition with mount point /
With the latter method you may have to edit the /etc/fstab uuid of the swap to match...idk. (we could have the same nic ;) )
Install unr on that.

I only see an issue with the previous method of installing unr on 9.10 desktop. previously this may have worked but now a problem with the desktop switcher option.
>  Desktop Switcher 
    Allows easy desktop-mode switching between Netbook mode and Classic mode (unavailable in Ubuntu 9.10 due to a stability issue) [9]. From your wiki article.

---

### Post by completeidiot on 2009-12-23
It's a new computer, so starting over isn't the end of the world for me by any means. A reinstall is no big deal....although I'm not sure how best to go about it. However, I'm sure someone else will have this problem eventually.

---

### Post by spiderbatdad on 2009-12-23
Well. UNR is awesome. I just installed it today. I thought I couldn't get any compiz effects but i was wrong. Enabling them through the appearances menu worked, and I'm very happy to have the window ring switcher. :)

So what is the exact problem? Your computer will not boot the cd, but will boot the 9.10 cd? If so, I can only think the cd is bad, so try again with a new download. Once you fire it up the partition editor is your friend. Choose to manually create the partition, then "Forward", then highlight and delete the primary linux partition. Add a new primary partition mount point is /
If you have any other problems. Ask for more help.

---

### Post by completeidiot on 2009-12-23
The problem was that the computer had what i think was a demo version of win 7 of on it...and i couldn't get it to do anything related to UNR. For whatever reason 9.10 worked. Doesn't make sense to me either

---

### Post by spiderbatdad on 2009-12-23
You're not installing from within windows are you (wubi install)?
Have you checked bios settings to boot from cdrom? (F2 setup when computer first starts.)

---

### Post by completeidiot on 2009-12-23
I was trying that at the time. Now I'm running Karmic Koala flawlessly. Completely got rid of windows.

---

