---
title: "Connecting to Ubuntu from my Windows XP machine"
date: 2007-04-04
forum: Networking &amp; Wireless
---

### Post by jamrock on 2007-04-04
I installed Ubuntu for the first time on a spare PC last week.
I can see my Windows PC from my Ubuntu machine. This includes viewing windows folders and files. I use a LAN connection not Wireless.

When I am on my Windows PC, I am able to see my Ubuntu machine in Windows "My Network Places".  When I try to view data on the Ubuntu machine, I am prompted to enter my "User Name" and "Password". I then enter the user name and password that I would use to log onto my ubuntu machine.  However, I am unable to connect.

Would appreciate your help and advice.  Please keep in mind that I am new to Linux / Ubuntu.  Although technically inclined, I am not a real techie. 

Thanks in advane.

---

### Post by Brind'Amour on 2007-04-06
I have been having the same problem. 

I just upgraded to version 6.10 (clean install), and have set up my shares very similar to what they were before. Now I can see, from the Windows XP machines the Ubuntu machine but it wont accept any username/password combination I try. I can see the Windows machines from the Ubuntu machines though. I believe that I have all the share settings correct.

Any help please?
Thanks...

---

### Post by Brind'Amour on 2007-04-06
Ummmmm.....](*,) \\:D/ :-({|= 

Finally found the answer, may help you jamrock.

I had to create a samba user and set a password:
sudo smbpasswd -a *username*

and enter a passward when prompted. I then used these details to access the Ubuntu machine from my Windows XP computer. I had to use as the *username* the pre-existing system username.

I hope this helps you.

---

### Post by GQed76 on 2007-04-06
is there away for there not to be a password/username required?

---

### Post by Grampy on 2007-04-07
This is a great thread, answered my windows <> Ubuntu file sharing questions.
 
The ubuntu group should really make this type of information clear for new users.

---

### Post by jamrock on 2007-04-13
Hi Brind'Amour,
thanks very much for replying. A couple of questions to clarify:
(1) I am assuming that I do this on the Linux machine.
(2) I am also assuming that I do this via the "terminal".

---

### Post by jamrock on 2007-04-13
I did try Brind'Amour suggestion re setting up a samba userid and password and it worked.

Thanks again Brind'Amour.  Much appreciated.

---

### Post by wpqc213 on 2007-11-01
New user here too. I cant connect from any of my WIN XP pro stations to my Ubuntu stations. I did get a SAMBA password set but I am not 100% sure I was correct on the user name as I am using the same as my login.

Please refresh my memory..

Thanks!

Wayne

---

### Post by Bob1275 on 2007-11-01
Hi Wayne, I'm a fairly new user also; but actually you do need to set up a totally separate user on your ubuntu machine and use this to log on from your xp machines. In other words if you're logged in as "Wayne" on the ubuntu machine, you'll need to log on as a separate user from the xp side.

ex. first create user Wayne2 on ubuntu machine then from terminal:

sudo smbpasswd -a wayne2
it'll ask for your password for Wayne to administer, then ask for your wayne2 password twice.
You may need to reboot on the xp side

Then you should be good to go!

---

### Post by wpqc213 on 2007-11-02
Thanks for the help Bob!!

Still hacking away here with this problem. I have tried this before and for some reason it always tells me "Unable to modify password entry for wayne 2
I get the first shot at entering the password fine but past that it's over:lolflag:

Thanks for any help and ideas!

Wayne



> **Bob1275 said:**
> Hi Wayne, I'm a fairly new user also; but actually you do need to set up a totally separate user on your ubuntu machine and use this to log on from your xp machines. In other words if you're logged in as "Wayne" on the ubuntu machine, you'll need to log on as a separate user from the xp side.

ex. first create user Wayne2 on ubuntu machine then from terminal:

sudo smbpasswd -a wayne2
it'll ask for your password for Wayne to administer, then ask for your wayne2 password twice.
You may need to reboot on the xp side

Then you should be good to go!

---

### Post by wpqc213 on 2007-11-02
Disregard the last cry for help.. I went back and reworked my passwords and re entered the entry per Bob's suggestion and it is up and running:)

Thanks for the help!!

WT

---

