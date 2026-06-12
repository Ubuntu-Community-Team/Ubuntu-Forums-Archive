---
title: "Simple Network setup"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by Hygaphunkik on 2009-12-18
Hi Bit of a long one here.

At work we are having our network swapped over to an ubuntu based system, leaving windows behind. Most of the pc's are ubuntu standalones that need access to a shared filing system and to the internet, a few are windows based due to the software that needs to be run on them, and behind this all is an 8.04 server. Now in a few months when this is all setup and stable I will be taking over the administration of this network and have never done anything like this before so I thought I would get to know a bit more about what I am doing by building a simple network at home. I already have a couple of desktop pc's and a few laptops that I can bring in to service on this project, and a lan cable coming out of my BT broadband box to supply internet access. What I need to know before I really start installing server edition 8.04 is what else might I need. Some kind of lAN splitter, or some wireless splitter box? Once I have all the bits together then I can start to put this together and ask some more questions.

Remember when replying I am an idiot ;-) and have no experience of creating a real network, either on ubuntu or windows.

Thanks.

---

### Post by ubudog on 2009-12-18
This might help: [https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

---

### Post by bodhi.zazen on 2009-12-18
A LAN is easy to set up, are you using a router, or do you wish to set yup the Ubuntu server to do your routing (DNS, DHCP, firewall, etc) ?

---

### Post by Cheesemill on 2009-12-18
You need a network hub or switch to connect all the bits and pieces together, you basically just plug a network cable from each of the machines and the cable from your BT box into it. This should get all of your hardware onto the same network.

---

### Post by Hygaphunkik on 2009-12-18
> **Cheesemill said:**
> You need a network hub or switch to connect all the bits and pieces together, you basically just plug a network cable from each of the machines and the cable from your BT box into it. This should get all of your hardware onto the same network.

Cool off to ebay for a network hub or switch.

@ all others.

Ultimately I would like to understand how to assign ip addresses, including reserving some, but I would be happy to start with a file server that I could use to share files between windows and ubuntu machines.

---

### Post by bodhi.zazen on 2009-12-18
You probably need a router =)

Switches if needed, not sure you can purchase what I think of as a "hub"

---

### Post by Cheesemill on 2009-12-18
> **bodhi.zazen said:**
> Switches if needed, not sure you can purchase what I think of as a "hub"

I know this but you'd be surprised how often I've seen switches referred to as hubs:)

---

### Post by running_rabbit07 on 2009-12-18
> **Hygaphunkik said:**
> Cool off to ebay for a network hub or switch.

@ all others.

Ultimately I would like to understand how to assign ip addresses, including reserving some, but I would be happy to start with a file server that I could use to share files between windows and ubuntu machines.
If you ever need help with addressing a small network, PM me. I am working on my Cisco certification and every bit of practice helps. To learn on our own, check out this link. [http://docs.sun.com/app/docs/doc/816-4554/ipplan-5?a=view](http://docs.sun.com/app/docs/doc/816-4554/ipplan-5?a=view)

OP, let me know how many hosts, switches, and routers you have and I can come up with an easy plan for you. 

I think the OP's biggest task is setting up the FTP server software on on each machine. Setting up shares with permissions on a multi-platform network is a bit harder.

---

### Post by running_rabbit07 on 2009-12-18
> **Cheesemill said:**
> I know this but you'd be surprised how often I've seen switches referred to as hubs:)

Yeah, I've seen many who didn't know the difference in the first weeks of CSCO 120. Hubs are phasing out. You can't get high speeds with all of the collisions hubs create.

---

### Post by Hygaphunkik on 2009-12-28
Thanks for suggestions guys but I am still trying to crawl let alone walk.

Hope you are prepared to help a total noober through this. Let me tell you how far I have got.
Work gave me an unused 3com Baseline Switch 2250plus. I plugged a LAN cable from the BT home hub (Broadband wireless router modem thing) into one of the input bits on the end (there are 2 LAN ports and 2 other ports above). In the main section I have plugged my server and a laptop.

The server is an ubuntu 8.04 edition, I put on s simple GUI front end X I think. The only software bits are firefox, gedit, Gnome Terminal, and synaptic. I followed the instructions on another thread to get this far. I plugged in the laptop expecting to see the server on the network, even if I could not share any files or anything, but could see nothing. So I have reached my first hurdle how do I configure the server to allow my laptop to see it?

Remember I am a complete noober idiot, as you can probably tell from the completely untechnical way I have described my situation.

Once the server is set up I will probably create another ubuntu desktop, to plug in and a Kubuntu laptop as well. But lets start with this little step. How do I see my server, and if I can create a folder to share files that would be extra magic.

Any help would be appreciated though I cannot guarantee to respond to each post individually.

---

### Post by mapes12 on 2009-12-29
I know there are zillions of guides out there but here's one I found particularly useful. It focuses on Debian (which Ubu is based on) but the networking stuff is generic to all systems. Happy reading: [http://www.aboutdebian.com/](http://www.aboutdebian.com/)

:lolflag:

---

### Post by Hygaphunkik on 2009-12-30
Cheers Mapes

I came across that one and have now managed to get ubuntu laptops sharing a samba file server type thing. I am still having problems with Kubuntu and windows, but to be honest I don't know windows as well as ubuntu. Ubuntu seems to encourage learning and understanding what is going on whereas windows discourages it.

Anyway, I used webmin to administrate and that helped a huge amount, just to start pointing me in the right direction.

Off to find out what is going on with the KDE and mounting samba shares, before I tackle windows.

---

### Post by running_rabbit07 on 2009-12-30
You will need the program in the screenshot for Kubuntu. I had Kubuntu instaled for a week and burnt out on its deficiencies pretty quickly. It looks great, but too many functionality disorders.

---

### Post by Hygaphunkik on 2009-12-30
Cheers Running Rabbit 

I installed nautilus this morning, mainly because it worked a charm in the x windows manager I installed on the server, and now I have a wierd kind of Gnome/Kubuntu laptop. Still it seems to work ok and I have been transfering files quite happily.

Now I am moving onto the trickiest phase, getting the Mrs Vista PC to see the samba share folder. After digging around I just managed to change the regedit file thing (believe me that was an epic struggle to find what was going on with that. Why does windows make so little sense, and why is it so hard to find nice hand holding help for the trickier bits). I just have to wait and see what happens when I get a chance to reboot it. She looks like she is set in for the evening.

---

### Post by running_rabbit07 on 2009-12-30
I haven't been able to get Windows and Ubuntu to work with each other yet. It seems that doing that requires setting up share accounts and all that happy stuff. I have seen a few HowTos floating around, but haven't taken the time to try them.

---

### Post by Hygaphunkik on 2009-12-31
Bingo.

I now have a samba file server in the living room. My vista problem was caused by the zone alarm firewall. I had to set an exception for the IP address of the ubuntu server. As soon as I had done that up popped the server and the shares folder. Magic. Next step, a huge usb hard drive to plug in, so my data is safe, and then I can start again, just to confirm that I know what I am doing. 

The whole thing is working through my home hub router, not as effiecient as a switch I know but it is a start and allows access to the network from wireless devices. I will have tpo start looking at that to see how I can configure static IP's, oh and set up a printer share as well.

Thanks for everyones help so far.

---

### Post by oldsoundguy on 2009-12-31
a quick tip .. make sure all of your units are on the same network .. using MSHOME for the Windows machines and the Linux default means that one will not be able to talk to the other.  It was easier to rename the MSHOME to the Linux default (which is NETWORK on my system), so that is what I did!

---

