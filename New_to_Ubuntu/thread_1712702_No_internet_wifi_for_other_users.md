---
title: "No internet wifi for other users"
date: 2011-03-23
forum: New to Ubuntu
---

### Post by noob.bot76 on 2011-03-23
Hello all, 

My wifi connection is fine when I'm logged in; but when I log in as another user there is no wifi connection, and not even the wifi icon. 

How do I get wifi for all users?

---

### Post by d3v1150m471c on 2011-03-23
my guess would be to connect to the wifi network as the user you logged in as.

---

### Post by noob.bot76 on 2011-03-23
so, i'm logged in right now in my "account" or whatever, and I'm connected to the internet fine. 

when i switch users, even though i don't disconnect or do anything to the wifi connection, there is not wifi icon and no internet connection. 

thanks

---

### Post by noob.bot76 on 2011-03-23
now i can get on the internet -- don't know what changed. but there is still no icon for the wifi
a
also, does my wife now have to log in as me and connect to the internet before she can connect in her account? what if i want to have a guest user, etc.?

---

### Post by noob.bot76 on 2011-03-23
Uh, don't kow why it works now, but problem seems solved. 

Only "kink" is that whoever logs in first gets the wifi icon. I rebooted and logged in as another user, and there was the icon -- but when i switched to my account, no icon. :confused:

sorry to waste everyones time -- i really couldn't connect before!

---

### Post by tordeu on 2011-03-23
Although this is fixed, I want to suggest something:

Go to System > Preferences > Network Connections. Choose the "Wireless tab", select you connection and then "Edit".

At the bottom there is a check-box "Available to all users". Make sure this is checked. And hit "Apply".

It would not explain the behaviour you described with the first user to log in to have access, but on the other hand, it does not hurt to check if "Available to all users" is checked for your connection.

---

### Post by walt.smith1960 on 2011-03-23
> **noob.bot76 said:**
> Uh, don't kow why it works now, but problem seems solved. 

Only "kink" is that whoever logs in first gets the wifi icon. I rebooted and logged in as another user, and there was the icon -- but when i switched to my account, no icon. :confused:

sorry to waste everyones time -- i really couldn't connect before!

That appears to be normal behavior with Network Manager.  I have gotten NM to display on more than one user's desktop by opening a terminal and typing "nm-applet".  You have to leave the terminal session open though.  Close the terminal and nm-applet closes.

---

### Post by tordeu on 2011-03-23
In that case you could try

```

screen nm-applet

```

and then close the terminal

And you can also make
```

nm-applet

```

run automatically as a startup application by going to System > Preferences > Startup Applications.

Click "Add", enter some name (for e.g. "starting nm-applet"), enter "nm-applet" as "Command", enter a comment if you like and then click "Add".

This would need to be done for every user, though. Another possibility (although I am not sure if this is the right place), would be to add it, for example, to the file:

```

/etc/gdm/PostLogin/Default

```

This files does not exist at first, so you should copy the Default.sample to Default
```

cd /etc/gdm/PostLogin
sudo cp Default.sample Default

```

and then edit it the Default file and append "nm-applet" to it. Like this (for example):
```

sudo echo "nm-applet" >> /etc/gdm/PostLogin/Default

```

This should work for all users, although (as already mentioned) I am not sure if this is the right place to put it.

---

