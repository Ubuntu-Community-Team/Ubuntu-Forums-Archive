---
title: "Trying to automate my wireless connection..."
date: 2006-12-31
forum: Networking &amp; Wireless
---

### Post by CalumII on 2006-12-31
I've got a wireless connection using a Belkin F5D700UK with an rt61 chipset on Kubuntu (Dapper).  The driver automagically loads and the hardware all works.  I've got a Linksys ADSL modem and a Belkin router, both of which should be chaining DHCP.  The whole setup works in windows.

Now, I can get it to work perfectly, by following this procedure (discovered through much trial and error).  

1) Run wlassistant and attempt to connect to my router.  This inevitably fails.

2) Issue the following arcane commands:

sudo iwpriv ra0 set NetworkType=Infra
sudo iwpriv ra0 set AuthMode=SHARED
sudo iwpriv ra0 set EncrypType=WEP
sudo iwpriv ra0 set DefaultKeyID=1
sudo iwpriv ra0 set Key1=my WEP key
sudo iwpriv ra0 set SSID=my ESSID
sudo dhclient ra0

3)I then get a client lease and get network access.  However, DNS doesn't work: in order to fire on all cylinders, I have to edit resolv.conf to my ISPs DNS servers, as dhclient seems to rewrite resolv.conf to ask the router for DNS.  

Once I've followed these steps, I have a beautiful wireless connection.

So, my questions, in order of importance:

1) What is wlassistant doing in order to make the wireless interface available?  When I start the computer, ifconfig just returns eth0 and lo; after I run wlassistant, ra0 is added.  I've tried to run it (wlassistant) from a shell and see what is going on, but I can't make head or tail of the output and just trying trying to copy the output into a shell doesn't seem to work.   So, in other words, how do I bring up ra0?

2) How can I either get the router to provide DNS services, or stop dhclient rewriting resolv.conf?

 3) How can I combine these steps into a script to be run at boot?  Boot scripts are a closed book to me!

Many thanks for any help, and Happy New Year!

Cheers,
Calum

---

### Post by michaeljustman on 2006-12-31
Why don't you try network-manager to manage your wireless networks? Works great for me.

```
sudo apt-get install network-manager-gnome
```

---

### Post by CalumII on 2007-01-02
Thanks for the suggestion - I've downloaded and installed it, but when I run nm-applet it just says 'No Network Connection'.  I can't seem to find any way of persuading it to look for one...any ideas?

Cheers,
Calum

---

### Post by pauljturner on 2007-01-02
I think you have to comment out the lines in the /etc/network/interfaces file that refer to your wireless setup.  I read somewhere that network-manager ignores anything that is configured that way.  Try commenting the lines out and rebooting to see if it picks it up.

---

### Post by CalumII on 2007-01-02
I tried playing with /etc/network/interfaces and ended up breaking my install!  For some reason, there were directives for a wlan0 and a ra0, the latter commented out.  Aha, I thought, I'll try disabling wlan0 and try to bring up ra0 automatically.  However, for some reason networking couldn't set itself up on boot and so it just hung.  After a frantic scrabble around trying to find my original install disc (sigh) I managed to change it back.

I've now discovered that getting the ra0 interface up is easier than I realised - just an 'ifconfig ra0 up' does the trick.

So I now have the following script which kickstarts my networking.  Last question (I hope): how do I get this run on boot, for all users?

```
ifconfig ra0 up
iwpriv ra0 set AuthMode=SHARED
iwpriv ra0 set EncrypType=WEP
iwpriv ra0 set DefaultKeyID=1
iwpriv ra0 set Key1=my key
iwpriv ra0 set SSID=my ssid
dhclient ra0
cp /home/calum/resolv.conf /etc/resolv.conf
```

It annoys me having to constantly overwrite resolv.conf but I can't see a better way. It seems to be possible to modify dhclient.conf to stop dhclient from doing anything about DNS, but will this cause an issue with updates in the future?

Cheers,
Calum

---

### Post by pauljturner on 2007-01-02
Did you try commenting out everything except for the loopback (i.e. lo) stanza in /etc/network/interfaces and rebooting?  You should then be able to use network-manager which should save you having to automate the code you have created.  

See this thread:

[http://www.ubuntuforums.org/showthread.php?t=205902]("http://www.ubuntuforums.org/showthread.php?t=205902")

---

### Post by bcs on 2007-01-22
Hi,
I followed the comment in the thread linked:

> AFAIK, you need to comment out the entries for your "physical" network cards (interfaces) in /etc/network/interfaces, otherwise Network Manager won't be able to control them.
In other words, the only "active" lines (i.e., lines not starting with a #) in /etc/network/interfaces should be:
Code:

auto lo iface lo inet loopback

Oh, and you need to have the "Notification Area" active in one of your panels, otherwise the NM applet won't be visible...

but it broke my network connection...I think the problem is that I didn;t set "Notification Area" active in one of my panels;  I have no idea what that is.   Can anyone assist?  Basically all I'm looking to do is just add a couple of hidden wireless networks to the network manager; it is working fine with /etc/network/interfaces totally uncommented, but I'm just not sure how to add networks. Thanks!

---

