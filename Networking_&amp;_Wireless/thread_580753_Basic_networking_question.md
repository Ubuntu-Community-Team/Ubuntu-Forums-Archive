---
title: "Basic networking question"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by bayonetblaha on 2007-10-19
My friends and I occasionally play server/client architecture multiplayer games together, but we must be doing it wrong. Mostly freeciv and wolfenstein.

 Every time we play, the only way we know how to do it is to find a place where we can all have different IP addresses on internet connections, and everyone connects to the server through the internet (such as a computer lab).

 I have a wireless router connected to a cable modem at my house, but we can't seem to get it working with the usual ip-connection method if we all have the same IP address. Do I need to buy a switch or a hub or what? How do people normally play multiplayer games without a seperate internet connection for each computer?

---

### Post by WedgeHG on 2007-10-19
You shouldn't all have the same IP address. The purpose of an IP address is to uniquely identify each computer on the network. If more than one computer has the same IP address it is sure to cause problems.

Are you all connecting through the wireless router? If so then it probably assigns IP addresses through DHCP by default. If not, you will need to manually assign addresses to each computer. Make sure that they are all in the same subnet. A typicalr choice is addresses like 192.168.1.1, 192.168.1.2, 192.168.1.3, and so on with the subnet mask of 255.255.255.0 for all of them. Just make sure that all of the computers have different IP addresses.

---

### Post by bayonetblaha on 2007-10-19
Maybe there are multiple types of IP adresses, I think I heard something about that, and it's kind of the explanation I'm hoping for. All I know is when we're all connected through the router and we go to whatismyip.com or check the "inet IP" in ifconfig, we have the same IP there. 

How do I go about manually assigning IP addresses? Keep in mind that I am dealing with Windows, OS X and Ubuntu here... is this something I will have to figure out how to do on each different OS, or something I do in the router's controls?

---

### Post by WedgeHG on 2007-10-19
When you go to a website like whatsmyip.com it shows you the IP address of your router. Your computer actually has a different IP address but your router is running something called NAT so the outside world (the Internet) thinks that it is your address. It will think that every computer connected to your router has that IP address.

Given that, it is likely that your computer and the computers of your friends are already set to automatically get IP addresses from your router (DHCP). This is typically the default. 

To see what the IP address is on your Ubuntu computer is, open a terminal (under Applications,  accessories, termina) and type "ifconfig". Your IP address will be listed after "inet addr:". It might show you several interfaces like eth0, eth1, ath0 and so on. Most likely only one of those will have an IP address so it should be easy to spot. And it probably starts with 192.168.1. 

For a Windows computer, click Start, Run, then type "cmd" and press enter. This will give you a command line. Then type "ipconfig" and press enter.

I have no clue about the Mac.

Then when connecting to your game server (I'm assuming it is running on one of your computers unless I'm completely misunderstanding your situation) just type the address for that computer when you are connecting with the game.

---

### Post by bayonetblaha on 2007-10-19
Aha! I believe I understand now. I won't be able to try it out until the next time we decide to try and play some games- hopefully this instruction will do the trick. Thanks for all your help, you make Linux work.

Nelson

---

### Post by rfurman24 on 2007-10-19
You should be able to see the Ip on the mac in "about this mac"

---

