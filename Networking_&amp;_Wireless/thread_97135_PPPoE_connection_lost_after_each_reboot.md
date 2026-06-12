---
title: "PPPoE connection lost after each reboot"
date: 2005-11-30
forum: Networking &amp; Wireless
---

### Post by nsa_767 on 2005-11-30
Hi, I've just installed Breezy (fresh install, not an upgrade) and I seem to have to run *pppoeconf* every single time after a reboot.

I.e. I run *pppoecof*, setup the internet connectin and tell it to connect at startup. Then, when I reboot and startup the system again, there is no connection. 

Issuing *sudo pon dsl-provider* tells me some plugin is loaded, but there is still no connection. In order to get on the net, I again have to run *pppoeconf.*

Searching the forum, I found some reference to Bug 10080 ([https://bugzilla.ubuntu.com/show_bug.cgi?id=10080)](https://bugzilla.ubuntu.com/show_bug.cgi?id=10080)), but this doesn't seem to help.... The line "*pre-up /sbin/ifconfig eth0 up*" is already in my "*/etc/network/interfaces*".

Help, please???? It all worked fine in Hoary....

---

### Post by mips on 2005-11-30
This is not going to help you but what adsl device are you using, brand&model ?

---

### Post by nsa_767 on 2005-11-30
not exactly adsl, its a wireless 64k connection but it works over pppoe-wan miniport, or atleast that is what windows says. I can say what make/brand, since the transceiver is enclosed in aerial/dish ontop of the roof. 

:(  I had this setup and working for well over two months in Hoary using pppoeconf only once.

---

### Post by mips on 2005-11-30
Ineteresting, whos the ISP, got a link ?

---

### Post by nsa_767 on 2005-11-30
I don't think that is going to get us anywhere, since it is a small local ISP, but if you want.... My ISP's internet address:

[http://www.aerosat.co.za](http://www.aerosat.co.za)

The thing is, the connection works... I'm connected right now, but when I restart the PC, it won't work and I'll have to run pppoeconf again. After running pppoeconf it will again work, but I don't want to run pppoeconf everytime I boot the system. 

Remember, everything worked perfectly in Hoary.

---

### Post by nsa_767 on 2005-11-30
EDIT: This did not work....

Ok, I'm going to try editing /etc/network/interfaces along the lines of what was done in the following thread: [http://ubuntuforums.org/showthread.php?t=75687&highlight=pppoe+connection+problem](http://ubuntuforums.org/showthread.php?t=75687&highlight=pppoe+connection+problem)

Hope this works....

EDIT: Here is the terminal output related to first post...

> 
******@******:~$ sudo pon dsl-provider
Plugin rp-pppoe.so loaded.


Eventhough this plugin loads, there is no connection, I'm only able to connect after running pppoeconf, afterwich I'm connected and it also states "Plugin rp-pppoe.so loaded."... Odd???

---

### Post by mips on 2005-11-30
Post your /etc/network/interfaces here.
Anything of interest in /var/log/messages ?

---

### Post by nsa_767 on 2005-12-01
/etc/network/interfaces before following advice on [http://ubuntuforums.org/showthread.php?t=75687&highlight=pppoe+connection+problem:](http://ubuntuforums.org/showthread.php?t=75687&highlight=pppoe+connection+problem:)

> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet static
	address 192.168.1.2
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 196.14.120.2 66.110.110.4
	gateway 196.168.1.1

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

# added by pppoeconf
auto eth0

    pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf



/etc/network/interfaces after following advice on [http://ubuntuforums.org/showthread.php?t=75687&highlight=pppoe+connection+problem:](http://ubuntuforums.org/showthread.php?t=75687&highlight=pppoe+connection+problem:)

> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
#iface eth0 inet static
#	address 192.168.1.2
#	netmask 255.255.255.0
#	network 192.168.1.0
#	broadcast 192.168.1.255
#	# dns-* options are implemented by the resolvconf package, if installed
#	dns-nameservers 196.14.120.2 66.110.110.4
#	gateway 196.168.1.1

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

# added by pppoeconf
auto eth0
	iface eth0 inet manual # as per advice on forums

    pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf



Both of the above variations have no effect on the problem.

As for the /var/log/messages... What would you call interesting? My n00b brain is having difficulty making heads or tails of it...

---

### Post by mips on 2005-12-01
Looks ok to me.

Have a look at this thread,  [http://ubuntuforums.org/showthread.php?p=403124#post403124](http://ubuntuforums.org/showthread.php?p=403124#post403124)

If you still cannot get it going maybe look at the script option on the last post in that thread.

Alternatively stick a router between your PC and the Satelite box and let it handel the PPPoE stuff.

Do you use static addresses on Aerosat ?

---

### Post by nsa_767 on 2005-12-01
I've always used static on my Linux box and on Windows it also seems to be using static... There is no DHCP service, if that clarifies things.

BTW: I'm on my windows now, Breezy is a little unstable. I did update it and it has all the current patches/fixes, but I have odd things like Firefox stalling when I try and print... :-( I miss Hoary....

---

### Post by mips on 2005-12-01
Does Breezy do anything for you that Hoary does not ?

I myself am not to impressed with Breezy and I'm probably gonna wipe it from my laptop soon.

---

### Post by nsa_767 on 2005-12-01
Well, I wanted to try the latest version of R, which doesn't work on Hoary.... But yeah, for the most part, I could live without Breezy and all it's news bell and whistles. 

I've been searching the forums and there seems to be quite a few pppoe-related complaints... I'm definitely not the only one...

---

### Post by Dov on 2005-12-01
This may sound really simple, but I'm a new user and  had the prob of losing most of my settings on each reboot - untill I set the system to save changes after each session in 'Sessions' in the System/Preferences tab.
I still haven't got my ppp running @ all though!!!

---

### Post by nsa_767 on 2005-12-01
Hi Dov, thanks for the suggestion, but I already tried that and it didn't work...

Oh, I see this is your first post, so welcome!

Mips, I checked out that link... Haven't tried it yet, but I doubt it'l work... Will try tomorrow. I now need to get my out-of-date windows back in a usuable condition.

Thanks for all your help.

---

### Post by Reshin on 2005-12-05
Modified it so that 'pppoe maintained' lines are before 'auto dsl-provider'
> # added by pppoeconf
auto eth0
iface eth0 inet manual
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider
Worked for me :)

---

### Post by nsa_767 on 2005-12-06
Thank you for all the suggestions, unfortunately I don't have Breezy anymore... 

As noted before, Breezy on my system was a little buggy (though I am sure I'm an "isolated incident") and due to pressure from other users of the system I've ended up changing distro... But don't think me a traitor, I'll be back for Dapper!

So, thank you again for all the help. This is truly a great community.

---

### Post by mips on 2005-12-06
Mind if I ask what distro you moved to ?

---

### Post by nsa_767 on 2005-12-08
Switched to Fedora Core 3... It's worked out OK... I'm not that impressed with up2date and yum, a bit slow for my liking, but all the programs I want and need are available for it.

I didn't really want to go for an RPM-based system, but I was afraid that the problem my PPPoE might also be in other Debian-based distros.

Anyway, it seems to be working (Fedora that is...)... But ask me again in a week or two....

BTW: When I was looking for info on this problem, I found quite a few similar posts... This suggest the problem is relatively common... Someone should maybe make a wiki-page or a sticky thread in the forums on how to solve this...

Thanks again for all the help.

---

### Post by Wagner on 2005-12-14
[QUOTE=Reshin]Modified it so that 'pppoe maintained' lines are before 'auto dsl-provider'

Worked for me :)[/QUOTE]

It worked just fine for me also.

Thanks.

---

