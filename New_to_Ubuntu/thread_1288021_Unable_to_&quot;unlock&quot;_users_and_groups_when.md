---
title: "Unable to &quot;unlock&quot; users and groups when connecting via vnc"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by CharlesA on 2009-10-10
Hi all,

I saw a bug report for Ubuntu 8.4 for this specific issue, but nothing for 9.04.

Anyway, I wanted to edit the users and groups remotely via vnc, unfortunately the "unlock" button was greyed out in gnome. I didn't try to edit them via command line, but ended up just bouncing the box after hooking up monitor/keyboard/mouse.

Is there any way to fix this?

Thanks!

---

### Post by tarps87 on 2009-10-15
Not a solution but a work around, run the user edit program using gksudo, I can't remember what the program is called but if you edit the menu it will show you the command.

This may not be a bug, instead it could be a security related issue, personally I would use a ssh connection and the command line to edit users over a network

---

### Post by CharlesA on 2009-10-15
> **tarps87 said:**
> Not a solution but a work around, run the user edit program using gksudo, I can't remember what the program is called but if you edit the menu it will show you the command.

I tried that, no luck. It prompts for my password but still doesn't activate the unlock button in users and groups.

For those interested: The users and groups program is "users-admin."

>  This may not be a bug, instead it could be a security related issue, personally I would use a ssh connection and the command line to edit users over a network

[After some more digging, it looks like it's a security thing]("https://bugs.launchpad.net/ubuntu/+source/policykit/+bug/238799"):

> The Unlock button should always be greyed out in users-admin by default when running over a SSH session, as the default Ubuntu policy for this action is to only grant authorization when running on the active console. A SSH session can never be on the active console.

Only problem is that I don't want to test the "fix" on a live server. It's not that big of a deal if I break something, since I can just reimage the machine, but it's still a pain.

Note to self: Even if it's a bug report for an older version, read it anyway.

---

### Post by tarps87 on 2009-10-15
It looks like using a ssh connection is the way to do it then, I agree about not testing it on a live system. You could do the same as me, set up a server and client machine using virutal box, then it is just a case of making a backup of the virtual hard drive.

If you want to use a ssh connection these should help
[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)
[https://help.ubuntu.com/8.04/serverguide/C/user-management.html](https://help.ubuntu.com/8.04/serverguide/C/user-management.html)

---

### Post by CharlesA on 2009-10-15
I've already got VNC tunneled over SSH, for security, so that's fine. I'll probably mess around with the install of 9.04 server in VB later today to see if I can get the "unlock" button working, or if I should just stick to useradd, usermod, and userdel.

Unfortunately I cannot figure out how to add the "real name" to a user from the command line, the same way I can by using the GUI.

---

### Post by tarps87 on 2009-10-15
I can't remember how to add a users name to an existing user but if you use the adduser and deluser commands it will prompt you for each bit of information

---

### Post by CharlesA on 2009-10-15
> **tarps87 said:**
> I can't remember how to add a users name to an existing user but if you use the adduser and deluser commands it will prompt you for each bit of information

Thanks for the infos. :)

---

