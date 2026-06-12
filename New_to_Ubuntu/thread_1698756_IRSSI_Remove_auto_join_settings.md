---
title: "IRSSI Remove auto join settings"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by norlane on 2011-03-02
i see how to add a server to the auto connect when  irssi starts.
Can any one tell me how to  turn this off if i want to connect to a different server 
on starting irssi. 

I think this is an example of setting the auto join for a network irc server.
Thankx for ant help.

/network add -autosendcmd "/^msg nickserv ident yourpassword;wait -freenode 2000" freenode
/server add -auto -network freenode irc.freenode.net 6667
/channel add -auto #channel freenode

---

### Post by peculiar penguin on 2011-03-02
Add the server again but omit the -auto switch (and save your config), or just edit ~/.irssi/config with a text editor (find your server and change the "autoconnect" value to "no").

---

### Post by norlane on 2011-03-02
thanks for this have been viewing the config file with less in terminal quit cool.
will try this.

---

### Post by Jet Chang on 2011-07-19
> **peculiar penguin said:**
> Add the server again but omit the -auto switch (and save your config), or just edit ~/.irssi/config with a text editor (find your server and change the "autoconnect" value to "no").

Hello

I have an IRC bouncer on a shell, I did the /NETWORK ADD and its constantly trying to connect to my bnc which is failing.

I opened the .irssi config file with nano and changed the "autoconnect" to "no" but when I try to connect to an irc server it still tries to connect to the bnc first.

I have tried everything, I even uninstalled irssi and reinstalled it and it still does the same thing.

Please help with this problem!

---

