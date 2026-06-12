---
title: "Allow Local System Administrator Login??"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by Goldline on 2009-11-12
Does this option still exist, see screenshot below for clarification:

[IMG]http://31mjaa.bay.livefilestore.com/y1pjngthxvtXIkx2OWAoe9Y3jdgUeNioaMgraJ2sdz5vyAc8X80snXgmCi-AntxMevkYO2I1DPGsOZpNEOeGe2Ju3WQb-Aw99d_/root_3.jpg[/IMG]

---

### Post by philinux on 2009-11-12
Not in Karmic. The new GDM has no gui to configure it as yet.

---

### Post by Goldline on 2009-11-12
Can it be accomplished by using commands or would that be difficult 
to achieve ?

---

### Post by philinux on 2009-11-12
> **Goldline said:**
> Can it be accomplished by using commands or would that be difficult 
to achieve ?

The new login window can only really be configured cosmetically at the moment anyway. Thats it. Totally different. Have a search of the old karmic development forum.

---

### Post by aBaldrich on 2009-11-12
If you are an absolute beginner you should not log in as an administrator. There is *nothing  *you can't do as a normal user (unless you were a linux guru). And you could waste the entire OS by mistake.
Also according to [this thread]("http://ubuntuforums.org/showthread.php?t=716201") we should not give assitance for root graphical login on the ubuntu forums.

---

### Post by Goldline on 2009-11-14
Okay but atleast can someone tell me if and when the GUI is going to get updated
officially with the update manager to allow local system administrator login ?
Is there an ETA!? Or could it be anywhere between a few weeks to afew months ?

---

### Post by tnsmart on 2009-11-29
Check this out:

[http://www.linuxreaders.com/2009/10/29/root-login-on-ubuntu-9-10/](http://www.linuxreaders.com/2009/10/29/root-login-on-ubuntu-9-10/)

---

### Post by Pritamsng on 2010-02-10
> **tnsmart said:**
> Check this out:

[http://www.linuxreaders.com/2009/10/29/root-login-on-ubuntu-9-10/](http://www.linuxreaders.com/2009/10/29/root-login-on-ubuntu-9-10/)
sorry tsnmart, people are asking about GUI login as ROOT,
the old version then 9.4. It was possible in GUI system>administration>login. in 9.4 it have different window, where security tab is not prisent but still we can modify it in the file /etc/gdm/gdm.conf. 
But in 9.10. gdm.conf file itself not there. i think it is not possible. 
if any one know it. then please reply.

---

### Post by Pritamsng on 2010-02-10
He here the solution...
 
at the time of login...
just click on other 
write the user name root.
give the password if you activate it as "sudo passwd root" or sudo -i (give your user passwd) then change your root password "passwd" . log out then try to log in as root by clicking other.
 
hope..... security for local system administor is not present in 9.10.

---

