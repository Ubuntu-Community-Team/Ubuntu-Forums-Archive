---
title: "Same user logged in multiple times"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by SuaSwe on 2010-05-21
Hi all,

Running cmd 'users' on my server indicates that I am logged in six times:

suave@server:~$ users
suave suave suave suave suave suave
suave@server:~$ 

Does anyone know if this will affect Screen, so that if I log in from another location I cannot get at the screen session of one of the previous (still active) login sessions? Also, is it possible to find out which one I am logged onto currently, and can I somehow terminate the others?

---

### Post by warfacegod on 2010-05-21
Bearing in mind that I know little about servers, it's my guess that the different logins represent different processes in the guest computer. I think the only way to answer your question is for you to try it and see what happens. I don't think you'll have any problems.

---

### Post by SuaSwe on 2010-05-21
OK, do you know how to terminate user sessions? Is there like a kill command or something I could try?

---

### Post by warfacegod on 2010-05-21
> **SuaSwe said:**
> OK, do you know how to terminate user sessions? Is there like a kill command or something I could try?

I don't know. Try the server's System Monitor> Users tab if it has one.

---

### Post by ibuclaw on 2010-05-21
Use
```
who
```
To get a better represented list of users logged in.

you can then grep the tty / pts sessions displayed in the 'ps' command to find out just what they are running.

ie:
```
ps aux | grep tty7
```

Regards
Iain

---

### Post by Dougie187 on 2010-05-21
Every open terminal counts as a login. For example. I have 2 terminals open currently (every instance of screen would count as well). Here is my output.

```
users
dwj07 dwj07 dwj07
```

```
who
dwj07    tty7         May 21 06:58 (:0)
dwj07    pts/0        May 21 08:00 (:0.0)
dwj07    pts/1        May 21 08:01 (:0.0)
```

the tty7 instance is my gui login, and the two pts are the two terminals.

If you have 5 instances of screen running, you can get a list of their numbers by running
```
screen -r
```

If you only have one of them, this will reattach you to your detatched screen. If you have multiple instances it will list them, like this
```
screen -r
There are several suitable screens on:
	16594.pts-2.bespin	(05/21/10 08:15:40)	(Detached)
	16528.pts-2.bespin	(05/21/10 08:15:36)	(Detached)
Type "screen [-d] -r [pid.]tty.host" to resume one of them.

```

Then you can reattach to each one individually using the command listed
```
screen -r 16594.pts-2.bespin
```

Once in you can simply type exit to close the screen.

---

