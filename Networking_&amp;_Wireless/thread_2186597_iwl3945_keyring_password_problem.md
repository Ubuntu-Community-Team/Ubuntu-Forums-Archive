---
title: "iwl3945 keyring password problem"
date: 2013-11-08
forum: Networking &amp; Wireless
---

### Post by sinisaperovic on 2013-11-08
Hi.

I'm having Toshiba laptop with 3945 intel wireless and while browsing the network connection just disappeared. Another thing, the network-manager-gnome is nowhere to be found on the system :o so there was no panel icon neither.

After re installing network-manager-gnome the hell begun - there is no way to get keyring password to access wireless network.

1. I set my wireless network available to all users and back - no luck
2. I deleted files in .gnome2/keyring/ - no luck
3. I changed my user password (it was too short which is allowed in installation but no later on) - no luck
4. I reinstalled network manager and keyring manager - no luck
5. I found that somewhere there is proposed solution to leave the password blank - I cannot do that, my button is disabled if password is blank or less than 8 characters long
6. I tried all variations and combination of 1 - 5 that can be fund online - no luck

How to get by keyring manager to be able to access my wireless network? There is nothing wrong with my wireless nor ethernet card since it can connect (wired) and detect all access points (wireless) so it does work on the hardware level. It seems that all I'm having trouble with is keyring manager and it's password to access wireless connections. Maybe it was another piece of software gone missing together with network-manager-gnome? I don't know...

This has never happened to me and I'm using Ubunutu since 5.10, exclusively since 7.04. Also have in mind that this occurred in the middle of my browsing, I did not meddle with my laptop nor was I installing / upgrading anything. 

I hope that someone can help me since I'm loosing my mind here :-(

Cheers,

Sinisa Perovic

---

### Post by steeldriver on 2013-11-08
Hello and welcome to the forums

What are your symptoms exactly? The Intel cards have known issues with wireless-n mode that can cause them to make repeated requests for the *wireless* password - what makes you think it's a keyring issue specifically?

---

