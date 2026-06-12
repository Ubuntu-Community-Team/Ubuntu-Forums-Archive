---
title: "starting over"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by Aisthesis on 2010-05-24
Having installed ubuntu 10.04 from a disk i got from students at school, i lost my wireless connection (apparently no driver for my dell laptop wireless connection) and it appears that i have a 32-bit system, while i want a 64-bit.
 
so, i'd like to start over with a linux install. what distribution would you guys recommend for ease of installation and presence of necessary drivers--at least to get on the web so that i can download what's missing?
 
i definitely want 64-bit, and i'm not fixated on ubuntu--fedora, etc. are also fine.

---

### Post by TBABill on 2010-05-24
If you want 64 bit and deb/Ubuntu compatibility I'd try Mint 9. It's easier to setup and has all the codecs and other necessary multimedia plugins already installed. 
 
If you want fast and don't care about 32 bit or 64 bit, PCLinuxOS is the fastest distro I have used and is way simple to install (and comes setup with everything you need....no "restricted extras" to worry about). It outruns any 64 bit OS I have tried. It's RPM based, however, but uses Synaptic for software manager AND updates. It's available in KDE, Gnome, LXDE, Openbox, E17, etc., but KDE was fastest for me.
 
I like Mint 9 and Ubuntu both. But they ran hot on my laptop and I had trouble getting my CPU to scale down under light loads, which resulted in high heat. Hopefully your luck will be better and you can enjoy whichever interests you. Or try them all on separate partitions. Lubuntu is also very fast and based on 10.04.

---

### Post by nhasian on 2010-05-24
Installing mint 9 is not going to magically make the wireless adapter function if Ubuntu 10.04 didn't see it, since it is based off of 10.04 the result will be the same.

Aisthesis, go ahead and install Ubuntu 10.04 64bit and plug your laptop up to the internet via the ethernet adapter temporarily until we can help you get your wifi adapter online.

once you have ubuntu installed, go to System-> Administration-> Update Manager and check to make sure you have the most recent updates installed.  you may need to reboot after they are installed.

then go to System-> Administration-> Hardware Drivers to see if you can enable any restricted drivers for your wifi adaptor, video card, etc.

finally if you still do not have wifi, please give us the output of this terminal command:

```
lshw -C network
```

---

### Post by cascade9 on 2010-05-24
Probably a good idea to check if your system supports 64bit before you d/l the .iso (if you know its 64bit for sure, dont bother) 

> **TBABill said:**
> If you want fast and don't care about 32 bit or 64 bit, PCLinuxOS is the fastest distro I have used and is way simple to install (and comes setup with everything you need....no "restricted extras" to worry about). It outruns any 64 bit OS I have tried. It's RPM based, however, but uses Synaptic for software manager AND updates. It's available in KDE, Gnome, LXDE, Openbox, E17, etc., but KDE was fastest for me.
 

I havent tried the 64bit version of PCLinuxOS, but the 32bit version I did try was awfully slow. I might have to try the 64bit version, just to check it out.

---

### Post by theozzlives on 2010-05-24
When I did a fresh install of Lucid 64bit, I went to "Try", installed the Brodcom STA drivers, then ran install. It found my wireless just fine.

---

### Post by dFlyer on 2010-05-24
What model of Dell, I have the Studio 1735 and everything works. Chances are you need the STA wireless driver. If you can connect to a network with a cable, just run hardware drivers under system administration and it should pull in the driver.

You might want to visit the Dell community site and build your own Dell install of Ubuntu 10.04. It's very easy to do and should import all the drivers you will need. See link below.

[http://en.community.dell.com/support-forums/software-os/w/linux/building-base-ubuntu-factory-iso.aspx](http://en.community.dell.com/support-forums/software-os/w/linux/building-base-ubuntu-factory-iso.aspx)

---

### Post by TBABill on 2010-05-24
Cascade9, PCLinuxOS 2010 is still only 32 bit but it blazes. I had tried 2007 and 2009 but had different issues. The latest is faster than anything else I tried, including OpenSUSE, Mandriva, Ubuntu, Mint, Fedora, Vector and a few others, regardless if they were 32 or 64 bit.

---

### Post by cascade9 on 2010-05-24
> **TBABill said:**
> Cascade9, PCLinuxOS 2010 is still only 32 bit but it blazes. I had tried 2007 and 2009 but had different issues. The latest is faster than anything else I tried, including OpenSUSE, Mandriva, Ubuntu, Mint, Fedora, Vector and a few others, regardless if they were 32 or 64 bit.

Odd. I'll try a reinstall, but from what I saw it was seriously slow. The debian lenny when I threw it on the same machine was a lot faster. 

Maybe you are using much newer hardware than what I was playing with...thats all I can think of.

---

