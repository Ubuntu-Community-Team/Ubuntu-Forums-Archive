---
title: "Celtx assistance... have access, but not really"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by DJTJ on 2011-07-21
Ok, I have Ubuntu and I have been reading previous threads for weeks now trying to get Celtx to work. Please read text in between images, soz images are so big.

I have access now, kind of, but have two significant and annoying problems I was hoping some of you other Ubuntu users could help me out with.

Problem 1: Can only access it in an annoying way/can't get it into launcher. Here's what I do:

[IMG]http://oi55.tinypic.com/295wtps.jpg[/IMG]
This is inside folder Celtx, I click on the file Celtx
[IMG]http://oi56.tinypic.com/vpgnmc.jpg[/IMG]
I click run
[IMG]http://oi56.tinypic.com/241l6xj.jpg[/IMG]
I get it open, everything looks fine
[IMG]http://oi53.tinypic.com/2a7trvl.jpg[/IMG]
I right click it in launcher and click on 'keep in launcher' and then close it and when I click in again in the launcher it flashes five times and then stops and nothing happens. Thus, I cannot find a way to more easily open it up

Problem 2: Whenever I save a file in Celtx, it doesn't want to open back up again. Here's what I do:

[IMG]http://oi53.tinypic.com/dzvuqp.jpg[/IMG]
I 'saved as' a piece of work in celtx. This is the saved celtx work where I saved it. For some reason it is a zip
[IMG]http://oi52.tinypic.com/1hchac.jpg[/IMG]
Here it is opened up
[IMG]http://oi55.tinypic.com/rkdmae.jpg[/IMG]
[IMG]http://oi56.tinypic.com/nwzw39.jpg[/IMG]
I get this code when I open those files in the zip up. So essentially the problem with this is not being able to reopen the celtx files as I had them when saved


Any help, anyone?

---

### Post by ajgreeny on 2011-07-21
Can you please edit this post and remove the in-line graphics, and add them as attachments.I gave up trying to read the post or deal with your problem, as on my small monitor it means continual scrolling up and down and also from side to side, and I can not keep up with where I have got to.

Attachments of a picture or pictures make life many, many times easier.

---

### Post by lykwydchykyn on 2011-07-21
When I installed celtx on my wife's computer, I did this:

1. copy the celtx folder to /opt
```

sudo cp -r ~/celtx /opt/

```
2. created a script to run it in /usr/local/bin/celtx
```

#!/bin/bash
cd /opt/celtx
/opt/celtx/celtx

```
3. Made the script executable
```

sudo chmod +x /usr/local/bin/celtx

```

4. created a file called Celtx.desktop in ~/Desktop with this in it:
```

[Desktop Entry]
Exec=celtx
Icon=/opt/celtx/icons/default48.png
Name=Celtx
StartupNotify=true

```

---

### Post by DJTJ on 2011-07-26
I have created a file as you said on point number 4.
I put it in the right place.
However I cannot open it up and write the rest in. I tried doing it with a folder also, but again the file in that didn't open up.

Any thoughts?

---

### Post by lykwydchykyn on 2011-07-27
> **DJTJ said:**
> I have created a file as you said on point number 4.
I put it in the right place.
However I cannot open it up and write the rest in. I tried doing it with a folder also, but again the file in that didn't open up.

Any thoughts?

I don't know what you mean that you can't open up the file.  How did you create the file in the first place?

Just open gEdit (or whatever text editor you prefer), copy in the text in that code box, and save as ~/Desktop/Celtx.desktop.

---

### Post by DJTJ on 2011-07-27
[ATTACH]198601[/ATTACH]

[ATTACH]198602[/ATTACH]

[ATTACH]198603[/ATTACH]

I have inserted three attachments, which are screenshots of what I did.

Nothing really happens after I have entered the code, except of course Celtx opening up after step 2.

I entered the code into the document and saved it as you said.

Then it comes up with the message in attached picture 3 when I try to open it from the desktop.

Any thoughts?

---

### Post by lykwydchykyn on 2011-07-27
The code in step 2 is not to be entered at the command line.  It's to be placed in a file at /usr/local/bin/celtx.  

You'll need sudo privs to create the file.

---

### Post by DJTJ on 2011-07-27
Can you explain that last post please.

I tried creating a file and putting that in but it won't let me save it (yes, I did a text file).

What does sudo privs mean? And what do I do with it?

---

### Post by lykwydchykyn on 2011-07-28
Please read:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You cannot edit any file outside your home directory without elevating your privileges with sudo or gksudo.  I'm afraid I'm not very familiar with Unity (using KDE myself), so the nuts and bolts of how to run a text editor such as gedit as root in Unity is not something I can walk you through.

If nothing else open a terminal and run:
```

sudo nano /usr/local/bin/celtx

```

then paste in that code I gave you.

---

