---
title: "ath0 behaviour changed in 6.10?"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by bonzini on 2006-10-29
Has the atheros wifi stuff changed dramatically on 6.10?

On 6.06 I had an ath0 interface.

On 6.10 I have an ath0 interface AND a wifi0 interface.

I see by some other recent posts that I am not the only one.

The reason I ask is that my "administration -> networking", which worked fine on install last week (let me set my WEP key for instance) now craps out and starts up the bug report system.

Thanks for any light you can shed on this!

---

### Post by spd106 on 2006-10-29
Yes, the new madwifi-ng driver creates two interfaces. wifi0 is the underlying interface and isn't used for user configuration. ath0 is the one you should setup with a key or static address etc.

The idea is that you can have multiple (virtual) interfaces named ath0, ath1, ath2 etc that can be in differnet modes or connected to different APs simultaneouly. Sadly, the tools to do this aren't included in Edgy, so you'll have to build the source form [http://www.madwifi.org](http://www.madwifi.org) to get the extra features.

wifi0 should not be in the network-admin tool, nor should it appear in the /etc/network/interfaces file. It will however appear with ifconfig or dmesg.

---

### Post by bonzini on 2006-10-29
Thanks very much for the information.

Any ideas if this might be what makes the Network Administration tool crash?

Now that I know wifi0 is supposed to be around, I'll do some digging myself.

---

### Post by bonzini on 2006-10-29
Ooops, I should have been a little more clear in my last question.

The last time I was able to look (yesterday) in the Admin tool I didn't see wifi0 there.

Now I can't look, as I mentioned, it crashes right away.  However, I can pick the network icon out of the top right corner of the screen and in my connections I only have ath0 and lo0 (no eth0 on purpose).

So in conclusion, my goal is to be able to run the network admin tool, because I'm not sure how else to configure things when I'm on the road (starting tomorrow in fact).

Thanks in advance!

---

### Post by spd106 on 2006-10-29
I'm not sure exactly what the most likely cause of the crash is, but try looking in the /etc/network/interfaces file. It's possible that this file has been misconfigured, since network-admin writes the settings to this file.  Look in **man interfaces** for the correct layout. 

You can also configure the interface from a terminal through **ifconfig**/**iwconfig**. Also **sudo ifup ath0** is quite useful once the interface is configured correctly.

Did you upgrade from Dapper or is it a clean install? I've not upgraded my laptop yet, but in a clean Edgy RC install on a separate partition the restricted modules package was not installed. I tried to install it separately afterwards but it wouldn't work. I filed a bug after the beta had similar symptoms and there has been much activity there since. Hopefully I'll get round to sorting it soon, I'm still sorting out my desktop PC after upgrade troubles.

---

### Post by bonzini on 2006-10-29
I've looked at the interfaces man page you suggested and don't see anything obvious wrong with my /etc/network/interfaces file:

[INDENT]clh@dabuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
wireless-essid Livebox-c372
wireless-key E1D48A7AFFC92C9AE692AF374C

auto wlan0
iface wlan0 inet dhcp

clh@dabuntu:~$ [/INDENT]

(I've changed some of the characters in the essid and key)

FWIW ifconfig and iwconfig seem relatively happy.  For instance I can "ifconfig eth0 down" with no complaints.

Also I can't see anything obvious in the various log files related to any network interfaces.  There is a DHCP connection trying to establish itself every so often on eth0 (whether or not I have done an ifconfig eth0 down), but I'm assuming that isn't the problem.

As I say, the wireless communications are working well as far as I can tell, it's just that pesky admin tool that is not working.

I may have to resort to the command line in my hotel this week. ](*,) 

Thanks again for your kind help!

---

### Post by bonzini on 2006-10-29
Aggh, sorry!

So with respect to your question about upgrades, I started from scratch as my 6.06 was well-worn having travelled the beta path from a previous Breezy installation.

The only . files in my home directory that I've copied over are the evolution, netbeans, gaim, and skype directories.  All of the others are fresh.

Restricted modules (installed by default AFAIK) are:

linux-restricted-modules-2.6.17-10 2.6.17.5-11
linux-restricted-modules-common 2.6.17.5.11
linux-restricted-modules-generic 2.6.17.10

FWIW my machine is a dual core 3.2Ghz P4 so the above look reasonable to me.  What's missing are the 386, (obsolete) 686, and k7 versions none of which seem appropriate.

Again, thanks!

---

