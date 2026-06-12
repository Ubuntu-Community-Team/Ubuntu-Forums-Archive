---
title: "Samba working with LAN, not working with wireless"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by iopo on 2008-05-23
Hi guys,

I installed Samba at school where my laptop was connected via ethernet. Using Dolphin I was able to browse the network and see all the computers connected.

At home I use wireless. I have been trying for the past two days to establish a connection with my girlfriend's laptop but nada! No luck at all.

We share the same wireless connection, we are part of the same workgroup, I checked the smb.conf to make sure that wireless was not blacklisted. Still no luck! When I go to Network > Samba Shares > Workgroup I only see my machine. Similarly, on my girlfriend's laptop, if I go to Network, her computer is the only one in the network.

I have no idea on what to do and I have been searching the internet for quite sometimes with no luck!

Thanks a lot!

---

### Post by aikiwolfie on 2008-05-23
So far as I know there's some sort of bug in Ubuntu or the version of Samba that Ubuntu uses that stops it connecting to Windows shares.

---

### Post by superprash2003 on 2008-05-23
ensure that both pcs can ping each other.. try accessing each other's pc by typing smb://(ip of pc to access)

---

### Post by iopo on 2008-05-24
Thanks a lot for the replies!

Typing smb://workgroup/ in Konqueror address bar, I managed to see both the computers, but when I click on my girlfriend's one it say "impossible to connect to smb://...".

Also, if I open the vista box, I click network, I don't see the Ubuntu box under "workgroup".

I'm pretty sure the vista sharing setting are fine: I turned "public folder sharing" on and I made a folder public. Theoretically, everybody belonging to the same network should be able to access the folder.

So I suspect that the problem is samba on my computer. But I  tried everything I found in threads/how-tos: mess up with users, change the smb.conf. Still no luck!

Anybody has a suggestion?

Thanks!

---

### Post by AbredPeytr on 2008-05-24
> **aikiwolfie said:**
> So far as I know there's some sort of bug in Ubuntu or the version of Samba that Ubuntu uses that stops it connecting to Windows shares.

Can't be Ubuntu in general. I got sharing to work on my Ubuntu partition. I can print and play music files from my desktop. I haven't yet got sharing working on my Kubuntu partition.

---

### Post by iopo on 2008-05-24
Hi AbredPeytr,
I'm not sure I understand: are you saying it is a KDE/Kubuntu problem or that you never tried to connect a Kubuntu machine with a windows one?
I never thought it could be a Kubuntu specific problem...

---

### Post by iopo on 2008-05-27
I figured out the problem with the wireless. If the laptops are connected via wireless, in order to see my workgroup I need to stop and restart the samba daemon manually. After I do this my laptop responds the same way than with a LAN network.

However I still wasn't able to connect to my vista laptop. 

Any suggestion?

Thanks

---

### Post by Ceadda on 2008-05-29
> **iopo said:**
> I figured out the problem with the wireless. If the laptops are connected via wireless, in order to see my workgroup I need to stop and restart the samba daemon manually. After I do this my laptop responds the same way than with a LAN network.

However I still wasn't able to connect to my vista laptop. 

Any suggestion?

Thanks

bump

---

