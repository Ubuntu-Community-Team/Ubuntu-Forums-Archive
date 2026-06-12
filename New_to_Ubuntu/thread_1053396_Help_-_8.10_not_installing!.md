---
title: "Help - 8.10 not installing!"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by jezebel on 2009-01-28
Hi again -
I've decided (with this forum's help!) to reinstall Ubuntu and make my  Vista machine a dual boot...

So, I downloaded 8.10 (Intrepid), burned the ISO, and booted my pc from the cd.

I get the Ubuntu menu; I choose 'install Ubuntu', and then - nothing. My monitor glows, like it's waiting for the os to start; my pen tablet glows, knowing it has power, but the cd drive and HD are not spinning, nothing.

Same thing happens when I decided to try to run the live CD - nada.

Any suggestions, help? Please!

(I'm running Intel Core 2 Duo E8400, Gigabyte EP43-DS3R; dual monitors; Nvidia 9600; have 1 tb hd in 5 partitions. Oh, main OS is Vista).

---

### Post by avtolle on 2009-01-28
Before you burned the iso to Cd as an image, did you check the md5sum?

[http://psychocats.net/ubuntu/iso#checksum](http://psychocats.net/ubuntu/iso#checksum) on how to do it from Windows, if you didn't do it or don't know what I'm posting about.

---

### Post by jezebel on 2009-01-28
I just downloaded and ran the winmd5sum and had a match. So, I'm guessing that the iso is not the problem?

EDIT: I just put the Ubuntu boot disk in my old xp machine, and it's running Live CD just fine - problem's got to be in my hardware? Any ideas?

---

### Post by jezebel on 2009-01-28
Is it possible that Ubuntu can't recognize my Sata hdd?

---

### Post by Branimir on 2009-01-28
Perhaps your video card is not recognized?
That happened to me when I tried to install 7.10.
ctr-alt-f1 will give you prompt, from there
you can $sudo dpkg-reconfigure xserver-xorg
and you'll get screen, at least that's how it worked
for me.

Hope this helps.

Greets, Branimir.

---

### Post by avtolle on 2009-01-28
> **jezebel said:**
> Is it possible that Ubuntu can't recognize my Sata hdd?
Could be; this has been an issue with other releases. 

Take a look at [https://help.ubuntu.com/community/BootOptions#Introduction](https://help.ubuntu.com/community/BootOptions#Introduction) as to generally how to use boot options, and try "all-generic-ide" (without the quotation marks) as an install boot option.

---

### Post by avtolle on 2009-01-28
Another thing to try; from the initial menu, try Safe Graphics Mode to see if you can get around any video card problems.

---

### Post by jezebel on 2009-01-28
Branmir - I tried what you suggested, but no luck. I couldn't even get the prompt.

Avtolle - thanks for that link; I'm at work now, but will try loading the cd again later (at home). However, I don't remember the initial menu giving me the safe graphics option.

Another possible problem could be that I don't have an onboard graphics card and have to rely totally on my nvidia 9600

---

### Post by linux_tech on 2009-01-28
Try alternate install.

---

### Post by jezebel on 2009-01-28
Linux_tech -

What do you mean by 'alternate install'?

---

### Post by linux_tech on 2009-01-28
There are some instructions here
[http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)

---

### Post by linux_tech on 2009-01-28
Alternate install is text based install w/ more configuration options.
[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by jezebel on 2009-01-29
Branimir - you were right, it was the graphics card. 

In 8.1, the 'safe graphics' mode is not obvious, but easy to find. I hit F4 (for modes) and selected Safe Graphics mode, et voila!

I now have another problem, not knowing which choices to make for the manual install... I'll post this separately.

Thanks to all of you awesome forum people!!

---

