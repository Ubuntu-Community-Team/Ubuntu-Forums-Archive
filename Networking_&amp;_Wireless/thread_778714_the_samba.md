---
title: "the samba"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by evilbuntu on 2008-05-02
Hi folks

I was setting up my samba to windows yesterday and was having an issue
I set everything upin webmin
My server can see and access on my win workgroup shares but not vise verse. When I go to enter the name and pass on the win xp user machine it won't accept it just keeps repopping the window up repeatedly and placing my hostname before the user name such as

Hostname/user
password

I have tried convrting unix to samba users but it never gives me confirmation, it just says converting for hours 

Am I forgetting something on the win end

Thanks a bunch
running server 7.10 and webmin

---

### Post by sisco311 on 2008-05-02
Did you set up a samba password for your user?
```
sudo smbpasswd -a <username>
```

<username>  = your user name or any other user on your Ubuntu box.

---

### Post by njparton on 2008-05-02
Workgroup, usernames and passwords must all be the same (and linux is case sensitive remember).
 
If that doesn't work, post your /etc/samba/smb.conf file.

---

### Post by evilbuntu on 2008-05-02
I am just using my Linux user prmissions such which I use for my FTP access in
users and groups, I thought that was why I was doing the webmin convert

So do I have to go somewhere and make one group for samba all with one password?
I'm at work so I will put my cfg file up tonigt if it helps
I was using webmin to avoid editing files but I'm not afraid to edit if it needs to be done

Why would I be able to access my user shares from. My server but not the server shares from the user
I've evn tried using my hostname user and pass but it wont let me in

Hmmmmm

Thanks so much for the fast replies

---

### Post by njparton on 2008-05-02
Every windows user needs to have a linux account of the _same_ name followed by the smbpasswd command to set a password as posted above. Make this password the same as in windows for simplicity.

---

### Post by evilbuntu on 2008-05-02
Do I set that name and pass in ubuntu users and groups, or in webmin 
Also when you say their username and pass has to be the same do you mean the specific computers name, their windows login name/ pass or the user in my ubuntus users and groups

Also what is the convert unix to samba in webmin because I thought that was for taking my serves permissioned users and setting them up as samba users

I am entering their user name and pass from my server

Does that mean I have to make a user on m samba the same as the windows username and pass?

---

### Post by njparton on 2008-05-03
Yes, all USERS must be the same names and passwords in windows, linux and samba.

---

### Post by evilbuntu on 2008-05-03
> **njparton said:**
> Yes, all USERS must be the same names and passwords in windows, linux and samba.

so what I will do when I get home is if i have an xp computer in the next room of my house called "Marc" and the password is "123456" then i go to my user and groups in ubuntu and create a user marc with a pass 123456 and convert the unix to samaba and that should work?

thanks guys

p.s. pertaining to the xp computer is the actual user login and pass what needs to be the same or the acutal computers name and a network pass?

---

### Post by njparton on 2008-05-03
No! _M_arc and _m_arc are not the same.

---

### Post by Iowan on 2008-05-03
There IS a way to map (nonmatching) usernames from Windows to Linux/Samba - I've been looking for it, but can't locate it just now.

---

### Post by evilbuntu on 2008-05-04
> **njparton said:**
> No! _M_arc and _m_arc are not the same.

LOL funny

But again is it the xp user and pass that is the same?
I will try that as I have not been home

Thanks everyone, i will put thanks for everyone once this is done

---

### Post by njparton on 2008-05-05
I still don't quite know what you're talking about :)

Linux username = windows username

linux password = windows password

It's a simple as that.  We seem to be going round in circles here - just make every corresponding detail match.

---

