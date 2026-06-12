---
title: "ABCDE / How to override .conf file in /etc?"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by baligirl on 2010-04-19
I read some blogs that talked about using the application ABCDE to be able to automatically rip CDs to mp3 files in my home directory, and am trying to do this.  This involves writing my own configuration file named ".abcde.conf" and placing it in my /home directory.  The idea is to have this file run instead of the default "abcde.conf" file which resides in the /etc directory.  Note that I also set up my preferences to run ABCDE when a CD is popped in the drive.

So when I pop in a CD, my conf file (in my home) is supposed to automatically run and rip the CDs.  For a while I had an error with this, until I changed the permissions of my conf file using "chmod a+x" so that it could execute.  This leads me to believe that my conf file is indeed the one that is being run.

However, no matter the edits I make to this file, none of them seem to take effect!  I save the file after my edits.  I've rebooted once or twice.  But it still does not create mp3 files (it creates the default ogg files), and it doesn't put them into the directories that I tell it.  This makes me wonder if MY file is indeed the one that is running.

Do I have to do something to ensure that my /home/.abcde.conf file is being run, and not the /etc/abcde.conf file?  I was wondering if I need to edit /home/.profile or /home/.bashrc, and if so, what exactly do I need to type in there?

I am using Ubuntu 9.10.  I'm a bit of a newbie at this.  Thank you in advance for any help you might provide!

---

### Post by andrew.46 on 2010-04-19
Hi Baligirl,

In fact abcde looks first at the commandline, then ~/.abcde.conf and finally /etc/abcde.conf. The configuration file ~/.abcde.conf does not need to be executable btw. Could you post your own configuration file? If it is giving you some grief there is one you could use as a starter if you like:

[http://www.andrews-corner.org/abcde.html#mp3](http://www.andrews-corner.org/abcde.html#mp3)

and could you also just confirm that the file is in the correct place by running the following command:

```
andrew@skamandros~$**[COLOR="Red"] find $HOME -name '.abcde.conf'[/COLOR]**
/home/andrew/.abcde.conf

```

All the best,

Andrew

---

### Post by baligirl on 2010-04-19
Hi Andrew,

Your blog is indeed one that I was looking at to do this (and the most helpful, I might add!)

I ran what you asked, and I got nothing in return.

[B]jennie@laverne:/$ find $HOME -name '.abcde.conf'
jennie@laverne:/$ 

[/B]but it does appear in my home directory (in /home, not /home/jennie):
[B]
jennie@laverne:/home$ ls -la
total 36
drwxr-xr-x  4 root   root    4096 2010-04-19 21:17 .
drwxr-xr-x 21 root   root    4096 2010-04-11 16:27 ..
-rwxr-xr-x  1 root   root    2253 2010-04-19 21:17 .abcde.conf
-rw-r--r--  1 root   root    2253 2010-04-19 21:15 .abcde.conf~
drwxr-xr-x 70 jennie jennie  4096 2010-04-19 21:44 jennie
drwx------  2 root   root   16384 2010-04-11 15:26 lost+found
jennie@laverne:/home$ pwd
/home


[/B]I'm attaching this file as a txt.  I had it beefed up to do both ogg and mp3 files, and as I mentioned, the default ogg files were being created, but I took that out to just concentrate on why the mp3s were not being created.

Thank you so much for your help!  I'm looking forward to using this!

best regards,
Jennie

---

### Post by baligirl on 2010-04-19
PS  The default ogg files are still being created, even with this conf file....

-Jennie

---

### Post by baligirl on 2010-04-19
Andrew,

It finally dawned on me what you were getting at here.  I moved the .abcde.conf from /home to /home/jennie, and now it's working!  The mp3 files are showing up, and in the proper directories.  Thanks so much for your help here!  I never would have figured this out on my own.

best regards,
Jennie  ;)

---

### Post by andrew.46 on 2010-04-19
Hi baligirl,

I think I can see the problem:

> 
I ran what you asked, and I got nothing in return.

```
jennie@laverne:/$ find $HOME -name '.abcde.conf'
jennie@laverne:/$
```

but it does appear in my home directory (in /home, not /home/jennie):


The configuration file should by default actually be in the directory that corresponds with your $HOME variable rather than simply in a directory that has been called 'home'. On your system if you run the following as an ordinary user:

```
andrew@skamandros~$ **[COLOR="Red"]echo $HOME[/COLOR]**
/home/andrew
```

this will show you where the .abcde.conf file *should* go, in my case the file should be /home/andrew/.abcde.conf. All of the editing of this file and the running of abcde should be done as an ordinary user btw and in your own $HOME environment, I think you may be straying into the wrong area a little :).

Hope this puts you onto the right track,

Andrew

---

### Post by andrew.46 on 2010-04-19
Hi Jenny,

> **baligirl said:**
> It finally dawned on me what you were getting at here.  I moved the .abcde.conf from /home to /home/jennie, and now it's working!  The mp3 files are showing up, and in the proper directories. 

Our messages have crossed and in the meantime you have it all worked out :). I hope you enjoy tinkering with the configuration file and this great program!

All the best,

Andrew

---

### Post by baligirl on 2010-04-19
Andrew,

Yes, our messages did cross.  And thank you so much for your original blog posting as well!  I had ripped a number of my CDs a while ago, with some annoying GUI that needed constant monitoring, and this will be so much better!

I did change my permissions from root back to jennie, so I think I'm all set now.  THANKS!!!

Jennie

---

### Post by MrWES on 2010-04-20
> **andrew.46 said:**
> Hi Jenny,



Our messages have crossed and in the meantime you have it all worked out :). I hope you enjoy tinkering with the configuration file and this great program!

All the best,

Andrew

Nice! -- another fan of ABCDE. What a great little app.

Bill

---

### Post by andrew.46 on 2010-04-20
Hi Bill,

> **MrWES said:**
> Nice! -- another fan of ABCDE. What a great little app.

Indeed and it looks like development is starting to move along a little now:

[http://code.google.com/p/abcde/source/list](http://code.google.com/p/abcde/source/list)

although the developers are still nibbling at the edges a little...

Andrew

---

### Post by baligirl on 2010-04-23
Hi Andrew / Bill / others,

I notice that when ripping my CDs, the cover art is not downloaded into the folders with the mp3/ogg files.  I looked at the options for ABCDE, but didn't see anything related to this.  Any thoughts on how to do this, or perhaps suggestions on another program or script to run which would grab the art for me?

thank you!!!

best regards,
Jennie

---

### Post by MrWES on 2010-04-24
I just normally let my media player, such as Rhythmbox do that.

---

### Post by baligirl on 2010-04-25
Thanks Bill!  Then I'm all set here!

v/r,
Jennie

---

