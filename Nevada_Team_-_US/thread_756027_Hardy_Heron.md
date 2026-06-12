---
title: "Hardy Heron"
date: 2008-04-15
forum: Nevada Team - US
---

### Post by StefAndrew on 2008-04-15
I finally broke down and decided I didn't want to wait for the full release in another week or so.  So I shrank my HD in Vista to free up 20gb of space and installed the Beta.  No matter what though, it seems like I can't make my Dell wireless work without disabling IPV6 from /etc/modprobe.d/aliases.  This fixes it everytime, but kind of annoying to have to do so.

Anyway.  Has anyone here installed Hardy yet?  I personally love it so far.  The wallpaper is really cool, and appropriate.  It's definitely becoming more and more polished every release.

I also tried out the WUBI install from inside Windows and I'm happy to say it worked like a charm too, but I wanted to have Ubuntu on it's on REAL partition.

What has your experience with Hardy been?

---

### Post by phaeussler on 2008-04-15
Hi,

I am using the hardy beta since more than two weeks on an old DELL inspiron 2500 laptop. Until I updated some packages yesterday evening everything went fine concerning the wireless lan. Then, yesterday evening I updated again all new packages. After the update my wireless lan is now broken. When I boot the system the lan is configured for ipv6. Since my router is not cappable of this it dosen't work.

The work around I found is this: I must open the network configuration tool, switch to "static IP adress", add IP settings, re-enter the WEP key and apply these settings. When I do this the lan interface is again configured vor ipv4 afterwards and everything works fine.

The problem is when I reboot the system everything is broken again. The settings are switched back to ipv6 and I must repeat the work around.

As I said this problem occurred after the package upgrade yesterday evening. Before everything was ok.

Is it possible to turn off ipv6 completely? If so how could I do this?

Best regards
pascal

---

### Post by StefAndrew on 2008-04-15
> gksudo gedit /etc/modprobe.d/aliases

Find this line:

> alias net-pf-10 ipv6

And change it to:

> alias net-pf-10 off

That *should* turn ipv6 off.  That seems to fix it for me and I don't have to worry about it anymore.  Just reboot afterwards and that should make it easier to connect.

---

### Post by Twintop on 2008-04-15
I've been running Hardy on my desktop machine since shortly after the Gutsy release (before Alpha1 was out), and it's been, for the most part, rock solid and has only improved in reliability.

I installed it on my Dell Laptop (XPS m1210) when the Beta came out (upgrading from Gutsy) and have only had issues with VirtualBox (using the Gutsy packages because no Hardy packages exist) seizing up randomly, and, my Wifi not working with WEP for a few days because of a regression in the driver for my card.

In both cases, it seems that the Compiz-Fusion support has been improved quite a bit both in support for video cards and features. Upgraded packages in general is something that is a Good Thing (TM), but the new PulseAudio is still kinda shaky. All in all, Hardy > Gutsy.

---

### Post by Neon Lights on 2008-04-15
I had been using it on and off since alpha 3, and full time since beta. =]
it's quite nice, though I was /really/ disappointed they delayed the theme. =/

---

### Post by StefAndrew on 2008-04-16
There was supposed to be a new theme?  I thought I remembered hearing about a new theme, but never read any real details about it.

---

### Post by Neon Lights on 2008-04-16
Mhm, Hardy was going to have a complete makeover, but 'twas deferred to Ibex.

---

### Post by Twintop on 2008-04-16
I had the new theme for a while before they pulled it. You can get *most* of that delayed theme back if you switch to Human-Murrine. I still don't fully understand why it was delayed until 8.10...

---

### Post by Neon Lights on 2008-04-16
No no no :P Human Murrine was just a simple improvement. Ibex is getting a *complete* redo of the theme, including a gdm face browser by default, updating the color palette, and I think I read a redone icon theme.

---

### Post by StefAndrew on 2008-04-30
Well, now that I have the full release installed, everything is working like a charm, minus wifi and closing lid to go to sleep.  I am going to try ndiswrapper for my wifi when I remember to try it out.  I have the drivers ready to go, I just forget to try it out when I get home from work.  It blocks my personal laptop from work.

---

