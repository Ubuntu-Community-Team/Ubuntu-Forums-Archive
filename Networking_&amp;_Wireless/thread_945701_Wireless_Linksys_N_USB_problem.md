---
title: "Wireless Linksys N USB problem"
date: 2008-10-12
forum: Networking &amp; Wireless
---

### Post by gorkos on 2008-10-12
I have dual boot system, Ubuntu and XP, with wireless USB Linksys N adapter (WU..300N). On XP it works quite fine, without problem, but on Ubuntu, after I have tried all I have found here on forum and Ubuntu site, I always have same kind of problem. 
"sudo depmod -a" and "sudo modprobe ndiswrapper" do all they need, but when I want to connect to my network using WEP 128 encryption,  and for example using KNetworkManager (I tried a few possible scenarios, with different network managers), connection succeed until some 28% and than block. It seems like software (ndiswrapper or some communication software) issue some command which block a wireless card, because when I try after that to login in XP, wireless card does not work without hard reset of card (plug out of power and return network card). And after that it again works in XP.  Is it possible anywhere to see in Ubuntu **log file of communication initialization process**? Does anyone can suggest something? Every command I have found in forum works ok, with good result (lsusb and all others), but I can not make a connection to network. When I tried some other possible scenario, one of result is that when making connection, link diode on card blink non stop (on XP it just light non stop, not blink), and after than I can not event restart the system, I must use CTRL ALT SYS B key combination to reset Ubuntu.

---

