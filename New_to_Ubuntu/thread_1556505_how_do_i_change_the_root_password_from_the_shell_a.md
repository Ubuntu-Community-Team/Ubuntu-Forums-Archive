---
title: "how do i change the root password from the shell? and add guest account also??"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by bradmayne04 on 2010-08-19
Can't remember how to change the password for root access/ which is the same as login for me now when I boot this up.  I wanted to change my login and well as root on this machine since it's just at home and for other uses.  I also wanted to enable a simple guest account though too as well.  Can someone give me a quick walkthrough with the commands? thanx

---

### Post by mcduck on 2010-08-19
There really is no reason to enable the root account, and actually giving instructions for doing that is not allowed by the forum rules.

It only makes things more complicated, people tend to mess their systems doing that and in the end anybody who really might need to do that will already know how it's done.

What comes to guest account, if it's for random guests then have you tried the "guest session" from the user switcher applet in the top right corner of your desktop? That's far better than any normal guest account, as it's automatically erased after the guest logs out and created from scratch again when used. This makes sure that whatever the guest doesn't won't leave any remaining stuff on your system, which is good for you and the guest as well...

For any regular users you should probably just create their own normal user accounts instead.

---

### Post by ElNerdoDeGeek on 2010-08-19
re: the guest account, go to the user control in the System menu. You can add an account named "Guest" that doesn't have admin privileges and doesn't require a password very easily. =)

> **bradmayne04 said:**
> the same as login for me now when I boot this up.

I wanted to address this. I'm not 100% sure what you mean by that, but it sounds like you actually login as root, instead of as a user with administrative powers.

This is really, really dangerous. Running as root is the same thing as being administrator in Windows XP; it gives absolutely everything that you execute full, unfiltered access to the system. I assume you are running as root to give you the ability to do administrative tasks, but you don't need to run as root to do the occasional package installation and such.

When you login as an admin instead of root, it runs programs at basically the same level as a normal user. However, when something requests access to, or does something that requires, root privileges, you enter your password to temporarily elevate that single program's privileges. This is very easy to do, and much, much safer. There's no reason why you'd need to constantly run as root, it just shouldn't be done.

---

### Post by philinux on 2010-08-19
> **bradmayne04 said:**
> Can't remember how to change the password for root access/ which is the same as login for me now when I boot this up.  I wanted to change my login and well as root on this machine since it's just at home and for other uses.  I also wanted to enable a simple guest account though too as well.  Can someone give me a quick walkthrough with the commands? thanx

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

---

### Post by bradmayne04 on 2010-08-29
> **ElNerdoDeGeek said:**
> re: the guest account, go to the user control in the System menu. You can add an account named "Guest" that doesn't have admin privileges and doesn't require a password very easily. =)



I wanted to address this. I'm not 100% sure what you mean by that, but it sounds like you actually login as root, instead of as a user with administrative powers.

This is really, really dangerous. Running as root is the same thing as being administrator in Windows XP; it gives absolutely everything that you execute full, unfiltered access to the system. I assume you are running as root to give you the ability to do administrative tasks, but you don't need to run as root to do the occasional package installation and such.

When you login as an admin instead of root, it runs programs at basically the same level as a normal user. However, when something requests access to, or does something that requires, root privileges, you enter your password to temporarily elevate that single program's privileges. This is very easy to do, and much, much safer. There's no reason why you'd need to constantly run as root, it just shouldn't be done.

I must not have explained myself properly.  Please allow me to clarify.  Right now I only have one account on this linux box.  (which is mine)  My login password is also the password I use when i need to either sudo or to update or anything else where I am prompted for a password for "administrative tasks".  I don't want a root account.  I know the inherent risks.  What I wanted to do was to change my login password.  I was wondering if that if I change my login password will that automatically change my password when I am asked for a password when i need to run a program as root (example- nmap, where nmap will tell you that root privileges are needed for nmap to run correctly) and if not how would i change that password for sudo and "administrative tasks".  
Also, about the guest account.  I want to enable a "normal" account for other users.  I mistakenly used the term "guest" before.  I have to work on my terminology LOL.  Thanks for taking the time to read this after I clarified this thread.

---

### Post by mcduck on 2010-08-29
The password you are asked for admin tasks is exactly the same password you use to login, so yes, if you change your login password then that's the password used for admin tasks as well.

You can add new user accounts in System/Administration/Users and Groups. Note that by default the new user accounts will be unprivileged, normal user accounts, so if you want to give somebody admin rights you need to do it manually. The Advanced-button in Users and Groups gives you access to such options.

---

