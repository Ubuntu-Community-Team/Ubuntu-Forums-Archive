---
title: "Connecting Two Wireless Routers"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by bond17_007 on 2008-06-07
Hi All, 
  I really need help with this. 
Here is the scenario. 

I have a DLINK router D1310 that is connected to the cable modem. This is located at the family room on the main floor. 

On the 2nd floor I have a desktop that does not have a wireless card. But I do have a Belkin F5D7230-4 router (this supports Bridge and AP mode both). 

There is no wire running through main floor to 2nd floor so I am trying to bridge the routers wirelessly. 
I googled but couldnt find a solution that worked ;(. 
Please let me know if you guys have done something similar to do.. 

to clarify here is an  image


Main Floor:
MODEM  ----> DLINK 1310   \ /  (Wireless)
                          |||

2nd Floor:

BELKIN (F5D7230-4 version 2000)  \ /  (Wireless)  ---> Desktop
                                 |||

---

### Post by cdtech on 2008-06-07
Just give your second router it's own static ip address (something other than 192.168.1.1) I use 192.168.1.10 as my wireless, and use the first as your gateway (192.168.1.1) for the second router.

Is this what you mean?

---

### Post by blastus on 2008-06-07
You want to set the wireless mode of the second router to "client bridge", turn off DHCP, enter the PSK of the primary router's wireless network, make sure the router's IP address is on the same subnet as the primary router, then join the primary router's wireless network.

I don't know how Belkin bridges work, but it's fairly easy to setup a wireless bridge with a WRT54GL running DD-WRT v24 firmware. What's really nice about it is that you don't have to worry about setting up stupid flaky wireless drivers ever again. Just plug in whatever device you want into the bridge and it's instantly on the network! :)

---

### Post by bond17_007 on 2008-06-08
Hi Blastus,
   
   Here is the problem I am running into
The DLINK router does not seem to have a bridge mode or AP mode, hence I chose this one to be connected directly to the modem. 
The IP address it has is 192.168.0.1, with subnet 255.255.255.0
It will give out IPS from 192.168.0.2-254

Belkin router on the otherhand has IP 192.168.2.1 with subnet 255.255.255.0

So, I did the following
1. Configured the DLINK router wiht a SSID say "mySSID" with WPA-"password"
2. I changed the IP address for DLINK to say 192.168.2.1, 255.255.255.0 (the reason I did this is becuase i was running into problems with belkin when changing the IP)

3. Wireless set up successfully in channel 1. 

===
4. with Belkin, I reset the router with factory defaults. 
5. Changed the settings to have IP 192.168.2.100 with 255.255.255.0. 
6. Disabled the DHCP. 
7. Configured the SSID to "mySSID" with WPA - "password" (to have both the routers same ssid and pwd)
8. Restarted the router. 

9. STill the Belkin was not getting connected to DLINK ie.. i was not able to connect to the internet via Belkin router. 

You mentioneed DD-WRT. My question is whats the benefit of having that?
(i am very new to this networking stuff :S). Both the routers have their own working firmware, what difference would it make if i put DD-WRT. 

(i did find dd-wrt for my belkin however not for dlink :( so i don tknow if thats goign to solve my probelm)

Thanks again for all your help, appreciate it

---

### Post by kevdog on 2008-06-08
If have ddwrt using it on my linksys wrt54gl in combo with a dlink router.  I use the repeater bridge mode, however I have used client bridge also.  The repeater bridge also additional clients on the second router (linksys) (both wired and wireless) access through the first router (dlink) and then the internet.  I have wired computers connected to the dlink, and 3 wireless computers using the linksys router.

Ive never used belkin before, however my advice at this point would be to get things set up AND THEN add wpa on top of the setup.  Using security models prior to having a working setup confuses things.  

The Belkin for sure has a client bridge or repeater bridge mode?  (Again the server router does not need special software).  Here is a screenshot of my options for you to take a look:

---

### Post by blastus on 2008-06-08
[QUOTE=bond17_007]Hi Blastus,
   
Here is the problem I am running into
The DLINK router does not seem to have a bridge mode or AP mode, hence I chose this one to be connected directly to the modem. 
The IP address it has is 192.168.0.1, with subnet 255.255.255.0
It will give out IPS from 192.168.0.2-254

Belkin router on the otherhand has IP 192.168.2.1 with subnet 255.255.255.0

So, I did the following
1. Configured the DLINK router wiht a SSID say "mySSID" with WPA-"password"
2. I changed the IP address for DLINK to say 192.168.2.1, 255.255.255.0 (the reason I did this is becuase i was running into problems with belkin when changing the IP)

3. Wireless set up successfully in channel 1.[/QUOTE]

You should set the IP address of the DLink router to say 192.168.0.1 and the Belkin router to 192.168.0.2. The IP address of the routers have to be different but they have to be on the same subnet. My primary router is set to 192.168.0.1 and secondary router 192.168.0.2. I had issues getting an IP address from a device connected to the secondary router until I set the IP address of the secondary router--even though the secondary router had successfully joined the wireless network of the primary router.

[QUOTE=bond17_007]
===
4. with Belkin, I reset the router with factory defaults. 
5. Changed the settings to have IP 192.168.2.100 with 255.255.255.0. 
6. Disabled the DHCP. 
7. Configured the SSID to "mySSID" with WPA - "password" (to have both the routers same ssid and pwd)
8. Restarted the router. 

9. STill the Belkin was not getting connected to DLINK ie.. i was not able to connect to the internet via Belkin router.[/QUOTE]

You have to set the wireless mode of the secondary router to "client bridge" or something like that. The bridged router has to "join" the wireless network of the primary router. I don't know how this is done with a Belkin router, but with a WRT56GL running DD-WRT v24 you select Status->Wireless->Site Survey and then select the wireless network you want to join. It should tell if you if it successfully joined the wireless network. 

[QUOTE=bond17_007]
You mentioneed DD-WRT. My question is whats the benefit of having that?
(i am very new to this networking stuff :S). Both the routers have their own working firmware, what difference would it make if i put DD-WRT. 

(i did find dd-wrt for my belkin however not for dlink :( so i don tknow if thats goign to solve my probelm)

Thanks again for all your help, appreciate it[/QUOTE]

DD-WRT v24 was just released May 24, 2008. It has a lot of features apparently only available in very expensive routers. It's open source and supposed to be secure, reliable and robust. I think I might get another WRT54GL and put DD-WRT v24 on it and use that as my primary router and get a 1000mps switch. The only thing I don't like about the WRT54GL is that the switch is only 100mps.

Edit: The other thing you have to do is turn off the firewall on the bridge router. There are probably ways to configure it but I just turned it off. The firewall on the primary router stays on.

---

### Post by bond17_007 on 2008-06-09
Thank you guys for the prompt response. 

The reason I change the IP pool in primary router (DLINK) to 192.168.2.1-254 is because, the Belkin router would hang if I changed it to "192.168.0.2" etc.. so instead i change the DLINK pool so i can just change the belkin one like "192.168.2.2" (which worked). 

Today I will try to put DDWRT on my belkin hopefully that would resolve it. 

I also tried the tech support of belkin and they were telling me that  for bridging or AP mode I have to have both the routers support that mode (not sure if its entirely true). 

The DLINK router I have is DLINK 1310; which does not have much options for Bridge mode or AP mode. but my Belkin one does. 
Also, I wasnt able to find DDWRT that is compatible for DLINK. 

Do you think just chaning the firmware on belkin would resolve it?

I will post more tonight as I can get some screen shots to clarify :)

---

### Post by bond17_007 on 2008-06-09
I was reading more on DD-WRT but this is what i got from their website:
  "Belkin F5D7230-4 v2000: This version has a different flash chip than the other versions, and it will enter a reboot loop if a special SF build is not used. ....

**This version also has a different switch chip so only wireless will work after flashing**. **_Wired can be enabled, but the ports can only be set to either WAN or LAN. If you only have wireless clients or want to use it as an AP or Client Bridge; this is not a problem. However, you are not able to use this device as a wired router with wired clients._** "

Does this mean it wont work for me?
coz I will be connecting my Desktop through Ethernet port to Belkin which should be connected to internet via. wireless connection with DLINK.

---

### Post by bond17_007 on 2008-06-09
I think I bricked my belkin router while trying to set DD_WRT. 
After trying for hours, finally i got the router auto loop end. 
However, router is unable to issue any IP address.. it gets stuck trying to acquire IP address. 
if i connect it to internet and then to a compter, it acts like a hub instead :( 

Any reccomendations?

> **blastus said:**
> You should set the IP address of the DLink router to say 192.168.0.1 and the Belkin router to 192.168.0.2. The IP address of the routers have to be different but they have to be on the same subnet. My primary router is set to 192.168.0.1 and secondary router 192.168.0.2. I had issues getting an IP address from a device connected to the secondary router until I set the IP address of the secondary router--even though the secondary router had successfully joined the wireless network of the primary router.



You have to set the wireless mode of the secondary router to "client bridge" or something like that. The bridged router has to "join" the wireless network of the primary router. I don't know how this is done with a Belkin router, but with a WRT56GL running DD-WRT v24 you select Status->Wireless->Site Survey and then select the wireless network you want to join. It should tell if you if it successfully joined the wireless network. 



DD-WRT v24 was just released May 24, 2008. It has a lot of features apparently only available in very expensive routers. It's open source and supposed to be secure, reliable and robust. I think I might get another WRT54GL and put DD-WRT v24 on it and use that as my primary router and get a 1000mps switch. The only thing I don't like about the WRT54GL is that the switch is only 100mps.

Edit: The other thing you have to do is turn off the firewall on the bridge router. There are probably ways to configure it but I just turned it off. The firewall on the primary router stays on.

---

