---
title: "No Wired Network 7.10"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by hklak on 2007-11-02
Here is the scenario; I had 7.04 and everything ran smoothly.  I am a newbie and have come a long way.  So I decided to move up to 7.10.  I have no wired network connection.  I've read many posts and tried a sh*load of things.  Nothing.  I went as far as going back to 7.04 and guess what, no wired network?  

If anyone has some patience out there to walk me through this - that would be appreciated greatly.

---

### Post by PhilipGanchev on 2007-11-02
Some things to try:
- Check that your network card's LEDs light up when you plug in the network cable.  If you can't see any lights, check that the cable is well plugged into the network port on one end and into your modem or live network port on the other.  Can another computer access the network on the same cable and modem?  If you have a PCMCIA network card, make sure it is well plugged into your PCMCIA port.
- Open a terminal and type the command "sudo ifconfig eth0 up" to activate the ethernet interface and "ifconfig eth0" to check it.  
- Type "sudo dhclient" to try to conficure your IP address dynamically. What is the output and does your network work now?
- Type "lspci | grep -i ether" to list your ethernet card.  Type "lsmod | less" to list the installed drivers, and look for one whose name suggests it may be for your card.

What is the output of all the commands?

---

### Post by hklak on 2007-11-02
thank you for responding.  i actually just got done removing 7.10 and regain the space.  i plan to install 7.10 over the weekend.  i'll post my results.  thanks once again

---

### Post by dalziel on 2007-11-02
I'm as new as you (probably newer), and I had exact same problem, here's how I was (so far) able to fix it.
Select
Applications/Accessories/Terminal
then type 
sudo gedit/etc/resolv.conf
Put in password if asked for
In this file, the only entry was the address for my DSL modem, so I inserted ABOVE that address,the DNS obtained from my ISP to connect to the internet. It worked! I get no credit, as the suggestion came from a post about Ubuntu 6.06 I think.
Good luck

---

### Post by SwaroopKunduru on 2007-11-02
> 

- Check that your network card's LEDs light up when you plug in the network cable. If you can't see any lights, check that the cable is well plugged into the network port on one end and into your modem or live network port on the other. Can another computer access the network on the same cable and modem? If you have a PCMCIA network card, make sure it is well plugged into your PCMCIA port.
- Open a terminal and type the command "sudo ifconfig eth0 up" to activate the ethernet interface and "ifconfig eth0" to check it. 
- Type "sudo dhclient" to try to conficure your IP address dynamically. What is the output and does your network work now?
- Type "lspci | grep -i ether" to list your ethernet card. Type "lsmod | less" to list the installed drivers, and look for one whose name suggests it may be for your card.



1) Brodcom wireless  card is O.K it is working on windows boot.

2) sudo ifconfig eth0 up --- this is throwing an error
SIOCSIFFLAGS: No such file or directory

3) lspci | grep -i ether
Nothing returned

4) lsmod | less 
On this command it has listed lot of modules including ndiswrapper.

Please help me fixing this problem.

---

### Post by hklak on 2007-11-04
i removed it entirely.  extremely disappointed at how not friendly this turned out to be.  7.04 was great.  shame i upgraded.  stuck with xp yet again.  thank you for your help though.

---

