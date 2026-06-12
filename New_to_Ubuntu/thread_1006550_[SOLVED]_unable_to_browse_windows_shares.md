---
title: "[SOLVED] unable to browse windows shares"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by BDNiner on 2008-12-09
I have several windows shares setup on my XP computer. I am able to connect to all of them except for one using nautilus' browse network option. I will post the specifics and answer any questions of the issue once i get home. I just thought it was strange that I am able to connect to a browse 2 other shared directories on the same computer.

---

### Post by taseedorf on 2008-12-10
im sure you've done this, but on the one you cant see, have you allowed all other computers to see it, as far as windows firewall or router is concerned?

---

### Post by BDNiner on 2008-12-11
Yes I have they are all setup the same. I have set my windows firewall to allow access to my 3 shared folders across the network. The only thing i can see being an issue is that the share is in My Documents under my another user's profile but I have admin access to the computer. It is making me pull my hair out right now.

---

### Post by halitech on 2008-12-11
can you connect using the IP address and share name of the windows computer?

ie smb://192.168.x.x/sharename

---

### Post by Kellemora on 2008-12-11
Hi BDN

I think I might see your problem, then again maybe not.

Having it under another user name is not the problem, but do you have it under the SAME GROUP NAME?????

Even if you don't, it should be visible under Windows Network!

One other thing Places/Network does NOT always work right in Ubuntu.  Sometimes you have to go up to GO/Location and type in the IP number of the machine for it to show all the shares.

However, since you said other shares on that same machine are showing up, I would go back to the Windows machine and double check everything again.  I've shared folders nested some 8 levels deep stored in documents and settings/my documents with no problem.  Even password protected and hidden folders to at one time.

On trick you may try is to UNSHARE the folder and then SHARE it again.  I've had to do that many times as they somehow just got lost in the shuffle.

Good Luck

TTUL
Gary

---

### Post by BDNiner on 2008-12-12
I don't think you guys understand. I can see the folder but when i try and open it I get an error something like it is not accessible. I will post the exact error when i get home. So it will not let me browse into the folder and see the contents. but it is displayed. I have 2 other shares on the same computer and they work fine. 

I have tried unsharing and resharing the folder on the windows PC and still get the same results. I don't understand what is wrong with that folder. I copied all the data to a backup drive and created a new share and that works. I still want to fix this issue since i will only update the data on the backup drive every once in a while.

halitech, I will try connecting to the IP address and share name and see if that enables me to access the folder.

---

### Post by foofighterjim on 2008-12-12
As a test only make sure that the "Everyone" group has full permissions. Then try to access the folder, if this works you will need to make sure that your group settings are correct.

---

### Post by BDNiner on 2008-12-12
The exact error that i get is: "Unable to mount location. Failed to mount windows share."

---

### Post by BDNiner on 2008-12-12
Thank you so much. This worked perfectly, I don't know why i did not see this before. "Everyone" wasn't listed and it was for the other shares that I had setup.

> **foofighterjim said:**
> As a test only make sure that the "Everyone" group has full permissions. Then try to access the folder, if this works you will need to make sure that your group settings are correct.

---

### Post by foofighterjim on 2008-12-13
No problem, its not best practice however to leave the Everyone group with full access. You would be much beter served to create a group setting just for the Ubuntu user.

---

### Post by BDNiner on 2008-12-15
I did not give everyone full access, just read. all i wanted to do was copy about 6 GB of data and copy it to my memory card and them walking to the other computer...would have taken like 4 hours. But the wireless connection was just as slow. Started at 260 kb/s and then slowed to about 80kb/s. it went for around an hour before the window box crashed. I will start over on wednesday morning anyways.

I am almost at the point of snaking some cable through the walls and creating an ethernet network. That way i can build a NAS linux box and setup a media server.

---

