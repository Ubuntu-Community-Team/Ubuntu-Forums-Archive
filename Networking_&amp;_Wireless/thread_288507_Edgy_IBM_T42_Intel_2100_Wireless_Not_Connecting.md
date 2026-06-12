---
title: "Edgy: IBM T42 Intel 2100 Wireless Not Connecting"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by wcbaker on 2006-10-29
Hello everyone. I just installed edgy on my Thinkpad which happens to have an Intel 2100 card. It would connect to networks just fine unless I use NetworkManager. Now, I can see all of the networks, it recognizes which ones are secure and will take a password and all that jazz, but regardless of what security the wireless network has it will not connect. Any thoughts?

---

### Post by spaceghoti on 2006-11-06
I have the exact same problem with my T42.  It sees them but never connects.  I have my wireless router set up without any kind of encryption and it still refuses to connect.  I'm at a loss where to begin.

---

### Post by spaceghoti on 2006-11-12
So, no one has any idea?  Do we know if we have the right Cisco drivers for the chips?  Am I doomed to a laptop without wireless connectivity?

---

### Post by jsares on 2006-11-21
I'm having the same problem on a T41p with Intel Pro 2100.  I think the problem is the system defaults to having the wifi and bluetooth turned off.  I tried:

sudo iwconfig eth1 txpower on

but that didn't give any output and didn't turn the wifi on.

Any help?

---

### Post by spaceghoti on 2006-11-21
If the wifi is not turning on, then why would it see what networks were available?  Unless I specifically disable my eth1 and wifi0 in my network settings, my wireless indicator stays lit.  It attempts to connect to my wireless network (again reminding everyone that it has no security enabled) when I use wlanassistant and reports failure.

---

### Post by jsares on 2006-11-23
Not sure what I did but after a reboot its working.  I'm connected right now to a neighbors wifi.  I'll have to get WPA support to connect to my network.

---

### Post by spaceghoti on 2006-11-24
I feel dumb now.  After fiddling with eth1 again, I enabled DHCP and it immediately connected to my local network.  I never realized neither static nor DHCP were enabled by default.

---

### Post by ingo on 2007-01-26
I've got a T41 with the same card. I'm on Kubuntu and I also ha(ve)d teething problems with wpa. knetworkmanager helped me a lot 'cos it takes care of all the wpa config stuff.

How did you work it out for you lot? Everybody connected? If not, try installing it.

NOTE: It does not like any manual configurations, so you have to edit out any changes you made to your wpa_supplicant.conf and /etc/network/interfaces

---

### Post by dr_gap on 2007-02-21
>I feel dumb now. After fiddling with eth1 again, I enabled DHCP and it 
>immediately connected to my local network. 
>I never realized neither static nor DHCP were enabled by default.

What exactly did you do?

---

### Post by dr_gap on 2007-02-21
This did the trick for me on my T41 / Intel 2100:

[http://www.stoltenow.com/archives/2006/12/ubuntu_configur.html](http://www.stoltenow.com/archives/2006/12/ubuntu_configur.html)

I'm posting this wirelessly.

-gap

---

