---
title: "Multiple Hard Drive Duel Boot"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by waldo_phill on 2009-11-08
OK..here it goes, I am looking to set-up a duel boot system with multiple hard drives, every post I can find on the subject states to edit /boot/grub/menu.lst the thing is that file does not exist on my system.

I currently have a 40GB hard drive with widows install just sitting (the other PC's motherboard went out):rolleyes:

My system is currently running a 160GB hard drive with ubuntu 9.10 on it, plus 2 other hard dive for media :D (1.5TB and 750GB).

I would like to plug in the 40GB hard drive and set up the duel boot.

Any help would be appreciated.

---

### Post by yanceypd on 2009-11-08
You may have issues with the windows hard drive if it was the OS on dead Computer because of drivers etc setup on it.  If you have the system disk that too will not be a valid licensed PC. You might be able to use it in Virtual box. Good luck

---

### Post by QIII on 2009-11-08
If you are using Karmic and it was a fresh installation (that is: not an upgrade), then you are using GRUB2 and menu.lst is no longer applicable.

So:  

Did you do a fresh installation of Karmic?

If you did, and assuming your Windows drive is not going to complain too much about the hardware being quite different than the computer it was previously on, make sure in your BIOS settings that your Ubuntu drive is set to boot first.

Then, in the terminal, do

```
sudo apt-get install os-prober
```

You may be told you have the latest.  Just move on.

```
sudo os-prober
```

```
sudo update-grub2
```

When you reboot, your Windows OS should be available in GRUB2.

Whether or not it will work with such a different set of hardware than it expects is unknown.

---

