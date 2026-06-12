---
title: "help me help me filesystem squash failed"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by fatharraxman on 2010-11-10
how to deal wiyh this message on my boot 
busyBox v1.15.3 (ubuntu 1:1.15.3-1ubuntu5)bulit.in shell(ash)
Enter 'help' for list of built-in commands (initramfs)mount: mounting dev/loop1 on//filesystem.squashfs failed: Input/Output error
can not mount/dev/loop1c/cdrom/casper/filesystem.squash on "filesystem.squashfs"
[COLOR="Red"]this happened after I uninstalled ubuntu and reinstalled it to increase the ubunt space inside windows 7 startr in my hp 100 mini now I can not use ubuntu please help me I am for waked  complete night I can not sleep withou an ubuntu again in my laptop[/COLOR]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=175207&stc=1&d=1289397974[/IMG]

---

### Post by Hippytaff on 2010-11-10
Did you install with wubi or 'real dual boot?

---

### Post by fatharraxman on 2010-11-10
I installed it from USB then from Wubi all the same message

---

### Post by Hippytaff on 2010-11-10
And does the live environment work from usb (ie can you boot from the live usb ok)

---

### Post by fatharraxman on 2010-11-10
no 
I downloaded it twice thought the problem from the files but in vain I made disk repair scan and defragment uninstall and reinstall for two days trying to find errors and fix it in vain went to bios and set default all in vain

---

### Post by Hippytaff on 2010-11-10
What graphics card to you have?
 
When you get dumped into busybox try
```

acpi=off

```
If that doesn't work
```

start x

```
If that doesn't work post back

---

### Post by fatharraxman on 2010-11-10
> **Hippytaff said:**
> What graphics card to you have?
 
When you get dumped into busybox try
```

acpi=off

```
If that doesn't work
```

start x

```
If that doesn't work post back

acpi=off gave me nothing when i tried start x it said :
> /bin/sh:start:not found

---

### Post by Hippytaff on 2010-11-10
Sorry, should've been
 
startx (no space)
 
[http://computergyan.wordpress.com/2009/12/31/solving-the-busybox-black-screen-problem-in-grub2ubuntu9-10/](http://computergyan.wordpress.com/2009/12/31/solving-the-busybox-black-screen-problem-in-grub2ubuntu9-10/)
 
Try this, I think this mightbe a but though :-s
 
Though having said that, I had a similar problem with a different distro and it turned out my iso was corrupt - so maybe check the md5sum
 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by fatharraxman on 2010-11-10
> **Hippytaff said:**
> Sorry, should've been
 
startx (no space)
 
[http://computergyan.wordpress.com/2009/12/31/solving-the-busybox-black-screen-problem-in-grub2ubuntu9-10/](http://computergyan.wordpress.com/2009/12/31/solving-the-busybox-black-screen-problem-in-grub2ubuntu9-10/)
 
Try this, I think this mightbe a but though :-s
 
Though having said that, I had a similar problem with a different distro and it turned out my iso was corrupt - so maybe check the md5sum
 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

same startx not found

---

### Post by Hippytaff on 2010-11-10
Try those links ^^ and also can you post the specs of your pc?
 
If the liveUSB dumps you into busybox then my initial thoughts would be corrupt iso. If ubuntu has worked before, even more so.
 
Wubi often goes wrong after a while, so no surppise there. So maybe download an iso, checksum it, Burn to CD at the lowest speed (make sure you burn the iso image rather than the file) and see if you can boot from that. If the specs of your laptop are less than 1GB ram, then try lubuntu instead.
 
Let me know how it goes :-)

---

### Post by fatharraxman on 2010-11-10
> **Hippytaff said:**
> Try those links ^^ and also can you post the specs of your pc?
 
If the liveUSB dumps you into busybox then my initial thoughts would be corrupt iso. If ubuntu has worked before, even more so.
 
Wubi often goes wrong after a while, so no surppise there. So maybe download an iso, checksum it, Burn to CD at the lowest speed (make sure you burn the iso image rather than the file) and see if you can boot from that. If the specs of your laptop are less than 1GB ram, then try lubuntu instead.
 
Let me know how it goes :-)

i tried another iso and downloaded two others but the same 
the live usb also the same and the web site is not solving [COLOR="Red"]anything please help[/COLOR]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=175205&stc=1&d=1289397974[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=175206&stc=1&d=1289397974[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=175207&stc=1&d=1289397974[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=175208&stc=1&d=1289397974[/IMG]

my RAM IS 1 GB
i dont have cd rom it is an hp mini

---

### Post by fatharraxman on 2010-11-10
**[B]*_[COLOR="Red"]some one help me please[/COLOR]_***[/B]

---

### Post by Hippytaff on 2010-11-10
Might be a bug...not sure what else to offer :-s

---

### Post by fatharraxman on 2010-11-10
is there any ubuntu geek to help please????
I solved it after I  changed the creator program into linuxlive usb creator and re create the bootable flash
thank you

---

### Post by fatharraxman on 2010-11-10
**[B]*_[COLOR="Red"]:confused:[/COLOR]_***[/B]

---

### Post by fatharraxman on 2010-11-10
:confused:
i am waiting for some one 
or for a miracle
or  a geek
it should be fixed
:popcorn:

---

