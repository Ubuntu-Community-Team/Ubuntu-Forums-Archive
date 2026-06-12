---
title: "Installing network/ethernet drivers on ubuntu? Halp needed please"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by Halt, Reptar on 2011-04-11
Hello forum.

I installed Ubuntu and I can't connect. I would greatly appreciate the help.

---

### Post by Halt, Reptar on 2011-04-11
Bump. I'd really like to figure out how to connect to the internet with ubuntu. :)

---

### Post by 3rdalbum on 2011-04-11
Ubuntu usually comes with all drivers. Does Ubuntu report itself to be connected? What happens when you try to go to a website?

---

### Post by mapes12 on 2011-04-11
Does the Network Manager applet appear in your panel (top r/h corner). If yes then right click>Connection Information.

---

### Post by Halt, Reptar on 2011-04-11
> **mapes12 said:**
> Does the Network Manager applet appear in your panel (top r/h corner). If yes then right click>Connection Information.

Yes the network manager is there but "Connection Information" is grayed out.

---

### Post by Halt, Reptar on 2011-04-11
I'm trying to transfer what seems to be the Linux equivalent of the drivers I need, onto a CD so I can install them on Ubuntu. I get an error when I try doing that through explore. Would Nero work? How can I get "[kernal tar file]("http://www.nvidia.com/object/linux_nforce_1.0-0261.html")" onto a disk so I can then boot up Ubuntu and install the drivers? Also, how would I install them once I'm there?

---

### Post by Halt, Reptar on 2011-04-11
> **3rdalbum said:**
> Ubuntu usually comes with all drivers. Does Ubuntu report itself to be connected? What happens when you try to go to a website?
When I go to a website it says server not found. Ubuntu is not reporting itself connected.

---

### Post by 3rdalbum on 2011-04-12
In the network manager applet, you should see your wired connection/Ethernet card listed. Do you? Does it let you go to Edit Connections... and set up your Ethernet connection?

The file you posted a link to is much too old to install on Ubuntu. It's from almost 8 years ago! Nforce drivers are in the Linux kernel already, as another part of the Nvidia website says.

What version of Ubuntu are you using? It should be 10.04 or later.

Finally, can you please go into the terminal (Applications > Accessories > Terminal) and type:

```
lspci
```

(that's LSPCI but in lowercase) and see if your Ethernet is listed.

---

### Post by Halt, Reptar on 2011-04-13
> **3rdalbum said:**
> In the network manager applet, you should see your wired connection/Ethernet card listed. Do you? Does it let you go to Edit Connections... and set up your Ethernet connection?

The file you posted a link to is much too old to install on Ubuntu. It's from almost 8 years ago! Nforce drivers are in the Linux kernel already, as another part of the Nvidia website says.

What version of Ubuntu are you using? It should be 10.04 or later.

Finally, can you please go into the terminal (Applications > Accessories > Terminal) and type:

```
lspci
```(that's LSPCI but in lowercase) and see if your Ethernet is listed.

Yes my wired connection/ethernet is listed in the network manager applet and it lets me go to edit connections.

I'm using 10.10.

Typing lspci in terminal does list my ethernet.

I don't know if this matters but someone on another forum suggested to go to edit connection and set it to manual and then type in all my information like ip address netmask etc. Well I did this and then it said connection established but when I tried to go on any website it wouldn't load. No error messages or anything, the pages just don't load. Grr.

---

