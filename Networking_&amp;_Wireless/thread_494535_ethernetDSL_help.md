---
title: "ethernet/DSL help"
date: 2007-07-07
forum: Networking &amp; Wireless
---

### Post by psyguy92 on 2007-07-07
Hi. I have a new Ubuntu installation and I can't get the Wired Connection to show up under Network Settings (System->Administration->Network).  I've tried rebooting, and rebooting the DSL modem, and nothing shows up.  lspci from a terminal shows 00:04:0 Ethernet controller: Sillicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)

I want to input the IP/Gateway/etc. information, but it won't even show up in the network settings application. Any ideas?

---

### Post by djchandler on 2007-07-07
> **psyguy92 said:**
> Hi. I have a new Ubuntu installation and I can't get the Wired Connection to show up under Network Settings (System->Administration->Network).  I've tried rebooting, and rebooting the DSL modem, and nothing shows up.  lspci from a terminal shows 00:04:0 Ethernet controller: Sillicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)

I want to input the IP/Gateway/etc. information, but it won't even show up in the network settings application. Any ideas?

I am assuming you are directly connected to the dsl modem by ethernet cable.

Is this a dual-boot system, and it shows under windows? You may need to install PPPoE software to see it in Linux. The pppoeconf  should already be installed by default. Use Synaptic to install pppoe. Doing a search in Synaptic for pppoe will show you the packages necessary, dependencies and all.

D. J.

---

### Post by psyguy92 on 2007-07-07
PPPoE was installed under Synaptic already. I did pppoeconf from a terminal, and it said:

no working ethernet card could be found. if you have an interface card which was not autodetected so far, you probably wish to load the driver manually using the modconf utility. run modconf now?

Saying yes repeats the message, saying no exits.

Isn't the card autodectected if it shows up under lspci?  
It is connected directly with an ethernet cable, to a DSL modem.  Ubuntu is currently the only drive connected, and is not dual-booting.  The connection does work fine under WinXP.

What should I do now?

---

### Post by psyguy92 on 2007-07-07
clarification: 
pppoeconf is installed in synaptic. pppoe doesn't show. are the the same?
pppoe from terminal doesn't run, but pppoeconf does. 

apt-get install pppoe says 'not available'.

---

### Post by psyguy92 on 2007-07-07
I would like to be able to determine if the hardware is something weird (it's integrated into the motherboard) that Linux will not work with, or if there is a strange software problem.  I've put all the information I have in the above posts. If anyone has any ideas, or needs more info and can tell me how to get it, I'd appreciate it :)

---

### Post by djchandler on 2007-07-08
> **psyguy92 said:**
> clarification: 
pppoeconf is installed in synaptic. pppoe doesn't show. are the the same?
pppoe from terminal doesn't run, but pppoeconf does. 

apt-get install pppoe says 'not available'.

ppoeconf is just the user interface for configuring pppoe. Install pppoe in Synaptic. It does show up in the repositories there. It is possible the repository you need to access is down for some reason. Do you know if you had to install pppoe software to access dsl in Windows? Some new DSL modems such as the new SpeedStream 4100s used by AT&T Yahoo have an ip address built in, i.e., hard-coded, and don't require pppoe. Older dsl modems may require pppoe software. A simple solution may be to get a router with built-in ethernet switch. It will also give you a hardware baseed Network Address Translation (NAT) firewall. That will also help you see if there really is a problem with the ethernet interface in your computer. Most routers have hard-coded ip address, and their configuration page can be reached by typing in something like

[http://192.168.1.1/](http://192.168.1.1/)

The user manual will give you the proper address and password to access the web-type interface.

But before you do that, use Synaptic to install sysinfo. It will tell you if everything is okay with your ethernet device. After installing, you will find it under Applications in System Tools. I'm attaching a screen shot showing the info for my on-board ethernet controller.
[ATTACH]37578[/ATTACH]

Depending on what side of the world you are on, it may be a bit before I get back when you can read this. I'll try to check in again in about 10 hours to see how it is going.

DJ

---

### Post by psyguy92 on 2007-07-08
Ok - I've put a screenshot showing what happens when I do : sudo pppoeconf  and the results of sysinfo (I had to get it by searching for a .deb on a computer with a working net connection).
I can't install anything directly, because there is no net connection on the computer.

Can you tell me what these mean from the screenshot? Where the problem is?
By the way, I tried to use this same DSL connection on another computer with Ubuntu (the one I'm typing on), and it works just fine, so isn't it safe to assume that the DSL modem is ok?  What about the ethernet port? software?!?  

Sorry getting a bit frustrated :(

---

### Post by djchandler on 2007-07-08
> **psyguy92 said:**
> Ok - I've put a screenshot showing what happens when I do : sudo pppoeconf  and the results of sysinfo (I had to get it by searching for a .deb on a computer with a working net connection).
I can't install anything directly, because there is no net connection on the computer.

Can you tell me what these mean from the screenshot? Where the problem is?
By the way, I tried to use this same DSL connection on another computer with Ubuntu (the one I'm typing on), and it works just fine, so isn't it safe to assume that the DSL modem is ok?  What about the ethernet port? software?!?  

Sorry getting a bit frustrated :(

Understandable.

Go into your bios and make sure ethernet is enabled there. If it is, which it must be since you can get through to the dsl in Windows, I would guess that the ethernet device on your motherboard is not supported with open source drivers. You may need to add a repository that is of a commercial nature to your Synaptic database of repositories. What a pain. Guessing again, SiS is not releasing their hardware requirements info for an open source driver to be written, and they want to keep it proprietary, for whatever reason. Canonical just won't include those drivers in the repository database. Were you able to get on the internet with the Live CD? Try running that and tell me what happens?

The other thing I would try before going to drastic measures is putiing your Windows HDD back in and see if you can get online if you can't get online with the Ubuntu Live CD.

My third guess is that you have the wrong ethernet cable. There is such a thing as a cross-over cable for hooking together two 10/100base-T adapters without going through a hub or switch. Are you using the same cable as worked before with Windows?

My fourth and final guess is that the on-board ethernet adapter is no longer working at all if its enabled in the bios. That solution calls for disabling the ethernet adapter in the bios, and buying a new brand name ethernet network interface card, and using up a PCI slot on your motherboard. I know 3Com cards work, and I think I've had an SMC card work with Ubuntu before as well. Linksys has gone to the dogs since being taken over by Cisco, but I believe their cards are supported. Whatever computer you are using now, use it to find a database of Ubuntu supported hardware. I think there is such a thing somewhere, or at least a database of unsupported hardware.

I'm sorry, I completely forgot about you this morning after church. I got caught up in watching the Wimbledon Men's Final, and then I took hydrocodone for my shoulder pain. I probably should have told you I've been on pain medications, waiting to get in to see an orthopedist who is an expert in unusual shoulder problems. Some reconstruction on my right shoulder is probably necessary due to a bony cyst plus other mechanical damage, whatever that means My memory is not up to the usual levels. My wife is saying I'm having slight dementia, especially short term memory problems. I'm only 55. Right now I'm on hydrocodone and orphenadrine, a muscle relaxer, so I'm blaming the medications, with no less than 12 prescriptions to keep track of.

I hope I'm helping you. I do have over 25 years experience working with computers. Most of this information, geek that I am, is bound to be mostly reliable. I'm wondering why nobody else is trying to help you with this. If nobody else is going to help, you may as well send me email, and that will get my attention more reliably. Go to my profile, and you can email me from there. Then I won't get caught up in some other thing here in the forums and forget about you. I'll try to focus if you want to try that. My regular job does not allow me to work in my medicated state, so I'm here all the time except when I am asleep. You can probably discern a normal sleeping schedule based on my location.

Sincerely,
DJ

---

### Post by psyguy92 on 2007-07-08
I haven't enabled or disabled anything in the BIOS. The only BIOS changes I've made are those that allow booting from a CD first (to install Ubuntu), and then changing back. I'm using the same cable/configuration that works with that computer under WinXP, so it is not a cable problem, and it would seem to not be a BIOS problem.

What does it mean that the ethernet port is identified with Sysinfo?  The modem is a Siemens SpeedStream 4200 Ethernet ADSL modem.

I am using this modem currently to post this message, on a laptop (not the computer I'm trying to fix/install/etc.).

I assume that the modem works with Linux/Ubuntu, because that's how I'm posting. I would guess it would be the integrated ethernet port on the desktop (system in question) that is the culprit?

---

### Post by psyguy92 on 2007-07-08
Forgot to mention, I don't really know how to add a closed source repo, and connect to it, if I don't have an active internet connection, and don't know how I would go about figuring out what it is that I need or where to get it and copy it over using something like a pen drive.

---

### Post by ravsas3 on 2007-07-20
so!!?
you fixed your problem!! hey i need help with a sis ethernet card wanmini(pppoe) connection and surfboard cable modem
thank you if you could spare time for me

---

### Post by psyguy92 on 2007-07-20
Unfortunately, I ran out of time to work on this, and don't have access to the computer I was working on anymore.  Strangely enough, when the modem was hooked back up with WinXP, it too refused to work with the standard ethernet connection (it did before), and had to use the USB connection to get it to work with WinXP.  It's hard to believe that the ethernet randomly died at the exact same time Ubuntu was installed. Oh well.

ravsas3:
It's usually better to start your own thread.  Your post is more likely to get noticed and get responses.  

Good luck :)

psyguy92

---

