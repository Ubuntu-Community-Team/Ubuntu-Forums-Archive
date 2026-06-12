---
title: "Ubuntu 10.04 &amp; i855 chipset"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by Waldo222 on 2010-04-30
Hi,

I've been experimenting with ubuntu for about 3 months now and have been quite impressed. That is until today. I had a great 9.10 installation on my Dell d400 that I 'upgraded' to 10.04. I can hear the groan of the ubuntu experts now. 

Yes, I now have a nice silver brick. The 'upgrade' process completed and I rebooted to....a black screen and a bricked laptop (now re-installing 9.10). After poking around I discovered that this is a known problem.

One simple question, what is this not mentioned in the 'known issues' file? You know, I could have waited until this problem was resolved instead of thinking that the ubuntu community is not much different from the usual gang of ..... at microsoft and apple.

Great it seems that it is true, open source is not ready for prime time. I know you're not getting paid but really this one is a show stopper and not even a mention.

I had the impression that the many flavors of Linux could extend the life of older hardware. Isn't that one of the selling point of the OS?

Oh well, another cheesed off user, just like the big boys make.

OK rant ends I have to go rebuild my 9.10 loaded laptop.

:(

---

### Post by mörgæs on 2010-04-30
Welcome to the forum and to Ubuntu.

In this particular case a clean install would not have made any difference, but else you are right: That is the first to try. 

As you have already seen in 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/568779](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/568779)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541511?comments=all](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541511?comments=all)
there is a lot of attention on this bug. I think the best advice is simply keeping an eye on the bug reports for now.

Ubuntu 10.04 will come in four additional subreleases: 10.04.1 to 10.04.4 

When the bug is fixed according to Launchpad, you could wait for the next subrelease and try a live boot. Since 9.10 is working and has plenty of time left you will not be Ubuntu-less meanwhile. Some would say that now 9.10 is finally getting stable, so best is sticking to it :-)

---

### Post by nomnex on 2010-08-22
> **Waldo222 said:**
> 
I had the impression that the many flavors of Linux could extend the life of older hardware. Isn't that one of the selling point of the OS?


Try some distributions (they all provide a live CD) with your hardware. There is no need to downgrade, usually.

Check this post if you have a i855 chipset [http://ubuntuforums.org/showthread.php?t=1544048](http://ubuntuforums.org/showthread.php?t=1544048)

---

### Post by Rubi1200 on 2010-08-22
There are fixes/workarounds for Intel chipsets and 10.04; I successfully applied the workaround involving the Glasen PPA mentioned here:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

This works for i855 chipsets.
 
Kernel updates etc. did not have any negative effects either.

Of course, if you don't want the hassle (which it is not) then stick with 9.10 until things change.

---

### Post by ImConfused on 2010-12-16
I have looked up info on Fedora.  While it seems to have advantages over Ubuntu with regard to the i855 it is not as easy to set up for the home user.  9.10 is ending its lifespan in April 2011 I think.  Is there any light in sight for a smooth installation of Ubuntu for the i855 chipset by then?  The Ubuntu live CDs I have chosen up till now do not look like a smooth installation would occur.  By staying with the standard packages and upgrades I have kept my Ubuntu operating system (first 9.04 then 9.10) running relatively smoothly.  Fedora doesn't seem to have those safeguards built in.

---

