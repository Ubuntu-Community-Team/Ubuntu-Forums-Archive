---
title: "Problemc connecting to Windows LAN"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by ChTidio2 on 2009-04-03
I read through the threads I could find on this issue and I believe I followed all the steps outlined, but...

I am running Ubuntu 8.04 inside VMware as a Virtual Machine.  My system is connected to a Windows LAN.  I can access the Internet from the Ubuntu VM and I can see all the LAN nodes (and server) from Places -> Network -> Windows Network. However, when I double-click on any of the server icons, to connect to that system, I just get a blank screen.  Also, the Ubuntu box is not visible on the LAN.

I have installed samba and have enabled my user name on it.

Do I connect Ubuntu to the Domain, so that I can share this box and access the other LAN boxes from it?  If so, how would I go about it?

Sorry if this sounds trivial  :-(  Hopefully I am posting to the newbie forum.  If this has been addressed in another thread, no need to repeat it hear, just point me to it.

Chris

---

### Post by superprash2003 on 2009-04-03
try accessing the shares this way [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by ChTidio2 on 2009-04-03
Thanks.  I went to the URL and tried your suggestion, but when I select Places --> Computer, I get the "Computer - File Browser" dialog, but no GOTO field.

Just in case I am messing something obvious up, did I mention I'm really green at ubuntu?

Chris

---

### Post by odinb on 2009-04-03
What I do is usually this:

In Ubuntu to map a network share using samba you do as follows:
Choose "Places" >> "Connect to Server..."
Change "Service type" to "Windows share"
In the window, fill in the following:
Server: myservershare (or whatever your servername is)
Share: (leave empty)
Folder: pub (or whatever folder you want it to start with)
User Name: (username for the share)
Domain name: (put whatever domain you are on if needed)
Tick "Add Bookmark" if you want to map it permanently, and give it a name, i.e. Pub drive (or whatever works for you).
Click "Connect" and enter your share password, tick "Remember forever" and then click "Connect" again!

Voila, the network share is now mapped!

---

### Post by ChTidio2 on 2009-04-03
Thanks, Odinb.  I must be doing something wrong...  I feel so dumb :-(

I tried what you suggested.  I am trying to access folders on an external USB drive connected to a windows XP system.  The name of the computer is bk2n. The name of the Sgare for the drive is mi44.  The XP box is part of a dimain caller clrhouse.  So this is what I did.

I chose "Places" >> "Connect to Server..."
I changed "Service type" to "Windows share"
In the window, I filled in the following:
Server: bk2n
Share: mi44
Folder: mdata
User Name: myuserName (for the share)
Domain name: clrhouse
I ticked "Add Bookmark" and gave it the name MyMI44
I clicked "Connect" and enter my share password, I ticked "Remember forever" and then clicked "Connect" again!

After a minute or so, I got the error message: 

Can't Display Location "smb://bk2n/mi44/mdata"  
Failed to mount Windows share.

Going nuts ovet this :-(

Chris

---

### Post by superprash2003 on 2009-04-04
try using ips instead of hostnames

---

### Post by ChTidio2 on 2009-04-04
Thanks, I tried that and the only difference was that now the error message read:

Can't Display Location "smb://192.131.2.113/mi44/mdata"
Failed to mount Windows share.

where 192.131.2.113 is the IP address of the Windows box I am trying to access.

Chris

---

### Post by BoogeyOfTheMan on 2009-04-04
Try [http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

I just used steps 2 and 3. It doesnt automount (thats next on my todo list), but its a good temp fix.

---

### Post by superprash2003 on 2009-04-05
i guess that a nautilus bug , try refreshing the page or opening it 2 or 3 times

---

### Post by ChTidio2 on 2009-04-06
Thanks BoogeyOfTheMan.  I thried that approach at home (no domain) and it appeared to work in accessing a Vista box in the workgroup, so I got all excited, thinking I had finally solved the problem.  Then, I tried it this morning on the LAN I really want to use it on and it did not work.

Ubuntu is running as a virtual macine, under Vista, so I even tried to access  the main Vista Drive (on the box ubuntu is running) and still no dice. 

I created a directory

mkdir ~myvistabox

I typed, 

sudo smbmount //192.131.1.20/Cdrive /home/myusername/myvistabox -o username=shareusername,password=sharepassword,uid=1000,mask=000

and I get 

"mount error 2 = No such file or directory"

Don't know which directory it's referring to, but I double/triple checked.  There is a Cdrive share on the vistabox and the username/password I used are correct.  There is also a myvistabox directorry off my username directory in the ububtu VM.

I am keeping careful notes of all these steps, to hopefully help the next new user avoid the mistakes I am making (once I find out what they are), because I'm sure I must be doing something wrong, only I can't figure out what.

Chris

---

