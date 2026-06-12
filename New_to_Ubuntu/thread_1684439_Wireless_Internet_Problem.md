---
title: "Wireless Internet Problem"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by petronell on 2011-02-09
Hi I have installed xubuntu 10.10 on an old Fujitsu S6120, and the internal wireless card seems to be identified, and is connecting to a couple of wifi networks fine.

When I try to connect to my wifi network though it just refuses and after about 20 seconds asks for the password again (like I have got the password wrong), there are a number of windows pc's connecting to the network fine.

Stumped - anyone got any ideas?

PS I know I have entered the correct password...

---

### Post by [Snc] on 2011-02-09
Is it a DHCP network or do you have to enter your IP settings manually?

---

### Post by petronell on 2011-02-09
All three networks use DHCP to issue IP addresses.

---

### Post by petronell on 2011-02-09
Just to add I have looked at the router's logs and it doesn't look like the laptop is getting to the point of asking for an ip address from it?

---

### Post by whatthefunk on 2011-02-09
Sounds like a Network Manager problem.  My god is that program worthless.  Try Wicd network manager.

---

### Post by petronell on 2011-02-09
Thanks for your reply. I'm now even more confused! I have installed wicd and it returns an error saying bad password.

But I have double and treble checked the password, and had someone else check the password and it is correct.

How is linux changing the password between what is typed in and what hits the router for authentication?

---

### Post by wep940 on 2011-02-09
First, go to network manager (or wicd I guess in your case now, if it has the same functionality) and edit any existing connection and delete it.  I know with network manager if you set up a connection incorrectly, it is still a known connection with the bad information so you have to delete it first before you'll ever get another good connection.
 
Second, be absolutely positive you enter the password correctly - I can't tell you how many times I've been setting up a PC on someone's network and could swear I got the password correct only to find I didn't.  When using network manager, I believe there is a check box beneath the password entry fields the you can check so you can see the password instead of "*"'s.
 
Third, if you have MAC filtering on the router, be sure the PC's MAC is in the allowed list on the router.

---

### Post by crf on 2011-02-10
You could try entering your password as hex codes.

---

### Post by whatthefunk on 2011-02-10
You need to remove Network manager and restart Wicd

```
sudo apt-get remove network-manager
```

```
sudo /etc/init.d/wicd restart
```

---

### Post by wep940 on 2011-02-10
It used to be if you installed wicd, network manager was deleted by default.  Not knowing wicd, I still think it would be wise to flush any information it is keeping regarding the connection.  They need to start with a clean slate.

---

### Post by whatthefunk on 2011-02-10
I might get rid of part of it, but not all of it.  It still tries to control things and gets in the way.

---

