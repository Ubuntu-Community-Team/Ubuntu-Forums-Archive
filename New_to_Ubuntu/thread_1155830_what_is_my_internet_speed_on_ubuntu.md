---
title: "what is my internet speed on ubuntu?"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by kapi on 2009-05-11
Want to locate the connection speed in ubuntu but can't see it anywhere

any ideas?

Thanks

---

### Post by anaconda on 2009-05-11
System>Administration>System monitor.

and the "resources" tab from there.

Network history shows how fast you receive and sed data.

---

### Post by profeta81 on 2009-05-11
main menu -> system -> system monitor

under the tab "resources" there's CPU, memory and Network usage graphs... 

also you can start it from a terminal:
$ gnome-system-monitor

hope this is what you were looking for ;)

---

### Post by kapi on 2009-05-11
Sorry I'm looking for the connection speed saying that say I get 100Mbps over the internet

cant see it in resources

---

### Post by MJWitter on 2009-05-11
> **kapi said:**
> Sorry I'm looking for the connection speed saying that say I get 100Mbps over the internet

cant see it in resources

Right click on the network icon in the top right panel and click Connection Information.

---

### Post by kapi on 2009-05-11
Got it

Thanks for your help, just right clicked the wirelss network connection icon and selected connection information. am running on 54Mbps

Kapi

---

### Post by windfarm on 2009-05-11
I think 54 Mbps is the speed of the wireless connection between your PC and your wireless router/modem, not the speed of your internet connection. I say this because my wireless network ALWAYS reports it is running at 54Mbps while internet connection speeds vary by time of day.
 
To find out the speed of your connection you could use a speed checking webite - Google Internet connection speed test.
 
Hope this helps.

---

### Post by scottuss on 2009-05-11
> **windfarm said:**
> I think 54 Mbps is the speed of the wireless connection between your PC and your wireless router/modem, not the speed of your internet connection. I say this because my wireless network ALWAYS reports it is running at 54Mbps while internet connection speeds vary by time of day.
 
To find out the speed of your connection you could use a speed checking webite - Google Internet connection speed test.
 
Hope this helps.

You are right. It is not the speed of your Internet connection, 54Mbps is the speed of your wireless connection. If you see 100Mbps then you are most likely connected directly to the router via a cable, therefore it is this speed it is measuring.

---

### Post by freak42 on 2009-05-11
... and whether it's 100 Mbps or 54 Mbps.. it most likely isn't your internet speed anyway. It's the speed between your computer and router, which usually is many times greater than your actual internet speed.

---

### Post by scottuss on 2009-05-11
> **freak42 said:**
> ... and whether it's 100 Mbps or 54 Mbps.. it most likely isn't your internet speed anyway. It's the speed between your computer and router, which usually is many times greater than your actual internet speed.

That's what I said :p

---

### Post by freak42 on 2009-05-11
> **scottuss said:**
> That's what I said :p

oh.. true.. sorry my bad

---

### Post by tubbygweilo on 2009-05-11
kapi, another way to get an idea of your internet speed is to wait until you have a big update from Ubuntu and then look for something like "download speed" to be found somewhere below the progress bar. This should be a real world download speed but from comparing it to other speed test utilities such as those supplied by ISPAs it appears to run a bit faster. You could also try the same thing by downloading an Ubuntu LiveCD and watching the speed indicator.

---

### Post by Cheesemill on 2009-05-11
Downloading the latest Ubuntu Desktop torrent should also max out your bandwidth

Just select the ubuntu-9.04-desktop-i386.iso torrent from [http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/) and fire it up in your torrent client (Transmission comes as default).

Wait a few minutes and it should be downloading at your maximum speed (remember to multiply this value by 8 to get speed in bit/s which is the unit that broadband providers quote their speed).

Cheesemill

---

### Post by indigene on 2009-06-29
Still...can anyone suggest how the speed can be continously monitored. 

Is this completely dependent on the ISP, and hence one a tool provided by them can only measure?

OR Ubuntu has something or an application in any of the public repositories that can do this?

---

### Post by automaton26 on 2009-06-29
For occasional checking, you can use [http://www.speedtest.net]("http://www.speedtest.net").

---

### Post by Wim Sturkenboom on 2009-06-29
> **tubbygweilo said:**
> kapi, another way to get an idea of your internet speed is to wait until you have a big update from Ubuntu and then look for something like "download speed" to be found somewhere below the progress bar.I have always been wondering if that is in bits per second or bytes per second?

---

### Post by indigene on 2009-06-29
Perfect tool!

---

### Post by niteshifter on 2009-06-29
Hi,

Real time speed can be displayed - add the GNOME netspeed applet to a panel. It can be configured to show bytes or bits per second.

---

