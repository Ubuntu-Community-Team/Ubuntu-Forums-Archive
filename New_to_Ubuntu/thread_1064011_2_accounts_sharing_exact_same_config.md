---
title: "2 accounts sharing exact same config"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by Fabzil on 2009-02-08
Hello everyone ! 

Well, my problem is simple : **how can i create 2 differents accounts that will share absolutly everything on the computer ?**

I know it may sounds weird, but what I wanna do is that my girlfriend could use the computer and all the stuffs in it just like me (same firefox bookmarks, same installed programs), but I dont want her to have admin rights ('cause I'm not friendly). Is it possible to, like, log on the same scession but with differents rights ?

Thx !
*Glak*

P.S. : i've already dl the pocket guide, will be usefull I think
P.S.2 : sorry for bad english, i'm french

---

### Post by ptn107 on 2009-02-08
Why can't you both just use the same account?  When you need admin rights Ubuntu will ask for a password via gksu/sudo.  Just don't tell her the password and she won't be able to do anything.

---

### Post by cariboo on 2009-02-08
I would suggest that the only thing you copy to your girlfriends directory, is you bookmarks file. Then she can set up her desktop the way she wants. Use the foxmarks addon for FIrefox to keep the bookmarks in sync.

Create a directory in /home for media and set it up so that it is accessable by both of you.

Linux is designed as a multiuser system, you can set it up so that the users only have access to their own home directory, and no others.

Jim

---

### Post by sleepyjon on 2009-02-08
If you want the exact same stuff (background, res, all the same settings for all the programs)

You could try making linking her config files to yours, or move yours to a new directory and link them both.

---

### Post by Fabzil on 2009-02-09
> 
*Why can't you both just use the same account? When you need admin rights Ubuntu will ask for a password via gksu/sudo. Just don't tell her the password and she won't be able to do anything.*

Yeah, you're right, but she will need to log in at the start, so she will know the pass ;)


> *I would suggest that the only thing you copy to your girlfriends directory, is you bookmarks file. [... ] Linux is designed as a multiuser system, you can set it up so that the users only have access to their own home directory, and no others.*
Thx for taking time answering me. But we definitly wants the same config. [-(


> 
[I]If you want the exact same stuff (background, res, all the same settings for all the programs)
>You could try making linking her config files to yours, or move yours to a new directory and link them both.[/I]

Mmmm ok, I will try find out on the net what you mean and if I dont get it I will ask you :D



[B]Thx for the help ! 
Have a nice day ![/B]
[SIZE="2"]BTW I don't drink coffee. Even beeing a 3-year comp' science student, I do tea. Tea is good.[/SIZE]

---

### Post by theozzlives on 2009-02-09
> **GoLookAndKill said:**
> Hello everyone ! 

Well, my problem is simple : **how can i create 2 differents accounts that will share absolutly everything on the computer ?**

I know it may sounds weird, but what I wanna do is that my girlfriend could use the computer and all the stuffs in it just like me (same firefox bookmarks, same installed programs), but I dont want her to have admin rights ('cause I'm not friendly). Is it possible to, like, log on the same scession but with differents rights ?

Thx !
*Glak*

P.S. : i've already dl the pocket guide, will be usefull I think
P.S.2 : sorry for bad english, i'm french

FireFox has a FoxMarks addon that will store your bookmarks on a server and you two can syncronise your bookmarks. Most programs should work but only you can install new ones.

---

### Post by Fabzil on 2009-02-09
> **theozzlives said:**
> FireFox has a FoxMarks addon that will store your bookmarks on a server and you two can syncronise your bookmarks. Most programs should work but only you can install new ones.

Well, I would like to sync not only the bookmarks from Firefox ^_^. It was just an example. Keeping ubuntu up-to-date is more important for e.g. and this is what I would like. I'll look for that "files linking" stuff

thx anyway ;)

**Glak**

---

### Post by binbash on 2009-02-09
just link the configs that is all

---

