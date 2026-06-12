---
title: "Wireless monitor"
date: 2006-12-26
forum: Networking &amp; Wireless
---

### Post by Nevermore on 2006-12-26
Hi everyone
i am looking for something that will tell me realtime the quality of the wifi signal i am getting, 
gnome one isn't good, and wifiradar one is not good either.
i need something that is very fast and sensitive in order to locate a wifi node that is trying to hack my wpa password.
Thanks!
i am on edgy and i have an ipw2100 intel card

---

### Post by Floppyjoe on 2006-12-26
Have you tried SWScanner? Simple Wireless Scanner. I don't think it can find ad-hoc nodes though.

---

### Post by Nevermore on 2006-12-28
> **Floppyjoe said:**
> Have you tried SWScanner? Simple Wireless Scanner. I don't think it can find ad-hoc nodes though.

thanks
it is nice
but is not so fast in answering to variations..kismeth is far faster, but i dunno how to make it work with my ubuntu

---

### Post by tturrisi on 2006-12-28
> but is not so fast in answering to variations..kismeth is far faster, but i dunno how to make it work with my ubunt

[http://www.kismetwireless.net/documentation.shtml](http://www.kismetwireless.net/documentation.shtml)   
  [i]  ipw2100         Intel/Centrino      Linux       ipw2100-0.44+
                    [http://ipw2100.sourceforge.net/](http://ipw2100.sourceforge.net/)
                    Capture interface:  'ethX'
                    The Linux IPW2100/Centrino drivers for 802.11b cards
                    now support rfmon, so here's support for them.  They act
                    more or less like any other wireless interface would.[/i]

do this:
sudo gedit /etc/kismet/kismet.conf
change these 2 sections:
```
# User to setid to (should be your normal user)
#suiduser= YOUR-USER-NAME-HERE
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=ipw2100,eth1,Centrino_b
```
where eth1 = the name of your interface, eth0 is likely the wired interface & eth1 the wifi.  Check in System>Administration>Networking

---

