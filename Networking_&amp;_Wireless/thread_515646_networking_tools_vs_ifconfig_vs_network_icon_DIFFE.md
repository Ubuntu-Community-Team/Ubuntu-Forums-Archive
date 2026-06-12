---
title: "networking tools vs ifconfig vs network icon DIFFERENT INFO"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by ragecyr on 2007-08-02
so this is wierd....

i have no eth0 (where is it, where did it go, i have no idea)

my wired is eth1

i plug in and it will dhcp and be fine and all
ifconfig eth1
shows no ip
go to networking tools.. shows no ip on eth1, click configure and it brings up that its set to dhcp. tcpdump -vv -i eth1: nothing being sent wireshark eth1 shows normal activity.

now if i set IP manually, in the networking, ifconfig eth1 shows no IP, networking tools shows no ip. can't connect out (not an issue on other laptops, or the network, just this laptop).

now if i set ip with ifconfig eth1, it will show that set ip in networking tools, but not in networking.

so lets say i do manual ip in networking.. 1.1.1.2 (example)
ifconfig eth1 1.1.1.3

technically they should overwrite eachother and i should now have 3 as my ip...


on this machine, networking shows 2, networking tools and ifconfig show 3.





so somethings not right here and it seems to not be in sync. any ideas on where i could start to solve this problem? (feisty)
would there be a way to 'reinstall' networking perchance and just start fresh and rediscover devices and all, that almost seems like an easier answer than what i might have to do to unconfuse the computer

---

### Post by noob12 on 2007-08-03
For the first question, look at **/etc/iftab**.  You may have had an eth0 with a different mac address at some point.  In any case if it isn't there anymore and isn't going to be, you can
certainly associate eth0 with the mac addr that is currently named eth1.  Best to reboot if you do.

For the other questions you may be confusing operations on the interfaces themselves and operations on the file **/etc/network/interfaces**.  Or you've confused me.  Possibly both.

---

