---
title: "Intrepid: Ethernet eee 901 does not work with CLEAN install"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by ghepardo on 2008-11-05
Hi,
I've just did a CLEAN install (not an upgrade, but a format and then install) of Xubuntu 8.10 on my asus eee 901 (20gb).

The system installs fine, but I can't connect to internet because the wireless does not work (I knew this and there are workarounds) but also the ETHERNET DOES NOT WORK.

In fact most of the times the ethernet fails to get an IP address from my router DHCP, and even if I set a static IP, internet does not work. I can't surf the web nor ping a direct ip address.

What can I do ?

Can't nor fix wireless, because I need at least ethernet to get the files (from repositories) for wireless to work...

Can someone help me ?

---

### Post by Ghostlove on 2008-11-09
This is my problem exactly with my Eee 900 - if you find a solution, please let me know.

---

### Post by ghepardo on 2008-11-10
Hi,
I've found a solution.
The solution consists on removing the network manager from the autostarted application.

Here is the code you have to use:

1. Disable NetworkManager from starting up:

```

$ sudo update-rc.d -f NetworkManager remove

```

2. Reboot

3. Manually set up eth0 using ifconfig and route:

```

$ ifconfig eth0 10.0.0.10
$ route add default gw 10.0.0.24. Edit /etc/resolv.conf:
$ echo "10.0.0.2" >> /etc/resolv.conf

```

The exact IP addresses will be different for your individual setups, of course. So, to take advantage of your router DHCP, in spite of the last section of code (3), you might want to try running

```

dhclient eth0

```


Hope this helps,

Ciao bella! :)

---

### Post by Ghostlove on 2008-11-10
Ghepardo I am trying this right now. If it works I will bake you biscuits and send them all the way to Italy. :D

---

### Post by Ghostlove on 2008-11-10
Argh. I'm getting:

```
10.0.0.24. : Unknown host
```

---

### Post by Ghostlove on 2008-11-10
Oh poop. Same error I've gotten a few times before trying to do this:

"No working leases in persistent database - sleeping."

All I want to do is get on the damned internet with my little EeePC. :(

---

### Post by ghepardo on 2008-11-10
In spite of using the code at the point 3 
```

$ ifconfig eth0 10.0.0.10
$ route add default gw 10.0.0.24. Edit /etc/resolv.conf:
$ echo "10.0.0.2" >> /etc/resolv.conf

```

rollback all the things you did at the point 3 (I mean delete the line with 10.0.0.2 in the file /etc/resolv.conf) and then use this one:

```

sudo dhclient eth0

```

and it will work ^^.

---

### Post by Ghostlove on 2008-11-10
It didn't even let me do point 3. I just kept getting 'Permission denied', even using sudo. :(

---

### Post by ghepardo on 2008-11-10
> **Ghostlove said:**
> It didn't even let me do point 3. I just kept getting 'Permission denied', even using sudo. :(

Reboot.
Do the point 1.
Reboot, then do this:
```

sudo dhclient eth0

```

I am going to sleep now, tomorrow I've got to work.

I've added you to my msn, I can help tomorrow if you still need.
But I don't think, you seem a smart girl and this is an easy trick to do ^_^.

Ciao bella!

---

### Post by Mr_Miyagi on 2008-11-21
Ghostlove, can you confirm that this worked?
Thanks!

---

### Post by Mr_Miyagi on 2008-11-24
Unfortunately this does not work for me at all. Anyone have a solution for this.

---

### Post by ghepardo on 2008-11-24
```

sudo apt-get remove NetworkManager

```

and then install WiCD:
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by Mr_Miyagi on 2008-11-24
Hmm, does not work. I'm going to see if I can try it with another network tomorrow. I thought I had a static ip (that's why I'm paying so much for my connection) but looking through my ISP help pages I think it might be dynamic. What can happen is they sometimes lock an IP to a mac-adress for a certain time (I'm using internet on my stationary computer). Usually you can just 'release' it and it will work with another network card. I have tried it but doesn't make any difference. I have managed to find a kernel that will give me wireless internet, so that's at least something. 
I'll report in tomorrow.
Thanks!

---

### Post by Mr_Miyagi on 2008-11-25
Ok, so I let my internet connection "rest" over night to be sure that any "IP-lock" would be released. And to my delight that worked. I was getting worried it was something wrong with my hardware, didn't test the ethernet before I erased Xandro. But now it's working! :guitar:

Damn that feels good, thanks for all the help...at least I got a better network manager :wink:

---

### Post by ghepardo on 2008-11-25
> **Mr_Miyagi said:**
> 
Damn that feels good, thanks for all the help...at least I got a better network manager :wink:
Absolutely.

---

### Post by gazzmaniac on 2008-12-21
Hi ghepardo, 
I would like to thank you for the solution you supplied to Ghostlove - the DHCP solution worked first time for me.

Regards,
Gary

---

### Post by Tomatz on 2008-12-21
You really should check out ubuntu eee. It has all the drivers etc out of the box.

[http://www.ubuntu-eee.com/](http://www.ubuntu-eee.com/)

---

### Post by ghepardo on 2008-12-21
> **gazzmaniac said:**
> Hi ghepardo, 
I would like to thank you for the solution you supplied to Ghostlove - the DHCP solution worked first time for me.

Regards,
Gary

You'r welcome mate ^^

---

### Post by robstr on 2009-02-28
Thanks for your post! I had the same problem running Easy Peasy and eeebuntu on my eee 1000. The wired connection worked fine in Xandros and with another computer. Your fix worked for me on eeebuntu. After getting the wired connection working with your dhclient suggestion, I installed WICD, an alternative network manager tool. See Ray Haque's review and installation instructions:

[http://rayhaque.blogspot.com/2008/06/eee-pc-network-manager-replacement-wicd.html](http://rayhaque.blogspot.com/2008/06/eee-pc-network-manager-replacement-wicd.html)

WICD seems immune to the problem, and I prefer its user interface. I haven't tested the wireless yet.

---

