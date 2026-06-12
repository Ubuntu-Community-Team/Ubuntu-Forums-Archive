---
title: "Complete beginners broadcom woes"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by kngedgr on 2008-09-03
Hello everyone! and let me be the first to say, I am terrified of posting here simply due to the overwhelming amount of knowledge being tossed around this community.

I'm new to Ubuntu, I bought this laptop for college off ebay, decided I disliked vista, and wanted to start using linux instead. I figured it would be easy and for the most part it's been great. Everything is free! which helps me out because I can't afford books. I'm A+ certified, basically means nothing. Anyway I love Ubuntu, and I'm eager to learn. Please don't flame me.

I will try to be as clear and concise as I can. Keep in mind I am a complete beginner, I don't know how to boot into a kernel or any of that stuff.

OK.

Here's my problem. I cannot connect to my wireless network. I cannot see my wireless network.

Here's my specifics.
Acer Extensa 5420-5687 Laptop
AMD Turion 64x2
Running Hardy Heron (trying to get into the lingo)

[IMG]http://img292.imageshack.us/img292/7161/helpme3np4.png[/IMG]

ok see that? me too. I tried manually putting in my ssid and wep key but to no avail. now here's the confusing part.

[IMG]http://img508.imageshack.us/img508/4374/helpme1ef0.png[/IMG]

That's my card! it's there! so, I know that it's being detected by ubuntu. I also know that it's a 4311 card. I was tyring to use that driver for linux that you can see in the top image, at the top, but I only got as far as making the blacklist file. when i tried to place it in modprobe.d it said "permission denied".

[IMG]http://img528.imageshack.us/img528/8870/helpme2ib2.png[/IMG]

ok #1 I have no clue what that disabled network thingy is, nor do i know how to enable it.
and #2 That looks like a driver to me!

one more thing. I have a switch on the front of my laptop that allows me to turn on and off my network card, that stopped working when I pooched vista for linux. It doesn't really matter though. I tried a tutorial on the support website, but I couldn't find a gnome-device-manager in the synaptics package manager so I didn't get far.

one last thing, as you can see from the first image, sorry it's big. I tried using Ndiswrapper and a ton of other things. but I couldn't figure out this kernel thing, so I only got as far as typing a few things into the terminal with errors returning to me. if there's anything you need me to clarify i will. I'm really excited with starting linux and I want to try to contribute to this community as much as i can. Any help is greatly appreciated.

---

### Post by Ayuthia on 2008-09-03
Not for sure if you have a working wired connection in Ubuntu or not, but if you do, you can try going to the Panel and trying System->Administration->Hardware Drivers.  There should be an option for your Broadcom card.  If it is not there, you can try going into Synaptic (the package manager for Ubuntu) and installing b43-fwcutter.  It will ask you if you want to have it find the firmware for you.  Select yes and you should be set (you might have to reboot).

Like I said earlier, this does require a working internet connection.

---

### Post by kngedgr on 2008-09-03
it doesn't look like a wired connection will be happening, I can't see the wired or wireless connections now.

---

### Post by Ayuthia on 2008-09-03
> **kngedgr said:**
> it doesn't look like a wired connection will be happening, I can't see the wired or wireless connections now.

You can try this link:
[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)

Go to Option 2.  It is the section for those without an internet connection.  Of course, this means that you will need to go to either another computer with a connection or if you are dual-booting (have Windows on this laptop) you can go into Windows and download the files.

---

### Post by kngedgr on 2008-09-04
I only got as far as tar xfvj broadcom-wl-4.80.53.0.tar.bz2 when I got there I got an error, saying the file isn't a bzip2 file, then I checked, and It's a tar.tar?

---

### Post by kngedgr on 2008-09-04
I take that back I downloaded the wrong file.

---

### Post by biggest lund on 2008-09-04
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by kngedgr on 2008-09-04
It worked! hooray! that wasn't too bad, Thank you for helping!

---

