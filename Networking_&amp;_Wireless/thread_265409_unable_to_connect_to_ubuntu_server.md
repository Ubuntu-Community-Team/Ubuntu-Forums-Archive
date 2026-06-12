---
title: "unable to connect to ubuntu server?"
date: 2006-09-25
forum: Networking &amp; Wireless
---

### Post by patz on 2006-09-25
guys can u help how to connect my client computer  to ubuntu server.. this is the problem that i had encountered during connecting to server. 

hots error, FIFO diagnostic register 0000
PCI bus error,bus status 80000020 

then my connection status in blinking ON and OFF, is it possible that my ethernet card has dammage or need to replace? .I already configure the gui, DHCP,firestarter etc... can anybody help pls...

---

### Post by Mr Frosti on 2006-09-25
There are many different ways to connect to another machine. In this specific issue, what type of connection are you trying to establish? Is this for authentication, or updates? 

If you would like to test your network card, open a terminal and type "/sbin/ifconfig". See what information your network card is reporting. If it is flashing lights, this typically means it is polling the network for resources, such as a DHCP server, etc.

---

### Post by patz on 2006-09-25
> **Mr Frosti said:**
> There are many different ways to connect to another machine. In this specific issue, what type of connection are you trying to establish? Is this for authentication, or updates? 

If you would like to test your network card, open a terminal and type "/sbin/ifconfig". See what information your network card is reporting. If it is flashing lights, this typically means it is polling the network for resources, such as a DHCP server, etc.

I want to share the connection of the internet. i had setup ubuntu 6.06 and 1 spare computer. sir can i ask you what is the cable connection when you want to network a Ubuntu server and client is windows Xp? is it crossover connection or straight? thank you very much:D

---

### Post by Mr Frosti on 2006-09-26
A crossover cable will connect the two machines to each other. However, unless you have more than one network port on each machine, this is not an ideal solution, as they can only talk to each other.

If you have one machine connected to the Internet, and you wish to share this connection to the other machine, you are looking to setup an Internet gateway. Typically on a high speed connection, these "gateways" reside on the router hardware.

In the spirit of Linux, I know that you can setup a gateway connection. One particular distribution, Coyote Linux makes this super simple. You might want to check into this if this is the sole purpose of your Ubuntu machine.

---

