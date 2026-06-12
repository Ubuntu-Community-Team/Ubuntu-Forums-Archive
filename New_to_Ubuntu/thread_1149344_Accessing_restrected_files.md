---
title: "Accessing restrected files"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by triunenature on 2009-05-05
So, some background.

I created a second user and named it guest.  gave it no password by doing a little trick i read about.

Anyway... that all went dandy, however out of courisoity, i was trying to see what i could do in the guest account.

So i restrected access to /home/guest via the guest account (right clicked the file and made it where only guest could access it)

Then i went to my main account, and was trying to see how to use my admistrative abilitys

I went to the file and double clicked it... access restrected. (ok... well at least this will be fun)

Terminal ->
```

CD /home/guest
Permission denied.

```
Ok... well i know how to fix that

```
sudo cd /home/guest
sudo: cd: command not found

```

Well now im stuck...  How does the administrator access restrected files?  (I mean i could always log back into guest and unrestrect them, but thats no fun)

---

### Post by skymera on 2009-05-05
If you've stopped access from the Guest account using Guest. That means only guest can look and write to files.

That means you can't, nor can root. Neither of you have permissions.

---

### Post by triunenature on 2009-05-05
> **skymera said:**
> If you've stopped access from the Guest account using Guest. That means only guest can look and write to files.

That means you can't, nor can root. Neither of you have permissions.

Now thats odd. One would think root could over-ride a secondary account.  Isn't that kinda what sudo was made for?

Surely there is a way past this... chmod maybe?

---

### Post by freak42 on 2009-05-05
the problem is that 'cd' is not really a program, but a bash built-in command (like for instance echo), that's why sudo doesn't work. (ls is a program (try where ls and where cd, there sudo works).

What you can make is a bash (command-line instance) with root rights:
sudo bash

you'll be asked for your password, and then you see a root command line.. there you should be able to change into your guests directory and do stuff

when you're done type 
exit 
to leave the root command shell

---

### Post by triunenature on 2009-05-05
> **freak42 said:**
> the problem is that 'cd' is not really a program, but a bash built-in command (like for instance echo), that's why sudo doesn't work. (ls is a program (try where ls and where cd, there sudo works).

What you can make is a bash (command-line instance) with root rights:
sudo bash

you'll be asked for your password, and then you see a root command line.. there you should be able to change into your guests directory and do stuff

when you're done type 
exit 
to leave the root command shell

Thank you!!!!!!!!

Last question, how can i access files via terminal (lets say /home/guest/test.jpg was a file i wanted to access how would i do it

```

sudo bash
pw:

```
New terminal
```

cd /home/guest

```

(if it was a text file, gedit works, but with a picture or what have you, how can i access it?

---

### Post by _Purple_ on 2009-05-05
> **triunenature said:**
> Thank you!!!!!!!!

Last question, how can i access files via terminal (lets say /home/guest/test.jpg was a file i wanted to access how would i do it

```

sudo bash
pw:

```
New terminal
```

cd /home/guest

```

(if it was a text file, gedit works, but with a picture or what have you, how can i access it?


You can use the default image viewer eye of Gnome
```
eog image.jpg
```

Or you can use gimp or any other image viewer/ editor of your choice
```
gimp image.jpg
```

---

### Post by freak42 on 2009-05-05
> **triunenature said:**
> Thank you!!!!!!!!

Last question, how can i access files via terminal (lets say /home/guest/test.jpg was a file i wanted to access how would i do it


slightly off-topic, you can also use nautilus (the fileviewer/'explorer' of ubuntu) with root rights:

sudo nautilus

that way you can graphically browse to the guests files and should be able to double-click them to open them with whatever application is configured for the file type.. (obviously you can also copy,delete and change permissions of files)

hth

---

### Post by alphacrucis2 on 2009-05-05
> **freak42 said:**
> slightly off-topic, you can also use nautilus (the fileviewer/'explorer' of ubuntu) with root rights:

sudo nautilus

that way you can graphically browse to the guests files and should be able to double-click them to open them with whatever application is configured for the file type.. (obviously you can also copy,delete and change permissions of files)

hth

Should actually be

```
gksu nautilus
```

---

### Post by triunenature on 2009-05-05
Ok perfect 

```

sudo nautilus

```

THATS exactly what i was looking for... thank you sooo much

---

### Post by _Purple_ on 2009-05-05
> **triunenature said:**
> Ok perfect 

```

sudo nautilus

```

THATS exactly what i was looking for... thank you sooo much

For graphical applications, gksudo should be used instead of sudo as alphacrucis2 already mentioned. For more information, 
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

