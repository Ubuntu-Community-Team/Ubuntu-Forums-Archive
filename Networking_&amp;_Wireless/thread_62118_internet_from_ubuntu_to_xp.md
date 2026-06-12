---
title: "internet from ubuntu to xp"
date: 2005-09-03
forum: Networking &amp; Wireless
---

### Post by billyK on 2005-09-03
hello guys !
i read the other posts but couldn't find the solution for my problem.
there we go : i recently installed ubuntu on my pc desktop and on the other machine, a laptop, i have installed Windows XP. How can i share the connection from the ubuntu machine to the XP machine because it isn't working !!!
I don't have a MAC address assigned to my computer or anything else.
Form win xp to win xp it was very simple everything was made automaticly so i didn't assign any ip address to my laptop machine (i left all fields blank).

What's the solution to leave also the ip address fields blank on the laptop (xp machine) ?
Are there any other solutions to share the connection ? I have both installed on ubuntu : eth1 and eth0 . eth1 is the one where the internet cable is plugged in. on my ubuntu machine the internet is working perfect.

please, can anyone explain me step-by-step the setup process ? i'm a newbie with ubuntu.

here are my ip addresses : IP 192.168.1.7 -mask 255.255.255.0 and gateway 192.168.1.101

thank you very very much in advance!

i hope there is someone out there who can help me and explain this to me step by step!

thanx guys!

---

### Post by bjweeks on 2005-09-03
Do you have a router? > I don't have a MAC address assigned to my computer or anything else. Yes, you do all network hardwear have a mac address. So you are trying to connect the two computers togeather? I need more info.

---

### Post by trash on 2005-09-03
If your talking about sharing the internet connection, the get Firestarter from the universe repositories, in the setup it will ask you if you want to share the connection. :)

---

### Post by billyK on 2005-09-03
no i don;t have any router only two network cards installed on the desktop pc . 
the internet cable is pluged in the eth1 netwrok card and from the other network card the eth0 is going out the cable connected to the laptop computer. what anything else you wanna know?

---

### Post by billyK on 2005-09-03
hello i tried with firestarter but there's an error : firewall cannot start the device is not ready eaither eth1 or eth0 . i switched them between and the same result! why?

---

### Post by trash on 2005-09-03
were you connected to the net during the firestarter setup? your pppoe connection should be active for firestarter to detect it.

---

### Post by billyK on 2005-09-03
yes i was connected...i'm connected trough a LAN network not a modem connection.

---

### Post by billyK on 2005-09-03
the exact error is : failed to start the firewall the device eth1 is not ready !  but the internet is working properly... :(

---

### Post by trash on 2005-09-03
no idea, have you tried restarting?

---

### Post by masteryoda on 2005-09-03
[QUOTE=billyK]hello i tried with firestarter but there's an error : firewall cannot start the device is not ready eaither eth1 or eth0 . i switched them between and the same result! why?[/QUOTE]
 I have a similar setup... one pc with win Xp and mine with winxp/kubuntu.
After banging my head with the various internet connection sharing methods....I have realised.... ICS is not the easiest way.... here is what I have done.... (this method works for any OS available in the world.)
1) Assign some IP address to the ethernet card that connects to other pc/network. (eth0 in ur case). say 192.168.0.1 (  i would also suggest to assign IP address to other PC say 192.168.0.1)
2) Install some proxy server on ur pc with internet connection. (Ubuntu in ur case)
3) now on ur other pc configure all ur programs to  use proxy from 192.168.0.1 and port : xxxx

Thats it!!! works perfectly regardless of which OSes ur connecting.

Now some specifics:
1) Proxy server: Squid is very popular... install it.. then open the file squid.conf ( i don't remember where it is... plz search it) and  uncomment and add or modify:

http_port xxxx                                  (use any port... 3128 is default)


acl localnet src 192.168.0.0/255.255.0.0


http_access allow localnet

(squid.conf modifications---- thx to tonym)

2) In winxp open internet explorer  tools>internet options>connections>lan settings>select proxy.. and add 192.168.0.1 and port as 3128.
all programs that connect to internet mostly have proxy option... so just add proxy settings to them.

3) If u want to share internet from winxp... use proxy servers like ccproxy or proxy+...

---

### Post by billyK on 2005-09-03
it's not working i think i'll lose my mind.....damn

---

### Post by robert_pectol on 2005-09-07
Follow this guide.  It will explain all the steps necessary for configuring Ubuntu as a NAT-routing gateway.  It even has a NAT routing script that you can download, which sets up this functionality in Ubuntu:

[http://rob.pectol.com/content/view/3/1/](http://rob.pectol.com/content/view/3/1/)

It also has information on Ubuntu-firewall; a firewall written specifically for Ubuntu Linux which sports NAT-routing and port forwarding capabilities.  Good luck!

---

