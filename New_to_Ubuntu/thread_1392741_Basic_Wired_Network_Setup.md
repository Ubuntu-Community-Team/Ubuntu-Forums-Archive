---
title: "Basic Wired Network Setup"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by JimTheSailor on 2010-01-28
Hi;)
I am new to both Linux and setting up a network.
I am running Ubuntu 9.10.
I have three computers connected to the web via a D-Link Dl-604 router using ethernet.
I want to connect my computer to one of these. It is running Vista Home Premium.
On the Vista machine I have shared the printers and set up a workgroup JJGROUP.
(1) Do I need any more wiring or network cards etc or do I have everything I need since both computers are connected to the router already?
(2) I cannot see how to set up the network using Gnome. The _NetworkManager_ icon is showing in the tray and clicking it shows "Wired Network" greyed out, "Auto eth0", "Disconnect" and a VPN option to setup a VPN.
Under the menu System=>Administration I have _Network Tools_ which shows Ethernet Interface (eth0) and Loopback Intercace (lo) information.
I cannot see how to use these to actually set up a local area network. I have spent days searching Umbutu Forums, the web and reading all kinds of things but have gained nothing but high blood pressure.
Thanks for any help you can give me.
Jim

---

### Post by A&#11375;A on 2010-01-28
I'm not that good with ubuntu yet, so i don't know how to fully diagnose the issue with the network, but posting what kind of network card you have should help.

As for the printer, this guide should be able to help
[http://www.watchingthenet.com/connecting-to-shared-printers-on-windows-computers.html](http://www.watchingthenet.com/connecting-to-shared-printers-on-windows-computers.html)

---

### Post by halitech on 2010-01-28
> **JimTheSailor said:**
> Hi;)
I am new to both Linux and setting up a network.
I am running Ubuntu 9.10.
I have three computers connected to the web via a D-Link Dl-604 router using ethernet.
I want to connect my computer to one of these. It is running Vista Home Premium.
On the Vista machine I have shared the printers and set up a workgroup JJGROUP.
(1) Do I need any more wiring or network cards etc or do I have everything I need since both computers are connected to the router already?
(2) I cannot see how to set up the network using Gnome. The _NetworkManager_ icon is showing in the tray and clicking it shows "Wired Network" greyed out, "Auto eth0", "Disconnect" and a VPN option to setup a VPN.
Under the menu System=>Administration I have _Network Tools_ which shows Ethernet Interface (eth0) and Loopback Intercace (lo) information.
I cannot see how to use these to actually set up a local area network. I have spent days searching Umbutu Forums, the web and reading all kinds of things but have gained nothing but high blood pressure.
Thanks for any help you can give me.
Jim

1. No you don't need anymore wiring or network cards if you are doing everything through the router

2. Does the Ubuntu machine have a connection to the Internet? ie. does it have an IP address in the same subnet as the Vista computer?

You won't do the networking through Network tools or the Network Manager. You should have a Places Menu in the top bar, click that and Connect to Server. Select Windows computer (guessing on the names as I use XFCE) and enter the info for the Vista computer. Click connect and you should be connected.

---

### Post by J V on 2010-01-28
1: yes, one to connect the pc 2 pc link :)
2: The connection needs to be set up on the windows box, not the linux one... Actually, it would probably be much more stable to use the linux box as the "mini-switch"

Edit: Oh you want to connect with it? thats easy, make a shared folder on windows then go to network :)

---

### Post by halitech on 2010-01-28
> **J V said:**
> 1: yes, one to connect the pc 2 pc link :)
2: The connection needs to be set up on the windows box, not the linux one... Actually, it would probably be much more stable to use the linux box as the "mini-switch"

why would the OP need more cables and NICS if they have a connection through the router? Why add more components to the mix that can screw up?

---

### Post by JimTheSailor on 2010-01-28
Thanks to all of you.:p I will now try to figure out what I need to do to connect to the server;)

---

