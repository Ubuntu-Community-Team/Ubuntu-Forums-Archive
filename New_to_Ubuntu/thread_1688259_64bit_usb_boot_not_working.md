---
title: "64bit usb boot not working??"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by tnt87 on 2011-02-15
finally had enough of windows so im trying Linux. ubuntu is my first option but i want to do a test run with it using the usb function but it wont work. says it cant find a certain file something something 32. im running asus ul30vt win7 at the moment. i have dont the usb install and have tried to boot it from the usb but am getting that error.

---

### Post by mikewhatever on 2011-02-15
If you get an error, please post the exact text.

---

### Post by tnt87 on 2011-02-15
- i start my computer
- press esc
- choose to boot from flash drive (e drive)
- i get an error saying it cant find the vesamenu.c32
That is all that happens and i have to restart to get into windows

---

### Post by oldfred on 2011-02-15
There are a couple of bugs, do either of these workarounds work?

syslinux errors help/enter works:
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779)
Delete ui in syslinux.cfg
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382)

---

### Post by tnt87 on 2011-02-15
ok i trying the help command when i get the error msg in ms-dos, doesn't work.
As for the changing of a UI i have no idea how to do that im currently looking through CFG editors but not sure what to do after that. they guy prescribing the remedy doesnt provide a how to.

---

### Post by tnt87 on 2011-02-15
further update...
the error msg say "could not find kernal image: vesamenu.c32
any ideas?

---

### Post by Hakunka-Matata on 2011-02-15
Hi, USB creation is sometimes problematic.  rather than try to convince you of that, maybe you'd like to read this URL, on your situation exactly.
[http://www.linuxquestions.org/questions/linux-newbie-8/could-not-find-kernel-image-on-usb-ubuntu-682465/]("http://www.linuxquestions.org/questions/linux-newbie-8/could-not-find-kernel-image-on-usb-ubuntu-682465/")

---

### Post by tnt87 on 2011-02-15
Thanks for the reply. Read through it and trying some of the solution that it suggests. ill get back to you.

---

### Post by BananaPeal on 2011-02-15
If you're trying to run ubuntu64 off of a usb drive i highly recommend pendrivelinux.com ... worked for me... super easy for win7 going to ubuntu, although now I can't install video drivers just right. more on that later, but i'm booting correctly and all.

---

### Post by tnt87 on 2011-02-15
Ok nun of that stuff worked im going to try the pen drive bananapeal suggests. brb

---

### Post by tnt87 on 2011-02-15
just an update on what i have tried.
typing "help" in ms-dos
typing "install" in ms-dos
i have copied vesamenu.c32 throughout the boot menu
tried the pendrive bananapeal suggested.

still same error msg "could not find kernel image: vesamenu.c32"
im running an asus ul30vt.

any other suggestions?

---

### Post by tnt87 on 2011-02-15
nope none of it is working

---

### Post by tnt87 on 2011-02-15
running ubuntu 10.10 from USB offcially doesnt work on asus ul30vt. If you know otherwise then please contact me on [email]t.n.telesnitsky@gmail.com[/email]. Thanks.

---

### Post by Hakunka-Matata on 2011-02-15
How do you have the USB stick formatted, FAT16 or FAT32?  It should be FAT16 you know, correct?

---

### Post by Hakunka-Matata on 2011-02-15
I think I just misspoke, 16 or 32, which is right?

---

### Post by Cracklepop on 2011-02-15
Are you using usb-creator-gtk, or unetbootin?  

I forget which, but a boot image created with one of them refused to work on my Asus netbook, I had to switch to the other.

---

### Post by Hakunka-Matata on 2011-02-15
Yeah, I've had all sorts of different kinds of problems with USB sticks, but always got them to work just by trying different formating and programs to format with.  unetbootin has always worked, eventually.  Looks like tnt87 went away.  Persist, it'll work eventually...............

---

### Post by tnt87 on 2011-02-17
ok just to get back to it and call this one solved. Unfortunately i dont know how it exactly happened. i used a diffrent usb (not sure why) and it just worked.... i dont know much about computers but the Lexar USB didnt work and Verbatium did. Now that you guys mention it the Format may be diffrent though. i was using the Linuxusb installer and it offers fat32, perhaps this is the problem not sure.

To sum up try using diffrent file formats [Hakunka-Matata]("http://ubuntuforums.org/member.php?u=735950") recommends fat16. Thanks to you all for the help to.

---

### Post by tnt87 on 2011-02-17
how to i mark this as solved...

---

### Post by Hakunka-Matata on 2011-02-18
Mark as Solved using **_Thread Tools_** Upper right hand side of page  Glad to see you have it working

---

