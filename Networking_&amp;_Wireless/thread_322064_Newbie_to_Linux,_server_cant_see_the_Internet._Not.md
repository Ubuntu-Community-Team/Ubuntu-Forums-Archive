---
title: "Newbie to Linux, server cant see the Internet. Not sure where to begin :-("
date: 2006-12-19
forum: Networking &amp; Wireless
---

### Post by noreaga on 2006-12-19
Alright here goes. Newbie here to Linux, but needed to use it for work, so here I am :-).

I installed Red Hat 3 today on a Dell server for work. We're using a basic cat6 cable, so no wireless stuff here. During the install, I was prompted to enter in IP and DNS server addresses (I am assigned a static IP, so I unchecked the 'use DHCP' option and filled out the info). There was a choice between the eth0 and eth1 interface.

To tell you the truth, I didnt know which one to use, or what the differences were, so I just stuck with eth0.

Anyways, long story short, I have no access to the Internet once I boot into RedHat.

And, to top it all of, I dont know where to begin troubleshooting since Im not familiar with doing such tasks on a Linux box. Windows wouldve been a different story.

So, Im wondering (hoping) if anyone here can help me out. What should I start off checking for, and how ? Whats this eth0/eht1 business ? How can I verify that the static IP and DNS info I entered for the box has been captured by Red Hat ?

Thanks everyone :-)

---

### Post by ciscosurfer on 2006-12-19
> **noreaga said:**
> Alright here goes. Newbie here to Linux, but needed to use it for work, so here I am :-).

I installed Red Hat 3 today on a Dell server for work. We're using a basic cat6 cable, so no wireless stuff here. During the install, I was prompted to enter in IP and DNS server addresses (I am assigned a static IP, so I unchecked the 'use DHCP' option and filled out the info). There was a choice between the eth0 and eth1 interface.

To tell you the truth, I didnt know which one to use, or what the differences were, so I just stuck with eth0.

Anyways, long story short, I have no access to the Internet once I boot into RedHat.

And, to top it all of, I dont know where to begin troubleshooting since Im not familiar with doing such tasks on a Linux box. Windows wouldve been a different story.

So, Im wondering (hoping) if anyone here can help me out. What should I start off checking for, and how ? Whats this eth0/eht1 business ? How can I verify that the static IP and DNS info I entered for the box has been captured by Red Hat ?

Thanks everyone :-)eth0 and eth1 stand for your network card locations.  If you've setup your IP and DNS details specific to eth0 already, then you can try to switch over the cable to the other NIC (Ethernet card) that you have on your computer.

From a Terminal (Applications > Accessories > Terminal) you can enter in **ifconfig **or **ifconfig -a** to see if the details you've entered for your card took or not (most likely they did).

To get your networking restarted, you can enter in the following (again, into a Terminal)```
sudo /etc/init.d/networking restart
```I don't know if the following command will work on Red Hat or not and for some strange reason, I feel that ifconfig may not be installed either (I may be getting confused with SuSE)...anyway, you can also try entering in the following into a Terminal if the last command didn't work```
sudo ifdown eth0
sudo ifup eth0

AND IF YOU'RE USING ETH1 INSTEAD

sudo ifdown eth1
sudo ifup eth1
```Once you think things are setup okay, then go to a browser and try to hit a site.  Otherwise, from the Terminal again, you can try to Ping a site```
ping google.com
```If you get success, then you're good to go!

Hope this gets you started.  Please feel free to keep asking questions...someone here will be able to help you out!

---

### Post by noreaga on 2006-12-20
Thanks guys, got her up and running.

The problem was that there was no entry in the routing table for the default gateway, even though I could have sworn that I specific the IP during RedHat setup.

I just had to go in through the terminal, and use the route add command to add it in, and voila !

Thanks everyone !

---

### Post by ciscosurfer on 2006-12-20
> **noreaga said:**
> Thanks guys, got her up and running.

The problem was that there was no entry in the routing table for the default gateway, even though I could have sworn that I specific the IP during RedHat setup.

I just had to go in through the terminal, and use the route add command to add it in, and voila !

Thanks everyone !Glad to hear that you've got it all worked out!

---

