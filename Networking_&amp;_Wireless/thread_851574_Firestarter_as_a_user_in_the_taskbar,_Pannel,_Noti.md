---
title: "Firestarter as a user in the taskbar, Pannel, Notification area"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by LouEven on 2008-07-06
666 I'm out

---

### Post by Tyche on 2008-07-06
> **LouEven said:**
> I'm running 8.04 and I'm using Firestarter. I was wondering how I could view the Firestarter icon in the menu/taskbar while a regular user. I know it's running in the background, but it would be nice to see what is going on while a regular user.

Is there a security issue with doing this if it is possible?

T.I.A.
Thanks In Advance.

No security issue that I know of.  But it is a bit involved, so bear with me.  Go to System -> Preferences -> Sessions.  On the "Startup Programs" select "Add".  In the box that pops up, put in the following information:
Name = Firestarter
Command = gksudo firestarter
Comment = Firewall front end

Hit the "OK" button and you're good to go on the next reboot.  What will happen on reboot is that you will log in with your user name and password, then, after a short delay you will be asked for your password again.  ENTER THE SAME PASSWORD.  This will bring up Firestarter - a blue button with a right facing black arrow on it as well as the Firestarter window.  DO NOT CLOSE THE WINDOW WITH THE "CLOSE" "X".  Just click the button.  The button acts as a toggle to show/remove the window.  If you close with the CLOSE "X", it will shut down the button, too.

To bring it up BEFORE you reboot, go to System -> Administration -> Firestarter.  Again, the button toggles the window.

NOTE:  gksudo is a window box to request your password for sudo.

Hope this helps.

---

### Post by LouEven on 2008-07-06
666

---

### Post by Tyche on 2008-07-06
LouEven,

That's the wierdist thing I've ever heard.  Your password in the gksudo window should have given Firestarter the administrative privelages it needed to run.  I've started Firestarter this way dozens of times without a problem.  If I hadn't felt confident in its being able to work, based on empirical experience, I wouldn't have posted a reply (there are all too many things that I won't reply to in the forums, because I don't feel confident that I can answer the question).  The information I gave you is exactly as it is in my Sessions Preferences Startup tab.

As for not connecting to WEP2, I have NO idea.  I've never seen where administrative privelages were needed to activate it, since the network should have been started before the desktop even came up.  I don't run wireless myself, but my wife does, and she's never needed administrative privileges to connect to the network.

I'm afraid that you have some other problem that's causing the symptoms, and someone else will have to take over.

I'm sorry I can't do more.

---

### Post by LouEven on 2008-07-07
666

---

### Post by dmizer on 2008-07-07
the first user on your machine is not "admin", it merely belongs to the [sudo group](https://help.ubuntu.com/community/RootSudo).

sudo is the ability to temporarily switch your user to another account for the purpose of making quick changes to the system without having to log out and back in again.

in this case, your first account could sudo as the root (equivalent to admin in windows) in order to run the firestarter gui.

if you wish your second user to be able to run the firestarter gui, you'll also have to grant sudo rights to your new user.  this can be done via the gui users interface in the "administration" menu.

but really, it's a good idea to keep your sudo capable users to a minimum.

if you must see the firestarter log output, just take a look at dmesg.

---

### Post by LouEven on 2008-07-07
666

---

