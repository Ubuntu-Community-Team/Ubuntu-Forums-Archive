---
title: "Intel 537ep soft modem"
date: 2006-10-23
forum: Networking &amp; Wireless
---

### Post by gargoyle on 2006-10-23
I have looked at a few posts and guide for installing this modem.
In the guide[Howto install Intel 537ep Dapper]("https://help.ubuntu.com/community/DialupModemHowto#head-ea2d9e972a0f68a252cee1f0491fb86361cc3766")
> Installing on 6.06.1

Fortunately, the install works perfectly on 6.06.1 (you have 6.06.1 if "uname -r" prints 2.6.15-27-386 or 2.6.15-27-686). Simply unpack, then type the following:

1. make clean 
2. make 537 
3. sudo make install 

Unfortunately it does not seem to like the **make command**. 
It say the command can not be found.**bash: make: command not found**
So it would seem like I do not need to recompile. 

However in another post. [Howto install Intel 537ep Post]("http://www.ubuntuforums.org/showthread.php?t=210405&highlight=intel+537")

It seem like I need to download and recompile.

So which is it??
I do not have a working modem on the Ubuntu computer so I do not know how I would do a lot of stuff on the one post.

Any help here?

---

### Post by ReaderRat on 2006-10-23
May be a re-print:
[**Modem HowTo**](https://help.ubuntu.com/community/DialupModemHowto)
Hope it helps.

---

### Post by chuckman78 on 2006-10-23
Hi gargoyle.

I think you will find this link usefull:

[http://www.ubuntuforums.org/showthread.php?t=210405&highlight=537ep]("http://www.ubuntuforums.org/showthread.php?t=210405&highlight=537ep")

I suggest you read it all, then print it to have it handy, and download all the needed packages to a USB pendrive.

Regards,

Carlos.

---

