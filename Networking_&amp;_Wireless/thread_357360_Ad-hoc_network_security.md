---
title: "Ad-hoc network security"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by BeachBum on 2007-02-09
Hello all,

I have a rt61 based wireless card in a workstation that shares internet with other computers.  Until the serialmonkey rt2x00 drivers work reliably (and I can use the card in master mode) I am sharing the net using ad-hoc mode.  I live in the city where at any given time I can see 30+ other networks near me, so there is alot of potential for mischevious activity on my network.  

I understand that I can use mac-filtering and WEP to secure the network, however thats not enough anymore as anyone can gain access to these tools and tutorials for free.  That said, I cannot prevent passive attacks on the network, and cannot control who can connect.  Are there any ways to prevent unwanted access to the networked computers?  For example, if someone spoofs a mac address + sniffs the wep key and is able to surf my net, I want to make sure they cannot acccess files on any other computer.  

Also, does anyone know anything about WPA-NONE?  Its an encryption option offered by the rt61 driver, but documentation from Ralink is scarce, and NetworkManager tells me that the security used in that scenario is unsupported by my hardware (ipw2200)

Thanks for any tips!

---

### Post by spd106 on 2007-02-09
I think the standard response is to tell you to use ssh. That way all data transfers will be encrypted twice. It's the belt and braces approach to network security. There are guides all over the place, but I suggest you start in the wiki [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

Sorry I haven't got a clue about WPA-NONE, never heard of it.

---

### Post by BeachBum on 2007-02-15
Thanks for the reply!

I have SSH setup already for remote access, what I'm looking for is from within my home network, a sort of LAN only VPN I guess.  Here is my network topography

Internet -> wired router -> workstation + internet connection sharing via ad hoc -> laptops

What I'm looking for is another level of encryption between the laptops and workstation thats relatively transparent, and preferably platform independent.  The other issue is that everyone using the workstation internet is a student, so the solution needs to be "roam-able" and simple enough to turn on/ off when we leave my apartment.  I can see how using SSH would do just what I'm asking, but how would I tunnel ALL net traffic through the SSH tunnel?

Thanks for the advice!

---

### Post by spd106 on 2007-02-15
There are several options, you could stick with [ssh]("https://help.ubuntu.com/community/SSH_VPN"), try [openvpn]("https://help.ubuntu.com/community/VPNServer") (uses SSL) or you could find a way to set up a vpn using pptp or ipsec.

Are you using linux only or mixing in some windows PCs as well?

---

### Post by BeachBum on 2007-02-19
Thanks for the links, both look like viable options.  I would like to use one Windows laptop, but my only concern is the modularity of the solutions.  I like the ssh route, especially only needing ifup/down in linux, but how complicated would it be using Windows?  Any suggestions for programs?  

Thanks for the input!

---

