---
title: "My pc is too slow..."
date: 2009-08-19
forum: New to Ubuntu
---

### Post by cignox1 on 2009-08-19
Hi all, I'm relatively new to linux, because anytime I tried to use it, I always had a hard time making it work properly (crashes, devices not working and so on).
A few days ago I decided to move to linux on my notebox (celeron 1.6 Ghz, 256Mb of shared memory) and after a couple of days I was even able to make my internet connection working (wow).
My problem is now that it is slow as hell: far slower than Windows Xp that was installed before. Applications take even minutes to load (i.e. netbeans, eclipse), desktop menus require seconds to appear and update, switching from a window to another is very slow and even when I'm writing this text I'm experimenting lags with keyboard (symbols require even one second to appear). 
As I'm not familiar to linux I was expecting a performance boost moving from Win to linux, but somehow this did not happen. Is my system simply to slow for ubuntu to work or are there settings to make everything faster? Note that the system monitor says that only 130 Mb are being used.

In addition, Updates Manager (hope this is the name, I have the italian version) appears randomly (at least when I go on the System menu) and since it requires a couple of minutes to execute I can't do much else when it happens...

I hope that somone can help me because now my system is barely usable and I would not be forced to go back to Xp if possible...

Thank you!

---

### Post by Paddy Landau on 2009-08-19
A couple of things...

As your computer specs are so small, you probably want to load [Xubuntu]("http://www.xubuntu.org/") instead of Ubuntu. It works fine on my old computer. It's not as pretty as Ubuntu, but it works!

How large did you make your swap partition? For 256Mb RAM, I'd suggest a minimum of 1Gb based on everything I've read in these forums.

---

### Post by super kim on 2009-08-19
what version of ubuntu are you using? the system monitor will tell you what is 'slowing' your computer.

is the update manager coming up with updates? you can change how often it checks for updates.

with your system monitor look to see on the resources graphs what is low cpu or memory, check the processes to see what is using all your resources.

---

### Post by tarps87 on 2009-08-19
You should be able to run Ubuntu on your computer with reasonable performance (I've run it on lower), try running the command top in a terminal an see what is at the top of the list.
The update manager will appear whenever there are updates, this can be change by going to Software Sources. System -> Admin -> Software Sources
clicking on the updates tab, here you can change the interval or turn it off. It use to just be a notification but it appears to have changed

Just a note, I would not recommend using Netbeans or Eclipse for performance timings is it will vary with project open and the size of then. 4 - 5 minutes is standard for me at work (xp, 3.40GHz, 3GB ram)

---

### Post by themusicalduck on 2009-08-19
256mb is not enough to run Ubuntu.. I think the minimum required is 384 or something like that.

I'd recommend trying Xubuntu or maybe even try some more lightweight distros. Xubuntu should be alright though.

---

### Post by snowpine on 2009-08-19
Give Puppy linux a try if you want a real speed boost:

[http://www.puppylinux.org/](http://www.puppylinux.org/)

---

### Post by mrbiggbrain on 2009-08-19
> **themusicalduck said:**
> 256mb is not enough to run Ubuntu.. I think the minimum required is 384 or something like that.

I'd recommend trying Xubuntu or maybe even try some more lightweight distros. Xubuntu should be alright though.

Are you running 9.04? If so the only real way to get the speed on that hardware would be to install off the minimal cd, then manualy apt-get x11, fluxbox (or kde/gnome if you really want that), the reason, there will be tons of services and things that you just dont need on that hardware.

---

### Post by jrlii on 2009-08-19
256MB is not enough for Ubuntu in versions after 7.10.

My old 850MHz. 256MB laptop worked beautifully with 7.10, but slowed to a crawl with 8.04, and newer isn't going to work any better.

Indeed, the only way I was able to load 8.04 on the contraption was using the alternate, non-graphical method, 'cause the graphical installer won't run in 256MB period.

I've been meaning to try Xubuntu, but haven't gotten around to it yet.

Doing updates and making changes is much easier when you have and extra partition for /home. (Lately I've been giving that one the bulk of the disk.) That way you can blow away the system partition for a new version (or to revert to an old version) without having to worry about your data. Not having /home on a separate partition is most of why I haven't reverted to 7.10 or tried Xubuntu on that machine.

---

### Post by cignox1 on 2009-08-19
Thank you all. I remember that Suse run nice a few years ago, I even buied it but never used it due to the mentioned issues. Perhaps I could give it a try again.

The version of Ubuntu is the last available on the site (downloaded a few days ago).

I did not use Eclipse and Netbeans for timing, I actually would like to use NetBeans for my Java and C++ projects and Eclipse just because everyone is talking good things about it :-)
But Netbeans was too slow (a couple of minutes without opening projects) and Eclipse the first time hung my pc, the second I had to wait at least 5 minutes. I suppose I should look for another distro, too bad. The fact that a linux distributions doesn't work on a system when XP SP 2 runs just fine surprises me quite a bit though...

Which are the main differences between Ubuntu and Xubuntu? I'm expecially worried about my usb wireless device, I spent two days to make it work.

Thank you!

---

### Post by ayenack on 2009-08-19
Maybe a memory upgrade. Memory's cheap as hell now so stick in the maximum your system will take and it should run just fine.

I've had Ubuntu and Xubuntu running on systems with less processor power but more ram and they've run just fine. I've also had a laptop with a celeronM 1,5GHz CPU with 250MB Ram a while ago running Xubuntu 7.04 and it ran quick, better than XP.

---

### Post by Paddy Landau on 2009-08-19
> **cignox1 said:**
> Which are the main differences between Ubuntu and Xubuntu?
Xubuntu is designed for older computers with smaller specs. The display isn't as pretty, which makes sense because 'pretty' = more resources. A few programs are different, e.g. terminal. I've not noticed anything significant between the two from the point of view of using it.

I believe that the important drivers, such as wireless, are the same between the two. Note carefully what you did to get your wireless working, and do the same with Xubuntu.

You can, of course, try it out with the Xubuntu Live CD, although I'm not sure that your wireless would work like that.

---

### Post by lykwydchykyn on 2009-08-19
The main difference is that Xubuntu uses [XFCE]("http://www.xfce.org/") for it's desktop environment while Ubuntu uses [GNOME]("http://www.gnome.org/").

You don't have to reinstall to see if it will improve things for you.  Just install the xubuntu-desktop package, log out, and choose XFCE under the sessions menu.

That said, I don't know that Xubuntu is really all that much lighter.  Speed issues are always subjective, and sometimes the depend on other things like video card drivers or hard drive performance.

If you really want speed, I'd suggest [LXDE]("http://www.lxde.org/").  Just install the lxde package in synaptic, log out, and choose "LXDE" from the session menu before logging in again.

But keep in mind, all that really does is give you a lighter desktop environment.  It will reduce some of the overhead in the system, but it isn't going to make programs run any faster (well, ok it might if they don't have to do as much swapping).  

It's worth trying, anyway.

---

### Post by louieb on 2009-08-19
> **cignox1 said:**
> ... I remember that Suse run nice a few years ago. ...

LOL in 2006 I had Ubuntu Breezy (v5.10) running on a then 10 year old P1-200mHz 128mb, ram PC.  Finally gave that PC away - wonder what its doing now?    

When XP came out late in 2001 256MB ram was a lot of memory.  And even today with SP3,  it will still run - not great but OK.  If you need that PC to do a lot of things maybe not so fast then XP will fit that pretty well.

But if you want speed for a few things like surfing, email, and the occasional letter then Puppy is pretty good. or something in between might take a look at the Ubuntu based Crunchbang Linux.

---

### Post by cignox1 on 2009-08-19
> 
 And even today with SP3,  it will still run - not great but OK


Is due to SP3 that I decided to switch to linux: my notebook became really slow and I decided it was time to change.

I fill follow your suggestions. In the meantime I try to look wich distributions are there (most probably I will try with Xubuntu, I will miss Gnome though :-)

---

### Post by alexlafreniere on 2009-08-19
I second the suggestions for CrunchBang. It's even more lightweight than Xubuntu. I just love having the apt package system in as light a package as possible. If you don't like that try Puppy Linux. Both are very good distros. For a PC with those kinds of specs, OpenSUSE woul dnot be the greatest, it would run just about as "well" as Ubuntu does on your machine. However for anything that's got about 1.5ghz and 1GB of RAM, Ubuntu runs fantastically so pelase don't judge it based off your experience here.

---

### Post by alexlafreniere on 2009-08-19
> **cignox1 said:**
> In the meantime I try to look wich distributions are there (most probably I will try with Xubuntu, I will miss Gnome though :-)

The XFCE desktop environment in Xubuntu is almost identical to GNOME, just considerably more lightweight. You can even apt-get install GNOME applications, and they run perfectly. I can't live without my gedit for coding. :)

---

### Post by cignox1 on 2009-08-19
Thank you, I just installed XCFE and it looks nice enough and is considerably faster. I can live with it :-) In the meantime I will check if it is possible to add some ram (is a 6 years old notebook, so I'm not sure)...

Sorry if I sounded harsh, it's just that I hear anywhere how cool is linux and each time I try to use it I seem to have any sort of issues, compatibility, stability and so on.

Now I just have to set Samba or something similar to share data with my desktop and I'm fine ;-)
Thank you again!

---

