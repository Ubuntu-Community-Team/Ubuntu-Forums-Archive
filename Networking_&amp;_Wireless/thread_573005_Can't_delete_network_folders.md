---
title: "Can't delete network folders"
date: 2007-10-11
forum: Networking &amp; Wireless
---

### Post by Bob1275 on 2007-10-11
Here goes first post... I have Samba set-up on my ubuntu machine and cannot delete folders on the network (they're multiplying like rabbits!) :). Cannot delete on windows xp side either.

 I deleted these off my ubuntu desktop a long time ago, should I have removed them from the network first?

 I get an error when trying to send to trash: &#8220;cannot move to trash do you want to delete immediately&#8221;, when I hit delete it says: &#8220;operation not permitted&#8221; smb://desktop2/%23shared%20folder%20desktop
 
If I try to open a folder, it either opens but with no contents (obviously); or gives an error:
&#8220;the folder contents could not be displayed, cannot find, perhaps they were recently deleted&#8221;

I tried for example: sudo rm -r smb://desktop2/#SHARED FOLDER desktop
(saw in a forum) I tried with the -f operand too (forced), but didn't do anything either...
 I don't know if this was correct, but just can't seem to fix this...

Thanks very much for the help.

---

### Post by eendoe on 2007-10-11
Not much of a response for a first post;

This looks like either;

a) a network connection probelm (the resource is not accissible by client)

or

b) if you are just removing a link try to delete it manually as root, i.e;

su rm -f /home/user/Desktop/link

Any luck???

---

### Post by Bob1275 on 2007-10-11
Did you mean like the following? (If I did something lame let me know ;)..)

When I typed: su rm -f /home/bob/Desktop/#SHARED FOLDER WITH COMP 2
I get:
su: invalid option -- f
Usage: su [options] [LOGIN]

Options:
  -c, --command COMMAND         pass COMMAND to the invoked shell
  -h, --help                    display this help message and exit
  -, -l, --login                make the shell a login shell
  -m, -p,
  --preserve-environment        do not reset environment variables, and keep
                                the same shell
  -s, --shell SHELL             use SHELL instead of the default in passwd

Thanks..

---

