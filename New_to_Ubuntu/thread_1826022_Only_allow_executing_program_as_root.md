---
title: "Only allow executing program as root"
date: 2011-08-16
forum: New to Ubuntu
---

### Post by MG&amp;TL on 2011-08-16
I have written a program, however it modifies  system files. :twisted:

I would like this to be only able to run as root, otherwise the .sh files it runs on fail, as they are not root. If I execute my program as root, it works (obviously).

How would I make it so that it will ONLY execute as root? (i.e. like the prompt shown by synaptic when you open it)

Thanks for help (I consider this a 'noob' question, so I put it here. Feel free to move if wished.) :)

---

### Post by androssofer on 2011-08-16
> **MG&TL said:**
> I have written a program, however it modifies  system files. :twisted:

I would like this to be only able to run as root, otherwise the .sh files it runs on fail, as they are not root. If I execute my program as root, it works (obviously).

How would I make it so that it will ONLY execute as root? (i.e. like the prompt shown by synaptic when you open it)

Thanks for help (I consider this a 'noob' question, so I put it here. Feel free to move if wished.) :)

this is how i think its done: 

fire up terminal (cus using the term 'fire up' is fun)

log in as root:

```
su
```

if root isnt set up yet. (by default it isnt on ubuntu). on the forum we can only point you to this [article]("https://help.ubuntu.com/community/RootSudo") to show you how. (they are funny about it)

navigate to the place wer the file is.

and do:

```
chmod 744 filename
```

this will mean only root can execute it, and other can only read.

(havent tested this, and might b a simpler way, but i rekon it'll work ;-) )

---

### Post by androssofer on 2011-08-16
ignore that! thot of a btr way (its still early in the am for me!)

fire up terminal

go to where the file is, then do:

```
sudo chown root:root filename
```

then:

```
sudo chmod 744 filename
```

and tht will work! and u dnt hav to login as root or any crap like tht!

(havent tested it... :p )

---

### Post by MG&amp;TL on 2011-08-16
Thanks androssofer! Works geat, now can continue on my programming voyage 

I was VERY tempted by logging in as root, but anyway...

Incidentally, how do you make something open in a terminal when you double click on it? Currently I have to run it from a terminal, otherwise nothing happens :(

Thanks, for the help, especially in the morning (morning here too, been up since 6 developing) :shock:

---

### Post by androssofer on 2011-08-16
> **MG&TL said:**
> Thanks androssofer! Works geat, now can continue on my programming voyage 

I was VERY tempted by logging in as root, but anyway...

Incidentally, how do you make something open in a terminal when you double click on it? Currently I have to run it from a terminal, otherwise nothing happens :(

Thanks, for the help, especially in the morning (morning here too, been up since 6 developing) :shock:

woo! gdgd. 6!? and i thot i was hard done by getting up at 8! haha.

em... i think (not at my ubuntu box atm so cant test) you can create a shortcut (or launcher as it might b called) and select run in terminal on that, then in the command part of the shortcut put the commands to cd into the folder then run the script. then when you double click on the shortcut it will run it in terminal without needing to ask :-)

---

### Post by Elfy on 2011-08-16
> I was VERY tempted by logging in as root, but anyway...

> log in as root:
su

sudo -i

---

### Post by MG&amp;TL on 2011-08-16
Thanks, forestpiskie. I did get it, just resisted the temptation :D

@androssofer, that's great :D , but what if I want to distribute it? I can't have a launcher of a launcher, can I? A shortcut of a shortcut made windows crash, but it might be different to ubuntu.

---

### Post by BinaryEnCoder on 2011-08-16
well you can add up some lines at the start of the program to do a check 
if uid is root's or less than 1000 than the program exits

---

### Post by androssofer on 2011-08-16
> **MG&TL said:**
> Thanks, forestpiskie. I did get it, just resisted the temptation :D

@androssofer, that's great :D , but what if I want to distribute it? I can't have a launcher of a launcher, can I? A shortcut of a shortcut made windows crash, but it might be different to ubuntu.

i have no idea... cud put it in a zip folder, so u hav the launcher and your script in the zip. user extracts it. then runs launcher, then it calls the script... and runs it in terminal?

---

### Post by MG&amp;TL on 2011-08-16
Hmmm...I shall research further. I kind of want it to do a little pop-up asking for permission. Is there source code for that, or is it built-in to Ubuntu? Thanks for all the help guys.

---

