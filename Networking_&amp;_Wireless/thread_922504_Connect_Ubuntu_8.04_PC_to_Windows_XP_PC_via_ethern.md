---
title: "Connect Ubuntu 8.04 PC to Windows XP PC via ethernet NIC"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by TinusB on 2008-09-17
Hi, I cannot find any solution on the internet for my problem.

I have a PC with Ubuntu Studio 8.04 and another one with Windows XP. The XP PC are connected to the internet. I want to access the internet from the Ubuntu PC via ethernet.

I have the two PCs connected now (with the right cable), but I don't know how to set things up. In Windows the network icon on the taskbar has an exclamation and says: Limited or no connectivity. The Linux PC don't see anything.

Please help!

---

### Post by vorgusa on 2008-09-17
You will need to set a static IP address on both the windows and ubuntu computers.  I have never tried this before, but I believe that all you need to do is bridge the two network interfaces on the windows machine.  Is there a reason why you want to do this instead of connecting the Ubuntu machine to a router or switch?

---

### Post by TinusB on 2008-09-17
Thankyou for the reply!
Where do I set the static IP address?
I am doing this, because I don't have a router or a switch and we have no computer shops in a radius of 160km where such items are sold. I also want only this two computers to be connected.

---

### Post by vorgusa on 2008-09-17
if you do not have a router this might not work properly.  You will need a NAT, which a router would provide so that you can have multiple computers on one internet connection.  I am not sure the best way to set this up on a windows computer or Ubuntu computer for that matter.  I read an interesting article the other day about a program for windows XP that would do software routing 
[http://www.smallnetbuilder.com/content/view/30576/52/](http://www.smallnetbuilder.com/content/view/30576/52/)

you could try that out, it will do a lot more then what you need and is a little complicated though.. if you can go online and buy a cheap router they will deliver it for cheaper the going to best buy.

---

### Post by rbc on 2008-09-17
For Ubuntu, left click on the network applet (top right of screen). Select Manual Configuration. Next click the unlock button (you will need your password). From there uncheck Enable Roaming, then set your static IP. Do not do any of that yet though. Here's what you will need to do on the Windows side:
[http://support.microsoft.com/kb/306126](http://support.microsoft.com/kb/306126)
Also, do some Googling about Internet Connection Sharing. By the way, how are you connecting to the internet now?

---

### Post by TinusB on 2008-09-18
> if you do not have a router this might not work properly. You will need a NAT, which a router would provide so that you can have multiple computers on one internet connection. I am not sure the best way to set this up on a windows computer or Ubuntu computer for that matter. I read an interesting article the other day about a program for windows XP that would do software routing
[http://www.smallnetbuilder.com/content/view/30576/52/](http://www.smallnetbuilder.com/content/view/30576/52/)

A while ago I was told that the setup I have, should work perfect.
I really don't know if my Windows PC (P3, 500MHz, 265MB RAM) will be able to handle another program at startup - it is allready very slow.

A few months ago me and my brother were connected via bluetooth (we both have XP) and he was able to browse the internet through my computer's internet connection.

> For Ubuntu, left click on the network applet (top right of screen). Select Manual Configuration. Next click the unlock button (you will need your password). From there uncheck Enable Roaming, then set your static IP. Do not do any of that yet though. Here's what you will need to do on the Windows side:
[http://support.microsoft.com/kb/306126](http://support.microsoft.com/kb/306126)
Also, do some Googling about Internet Connection Sharing. By the way, how are you connecting to the internet now? 

I am connecting to the internet by Wireless LAN (an EnGenius EUB-362 EXT USB adaptor that does not work in Ubuntu) and it is called Wireless Network Connection in Network Connections.

I enabled ICS for the wireless connection. Then I right-clicked on the Local Area Connection 2 then selected Properties>Internet Protocol(TCP/IP)>Properties>Use the following IP address and typed 192.186.0.2 and 255.255.255.0. The first Local Area Connection (it was with bluetooth as described above) had  192.186.0.1, but I do not use it now.

So now the exclamation disappeared (the icon as well) and in Network Connections it says connected.

In Ubuntu (I could not follow the steps exactly as you said) I went to System>Administration>Network>Wired Connection>Properties>Enable this connection. Then I chose Static IP address and typed 192.186.0.3 and 255.255.255.0 jumped up in the second line.

But still I cannot browse the internet from Ubuntu. When I click Places>Network, I can see Windows Network and when I click this I see the other computer (I think) but cannot access the shared files.

So I went to Setup a home or small office network in Windows and chose the wireless connection to be the connection to the internet and Local Area Connection and Local Area Connection 2 (bridged by the wizard to be Network Bridge) to be the computer that uses this computer's internet connection. But still no internet in Ubuntu.

I'm afraid that I am going to mess things up if I try some of the options I don't know much about.

I'll appreciate any help with this.
Thanks a lot for replying.

---

### Post by TinusB on 2008-09-18
I found this page:
[http://achinghead.com/archive/57/sharing-windows-internet-connection-linux/](http://achinghead.com/archive/57/sharing-windows-internet-connection-linux/)

I went to System>Administration>Networking and clicked on Properties for the wired connection and set the connection to DHCP.
Now I have internet access in Ubuntu!

---

### Post by vorgusa on 2008-09-18
> In Ubuntu (I could not follow the steps exactly as you said) I went to System>Administration>Network>Wired Connection>Properties>Enable this connection. Then I chose Static IP address and typed 192.186.0.3 and 255.255.255.0 jumped up in the second line.


Did you assign the ubuntu computer a Gateway?  If I understand the setup it should be the windows XP machine (if it is sharing your connection).  

If you are connecting through a wireless Lan and bridging your connection you should select the same gateway as the Windows Computer.

Try both if one does not work

---

