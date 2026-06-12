---
title: "[SOLVED] Connecting through another computer?"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by Washer on 2008-06-14
I have a desktop. Is it possible to get the net from the wireless on my laptop? I also have a router & the assorted router cables. All are running hardy.

---

### Post by mohitchawla on 2008-06-14
Connect the two systems with a cross cable, open up the network manager in your desktop system, click the properties of the ethernet interface, enter the ip address of your laptop in the gateway field and the necessary address settings (static/dynamic) , I think that should do it. Cheers.

---

### Post by Washer on 2008-06-14
> **mohitchawla said:**
> cross cableI'm guessing that's not the cable that goes to/from the router. Is it possible to use the router instead?

---

### Post by mohitchawla on 2008-06-14
If your router does have ethernet ports on it, then yes , router can be used ,by connecting one end of the  router cable provided to you to the desktop and the other to the ethernet port on the router.

---

### Post by Washer on 2008-06-14
Appreciate it. I can't work on it now, but I figured I should find out if it was possible before I began. I'll probably have questions later.

---

### Post by Washer on 2008-06-14
do I need 2 network cards on the laptop?

edit: nvm I obviously have 2. Still can't get it working...

---

### Post by Washer on 2008-06-14
Ok now i'm not so sure. I'm going by [this guide]("http://ubuntuforums.org/showthread.php?t=197748").

> start firestarter and follow the guide, select your internet bound nic for internet side and local nic for local network side.
Start up the firewall if it is not already running."

so I did that & it started the firewall & it complains eth0 isn't ready. I connect to the router (it automatically disconnects from the wireless) then attempt to start firestarter again & it says wlan0 isn't ready.

So i can't connect to both at the same time - it's a network card problem isn't it?

---

### Post by mohitchawla on 2008-06-15
I am unable to follow here. You say when eth0 is ready , wlan0 isn't and vice-versa, right ? If yes, then its not a network card problem really. Also, are you sure the interfaces are named as eth0 and wlan0 (check ifconfig, iwconfig )? Plus, you could do without the firewall initially to make the process simpler.

---

### Post by Washer on 2008-06-15
Hmm. I was using ubuntu 6.06 because someone borrowed my hardy cd. I'm dling xubuntu right now, i'll post again when i'm done. I have to run it from cd & the 6.06 cd keeps freezing.

i didn't check ifconfig/iwconfig, I right clicked on the bar & hit properties. Also used that network tool that does ping/traceroute/ports etc & it said eth0, wlan0.

but yeah I don't know how to connect to both at the same time. Using the toolbar it always disconnects from wireless when I click wired & vice versa.


yup ifconfig/iwconfig confirms- eth0, wlan0, lo, sit0

---

### Post by Washer on 2008-06-15
well as it turns out the card works perfectly in 6.06 but not in xubuntu hardy... Researching.

---

### Post by The Martian on 2008-06-16
Hiya Washer.
I'm not sure I get what your after, you want to have network/internet access on both machines? And you've already got it on the wireless laptop, I'm assuming you're obtaining this from your router wirelessly? so now you need access for the desktop machine? The way to go is to connect to the router, (wired or wirelessly, wired would be better for a desktop), not the laptop. you only need one nic in each machine.
as I understand it Firestarter is for internet connection sharing, IE it's a sort of cutdown software internet (Network Address Translation) router that runs on the PC that has the internet connection, and then this machine routes the internet connection in and out to the correct internal IP numb.
This is exactly what a hardware router does, so you don't need the software version (Firestarter). 
To recap, internet comes in to router, machine/s connects to router, (wired or wirelessly).

I do hope I've not missunderstood your prolem.
All the best mate.
                     The Martian

---

### Post by Washer on 2008-06-16
Hey Martian. Yeah well the router /w wireless is in the lab down the hall. I can't get a cable to it, at least not easily. I guess I could buy a pci card, but i'm feeling stubborn, anyway i get more brag points with this. Nobody uses this laptop because it has no hard drive.

update: i got the wireless on xubuntu working, wish I had tried ndiswrapper first, would have saved me a few hrs.

---

### Post by Washer on 2008-06-16
ok i'm completely stuck getting both connections enabled simultaneously. I'm not even sure that it's necessary, only that firestarter won't work without both on. Any help would be appreciated.

I'm using one of these cards, WPC11v4. 
[img]http://img129.imageshack.us/img129/108/p5906162n1pu5.jpg[/img]

I think it might not be working same as an external USB adapter. I think I remember windows connecting to lan & wireless simultaneously using some USB device i had.

---

### Post by Washer on 2008-06-16
On the plus side, xubuntu is quite impressive. It only crashed once & I fixed that problem.

---

### Post by mohitchawla on 2008-06-17
The network card performs the same function as its USB counterpart.

By the way, if you are patient enough, could you post your original problem, in terms of your setup and what you actually want (in terms of internet access, equipment etc.). Just trying to make things simpler. Cheers !

---

### Post by The Martian on 2008-06-17
Hiya Mate.
I think I get ya now, you wanna use the old laptop as a repeater/extender?
Geddin a bit more complicated, and I,m out of my depth now, but you will need both cards running, with Internet conn sharing, (Firestarter) running on the connection of the card receiving signal from other router, I'd also think they need to be on different channels, as for the whole net set up, IP numbering and such I don't know.
If there is a prog you can find that will set up as an actual repeater/extender, then the setup and such should be taken care off and firestarter I imagine would,nt be needed.
Sorry I can't be more helpfull.
                            The Martian

---

### Post by Washer on 2008-06-17
> **mohitchawla said:**
> The network card performs the same function as its USB counterpart.

By the way, if you are patient enough, could you post your original problem, in terms of your setup and what you actually want (in terms of internet access, equipment etc.). Just trying to make things simpler. Cheers !

Ok, I have

- a wireless router down the hall, can't get to it with a cable
- a laptop with that linksys card that can access the internet through that wireless router
- a desktop without a wireless PCI card, can't access the internet
- a router that connects the laptop to the desktop /w wires, also can't access the net


I'm trying to get the desktop online through the laptop. A repeater/extender, as martian said.

---

### Post by Washer on 2008-06-26
Well I took a break & just now got it working. I'm posting from the desktop. All you really need is firestarter. This guide works best.

[http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)

I was missing the nameservers on the client & i think you have to explicitly add the http/https policies in firestarter, not sure, i'll add more when i start from a clean build again tomorrow.

oh and the command for enabling another connection is "sudo ifconfig eth[COLOR="Red"]X[/COLOR] 192.168.[COLOR="Red"]0.104[/COLOR] up" replace the red with your version

---

