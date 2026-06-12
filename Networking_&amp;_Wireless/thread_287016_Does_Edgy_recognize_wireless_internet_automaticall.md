---
title: "Does Edgy recognize wireless internet automatically?"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by Kevomiller on 2006-10-28
Hey!

I was curious if Edgy recognized wireless internet by itself or if you have to download a program?!

Thanks!

---

### Post by reacocard on 2006-10-28
Edgy will recognize wireless automatically, if your card is supported, but configuring it with just the built-in tools hasn't changed from dapper (i.e. it's a pain). I use network manager to manage my wireless under edgy, and it works beautifully.

---

### Post by Kevomiller on 2006-10-28
The Network manager that it comes with, or something you have to download?

Also, I'm on an Intel Mac, is that card supported?

When you say Automatically, do you mean that you dont have to do anything, it just recognized it, or that you still have to configure it?

Thanks!

---

### Post by reacocard on 2006-10-28
iirc, the Intel Macs use intel wireless, which is supported automatically. You can use System->Administration->Networking to configure it, but it's much easier to use network manager. just

```
sudo apt-get install network-manager network-manager-gnome
```

to get network manager. Then do

```
gksudo gedit /etc/network/interfaces
```

and comment out everything except the entry for 'lo' (should be the first two lines). Reboot, and network manager will put a little icon in your system tray to manage your wireless with.


So to answer your questions:

-it's not installed by default, but it's in the repos so it's easy to get.

-yes

-it'll recognize and set up the card itself fine, but selecting the network to connect to is difficult without network manager.

---

### Post by jj9000 on 2006-10-28
Thanks a lot, the network-manager is a cool tool, and it solves my problem perfectly!

But..
It seems that Edgy does not search for wireless networks out of the box, for my card (Intel PRO/Wireless 2200BG, in a Thinkpad T43). You have to type in the ESSID yourself. Even checking the checkbox in Network Settings labelled "Scan for available services ... " in the General Tab, does not allow my card to discover 802.11 networks. 

In Dapper, I did not have this problem, my card worked out of the box.

Any thoughts? Has this issue already been identified?

---

### Post by linux_explorer on 2006-10-30
Windows was sucking my toshiba a10 satellite and had renderred it unusable for about 6 months. Edgy runs great though! But I am facing this problem too, i.e.,  I have to manually enter the ESSID of the networks in order to connect. I do not get a list of available services (as in Windows) at all. This means I would not be able to connect to a wireless network for which I do not know the ESSID. Any fixes yet?

---

### Post by Kevomiller on 2006-10-30
I can't get the wireless connection to work in Dapper.

Where do I get my ESSID?  I'm not for sure if I have it or not.

Also, Edge doesn't work on my Intel Mac.

I get huge, orange waves. lol.

I'd like to get dapper goin tho.

So if you can help me find that network manager for Dapper, or whatever, I would apprecaite it.


Kevin

---

### Post by reacocard on 2006-10-30
You can use the same method to install network manager in dapper.

The ESSID is the name of the network. Just use OSX or Windows to find out what that is, if you don't know it.

---

### Post by mike41 on 2006-10-30
There is an old tool called netapplet which works quite well. It gives you a list of the networks.

sudo aptitude install netapplet

---

### Post by surferchild007 on 2006-10-30
I am new to Ubuntu. What do mean to comment out I don't want to break anything.

---

### Post by KHatfull on 2006-10-30
Man, either all forum posts are going to have to hang around forever or I better start making PDFs of articles like this :mrgreen: 

Thanks for this, fixes me up too.  Curious though, why not install Network Manager by default?  Given the amount of forum traffic on wireless it would seem a no brainer...

---

### Post by todds on 2006-10-31
i strongly agree that network manager should be installed by default,there is a huge amount of posts regarding networking in general,it does make sense,then again iam a newbie really just coming over from pclinuxos so maybe there is a particular reason for it...

regards

todds

---

### Post by reacocard on 2006-10-31
> **surferchild007 said:**
> I am new to Ubuntu. What do mean to comment out I don't want to break anything.

To comment out a line, just put a # in front of it. Like this:
```
#This line is commented out!
This line is not.
```

---

### Post by reacocard on 2006-10-31
> **KHatfull said:**
> Man, either all forum posts are going to have to hang around forever or I better start making PDFs of articles like this :mrgreen: 

Thanks for this, fixes me up too.  Curious though, why not install Network Manager by default?  Given the amount of forum traffic on wireless it would seem a no brainer...

That's a question that's been asked many times. The short answer: It's not ready yet.

Network manager currently cannot handle some things, such as static IP addresses and using more than one network interface at a time. These restrictions make it unsuitable for being the default method of managing networks.

These problems are being worked on, and perhaps a future version of network manager (.7?) will be included by default, but its not going to happen very soon.

---

### Post by hairypete on 2006-10-31
Another thing that network manager can't seem to handle is noticing that my wireless card is plugged in!  I'm using a Ralink 2400 card with Dapper which works fine the first time you configure it manually after installation (I've done this three times now) but then won't connect when you next boot up.  Because of this, I figured that network manager might be the answer, so in went the ethernet cable from the back of my xbox, I downloaded and installed NM, which picks up the wired network with no trouble, but as soon as I plug in my wireless card, even after editing /etc/network/interfaces and rebooting, all I get from NM is "no network devices detected" or words to that effect.  ](*,) ](*,) 

I even tried installing Edgy, and I had the same problem with NM, and after having the system freeze on me whenever I tried to activate the card manually, I reinstalled Dapper and decided to come begging for help!

Any ideas would be greatly appreciated...

---

### Post by hairypete on 2006-10-31
bumpity bump :)

---

### Post by tombott on 2006-10-31
> **reacocard said:**
> iirc, the Intel Macs use intel wireless, which is supported automatically. You can use System->Administration->Networking to configure it, but it's much easier to use network manager. just

```
sudo apt-get install network-manager network-manager-gnome
```

to get network manager. Then do

```
gksudo gedit /etc/network/interfaces
```

and comment out everything except the entry for 'lo' (should be the first two lines). Reboot, and network manager will put a little icon in your system tray to manage your wireless with.


So to answer your questions:

-it's not installed by default, but it's in the repos so it's easy to get.

-yes

-it'll recognize and set up the card itself fine, but selecting the network to connect to is difficult without network manager.

Thanks for this mate. Dapper picked up my Wireless connection no prbs, Edgy shows nothing. That's progress for you!
Just installed Network Manager,fingers crossed that this will actually find   my wireless network.

---

### Post by gasolino on 2006-10-31
I have discovered Network Manager, and it is glorious. Before, I could almost NEVER connect to the wireless at my school. It has a great interface, too, and doesn't take 10 minutes to switch profiles like the default Networking application. It usually finds my network and connects automatically. Thanks!

---

### Post by KHatfull on 2006-11-01
> **reacocard said:**
> That's a question that's been asked many times. The short answer: It's not ready yet.

Network manager currently cannot handle some things, such as static IP addresses and using more than one network interface at a time. These restrictions make it unsuitable for being the default method of managing networks.

These problems are being worked on, and perhaps a future version of network manager (.7?) will be included by default, but its not going to happen very soon.

Fair enough, I hadn't noticed the static IP issue in my giddiness in having something that worked well and as I wanted it to for my wireless card :) 

Let's hope it's improved soon...I find it to work well given it;s current feature set.

Thanks!

---

### Post by tdamocles on 2006-11-02
> **reacocard said:**
> iirc, the Intel Macs use intel wireless, which is supported automatically. You can use System->Administration->Networking to configure it, but it's much easier to use network manager. just

```
sudo apt-get install network-manager network-manager-gnome
```

to get network manager. Then do

```
gksudo gedit /etc/network/interfaces
```

and comment out everything except the entry for 'lo' (should be the first two lines). Reboot, and network manager will put a little icon in your system tray to manage your wireless with.


So to answer your questions:

-it's not installed by default, but it's in the repos so it's easy to get.

-yes

-it'll recognize and set up the card itself fine, but selecting the network to connect to is difficult without network manager.


Does this work in 6.10?  It says that the package is not found....

---

### Post by KHatfull on 2006-11-02
Working with 6.10 for me currently...

---

### Post by reacocard on 2006-11-02
> **tdamocles said:**
> Does this work in 6.10?  It says that the package is not found....

It works fine in edgy, as that's what I'm using. Make sure you spelled everything correctly. Also, do a 
```
sudo apt-get update
```
then try it again.

---

