---
title: "Networking in Kubuntu - How?"
date: 2005-04-06
forum: Networking &amp; Wireless
---

### Post by dickinsd on 2005-04-06
Ok I have used the Ubuntu Live CDs several times and I have various levels of success, nearly all of the time with ubuntu 4.10 I would have to setup the network my self, or at least goto the network config window at this point it usually finds the missing network device on its own and I can browse the web fine.

I have tried the Ubuntu 5.04 Live CD and the Kubuntu Live CD - both look very good, the Ubuntu 5.04 CD is great and I have been able to connect to the web just fine (even with wireless cards in some cases) - perfect!

I have a problem with one machine using kubuntu.

The machine is a desktop using the onboard network connection to connect to a router (using wires on this machine)

The network device is *Onboard: nVIDIA nforce3 LAN Controller*

I think my main problem is down to a sheer lack of knowledge of KDE - personally I prefer gnome.

I try to connect to any web page and it fails - web site cannot be found (I think from memory...)

How do I add network devices in KDE - that would be a really big help for now.

Dave

---

### Post by dataw0lf on 2005-04-06
Have you tried pinging other machines (or your router) ?  What does ifconfig report?

---

### Post by sjalex on 2005-04-09
First thing will be to try running (in a terminal) 'ifconfig' which displays all "up" network interfaces and will turn up an entry for at least something called "lo". You should probably have one called "eth0" as well. If you don't, try 'ifconfig -a' which will list all interfaces regardless of state (up or down).

If you see "eth0" after running 'ifconfig -a' but not after running 'ifconfig' your card is detected and drivers installed, but is not in an up state (not operational in the software/switched off).

depending on your network you can do a few things here,  but let's start with the card configuration and bringing it up. In kubuntu there's a handy dandy Control Center applet in the K menu. You can open that up and select "Internet & Network/Network Settings" and click the Administrator mode button. (I have had no luck getting it into administrator mode with the provided button, so YMMV on that. If the button doesn't work, at a terminal prompt do 'sudo kcontrol'. provide your password when prompted.)

Once you have the Network Settings dialog open you'll be shown a list of the interfaces and their various attributes. Select the relevant one and use the configure interface button. You'll want to make sure you check off the "Activate when computer starts" box.

If this stuff doesn't work, make sure the card and cable are working. You're showing link lights on both ends, right?

sjalex

---

