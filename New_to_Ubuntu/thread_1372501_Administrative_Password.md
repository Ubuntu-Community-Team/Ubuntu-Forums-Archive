---
title: "Administrative Password"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by JupiterMike on 2010-01-04
I finally have Karmic Koala install stand alone(no windows) on my laptop. Some areas I attempt to enter (eg-Synaptic Package Manager/Update Manager) ask for a password. "Enter your password to perform administrative tasks".  What password is it asking for and how do I establish one?  I,ve tried all the passwords I used when installing Ubuntu Karmic Koala and none work.  I,m learning as I go along

---

### Post by lotharmat on 2010-01-04
> **JupiterMike said:**
> I finally have Karmic Koala install stand alone(no windows) on my laptop. Some areas I attempt to enter (eg-Synaptic Package Manager/Update Manager) ask for a password. "Enter your password to perform administrative tasks".  What password is it asking for and how do I establish one?  I,ve tried all the passwords I used when installing Ubuntu Karmic Koala and none work.  I,m learning as I go along

Really dumb question... but... are you sure that caps lock is not on?

---

### Post by J V on 2010-01-04
Yes, its the same password you use to log in, if you don't know it synaptic will be the least of your worries...

---

### Post by lotharmat on 2010-01-04
> **J V said:**
> Yes, its the same password you use to log in, if you don't know it synaptic will be the least of your worries...


Is it possible to install ubuntu with no password?

---

### Post by bodhi.zazen on 2010-01-04
> **lotharmat said:**
> Is it possible to install ubuntu with no password?

No, but you can change to an empty password post install.

---

### Post by danbicknell on 2011-05-08
Just wondering if you found a solution to you problem as I am experiencing similar issues.

I recently upgraded to 11.04 server, then installed the desktop on top of that.  I can use the administrative password successfully almost everywhere except with Update Manager and Synaptic Package Manager - where it completely refuses my login.  

I'm wondering if, because I added the desktop after installing the server, that it might be looking for a password file that was never generated?

---

### Post by collisionystm on 2011-05-08
> **danbicknell said:**
> Just wondering if you found a solution to you problem as I am experiencing similar issues.

I recently upgraded to 11.04 server, then installed the desktop on top of that.  I can use the administrative password successfully almost everywhere except with Update Manager and Synaptic Package Manager - where it completely refuses my login.  

I'm wondering if, because I added the desktop after installing the server, that it might be looking for a password file that was never generated?


The 'desktop' is just a GUI. It creates no password files. Can you open a terminal and act as sudo? Do this

```

sudo passwd username

```

Now try your new password and see if it works.

I never think installing a GUI on top of server is a good idea. You may as well just install ubuntu desktop from the start. There is no difference between the 2. They both share the same software and capability's.

---

### Post by Muhnamana on 2012-01-31
Im experiencing the same issue. I'm trying to run the Samba gui program and it keeps asking for the administrative password. Well I keep entering it correctly and refuses it each time. And no, the CAPS lock is not on.

I've done the following and changed my original password during install to something simple and easy:
```

sudo passwd username

```But I can do the following with the new password:
```

sudo gedit /etc/samba/smb.conf

```I've run into this with other programs and had to start them via the terminal.

What am I not doing correctly?

---

