---
title: "Trying to get a modem to work"
date: 2014-03-08
forum: Networking &amp; Wireless
---

### Post by peyre on 2014-03-08
I have a new (to me) laptop, a Sony Vaio VGN-CR510E from ca. 2008, running Xubutu 13.10 64-bit.  I'd like to get a modem working in case I need to dial up when I'm staying at a relative's house (they don't all have WiFi). This Vaio comes with a built-in winmodem, but we all know how shaky those are to get to work.  It seems to be a Conexant; I've run scanModem and attached the resuting file here.  It seems to be a Conexant.  I've tried getting it to work (even tried the drivers from linuxant, IIRC), but no love.  Maybe it's because I'm running 64-bit?  Dunno.

So, as a second choice, I plugged in my wife's USB modem.  It's a Zoom Series 1063, Model 3095.  I figured that'd be a safe bet since Cardbus modems always worked flawlessly on my old laptops.  But KPPP says it can't open the modem when I query it.  lsusb reports this for it:
```
Bus 005 Device 002: ID 0803:3095 Zoom Telephonics, Inc. 
```

Anyone have any ideas?

---

### Post by phidia on 2014-03-08
[This site]("http://xmodem.org") has links to maybe even get the laptop's modem functioning. It's been quite a while since I had to set up a dial up modem but you will need to install wvdial as well. Although not updated the official Ubuntu documentation on modem configuration is [here]("https://help.ubuntu.com/community/Modems").

---

### Post by peyre on 2014-03-09
Thanks.  xmodem.org seems to be kind of out of date and not easy to find what you need.  The Ubuntu documentation is also limited in what it offers.  I never expected the build-in winmodem to be easy to set up, but I thought the USB modem would work fine since it worked when I plugged it in to my old laptop to see if it worked with Ubuntu.  Different computer, different version of Unbuntu, 32 vs 64 bits?  I don't know what's causing it to pratfall on this machine.

---

### Post by phidia on 2014-03-09
Do you think you could get the windows drivers for your internal modem (or the usb external modem).
Maybe you could use [ndiswrapper]("http://en.wikipedia.org/wiki/NDISwrapper") to get one of those modems working.
There is more information [here]("http://books.google.com/books?id=YkptQV6f7L8C&pg=PA90&lpg=PA90&dq=ndiswrapper+dial+up+modem&source=bl&ots=tsJso46fvr&sig=hts_aXYZnHXFmeGO9VzjXiYfv1Y&hl=en&sa=X&ei=JiQdU7O6NIfyqQGqz4DYDQ&ved=0CDcQ6AEwAg#v=onepage&q=ndiswrapper%20dial%20up%20modem&f=false") about dial up modems but that re-enforces my own bias which is that only serial modems were fully supported in linux. 
Still you said you had it working in an older computer so maybe?

---

### Post by peyre on 2014-03-10
I can certainly get the Windows drivers for the internal modem, but I wouldn't expect them to help since it's a softmodem.  Now the USB modem might work with them.  I'm surprised though--the USB modem came with Debian drivers, which I installed, but my system still didn't see it.  This makes me suspect none of this will work in 64-bit.  I think I'll try reinstalling Xubuntu but in 32-bit; I was toying with the idea anyway.

---

### Post by peyre on 2014-03-11
Well...no, that doesn't seem to be it.  I've reinstalled with Xubuntu 32-bit, installed the drivers that came with the USB modem (in handy .deb format even!), but still the computer doesn't recognize either the internal or the USB modem.  :(

---

### Post by phidia on 2014-03-11
I once set up serial modems and even performed trouble shooting/checking with att code.
That was quite some time ago though. 

Are you using PPPconfig to set up your modem and connection? See the debian guide [here]("http://gr8idea.info/os/tutorials/debian-gnome/dial.html") maybe?

I know you said you had the usb modem working once (things get removed from newer kernels unfortunately) but in my memory most usb modems were also winmodems.

Doing a little more searching I found this: > Just get a Rosewill RNX-56USB. It's $25 and works great with Ubuntu. Just remove modem-manager as it will grab it by mistake (Ubuntu bug #496206) and limit Gnome-PPP to 230400 max else the modem will drop to 9600 baud.
I have messed with softmodem drivers in the past and I don't have the time for them anymore. For those who do, the devs on the linmodem mailing lists are very helpful.   Maybe you could find that modem and have it work for you?

---

### Post by peyre on 2014-03-12
Yeah, it looks like a hardware solution might be the way to go here.  When all else fails...

---

### Post by peyre on 2014-03-24
Well!  

I bit the bullet and purchased a Rosewill RNX-56USB.  On my main system (the one that doesn't need it, of course), GnomePPP recognizes it as /dev/ttyACM0.  But my laptop doesn't recognize it at all, go figure.  Both machines are running 13.10 32-bit.

Now I don't know what to do.

---

