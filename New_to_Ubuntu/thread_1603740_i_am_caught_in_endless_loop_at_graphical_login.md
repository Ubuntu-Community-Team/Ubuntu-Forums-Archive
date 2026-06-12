---
title: "i am caught in endless loop at graphical login"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by kimsia on 2010-10-23
Hi all, 

this is what i did earlier today:

1) removed 4-5 older kernels to save disk space.

2) installed git and modifed the PATH in .profile

subsequently when i reboot my computer. i cannot login . if  i type correct password, i will go into a black screen and then go back to the login screen again. if i type wrong password, i will of course be prompted for wrong authentication.

i tried asking for help for 5 hours in irc channel.

i have done the following:
1) add new user by going in as recovery mode root  the newuser too faced the same problems.

2) at the graphical login i tried ctrl alt F1 and i get a list of messages telling me that sudo , etc commands are not located because /bin or /usr/bin are not located on PATH.

i am not sure what i did wrong. 

i am loathed to reinstall.

all i want is to regain control of my user access.

i swear i will never touch kernels again.

Please help.

This is my working laptop and i am a lone ranger with no technical knowledge. i have access to a server only via this laptop. i will not know how to regain ssh access to my server if i need to format this laptop.

i am supposed to be working today instead of spending time like this. so please help.

any help is greatly appreciated.

---

### Post by kimsia on 2010-10-23
fix by fixing path in .profile and etc/environment 

remember to do a source ~/.profile and source /etc/envrionment after making changes

---

### Post by AngusH on 2010-10-23
> **kimsia said:**
> fix by fixing path in .profile and etc/environment 

remember to do a source ~/.profile and source /etc/envrionment after making changes

Are you saying you fixed the problem? If so please mark this thread solved (it's in thread tools at the top), if not try dropping to a root shell at boot and removing the changes you made to the path.
Angus

---

