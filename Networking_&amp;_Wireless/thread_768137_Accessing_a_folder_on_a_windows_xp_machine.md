---
title: "Accessing a folder on a windows xp machine"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by rlwpub on 2008-04-26
I have been searching for days on google and on the forums and can't find the answer I need.

I can access my ubuntu machine from windows xp using samba with no problem.

But... I can't access files on any windows xp machines on our network from ubuntu.

I can see the windows machines but when I click on one I get this error.

The folder contents could not be displayed.

Help! :)

Re's
Rob Whisonant

---

### Post by S.O.P on 2008-04-26
Plenty of threads discussing similar issues it seems.

Came across of one that rang true, tis a Nautilus issue, try using Konqueror and all Windows (XP) shares can be accessed as per normal.

Happened for me as well, couldn't sort it out until I installed Konq, it's all there in black and white or blue and white, whatever takes your fancy.  One thread I read has a link to a Launchpad bug so hopefully it's being worked on.

---

### Post by Coolit on 2008-04-26
I have the same issue accessing vista shares, hopefully it will get fixed soon.

---

### Post by Iowan on 2008-04-26
You didn't mention which version of Ubuntu (I haven't dealt w/ 8.04).  I frequently have better luck using Places>Connect to Server option.

---

### Post by rlwpub on 2008-04-27
> **S.O.P said:**
> Plenty of threads discussing similar issues it seems.

Came across of one that rang true, tis a Nautilus issue, try using Konqueror and all Windows (XP) shares can be accessed as per normal.

Happened for me as well, couldn't sort it out until I installed Konq, it's all there in black and white or blue and white, whatever takes your fancy.  One thread I read has a link to a Launchpad bug so hopefully it's being worked on.

I thought Konqueror was a web browser. What I am trying to do is edit a open office document that is on a windows xp machine with open office on a ubuntu machine.

Can anyone help with that?

Re's
Rob

---

### Post by Rahu on 2008-04-27
I'm having the same issue with a fresh install of 8.04.

Except I don't even see my windows machine listed in the network section.

Doing a manual "Connect to Server" also fails.

---

### Post by nullmind on 2008-04-27
Have you guys tried using the IP address of the host machine rather than it's Windows-based "name" (can't remember what that's called, is it "Active Directory"?)

On large networks, such as at university, I usually am sitting next to the bloke I want to access files via and he can just tell me his IP or instant message it to me. I then open nautilus and navigate to "smb://IP_ADDRESS/" to access their machine.

Also, sometimes people share things but don't have a "share point". For example I noticed if I only share a directory called "Diablo II" I couldn't navigate to "smb://192.168.1.1/", but could navigate to "smb://192.168.1.1/Diablo II".

---

### Post by S.O.P on 2008-04-27
> **rlwpub said:**
> I thought Konqueror was a web browser. What I am trying to do is edit a open office document that is on a windows xp machine with open office on a ubuntu machine.

Can anyone help with that?

Re's
Rob
Konqueror is a web browser amongst other things but when you first start it up, you can browse Samba shares.  Now, through Konqueror you can see the shares, browse the shared directories and grab the files you need.  For your problem, that doesn't help unless you bring the file over locally and then open it.

I'm assuming something is broken with the Nautilus/Hardy/Samba combination since Konqueror can access those shares as per normal.  Nautilus should just browse the shares like it did in Gutsy.

Edit:  Used smb://IP/Folder and smb://name/Folder in Nautilus and that works fine.  But, it's not that helpful, I can't remember the name of every shared directory on each IP and just smb://IP/ gets me a blank page.  I want to browse like Nautilus could and Konqueror can.

---

### Post by avpap on 2008-04-27
I have the same problem in Vista. I can see my Vista Pc in my Home  Network but I cannot see the shared drives. Did someone find an answer.  I'm using Hardy Heron 8.04

---

### Post by spawn12345 on 2008-04-27
> **avpap said:**
> I have the same problem in Vista. I can see my Vista Pc in my Home  Network but I cannot see the shared drives. Did someone find an answer.  I'm using Hardy Heron 8.04

Yeap have the same problem

---

### Post by Rahu on 2008-04-27
Here's what I get when I try to connect directly by IP:
[IMG]http://i26.tinypic.com/2vl39j5.png[/IMG]

Any idea on what I could do to get at my windows share?

---

### Post by S.O.P on 2008-04-28
Use the location bar in Nautilus and type in smb:\\IP\Folder Name.

Or use Konqueror.

---

### Post by Mazza558 on 2008-04-28
Even Konqueror doesn't work properly for me.

---

