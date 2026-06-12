---
title: "unable to write to samba share from windows 10"
date: 2019-08-08
forum: Networking &amp; Wireless
---

### Post by kalyori on 2019-08-08
I've set ubuntu 19.04 up on my laptop and I followed this [guide]("https://tutorials.ubuntu.com/tutorial/install-and-configure-samba#2") to install SAMBA (4.0.10 I think) as I want to share files locally between my Mac and PC.

I have created a shared folder called "sambashare" and on Windows 10 I have added a network location for sambashare (laptop-ip/sambashare).
I now see the network location "samba" in "This PC". I logged in with the username and password I set for samba.

It opens the folder when I click it but when I try to create a folder it says I need permission.

Does anyone know what I might've done wrong here?

Appreciate any help, thanks!

---

### Post by Morbius1 on 2019-08-08
The share definition allows write access to anyone with the proper credentials but there is no mention in that guide that states you must alter the Linux permissions on that folder to allow it.

So the way it is set up currently anyone with credentials can have read only access to the share but only "username" can write unless you modify Linux permissions or change the share definition. Are you logging in with "username" or with another user name.

---

### Post by kalyori on 2019-08-08
Thanks for your response.

This is for a home network so I don't think I need to worry about security. Anyone on the network can access the folder.
Would you recommend credentials or altering the Linux permissions on that folder? What's the best course of action for my use?

So let's say my username is "myuser" and let's say my computer password is "mypass".
I followed this step:

sudo sambapass -a myuser

So I should log in on Windows with "myuser" and "sambapass".

Another thing to note is I can't write to the directory from the laptop itself. I also get access denied (probably because I'm not logged in with "sambapass" but "mypass" and I'm not sure what to do about that.

**EDIT**: I've been trying various things online. This is my current config:

comment=Samba on Ubuntu
create mask = 0777
directory mask = 0777
force user = myuser
guest ok = yes
read only = no
write list = myuser
guest account = myuser
available = yes
writable = yes
browsable = yes

Proceeded to restart computer. Still unable to write to this folder from ubuntu or from Windows 10. I re-added the network location in Windows 10, but was not prompted for a password this time.

**EDIT 2:**I used chmod to make the directory permissions 777 and now everything is working.

---

