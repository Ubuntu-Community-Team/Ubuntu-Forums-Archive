---
title: "Alternative Network Manager"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by robfranssen on 2008-09-01
Hi,
I installed xubunto 8.04 on an old Compaq-laptop, PII, 166 M RAM. 3 GB HD, using a Linksys WPC54G wireless card.
After spending hours reading posts about wirelass cards, downloading and installing firmware and  the limited capabilities of the Network Manager, i decided to use the DHCP-server on my router to get connected with the wireless card.

Having said that, my network USED to work with fixed IP's and a hidden SSID; my Win-PC's and an iMac had no problem connecting automagically on login.

So my question is: 
Is there an alternative Network Manager available for xubuntu to do the same job as his pals under  Windows- and Leopard? (auto-connect upon login to hidden network with fixed IP)

I already tried WICD, but it doesn't work properly under xubuntu (hangs with blanc screen)
I hope somebody can give me a hint without the need to spend more hours under the hood (in Terminal).

PS: I only started using Linux a few weeks ago. So, a newbee without an intention to become a Linux-wiz. The Compaq should just do its work as in his previous life under Win98SE; wordprocessing, spreadsheets, e-mail and similar basic tasks...

---

### Post by modmadmike on 2008-09-01
Have you tried putting it in Roaming mode, this lets it act like windows were there is an applet int the tray that lets you conned to a wireless (wired also) network and shows the signal Plus this lets you use all the nifty features.

---

### Post by caljohnsmith on 2008-09-01
> **robfranssen said:**
> 
Having said that, my network USED to work with fixed IP's and a hidden SSID; my Win-PC's and an iMac had no problem connecting automagically on login.

So my question is: 
Is there an alternative Network Manager available for xubuntu to do the same job as his pals under  Windows- and Leopard? (auto-connect upon login to hidden network with fixed IP)
I use Network Manager with my wireless card, and I am able to connect just fine to a network with no broadcast SSID using a static IP. I just go into Network Manager, click on the wireless interface, hit "properties", and then type in the SSID where I might normally use the pull-down menu to pick one. Then under "connection settings" I set up a static IP with the correct gateway, and everything works fine. 

Have you tried something similar or do you still have problems when doing the above steps?

---

### Post by robfranssen on 2008-09-01
I read your post and tought: 'what the heck, give it another try'.
So i started with a working wireless connection. Then i started Network Manager, unlocked it with my password and clicked on the wireless card and 'Properties'

Next, i disabeled roaming, entered the SSID, WPA personal (as before), Network password, Static IP, same IP as before, subnet mask and gateway.
After clicking OK, my PC and/or ubuntu - in their uther wisdom - did some misterious things, but the final result is that i don't have a working connection anymore. Can't even ping my router.

Are you shure you are talking about the same Network Manager? I use the one included in the xubuntu 8.04 distro. (for obvious reasons this post was send from my iMac; great machine ;-)

---

### Post by caljohnsmith on 2008-09-01
> **robfranssen said:**
> I read your post and tought: 'what the heck, give it another try'.
So i started with a working wireless connection. Then i started Network Manager, unlocked it with my password and clicked on the wireless card and 'Properties'

Next, i disabeled roaming, entered the SSID, WPA personal (as before), Network password, Static IP, same IP as before, subnet mask and gateway.
After clicking OK, my PC and/or ubuntu - in their uther wisdom - did some misterious things, but the final result is that i don't have a working connection anymore. Can't even ping my router.

Are you shure you are talking about the same Network Manager? I use the one included in the xubuntu 8.04 distro. (for obvious reasons this post was send from my iMac; great machine ;-)
You're right, my mistake; I missed the part that you are using Xubuntu. It sounds suspiciously like the XFCE network manager is quite similar to Gnome's network manager though. If you do:
```
xprop | grep WM_CLASS
```
And click on your open network manager window, what does it return? 

When you say you started with a working wireless connection, how did you configure it if not with your Xubuntu's network manager? Did you do it at the CLI?

---

### Post by robfranssen on 2008-09-01
1. If i run xprop | grep WM_CLASS in Terminal and next on the window 'Network Settings
WM_CLASS(STRING) = "xfce4-panel", "Xfce4-panel"

2. In the previous situation, the Network Manager Icon initially was two screens. After one click, it showed the wireless networks in the area and - after clicling on my own and entering SSID en network-password - connected to my router. This was only possible after i set my router to transmitting SSID and activating the DHCP-server in my router.

3. As soon as i open Network Manager, unlock, open properties of the wireless card and disable "Enable roaming mode' and click on OK (regardless of all other info entered in that window), my wireless connection dies.

4. What is a CLI? Command Line Interface? Same as terminal?

---

### Post by caljohnsmith on 2008-09-01
> **robfranssen said:**
> 1. If i run xprop | grep WM_CLASS in Terminal and next on the window 'Network Settings
WM_CLASS(STRING) = "xfce4-panel", "Xfce4-panel"

2. In the previous situation, the Network Manager Icon initially was two screens. After one click, it showed the wireless networks in the area and - after clicling on my own and entering SSID en network-password - connected to my router. This was only possible after i set my router to transmitting SSID and activating the DHCP-server in my router.

3. As soon as i open Network Manager, unlock, open properties of the wireless card and disable "Enable roaming mode' and click on OK (regardless of all other info entered in that window), my wireless connection dies.

4. What is a CLI? Command Line Interface? Same as terminal?
Yes, CLI is command line interface or the terminal. :) So I don't understand--why can't you just do what you originally did in your network manager to at least get connected again? And when you go through setting up your connection manually, what static IP, subnet mask and gateway IP are you using? On one of your working machines (Win PCs and iMac) can you get the gateway IP to confirm? In Win XP, if you right-click the wireless icon, select "properties", and then there is another tab you can click on (can't remember its name), it should tell you your gateway IP (which is your router). Or if you go to Start > Run > type "cmd" > type "ipconfig /all" I think you can get the same info.

---

### Post by robfranssen on 2008-09-01
In the mean time i did; getting connected again (by Enabling roaming mode again)
I the past (when running Win98SE) i used:
IP 192.168.2.210
Submask 255.255.255.0
Gateway 192.168 2.1 (my router, Siemens Gigaset SX551 WLAN dsl)
DNS 192.168.2.1 and 195.121.1.34 (the DNS-server of my Internet Access Provider)

In the actual situation the laptop gets it IP from the router (DHCP) and there is no need to provide info on Gateway, Subnet Mask and DNS (could be that this info is obtainded from /etc/network/interfaces, put there by Network Manager when configuring my Ethernet-card; have no clue)

My other PC's are at 192.168.2.220 and 230, my iMac is at 192.168.2.240 and they are/were one big happy family :-) , including file sharing and the use of VNC.

As i said, the old Laptop is working again as well, but only because of the fact that broadcasting SSID and DHCP are enabled on my router, a situation i don't like and which was not needed in the past when this same laptop - in its previous life - was running Win98SE.

The Nework Manager i got from Xubuntu doesn't seem capable to get me what i wanted to start with: auto-connect upon login to hidden network with fixed IP and i doubt whether Ubuntu can be run on this old horse with only 166 MB RAM and 3 GB HD

---

