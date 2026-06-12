---
title: "How do I browse wireless networks?"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by iNeeed on 2008-12-18
Ok, so I am one of those people thats been driving around in a car(windows) with no idea how any of it works for many many years.  I recently switched to Ubuntu and love it for obvious reasons.
My latest problem is connecting to wireless networks.
At home I have a wire that goes into my laptop and I'm automatically on the web.  I live in an apartment and the whole house is wired.
I went to my local coffee shop today to intake coffee and browse the web and could not figure out how to browse for available networks(in vista there was a button for this) 
So far I have installed Broadcom sta wireless driver and there is also a Broadcom B43 wireless driver available to install.  I tried to activate both but it only let me activate 1.  I still can't browse networks though and am VERY confused.  If anyone can help or has any advice or a starting point I would really really apreciate it.

Thanks!!!

---

### Post by donkyhotay on 2008-12-18
I use wicd for browsing/accessing wireless networks. I find it much easier then using the built-in system that comes with ubuntu. You can install it with:
```
sudo apt-get install wicd
```
then try browsing for networks from there.

---

### Post by lovelyvik293 on 2008-12-18
```
apt-get install wicd 
```
i got
```

vik@linux-machine:~#sudo apt-get install wicd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wicd

```

---

### Post by iNeeed on 2008-12-18
> **donkyhotay said:**
> I use wicd for browsing/accessing wireless networks. I find it much easier then using the built-in system that comes with ubuntu. You can install it with:
```
sudo apt-get install wicd
```
then try browsing for networks from there.

Thanks for responding.
I tried that and got this message

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wicd

---

### Post by Crafty Kisses on 2008-12-18
What version of Ubuntu do you have? If it's earlier than Intrepid, I believe all you have to do is the following, **Settings > Repositories > Third Party Software** then add the following line: 
```
deb http://apt.wicd.net hardy extras
```

---

### Post by lovelyvik293 on 2008-12-18
For the wcid we have to add the line
```

deb http://apt.wicd.net gutsy extras

```
in the software sources.
For wcid check it
[https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)

---

### Post by Crafty Kisses on 2008-12-18
> **lovelyvik293 said:**
> For the wcid we have to add the line
```

deb http://apt.wicd.net gutsy extras

```
in the software sources.
For wcid check it
[https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)

Yeah, it depends on what version of Ubuntu you have. Different versions require different lines.

---

### Post by iNeeed on 2008-12-18
I have 

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"

---

### Post by lovelyvik293 on 2008-12-18
In this case use
```

deb http://apt.wicd.net intrepid extras

```

---

### Post by fredbird67 on 2008-12-18
INeeed, I had a similar problem over the weekend with Xubuntu on our laptop, so I posted on here and found help, and it's all in the following thread:  [http://ubuntuforums.org/showthread.php?t=1010303](http://ubuntuforums.org/showthread.php?t=1010303)

However, I haven't had the laptop out of the house since that time, so I can't vouch for whether or not the steps Ayuthia had me do are supposed to work elsewhere or not, but I do plan to try it sometime.

---

### Post by ugm6hr on 2008-12-18
Stop.

Before installing Wicd (which is very good), make sure that you have your hardware set up properly.  The built-in Network Manager works just fine for most people, and causes less problems with updates etc.

Give the output from:
```
lshw -class network
lspci
```

This will confirm your wifi hardware.

I presume you have a Broadcom card.  These are now fairly well supported in Linux (I believe).

A quick google of "ubuntu" and your hardware will give you an answer.

Once sorted, Ubuntu also (like Vista) has a "button" for wifi browsing.  It sits in the top right corner, and looks like 4 vertical grey bars, or 2 computer screens.  Just left-click on it:

[IMG]http://projects.gnome.org/NetworkManager/images/wireless-at-tealuxe.png[/IMG]

Ref: [http://projects.gnome.org/NetworkManager/](http://projects.gnome.org/NetworkManager/)

---

### Post by iNeeed on 2008-12-18
This is my latest error message

W: GPG error: [http://apt.wicd.net](http://apt.wicd.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FEC820F4B8C0755A

Thanks everyone for your help.

---

### Post by nothingspecial on 2008-12-18
You need to add the key

```
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
```

---

### Post by iNeeed on 2008-12-18
BCM4311 802.11b/g WLAN

---

### Post by ugm6hr on 2008-12-18
A quick google found this: [http://ubuntuforums.org/showthread.php?t=1008072](http://ubuntuforums.org/showthread.php?t=1008072)

Although, in theory, selecting the correct driver (wl / b43) from the System->Administration->Hardware Drivers menu should work too.

PS: What options do you have when you click on the NM icon (top right)?

---

### Post by iNeeed on 2008-12-18
wired networks
wired connection 1
auto etho
vpn connection ->
                  configure vpn
                  disconnect vpn

---

### Post by iNeeed on 2008-12-18
> **ugm6hr said:**
> A quick google found this: [http://ubuntuforums.org/showthread.php?t=1008072](http://ubuntuforums.org/showthread.php?t=1008072)

Although, in theory, selecting the correct driver (wl / b43) from the System->Administration->Hardware Drivers menu should work too.

PS: What options do you have when you click on the NM icon (top right)?

Yes!!! I did what this person did and bingo.
I can now surf the web and drink coffee in a public place.
Thank you so much for your help!

---

