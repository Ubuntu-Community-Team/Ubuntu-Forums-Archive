---
title: "Back to my Ubuntu to Ubuntu Networking issues"
date: 2018-02-24
forum: Networking &amp; Wireless
---

### Post by Stan_Meissner on 2018-02-24
I posted asking for some networking help a week ago and ended up with some dependency errors on my new Zareason desktop.  In retrospect I attribute the problems to operator error, downloading the OS on a wireless connection and getting over my head with dependency and other critical errors as a result.  I did manage to get my system running well enough to download Ubuntu from a wired connection and reinstall and it looks like this third distro is the charm as all is running great and it's an awesome computer built to my specs.

So I'm attempting to network the two Ubuntu computers and have the print sharing working and can see the laptop from the desktop and visa versa.  I have been doing some reading and even though I have Samba installed it looks like there is something called Apache that might be required for Ubuntu to Ubuntu.  As I said, I'm really close and I can see the network from my wife's laptop but can't open the public folder from either computer.  Suggestions are encouraged as I'm reading a hodge podge of suggestions up to and including entering IP addresses but I can't be sure which fix applies to me and don't want to do any damage.  This is not critical that we network but it would be nice and it looks like we're very close to having it working so any help would be appreciated.  Thanks.

---

### Post by Morbius1 on 2018-02-24
But you aren't using Ubuntu. You are using Ubuntu-Studio right? And it's not with the default XFCE desktop it's using MATE, right?

The only sharing "thing" I know about that uses Apache the way you are describing it is gnome-user-share and no one living knows how that works.

Why not just install ssh:
```
sudo apt install ssh
```
On the other machine open whatever file manager is on that one and enter this:
```
sftp://hostname
```
Replace [COLOR=#0000cd]*hostname*[/COLOR] with the host name of your machine.

Or:
```
 sftp://hostname.local
```
Or:
```
sftp://some-ip-address
```

---

### Post by Stan_Meissner on 2018-02-24
No, I decided when I had trouble with Studio and Mate to go back to the basics.  I'm running Ubuntu now with the standard desktop.  Studio was actually kind of an overkill because I am only using Gimp for layered graphics and I switched from a DAW to a Tascam DP-24 for my music and only use Audacity for a few final tweaks to the WAV and then convert it to MP3.  I had Zareason load Studio with the build but it's no big deal.  Let's start with a clean slate with Ubuntu as the OS.  I'm not a power user when it comes to terminal commands, when I get a new computer I research and install and get everything running and don't touch it again until the hardware fails five years down the road when I do it all over again.  You ask why I don't just install SSH and my reply is "what is SSH?"  

I used to network in Windows for years and it was a few clicks with the GUI and I was good to go.  This in my mind is one of the more irritating things about Linux distros is having to jump through all these hoops to do something as basic as a home network.  I've been using it exclusively since 2010 and networking is the one thing I have never been able to conquer.  I get the printer sharing going and get stuck on the file sharing part.  Responses have indicated that Linux networks have better security but my reply is why does setup have to be so convoluted as that has nothing to do with security.  Anyways, what is SSH and will it work with Ubuntu?  I'm thinking that I'm very close if the printer is working and I can see the computers on the network but I'm not going to enter any terminal commands until I know it's going to work.  I'd rather give up and buy my wife a thumb drive than goof up my system and have to reinstall again.

---

### Post by Stan_Meissner on 2018-02-27
I have decided that since I got my print sharing working and home networking is not critical to anything we're doing here to call it a done deal.  If my wife wants to view family photos and videos on my desktop she can come into my office and do that.  When the dust settles I'll research posts and videos on this subject and see if I can figure it out on my own.  Thanks to all who have offered help and I do apologize for my unfamiliarity with this subject as my ignorance of this function seems to have caused some frustration.  File sharing is the only thing I have been unable to figure out since I switched to Linux in 2010 and that is why I asked on here.  I'm still thinking that I'm close as I can see both computers on the network but mastering this task will have to wait until I retire this summer and have time to study it in detail.

---

