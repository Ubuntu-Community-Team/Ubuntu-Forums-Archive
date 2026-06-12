---
title: "samba big problem"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by ludolf on 2007-08-07
Hi all,

I have been browsing the forum and the net for the last 2 days. honestly iam very close to hit my head to the wall.
Please help, and here is my probelm:

I have two computers.
First: ubuntu, connected to the net using dsl router, and connecting it was easy using sudo pppoeconf, its connected using USB, and for details the usb is pluged to the router and to the computer. the connection is fine and Iam happy with it.

second: XP professional, connected to the same router, and its not able to connect to the internet or to the other computer.

So non of the computers is able to see the other.

when I go to network from places I see that the location is network:/// and I see icon called windows network, when I click it the location becomes smb:/// and nothing inside the folder.


Please please help in solving that,

Thanks in advance.

---

### Post by dmizer on 2007-08-07
okay ... you say that you're connected to your dsl router with a usb cable.  you also indicate that you're using pppoeconf to connect to the internet with ubuntu.

because of this, i think you're probably not actually connecting with a router, but with a modem.  there are many differences between a modem and a router, but the ones you should be concerned about is this:
1) with a modem, you can only be connected to the internet with one computer at a time.
2) some modems have both a usb port, and an ethernet port which would seem to allow two computers to use the same modem.  but modems with both an ethernet port and a usb port do not generally allow both ports to be used at the same time (one or the other, but not both).

this means that with your modem, despite the fact that you can physically connect both your ubuntu computer and your xp computer to it ... you will not be able to use the internet with both computers at the same time, and further ... you both computers will not be able to see eachother.

one quick, easy, and cheap fix for your problem (if i'm understanding it correctly) is to purchase a dedicated router.  you can purchase a very cheap wired router to take care of your pppoe authentication when it's connected to the ethernet port on your modem.  it also allows (depending on your purchase) up to 4 computers to connect to the internet at the same time.

wireless routers will allow many more computers to connect to the internet via wireless, but they are more expensive.

---

### Post by Austin_KW on 2007-08-07
What is your router model? Can you connect to the router and configure ppp on the router and then use the router to share this internet connection.

The other option is to connect the two PC ethernet ports, with a crossover ethernet cable and use firestarter to share the internet (usb) connection. But this means that the sharing PC must be on to use the internet on the second pc.

---

