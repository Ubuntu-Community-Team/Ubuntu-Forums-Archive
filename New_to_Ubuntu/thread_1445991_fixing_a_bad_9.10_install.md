---
title: "fixing a bad 9.10 install"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by Garthhh on 2010-04-03
I had a working 8.04 install on my pentium III
took the plunge & upgraded all the way to 9.10 when I installed a new HDD, I used the same 8.04 cd
things aren't working so I was going to put a newly downloaded 9.10iso on a USB,  & do a fresh install
reformatted usb w/gparted won't let me put the iso on it using the usb creator widgit 

thought I should probably check the file, but can't follow 
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

I would like to have a both a good USB version & a good cd version, so later this week I can do a fresh install on my notebook & show off how easy this is for a couple of friends as live demo

---

### Post by howefield on 2010-04-03
Open a terminal (Applications > Accessories > Terminal) and navigate to where you have stored your downloaded iso file.

Then type, 

```
md5sum name_of_file
```

"name_of_file" should be substituted with the actual name of your iso file. Once it has generated the md5sum, compare it against the relevant line in your link above.

---

### Post by s_ø on 2010-04-03
I have some issues with the usb startup creator as well. Sometimes i have to format the usb drive several times. I use the format drive option there is in the usb startup creator.

---

### Post by takisan on 2010-04-03
It could be a bad .iso. I managed to have Karmic running perfectly on a Pentium III. I'd try getting the Torrent and seeing if that .iso is bad. If not, then I'd stick with Hardy or Try Lucid (And I also had Hardy running on an AMD K6-3.)

---

### Post by Garthhh on 2010-04-03
> **howefield said:**
> Open a terminal (Applications > Accessories > Terminal) and navigate to where you have stored your downloaded iso file.

Then type, 

```
md5sum name_of_file
```"name_of_file" should be substituted with the actual name of your iso file. Once it has generated the md5sum, compare it against the relevant line in your link above.

I used:

 md5sum /home/garthh/Documents ubuntu-9.10-desktop-i386.iso
md5sum: /home/garthh/Documents: Is a directory
md5sum: ubuntu-9.10-desktop-i386.iso: No such file or directory
I don't have something right

I reformated the USB twice on gpart, nothing happens when I push the format button on the usb creator.  I'm trying to make sure even if I resort to cd I have a good burn

---

### Post by howefield on 2010-04-03
> **Garthhh said:**
> I used:

 md5sum /home/garthh/Documents ubuntu-9.10-desktop-i386.iso
md5sum: /home/garthh/Documents: Is a directory
md5sum: ubuntu-9.10-desktop-i386.iso: No such file or directory
I don't have something right

Open a new terminal and try...

```
cd Documents
```

followed by

```
md5sum ubuntu-9.10-desktop-i386.iso
```

---

### Post by Garthhh on 2010-04-04
8790491bfa9d00f283ed9dd2d77b3906
8790491bfa9d00f283ed9dd2d77b3906

perfect thanks

It's a whole new world on this machine, went from 250meg to a gig on ram
I was never quite sure if I was crashing or working before, even in it's former life as an xp machine:KS

---

### Post by Garthhh on 2010-04-04
Burned fine as a cd, the USB still isn't working, shows all the  space 7g+ being used, even though it's blank....

I'm doing a new install right now.

I can't wait to get it [unbuntu] on this machine, but I'm waiting until after I have more success on my beater machines [the pentium III & my Pentium IV notebook]

---

### Post by howefield on 2010-04-04
> **Garthhh said:**
> 8790491bfa9d00f283ed9dd2d77b3906
8790491bfa9d00f283ed9dd2d77b3906

perfect thanks

That's good, having verified that your download is good, you need to do the same for the burned CD.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Garthhh on 2010-04-04
Not quite there 
I went back to my old HDD
I made it the slave so I'm back on 8.04lts for the time being

the 9.10 build on the new HDD only worked with the live cd in.
I did a 2nd install same result
on the 3rd I installed as if it was to be a dual boot
at the end on the install when it asks to do a restart & during that remove the live cd,
grub would start to load & say no such found & give a number that resembled the hash check number [didn't write it down so it's hard to know exactly]

any suggestions?

---

