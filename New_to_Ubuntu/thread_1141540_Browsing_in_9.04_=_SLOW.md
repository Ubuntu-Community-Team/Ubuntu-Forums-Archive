---
title: "Browsing in 9.04 = SLOW"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by Ginoxy on 2009-04-28
login into the system it self is very fast but unfortunately accessing some youtube is not ! if im accessing youtube.com i can watch clips in a normal way but if the clip it self on ther site or blog it gives slow motion picture and lagging and i think it is from firefox but i was mistaken again coz even opra has the same issue ! 

however some other flashy things like java or flash is not working probably with firefox !

---

### Post by NightwishFan on 2009-04-28
Did you install the flashplugin-nonfree package?

---

### Post by Ginoxy on 2009-04-28
how can i install that file ? 
im not sure if i did so

---

### Post by Praxicoide on 2009-04-28
Look for it in Synaptic.

EDIT:

If you want to install it and remove any free versions, run this:

```
sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install flashplugin-installer
```

Flashplugin-installer is the name of the nonfree package in Jaunty. Installing flashplugin-nonfree will make the machine install this one anyways, so it doesn't really matter.

---

### Post by Ginoxy on 2009-04-28
so is it free or not free !

---

### Post by Praxicoide on 2009-04-28
Adobe's flash is non-free, in the sense that it is not open source. It is "free of charge" to users.

There is a project called Gnash which is an open source version of flash (code that can be freely distributed and improved upon), and so far they are adobe flash 7 compatible. Unfortunately, this is not yet enough to view YouTube, which requires Flash 9 or 10.

---

### Post by Tibuda on 2009-04-28
> **Ginoxy said:**
> so is it free or not free !

It is free like "free lunch" ([there's no such a thing]("http://www.amazon.com/Theres-Such-Thing-Free-Lunch/dp/087548297X")), but not free like "free speech" or "freedom".

---

### Post by Ginoxy on 2009-04-28
the question is that in the previous version it was working GREAT but now i need to download something which is not free and may be not compatible and then it might works well !

---

### Post by Praxicoide on 2009-04-28
If you had it working GREAT, then you probably had the nonfree plugin installed. The plugin provided by the installer IS compatible, and unless you have other unrelated issues, such as video card compatibility, WILL work great.

---

### Post by chrisod on 2009-04-28
It could be Compiz. It was not enabled on my laptop on 8.04 - when I upgraded to Jaunty Compiz was turned on by default and it was painfully slow on my laptop. Once I disabled Compiz all was back to normal.

---

### Post by Andrew_P on 2009-05-04
I noticed that browsing with Firefox 3 in a clean install of Ubuntu 9.04 was extremely slow.  Even a site like Google ([http://www.google.com/](http://www.google.com/)), which, due to its simplicity, is normally rendered in less than a second, would take upwards of 8-10 seconds under 9.04.  Another site that I like to use as a test case, Weather Underground ([http://www.wunderground.com/](http://www.wunderground.com/)), which completes loading and rendering in about 8 seconds on my 2.4 GHz Intel Celeron laptop under Ubuntu 8.10 or Windows XP, failed to complete in 10 minutes (yes, that's right, MINUTES) under Ubuntu 9.04.  The problem doesn't appear to be the browser: When a file transfer is completed, the browser seems to handle it an normal speed.  However, the network file transfers seem to be extremely slow.  The machine is on a wireless 802.11 WiFi link running at about 38 Mb/s, connected to a 1.5 Mb/s DSL service.  I also noticed that under 9.04 it took about two (2) minutes for it to establish a WiFi connection with the Netgear router, usually with a couple of failures requiring manual restart, while the same machine, running in the same location, would connect to the router in 20-40 seconds, or less, with 8.10.  I didn't try plugging the machine directly into my wired network, as this laptop needs to work wirelessly and it wouldn't be of much use plugged in.

Something appears to be seriously broken in this release.  I played with it for a few hours, then scrubbed 9.04 from the hard drive and reinstalled 8.10.  It looks like it would be better to wait for 9.10 this October and hope that it works better.

---

### Post by NightwishFan on 2009-05-05
I have never noticed any slow browsing speed in Firefox by default, personally. The only time I did was when I accidentally installed using a bad CD, that leads to more problems then you would think.

---

### Post by Durden on 2009-05-05
It's ipv6 in firefox. Go to about:config in the URL bar and search for ipv6, set it to true (should be at false). Problem solved.

I've had to do this as well at the system level for some other things I run, you may have to too.

---

### Post by Scunnered on 2009-05-05
**Durden**

Like you I altered the ipv6 setting but still at times things are very slow.

I am wondering if it is my wireless connection that slows things down. Has anyone any ideas ?

---

### Post by Insanity01 on 2009-05-05
> **danielrmt said:**
> It is free like "free lunch" ([there's no such a thing]("http://www.amazon.com/Theres-Such-Thing-Free-Lunch/dp/087548297X")), but not free like "free speech" or "freedom".

free lunch? 
i thought they said ubuntu is free speech and not free beer (this is just random and has nothing to do with the actual thread here)

---

### Post by Andrew_P on 2009-11-20
> **Durden said:**
> It's ipv6 in firefox. Go to about:config in the URL bar and search for ipv6, set it to true (should be at false). Problem solved.

I've had to do this as well at the system level for some other things I run, you may have to too.

Even though there's a push to go to IPv6, the world is, in fact, mostly still running IPv4 at the user level (there's no IPv5).  I don't think I have a single piece of hardware in my LAN that's using IPv6.

It's too bad that the Ubuntu designers are apparently running their development experiments in a laboratory setting, not in the real world.:(  It's like the Web designers who create sites to run at 2000-pixel screen resolutions, but forget that there are lots of folks out there viewing the Web on quarter-VGA (320x240 pixel) screens on their portable wireless devices.  Linux was supposed to be about an operating system that would happily run on slow, ten-year-old hardware with a fraction of the memory required by Microsoft Vista.

---

### Post by queBurro on 2009-11-21
> **Praxicoide said:**
> Look for it in Synaptic.

EDIT:

If you want to install it and remove any free versions, run this:

```
sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install flashplugin-installer
```

Flashplugin-installer is the name of the nonfree package in Jaunty. Installing flashplugin-nonfree will make the machine install this one anyways, so it doesn't really matter.
+1, thanks for that, you've no idea how much frustration you've just gotten rid of with that single line of script and a short explanation :)

---

