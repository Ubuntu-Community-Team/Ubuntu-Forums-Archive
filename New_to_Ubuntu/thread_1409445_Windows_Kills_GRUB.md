---
title: "Windows Kills GRUB"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by spyd3r on 2010-02-17
Every time I boot into XP, it kills grub and I end up having to reinstall grub every single time i reboot from windows. HELP!

---

### Post by colobix on 2010-02-17
It kills grug? How?
If you mean you dont have grub anymore after you installed windows then you gonna have to restore grub using your ubuntu cd.
Is that what you mean, if yes then here is what you wana do.
Boot from the live cd, open terminal and use this command to restore your grub.
```

sudo mv /media/disk/boot/grub/menu.lst /media/disk/boot/grub/menu.lst.bad
sudo cp /media/disk/boot/grub/menu.lst.backup /media/disk/boot/grub/menu.lst

```

---

### Post by jfr1tz on 2010-02-17
maybe he means windows is "fixing" the mbr everytime it boots? like the traditional fdisk /mbr thing.

---

### Post by spyd3r on 2010-02-17
No, after rebooting from Windows it just goes into a boot loop. No grub no nothing. so i boot from disc and mount my linux partition and do a grub-install /dev/sda to get grub back... which works fine when i go in and out of linux. just when i reboot from windows it kills grub and i have to reinstall grub again...

---

### Post by colobix on 2010-02-17
Oh, well then you are able to boot into ubuntu if that is the case.?
well, then you can simply restore grub using startup manager. that will take care of the problem for you.

---

### Post by spyd3r on 2010-02-17
yea i can boot into ubuntu so long as i don't boot windows. after i reboot from windows it just goes into a loop. no grub no boot no nothing. i don't want to have to repair grub every time i boot into windows.

---

### Post by spyd3r on 2010-02-17
i think **_jfr1tz_** is on the right track, how do i stop this from happening?

---

### Post by meierfra. on 2010-02-17
Have a look at this:

[https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)

Feel free to ask if you need additional help.

---

### Post by oldfred on 2010-02-17
Are you running some sort of virus checker that sees a non-standard windows MBR and then it damages grub in the MBR. 

Some windows software is not compatible with grub2.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)

---

### Post by spyd3r on 2010-02-18
tried going back to the older grub. windows affects it the same.

---

### Post by meierfra. on 2010-02-18
Then have  look at the second link in oldfred's post.
If you need additional help, follow these [instructions ]("http://bootinfoscript.sourceforge.net/")to run the boot info script and post the RESULTS.txt

---

### Post by spyd3r on 2010-02-19
i've also tried using lilo to get to grub with the same outcome. i'm afraid the most likely culprit is McAfee or Dell crap. this is a bummer because i'm unable to remove/disable it permanently. {(will get hit by our corporate audit) [dell e6400] yes it's a work laptop} i'm afraid i'm going to have to resort to using the NT Bootloader... :(  i'm sure the solutions i have tried would have worked had it not been for McAfee.  I'll update with my results later this weekend.

---

