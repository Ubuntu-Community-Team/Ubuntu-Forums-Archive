---
title: "[SOLVED] SSH with kate and konqueror (in GNOME)"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by cannibal_bill on 2008-05-28
Hi,

I get this rather strange message when I try to connect through SSH from either Kate or Konqueror : 

```
An error occurred while loading **fish://user@server:22/path**:
The protocol /bin/sh: line 2: /dev/null: Permission denied is not supported.
```

I also get sometimes strange ouput like ```
### 000
```

_Permission denied is not supported_ !! and buggy error code . . .

Does anybody have an idea?
Everything worked fine until today.
I have an up-to-date 7.10.
FTP works fine with both konqueror and kate.
SSH works fine with shell and nautilus.

I know I should use kate & konqueror in kubuntu or try to find equivalents for gnome, but I couln't find better (file) browser than konqueror and better editor than kate (and now I'm used to them..) and I dont really like kde.

Anyway thanks for enlightening me !

[COLOR="Red"]edit: The problem was my host's permission on /dev/null
(I guess) they set it to 666 as adviced on every forum.

Now it works ![/COLOR]

---

### Post by kevdog on 2008-05-28
could you preface your ssh argument with 3 v's, something like

ssh -vvv ......

This will give verbose output.  Im not sure why things are not working.  And you probably want /bin/bash, rather then /bin/sh.

---

### Post by cannibal_bill on 2008-05-28
kevdog,

When you write "preface ssh argument", I cannot do it since it is a shortcut in konqueror (plus in kate, I just press ctrl-s and it "initiating connexion... saving...).
In shell (the terminal), -vvv outputs of lot but with no scrollbar (why ?!), even in fullscreen, I can read only the last few lines (chinese, but everything seems correct). By the way ssh works perfectly in shell and nautilus, but not in kate/konqueror.

I confirm the error (alert box in kate, text in place of file listing in konqueror) says bin/sh and not bin/bash.

I may have an explanation for "permission denied is not supported": if you take the whole message like this : 

The protocol [COLOR="Red"]/bin/sh: line 2: /dev/null: Permission denied[/COLOR] is not supported.

it seems clear to me that the error message echoes the protocol's failure message in place of the protocol's name. I would understand "The protocol xyz is not supported".
So I tried to understand what the red text means, and effectively when I enter "/dev/null" in terminal, it says "bash: /dev/null: Permission denied". I dont know what it should say so I looked for that here and in google and they said to chmod it to 666 and check for the owner (which is "root" here).

I guess I'm on the right way, do you have any info about what "/dev/null" should output and what user it should be set to ?

Thanks !

---

### Post by cannibal_bill on 2008-05-29
It still won't work.

I managed to get the ### 000 error again, it says exactely :

```
An error occurred while loading fish://user@server:
### 000
```

I have tried "konqueror fish://user@server" in terminal. It asks me for a password, then fails (as usual) with the following output in terminal : 

```
ASSERT: "!icon.isEmpty()" in /build/buildd/kdebase-3.5.8/./libkonq/konq_pixmapprovider.cc (81)
ASSERT: "!icon.isEmpty()" in /build/buildd/kdebase-3.5.8/./libkonq/konq_pixmapprovider.cc (81)
ASSERT: "!icon.isEmpty()" in /build/buildd/kdebase-3.5.8/./libkonq/konq_pixmapprovider.cc (81)
ASSERT: "!icon.isEmpty()" in /build/buildd/kdebase-3.5.8/./libkonq/konq_pixmapprovider.cc (81)

```

I could not find more info about that.
Kate still won't work, but does not output any error message in terminal.

I also searched for "/dev/null: Permission denied" but could not find anything interesting...

What can I do?
The weirdest thing is it stopped working all of a sudden: now it works, now it doesn't...

---

### Post by cannibal_bill on 2008-05-29
Bump !

No one's had this problem ?
Then please somebody tell me if it's BAD to use kate/konqueror in gnome. This is this ideal mix for me, and it HAS WORKED, perfectly !!

But is it a rather buggy mix ?

---

