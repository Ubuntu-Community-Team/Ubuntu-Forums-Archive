---
title: "Run a script at boot time in ubuntu"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by tanveer on 2008-03-13
Hi all,

I have done authentication against windows AD and it works fine with winbind. Now as the service startup order is very important so first samba and then winbind has to start. 

But whenever I reboot, I cant login whereas the output of wbinfo -u / wbinfo -g is showing fine. So then from command shell I again restart those services and then it agains works fine. I then changed the winbind file in /etc/rc2.d, /etc/rc3.d,/etc/rc4.d,/etc/rc5.d from S20winbind to S99winbind for later start then samba but still no luck.

I also followed the below solution but still same.

[PHP]

Create your script, give it execute rights and put it in /etc/init.d, then run this command :
Code:

sudo update-rc.d name_of_your_script defaults
[/PHP]

Any idea how to overcome this please.

---

### Post by SpaceTeddy on 2008-03-13
the commands look right.

what exactly is the problem with the scripts ? are you getting a dhcp lease after they try to initialize ? do you need your network to run sooner ? why do they fail ?
and are they run at boot time at all (have you checked that aswell)

---

### Post by tanveer on 2008-03-14
Thanks for reply.
yes they did get start at boot time. I checked that. 

I am getting IP from DHCP and as you said that may b the problem. One interesting thing is after reboot if I login with a local account and then from shell when I try to authenticate as AD user it works fine i,e,, shows login success. But not before that.

And current situation is after reboot when I try to login as AD user its blocks me saying my username or password is wrong. Then I go to shell and restart the samba and winbind service again which is already running & then I can get authentiated with ad user.

Why is this happening? Any help please.

---

### Post by SpaceTeddy on 2008-03-14
if the network cards are configured by network-manager, they will not be initilaized with an ip address until someone logs in. By this time, anything will have started of course. So samba essentially starts without a working network interface. which explains the problems (or would so).

can you please post the content of the follow command to verify this thesis ?
```
cat /etc/network/interfaces
```

thanks

---

### Post by tanveer on 2008-03-15
$ vi /etc/network/interfaces
[PHP]
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

auto wlan0
iface wlan0 inet dhcp
[/PHP]

thanks.

---

### Post by SpaceTeddy on 2008-03-16
mhm,.. according to that file your network is initiialized at boot time (except the wifi, which would need an essid tag and possibly a password to connect automaticially at boot time) . there goes my thesis :)

unforteunaltely i don't have many other ideas... at the moment. altought, the restarting is a little strange, since that would mean that something in the init goes wrong. but what i cannot say or even guess - i've worked to little with AD for that...

---

### Post by tanveer on 2008-03-17
Hi thanks for help.
One more interesting finding is if after reboot if you wait for say around 15/20 secs and then try to login with AD user it works.  k:) why I don't now !!

---

