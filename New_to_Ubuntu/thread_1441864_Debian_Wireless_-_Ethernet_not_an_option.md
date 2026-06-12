---
title: "Debian Wireless - Ethernet not an option"
date: 2010-03-29
forum: New to Ubuntu
---

### Post by Lunami on 2010-03-29
Alright, I'm trying to get my wireless working on an old Compaq Armada 1750 (400 mhz processor, 10 gig hard drive, 128 MB ram). The 3com support, although I do have a cable for allowing it to use ethernet, the cable, simply doesn't work, so I'm unable to do ethernet, as the laptop doesn't have an ethernet port.

The wireless, I just can't seem to get anything running, as I keep getting those blasted errors;


Errors were encountered while processing:

I'm trying to get Network Manager running, but it simply isn't working. I'm running out of patience. Apparently, I'm assuming I won't be able to do anything with this laptop as it doesn't have the proper port to run an ethernet cable. Is there anywhere I can the proper files from my windows machine to transfer the files to the laptop? I have a USB drive, but I'm getting the errors either way.

---

### Post by undecim on 2010-03-29
> **Lunami said:**
> Alright, I'm trying to get my wireless working on an old Compaq Armada 1750 (400 mhz processor, 10 gig hard drive, 128 MB ram). The 3com support, although I do have a cable for allowing it to use ethernet, the cable, simply doesn't work, so I'm unable to do ethernet, as the laptop doesn't have an ethernet port.

The wireless, I just can't seem to get anything running, as I keep getting those blasted errors;


Errors were encountered while processing:

I'm trying to get Network Manager running, but it simply isn't working. I'm running out of patience. Apparently, I'm assuming I won't be able to do anything with this laptop as it doesn't have the proper port to run an ethernet cable. Is there anywhere I can the proper files from my windows machine to transfer the files to the laptop? I have a USB drive, but I'm getting the errors either way.

Can you open a terminal, and copy and paste this text into it:
```
lspci
```
press enter and post the output here.

---

### Post by mikeyphi on 2010-03-29
Someone might be able to suggest options if you could provide the wireless chipset.

---

### Post by fly-by-night on 2010-03-29
1.  State your Ubuntu version (Debian is not Ubuntu and probably have support somewhere)
2. Don't say "the cable don't work" simply because the laptop is without ethernet.
3. Have you downloaded Windows drivers (or have available) for you wireless device
4. Have you installed **ndiswrapper** and **ndisgtk**
5. Did you install the drivers through ndisgtk etc (that bit you can google/search here)
6. You might have to restart your network from time to time (after changes).
7. You might have to edit two files (i) resolv.conf to add DNS servers (google or search here) and (ii) /etc/network/interfaces (google/search here).  
If you need DNS servers use 208.67.222.222 and 208.67.220.220 (openDNS)

Hang in there.  The Ubuntu and Linux community work hard to make things easier for us.  Respect.

And the chipset as mentioned by mike...

---

### Post by Lunami on 2010-03-29
fly-by-night

1. I'm not using Ubuntu, I'm using Debian Lenny.
2. The ethernet doesn't work. I have an adapter for my 3com PCMCIA card to use ethernet. It simply doesn't work. Either too old, or something may have gone wrong with it, etc... I don't know.
3. I have a disk for my wireless adapter, yes.
4. I can't get any of the network things to even install correctly, and I can't install them with the internet, because I can't get it.
5. Again, can't do that yet, because I don't have ndiswrapper or etc...
6. I'm not in control of that, but I'm sure if I needed to, I could get the owner of this network to reboot it.
7. I'll worry about OpenDNS when I get this working.

I don't even have a utility for wireless yet, it's what I've been trying to do, and it simply doesn't allow me to dpkg them. I downloaded them from the debian homepage onto my flash drive, and then to my laptop. There aren't options on my laptop for wireless yet, and this is my problem at the moment. Perhaps I should have been more specific. And yes, I have searched for quite a while, as I've been working on this laptop for about a week now, and I've attempted to solve this issue for several days now, and have given up and decided to come here for help.


This should answer your questions mikeyphi and undecim.

lsusb
Bus 001 Device 008: ID 0846:6a00 NetGear, Inc. Wg111(v2) 54 Mbps Wireless [RealTek RTL8187L]

If more information is needed, simply ask.

---

### Post by undecim on 2010-03-29
> **Lunami said:**
> I don't even have a utility for wireless yet, it's what I've been trying to do, and it simply doesn't allow me to dpkg them. I downloaded them from the debian homepage onto my flash drive, and then to my laptop. There aren't options on my laptop for wireless yet, and this is my problem at the moment.

So this problem is installing a wireless utility, rather than installing drivers?

If that's the case, I have two questions:

1: Do you have the "wpa_supplicant" command
2: What happens when you try to dpkg the packages you downloaded? What error do you get?

I need more specific information to diagnose the problem. Or, as Sherlock Holmes would say "Data! Data! Data! I can't make bricks without clay."

---

### Post by fly-by-night on 2010-03-29
Lunami remember the output from the second post to get you wireless device (undecim) info.

The Ubuntu CD's have ndiswrapper and ndisgtk on it.  It might be the same with Debian.  Add the CD to the repository in Synaptic Package Manager (or the one in Lenny) if it's not already there.  Search using Synaptic and it should pick it up on the CD.  If you reached this point then install ndisgtk that will automatically add ndiswrapper to the install.

Edit:  I see I'm posting after someone that more than likely know more than me.  Once you ensure everything  checks out with him/her then continue to ndiswrapper etc.

---

### Post by Lunami on 2010-03-29
> **undecim said:**
> So this problem is installing a wireless utility, rather than installing drivers?

If that's the case, I have two questions:

1: Do you have the "wpa_supplicant" command
2: What happens when you try to dpkg the packages you downloaded? What error do you get?

I need more specific information to diagnose the problem. Or, as Sherlock Holmes would say "Data! Data! Data! I can't make bricks without clay."

Verily.
1. I've never heard of such a thing. However, typing wpa_supplicant does bring up a --help like set of text.
2. I get something along the lines of this, this is where it looks like it starts to go wrong.

dpkg: dependency problems prevent configuration of network-manager:
 netowrk-manager depends on libnl1; however:
  Package libnl1 is not installed
 network-manager depends on libnm-util0; however
  Package libnm-util0 is not installed.
 network manager depends on dhcdbd (>= 1.12-2); however:
  Package dhcdbd is not installed.
dpkg: error processing network-manager (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 network-manager

From here, I tried to find libnl1, etc... and install them. It hasn't been working. I'll try making a new one again after a restart. (This laptop doesn't enjoy booting, at all. Going to install fluxbox when I get the wireless working.)

Edit:
By the way, love the Holmes quote.

---

### Post by undecim on 2010-03-29
> **Lunami said:**
> Verily.
1. I've never heard of such a thing. However, typing wpa_supplicant does bring up a --help like set of text.
2. I get something along the lines of this, this is where it looks like it starts to go wrong.

dpkg: dependency problems prevent configuration of network-manager:
 netowrk-manager depends on libnl1; however:
  Package libnl1 is not installed
 network-manager depends on libnm-util0; however
  Package libnm-util0 is not installed.
 network manager depends on dhcdbd (>= 1.12-2); however:
  Package dhcdbd is not installed.
dpkg: error processing network-manager (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 network-manager

From here, I tried to find libnl1, etc... and install them. It hasn't been working. I'll try making a new one again after a restart. (This laptop doesn't enjoy booting, at all. Going to install fluxbox when I get the wireless working.)

Edit:
By the way, love the Holmes quote.

Welcome to dependency hell. It's what package manager were designed help with, but since you are having to mess with packages manually, it's going to be a pain doing all this with a thumb drive.

Since you seem to have basic CLI wireless tools installed, I think that the easiest thing to do would be to connect to your network manually, then update/upgrade/install stuff from there. A quick Google search led me to this [http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/](http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/), which looks like a good tutorial/explanation to me.

If you can manage to get a connection once, install your network manager, and you should be good from there.

---

### Post by Lunami on 2010-03-29
> **undecim said:**
> Welcome to dependency hell. It's what package manager were designed help with, but since you are having to mess with packages manually, it's going to be a pain doing all this with a thumb drive.

Since you seem to have basic CLI wireless tools installed, I think that the easiest thing to do would be to connect to your network manually, then update/upgrade/install stuff from there. A quick Google search led me to this [http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/](http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/), which looks like a good tutorial/explanation to me.

If you can manage to get a connection once, install your network manager, and you should be good from there.

Alright then. Seems I'll just start working my way through "dependency hell". Hopefully, I'll be able to make it out. I'll report anything needed after I get this all worked out.

---

### Post by Lunami on 2010-03-30
I'll likely be changing the title here soon. Anyhow, I've come across a stuck spot on my dependencies.



dpkg:dependency problems prevent configuration of libstdc++6-4.3-dev:
 libstdc++6-4.3-dev depends on g++-5.3 (= 4.3.2-1.1); however:
  Package g++-4.3 is not configured yet.

This is the issue I'm having, and I can't seem to even find this error with google. Any help for what I need to do? I've tried opening the g++ to try and configure it, but it was a no-go.

---

### Post by undecim on 2010-03-30
> **Lunami said:**
> I'll likely be changing the title here soon. Anyhow, I've come across a stuck spot on my dependencies.



dpkg:dependency problems prevent configuration of libstdc++6-4.3-dev:
 libstdc++6-4.3-dev depends on g++-5.3 (= 4.3.2-1.1); however:
  Package g++-4.3 is not configured yet.

This is the issue I'm having, and I can't seem to even find this error with google. Any help for what I need to do? I've tried opening the g++ to try and configure it, but it was a no-go.

You need to install g++-4.3 I think.

---

### Post by Lunami on 2010-03-30
I had that as well, but it didn't work. I somehow managed to get it to work, no idea how, exactly not sure how I did so, however. Either way, still working on the wireless.

At the moment, I'm trying to find a way to add the Debian install disk to my repository via command line.

---

### Post by undecim on 2010-03-30
> **Lunami said:**
> At the moment, I'm trying to find a way to add the Debian install disk to my repository via command line.

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

has this line from /etc/apt/source.list
```
deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080701)]/ hardy main restricted

```

Adjust yours to match your debian disk.

---

### Post by Rameshnb on 2010-08-25
Hi,

I have a same problem, please look at the error below.

root@ramesh-desktop:/home/ramesh/Downloads# [COLOR=Red]dpkg -i g++-4.3_4.3.2-1.1_i386.deb[/COLOR]
(Reading database ... 116231 files and directories currently installed.)
Preparing to replace g++-4.3 4.3.2-1.1 (using g++-4.3_4.3.2-1.1_i386.deb) ...
Unpacking replacement g++-4.3 ...
dpkg: dependency problems prevent configuration of g++-4.3:
[COLOR=Red] g++-4.3 depends on libstdc++6-4.3-dev (= 4.3.2-1.1); however:
  Package libstdc++6-4.3-dev is not configured yet.[/COLOR]
dpkg: error processing g++-4.3 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 g++-4.3
root@ramesh-desktop:/home/ramesh/Downloads# [COLOR=Red]dpkg -i libstdc++6-4.3-dev_4.3.2-1.1_i386.deb[/COLOR]
(Reading database ... 116231 files and directories currently installed.)
Preparing to replace libstdc++6-4.3-dev 4.3.2-1.1 (using libstdc++6-4.3-dev_4.3.2-1.1_i386.deb) ...
Unpacking replacement libstdc++6-4.3-dev ...
dpkg: dependency problems prevent configuration of libstdc++6-4.3-dev:
 [COLOR=Red]libstdc++6-4.3-dev depends on g++-4.3 (= 4.3.2-1.1); however:
  Package g++-4.3 is not configured yet.[/COLOR]
dpkg: error processing libstdc++6-4.3-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libstdc++6-4.3-dev

here both are getting into loop on dependency. Please help on this.

Regards,
Ramesh:D

---

