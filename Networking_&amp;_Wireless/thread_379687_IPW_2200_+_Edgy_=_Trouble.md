---
title: "IPW 2200 + Edgy = Trouble"
date: 2007-03-08
forum: Networking &amp; Wireless
---

### Post by conash on 2007-03-08
Hello everybody

I know that some of you will say I am probably crazy and that ipw2200 works perfect with edgy but I am pretty sure I did everything right and still...it won't work.

I have reinstalled my Edgy recently and I installed Wifi_Radar, last time I did that everything worked perfectly but now I get Status: Disconnected in Connection Properties.

I checked the interfaces file, my eth1 wasn't even there so I entered 

auto eth1
iface eth1 inet dhcp

...still nothing

WiFi_radar can see my Ap but ... I doesn't show any "Connect" button

I tried setting everything up over terminal...still nothing

iwconfig shows 

unassociated ESSID: off/any
Mode: Managed Channel=0 (i should have 11)  AP: Not-Associated (yeah right!)
the rest is unimportant ...I guess :)

My encryption is WEP, I had WPA and changed it. Normally there shouldn't be a problem in Edgy.

The point is: I want to do this over the GUI not in command. I am a Linux newbie and I like to get my stuff done easy and fast (remember, this is why we started to build computers?!).

Sorry, I am pretty p..d off. 

I have not much to give in exchange but if anyone of you gets dumped by his girlfriend then I promise to cheer him up. I am a good joke teller. :)


.....so FINALLY, I did it, this is how, even if I am not very sure that it will work everythime

This work only for WEP!

go 

sudo gedit /etc/network/interfaces

then you write everything neatly

auto lo
iface lo inet loopback


auto eth0
iface etho inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



ok, afterwards go to network manager and make sure your connection is enabled

write your ESSID
select ASCII
write you password
click OK

should work

if not go have a coffee , come back and search the forum again before posting. :)


nice day ya'all

---

