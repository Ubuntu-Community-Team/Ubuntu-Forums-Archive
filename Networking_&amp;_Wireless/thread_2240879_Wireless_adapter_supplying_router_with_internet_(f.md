---
title: "Wireless adapter supplying router with internet (four PC's)"
date: 2014-08-22
forum: Networking &amp; Wireless
---

### Post by billy11 on 2014-08-22
Okay im here to ask some wierd q's and if a modderator has a better title then please change it, i have no idea what im trying to ask :/ 

HARDWARE:
 i have a new HP PAVILION windows 8.1 with a 8188 wifi card (only some softwares support it ) I have a external hdd running Ubuntu 12.04 (the OS i mainly use)

A dell dimension 4600 that is currently running windows xp ( it can run anything that you smart people suggest it too inorder to make my situation come true )

A COMPAQ presario that is dualbooting windows millenium (i believe ) and for sure Xubuntu because the computer is super slow.

wireless adapter for the old computers to connect wirelessly (yes they do work with it hahaha)

Wireless router (to do whatever with)

The other computers are macs and not that handy...

--------------------------------------------------------------------------------------------------------------------

I can connect to this network on my laptop windows pavillion, but the network is too weak for the other computers to connect by themselves. Xubuntu (compaq presario equiped with USB WIFI adapter) can view the network, but keeps asking for the password and i know its correct. (Windows xp can view it also but since its WPA2 it says it can't connect or communicate or something (or its wep, i forget)  Now, what for the questions to start...

1. (MAIN OBJECTIVE) Can I connect to the network in Xubuntu and create a miniature 'connectify' like network using the adapter? (connectify is a windows application and i dont know if it is compatible with linux / debian )

2. Can I somehow update the firmware and software to communicate with wep or wpa2? (the old compaq and Xubuntu with the N150 adapter)

3. If these above options fail, I can still connect to the network in Ubuntu 12.04. Is Ubuntu capable broadcasting its internet like windows is with hotspot apps like connectify?

4. Is there a linux distro that is simpler to do this on?

5. Can i use the wireless router by plugging it into the LAN port on my compaq presario or Pavilion? I understand that the wireless router is looking for a modem and that the lan port is looking for incoming internet so it propably wont work. 

--------------------------------------------------------------------------------------------------------------------

Any help would be astounding! thank you for your patience with a noob :)

---

### Post by weatherman2 on 2014-08-22
Simplify your life: get a wireless ethernet bridge.  This device connects wirelessly to a WiFi network but it has wired ethernet ports on it, so you can connect up wired devices to it.

You can buy a wireless ethernet bridge - or you can make one of these yourself with an old wireless router that supports DD-WRT or TomatoUSB firmware (which is like putting Linux on your router).  A lot of older Linksys "N" routers like the E2000, WRT320N, etc. work really well with TomatoUSB and may be purchased cheaply in some cases.  An old WRT54G "G" router would be slow but would also work.

A downside of using a wireless ethernet bridge: it can't support a lot of bandwidth if all devices are using it at the same time or all trying to download/upload at the same time.  But, you'd have the same issue if you tried to make your suggestion work by sharing one computer's WiFi.

---

### Post by billy11 on 2014-08-22
Okay the model is a D-link WBR-1310, where would i look to try installing this mode? and by the way, THANK YOU SO MUCH FOR THE QUICK REPLY

---

### Post by weatherman2 on 2014-08-22
I'm not sure that D-Link router is supported by DD-WRT or Tomato.  (A quick google shows it is probably not supported.)  Unfortunately, these router firmwares only work on a limited number of routers.

Even if you could turn that router into an ethernet bridge, it would no longer function as a regular router.  In other words, you need a router dedicated solely to being a wireless ethernet bridge.  You'd need another router as your "regular router" like you presumably have right now.

---

