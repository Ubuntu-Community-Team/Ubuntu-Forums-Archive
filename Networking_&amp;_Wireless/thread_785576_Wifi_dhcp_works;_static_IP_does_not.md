---
title: "Wifi dhcp works; static IP does not"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by spaceboy909 on 2008-05-07
Compaq R4010us
Broadcom wifi

A couple months ago I installed Ubuntu Gutsy and the wifi did not work out of the box, so I installed the ndis wrapper and got it running on my local net with dhcp.

Now, my lan is set to static, but Ubuntu doesn't seem to want to work that way.

Here's some of the problems I'm having, as I am trying to test out different possible solutions.

1) The gui manager does not allow a static IP to be set in roaming mode.

2) Non-roaming setup in the gui forces encryption which makes testing and setup more difficult.  It really needs to have an 'open' option like a standard utility would have.

3) There is a bug which many times erases my encryption key after I close out the box, so I have to type it in every time, and then I don't know if it even tried to use it in the first place.

4) This one is an annoyance, but doesn't prevent me from testing, and that many times it will erase ALL of my network data, and it must be typed back in.  PITB!

The best that I can achieve with wifi and **static** IP is that my card will connect in roaming mode, and show solid signal strength, but I can't actually get online.  The resolv.conf file seems to have the appropriate DNS entries.  In non-roaming mode, it won't connect at all.

I then tried jacking in with a static IP set, to no avail.  I then set my router **back to dhcp** and my settings to roaming, and both wired and wifi **work fine**, so it's something going wrong with the static setup.


I have tried the following guide, specifically the section on setting static IP's:  [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

```
sudo ifconfig <interface> down
sudo dhclient -r <interface>
[SIZE=2][B]sudo ifconfig <interface> *192.168.1.100* netmask *255.255.255.0* up
sudo route add default gw *192.168.1.1*[/B][/SIZE]
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>
```Unfortunately, this did not do the trick.  Any ideas?

---

