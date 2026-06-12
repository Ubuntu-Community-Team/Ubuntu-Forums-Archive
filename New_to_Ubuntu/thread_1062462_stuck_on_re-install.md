---
title: "stuck on re-install"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by 10sJunkie on 2009-02-06
I have been trying for over a month (with various results) to get a server distribution installed and up and running. I can't tell you how many problems I've had, overcome and had again. I've started over more times than I can count and now each successive attempt seems to bring more more bugs, glitches or surprises.

I'm using the "Perfect Ubuntu Server 8.40" tutorial... anyone have something else to offer?

TIA

---

### Post by punx45 on 2009-02-06
thats kinda general, you will probably have to tackle specific problems one at a time.

i can say you should probably try burning a new install disc, at a low speed to reduce the chance of errors, and also checksum the disc image that you downloaded.   wherever you got the image from should have provided an MD5 hash.   google MD5 checksum on how to do it and tools for whatever OS you are creating the install disc on.   

i dont know if this tutorial is giving you a custom distro or what, but the other option is to get the latest stable standard server edition straight from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
and then install each server tool one by one and resolve the issues as they come along.   thats how i did it.

---

### Post by DGortze380 on 2009-02-07
> **10sJunkie said:**
> I have been trying for over a month (with various results) to get a server distribution installed and up and running. I can't tell you how many problems I've had, overcome and had again. I've started over more times than I can count and now each successive attempt seems to bring more more bugs, glitches or surprises.

I'm using the "Perfect Ubuntu Server 8.40" tutorial... anyone have something else to offer?

TIA

Can you please be more specific about the issues?
Let's start with your hardware, what are you trying to run on?

---

### Post by 10sJunkie on 2009-02-07
I'm pretty sure the computer is sufficient. I got it new last month. It has a dual-core pentium processor (2.2GHz 1M), 2GB DDR2 memory, 250GB 3G SATA Hard Drive and a 1Gigabit network interface card (in addition to the standard ethernet adapter).

It is one of those that you have built to order from Tiger Direct. Ubuntu 8.04 came installed on it and it ran fine but they had only put in the base package so I had to go in and add packages and tweak settings in an effort to get ISPConfig to install.

At one point I had everything including ISPConfig up and (as far as I know) running fine but then I changed my internet service provider in order to get a static IP and when I went in to reconfigure the network interfaces and hostname, things started going wrong.

Then I realized I needed to reconfigure ISPConfig also (to give it the new static IP address) and I could find NO info on how to do that so I scrapped the whole install and decided to start over from scratch and now I can't even update the sources.list. I get an error message about failing to resolve the address and ending with the kind advice that I should "try apt-get update".....

grrh.

---

### Post by DGortze380 on 2009-02-07
Ok, slow down. Who is your ISP? You currently have a fresh install of 8.04 Server??

---

### Post by 10sJunkie on 2009-02-07
I have a business class internet account at Comcast. That is the only way to get a static IP where I live. I have their equipment here - it is a fancy 4 port modem. So I connected the server directly to the modem and connected my wireless router to another port.

Right now I have a clean install of the base system and I am trying (again) to get the networking configured. It seems to work fine as long as I leave the networking/interfaces file alone - but the default setting is DHCP and everybody says you've GOT to have a static IP for a server....

:)

Did I mention I've never done this before?

---

### Post by 10sJunkie on 2009-02-08
Ok. I got the networking up but when I try to install new packages I get a dpkg-preconfigure error. When I try re-linking /bin/bash to bin/sh, it tells me there is no such directory

---

### Post by punx45 on 2009-02-11
are you downloading .deb files to install?   most things you can install from the repositories.  just do 
```

sudo apt-get <package name>

```

sometimes package names might not be exactly what you think so you can 
```
aptitude search <package name>
```
and it will come up with anything similar.

---

### Post by 10sJunkie on 2009-02-12
Got this solved by starting over again.... don't know why it worked but it did. System is up and running now. Thanks!!

---

