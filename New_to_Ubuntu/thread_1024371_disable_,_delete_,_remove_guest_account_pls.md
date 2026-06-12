---
title: "disable , delete , remove guest account pls"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by quattrorally on 2008-12-28
Hi there noob here, I recently installed U-desktop 8.10 (64) on my system to act as a spare system, server, etc.  I want to lock it down and one of the things that really bothers me is the guest account.  I really want to disable it.

I was thinking that by installing the desktop I would have the basic desktop system and could install only the server components that I needed.  I am wondering however if I should have done the reverse, install the server and install only the needed desktop components, but now I am going off on the tangent, however if any one wants to chime in please do so.

But for now I really want to disable the guest account.

thanks

---

### Post by dasunst3r on 2008-12-28
To the best of my memory, the guest account is something created when you use the fast user switcher bar to switch into it.  After the guest logs out, it's deleted.

---

### Post by quattrorally on 2008-12-29
Great, so my system has an open account and not even a trace is left of what the "ghost" user is doing....what brainchild came up with that idea ?

As much as I like Ubuntu if there is no way of disabling this Ubuntu is getting wiped.


I though the whole idea of *nix was that every thing is based on standards and everything is defined, and treated same way.  A system logon account, be it root, deamon, or any user is always defined in the same way so why the he!! would they change the guest account and make it the M$ way (hide, convolude, obscure, and deveate from norm) ???

Please can some one shed some light on this issue ?

thanks

---

### Post by louieb on 2008-12-29
> ....what brainchild came up with that idea ?Since I started using Linux there have been request and questions on how to make a password less guest account.  Somebody in the open source community made one and Ubuntu included it with version v8.10.   One mans sugar is another mans vinegar. 

Just get rid of the fast user switcher from the panel and use quit option on the system menu. Or since its it a server use v8.04 and you'll get the bonus of 5 years of support. 

All user by default are not by default defined the same way root is special, its home dir is /root. Other users by default have there home dir in /home/<user name>.  

Its not like you can login to the guest account remotely. The guest account is limited. Not much he can do to trash a system.  I' am much more concerned about an unauthorized person having physical access to my server and its keyboard and terminal.

Once you get use to Linux you'll be able to build from the ground up add just the services and programs you need.  This is mostly true for Ubuntu and most other Linux distros. 

Good luck and have a Happy New Year.

---

### Post by quattrorally on 2008-12-29
Yes root is defined the same way, it exists in /etc/passwd has groups associated with it etc, and it's home dir "/root" is defined in the /etc/passwd file.

From my limited experience with *nix oses usually guest accounts were defined as regular users with a simple password, sometimes displayed somewhere within the logon message.  This method has been used for many many years and I frankly do not see anything wrong with it.

Did not mean to be rude "brainchild", just got quite annoyed (flashbacks of MS software practices) that I was able to logon to the system with an account that I could not find any traces of in the standard places of user administration.

Thanks

---

### Post by Airknocker on 2008-12-29
I think what happened here is the requests for a "Guest" account got misunderstood in the implementation.

I think you could easily kill guest by deleting the guest-session directory from /usr/share/gdm/

I have not tried this myself, but this is where the program launches from and I would think deleting the files will kill the ability to use it.

So, what we wanted was basically a "kiosk" setup where you could do a standard install of Ubuntu and it would contain a user account called "guest" that either had a simple password or no password at all.  The user would be restricted to Firefox, OpenOffice, a media player and maybe some other apps.  The account could not access the hard drive and only be able to use floppies, CD drives and USB drives.  Any temp files needed for the session would be wiped at logout (or the next log in).

Ideally, the system administrator could configure the guest account as needed but the user could not make any changes.  The request for this type of user account is for things like public libraries, internet cafes, etc.  Where you don't want someone to mess up the system, but you don't want to have to create a new user for each person either. 

The guest account in 8.10 missed the mark because it makes you log in as a regular user before you get the chance to start a guest session which defeats the purpose.  The guest session itself is workable, but we would like to see it be available from the login screen.

---

### Post by coolen on 2008-12-29
The guest account differs from a dummy account with a simple password mainly by the fact that it's temporary. No data is stored on the system (and the guest has very limited access to the system).

As far as I know, this was included by Gnome. I like the idea, although I personally have no use for it. It would help in a more shared setting, in which my Ubuntu machines do not find themselves.

As someone pointed out above, giving someone with enough experience physical access to your system is essentially giving them unlimited access.

Still, free software is all about choices, and yours is certainly a legitimate request. Found in another thread:
```
sudo apt-get remove gdm-guest-session
```

I can't try it, but after restarting GDM (Ctrl+Alt+Backspace) this reportedly works. Perhaps a brainstorm idea to disable this from a menu option somewhere would be in order, if none yet exists.

EDIT: Also, being able to log in as guest from the login screen would be massively useful.

---

### Post by quattrorally on 2008-12-29
Yes this command works and get's rid of it.   

Thanks for the help, greatly appreciated !


FYI: I have mounted a samba share accessible to all system users and this guest user could also see the drive for what it's worth.


However if you do want a guest account why not just create U:guest P:guest and assign the rights that you want to that user ?

---

### Post by Airknocker on 2008-12-30
> **quattrorally said:**
> Yes this command works and get's rid of it.   

Thanks for the help, greatly appreciated !


FYI: I have mounted a samba share accessible to all system users and this guest user could also see the drive for what it's worth.


However if you do want a guest account why not just create U:guest P:guest and assign the rights that you want to that user ?


Ah, there is the kicker.  Creating and configuring the account is not so hard.  What we need though is an account that "resets" at each log off, deleting any traces of the previous user.

Imagine this scenario:

A library patron logs on to check his email, surf the web, then downloads a photo from his camera and puts it in a document that he then saves to a thumb drive.  He logs off and leaves.  We don't want the next patron that uses that machine to "see" any of the things previous users did, where they went or documents they worked on.

I don't mind the idea of a user account that has a password, we could give that out when the patron signs in, heck we could even change it once in a while.  However, lock down of the account and deletion of previous user activity is of most importance.

---

### Post by coolen on 2008-12-30
Really, they're just different means to the same end. This is what Ubuntu (Gnome?) has chosen.

I would appreciate it if it were easier to change, but this is just what we're doing now. Similarly, if you don't like ALSA+Pulse, use OSS. Don't like Totem, use MPlayer. Don't like Firefox, use Epiphany.

Linux is all about choices and, nowadays, replaceable defaults. When something cannot be replaced, and is forced on the user, that's the real problem.

---

### Post by kuttapuly on 2010-08-03
:D this one works well,  thank you

---

### Post by kuttapuly on 2010-08-03
works well

---

