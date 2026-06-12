---
title: "Not booting correctly"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by Light Side of the Moon on 2009-03-11
Hi,
 I installed Ubuntu on my desktop yesterday, and I haven't gotten it to boot correctly, when Ubuntu boots, it will show the logo, and show that it's loading, but then it just will do nothing, there is just a black screen (never see the GUI except a black x for a mouse pointer briefly). However, if I boot into recovery mode and select resume normal boot, or press Alt + Shift + F1 while the Ubuntu logo is on the screen, it will boot into the GUI to log in. When I try to log in though, I get a blank yellowish screen.

I've tried a few things to try to fix it based on similar problems people have had, and I'm not really sure what I've done to be honest. I have never used any distro of Linux, and I'm used to windows (and tired of it) so I don't know much about commands in Linux or anything.

Thanks in advance for any help!

---

### Post by ajgreeny on 2009-03-11
Two questions:-

1-  Where did the CD come from and are you sure it is  good one and that the iso file it was burned from was also a good one?  You can check that with the md5sum, using the live CD if it works ok, though if it does, I suspect the iso and the burn is alright.

2-  What hardware are you trying to install to as it sounds rather like a graphics card or driver problem.

---

### Post by Light Side of the Moon on 2009-03-11
I burned the CD myself, it's an alternate download though, because I couldn't get the Live CD download to download entirely. I'm not really sure what md5sum is, but I did run the utility that is on disk to check to see if it was alright, and it showed no errors in the burn.

And as far as the hardware, I'll have to check that, I don't really remember, I only know that it's running an Intel integrated graphics chip, and it has 512MB RAM, I haven't used this particular desktop in a while, so I'm not really sure on anything else, if you need other details, Windows XP is still intact and I can find them for you. Thanks.

---

### Post by PunkLV on 2009-03-11
Intel integrated graphics chip might be the problem. At least I had one, it turned out there actually arent any drivers besides the ones that came with Motherboard.
Google your model in [http://www.google.com/linux](http://www.google.com/linux)

---

### Post by Light Side of the Moon on 2009-03-11
I Googled the model and it appears it isn't supported, any way of getting it to work?

---

### Post by PunkLV on 2009-03-11
Only one thing comes to my mind. AFAIK Linux can configure itself for your hardware, but this is done by compiling the kernel/source on your own machine via commandline. Although I probably am wrong. Sorry.

---

### Post by Light Side of the Moon on 2009-03-11
Thanks for the help PunkLV, I'll keep lookin on the internet and look around. I'll figure it out eventually, or just start completely over, I'm in no big hurry.

---

