---
title: "&quot;Accidently&quot; installed edubuntu, want to revert to ubuntu 11.04"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by SIkelelaS on 2011-07-03
I am very much the absolute beginner having just installed ubuntu 11.04 onto a laptop just a few days ago.  I've loved doing it and am enjoying exploring this world.  

I was browsing the software centre and found edubuntu which looked great for our kids.  After restarting the computer for something else I found that it was now running as edubuntu rather than ubuntu.  

My preference would be to run ubuntu rather than edubuntu.  This may not be an issue and if so please feel free to say so.  Alternatively could someone explain how to revert to the standard ubuntu?

---

### Post by wolfen69 on 2011-07-03
Just do
```
sudo apt-get install ubuntu-desktop
```
then log out and select ubuntu desktop session.

---

### Post by createdcreature on 2011-07-03
Use command [FONT="Courier New"]sudo apt-get install ubuntu-desktop[/FONT], like they said. Or reinstall.

---

### Post by srisharan on 2011-07-03
Edbuntu runs with the Ubuntu desktop doesn't it?I thought it only has a few extra educational packages,so it should not matter

---

### Post by arochester on 2011-07-03
On the sign in page, where you put in your username and password, you should be able to choose "session". Choose Gnome.

To remove Edubuntu  altogether look at [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by SIkelelaS on 2011-07-03
Thanks everyone, that seemed to solve it.  

I still have the edubuntu screen at login with no option for a different session.  However the actual desktop has reverted back to what I wanted.

Thanks for taking the time to respond

---

### Post by wolfen69 on 2011-07-03
> **SIkelelaS said:**
> Thanks everyone, that seemed to solve it.  

I still have the edubuntu screen at login with no option for a different session.  However the actual desktop has reverted back to what I wanted.

Thanks for taking the time to respond

For future reference, at the login screen click your name first and then you will see the sessions at the bottom. Switch it there, then give your password.

---

