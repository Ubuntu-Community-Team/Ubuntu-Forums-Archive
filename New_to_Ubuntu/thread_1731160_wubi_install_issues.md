---
title: "wubi install issues"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by aliasandy on 2011-04-16
i tried to use wubi to install ubuntu on my laptop today, it was going well until the end, when it said that it could not find certain files and to check the log which said "04-16 20:46 ERROR  root: Could not retrieve the required installation files" i have only tried it with the ubuntu desktop, not any other i.e. kubuntu etc, it was trying to install 10.04 LTS, any ideas on what i could do to get both linux and win7 running on my computer, oh btw im rockin a dell 15r, thanks for any help

---

### Post by scott-ian on 2011-04-16
Did you had your computer connected to the Internet during the install?

---

### Post by K_45 on 2011-04-16
I think that is a bug with 10.04, do you have 10.04.2? Otherwise I'd just use 10.10. Personally I'd dual-boot rather than use wubi.

---

### Post by scott-ian on 2011-04-16
> **K_45 said:**
> I think that is a bug with 10.04, do you have 10.04.2? Otherwise I'd just use 10.10. Personally I'd dual-boot rather than use wubi.
A dual-boot is better, but repartitioning can be difficult.  If it is a viable option, a dual-boot is the best.

---

### Post by aliasandy on 2011-04-16
yes it was connected to the internet for the duration of the install attempt, id like to be able to test out ubuntu in a method that is easier to reverse than a dual boot

---

### Post by K_45 on 2011-04-16
Reversing a dual boot isn't difficult, more info here:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Try wubi with the 10.10 release.

---

### Post by aliasandy on 2011-04-16
Ive heard that linux has difficulties with amd sometimes, my laptop is running an amd and is 64 bit, is there anything i need to do about this, or just download the 64 bit 10.10 iso

---

### Post by scott-ian on 2011-04-16
> **aliasandy said:**
> Ive heard that linux has difficulties with amd sometimes, my laptop is running an amd and is 64 bit, is there anything i need to do about this, or just download the 64 bit 10.10 iso
It is often a good idea to install 32 bit, even on a 64 bit machine.  Here are instructions on the matter: [http://ubuntuforums.org/showthread.php?t=958935](http://ubuntuforums.org/showthread.php?t=958935)

Ubuntu is better than windows in many regards.

---

### Post by K_45 on 2011-04-16
> **aliasandy said:**
> Ive heard that linux has difficulties with amd sometimes, my laptop is running an amd and is 64 bit, is there anything i need to do about this, or just download the 64 bit 10.10 iso

I'm running an AMD system too, the 64-bit .iso is fine. You should also check the CD isn't corrupted here:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by aliasandy on 2011-04-16
yea, im actually fairly familiar with md5 checksums, but could you tell me where i could find them to check against

---

### Post by K_45 on 2011-04-16
> **scott-ian said:**
> It is often a good idea to install 32 bit, even on a 64 bit machine.  Here are instructions on the matter: [http://ubuntuforums.org/showthread.php?t=958935](http://ubuntuforums.org/showthread.php?t=958935)

Ubuntu is better than windows in many regards.

Not any more. In 2008 sure, but now as with Win 7, unless you have an old machine or 2GB or less of RAM, go with 64-bit. 

To the OP, the MD5SUMS file is here:

[http://releases.ubuntu.com/10.10/](http://releases.ubuntu.com/10.10/)

scroll midway down.

---

### Post by aliasandy on 2011-04-16
okay, found the md5s, checked it and it matched, so i burned it to a dvd and booted it, got a screen with a flashing _ then a message that was up for to little time for me to read it mentioning linux, then back to the _ screen and nothing, had to manually power down then back up

---

### Post by K_45 on 2011-04-16
Try pressing F4 during boot and selecting the safe graphics mode.

---

### Post by aliasandy on 2011-04-16
press f4 after booting the live cd?

---

### Post by K_45 on 2011-04-16
Yes, and select safe mode. If that won't do it, we can try additional boot options or a text based installer.

---

### Post by aliasandy on 2011-04-16
I pressed f4 while it was booting and got to the start screen with options to boot a live session etc, then i booted a live session and got stuck at the same screen

---

### Post by K_45 on 2011-04-17
Did you see safe mode: - ?

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by aliasandy on 2011-04-17
no i did not, i will try that soon, currently working on other stuff, results to follow

---

### Post by K_45 on 2011-04-17
If that doesn't do it, we can try an alternate text based install:

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

---

### Post by aliasandy on 2011-04-17
it only gave me the options for driver update, OEM install or normal

---

### Post by K_45 on 2011-04-17
Try the text based installer:

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

---

### Post by aliasandy on 2011-04-17
currently burning the alternate amd64 image, any hints on what i need to do

---

### Post by K_45 on 2011-04-17
Nothing to do but boot it up and see what happens.

---

### Post by aliasandy on 2011-04-17
it brought me to the language screen then to select what i wanted to do and i hit install ubuntu, then a black screen with just the backlight on

---

### Post by K_45 on 2011-04-17
And this was with the alternate CD? Does Windows 7 boot up fine?

---

### Post by aliasandy on 2011-04-17
yes it is the alternate installer, and win7 still boots as well as it usually does

---

### Post by K_45 on 2011-04-17
Your hardware might not be supported by this kernel. Last thing I can think of to check is to boot up the 11.04 beta - this has a newer kernel and it will be released officially by the end of the month. The live cd is here:

[http://mirror.anl.gov/pub/ubuntu-iso/CDs//natty/](http://mirror.anl.gov/pub/ubuntu-iso/CDs//natty/)

as Beta 2. This has an updated kernel which should detect your GPU chipset.

---

### Post by aliasandy on 2011-04-17
Found this forum post regarding linux on my specific machine: [http://ubuntuforums.org/showthread.php?t=1633642](http://ubuntuforums.org/showthread.php?t=1633642)
should i try it without acpi and what would that affect, i dont know what it means

---

### Post by K_45 on 2011-04-17
Disabling ACPI will disable a lot of options related to power management, such as sleep. Not a good idea. I'd try the latest Beta before that.

---

