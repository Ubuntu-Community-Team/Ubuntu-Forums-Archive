---
title: "Simply cannot get networking to work on Ubuntu 8.04"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by tehsnipes on 2008-11-17
Hello,

I recently installed Intrepid on my dv2000 after a long hiatus from Linux and it was a disaster. Hardy took a lot of modifying but I managed to get almost everything working. One is the networking. I tried everything on this forum, I've browsed 100's of threads and it's really frustrating. The problem is that I cannot cannot connect to windows shares from my HP Dv2000 w/ Broadcom 4311 wireless. I tried everything such as editing smb.conf, reinstalling samba. I couldn't even connect to it in intrepid but now I can. The only problem is that I keep getting plagued by password requests. Even though I enter in the properly configured username and password it doesn't work. I press cancel and get the > Cannot diplay smb://desktop/files

Error: Failed to mount Windows share
Please select another viewer and try again.

PLease help. What I don't understand is why the developers changed the networking from gutsy. My laptop ran gutsy and everything worked flawlessly. Networking was incredible and intuitive and is one of the core reasons for which I chose to install Linux. This is quite frustrating and disappointing :(


****EDIT****
Yes they can ping each other. I tried.

---

### Post by cariboo on 2008-11-18
Have you created an smbpasswd for your user name?

Jim

---

### Post by tehsnipes on 2008-11-18
> **cariboo907 said:**
> Have you created an smbpasswd for your user name?

Jim

yes I have I ran the 


sudo smbpasswd -L -a 
       and 
sudo smbpasswd -L -e  

and got the output that the user was enabled.

---

### Post by tehsnipes on 2008-11-19
*bump*

still no progress. I keep getting the password dialog but cannot connect even though I provide the correct password. When I press cancel I get a 

> Couldn't display "smb://desktop/files/"
Error: Failed to mount Windows share
Please select another viewer and try again.

---

### Post by superprash2003 on 2008-11-20
you dont need to install samba if you are accessing a windows share.. is this windows share accessible from another windows pc?

---

