---
title: "Recommended Books for Ubuntu Server Administration"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by ITDude on 2010-06-10
I want to start off by saying I love Ubuntu! I like the support behind it and all it has done for the linux community. I have been on the forums before but never had to ask a question because it was usually already asked and solved! 

Now my First Ever Question! :)

I have been promoted at my job to Server Administrator. Woot! Only prob is I know not what I am doing. Can anyone recommend a few books, etc to help me out. 
My new duties include: Mail Server Admin (We Also use Zimbra for a few users and I dont have a clue how to add someone and BlackBerry Enterprise Server) Samba File Server, and just the General Admin for all our linux machines.  We currently run 4 8.04 servers and 1 10.04 server if that helps. :)

I have used Ubuntu at home for sometime, but I never used the server edition. I have been to the local book store but the books were for general desktop usage. I looked on amazon for several books but I dont want to waste money on one and it not be what I need. or buy several books, only to have them all have nearly the same information. 

Work has given me a budget of $200 for amazon to purchase anything I need so I can become their "Guru" I have seen several threads on here about books but they are usually for the desktop. I need help with the Server side of things. 

Any and all help is much appreciated!!! and sorry for the long post.

---

### Post by marshmallow1304 on 2010-06-10
It's not a book, but the [Ubuntu Server Guide]("https://help.ubuntu.com/8.04/serverguide/C/index.html") is an excellent resource, if not overly-detailed.  There are also many helpful articles for Ubuntu and Debian at [http://www.debianadmin.com/](http://www.debianadmin.com/)  Unfortunately, I cannot suggest any books, as I learn mostly through following guides and fixing things when I inevitably do something wrong.

---

### Post by ITDude on 2010-06-10
> **marshmallow1304 said:**
> It's not a book, but the [Ubuntu Server Guide]("https://help.ubuntu.com/8.04/serverguide/C/index.html") is an excellent resource, if not overly-detailed.  There are also many helpful articles for Ubuntu and Debian at [http://www.debianadmin.com/](http://www.debianadmin.com/)  Unfortunately, I cannot suggest any books, as I learn mostly through following guides and fixing things when I inevitably do something wrong.


Thanks marshmallow!!! Those will def help me out with alot of questions! 

looks like my afternoons for the next year or so are going to be consumed trying to learn what all I need to. LOL 

If anyone else has books to recommend or not to recommend still let me know. 

Thanks Guys

---

### Post by ITDude on 2010-06-10
here is a list of books I am about to order. If anyone has read or knows about any of them please let me know if im about to waste my money or spend it wisely. lol

978-0131367364 Practical Guide to Linux Commands, Editors, and Shell Programming, A (2nd Edition) (Paperback)

978-0071598927 Ubuntu Server Administration (Network Professional's Library) (Paperback)

978-0470108727 Hacking Ubuntu: Serious Hacks Mods and Customizations (ExtremeTech) (Paperback)

978-1430210825 Beginning Ubuntu LTS Server Administration: From Novice to Professional, Second Edition (Expert's Voice in Linux) (Paperback)

978-1430216223 Pro Ubuntu Server Administration (Paperback)

978-0470589885 Ubuntu: Powerful Hacks and Customizations (Paperback)

978-0071545884 Linux Administration: A Beginner's Guide, Fifth Edition (Paperback)

---

### Post by TheForumTroll on 2010-06-10
I haven't looked at the sites for some time but they used to be a good read:
[http://tldp.org/]("http://tldp.org/")
[http://www.linuxconfig.org/]("http://www.linuxconfig.org/")
[http://www.linuxtopia.org/]("http://www.linuxtopia.org/")
[http://lowfatlinux.com/]("http://lowfatlinux.com/")
[http://www.howtoforge.com/]("http://www.howtoforge.com/")

---

### Post by ITDude on 2010-06-10
> **TheForumTroll said:**
> I haven't looked at the sites for some time but they used to be a good read:
[http://tldp.org/](http://tldp.org/)
[http://www.linuxconfig.org/](http://www.linuxconfig.org/)
[http://www.linuxtopia.org/](http://www.linuxtopia.org/)
[http://lowfatlinux.com/](http://lowfatlinux.com/)
[http://www.howtoforge.com/](http://www.howtoforge.com/)


Thanks a million. I bookmarked them all!

---

### Post by TheForumTroll on 2010-06-11
Don't forget the [Tips & Tricks forum]("http://ubuntuforums.org/forumdisplay.php?f=100") right here on ubuntuforums.org :KS

---

### Post by iMisspell on 2010-06-12
We see you have the Desktop at home, why not install the server edition and get used to the command line alittle more and practice configuring the programs you need on that ?

If you only have one computer at home, maybe install VirtualBox and then install the server ed. to that.

If you run the following command, it will save the names of all the programs install on a system.
```
dpkg --get-selections > /path/to/installed-software.log
```

Then on a different machine you can run...
```
sudo dpkg --set-selections < /path/to/installed-software.log
```
and install all the programs to that machine.

Now you can play with all the programs install from your work server on your home machine and get used to things.


Just a suggestion.

Good luck.

_

---

### Post by ITDude on 2010-06-14
> **iMisspell said:**
> We see you have the Desktop at home, why not install the server edition and get used to the command line alittle more and practice configuring the programs you need on that ?

If you only have one computer at home, maybe install VirtualBox and then install the server ed. to that.

If you run the following command, it will save the names of all the programs install on a system.
```
dpkg --get-selections > /path/to/installed-software.log
```Then on a different machine you can run...
```
sudo dpkg --set-selections < /path/to/installed-software.log
```and install all the programs to that machine.

Now you can play with all the programs install from your work server on your home machine and get used to things.


Just a suggestion.

Good luck.

_

Actually I added a second HD and installed on it. lol. I thought about doing a virtual server but I was already using 12% processor at idle so instead of setting it on fire I just choose during boot up. :) 

Thanks for all the Help Everyone!

---

