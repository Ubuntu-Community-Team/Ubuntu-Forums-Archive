---
title: "Change Network Name"
date: 2006-12-08
forum: Networking &amp; Wireless
---

### Post by Priswell on 2006-12-08
I have a Xubuntu computer running on a Windows Network. I want to use the printer attached to one of my Windows computers, but I can't find it in Print Manager. I think that my Xubuntu computer has the wrong network name. How do I change the network name ?

---

### Post by taurus on 2006-12-09
Do you mean like the name in /etc/hostname?  If you decide to make a change to /etc/hostname, you MUST also make the same change (with a same name) to /etc/hosts or you will find out some commands won't work (especially sudo) and some of the network apps won't work...

Applications -> Accessories -> Terminal
```
gksudo gedit  /etc/hostname  /etc/hosts
```

---

### Post by Priswell on 2006-12-09
*Do you mean like the name in /etc/hostname?*

<taking a deep breath trying to explain>

Um, no. I'm referring to the network name. Each computer has its name, right? Then on the windows network, the network has a name as well. 

I have a network of 2 windows computers and 2 Linux computers. One of the linux computers, "Ubuntu", can see the Windows network. But the other one, "Xubuntu" cannot. 

When I look at the *network places* from my Ubuntu computer, I see two networks, one named "ABC" and the other "DEF". ABC has the two windows computers and Ubuntu, and the other one has only Xubuntu. Xubuntu can't see the ABC network, and so it cannot see the printer that resides on the ABC network.

Somehow, I've got to get the Xubuntu computer on the same network as the other 3 so it can use the printer.

Clear as mud?

---

### Post by Maddy on 2008-03-23
> **Priswell said:**
> *Do you mean like the name in /etc/hostname?*

<taking a deep breath trying to explain>

Um, no. I'm referring to the network name. Each computer has its name, right? Then on the windows network, the network has a name as well. 

I have a network of 2 windows computers and 2 Linux computers. One of the linux computers, "Ubuntu", can see the Windows network. But the other one, "Xubuntu" cannot. 

When I look at the *network places* from my Ubuntu computer, I see two networks, one named "ABC" and the other "DEF". ABC has the two windows computers and Ubuntu, and the other one has only Xubuntu. Xubuntu can't see the ABC network, and so it cannot see the printer that resides on the ABC network.

Somehow, I've got to get the Xubuntu computer on the same network as the other 3 so it can use the printer.

Clear as mud?

To do it through GUI, I would try System > Admin > Shared Folders and there's a "General Windows Settings" button if you add or edit a share. I don't know this works, as I usually tweak the smb.conf file.

second tab !!

---

### Post by Eiríkr on 2008-03-23
@Priswell --

For future reference ;), what you describe is more specifically known as the "workgroup name".  This is specific to Windows machines (and Samba sharing setups), and has exactly *zero* bearing outside of Windows World&#8482;.  

HTH,

Eiríkr

---

