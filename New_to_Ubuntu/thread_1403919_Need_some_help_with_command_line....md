---
title: "Need some help with command line..."
date: 2010-02-10
forum: New to Ubuntu
---

### Post by gshockxc on 2010-02-10
I'm trying to type the following command...
```

gedit /mnt/Kristan's iPod/ipod_control/Device/SysInfo

```

When when I do that, I lose the $ - prompt.  And nothing happens.  

How do I navigate to a directory where the name has spaces or odd characters?

Thanks,

---

### Post by mvalviar on 2010-02-10
> **gshockxc said:**
> I'm trying to type the following command...
```

gedit /mnt/Kristan's iPod/ipod_control/Device/SysInfo

```

When when I do that, I lose the $ - prompt.  And nothing happens.  

How do I navigate to a directory where the name has spaces or odd characters?

Thanks,

The shell is waiting for a closing quote. To insert spaces you could wrap the whole path with quotes.```
gedit '/mnt/Kristan's iPod/ipod_control/Device/SysInfo/'
```

---

### Post by gshockxc on 2010-02-10
Unfortunately, that didn't work.  Same result.  

How do I kill the process while it's waiting?  I've tried random stuff.  <esc> just lists the files/folders in the home directory.

---

### Post by paul_in_london on 2010-02-10
You need to "back slash escape" special characters like quotes and spaces in filenames so that the shell doesn't attribute any special meaning to them. Try the command like this:

```
gedit /mnt/Kristan\'s\ iPod/ipod_control/Device/SysInfo
```

Quick google:

[http://www.tuxfiles.org/linuxhelp/weirdchars.html](http://www.tuxfiles.org/linuxhelp/weirdchars.html)

The fact that you have a quote in the filename makes escaping a better option imho.

---

### Post by gshockxc on 2010-02-10
Brilliant.  That worked great.  I was using gedit, and I thought that would work. How can I execute the same command, but with root privileges to edit the file?

I tried ```
 gksudo /media/Kristan\'s\ iPod/iPod_Conrol/Device/SysInfo
```

It would let me open it, but I couldn't save changes.

Thanks for the help.

---

### Post by Miljet on 2010-02-10
```
 gksudo  gedit /media/Kristan\'s\ iPod/iPod_Conrol/Device/SysInfo
```

---

### Post by tacantara on 2010-02-10
With the gksudo command, I find that using it to open Nautilus, then navigating to the folder/file allows me to edit files.  In short:

```
gksudo nautilus
```

to open the Nautilus file browser, then find the file you're looking for and open it.  Make your edits, and then you should be able to save the file.

---

### Post by paul_in_london on 2010-02-10
Hmm. Would have thought gksudo would have done it, although in the command you just posted [COLOR="red"]gedit[/COLOR] was missing and you had [COLOR="red"]media[/COLOR] instead of [COLOR="red"]mnt[/COLOR]? Does this work?

```
gksudo [COLOR="Red"]gedit[/COLOR] /[COLOR="Red"]mnt[/COLOR]/Kristan\'s\ iPod/iPod_Conrol/Device/SysInfo
```

---

### Post by yeats on 2010-02-10
Another command line tip:  tab autocomplete.  Just type the first few letters of the file name and tab will autocomplete it (including bashslash escapes for spaces and apostrophes) for you.  In Ubuntu bash (your default shell), this works for commands as well.

---

### Post by gshockxc on 2010-02-10
I made a mistake in my earlier command line, but I did manage to get it to work a couple of different ways ... at least getting to the file.  

This is what it should have been: ```
gksudo gedit /media/Kristan\'s\ iPod/iPod_Control/Device/SysInfo
```


But once I get the file open, it's still read only.

It might have something with it being an iPod, but the instructions I was following indicated that I should be able to modify the SysInfo file and re-save.

Any thoughts?

---

### Post by gshockxc on 2010-02-10
> **chrissharp123 said:**
> Another command line tip:  tab autocomplete.  Just type the first few letters of the file name and tab will autocomplete it (including bashslash escapes for spaces and apostrophes) for you.  In Ubuntu bash (your default shell), this works for commands as well.

Cool.  Thanks for the tip.

---

### Post by paul_in_london on 2010-02-10
Shouldn't it be gksu instead of gksudo?

Actually in Ubuntu they're the same I think...

---

### Post by gshockxc on 2010-02-10
That could very well be.  When I use the autocomplete on gk, it comes up gksu.  Makes sense.  I'll give it a shot.

When I use ```
gksu gedit /media/Kristan\'s\ iPod/iPod_Control/Device/SysInfo
```
it opens up two files, "Kristans" and "SysInfo".  Each file is opened in the /media directory.  So does that mean I need to wrap the command line in quotes?

---

### Post by paul_in_london on 2010-02-10
```
paul@lucid:~$ ls -la /usr/bin/gksudo
lrwxrwxrwx 1 root root 4 2009-11-05 21:13 /usr/bin/gksudo -> gksu
```

---

### Post by paul_in_london on 2010-02-10
What's the output of:

```
ls -lart /media/Kristan\'s\ iPod/iPod_Control/Device/SysInfo
```

---

### Post by gshockxc on 2010-02-10
Here's the output.

```
-rw-r--r-- 1 root root 0 2071-12-01 01:51 /media/Kristan's iPod/iPod_Control/Device/SysInfo

```

---

### Post by sgosnell on 2010-02-10
When you use quotes, use " instead of '.

---

### Post by paul_in_london on 2010-02-11
Still not quite sure what's happening here. Out of curiosity, if you do:

```
[COLOR="Red"]sudo nano[/COLOR] /media/Kristan\'s\ iPod/iPod_Control/Device/SysInfo
```

(i.e. using sudo instead of gksudo/gksu and a "non-graphical" editor) can you open and save the file?

Have a look at this thread as well:

[http://ubuntuforums.org/showthread.php?t=132553&highlight=gksudo+ged&page=2](http://ubuntuforums.org/showthread.php?t=132553&highlight=gksudo+ged&page=2)

There are potential pitfalls, but you could just use sudo with gedit (which is what I tend to do myself):

```
[COLOR="Red"]sudo gedit[/COLOR] /media/Kristan\'s\ iPod/iPod_Control/Device/SysInfo
```

Does that work?

From the thread I just added, try this too:

```
gksudo 'gedit /media/Kristan\'s\ iPod/iPod_Control/Device/SysInfo'
```

---

### Post by gshockxc on 2010-02-11
I'll give those a try later today.  I won't be back at my machine until this evening.  Thanks for all the help.

---

### Post by mvalviar on 2010-02-12
Sorry that should have been a " like ```
gedit "mvalviar's mistake"
``` or you could use auto-completion as mentioned above.

---

### Post by achase79 on 2010-02-12
You can also drag and drop onto the terminal to add a path.  This works great for paths like yours.

---

