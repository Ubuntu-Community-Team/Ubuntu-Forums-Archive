---
title: "Gutsy Upgrade, now no internet."
date: 2007-10-06
forum: Networking &amp; Wireless
---

### Post by AndMei on 2007-10-06
Hello one and All

I have been using feisty(64bit) for a couple of months flawlessly. I decided to upgrade to Gutsy, and after the install, I have discovered I have been unable to access the internet.

I am connected through a Dlink G604 Wireless router. It is a hard wired NIC connection. I have a windows XP laptop which connects fine both wirelessly and wired through the Dlink router, so I have ruled out the router and cable as the causes of the problem.

I am able to acces other computers and an xbox on my network, but cannot load internet pages.

My NIC is integrated with the Motherboard and is an Marvell 88E8056 PCI-E GB. It is using the logical name eth0. It is detecting a network link and has been assigned an IP and DNS. 

I have selected Manual Configuration and DHCP in the network manager. 

The network and internet were flawless in feisty. Help

Thanks for your time

Andrew.:confused::confused::confused:

---

### Post by kevdog on 2007-10-06
What driver did you use in Feisty?? Or did you have to install a driver in Feisty.  Gutsy is using a different kernel so the driver for your card needs to be located inside the new kernel by default, or you need to load the driver into the kernel.  If you dont know, I think during the booting process, you can boot up into the old kernel -- if you did an upgrade, and then use lshw -C network to determine the old driver you were using.

---

### Post by AndMei on 2007-10-06
Thanks for the reply

I'll try to boot into the old kernel. In feisty everything just worked. I didn't have to install any restricted drivers.

Andrew

---

### Post by banana989 on 2007-10-07
I had the same problem with 2.6.22-13 w/ AMD64. 

My system uses the forcedeth network driver.

---

### Post by AndMei on 2007-10-07
Gday

I have spent a couple hours going through everything and this is what I have discovered.

1) I booted into kernel 2.6.20-16, but no change in internet connectivity.
2) I Inserted the Feisty install disc and ran off that. Normal connectivity..
3) The original driver was SKY2 v1.13.
4) The driver in Gutsy is SKY2 v1.14
5) The network manager applet is now v 0.6.5 vice the old v.0.6.4
6) Here are the changes I have noted in the network manager which is where i suspect the problem lies...maybe.
       a)The old nm applet had roaming disabled.
       b)in the new one if I deselect roaming It no longer gives me connection info from the nm applet. To get the network info,  I have to select manual config, then DHCP. I have to use terminal to view the IP/DNS setup. When I click on the applet icon it doesn't do that fancy little reconnect swirl. I have to right click to disable network, then do the same to reconnect.
      c)With roaming selected on(I assume this is for Wireless), the applet shows a wired connection with the proper network configuration, like the previous version. 
      d)I can connect to the router, and other computers on my home network. The other computers on my network can connect to the internet and my Ubuntu machine.
7) I am going to try another network manager, and barring that wait for the alpha Gutsy and try it off the disk. Failing that I guess re-install Feisty.

Thanks

Andrew

---

### Post by caled on 2007-10-09
Hi Andrew
  I think this is the same issue I am having with my desktop. I know the home network is working fine as I am on it wirelessly now, however gutsy can not seem to connect through a wired connection although it is capable of pinging [www.ubuntuforums.org](www.ubuntuforums.org).

I'm using a Via Rhine II and also a Rhine III chipset, so I dont think that the chipset drivers are to blame.

Really driving me insane, this one!

caled

---

### Post by kevdog on 2007-10-09
Can you post lshw -C network and look through dmesg (dmesg | more) for any errors relating to your network card.

Also post
route -n
cat /etc/resolv.conf

---

### Post by caled on 2007-10-09
I think I have solved the problem I was having, and so hopefully you will have the same solution.
For some reason, although it worked in feisty, the DNS servers do not seem to be recognised by DHCP, and so in System>Administration>Network, under the DNS tabs delete the current DNS servers and add the OpenDNS server addresses, which are
208.67.222.222
and
208.67.220.220

Hope this helps

btw, what ISP are you on and what brand router have you got?
I'm on an AOL connection running through a safecom router

---

### Post by banana989 on 2007-10-17
Is anybody else experiencing this? I've gone up to 2.6.22-14 and it still doesn't work! 2.6.22-12 works great.... is this really a dns thing?

---

### Post by helvete on 2007-10-18
having the same problem old kernel worked fine new kernel nope, i can connect to pages but takes near to a minute to get a page up

---

### Post by lizardbliz420 on 2007-10-18
I have the same problem too redic slow page loads

---

### Post by amcp21 on 2007-10-19
> **lizardbliz420 said:**
> I have the same problem too redic slow page loads
i have tha same issue too, but my lan card is disabled, the lights go off when I boot up ubuntu, but on the windows works fine

---

### Post by bclintbe on 2007-10-19
I found what banana989 had to say very interesting. I'm also running an AMD64 with the forcedeth network driver and having intermittent problems. I just upgraded to 7.10 today and that's when the problems seemed to start.

Sometimes I get a connection right from boot (I can see the lights on the router from where I sit), sometimes I don't. If I then do a hard boot, sometimes I get a connection. I did notice that once after signing in to Ubuntu I just unplugged and replugged into the NIC on the back of the computer... voila, lights come on and I have a connection.

---

### Post by helvete on 2007-10-19
i tried manually putting in the DNS servers from my ISP and its working alot better, however loaded up this morning and the setting i put in were gone!!!

---

### Post by banana989 on 2007-10-19
so ... should a problem ticket / bug report be filed ?

---

### Post by bclintbe on 2007-10-19
I added a bug report last night. It's #154207 "Wired internet connection does not start at boot". If anyone can add anything to the bug report from their experiences, that would be great.

---

### Post by mshaheen on 2007-10-19
hello guys

same problem here , but after reading a little more on the forums found that it's really a DNS problem somehow linked to IPV6 

just add the DNS servers IP from your ISP into SYSTEM>ADMINISTRATION>NETWORK>DNS
and everything should work ( but i little bit slower than usual )

also in firefox , 
put "about:config" in the address bar and hit enter
search for "IPV"
change "network.dns.disableIPv6" from false to true by double clicking it

restart firefox

things look better to me now ,try it guys and tell me what do u think

---

### Post by 3ws on 2007-10-19
I've been having the same problem, but have resolved it. I followed the advice about disabling IPv6. however, it was already set to 'false'. So not knowing what else to do I set it to 'true', and it works!

---

### Post by bclintbe on 2007-10-19
I had seen some of the forum posts about DNS issues as well, but they seemed different in that those people seemed to be able to still get a connection to their router/LAN. For me, the issue seems to be that the NIC itself is not being started at boot up (no LEDs on the NIC on the computer). 

I'll still look at the solution you mention when I get home and see if it works. Don't really like the idea of it working "but slower"...

---

### Post by bclintbe on 2007-10-19
Found a similar problem on a thread tonight that got me thinking. This other person has an nVidia graphics card (so do I) and his onboard NIC is also nVidia (like me). As soon as he enabled the nVidia restricted graphics driver, he also started to have problems. So, in the BIOS I disabled the nVidia NIC, put in an old ethernet card I had laying around and rebooted. So far, no problems. Internet seems to be running fine. 

Is it possible (just maybe) that somehow the nVidia restricted graphics drivers were screwing up the nVidia NIC???

---

### Post by admullis on 2007-10-20
> **bclintbe said:**
> 

Is it possible (just maybe) that somehow the nVidia restricted graphics drivers were screwing up the nVidia NIC???

Possible. I have an NVidia graphics card. The Gutsy upgrade left me with no X, and no network. X couldn't start because my NVidia drivers did not have an interface to the new kernel, or so the error message told me.

Luckily I had the NVidia driver install app still on my hardrive (get it from the NVidia site). Just click through to have it rebuild the driver interface to the new kernel

 I restarted, and X worked fine... and now so does the network.

---

### Post by MarkCrossley on 2007-10-20
I've just sorted the problem for my upgrade.

For some reason the upgrade disables the ethernet connection.
To enable it: System -> Administration -> Network. Select the 'Wired connection' and then click on properties. In the tick box that appears click on 'Enable this connection', then in the configuration section select DHCP (or static IP if that's what you use.)

Note - when I first tried to do this the network option wasn't available in the Administration menu. If that's the case for you:
System -> Preferences -> Main Menu. On the left hand side select Administration (right at the bottom). Then make sure the tickbox next to Network is selected.

I hope this works for you.

Mark

---

### Post by shouravv on 2007-10-20
I had the same problem at first, but then once I activated my network connection from System > Administration > Network , it started working just fine.

The weird thing is after installation Gutsy would not automatically enable the network connection available. I drove me nuts.

---

### Post by egrog52 on 2007-10-30
I had the same problem only thing was the box works perfectly happily on a netgear DG834 but not on the Safecom router . Tried another box also Gutsy the very same result , reverting to feisty and connects to the Safecom no problem.

---

