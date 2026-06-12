---
title: "Wireless on Pavillion dv2815nr"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by rugbert on 2008-05-22
First of all, Im running Fedora 8, but using ndiswrapper means that there shouldnt be much of/any difference right? Besides, these forums are way busier!

So I ran through [this thread](http://fedoraforum.org/forum/showthread.php?t=174265) which was really helpful but I cant get my car working. the drivers are installed but when trying to run 
```

iwlist wlan0 scan

```
I get 
```

wlan0     Interface doesn't support scanning.

```

Ive tried  two different drivers from HP's site listed for my HP, 37745 and the 38674 (and the drivers from the Dell site mentioned in the thread) but none of them let me scan for APs!

It shows up in Network Configuration under hardware, but not devices so I cant configure it in anyway.

And it doesnt matter if my toggle switch it on or not, or how many times i run modprobe ndiswrapper, it just doesnt work! 

This is a pretty commong laptop so someone here HAS to have fixed this....I hope!

---

### Post by Ayuthia on 2008-05-22
> **rugbert said:**
> First of all, Im running Fedora 8, but using ndiswrapper means that there shouldnt be much of/any difference right? Besides, these forums are way busier!

So I ran through [this thread](http://fedoraforum.org/forum/showthread.php?t=174265) which was really helpful but I cant get my car working. the drivers are installed but when trying to run 
```

iwlist wlan0 scan

```
I get 
```

wlan0     Interface doesn't support scanning.

```

Ive tried  two different drivers from HP's site listed for my HP, 37745 and the 38674 (and the drivers from the Dell site mentioned in the thread) but none of them let me scan for APs!

It shows up in Network Configuration under hardware, but not devices so I cant configure it in anyway.

And it doesnt matter if my toggle switch it on or not, or how many times i run modprobe ndiswrapper, it just doesnt work! 

This is a pretty commong laptop so someone here HAS to have fixed this....I hope!

Have you tried ```
sudo modprobe -r b43 ssb ndiswrapper
sudo modprobe ndiswrapper
```

Oops.  What kernel are you using (uname -r)?

---

### Post by rugbert on 2008-05-23
2.6.24.7-92.fc8

---

### Post by Ayuthia on 2008-05-23
> **rugbert said:**
> 2.6.24.7-92.fc8

Most of the rules will be the same since we are using the same kernel.  b43 was introduced in 2.6.24.  This change now causes ndiswrapper to load after ssb.  So you will need to unload b43 and ssb prior to ndiswrapper.  I am not for sure where you will need to blacklist b43 and ssb. 

I would try the modprobe combination that I mentioned earlier and see if it helps.

---

### Post by rugbert on 2008-05-24
heres my modprob.d/blacklist
```

# watchdog drivers
blacklist i8xx_tco

# framebuffer drivers
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist i810fb
blacklist cirrusfb
blacklist intelfb
blacklist kyrofb
blacklist i2c-matroxfb
blacklist hgafb
blacklist nvidiafb
blacklist rivafb
blacklist savagefb
blacklist sstfb
blacklist neofb
blacklist tridentfb
blacklist tdfxfb
blacklist virgefb
blacklist vga16fb

# ISDN - see bugs 154799, 159068
blacklist hisax
blacklist hisax_fcpcipnp

blacklist bcm43xx
blacklist ssb
blacklist b43

```

and modprobe.cof
```

alias eth0 forcedeth
alias scsi_hostadapter libata
alias scsi_hostadapter1 ahci
alias scsi_hostadapter2 pata_amd
alias snd-card-0 snd-hda-intel
options snd-card-0 index=0
options snd-hda-intel index=0
alias wlan0 ndiswrapper

```

oh yea, ndiswrapper -l gives me this
```

bcmwl6 : driver installed
        device (14E4:4315) present

```

where the drivers I used before just said installed.

---

### Post by Ayuthia on 2008-05-24
> **rugbert said:**
> heres my modprob.d/blacklist
```

# watchdog drivers
blacklist i8xx_tco

# framebuffer drivers
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist i810fb
blacklist cirrusfb
blacklist intelfb
blacklist kyrofb
blacklist i2c-matroxfb
blacklist hgafb
blacklist nvidiafb
blacklist rivafb
blacklist savagefb
blacklist sstfb
blacklist neofb
blacklist tridentfb
blacklist tdfxfb
blacklist virgefb
blacklist vga16fb

# ISDN - see bugs 154799, 159068
blacklist hisax
blacklist hisax_fcpcipnp

blacklist bcm43xx
blacklist ssb
blacklist b43

```

and modprobe.cof
```

alias eth0 forcedeth
alias scsi_hostadapter libata
alias scsi_hostadapter1 ahci
alias scsi_hostadapter2 pata_amd
alias snd-card-0 snd-hda-intel
options snd-card-0 index=0
options snd-hda-intel index=0
alias wlan0 ndiswrapper

```

oh yea, ndiswrapper -l gives me this
```

bcmwl6 : driver installed
        device (14E4:4315) present

```

where the drivers I used before just said installed.

You didn't mention that you had one of those fun cards!!!  

First thing, bcmwl6 does not work with NDISwrapper as of yet.  You will need to find an XP driver to help this work.

The reason why I say that your card is a fun card is because this card has been having some problems in Ubuntu.  I am not for sure about where the problem lies (new header files, compiler changes, ndiswrapper updates, or Ubuntu updates), but you might need to make a modification to make it work.  Please check this link:
[http://ubuntuforums.org/showthread.php?t=786397](http://ubuntuforums.org/showthread.php?t=786397)

It will provide a driver that might work, but it also gives you some information in step 2 that needs to be done to have the driver be present.

I am not for sure if Fedora has the file location at /etc/ndiswrapper/bcmwl5 or not though.  I want to say that it should be there because most of the distros I have used have it there.

---

### Post by rugbert on 2008-05-24
> **Ayuthia said:**
> You didn't mention that you had one of those fun cards!!!  

First thing, bcmwl6 does not work with NDISwrapper as of yet.  You will need to find an XP driver to help this work.

The reason why I say that your card is a fun card is because this card has been having some problems in Ubuntu.  I am not for sure about where the problem lies (new header files, compiler changes, ndiswrapper updates, or Ubuntu updates), but you might need to make a modification to make it work.  Please check this link:
[http://ubuntuforums.org/showthread.php?t=786397](http://ubuntuforums.org/showthread.php?t=786397)

It will provide a driver that might work, but it also gives you some information in step 2 that needs to be done to have the driver be present.

I am not for sure if Fedora has the file location at /etc/ndiswrapper/bcmwl5 or not though.  I want to say that it should be there because most of the distros I have used have it there.

Did you ever know that you're my hero,
and ev'rything I would like to be?
I can fly higher than an eagle,
'cause you are the wind beneath my wings.

---

