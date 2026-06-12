---
title: "how do i ..."
date: 2009-09-06
forum: New to Ubuntu
---

### Post by Thocrun on 2009-09-06
I have a ubuntu server and I wan't to connect it wirelessly to my windows xp home ed., I checked windows xp for wan cards, it has some, so I need to check the ubuntu server and get it connected, any way to do this?

---

### Post by mlentink on 2009-09-06
have you tried:
```
lspci -v
```
at all? That should list all of your devices, including any wifi cards.

If you want to know more about the command and its options, do:
```
man lspci
```

---

### Post by mapes12 on 2009-09-06
> **Thocrun said:**
> I have a ubuntu server and I wan't to connect it wirelessly to my windows xp home ed., I checked windows xp for wan cards, it has some, so I need to check the ubuntu server and get it connected, any way to do this?What is your definition of "server"? Most servers are configured from the command line with no GUI (security).

If you mean a straight forward Ubu machine the go to the XP machine and enable File & Print Sharing from Control Panel. Then go to the folders you want to share, right click and enable Sharing. CARE - the XP user account must have admin rights. A Limited user account will not support this.  

Over to the Ubu machine and install pyNeighborhood in Synaptic. Some tweaks first:

1. Edit>Preferences - Mount folder /home/yourusername
2. Remove mount point after unmount = tick
3. File Manager - add Nautilus

Then in the left hand pane right click the globe and select scan. Your XP shared folders will appear in the right hand pane. Double click the share to mount it then right click and select Nautilus to browse the folder and transfer files back and forth.

---

### Post by Thocrun on 2009-09-06
thanks mlentink, I tried it, it didn't have any wireless cards, so now I am trying to get the ubuntu 32 bit server (that's all) to write to a floppy so that I can put it on my other pc and connect it to ethernet since the one on my windows xp is disabled.

---

### Post by mlentink on 2009-09-06
> **Thocrun said:**
> so now I am trying to get the ubuntu 32 bit server (that's all) to write to a floppy so that I can put it on my other pc and connect it to ethernet since the one on my windows xp is disabled.
????
I'm not sure I understand what you are trying to achieve here.

---

### Post by Thocrun on 2009-09-06
one more question, is there anyway to run a floppy so when the computer starts it runs the cd instead?, I've got another comp that I want to run ubuntu desktop ed. on, it's been very stubborn to running the cd drive. I think it's D:\ or something like that.

---

### Post by Thocrun on 2009-09-06
oh, my windows xp has the ethernet cable disconnected and the server doesn't have wireless software, so I guess I'm trying to run plan c, get one of my old pc's to put desktop edition on and see if I can connect with that, I just wanted to edit the files on the server = main goal.

---

### Post by Thocrun on 2009-09-06
+ see the files and folders on there, I just thought it would be a lot easier for me to have access to it from another pc.

---

### Post by mlentink on 2009-09-06
OK.
Let me get this straight: 
- you have an Ubuntu box (your 'server') which is not connected to other computers. 
- you have a XP Home box which is not connected to anything else either. 
- You have another system around which you want to install Ubuntu on to see the files and folders on the 'server', and maybe edit a few of them?

Is that about it?

---

### Post by 3rdalbum on 2009-09-06
If I understand correctly, your aim is to allow the Windows clients access to the Ubuntu server. The Windows clients have wireless cards but no Ethernet, right?

Best solution is to buy yourself a wireless router. Connect it via Ethernet to your server, and have the clients connect to the router wirelessly, and everything will be able to see everything else.

---

### Post by Thocrun on 2009-09-06
> **mlentink said:**
> OK.
Let me get this straight: 
- you have an Ubuntu box (your 'server') which is not connected to other computers. 
- you have a XP Home box which is not connected to anything else either. 
- You have another system around which you want to install Ubuntu on to see the files and folders on the 'server', and maybe edit a few of them?

Is that about it?

yeah, they are all 32 bit too, I want to edit the files on the server

---

### Post by mlentink on 2009-09-06
OK.

You do not necessarily need Ubuntu to be able to see what's on your server. As per 3rdalbum, the first hurdle is to connect the machines. His suggestion is correct. 
As your ´server' does not have a wireless card, it is best to connect it physically to the wireless router with a ethernet cable. Most wireless routers provide ports for that purpose.
You can then connect your desktops either wirelessly or by cable.

Then you could connect over the network by several means. If you have shared folders on your servers you will be able to see those on your windows boxes. If not, you will have to use ssh to login to the server. If you want an easy filemanager for your server, install midnight commander on it. One step further: install Webmin on the server, to enable you to control it remotely through a browser-based GUI.

---

