---
title: "Trying 2 setup the ”eth1” network card to allow the internet to pass onto other PCs"
date: 2007-08-19
forum: Networking &amp; Wireless
---

### Post by bhowerton on 2007-08-19
Hello,

I am not sure where to post this so i also posted this in the absolute beginner section, but being that that is the absolute beginner section...I think that this question might be to advanced for that section....that is why I also posted it here.

Can someone please help me as this is what I am trying to do:

I have a computer (Compaq 5300US / Intel Celeron Processor 1.1GHz / 320MB SyncDRAM / 40GB HDD / “2” Ethernet network cards / 6MB download & 1MB upload Fiber Internet connection / CD-RW / Running Ubuntu Christian Edition vers. 7.04) that I am dedicating to be a Linux Server.

I am trying to setup this machine so that I can take my my internet connection from the wall and send it into the “eth0” Ethernet card (to supply the internet to the network). Then I want to send the internet out through the “eth1” Ethernet card (to supply the internet to all other PCs on the network).

So far I have got the “eth0” Ethernet card to accept the incoming internet signal (I am using that connection right now).

**But, how do I setup the”eth1” Ethernet network card to allow the internet to pass onto all the other PCs on the network.**
------------------------------------------------------------------------------------------------------------------------------
I just rebooted and went into BIOS. I checked the status of both Ethernet cards. It shows them as being active. I also clicked on the Ubuntu Start Menu button / System / Administration / Network. This also shows both "eth0" & "eth1" as being both a wired Connection and Active with a check mark. The address for both is "DHCP".

Right now I have the internet going from the wall into "eth0"...it is working...I am on the internet typing this post.

I also have a cable going from "eth1" (out of the Linux box) into the WAN port on my Netgear WGR614v5 Wireless router. From the router I have my other desktop PC connected by cable and I have a wireless laptop. Neither of the 2 PCs currently have any internet going to them.

**It is like the internet is going into "eth0" but not leaving through "eth1".**

Any help would be and is greatly appreciated!!

Please be as specific as possible as I am a new Linux user. I desperately want to get away from Microsoft and help support the Ubuntu Linux movement.

---

### Post by Soarer on 2007-08-19
Hi,
You may need to read up a little on networking, it will help you understand how to achieve what you want to do.

For example, eth0 is running DHCP and is therefore getting it's IP address from the 'wall' - presumably a modem or router. The other connection, eth1, has no where to get an IP address from in the same way. You need to set-up DHCP server on that interface to *provide* IP addresses to your connected units. It will therefore need a *fixed* address of its' own.

Then you need to ensure that traffic into eth1 is routed through your server to eth0 and then to the Internet.

Finally, you have to ensure that the built-in firewall (IPTables) permits the connections you want, and refuses those you don't.

It sounds harder than it is :). The easiest way is to use a front-end to the built in firewall. People often recommend 'Firestarter' (in the repos) for this, but I haven't used it much. I have used [Shoreline Firewall]("http://www.shorewall.net/") to do this. You *can* configure IPTables yourself, but it requires considerable knowledge.

At this point you are probably about ready to give up, but it's not as hard as it sounds. Try having a look at [https://help.ubuntu.com/7.04/server/C/ip-masquerading.html]("https://help.ubuntu.com/7.04/server/C/ip-masquerading.html") and reading the documentation. It's possible you could just cut & paste the entries at the bottom of the page :).

---

