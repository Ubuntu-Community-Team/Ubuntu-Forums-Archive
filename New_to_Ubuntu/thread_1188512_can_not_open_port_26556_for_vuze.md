---
title: "can not open port 26556 for vuze"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by drdave69 on 2009-06-15
I installed vuze using synaptic. First problem, it needs port 26556 open (or any port of my choosing) to properly connect. I have forwarded the port in my router already, so I am pretty sure it is not a router issue. I have used ShieldsUp! to investigate the port, and it says the port is "stealth Unknown Protocol for this port, Unknown Application for this port", is there a way to open up this port in Ubuntu? Does Ubuntu have a firewall? Second problem, it is version 3.1.1.0 and it keeps trying to update. The file updates and says to reboot, which I do, but then it asks me to to it again repeatedly, It does not update. Any help with this would be greatly appreciated.

---

### Post by synapsys on 2009-06-15
Vuze sucks. I would use either transmission or uTorrent under wine.

---

### Post by SoftwareExplorer on 2009-06-15
> **synapsys said:**
> Vuze sucks. I would use either transmission or uTorrent under wine.

I know this is getting off drdave69's question, but deluge is native Linux and feels a lot like Azureus, (what vuze was before it was called vuze).

Question for drdave69: did you specifically install any firewall?

---

### Post by sandyd on 2009-06-15
> **drdave69 said:**
> I installed vuze using synaptic. First problem, it needs port 26556 open (or any port of my choosing) to properly connect. I have forwarded the port in my router already, so I am pretty sure it is not a router issue. I have used ShieldsUp! to investigate the port, and it says the port is "stealth Unknown Protocol for this port, Unknown Application for this port", is there a way to open up this port in Ubuntu? Does Ubuntu have a firewall? Second problem, it is version 3.1.1.0 and it keeps trying to update. The file updates and says to reboot, which I do, but then it asks me to to it again repeatedly, It does not update. Any help with this would be greatly appreciated.
Ill tell you whats going on here.

Vuze, when installed from the repos has problems. When you update, you are trying to update files **THAT YOU DON'T HAVE THE PERMISSION TO UPDATE**. because the files are owned by another user.

The best thing i would suggest is going to vuze.com and downloading a copy manually. Just save it into your home folder, create a shortcut and run it like that. 

As for the connection problems, have you tried enabling DMZ?. does your computer (not the internet) ahve a static ip?

---

### Post by SoftwareExplorer on 2009-06-15
As for your second question: If i remember correctly, vuze's updating mechanism doesn't work properly in Ubuntu because it is trying to change things for all the users on the system, but it is running as your user. (Which can't do that). If it annoys you, you could turn off the automatic updates, as when there is a new version of vuze packaged for Ubuntu, the update manager in **Ubuntu** will tell you.

Edit:Looks like carlee beat me to it, I need to learn to type faster:D

---

### Post by drdave69 on 2009-06-15
> **SoftwareExplorer said:**
> I know this is getting off drdave69's question, but deluge is native Linux and feels a lot like Azureus, (what vuze was before it was called vuze).

Question for drdave69: did you specifically install any firewall?

No firewall installed.

---

### Post by drdave69 on 2009-06-15
> **carlee said:**
> Ill tell you whats going on here.

Vuze, when installed from the repos has problems. When you update, you are trying to update files **THAT YOU DON'T HAVE THE PERMISSION TO UPDATE**. because the files are owned by another user.

The best thing i would suggest is going to vuze.com and downloading a copy manually. Just save it into your home folder, create a shortcut and run it like that. 

As for the connection problems, have you tried enabling DMZ?. does your computer (not the internet) ahve a static ip?

I will try a new install from vuze.com.
Yes I have turned DMZ on, and how do I setup a static ip on my puter in Ubuntu?

---

### Post by SoftwareExplorer on 2009-06-15
> **drdave69 said:**
> I will try a new install from vuze.com.
Yes I have turned DMZ on, and how do I setup a static ip on my puter in Ubuntu?

Right click on network manager -> Edit connections.

Go to the wired, or wireless if that applies, tab, select it and go edit. Click on the IP v 4 settings tab and select manual. Click add. Put in the IP you want your computer to have, netmask (usually 255.255.255.0), and your router's address. (usually 192.168.0.1)

---

### Post by sandyd on 2009-06-15
> **drdave69 said:**
> I will try a new install from vuze.com.
Yes I have turned DMZ on, and how do I setup a static ip on my puter in Ubuntu?

set it up through the router. it should be under something like DHCP. 
YOu have to setup Static ip, becasue the DMZ only allows you to point towards one IP address. THe same goes for port forewarding.

and it seems that the caps and shift keys are broken on my keyboard. Have to stab them really hard to get something outta them...
time for a replacement.

---

### Post by drdave69 on 2009-06-15
> **SoftwareExplorer said:**
> Right click on network manager -> Edit connections.

Go to the wired, or wireless if that applies, tab, select it and go edit. Click on the IP v 4 settings tab and select manual. Click add. Put in the IP you want your computer to have, netmask (usually 255.255.255.0), and your router's address. (usually 192.168.0.1)

Sorry for such a nube question, I should know this, I know what to put in the address slot, but what do I put in the "netmask" & "gateway" slots?

---

### Post by SoftwareExplorer on 2009-06-15
I nearly forgot--you also have to set a DNS server, or the connection usually won't work. You can find it out when you have a automatic connection if you right click on the network icon, and go to Connection Information. You should write the DNS server(s) down and then enter them when you set up a static IP.

---

### Post by sandyd on 2009-06-15
> **SoftwareExplorer said:**
> I nearly forgot--you also have to set a DNS server, or the connection usually won't work. You can find it out when you have a automatic connection if you right click on the network icon, and go to Connection Information. You should write the DNS server(s) down and then enter them when you set up a static IP.
i suggest using the OpenDNS's dns servers, which are
[B] 				208.67.222.222
				208.67.220.220 			[/B]

 		 		 		 			the default gateway should be the address of the router.
Its still better to set the static ip through the router tho.

---

### Post by SoftwareExplorer on 2009-06-15
> **carlee said:**
> i suggest using the OpenDNS's dns servers, which are
[B] 				208.67.222.222
				208.67.220.220 			[/B]
 
Cool. I learn something new every day.
 		 		 		 			
> **carlee said:**
> Its still better ton set the static ip through the router tho.

True, I tend to forget that because my router can't.

---

### Post by drdave69 on 2009-06-16
Sorry I was gone so long, but when I set up a static ip on my puter, it would not allow me to get online for a while. Finally figured it out, had to use a DNS server. But I now have a static ip address :)
Still working on installing a new copy of vuze, will keep informed.

---

### Post by SoftwareExplorer on 2009-06-17
Sorry about that. It was after I told you how to change it that I realized I forgot and started to wonder if that was the case.

---

