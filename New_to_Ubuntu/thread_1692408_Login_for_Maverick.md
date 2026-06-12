---
title: "Login for Maverick"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by CompBio on 2011-02-21
I've been reading the threads on the Maverick keyring login, but I'm still confused by my system's behavior.

My wireless router has a password, AAAAA (obviously not the real one).  My login password is BBBBB.  In my System -> Administration -> Users and Groups settings, I have it set to Password: ask on login.

Ok, so when I boot, I never see a login screen.  Instead I get my desktop and a dialog that asks for a Keyring password.  I thought this was due to the mismatch between my router password and my user password.  But the password it's looking for is BBBBB, which I would expect to get on a login screen.

It's not really a big deal, but it seems weird to me that anyone could boot my laptop and see what's on my desktop without knowing my password.  Is there a way for me to get a more traditional login screen?

---

### Post by Thijk on 2011-02-21
You should also go to System -> Administration -> Login screen and select ***show the screen for choosing who will log in***. Then you'll get a login screen where you choose the right account and you'll have to enter your password

You probably have the ***log in as ... automatically*** option now

---

### Post by CompBio on 2011-02-22
> **Thijk said:**
> You should also go to System -> Administration -> Login screen and select ***show the screen for choosing who will log in***. Then you'll get a login screen where you choose the right account and you'll have to enter your password

You probably have the ***log in as ... automatically*** option now

Thanks!

Just when I thought I was no longer a newbie...

---

### Post by CompBio on 2011-02-23
Aak!  I didn't reboot until this morning and now I can't log in!!  I'm currently running off my old 10.04 install CD (not the fastest option).

What happens now is I get the login screen, but when I click on my username or hit <Return> the dialog just flickers.  I don't get an opportunity to enter my password.

How can I login now??

---

### Post by CompBio on 2011-02-23
Ok, after perusing a number of posts, I figured out how to get back to my old settings:

Ctrl-Alt-F1
Login as myself
sudo vi /etc/gdm/custom.conf

This is what I found:

> AutomaticLoginEnable=false
AutomaticLogin=compbio
TimedLoginEnable=false
TimedLogin=compbio
TimedLoginDelay=10
DefaultSession=gnome

So I changed it to:

"AutomaticLoginEnable=true"

And rebooted.  Now I'm back to the way it was (no login splash screen, enter keyring password).  So now I can work, but I'd still like to know the correct settings to get a proper login splash screen. 

Can anyone share their .conf file for a working splash screen?

---

### Post by Thijk on 2011-02-24
my .conf file is the same and I don't have that problem.

So the problem must be elsewhere, but I'm afraid I don't know where...

---

