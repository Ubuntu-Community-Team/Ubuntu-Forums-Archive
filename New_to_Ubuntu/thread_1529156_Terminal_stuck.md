---
title: "Terminal stuck"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by Georgia boy on 2010-07-11
I had to do a cd desktop in terminal to update the HPLIP. Now it's stuck there. Won't go back to home. Tried cd /home/thomas/ still no go.

Thanks

Tom

---

### Post by Georgia boy on 2010-07-11
Sorry, forgot to include screen shot.

Tom

---

### Post by MooPi on 2010-07-11
Try just ```
cd
```
It is how I go to home directory

---

### Post by Georgia boy on 2010-07-11
Tried but got this:
thomas@thomas-desktop:~$ cd
thomas@thomas-desktop:~$ 

I mean it shouldn't read what it says right? Should be something else not desktop?

Bad day altogether in this system for some reason.

Even tried cd /home/thomas/ and still got the same thing.


Tom

---

### Post by Georgia boy on 2010-07-11
thomas@thomas-desktop:~$ pwd
/home/thomas
thomas@thomas-desktop:~$ 

That's what I got when I did pwd.Came up with /home/thomas. But should the terminal be reading thomas@thoms-desktop:~$  ?
 Shouldn't it be reading something else or am I just tired and brain is fried and asking a stupid question?

I know, I set myself up for the answers that follow didn't I? ;)

Thanks

Tom

---

### Post by tjwoosta on 2010-07-11
lol, lets break this down for you

thomas@thomas-desktop:~$

thomas =  your username

thomas-desktop = your hostname (what you named your machine)

the directory doesnt start untill after the :

right now your in ~, which IS your home directory. 

If you want to go to your desktop directory try

```
cd Desktop
``` 
(with a capital D)

it should say 

thomas@thomas-desktop:~/Desktop$

---

### Post by iMisspell on 2010-07-11
Just to add alittle more to what tjwoosta said.
You are currently in yout 'Home' folder.
Your home folder holds your desktop (along with many other folders).

While you are in your home folder, you can use the following to see what else is in there.
```
ls -la
```


_

---

### Post by Georgia boy on 2010-07-12
Man was my brain fried yesterday! For some reason I kept thinking that my terminal home should have read something different. Told you that I would deserve whatever followed in the comments. :oops:

Messing around in the system trying to fix my scanner problems fried it and when I went into terminal to check something after having been in the Desktop installing the latest version of HPLIP for some reason I thought that I was still in the Desktop directory. Embarrassing totally. Was in home all along thinking that I was in Desktop. Told you I was fried. 

Thanks for not rubbing it in too hard. :lolflag:

Now, if I can only get that dang scanner back into operating I'd be as happy as a pig in a mudhole.

Thanks

Tom

---

