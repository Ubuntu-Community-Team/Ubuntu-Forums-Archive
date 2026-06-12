---
title: "Enter password for default keyring to unlock"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by groeswenphil on 2009-04-13
This message keeps popping up at start up. There must be a way to avoid it?

Phil

---

### Post by jhenager on 2009-04-13
I saw this other link:
[http://ubuntuforums.org/showthread.php?t=192281&highlight=GNOME+session](http://ubuntuforums.org/showthread.php?t=192281&highlight=GNOME+session)
and it seemed to help someone else. Try the steps listed there. Hope it helps.

---

### Post by Mortus Pryde on 2009-04-13
Oh good, this was one of the questions I was about to ask. Will check out the link when I get home. I just got ThinkFinger to work on my IBM T42, so I was thinking it may have something to do with that, a step missed or something. Will definately have a look.

---

### Post by lovinglinux on 2009-04-13
> **jhenager said:**
> I saw this other link:
[http://ubuntuforums.org/showthread.php?t=192281&highlight=GNOME+session](http://ubuntuforums.org/showthread.php?t=192281&highlight=GNOME+session)
and it seemed to help someone else. Try the steps listed there. Hope it helps.

That thread is 3 years old and provides a complicated solution. I wouldn't recommend following it.

This issue with the keyring is probably due to auto-login or because you changed passwords recently. 

Follow the instructions below:

> **mcduck said:**
> 
Changing/removing the keyring password is quite easy to do (no need to remove the current keyring or mess with user accounts):

1. open the keyring manager (Applications/Accessories/Passwords and Encryption Keys)

2. Go to Edit/Preferences

3. On the Password Keyrings-tab select the "login"-keyring & click "Change Unlock Password"

Now you can change the keyring password. If you use normal login set the password to same as your login password is to unlock the keyring automatically. If you use automatic login leave the new password fields empty to remove the keyring password.

---

### Post by Mortus Pryde on 2009-04-13
Thanks LovingLinux. Always nice to know how to do things the easy way before doing it the hard way. ;)

---

### Post by Zaizeku on 2009-04-14
> **lovinglinux said:**
> That thread is 3 years old and provides a complicated solution. I wouldn't recommend following it.

This issue with the keyring is probably due to auto-login or because you changed passwords recently. 

Follow the instructions below:

When I follow your instructions, there is no "login"-keyring there is only one that says default...

---

### Post by mcduck on 2009-04-14
> **Zaizeku said:**
> When I follow your instructions, there is no "login"-keyring there is only one that says default...

Are you *absolutely* sure that you are in the Keyring Manager's *preferences*-window?

---

### Post by Zaizeku on 2009-04-14
> **mcduck said:**
> Are you *absolutely* sure that you are in the Keyring Manager's *preferences*-window?

yes

In my other computer the login keyring appears... but for some reason it does not appear here, when I installed it I enabled the autologin from the same installation so does that alter this in any way? I guess so...

---

### Post by mcduck on 2009-04-14
> **Zaizeku said:**
> yes

In my other computer the login keyring appears... but for some reason it does not appear here, when I installed it I enabled the autologin from the same installation so does that alter this in any way? I guess so...

In that case check if the only keyring you have, "default" has a password.

If keyring manager asks for password to open a keyring, and you only have that one keyring, it must be the one that needs the password.. ;)

---

### Post by Zaizeku on 2009-04-14
> **mcduck said:**
> In that case check if the only keyring you have, "default" has a password.

If keyring manager asks for password to open a keyring, and you only have that one keyring, it must be the one that needs the password.. ;)

Yes that did it, thanks lovinglinux and mcduck :)

---

### Post by molder on 2009-04-15
What package do I need to add the Passwords and Encryption application?

---

### Post by mcduck on 2009-04-16
> **molder said:**
> What package do I need to add the Passwords and Encryption application?

It should be installed by default in Gnome, but in case you need it for some other DE the program is called "Seahorse".

---

### Post by raintheory on 2009-05-28
I've got this same issue...   sorta.  The steps here have not resolved it.

I get a message saying /usr/bin/mono can't access the default keyring because it is locked..

This just started happening after I installed thinkfinger on my Thinkpad T61 (which works great otherwise, I love it).  It's just that it kinda defeats the purpose of not having to type my password at login if I have to type it at the desktop for this message :(   It's great for the terminal and other password prompts though.

Any Ideas?  Let me know if you need any additional info!

EDIT: nm, I got it goin.  :)

-aA

---

### Post by labinnsw on 2010-05-12
Has any body worked out how to do this in Lucid yet? (Please note not talking about Karmic or any earlier releases.) As well as reading this thread, I have tried the links listed below.

[http://johnny.chadda.se/article/unlock-the-gnome-keyring-upon-login/](http://johnny.chadda.se/article/unlock-the-gnome-keyring-upon-login/)
[http://live.gnome.org/GnomeKeyring/Pam](http://live.gnome.org/GnomeKeyring/Pam)
[http://maketecheasier.com/auto-unlock-keyring-manager-in-ubuntu-intrepid/2009/03/14](http://maketecheasier.com/auto-unlock-keyring-manager-in-ubuntu-intrepid/2009/03/14)
[http://superuser.com/questions/43132/ubuntu-enter-password-for-default-keyring-to-unlock](http://superuser.com/questions/43132/ubuntu-enter-password-for-default-keyring-to-unlock)
[http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/](http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/)
[http://ubuntuforums.org/showthread.php?t=1124679](http://ubuntuforums.org/showthread.php?t=1124679)
[http://www.ubuntuupdates.org/packages/show/164566](http://www.ubuntuupdates.org/packages/show/164566)
[https://bugs.launchpad.net/bugs/557906](https://bugs.launchpad.net/bugs/557906)
[https://code.launchpad.net/~ubuntu-branches/ubuntu/lucid/gnome-keyring/lucid](https://code.launchpad.net/~ubuntu-branches/ubuntu/lucid/gnome-keyring/lucid)

They do not work because the tabs and views referred to are not present in Lucid, which leaves me guessing what to edit.

---

### Post by labinnsw on 2010-05-13
I am still trying to figure this out just in case anyone knows how and cares to help.

I have installed libpam-keyring based on [this link]("http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/").

I have configured up to just before > Options of the PAM module [from this link.]("http://live.gnome.org/GnomeKeyring/Pam")

(I am unable to understand the rest. Would appreciate if someone could translate that to human for me.) 

I rebooted and there is no change.

I am going to double check what I have done and reboot again.

---

### Post by labinnsw on 2010-05-13
After rebooting, there is no change. I have attached my "/etc/pam.d/gdm"

---

### Post by labinnsw on 2010-05-13
With the help of [this post]("http://swiss.ubuntuforums.org/showpost.php?p=7812370&postcount=2"), I finally got it right.

1.  Go to Applications >> Accessories >> Passwords and Encryption Keys.
2.  Select the Passwords tab if it is not yet selected.
3.  Right click on the directory "**Passwords:** default"
4.  Select "Change Password"
5.  Enter your current password in the "Old Password" Window.
6.  Leave the "New Password" and "Confirm" windows blank
7.  Click "OK" then click "Use Unsafe Storage"

Unlocking will not work because the keyring is automatically locked on reboot.
If you are not behind a firewall, I would recommended that you install firestarter from the repositories.

---

### Post by zami on 2010-05-17
> **labinnsw said:**
> With the help of [this post]("http://swiss.ubuntuforums.org/showpost.php?p=7812370&postcount=2"), I finally got it right.

1.  Go to Applications >> Accessories >> Passwords and Encryption Keys.
2.  Select the Passwords tab if it is not yet selected.
3.  Right click on the directory "**Passwords:** default"
4.  Select "Change Password"
5.  Enter your current password in the "Old Password" Window.
6.  Leave the "New Password" and "Confirm" windows blank
7.  Click "OK" then click "Use Unsafe Storage"

Unlocking will not work because the keyring is automatically locked on reboot.
If you are not behind a firewall, I would recommended that you install firestarter from the repositories.

Perfect!  Thank you!

-zami

---

### Post by Tholley on 2010-05-17
If you are using wireless, it seems a simple solution which works for me and many others, is... on you wireless icon up top, click on properties for the wireless, and check the box that says "available to all users."
 
 
I'm thinking that is the issue at hand... :)

---

