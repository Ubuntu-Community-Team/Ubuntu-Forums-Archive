---
title: "Network: access shared ubuntu from xp"
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by Leon945 on 2007-05-29
Hello people..

I have a problem i don't know how to fix..
I use ubuntu, and my brother uses windows xp..
We both have a bunch of videos and songs and we like to share them...
I can easily access my brothers xp shared folders, but he cant see my computer on the network...

How can i make my ubuntu computer be visible to xp computers?

thanks in advance!:D

---

### Post by Acknud on 2007-05-29
I am having the exact same problem.  I can see my windows network but I can't see ubuntu from windows.  I hope we find a solution.

---

### Post by Leon945 on 2007-05-30
Well, no one seemed to care too much about our problem..

i found the solution myself, its very easy.. (at least it worked for me)
here it is:
in the menu, go to
System->Administration->Shared Folders
go to the "General Properties" tab, and type in your windows "workgroup"
if you want XP computers to see ubuntu, check the "This computer is a WINS server" options.

the name that your comp is accessed with is specified in "smb.conf" file
this file can be found in

/etc/samba/smb.conf

you cand edit it like this:

open a terminal and type:
```

sudo gedit /etc/samba/smb.conf

```

it will open  a text editor with the contents of the file...
the second line in that file is:

```

netbios name = samba24

```

you can change whatever is there to the name you want your computer to have on your windows network, i changed mine to

```

netbios name = leonUbuntu

```

change only that.
save it
close it.
restart Ubuntu...
and done...


be free..

hehe that worked for me...

---

### Post by Acknud on 2007-06-10
Well so far I can get XP and Vista to see Ubuntu but I still can't connect.  It asks for a user/pass and when I put them in it just kicks back to the same question.  I know I am entering the right user/pass but it still won't accept.  I even tried using root as the user name with no go.

---

### Post by Gausian on 2007-06-10
use this howto...

[Samba How To]("http://http://ubuntuforums.org/showthread.php?t=202605")

---

### Post by Leon945 on 2007-06-11
> **Acknud said:**
> Well so far I can get XP and Vista to see Ubuntu but I still can't connect.  It asks for a user/pass and when I put them in it just kicks back to the same question.  I know I am entering the right user/pass but it still won't accept.  I even tried using root as the user name with no go.

go into the /etc/samba/smb.conf file.. 
search for the part that says:

**security = users**

change it to

**security = share**

that should stop asking for passwords from an xp computer.

:D

---

### Post by Acknud on 2007-06-12
Thanks guys.  I now have a working network involving xp, vista and ubuntu!

---

