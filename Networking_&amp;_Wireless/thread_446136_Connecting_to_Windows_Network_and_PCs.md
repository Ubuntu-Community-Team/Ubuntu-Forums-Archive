---
title: "Connecting to Windows Network and PCs"
date: 2007-05-16
forum: Networking &amp; Wireless
---

### Post by Panzor on 2007-05-16
Hey, I've been milling around the forums, answering people's questions, learning a few things, and I decided that it's time to figure out my own problem.

My network consists of a Win2000, XP Pro, and XP Home computers (well, those are the ones I'd like to connect to). I've identified them on my "Windows Network" as 'desktop configuration files.' 

I can access my XP Home's shared folder with no errors whatsoever. I'm not sure why this is, but it is.

The Win2000 and XP Pro machines do not allow me to open them. The error is below:
The shared documents folder on the left is the Shared on the XP Home that works. UnclePhlegm is the win2000 machine.
[IMG]http://i73.photobucket.com/albums/i209/FateMSGuild/Screenshot.png[/IMG]
I was hoping you guys could help me connect to all of these machine's shared documents (especially the win2000 since that's where my printer is connected) and allow the pcs to see this computer's shared documents.

On all of the other pcs (win2000, XP home and Pro) they are prompted for a user and pass which does not exist or wasn't set. I used my login information, but that does not work.

I'm not sure if I need samba to access them or what. What do you guys think?

---

### Post by Panzor on 2007-05-16
bumped. I need some help guys. At least point me in the right direction.

---

### Post by gerdt on 2007-05-17
I believe this is not an Ubuntu problem, but a Windows problem. I.e. I believe your windows shares are not correctly configured.
The fact that you _can_ access the XP Home PC means that your Ubuntu machine _is_ capable of connecting to network computers/shares.

Have you tried connecting to those windows pc's through other windows PC's ?

---

### Post by Panzor on 2007-05-23
Yes, all of the windows PCs can connect to each other.

---

### Post by gerdt on 2007-05-24
Are all PC's in the same workgroup?
I have sometimes the same problem.
What I do is have some patience, and try to refresh the window and try some more times.
NOrmally this works for me

---

### Post by Panzor on 2007-06-03
No, the PCs are all in separate workgroups.

---

### Post by Panzor on 2007-08-02
Someone else told me to put them all in the same workgroup and that seemed to fix the problem right up. Only now none of the other PCs can print O.O

Another problem for another thread. Thanks guys.

---

