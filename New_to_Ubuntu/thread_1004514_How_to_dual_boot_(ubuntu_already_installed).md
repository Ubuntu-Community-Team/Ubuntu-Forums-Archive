---
title: "How to dual boot (ubuntu already installed)"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by fletcham on 2008-12-07
Hi,

I have been using Ubuntu for just over a year. I would now like to dual boot with windows xp. I have a 500Gb HDD and a 1TB HDD with about 600 Gb of available memory left. It took me ages to get the system set up how I like it ( with compiz and AWN etc ) and would like to keep it how it is.

I just wanted to get some ideas of the best way to dual boot with XP as it sounds like it is pretty difficult when ubuntu is installed first.

Is it possible to save my entire current system on the bigger HDD and then install XP on the smaller HDD? If so how?

Sorry, im not very good with computers and would have given up on ubuntu without all your help.

thanks in advance

fletch :popcorn:

---

### Post by sportscrazed2 on 2008-12-07
well its easy to dualboot with windows installed first never did it the other way.  if i was to do it i'd probably back up ubuntu then install windows on the entire disc and then do it that way

---

### Post by kansasnoob on 2008-12-07
It's really not. The only two *difficult* things are the initial partitioning and restoring Grub.

This guide is fairly straightforward and simple:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

As far as restoring Grub one thing I'd add to their tutorial is, once you've run "sudo grub" and you're in Grub configuration mode begin with:

```
find /boot/grub/stage1
```

Because their guide assumes /boot/grub/stage1 will always be on "(hd0,0)" which is likely but not always true!

Here's another guide to restoring Grub:

[http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11](http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11)

---

### Post by billgoldberg on 2008-12-07
It is a bit harder to dual boot if Ubuntu is already installed, just because Windows will replace the Grub with it's own mbr.

So just partition the drive as you would on a normal hdd (or use another hdd) and make sure you have a copy of the "super grub disk" live cd, so you can put the grub back afterwards.

---

### Post by som1special2 on 2008-12-07
Hopefully this will help:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

if not please check the sticky on this page labeled "new users start here":

[http://ubuntuforums.org/forumdisplay.php?f=326):P](http://ubuntuforums.org/forumdisplay.php?f=326):P)

---

### Post by fletcham on 2008-12-12
Thanks for your help here. I so nearly had it all sorted following the guide provided by Kansasnoob - Cheers.

It just all went wrong on the last step when I was restoring GRUB. Again I used the instructions provided by Kansasnoob and used code: find /boot/grub/stage1, which showed (hd0,1). So I used (hd0,1) in the commands and not (hd0,0). It all seemed to work fine so I restarted my computer and it went into the GRUB screen. There were about 11 different options here, most look the same, but for each one i select it says "Error 17 - cannot mount selected partition". So ANNOYING!!!

If i press 'e' on the GRUB options the command lines show 
(hd0,2). Shouldn't this be showing (hd0,1). 

This is what i did to restore grub.:

1 boot using live cd
2 in terminal enter:
  :sudo grub
  :root (hdo,1)
  :setup (hd0)
  :quit

Can anyone help with this problem, I dont know what else to try.

Pleeeeaaaase help!!! :)

Fletch :popcorn:

---

### Post by zvacet on 2008-12-12
From live Cd run 

```
cat fdisk -l
```

and 

```
cat /boot/grub/menu.lst
```

and post it here.

---

### Post by fletcham on 2008-12-12
I am at work now, but will post the results this evening. Thanks

---

### Post by sturdy on 2008-12-12
Hi fletch,

Warning: I am an Absolutle Beginner but here is what I did:

Most computers allow you to press a function key at boot to select the boot drive. I had XP on C: (hd1) so wanted to put ubuntu on D: (hd2). I removed the power connector on hd1 which left only hd2 avail (for safety). Then I booted and installed from a ubuntu LiveCd. Of course the installation was to hd2. Now I have both XP (hd1) and ubuntu (hd2)installed and select which OS by pressing f8 at startup.

I like this setup because it is as simple as it gets. KISS is good...

HTH,
Sturdy

---

