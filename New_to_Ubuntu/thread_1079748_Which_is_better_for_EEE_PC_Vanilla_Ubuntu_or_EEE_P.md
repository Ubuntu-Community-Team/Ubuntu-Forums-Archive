---
title: "Which is better for EEE PC? Vanilla Ubuntu or EEE PC specific distros?"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by cyan on 2009-02-24
I am running Easy Peasy on an Asus 1000H. I am relatively happy with it and have been able to do just about everything I've wanted/needed with minor tweaks here and there. I am a Gnu/Linux noob and ease of use is important to me.

I am nervous, however, about using a non-vanilla flavor of Ubuntu. My fear is that at some point in the future, Easy Peasy or Crunchbang or EEEbuntu or any of the other EEEPC-centric distro developers might disappear.

Does it make more sense to use vanilla Ubuntu since, no matter how many offshoots, there will always be a community and developers for it? Is this an irrational fear?

Thanks for your input!

---

### Post by stalkier on 2009-02-24
Honestly just go with what has the best forums/help/etc. Make sure support for hardware is good and you should be good to go. Personally I love Ubuntu and I will never get away from it.

---

### Post by Old_Grey_Wolf on 2009-02-24
You can use a vanilla version of Ubuntu on the eeePC; however, you will need to modify it. I don't think this will be the solution for you since you said:

> **cyan said:**
> I am a Gnu/Linux noob and ease of use is important to me.

I understand your concerns expressed below; however, I would use one of the alternative distros, keep a backup of important data, and deal with the problem in the future if you have one. By the time the alternative distros disappear, vanilla Ubuntu may work with the eeePC out-of-the-box.

> **cyan said:**
> My fear is that at some point in the future, Easy Peasy or Crunchbang or EEEbuntu or any of the other eeePC-centric distro developers might disappear.

---

### Post by cyan on 2009-02-24
Great advice, Gray Wolf. I am trying to be good about backing up (loooove sbackup) so this reinforces what I've been learning.

Thank you!

---

### Post by Old_Grey_Wolf on 2009-02-24
> **cyan said:**
> Great advice, Gray Wolf.

Hehe, I am sure other people on the forum will disagree with me. :)

---

### Post by sgosnell on 2009-02-24
EasyPeasy, Cruncheee, and the others are just Ubuntu with different desktops and included apps.  Even if their maintainers go away, you still have Ubuntu installed.  For me, though, it wasn't that hard to get the standard Ubuntu working on my 900, following the excellent instructions found [here](https://help.ubuntu.com/community/EeePC/Fixes).  I tried several EEE-specific distros, and ended up with straight Ubuntu, giving me the same desktop everywhere except for my 701.  That doesn't have enough room on the SSD for a full install, so I put Cruncheee on it, and that works pretty well.  There is a reason there are lots of variants available - there are lots of people with lots of opinions about what they want.  The one to use is the one that works best for you.  I suggest installing many distros on SD cards and trying them out.  You'll eventually find the one you like best.

---

### Post by cyan on 2009-02-24
Thanks, SGOSNELL!

---

### Post by Hobgoblin on 2009-02-24
I use "standard" Intrepid with the [array.org](http://www.array.org/ubuntu/index.html) kernel on my EeePC 701SD.  Easy to do and works well.

---

### Post by hovzio on 2009-02-25
Hi, I use an eeepc 1000h and have had eeeXubuntu, eeebuntu and Ubuntu installed. I ended up using ubuntu, Intrepid Ibex. My other pc's all run intrepid and I just feel more comfortable having the same os on my pc's. Wireless networking (eth0 works as of intrepid) doesnt work out of the box.  As Hobgoblin mentions above; array.org has an eee kernel repo that gets things working. Another real bonus are the elmurato acpi scripts. The script gets all the hotkeys working and sets up an applet that lets you control fan usage, cpu freq. etc. Real cool stuff. heres the site:

[http://wiki.eeepc-info.de/index.php5?title=Installation_EeePC_Script_by_elmurato](http://wiki.eeepc-info.de/index.php5?title=Installation_EeePC_Script_by_elmurato)

EDIT:Sorry the above is a german site... here is one in english

[http://forum.eeeuser.com/viewtopic.php?id=39341](http://forum.eeeuser.com/viewtopic.php?id=39341)


You can download them here, this is the most recent version.Just enter in a terminal;

```
wget http://www.informatik.uni-bremen.de/~elmurato/EeePC/Intrepid_ACPI_scripts-EeePC.tar.gz

```
A good place to check things out at is:

[http://forum.eeeuser.com/](http://forum.eeeuser.com/)

Have fun, don't hesitate to try out different things;)

---

### Post by cyan on 2009-02-25
Saw the array.org posting and sounds like a good idea as well.

I guess the other thing to consider is that if it ain't broke, don't fix it. Everything is working so well, I should just continue working as I have and only change distros when I have a real need to. On my current setup, I have even managed to rip and convert some of my DVDs and then transfer to my Blackberry Storm for offline viewing. Extremely cool.

But the lure of a cleaner, faster, better install is just so compelling.

---

### Post by hovzio on 2009-02-25
> **cyan said:**
> Saw the array.org posting and sounds like a good idea as well.

I guess the other thing to consider is that if it ain't broke, don't fix it. Everything is working so well, I should just continue working as I have and only change distros when I have a real need to. On my current setup, I have even managed to rip and convert some of my DVDs and then transfer to my Blackberry Storm for offline viewing. Extremely cool.

But the lure of a cleaner, faster, better install is just so compelling.

Sorry off topic, what did you use to rip and convert those dvds?):P

---

### Post by leclerc65 on 2009-02-25
I installed Ubuntu 8.04 in my 701 (4G SSD) using the Adam's kernel, ran a program named NiceEEPc and never looked back.
Xandros is fast and easy to use, but when adding something, it is a pain in the buttocks for newbies (Asus proprietary drivers). 
With Xandros you have 1.3G free, with Ubuntu 400M free (out of 4G) so in both cases you need an external SD card to store the data anyway.

---

### Post by cyan on 2009-02-25
DVD::Rip and ffmpeg

---

### Post by ShakataGaNai on 2009-02-25
I am running Jaunty Netbook Remix on my 1000 (so "Vanilla"), albeit still in Alpha.  I'd have to say, whatever works the best for you. I prefer to still with Ubuntu direct and apply patches and things simply because then I know I've not got something screwy going on, or some little bit that has been snuck in by another publisher.

---

### Post by cyan on 2009-02-26
Shaka, when you run Jaunty, will an upgrade get you to the stable version when that's released? Or will you need to reinstall fresh?

---

### Post by ShakataGaNai on 2009-02-26
> **cyan said:**
> Shaka, when you run Jaunty, will an upgrade get you to the stable version when that's released? Or will you need to reinstall fresh?

Short answer: Yes

Long answer: Right now there are upgrades most every day, but it will "settle" once Jaunty is released, and baring me changing the repo's, stay on Jaunty.  The one down side is that right now the only thing you can install is the i386 version which might not be a bad thing for most, but a geek like me, wants the LPIA version.  So I'll end up re-installing anyway, then suffer the constant arch difference problems.

---

### Post by wisd0m on 2009-02-27
I just got an EEE Box 202. The included OS was a joke. I installed Ubuntu 8.10 via USB. The process took about 2 hours including installing all my favorite apps.

So far everything works fine. The Atom processor is a little under powered for the full Ubuntu OS though. I got 100% CPU load while downloading and installing updates. My boot time is about a minute.

I have not tried getting wi-fi working since it is 2ft from the router.

Is there an advantage to using EEEbuntu and would it work for the EEE Box?

---

### Post by sgosnell on 2009-03-01
The only advantage of eeebuntu is that the kernel is optimized for the EEEPC.  I'm not sure if the box is the same.  I have jaunty running from my SD card, and almost everything works out of the box.  With that kernel, I think Adamm's kernel is going to be redundant soon.  I have Intrepid on the SSD of my 900, and everything works with the standard kernel after some tweaking.  With Jaunty, wireless, brightness, volume, etc all worked OOTB.  I haven't tried the netbook remix, in fact I haven't even seen it anywhere.  I might try that out, but the standard desktop works fine for me, and give me the same environment on both my desktop and my EEE.

---

### Post by cyan on 2009-03-02
Thanks Shaka and all! For now I am staying put on Intrepid. Everything is working beautifully. I have heard that Koala really ups the compatibility quotient on netbooks. So I'll safe myself some heartache and only switch if needed later.

Thanks again, everyone!

---

