---
title: "Ipod Touch and managing on linux"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by chris88knox on 2010-08-12
Ok, I have an Ipod touch (2g) that I am wanting to manage in linux..(ubuntu 10.04)   How can I do this.... this thing is NOT jailbroken, and I would prefer not to do that....any suggestions?  Thanks

---

### Post by SlidingHorn on 2010-08-12
> **chris88knox said:**
> Ok, I have an Ipod touch (2g) that I am wanting to manage in linux..(ubuntu 10.04)   How can I do this.... this thing is NOT jailbroken, and I would prefer not to do that....any suggestions?  Thanks
Here's a couple places to get started with.  The first link is from just before Lucid was launched, so, while it may not be quite up-to-date, I still recommend reading it.  The second is a post of someone who seems to have gotten this done with some success.  It may or may not work -- nothing in the docs or wiki recent enough for me to tell you much else:

[https://help.ubuntu.com/community/PortableDevices/iPod](https://help.ubuntu.com/community/PortableDevices/iPod)

[http://ubuntuforums.org/showthread.php?t=1355610](http://ubuntuforums.org/showthread.php?t=1355610)

---

### Post by robbiemacg on 2010-08-16
If you are running 10.04, things should be pretty straight forward. I think [SlidingHorn]("http://ubuntuforums.org/member.php?u=732438")'s suggestions are sensible.
Definitely consult:

[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)
[https://help.ubuntu.com/community/Retrieving%20and%20setting%20the%20Firewire%20GUID%20%28FirewireGuid%29]("https://help.ubuntu.com/community/Retrieving%20and%20setting%20the%20Firewire%20GUID%20%28FirewireGuid%29")

And search the forums if you need to troubleshoot, but here's how my partner and I got her ipod touch to mount/synch last might.

We added the source "**[B]ppa:mcenery/ppa"**[/B]
Then reloaded the list of available packages (which you can do via synaptic or terminal).
We then installed **libimobiledevice1** and associated packages.
After that we ran "**sudo apt-get dist-upgrade**"
That pretty much solved our problems. While searching for the best solution we installed some other stuff like ifuse, etc., but these steps seemed to take care of the issues we were having with mounting/syncing the device.

We use Rhythmbox and have a machine running 10.04.

---

