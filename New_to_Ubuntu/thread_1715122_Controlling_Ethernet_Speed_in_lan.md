---
title: "Controlling Ethernet Speed in lan?"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by adeee on 2011-03-26
Guys i want to make a LAN with the help of 4 computer and 1st want to be a host computer. but i have no any idea how to make it as a host .and 2nd is how to control Ethernet speed over the LAN?

Can any body help me to how to build a LAN Host and LAN Host Party?

Also how to control net speed over the hole LAN?

Currently using windows.
But you can help me for Ubuntu10.04 and 10.10. :P

---

### Post by conneco on 2011-03-26
Very vague, all computers on a LAN are hosts,

ifconfig will be able to control the speed your nic goes at

---

### Post by gradinaruvasile on 2011-03-26
What do you mean by "control the ethernet speed"?

You will have 100 Mbit or 1 Gbit connection depending on the hardware (network adapters/switches) used.

mii-tool or ethtool are 2 utilities that tell your the connection speed (there are cases where only one of them works on certain network adapters). Or, if you use network-manager, right-click on its icon and select "connection information".

---

### Post by adeee on 2011-03-27
Further Explanation.

I have 4 computers and they are in very good position.
So I wan to make A computer center.

As you Know LAN is very important so I build a lan.
but there is a problem. i have 1 MB connection and i want to devide it in between the  computers.

So as the netcafes do( Dividing the speed between the computers) I want same.

So First i need no make a host computer you called it Server. Where the net will through to others computer.

i want to control the net. when i need to stop net i can do. and when i want to on the net i can do it from the host computer. So I need Software's and procedure how to control net speed..

if you dont mind i need these procedure both Ubuntu10.10 and Windows Xp

So what i need to do?

---

