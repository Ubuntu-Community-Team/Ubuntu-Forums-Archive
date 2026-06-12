---
title: "Error: no such partition ARGH!"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by penalt on 2010-07-30
Hello, first off, I am a complete Linux beginner and I think I have mucked up something fierce.  Recently, I installed Ubuntu 10 on my laptop and I have enjoyed playing around with it quite a bit.  A couple of days ago, however the windows side of the computer went down so I went to run the recovery partition.  Which turned out to be non-functional, which turned out to have mucked up GRUB.

Now, when I boot the system it goes to:

error: no such partition
grub rescue>

The best I have managed to do is to get the system to once recognize a really crude Super Grub disc on boot up.  When I tried booting linux via that all I got was an Error 15: file not found.  I have also tried reinstalling Ubuntu via my disc but it even refuses to boot to that.  I need help.  Also, please remember, I am a total beginner here and so you will need to step by step any instructions.  

In advance...thank you, very much.

---

### Post by sandyd on 2010-07-30
> **penalt said:**
> Hello, first off, I am a complete Linux beginner and I think I have mucked up something fierce.  Recently, I installed Ubuntu 10 on my laptop and I have enjoyed playing around with it quite a bit.  A couple of days ago, however the windows side of the computer went down so I went to run the recovery partition.  Which turned out to be non-functional, which turned out to have mucked up GRUB.

Now, when I boot the system it goes to:

error: no such partition
grub rescue>

The best I have managed to do is to get the system to once recognize a really crude Super Grub disc on boot up.  When I tried booting linux via that all I got was an Error 15: file not found.  I have also tried reinstalling Ubuntu via my disc but it even refuses to boot to that.  I need help.  Also, please remember, I am a total beginner here and so you will need to step by step any instructions.  

In advance...thank you, very much.
What happens when you try to boot from the ubuntu cd?

---

### Post by penalt on 2010-07-30
Completely ignores it.  I have made sure that bios is looking to the dvd drive first before the HDD.  The disc spins but does not boot after about a minute the grub error comes up on the screen.  I even tried burning a fresh disc in case it was the dvd.

---

### Post by sandyd on 2010-07-30
> **penalt said:**
> Completely ignores it.  I have made sure that bios is looking to the dvd drive first before the HDD.  The disc spins but does not boot after about a minute the grub error comes up on the screen.  I even tried burning a fresh disc in case it was the dvd.
you got a usb sticK? and does your computer boot from usb?

---

### Post by penalt on 2010-07-30
Yes, I do. and yes it can.

---

### Post by sandyd on 2010-07-30
> **penalt said:**
> Yes, I do. and yes it can.
maybe your computer hates cds now... try
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by penalt on 2010-08-02
Trying different options from that.  Thank you.  Worst case scenario is I might just have to blank the whole HD using Patition Magic and install Ubu in cold.

---

### Post by oldfred on 2010-08-02
This may tell us what is missing:


Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by penalt on 2010-08-02
Success!!!!  Kneel before Zo...<ahem>

Got the system to boot using the Unetbootin tool to put an iso of Ubu onto a usb key.  Once I got up and running I proceeded to install Ubuntu from Ubuntu.  Which fixed the MBR and Grub as I had hoped it would.  It also seems to have fixed the problem with accessing the Windows partition as well.

As of right now the computer is firing on all cylinders!  Both Ubuntu and the other partition are fully functional and accessible.  Happy dance all around.  Many, many thanks for all of your excellent suggestions and ideas!

---

