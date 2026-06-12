---
title: "Ubuntu laptop to server sync?"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by BlakeM on 2008-12-15
I'd like to start by saying I don't use forums much at all. I prefer to find answers by searching the web and forums like these. I think this would be about my fourth post to any forum ever. If I make any mistakes please let me know :P.

I'm not looking for specific answers, more like an indication if what I want to do with Ubuntu is possible and if so, how difficult it would be.

I'll be a med student next year and my ultimate goal is to use an eee pc at uni and a desktop/server PC at home (eee pcs don't look like the most comfortable computers to work on). What I aim to do is have the two computers synchronized so that all work, emails, files etc. are up to date at all times. I've read about Synplicity and Dropbox and this is **almost** exactly what I am looking for.

My complaint with Synplicity is that it doesn't work on Linux (slight problem ;-)). Dropbox is **perfect**, but limited to one folder only and also in the size of data you can store.

I've also read a bit into FTP but I must admit I haven't used it before. I do, however, intend to build a server.

Is there any way I can use currently available open source software (which can be used with Ubuntu) that can replicate the services provided by Dropbox and Synplicity?

---

### Post by BlakeM on 2008-12-15
Ok, I think I found a good thread. Just wasn't searching for the right things. Moderator please feel free to delete this thread :).

---

### Post by caue.rego on 2009-07-29
Delete might be a good idea, but you could leave that decision to the moderator and meanwhile do a favor for people like me, who fall in this topic through an external search, and help us by posting the link you've found! I'd appreciate it.

Although I'd guess you've found about **rsync** and its variates, and although I know how to use it, I'm trying to find something more automated like you've described. Right now, I'm testing out **unison** (again), **grsync** (which is not automatation at all), **conduit** (for first time) and **GAdmin-Rsync**, which are things I've found on Add/Remove.

---

### Post by asmoore82 on 2009-07-29
I use rsync over ssh with keys and Grsync -
No external "cloud" services required;
No passwords sent over the wire;
and everything is well encrypted.

---

### Post by The Cog on 2009-07-29
> **BlakeM said:**
> Ok, I think I found a good thread. Just wasn't searching for the right things. Moderator please feel free to delete this thread :).

You might post a link to that thread for others to follow.

I use rsync (over SSH) for this. Here is the script I use:
```
#!/bin/sh
LOCALDIR=$HOME/Sync/
REMOTEDIR=$HOME/Sync/
if /sbin/route -n | /bin/grep -q '^192.168.1.0 ' 
then 
    SERVER=192.168.1.103
else
    SERVER=<my public address>
fi
echo Syncing with $SERVER
echo Sending...
rsync --rsh=ssh -aizuKL $LOCALDIR $SERVER:$REMOTEDIR
echo Fetching...
rsync --rsh=ssh -aizuKL $SERVER:$REMOTEDIR $LOCALDIR
```
It syncs directory ~/Sync with the server, updating in both directions. It checks to see if it's at home or away, and uses the appropriate server address.

If I make a link in ~/Sync to other directories, it syncs them too.

---

