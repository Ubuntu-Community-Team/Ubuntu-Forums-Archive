---
title: "linksys does not work even though it recognizes it!!!"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by nimafl on 2007-04-16
Hello,

I am using a linksys network card. It recognizes the wireless card because it shows up, BUT it is always at 0% and it will not connect to the network even though it recognizes it. I am using the feisty version of ubuntu. I also had someone else connect to my wireless network on their computer using feisty and it worked for them. Any ideas?

---

### Post by pmenefee on 2007-04-16
No answer for you, but I'll be watching the thread because I've got the same problem.:confused:

---

### Post by computerease on 2007-04-16
The issue is most likely with the Linksys system itself.  This problem shows up on M$ windows machines as well as Linux machines.  I have seen this problem in a network I was setting up in Omaha (for an UNO professor).  While some machines would work virtually immediately, others would not no matter what we did.  We spent hours on the phone with Linksys and they were not able to solve it, I had the same thing myself circa a year ago, and have a current client in Illinois who has the same difficulty.  These are not the only clients that have had this problem.  My solution for my own network was to dump the Linksys hardware entirely and move to Netgear.  I had spent three weeks and untold hours on the phone with Linksys in order to find a solution.  Even when a solution was supposedly found, the system would inexplicably and irratically collapse, requiring the whole operation to be sequentially shut down and restarted numerous times per week.  I installed the Netgear router and cards.   My systems recognized and came up virtually immediately (a mixed network with both Linux and M$ XP).  This problem apparently appeared soon after Cisco began integrating Linksys into their operations and has persisted all of this time.  I simply advise my clients to change products.  Every time they do their problems go away.
I know the above is not much help with your problem, but I don't think your situation is unique.  It is a Linksys systems failure and it appears they have not, to date, addressed this intransigent problem.

---

### Post by jpl80 on 2007-04-16
what is the exact name and model number of the linksys card you are using? Did you go to the Networking part of the System menu and make sure it is turned on?

You may want to become more familiar with your basic setup utilities like, iwconfig and iwlist. try running:

sudo iwlist wlan0 scan

that should scan the network and tell you what wireless networks the card can see.

If that doesn't work it may be a driver issue. [Look at ndiswrapper and read it]("http://ndiswrapper.sourceforge.net/"). It's a way to run windows drivers on Linux. Linksys should release all of their drivers for free from their website.

Good Luck. I have a Linksys WUSB11 and it works just fine. But I have had issues with other Linux distros in the past.

---

### Post by computerease on 2007-04-16
There is another link that may also apply to your situation:
Has 2.6.17-11 dropped some wireless support? 
[http://ubuntuforums.org/showthread.php?t=366107](http://ubuntuforums.org/showthread.php?t=366107)

---

### Post by nimafl on 2007-04-19
i tried the sudo iwlist wlan0 scan 

and it said that the interface doesn't support scanning?

What can i do?

---

### Post by tturrisi on 2007-04-19
> **nimafl said:**
> i tried the sudo iwlist wlan0 scan 

and it said that the interface doesn't support scanning?

What can i do?
answer ALL of jpl80's questions!

---

### Post by nimafl on 2007-04-23
okay i tried 

lspci and here is my wireless card info

01:00.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

---

### Post by tturrisi on 2007-04-23
open a root terminal & do:

apt-get install build-essential
apt-get install linux-headers-`uname -r`
ifconfig ra0 down
rmmod rt2500
wget [http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz)
tar -xvzf rt2500-cvs-daily.tar.gz
cd rt2500-cvs-xxxxxxx/Module (#xxxxxxxxxx is a number that represent more or less a date)
make && make install
modprobe rt2500

---

