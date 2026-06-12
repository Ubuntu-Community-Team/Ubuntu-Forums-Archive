---
title: "[SOLVED] root password and/or WEP key reset?"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by Ant68 on 2008-12-09
Hi,
I have a fresh install of 8.10 and I set up NetworkManager applet (nm-applet) 0.7.0 under my user account. The issue is that the nm-applet does not work with my wireless network card Realtek (known issue I figured afterward). 

Now when I log in, I always have the system freezing onceI have logged in and before I can do anything in gnome (mn-applet make the system freeze). i.e. I see the wallpaper in the back and after 1 or 2 seconds (the time the mn-applet search for the network) it freezes.

I see to solutions:
1 – I log in as the root user and I remove my user account (this was the one I created during the install). I then can set up another driver. The issue is I do not know the root password. How can I get it set up so I can then log in with it in Gnome?
2 – How can I remove the WEP Key for my user so when I login the system will not freeze.

Could you please give me directions for these two options?

---

### Post by Pjotrovitz on 2008-12-09
OK, here's what you do to get rid of the connection:

Log into a failsafe X-Terminal session (choose it from the sessions list on your login screen).

Then you type nm-connection-editor when you get the terminal screen. This will bring up the connection editor window for network-manager. Delete your connection, close the program and type exit in the terminal. Now you should be able to log into your regular desktop again.

BTW, the root password is the same as the first user you installed's password initially (assuming you installed via liveCD.

Good luck!

---

### Post by sum janus on 2008-12-09
I don't think you can log in as root though.  That's what sudo is for.

---

### Post by wizard10000 on 2008-12-09
Easiest way to delete a user account is to create another user and add them to the admin group - then log on as that user and delete the unwanted user account.

Start in recovery mode and enter your password when prompted - then

```
adduser -g admin *username*
```

then - 

```
passwd *username*
```

You should then be able to log on as the new user and delete the old user account.

---

### Post by Ant68 on 2008-12-09
> **Pjotrovitz said:**
> OK, here's what you do to get rid of the connection:

Log into a failsafe X-Terminal session (choose it from the sessions list on your login screen).

Then you type nm-connection-editor when you get the terminal screen. This will bring up the connection editor window for network-manager. Delete your connection, close the program and type exit in the terminal. Now you should be able to log into your regular desktop again.

BTW, the root password is the same as the first user you installed's password initially (assuming you installed via liveCD.

Good luck!


it works fine now. Thanks a lot

---

