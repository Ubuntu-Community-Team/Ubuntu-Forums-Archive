---
title: "Newbie to uBuntu - Using Netgear MA111v2"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by al3x416 on 2007-01-28
Hello,

I'm currently an extreme newbie to uBuntu, and I have just started using it yesterday. I'm currently trying to get my internet to work on the uBuntu portion of my HD (currently on WinXP portion). I'm using a Netgear MA111v2, with a WEP-Key in Infrastructure on Windows. I've tried using ndiswrapper, and it says my hardware is installed, but I dont know how to connect, since it does not have the configuration tool like Netgear for Windows does.

Help is appreciated, but response may be slow. (switching between OS's)

Thanks,
Alex

---

### Post by Sepp1 on 2007-01-28
Take my advice for what it is, Im a noob too.
System -> administration -> network.

Select the wireless network card, and press properties.

type the name of the network, or select it from the dropdown list (case sensitive)
Select ASCII or Hex
Type network passphrase (ASCII) or Hex key

---

### Post by al3x416 on 2007-01-28
Sorry but, that didnt help. I also dont think the WEP is a passphrase, but something different.

[http://img254.imageshack.us/img254/5674/netgearhn3.png]("http://img254.imageshack.us/img254/5674/netgearhn3.png")

I hope that helps with any furthur help.

Also, the network I'm trying to connect to is channel 9, if that effects anything.

---

### Post by Sepp1 on 2007-01-28
As far as I can see, your wifi-network is 64 bit encrypted. I encoutered problems with that when i upgraded from dapper to edgy.
[http://www.ubuntuforums.org/showthread.php?t=346072](http://www.ubuntuforums.org/showthread.php?t=346072)
That MIGHT be the problem.
are you using dapper or edgy?

---

### Post by al3x416 on 2007-01-28
Newb talking - I just downloaded the newest version available at first.. I believe it was 6.10.

I'm not familiar with codenames.

I downloaded this, [http://www.ubuntu.com/products/GetUbuntu/download#currentrelease](http://www.ubuntu.com/products/GetUbuntu/download#currentrelease)

---

### Post by Sepp1 on 2007-01-28
Sorry
6.06 is codename Dapper Drake (Dapper)
6.10 is codename Edgy Eft (Edgy) - This is the latest
The next release will be Feisty Fawn.

I had to reconfigure my router, so the network was 128 bit encrypted, before I could connect with my Ubuntu 6.10 (Edgy).

---

### Post by al3x416 on 2007-01-28
While I'm waiting for my sibling to let me modify the router settings.

Any explanation on how to install WiFi radar, or is that pointless?

Any other ideas?

---

### Post by Sepp1 on 2007-01-28
```
sudo apt-get install wifi-radar
```

But you have to be connected to the internet:( 

Try connecting by ethernet cable. Most wireless routers also have a hub on the back.

---

### Post by al3x416 on 2007-01-28
Well, I tried doing a 128 bit encryption, but It didnt work.

Also, for some reason my hard wired connection keeps enabling itself over and over.

Also, just to make my life easier, is it ASCII or HEX I should be using? I try both.

And should uBuntu tell me when I am connected or not? It doesnt say anything.. I have to try in Firefox.

---

### Post by Sepp1 on 2007-01-28
If You type a 26 characters directly as a key in the router configuration. it is also hex on your computer. If you use a passphrase it is ASCII.

No Ubuntu, dosn´t tell you if you are conected with a wrong wep-key. The network just doesn´t work. It does however tell you wether it is reciving a signal (and how strong), in a litle green bar in the top right corner

I´m sorry it didn´t work, but at least your network is more secure now.

---

### Post by KrakensDen on 2007-01-28
The solution I usually recommend for any wireless issue is to install NetworkManager. Download it using Synaptic, or type 
```

sudo aptitude install network-manager-gnome

```

If, for some reason, that gives you problems, there is [a howto]("http://ubuntuforums.org/showthread.php?t=341357"), but those steps, in theory, should be taken care of for you by the system.

It will give you a little icon in your taskbar that you can click on, select a wireless network, and connect to it. It supports WPA, WEP, etc., with no manual configuration.

Why is this not in Ubuntu by default? It doesn't support some wireless cards with native Linux drivers, though in my experience wireless cards used via ndiswrapper work fine.

Sorry for your connection issues, good luck solving them.

---

### Post by al3x416 on 2007-01-28
I'm stuck right now. I couldnt compile Network Manager, and my wireless connection still doesnt work.

Help would be appreciated.

---

