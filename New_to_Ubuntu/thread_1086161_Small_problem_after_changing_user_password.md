---
title: "Small problem after changing user password"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by llogan on 2009-03-03
Hi,

I've been running Intrepid successfully for about two months now.  I have just one user account in addition to the root account.  Just recently I changed my user account password and everything almost works fine.  

The small problem is that when the gnome desktop opens, a dialogue box opens that says,

 "The app 'Network Manager Applet' (/usr/bin/nm-applet) wants access to the default keyring but it is locked" 

and prompts me for my password.  I put my new user account password in and it rejects it, but when I put my old password in I am allowed to access my wireless connection. This never used to happen before I changed my user password.  Now I effectively need two passwords to get on to the internet, one to log on to the system and the other to gain access to my wireless connection.  Network Manager is the only applet that accepts my old password. What did I do wrong?

Any suggestions or advice?

Thanks

---

### Post by kevin11951 on 2009-03-03
> **llogan said:**
> Hi,

I've been running Intrepid successfully for about two months now.  I have just one user account in addition to the root account.  Just recently I changed my user account password and everything almost works fine.  

The small problem is that when the gnome desktop opens, a dialogue box opens that says,

 "The app 'Network Manager Applet' (/usr/bin/nm-applet) wants access to the default keyring but it is locked" 

and prompts me for my password.  I put my new user account password in and it rejects it, but when I put my old password in I am allowed to access my wireless connection. This never used to happen before I changed my user password.  Now I effectively need two passwords to get on to the internet, one to log on to the system and the other to gain access to my wireless connection.  Network Manager is the only applet that accepts my old password. What did I do wrong?

Any suggestions or advice?

Thanks

thats weird,  nm-applet stores separate data for each user, and one users password should not affect the other.

---

### Post by stoogiebuncho on 2009-03-03
I think this is a fairly common problem, unfortunately.  There isn't really an easy way to change the keyring password built into Ubuntu, so you'll have to install another piece of software: [Seahorse]("apt:seahorse")

```

sudo apt-get install seahorse
```

When it has installed you can open it up and go to Edit > Preferences.  It has (among other things) a section devoted to the Gnome keyring.  You should be able to change your password there.

---

### Post by asmoore82 on 2009-03-03
^^ the above post is on the right track but seahorse is definitely in a 8.04 default install ...

you should be able to get there by simply "System -> Preferences -> Encryption and Keyrings"

---

### Post by Lazy-buntu on 2009-03-22
I'm having the same problem, going to System>Preferences>Password and Encryption doesn't lead anywhere useful.

---

### Post by Lazy-buntu on 2009-03-22
Found the answer I think. In Intrepid, you have to go to Applications>Accessories>Passwords and Encryption Keys

Go to something like the unlock password, change it. Put in your old password and then put in the new one your replaced it with in your account info.

---

