---
title: "Accessing files and printer on Windows XP Pro over home network has defeated me"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by amanchesterman on 2011-07-22
Hi I am hoping that some kind soul will take pity on an old(ish) guy with limited technical understanding and will help me solve this problem.

I am running Ubuntu 10:10 on a Toshiba laptop. Via our home network I want to access files and especially a printer on a PC running Windows XP Pro. I was able to do this until recently, but the XP machine has been replaced and I cannot get the new setup to work. I have spent most of today working through various howtos and threads on this and other forums, but many of them are very long and/or relate to other versions of Ubuntu, and the solutions I have tried so far simply don't work.

What I have done is:
- Installed the printer on the Windows machine and verified that it works OK.
- Turned off bidirectional printing support on the Windows machine, since in the past this has caused problems when printing from the Ubuntu machine.
- Turned on file and printer sharing on the Windows machine and verified that the Windows firewall is set to permit access via the network.
- Checked that Samba is installed on the Ubuntu machine and that the Samba daemon is working.
- Edited the smb.conf file so that the workgroup name is 'MSHOME', as it is on the Windows machine.

The symptoms are:
- From the Ubuntu machine I can ping the Windows machine across the network.
- From the Windows machine I can access the Windows shared folder and the shared folder on the Ubuntu machine.
- On the Ubuntu machine, when I click on 'Network' in the 'Places' navigation GUI, the icon for 'Windows Network' appears; and when I click on that, the icon for 'MSHOME' appears, and within that the icons for the two computers (the Ubuntu and Windows machines).
- But when I then click on the icon for the Windows machine I get an error message saying 'Unable to mount location - failed to retrieve share list from server'.
- On the Ubuntu machine, when I try to add a network printer and select the 'Windows printer via Samba' option, the browsing dialogue shows the Windows computer: but when I click on that, no printer appears.
- On the Ubuntu machine, if I add a Windows printer via Samba by typing in the network location, the printer appears to install: but if I then try to print a document or a test page it simply fails to respond (nothing happens).
- If I carry the Ubuntu machine through the house to where the printer is and plug it directly into the USB port, the printer works fine.

In summary:
- The home network is working (e.g. I can access the internet across it).
- The Windows machine can access the resources of the Ubuntu machine.
- The Ubuntu machine can't access the files or printer on the Windows machine, despite the Windows machine being set up to allow this.

I will be very grateful to anyone who can help, especially in a non-technical way. Since this kind of arrangement worked perfectly before, I think I must have overlooked some simple and obvious step in setting it up.

Btw I have read that there are ways to set up this kind of sharing without using Samba. But Samba is what I used before and it was perfectly adequate for my limited needs, so I would prefer to use it again now rather than venturing into unfamiliar territory.

Thanks in advance
John

---

### Post by MG&amp;TL on 2011-07-22
[https://help.ubuntu.com/8.04/internet/C/networking-shares.html](https://help.ubuntu.com/8.04/internet/C/networking-shares.html)

I'm not sure precisely what the problem is or what you have missed ( if anything!) but I have enclosed a link containing instructions.

This would appear to deal with files, not printing, but I'm sure that this will set the ball rolling. The resource is from the ubuntu documentation, which is a fantastic place to go for normal 'how-to questions' -although everyone here is perfectly happy to answer them anyway! :)

---

### Post by amanchesterman on 2011-07-22
Thank you for your prompt response. However, the link you have given is about how to access shared folders on a Ubuntu machine from a Windows machine, and that is not my problem: I can do that successfully. What I can't do is the other way around, i.e. how to access Windows resources from Ubuntu.

Incidentally I have already worked through the official documentation for Maverick networking and for Samba shares. I have followed the instructions: my problem is that the instructions they give haven't produced the results they are supposed to!

John

---

### Post by alphacrucis2 on 2011-07-22
> **amanchesterman said:**
> Thank you for your prompt response. However, the link you have given is about how to access shared folders on a Ubuntu machine from a Windows machine, and that is not my problem: I can do that successfully. What I can't do is the other way around, i.e. how to access Windows resources from Ubuntu.

Incidentally I have already worked through the official documentation for Maverick networking and for Samba shares. I have followed the instructions: my problem is that the instructions they give haven't produced the results they are supposed to!

John

In your network adapter settings in Windows, do you have file and print sharing ticked and actually shared the printer and folder

---

### Post by walt.smith1960 on 2011-07-22
What kind of printer?  If it's network enabled, I've had excellent success either plugging into the router or wireless networking if you have it.  Networked printers seem to be O.S. agnostic.  I tried printing via a network from one windows box to a  printer plugged into another Windows box years ago--before I knew what Linux was--and it was perhaps the most frustrating thing I've ever attempted.  I had a full head of hair before I started that :-).

---

### Post by amanchesterman on 2011-07-22
> In your network adapter settings in Windows, do you have file and print sharing ticked and actually shared the printer and folder

Yes file and printer sharing are turned on in the Windows network, and the properties for the Windows shared folder and the Windows printer both show them as being shared.

Thanks
John

---

### Post by amanchesterman on 2011-07-22
> **walt.smith1960 said:**
> What kind of printer?  If it's network enabled, I've had excellent success either plugging into the router or wireless networking if you have it.  Networked printers seem to be O.S. agnostic.  I tried printing via a network from one windows box to a  printer plugged into another Windows box years ago--before I knew what Linux was--and it was perhaps the most frustrating thing I've ever attempted.  I had a full head of hair before I started that :-).

It's a fairly old HP Deskjet -- alas, not network enabled, though it still works fine when connected directly to a Windows or Ubuntu machine.
I too used to have a full head of hair ... happy days!

John

---

### Post by Morbius1 on 2011-07-22
What I would suggest is 3 simple things first.

[1] See if the samba client on the Ubuntu machine is functioning properly:
```
nautilus smb://192.168.0.100
```Change 192.168.0.100 to the ip address of the Windows machine. 

[2] Run and post the output of the following diagnostic command:
```
smbtree
```[3] Post the output of the following command. There are rules about samba and hostnames:
```
hostname
```

---

### Post by amanchesterman on 2011-07-22
Thank you for your helpful responses. While waiting for people to reply, I continued searching for suggestions online, and eventually found one that worked.
It involved using the IP address of the Windows computer rather than referring to it by name.
I can now use the Windows printer and access Windows shared folders.
Thanks again, I have marked this thread as SOLVED.

John

---

### Post by nikkih on 2012-05-09
I have exactly the same problem. I can see the XP machine from Ubuntu (11.10) but cannot access it - could you post a link to your solution, please?

Thanks

---

