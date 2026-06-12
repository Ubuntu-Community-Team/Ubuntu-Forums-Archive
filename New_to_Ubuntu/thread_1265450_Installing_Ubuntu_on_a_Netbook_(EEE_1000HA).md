---
title: "Installing Ubuntu on a Netbook (EEE 1000HA)"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by Aphid on 2009-09-13
This question has probably come up before and you're thinking to yourself, why did he bother to register, just to post another question on a forum that doesn't really seem like it is specifically for that purpose. But... I'm not actually asking HOW to install it, I'm asking WHAT to install. 

I'm preparing to wipe Windows XP from my little netbook, because I'm ready to stop using it and move back to having an Ubuntu system again. It's been a long time since I had one and I'm looking forward to the move back again. I don't really need Windows for the specific products that I've needed for school, since I'm graduating this December (yay!). 

Anyway, when wanting to install Ubuntu on my little netbook, I've hit the problem of which type of Ubuntu I want to install. There's so many choices now for the netbook that never used to be there. Easy Peasy, Eeebuntu, the Remix from Canonical... and I'm frankly confused about which to do. 

I want to be able to update the Ubuntu system when it comes out, and have the full functionality of Ubuntu, and yet, I'm rather new to Ubuntu so actually "fixing" a regular install to work on my netbook could be entirely too difficult for me, possibly.

So I'm curious about your opinions... what should I use as my OS? Any ideas?

(And if I actually did post this on the wrong forum, or it isn't a good topic, I do apologize.)

---

### Post by ibizatunes on 2009-09-13
I would go with the ubuntu netbook release
[http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)

will work really well, on your netbook!

---

### Post by rob-ward on 2009-09-13
I would probably use either Ubuntu remix or eeebuntu. I would be tempted to download both and have a play as a live image.

When you do install them I think that if you install the ubuntu remix you will need to enable the jaunty backports to get WIFI working(think).

EDIT: Correction you don't need the backports : EDIT

Give them ago, if you don't mind playing around then you could always install both see which you get working and go with that.

---

### Post by Aphid on 2009-09-13
A couple of quick questions then: 

1) Is that link that ibizatunes gave me the same as the Ubuntu Remix?

2) Is the upgrading of the Ubuntu Remix (and the ibizatunes link if they're different), seamless? Or do you have to reinstall again to get the newest kernel and whatnot?

---

### Post by ibizatunes on 2009-09-13
The link i gave is the ubuntu netbook offical download location, 
ubuntu netbook remix or eeeubuntu will work i would install ubuntu netbook remix, as it will be update faster when ubuntu 9.10 rather that waiting for other people to customize it.... but it a personal choice

If you install, install using a manual partition table, and use ext4 instead on ext3
for / which need to be about 8gb
1Gb of swap
/home the rest
but make sure it ext4 as it will run quicker, and if you want to do a clean update, if you format your / partition you dont need to backup your personal data :-)

---

### Post by snowpine on 2009-09-13
Hi Aphid, I would recommend starting your Linux-on-netbook adventure with "regular" Ubuntu 9.04 Jaunty Jackalope. It is the original, "flagship" Canonical product and in my opinion the most stable and polished "flavor" of Ubuntu. Many users also like the Ubuntu Netbook Remix, which is basically the same except for an "iPhone" type of launcher interface (which I personally don't like). Eeebuntu, Easy Peasy, etc. are all 3rd party products that are not officially supported by Canonical; basically there is no guarnatee they will be stable and well supported over time. (Lots of 3rd party Ubuntu "remix" projects fizzle out when their maintainers move on; eeeXubuntu and Fluxbuntu come to mind).

Keep in mind you can try any Linux distribution as a Live CD or USB with no change to your computer. Most of us try a few before settling on one we like best; it is sort of a rite of passage. I really do recommend starting with "regular" Ubuntu, because unless you've tried the original, you can't really appreciate what each "remix" does differently. Good luck! :)

---

### Post by winotree on 2009-09-13
> **snowpine said:**
> ....Most of us try a few before settling on one we like best; it is sort of a rite of passage. I really do recommend starting with "regular" Ubuntu, because unless you've tried the original, you can't really appreciate what each "remix" does differently. Good luck! :)
Well -- I was going to say something that seemed so important at the moment, but after reading these words, I'm speechless.  Well said.  ;)

---

### Post by Aphid on 2009-09-13
I have used the original Ubuntu before, though I will admit that the last one I used was Hardy Heron. In fact, it's still installed on the little Netbook that my wife uses (the EEE701). 

It sounds like the best idea is to go with the original and just play with it. I just hope I can figure out enough about it that things will work okay. The hugest thing about it is that I really need wifi and the sound card. Other than that, I can have lots of time to twiddle with it and play with it later. ;)

Thanks for all the great responses though, they've been excellent.  

(And yes, I hate the iPhone-like launcher. It was in Xandros and there was a reason that OS disappeared off my computer really fast.)

---

### Post by K7522 on 2009-09-13
> **Aphid said:**
> (And yes, I hate the iPhone-like launcher. It was in Xandros and there was a reason that OS disappeared off my computer really fast.)

You can easily enable and disable it by going to System > Preferences > Switch Desktop Mode. I switch between the two a lot on my netbook, the UNR seems to run cleaner than desktop version on my netbook. Whatever your choice, good luck!

---

### Post by Rex Bouwense on 2009-09-13
Welcome.  I too have an EeePC 1000H.  I bought it with Windows because I couldn't get it with Ubuntu where I was located.  To make a long story short, I installed Jaunty UNR on it.  I was first going to dual boot Ubuntu and Windows but I really did not have a need for Windows any longer.  I have been playing around with Hardy for over a year on my old desk top and decided to "go for broke."  I am pleased with my choice.  I still have minor problems but the people on this forum are very helpful.  Most of the time the question has been asked and answered already so help is out there.

---

### Post by t0p on 2009-09-13
I've got Eeebuntu installed on my EeePC.  Wifi and webcam work right away.  That's down to the array kernel, I believe.  Lots of people here like Netbook Remix though.

---

### Post by LewRockwell on 2009-09-13
[http://ubuntuforums.org/showthread.php?t=1222961](http://ubuntuforums.org/showthread.php?t=1222961)

[https://wiki.edubuntu.org/HardwareSupport/Machines/Netbooks](https://wiki.edubuntu.org/HardwareSupport/Machines/Netbooks) 

.

---

