---
title: "Browse the network"
date: 2006-07-27
forum: Networking &amp; Wireless
---

### Post by jrjr on 2006-07-27
Hi all

My first install was really rough video wise.

 From what I can remember all I had to do to browse the network the first time was to change the /ets/samba/smb.conf file and set the workgroup to the workgroup of my other boxes - HOME

Now I am on my second clean install. The video went a lot faster and smoother this time but I can't seem to get browsing working. 

What i've done-
I changed the file to my workgroup again
Tried a bunch of different things found on the forum here
added user
removed user
added samba
removed samba
added samba again
rebooted a lot
etc.

So nothing has changed except for mshome going away -which is the default workgroup. I changed it so it should be gone eh?

Now when I click Places/Network Servers I get the window open with "Windows Network" displayed 

Double click displays my workgroup - home

Double click home and I get a prompt that says -
  
"The folder contents could not be displayed
Sorry, couldn't display all the contents of "Windows Network:home". "

Say ok to that and its a blank window. 

So being a noob of course im askin for help!! :p

Edit - 
BTW this is a hardwired network, no wireless

---

### Post by jrjr on 2006-07-27
I can ping all the other boxes by IP
What should I do to troubleshoot?

---

### Post by jrjr on 2006-07-27
I can see the Ubuntu box from windows box's but cannot see windows boxes from the ubuntu box. I installed LinNeighborhood but that only shows the local machine. 

What could be so different from one install to the next? 
The only difference I can think of is I formatted to ext3 and the first install I used ext2

Would that make a difference?

---

### Post by jrjr on 2006-07-28
.

---

### Post by jrjr on 2006-07-28
.

---

### Post by jrjr on 2006-07-29
?

---

### Post by jrjr on 2006-07-29
.

---

### Post by jrjr on 2006-07-29
.

---

### Post by Swab on 2006-07-29
Was the Windows box rebooted?  Maybe the problem was there.

---

### Post by jrjr on 2006-07-29
.

---

### Post by Swab on 2006-07-29
> **jrjr said:**
> Actually there are 2 windows boxes, a server and another desktop. Neither one have been rebooted since I last checked to see if I could browse. Good idea though. I tried that in the beginning when I was trying to get things working. 

Maybe when I threw it out the window it shocked it a bit. :mrgreen:

We have a server running Samba at work.  Every single Windows client except 1 can connect to it without a problem.  It keeps asking for a username and password and won't accept anything.  It's got me pulling my hair out.  I think I'll just have to reinstall that client.

---

### Post by jrjr on 2006-07-29
.

---

### Post by skralljt on 2006-10-19
I have this same problem, I think it may be related to whether or not your linux box is the wins server or the master domain controller, a bunch of complicated network crap.  xp boxes and ubuntu boxes apparently bump heads over who gets to call the shots controlling the network.  Also there is a dialog somewhere in the gui of ubuntu that lets you specify what your login name will appear as when you browse the network.  
another possibility:  did you change your login name?  if your login name corresponds to one on windows maybe that helps you login.  The share settings on the windows box may be user level instead of share level access.  that is all i can speculate.  
the best advice i can give you is to figure out how to use ftp or ssh/sftp, because they are way better than smb as far as reliability, resuming of downloads, and telling you what files failed to transfer should that happen.  And they are way more reliable than this samba business.  imho.

---

### Post by bait on 2006-10-20
Samba can be configured in a number of different configurations, from simple workgroup to full ( NT4 style) domain control.

 If your not using full domain control then you need to map windows groups to local groups in order to give access to the shares on the local machine.

 Lookup group map on the samba.org page.

---

