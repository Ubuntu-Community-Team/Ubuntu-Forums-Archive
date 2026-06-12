---
title: "Is there a Key Combo to Log Off?"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by matey3 on 2011-05-06
as you know in windows you can press/hold the windows key and press L to log off. Is there such a key combination in 11.4?
I logged in as this new user but there were errors and now I am getting a blank screen in (GUI).
Thanks for the help in advance.

---

### Post by adit on 2011-05-06
If GUI is unresponsive, login through Ctrl+Alt+F1 then issue the following command to logoff.```

gnome-session-save --logout
```

---

### Post by lotharmat on 2011-05-06
Win+L locks the screen in Windows- ctrl+alt+l does the same in Ubuntu.

I'm not sure you can 'log off' from a built-in keyboard shortcut - In Ubuntu you can create one though pretty easily!

---

### Post by josephmills on 2011-05-06
try ctrl+alt+delete
**edit I did not see that you have no gui **

---

### Post by matey3 on 2011-05-07
Thanks a lot for your replies.

ctrl,alt L works but at the time the screen was locked out and it returned some errors.
I had to go to the terminal (ctrl alt F1) and use pkill to get out:

sudo pkill -KILL -u USER_NAME

I think the problem was that I created a user in the terminal (used useradd and then adduser to group etc,)but when GUI started it said the user didnt have the rights to the home directory and few other things (I forgot exactly what)?

Thanks a lot guys!
regards;

---

### Post by coffeecat on 2011-05-07
In answer to your thread title question, the answer is yes. In fact it is a key combination to kill the xserver (or rather all processes in the current virtual console), but it has the same effect, returning you to the login screen where you can log in again or shut down the system. It is alt-SysReq-k. the sysreq key is often labelled simply "Print Screen" or "Print/SysReq" or some such combination. On some machines you need to use the Alt Gr key to the right of the spacebar rather than the left alt key.

This combination is one of the magic key combinations. The sequence for shutting down a frozen system is worth knowing about:

[http://en.wikipedia.org/wiki/Magic_keys](http://en.wikipedia.org/wiki/Magic_keys)

---

