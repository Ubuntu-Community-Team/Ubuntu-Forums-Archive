---
title: "Router connection"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by andreiiar on 2010-06-19
Hello,

I just installed ubuntu as first time linux user. I have some computer knowledge but no linux experience. 

The problem that I have is that I can't connect to the internet. I have a router hooked up to a aDSL modem. The router is DHCP configured but in ubuntu when I select auto eth1 it tries to connect but nothing happens ( I get 'disconnected' after a while ).   
I've tried to assign a static ip and the network manager shows as connected, I can even ping my router but I can't connect to it's network interface in firefox and internet is not working.

Strangely enough, I can't seem to access my admin panel of the router from my other 2 computers both running XP.

---

### Post by nhasian on 2010-06-19
you have your aDSL modem connected to the WAN or Internet plug on the router correct?  your computer should be connected to one of the regular LAN plugs 1-4 if you have a 4 port router.  assuming DHCP is enabled in your router, then your ubuntu will automatically get an ip address from the router.

---

### Post by andreiiar on 2010-06-19
Exactly nhasian. But it does not. The pc I use has dual boot and dhcp assigns ip in windows just fine. Not in ubuntu tho.

---

### Post by mapes12 on 2010-06-19
> The problem that I have is that I can't connect to the internet. I have a router hooked up to a aDSL modem. The router is DHCP configured but in ubuntu when I select auto eth1 it tries to connect but nothing happens ( I get 'disconnected' after a while ).
I've tried to assign a static ip and the network manager shows as connected, I can even ping my router but I can't connect to it's network interface in firefox and internet is not working.

Strangely enough, I can't seem to access my admin panel of the router from my other 2 computers both running XP.

I was happily running 9.04 and today decided to upgrade to 10.04. After the upgrade I had the exact same problem as the OP i.e no internet connection (even the XP machine) and couldn't access the router control panel. I called my ISP who confirmed by broadband line was OK. I did the reinstall again and again using other regressive Ubu versions. Same problem.

Did some head scratching than decided to replace the router with a spare new one I had lying around doing nothing. Hey Presto! Everything worked. I have no idea what caused all this but my original router appears to have been fried after the 10.04 upgrade. It's an old router and I can only guess that the large amount of data it was being asked to handle for upgrading and installing all my package applications made it fall over and die.

Not sure this will help but just thought my experience today may invoke some thoughts to help you out.

Best wishes.

Mark

---

### Post by andreiiar on 2010-06-19
Hi, i'm glad you got yours to work, mine is still off. After searching a lot on the forums and goggle I found nothing of help apart of learning a few commands and how to work my way around vi text editor - typing commands is fun by the way. 

I managed to reset network and I get a 'no working leases'. Assigning a static still doesn't work. 

note Router assigns ips in windows just fine

---

### Post by dixonstalbert on 2010-06-19
hi andreiiar

I am wondering why your system is bypassing eth0 and trying to connect on eth1

try typing ifconfig in terminal in Ubuntu and confirm eth1 is the right interface.

Also try ipconfig /all at cmd prompt on XP machine that can connect to internet. see what address is default gateway (the router) then use this address in web browser to see if you can connect to routers interface webpage- webpage might have info on network status of ubuntu machine

hope this helps
dixonstalbert

---

### Post by dixonstalbert on 2010-06-19
another thing you could try would be to try live cd of ubuntu  on each of your computers and see if it can connect to internet. maybe you have an unusual network card in the computer you are having trouble with and it is a problem with linux driver- I had lots of trouble with a broadcomm NIC in my dell laptop

---

### Post by andreiiar on 2010-06-20
Eth1 was my second nic. After inspecting the mac I identified the eth0 as the 'live' network card but it didn't show as available. Now I phisicaly  removed the second card from the pc. 

I'm still in the tree but now network manager doesen't show up at all. Confirming I tried the working DNS from windows.

---

### Post by andreiiar on 2010-06-20
First post from inside linux. I got it to work after I installed ethtools and set the speed to 10 full duplex mode ( rememberd I had the same problem in windows I don't know why it doesen't work on auto or 100 ). 


PS. How do I edit the prefix to SOLVED?

---

### Post by The Cog on 2010-06-20
Congratulations. I wouldn't have thought of that.

At the top of the page on the right is a red title "Thread Tools" - mark solved is under there, I think.

Welcome to Linux and Ubuntu.

---

