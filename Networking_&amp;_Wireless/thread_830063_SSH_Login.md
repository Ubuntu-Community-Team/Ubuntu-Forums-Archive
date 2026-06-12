---
title: "SSH Login"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by panosl on 2008-06-15
Trying to log in remotely through SSH.

I will get an 'operation timed out' msg, when I do, except if a user
is already logged in on the ubuntu box. This is weird, 'cause another
ubuntu box (same version, 8.04), which is located within the network, works
fine through SSH log in, without the need for a user to be already
logged in.

Where should I be looking?

---

### Post by panosl on 2008-06-16
Could this be related to the fact that the machine that SSH login works (without requiring an account to be logged in already), is connected through Ethernet, while the other in Wireless?

I am setting up the wireless through Gnome Network Manager, in roaming mode. Maybe I have no net connection till Gnome NM is started up?

---

### Post by tgrimley on 2008-06-16
I don't think Ubuntu installs an sshd by default.  Is one installed?  That would explain your time out.. (there's nothing listening on that port..)

```
sudo apt-get install openssh-server
```

Also, are you trying to ssh by hostname or ip? If by ip and you're sure about the IP it shouldn't matter what the connection is..

---

### Post by panosl on 2008-06-16
I've got OpenSSH server installed and it's running.

I am SSHing by IP (local network IP).

The weird thing is, that it allows me to SSH if I go to the physical box and log in there with a user. That's why i am thinking if it's a NM issue. I would try with an ethernet cable, but I would have to move *alot* of stuff around (it's on another floor), so I am looking it to be a last resort.

Pattern #1:

SSH from my laptop to the ubuntu desktop: TIMEOUT

Pattern #2:

Go the ubuntu desktop, log in with a user account.
Go back to the laptop and SSH to the ubuntu desktop: WORKS

---

### Post by tgrimley on 2008-06-16
Ah, sorry for asking obvious questions :)

To get this straight could you expclitly say what each is connected by (I didn't understand what you said regarding which is connected via wireless and which by ethernet).

It does sound like a NM issue.  Try doing ifconfig from a tty before you login and then from a terminal after and see if your ip changes (or if you even have one before logging in)

---

### Post by lswb on 2008-06-16
I think you hit the nail on the head with NetworkManager. This is a real problem IMHO. I'm not certain of the exact commands you'll need, but something like this added to /etc/rc.local might get it going, substitute your wireless interface for wlan0:

   ifconfig wlan0 up
   iwconfig wlan0 mode managed essid your-esssid-name 
   dhclient wlan0

This assumes you have a wireless router operating in managed mode with a dhcp server running, more or less the usual case.

This will probably need some tuning and there may be adverse consequences when NetworkManager starts up later! Good luck!

---

### Post by panosl on 2008-06-16
I should've mentioned them earlier :)

So, here's the setup:

[LIST=1]
[*]laptop: OS X Leopard, WIRELESS
[*]desktop 1: Ubuntu 8.04, WIRELESS
[*]desktop 2: Ubuntu 8.04, ETHERNET
[/LIST]

[LIST]
[*] laptop -> desktop 2: WORKS
[*] laptop -> desktop 1: DOES NOT WORK*
[/LIST]

* Works **only** if I go over to the physical box, and log in with a user account first.

running ifconfig in recovery mode (root shell), only has lo set up, no wireless. Of course that's not enough as desktop 1 is not connected through ethernet, it's wireless. :(

---

### Post by panosl on 2008-06-16
> **lswb said:**
> I think you hit the nail on the head with NetworkManager. This is a real problem IMHO. I'm not certain of the exact commands you'll need, but something like this added to /etc/rc.local might get it going, substitute your wireless interface for wlan0:

   ifconfig wlan0 up
   iwconfig wlan0 mode managed essid your-esssid-name 
   dhclient wlan0

This assumes you have a wireless router operating in managed mode with a dhcp server running, more or less the usual case.

This will probably need some tuning and there may be adverse consequences when NetworkManager starts up later! Good luck!

Great, at least we know now, what this is all about!

NM is a great app, but this is really sucky :(

I think it'll be better if I completely drop NM and do a manual configuration. I haven't done it before for wireless, but I guess it won't be *that* hard, will it?

/me has faith in linux!

---

### Post by tgrimley on 2008-06-16
No it's not too hard at all if you only want to connect to one network.. I've done it a couple times.  If you wanted some sort of roaming.. it'd be less fun :)

---

### Post by dmizer on 2008-06-16
> **panosl said:**
> Great, at least we know now, what this is all about!

NM is a great app, but this is really sucky :(

I think it'll be better if I completely drop NM and do a manual configuration. I haven't done it before for wireless, but I guess it won't be *that* hard, will it?

/me has faith in linux!

NetworkManager is indeed the culprit here.

disable NM according to these directions: [https://help.ubuntu.com/community/NetworkManager?#head-d279c8fbfc4d1711bb8e3a03a4b71c810878b0eb](https://help.ubuntu.com/community/NetworkManager?#head-d279c8fbfc4d1711bb8e3a03a4b71c810878b0eb)

reboot

then configure your wireless network by going to:
system > administration > networking

---

### Post by lswb on 2008-06-16
Yes, tgrimley is right, it's not too hard. When I said it was a real problem, I meant a problem with the way NetworkManager works, not a problem that would be hard to solve. You've already got the hardest part done, getting the wireless working at all!

---

### Post by kevdog on 2008-06-16
Here is the thread you want to make a manual connection:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by panosl on 2008-06-17
Found the reported bug, though it appears to be closed, and noted as not a NM issue: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/93912](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/93912)

---

