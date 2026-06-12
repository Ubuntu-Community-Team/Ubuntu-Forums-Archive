---
title: "what is sudo?"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by theprince862 on 2009-08-05
Hi i am just wondering what is sudo that sometimes it is written before the terminal command and how am i supposed to remember all these terminal commands

---

### Post by MelDJ on 2009-08-05
sudo means run as root or run as master of the computer

---

### Post by theprince862 on 2009-08-05
thanks alot MelDJ but am i supposed to memorize alot of commands or is there any other way

---

### Post by jerome1232 on 2009-08-05
sudo = super user do, it's used to elevate your accounts privileges to that of the admin user (called root in linux).


Whenever your not sure about how to use a command check out it's man page, they are basically help manuals. To view a programs man page just type 'man' before the command, ie if I wanted to see tar's man page:

```
man tar
```

remembering commands is just as hard as remembering where items are in a gui if you ask me, it just comes from use.

---

### Post by MelDJ on 2009-08-05
this might help
[http://docs.google.com/gview?a=v&q=cache:uJalavRuMiQJ:www.bienalfindelmundo.org/img/archives/174_20090206115656_ubunturef-pdf.pdf+ubuntu+commands+pdf&hl=en&gl=my](http://docs.google.com/gview?a=v&q=cache:uJalavRuMiQJ:www.bienalfindelmundo.org/img/archives/174_20090206115656_ubunturef-pdf.pdf+ubuntu+commands+pdf&hl=en&gl=my)

---

### Post by braete on 2009-08-05
root is the administrator of a linux system, he can do anything with any file
in ubuntu, by default' root password is locked. you cant login on that account.

but sometimes you need to do things that only root can do.
here comes sudo, witch grants, for a limited time, to your user the permissions of the root user

more here: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by MelDJ on 2009-08-05
you will get used to it... using commands like apt-get everyday will make you remember them easily. I don't think you can remember all the commands as there are many. But u will eventually remember the daily used one's: apt-get, ls, etc...
u could always look up the command for a specific task on the net...:popcorn:

---

### Post by LunaticHiatus on 2009-08-05
Sudo tells terminal that even if your running a user account, you are the administrator and can install whatever you like.

Ubuntu and most linux users do not run as administrator because if someone uses your computer and your on as administrator they can essentially mess around and break everything without your permission. So, its usually better to just run unprivledged and just have terminal and gnome ask you a password whenever you want to do something.

Thusly, if you say aptitude install firefox from a user account, it will say "your not an administrator, you have no right to do this!" if you say "sudo aptitude install firefox" it will say "password administrator?" and when you type it in, it will say "ohh, your the administrator!" and do what you like. It will then usually remember your password until you close terminal, and everything you say with Sudo in the front, will let terminal know the administrator, not the user is talking.

---

### Post by benj1 on 2009-08-05
apropos is also useful

'apropos find'

will give a list of installed programs with find in the man page description.

---

### Post by theprince862 on 2009-08-05
Thanks alot for your fast replies guys it really helped

---

### Post by Viva on 2009-08-05
You rarely need to use any commands in ubuntu, so you need not memorize any.

---

### Post by MelDJ on 2009-08-05
> **Viva said:**
> You rarely need to use any commands in ubuntu, so you need not memorize any.

that depends on how you like to get things done:D

---

### Post by wscheer on 2009-08-05
MelDJ,
When I first started using Ubuntu, I printed out these cheat sheets and they were pretty helpful. I liked it for restarting apache and other little tasks like that. It will become second nature after awhile. You won't really need to use a whole lot, since most tasks can be accomplished by copy/paste from a web page into your terminal.



fosswire ubuntu reference: [http://files.fosswire.com/2008/04/ubunturef.pdf](http://files.fosswire.com/2008/04/ubunturef.pdf)

a little folding pamphlet page: [http://xinocat.com/refcard/refcard-en-a4.pdf](http://xinocat.com/refcard/refcard-en-a4.pdf)

---

### Post by SunnyRabbiera on 2009-08-05
In any case one can cheat the command line if you know what to do, me I installed gksu-nautilus to bypass having the need to go into command line to open up nautilus in administrator mode.
But in any case Ubuntu does things differently then Windows, and other Linux distros.
I rather like the sudo approach as it means less passwords to remember yet you still have the security that linux holds over windows.

---

### Post by LunaticHiatus on 2009-08-05
Ah, the good olde command line vs gui debate. I see the gui is just a point and grunt and things like bash as a full fledged language. pointing and grunting works, but can be very ineffenct and slow. Speaking the native language takes a lot to learn, but is fast and handy.

---

### Post by ajgreeny on 2009-08-05
> **Viva said:**
> You rarely need to use any commands in ubuntu, so you need not memorize any.
You may not need to, but by Jove, it helps if you do know a few of the common ones and do a bit of reading.  It is often quicker to use the terminal than anything else, and a few utilities which you may find useful later in your ubuntu time are terminal only with no GUI available, eg tune2fs, mp3splt, mp3wrap, which I use a fair bit.

Don't be afraid of the terminal, it's an incredibly useful tool.

---

### Post by Viva on 2009-08-05
> **ajgreeny said:**
> You may not need to, but by Jove, it helps if you do know a few of the common ones and do a bit of reading.  It is often quicker to use the terminal than anything else, and a few utilities which you may find useful later in your ubuntu time are terminal only with no GUI available, eg tune2fs, mp3splt, mp3wrap, which I use a fair bit.

Don't be afraid of the terminal, it's an incredibly useful tool.

I agree with that, but trying to memorize commands is not the way to go. You'll remember them as you use them.

---

