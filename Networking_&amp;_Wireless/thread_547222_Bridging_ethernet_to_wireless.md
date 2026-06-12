---
title: "Bridging ethernet to wireless"
date: 2007-09-09
forum: Networking &amp; Wireless
---

### Post by aldenhg on 2007-09-09
I've got an XBox 360 (yes, MS is evil but I like Halo and they still lose money on every console sold) that is nowhere near my router and running Cat-5 isn't an option and neither is spending $100 on the MS sanctioned 360 Wireless adapter. After a bit of poking around I found the Linksys game adapters which are basically 1 port ethernet to wireless bridges, but I'd rather not go out and buy more crap. So here's what I want to do: Take my laptop, plug the 360 into the ethernet port and have the 360's traffic get routed through the wireless and on to parts unknown. I've already messed around with bridge-utils to no avail, but that was probably because I didn't know what I was doing.
For those who haven't worked with 360s before you can set the wired port to use a static IP address or DHCP. DHCP would be better for me.

---

### Post by aldenhg on 2007-09-11
bumpity bump

---

### Post by malaprohibita on 2007-09-19
I'd love to see an answer for this too.

---

### Post by lungdart on 2007-09-22
I am currently in the mists of doing the exact same thing with an xbox (non 360)

Computer room upstairs with wireless/wired router. Xbox downstairs with no network. Can not run a cat5 either. Boo urns.


I grabbed and old computer from my Fathers house which was "too slow" for him to use. Fresh linux install and its running great. Then my brain chimes in. If this little pig is going to be downstairs next to the xbox and TV doing some wireless bridging, it might as well run a mythtv backend and put a front end on the xbox. Plopped in a TV tuner card, and a wireless broadcom card.

Mannaged to get my broadcom card working using fwcutter.

Right now I am in the process of putting together the wireless bridge. After some research I found this site. [http://linux-net.osdl.org/index.php/Bridge](http://linux-net.osdl.org/index.php/Bridge)

It has very simple instructions.

1) Download bridge-utils
```
sudo su -p
apt-get install build-utils
```

2) Make sure both cards work, then disable them and setup the bridge
```
ifconfig eth0 0.0.0.0
ifconfig eth1 0.0.0.0
brctl addbr mybridge
brctl addif mybridge eth0
brctl addif mybridge eth1 
ifconfig mybridge 192.168.0.125 netmask 255.255.255.0

```

What this does is gets rid of both cards IP address so that the bridge can worry about that. Then it makes a bridge called mybridge. It then adds both cards to the mybridge bridge. Then you assign mybridge an IP address adding the computer itself to the network as well (without this step, the computer bridging will not be on the network, just a pure bridger. This is for security reasons, but I want to be able to access the machine as a myth tv backend.)

As soon as my ssytem is done updating, I will be doing this myself. So its not a garuntee yet. Let me know if it helped in your situation.

---

### Post by Bikerbob on 2007-12-11
So how did this project pan out?

I found that site as well, but then end of that page states that what I want to do .. share the wireless connection to the network does not work in linux without a lot of heartache.

I have this.

1. main pc - runs windohs! and some various linux distros that I like to play with.

2. G3 mac - running ubuntu fiesty 7.04 and working well.

Computer 2 uses the wireless on box 1 through a bridge I created on XP.

I want to have this working even if I am running a linux distro at the time. 

So what I want is a bridge that allows both machines to access the net as two individual machines like it does now when the first is running XP.

Anyone?

James

---

