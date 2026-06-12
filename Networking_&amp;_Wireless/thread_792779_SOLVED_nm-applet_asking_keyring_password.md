---
title: "SOLVED: nm-applet asking keyring password"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by patjlm on 2008-05-13
Hello,

Using XUbuntu 8.04, I had nm-applet asking me for the keyring password at each logon.

I saw many threads about this topic. Most of them gave the libpam-keyring (or libpam-gnome-keyring) solution. But I could not make this work with the autologin on.

I found a solution that may be useful to you: use manual configuration in nm-applet (no roaming). It seems that when using a manual configuration, nothing is stored in the keyring and the system is not asking for any password. libpam-gnome-keyring is not required anymore (I removed it...).

I hope this can help others...

---

### Post by bford16 on 2008-06-21
I don't think this thread should be marked, "Solved." For one thing, your results are different from mine. I have two machines with Xubuntu 8.04. One is a PIII with the i386 version; the other is an AMD Turion with the 64-bit version. Both systems kept prompting for the password, but in both cases, installing the libpam-gnome-keyring package solved the problem. Both had at least kernel 2.6.24-18.

On the x64 machine, the keyring password prompt simply stopped appearing. On the i386, there was a checkbox on the prompt to "always unlock" the keyring on login.  Perhaps there is a difference in the i386 and x64 packages?

So I think there may be some flakiness in the implementation of libpam-gnome-keyring. Or maybe there are undeclared dependencies or something...

---

### Post by nickdbliss on 2008-06-21
It stopped automatically with mine as well buddy. Cheers

---

### Post by daqron on 2010-12-08
I had the same issue. Network Manager was asking for a keyring password every time I boot (with autologin). Fixed on Xubuntu 10.10 as follows:

[LIST]
[*]Open network manager (right click on the wifi icon and select "Edit Connections")
[*]Go to the Wireless tab; click connection name; click Edit
[*]Check "Available to all users" at the bottom
[*]Apply, close
[/LIST]

---

### Post by grahammechanical on 2010-12-08
This happens when you set the system to have automatic login. It is a security feature. It does not happen when you set the system to require a password at login. The advice given by daqron is correct. It is the way around this. It is fine if you are the only user but it is not secure if you want to restrict access to the Internet to certain users.

Regards

---

### Post by daqron on 2010-12-09
> **grahammechanical said:**
> It is fine if you are the only user but it is not secure if you want to restrict access to the Internet to certain users.
Agreed. I only did this because it's a single-user laptop that never leaves the house and wouldn't give up any big secrets if it got totally haxored by wikileaks.

---

