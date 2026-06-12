---
title: "NOT creating a GRUB"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by cartisdm on 2009-12-17
I have a OSX (not to be discussed on this forum - I am aware of the rules) on my 16GB SSD on my netbook.  This boots up normally when I turn on my computer.

I am want to install Linux Mint on the internal 2gb USB stick and Ubuntu NBR on a 8gb SD card.  If I select f9 during boot I can chose what drive I want to boot up, this is perfect.  I DO NOT want to have a grub loader come up automatically because I know it will screw w/ my existing OS X installation.  How can I be sure that while installing the linux OSs to their respective drives I don't put a GRUB loader?

Again, I want to be able to choose my OS by manually selecting the boot device.  Otherwise it will default boot into my 16gb SSD w/out a GRUB


EDIT: Apparently I need more than 2gb to install the OS so I can't use the internal USB stick, but the same plan is still in effect for the SD card

---

### Post by kansasnoob on 2009-12-17
Once you get to the final screen in the installer you'll see an Advanced button that will allow you to select where to install Grub or even to choose to install no bootloader at all:

[ATTACH]140364[/ATTACH]

[ATTACH]140365[/ATTACH]

You might want to review this whole thing:

[http://members.iinet.net.au/~herman546/p23.html](http://members.iinet.net.au/~herman546/p23.html)

It's a different situation but Herman did great with screenshots. It kind of gives you an idea what to expect.

---

