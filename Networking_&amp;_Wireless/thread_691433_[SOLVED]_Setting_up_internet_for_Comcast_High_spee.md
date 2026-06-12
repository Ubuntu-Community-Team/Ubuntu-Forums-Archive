---
title: "[SOLVED] Setting up internet for Comcast High speed"
date: 2008-02-08
forum: Networking &amp; Wireless
---

### Post by surrender10 on 2008-02-08
Hi all,
 This is my first post, so plz pardon my newbie-ness.
OK, i installed ubuntu 7.04 on my old PC using Wubi and i have it on one of my folders on D drive.
Problem: Though with windows xp my internet connection is instantly recognised, i cannot get it to work with ubuntu.
I have searched and tried several things like plugging off modem and restarting etc but i cannot get into internet.

I used wired connection and automatic DHCP. My card is recognised as Realtek RTL 8139. So i guess card is not the problem. 
I have a comcast high speed internet setup here on my PC and 2 laptops. Only the PC is connected via cable connected through wireless router. The two laptops use the wireless router.

The modem (RCA DCM425C) is supplied by comcast which is conected to my Netgear router (WGR614 v6) and I have my PC's ethernet cable connected to this router. 

I should re-iterate, with windows xp on my pc i have no problems connecting to internet. 

BTW, i have a similar setup at work where there is direct access to internet and there my other PC work fine. Its only at home that i have this problem.

Any help please!! I am loving ubuntu except for the internet bit.

---

### Post by surrender10 on 2008-02-13
OK, I found a solution myself.

Since i had a dual boot PC with Windows Professional on one and Ubuntu 7.10 on other adn with ubuntu i did not know how to configure, i read more posts and tried a solution i saw online. So this is what i did:
1) My ubuntu settings were: DHCP ON andwired connection checkbox enabled.
2) I restarted and booted into Windows.
3) Right click on "My Computer"
4) Click on Properties -> Hardware -> Device Manager
5) Expand your network card section and double click on your network card (mine was realtek). 
6) Click on "Wake-on-lan after shutdown" and set it to enabled on the right.

and then i rebooted back to ubuntu and my internet worked.

I dont recall the post i saw this solution, but thanks to him/her anyway.

---

