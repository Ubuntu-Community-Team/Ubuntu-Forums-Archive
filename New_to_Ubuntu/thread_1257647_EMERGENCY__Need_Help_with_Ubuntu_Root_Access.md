---
title: "EMERGENCY : Need Help with Ubuntu Root Access"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by SriLankanBoy on 2009-09-04
I messed up with the user privileges in my account. :( I had two accounts in my ubuntu.
1. Administrator
2. Guest

I accidentally disabled all access to both accounts through the Users & Groups option. Now I cannot access the terminal, user & groups and other tools. How can I solve this problem ? :confused:

When I type a code in terminal, error message shows,
"administrator is not in the sudoers file.  This incident will be reported."

When I access Users & Groups it tells,
"Configuration Could not be Loaded.
You are not allowed to access the system configuration" :(

It is all because I disabled all my access myself !

I think if I can become root, I can solve this problem. How to solve this ? Any ideas ? :|

---

### Post by wojox on 2009-09-04
See if you can boot the LiveCD and undo it.

Else:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by nothingspecial on 2009-09-04
Restart and when the grub thing comes up press escape.

Log in to recovery mode/failsafe root terminal or whatever they call it these days.

---

### Post by SriLankanBoy on 2009-09-04
> **wojox said:**
> See if you can boot the LiveCD and undo it.

Else:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

The Live CD method did not work. It only shows the default root user.

I don't want to change the password. I want to enable all my access to my account.

---

### Post by SriLankanBoy on 2009-09-04
> **nothingspecial said:**
> Restart and when the grub thing comes up press escape.

Log in to recovery mode/failsafe root terminal or whatever they call it these days.

Could you explain the steps ? :confused: I am a newbie to Ubuntu ...

---

### Post by nothingspecial on 2009-09-04
Restart your computer and when the dialogue "grub loading" appears on your screen just before boot press escape.

You`ll be presented with a few options. One of them says something like recovery console or failsafe root terminal or something like that. Select that one and you will be logged in as root. From there you can fix your system.

---

### Post by SriLankanBoy on 2009-09-04
> **nothingspecial said:**
> Restart your computer and when the dialogue "grub loading" appears on your screen just before boot press escape.

You`ll be presented with a few options. One of them says something like recovery console or failsafe root terminal or something like that. Select that one and you will be logged in as root. From there you can fix your system.

Yeah. I logged in as root. How can I enable my user account (administrator) previleges through command line ? Could you explain me with the codes and stuff please ?

Sorry if I am disturbing you .:(

---

### Post by nothingspecial on 2009-09-04
```
sudo adduser *[COLOR="Red"]username[/COLOR]*
```

Will add a user
```

sudo adduser *[COLOR="Red"]username[/COLOR]* admin
```

Will give that account sudo privaledges.

Obviosly you don`t need sudo in the root recovery shell.

---

### Post by SriLankanBoy on 2009-09-04
Thank you so much nothingspecial. :)

It worked like a charm.

---

### Post by nothingspecial on 2009-09-04
No problem :)

---

