---
title: "Ooops...Broken it properly!"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by Kenny_Larsen on 2010-01-26
Hi All, firslty apologies for how this comes out formatted, I'm posting from links for reasons below:

Being half asleep and not with it, I was trying to get python 3 working and without engaging brain decided to remove python 2.6. I must have hit the complete remove button as lots of stuff seemed to go awry straight after I did it. I attempted to restart and x won't boot, it tries to start in a low grpahics range but the monitor just displays out of range. I used the recovery option in the grub to boot to a networked command prompt but have no idea how to go about fixing the system! Any help would be great as I'm at a complete loss of where to start, looks like a long afternoon...that'll teach me to read before doing things as root!

Thanks in advance,

Kenny

---

### Post by SuperSonic4 on 2010-01-26
Have you tried reinstalling python 2.6?

```
sudo apt-get install python
```

---

### Post by Kenny_Larsen on 2010-01-26
> **SuperSonic4 said:**
> Have you tried reinstalling python 2.6?

```
sudo apt-get install python
```
Hi,

Yes I have re-installed python, it wa sthe first thing I did, but I think it took a lot of stuff with it. Do you know if there is a log file I can access somewhere which will tell me what was removed?

Thanks,

Kenny

---

### Post by philinux on 2010-01-26
> **Kenny_Larsen said:**
> Hi,

Yes I have re-installed python, it wa sthe first thing I did, but I think it took a lot of stuff with it. Do you know if there is a log file I can access somewhere which will tell me what was removed?

Thanks,

Kenny

It removed a helluva lot of stuff I just tried complete removal to see.
It's a long list.

/var/log/apt/term.log

---

### Post by Kenny_Larsen on 2010-01-26
That is a long list! Time to make a copy of the hard drive and re-install i feel. :(               Thanks for the log location though. kenny

---

### Post by Paqman on 2010-01-26
> **Kenny_Larsen said:**
> Time to make a copy of the hard drive and re-install i feel.

Try reinstalling ubuntu-desktop, it pulls in a ton of dependencies.

---

### Post by blazemore on 2010-01-26
Definately
Solution is uber-simple
```
sudo apt-get install ubuntu-desktop
```probem solved, but it'll install all the default apps (transmission, rhythmbox) again, if you've removed them.

---

### Post by Sef on 2010-01-26
> blazemore
Definately
Solution is uber-simple
 	Code:
 	sudo apt-get install ubuntu-desktop 
probem solved, but it'll install all the default apps (transmission, rhythmbox) again, if you've removed them. 	

Actually to be correct, the code is this:

```
sudo apt-get update && sudo apt-get install ubuntu-desktop.
```

just copy and paste it in your terminal, if possible.   

The first command updates the repositories so you get the most updated programs.

---

### Post by blazemore on 2010-01-26
> **Sef said:**
> Actually to be correct, the code is this:

```
sudo apt-get update && sudo apt-get install ubuntu-desktop.
```just copy and paste it in your terminal, if possible.   

The first command updates the repositories so you get the most updated programs.

Alright, smartypants :P Don't be so pedantic.
I like to use semicolons instead of && btw, because occasionally I get the odd error with update.

---

### Post by Kenny_Larsen on 2010-01-26
Thanks all!

I ran the update then install as two lines whilst away from here :p! But I'll remember that shortcut!

Has solved it, I shall be more careful in future!

Kenny

---

