---
title: "Adminstrative password"
date: 2010-12-09
forum: New to Ubuntu
---

### Post by hkarn on 2010-12-09
Hello,

I am wonder how I get full access rights to the system.

I installed eee Applet to be able to control the fan and stuff.

When I try to change fan speed it asks for administrave password and my normal user password doesn't work. 

Also I can't access parts of the file system.

I tried the command $sudo passwd root but it says

hka@hka-1001PX:~$ $sudo passwd root
passwd: You may not view or modify password information for root.

I am on the first and only user account created which is an administrator.

---

### Post by sikander3786 on 2010-12-09
Root account is disabled on Ubuntu for some pretty good reasons.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

If you want temporary root access, this command would be sufficient.

```
sudo -i
```

You won't be able to see the root owned folders in filesystem. If you need to access them,

```
gksudo nautilus
```

While running nautilus with root privileges, **be cautious** and make sure don't delete/modify anything by mistake or your might be in some troubles ;-)

---

### Post by hkarn on 2010-12-09
ok i think i figured out where in the file system i should hang out and how to extract and install programs without needing any root access :)

But what do I do about this eee applet? Can I use some command to launch it with enough access to change fan speed and clock? Like some flag I can put in the autostart to run with it...

---

### Post by sikander3786 on 2010-12-09
Drag that eee applet icon to the desktop. Right click > Properties > [COLOR="Red"]Command[/COLOR].

Bring up application launcher by Alt + F2 and type,

```
gksudo command
```

Where command is the text for [COLOR="Red"]Command[/COLOR].

---

### Post by hkarn on 2010-12-09
Uhm sorry but I don't get how to do any of that.

Things doesn't drag from my Applications and they can't be right clicked in there.

And Alt+F2 does nothing.

Also now I got like 5 eee Applet tray icons. Is there like a task manager to shut them down cause they have no exit option in it.

EDIT
Ok I typed
```

cd /usr/bin
gksudo eee-applet

```
In my terminal and after promoting for my regular user password it opened a 6th instance of the eee applet that doesn't ask for an administrator password when changing the fan option.

Not that it did anything to the fan anyway but that is probably just the eee Applet that is broke or incompatible with my particular eee...

But if I want another program auto-starting with these rights I just put a command like gksudo /usr/bin/application in the autostarter? Is it possible to add my user password in the command line so it doesn't have to prompt for it every time?

I also managed to kill the processes even the one run by root in the terminal (whoo uni linux command intro paying out). But is there a graphical task manager, I can't find one?

---

### Post by sikander3786 on 2010-12-09
Sorry, you are using Netbook Edition and icons can't be dragged to desktop there :oops:

You need to find the command for launching you app. Or post a link to that so we can try finding that for you ;-)

---

### Post by hkarn on 2010-12-09
Think I forgot to update my browser and didn't see you had answered before I edited. There is some new information and questions in my last post.

Thank you for the help btw.

---

### Post by sikander3786 on 2010-12-10
You are Welcome :-)

If the path is correct, this command should start your app with root previleges.

```
gksudo /usr/bin eee-applet
```

Alt + F2 does nothing on the netbook edition.

Click the Applications Icon in launcbar (pair of scissors) and search for 'System Monitor'.

Autostart an app with root previleges :-k , I don't have many ideas for that unfortunately.

---

