---
title: "Copy file"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by Steve Moss on 2011-02-08
Sorry if this is really stupid

I am trying to copy a file from my /home directory to a wine directory which was created I think on install

I am typing the following into the console

cp streamci.dll ~/.wine/drive_c/windows/system/32

I keep getting a message " No such file or directory exists"

I definitely have the source file "streamci.dll" in a sub-directory of home

I have also typed the following command into the console

find -iname mscoree.dll and got this result

/.wine/drive_c/windows/system32/mscoree.dll

This suggest that the target directory exists

What am I doing wrong? (I appear to have the source file and the target directory)

---

### Post by if4124l on 2011-02-08
is that system/32 ? you might have mistyped it. it's system32. Also, you could use nautilus for copying files(ctrl-H to show hidden files), or use ls ~/.wine/drive_c/windows/ to check the directory.

---

### Post by jonny163 on 2011-02-08
And also, capital letters are all important. If your windows folder is called Windows, you need to write Windows :)

---

### Post by Steve Moss on 2011-02-08
Thanks

Checked the capital letters...looks OK and also checked I typed system32 and not system/32

I tried typing ls ~/.wine/drive_c/windows/ system32 is there

---

### Post by howefield on 2011-02-08
Try Nautilus, 

Go to Places > Home and press Ctrl + H to view hidden files/folders.

---

### Post by ikt on 2011-02-08
> **Steve Moss said:**
> cp streamci.dll ~/.wine/drive_c/windows/system/32

I keep getting a message " No such file or directory exists"

I definitely have the source file "streamci.dll" in a sub-directory of home

Are you 100% sure you're in the same location as streamci.dll in terminal?

Use "ls -a" to see all the files in the directory you're in, and pwd to see where you are at.

---

### Post by Steve Moss on 2011-02-08
OK

Tried CTL H and found the folder is there

However what is strange is I tried this (this has been copy/paste from console)


samsung@ubuntu:~$ ls /home/samsung
Desktop    examples.desktop  Public                       Ubuntu One
Documents  Music             Templates                    Videos
Downloads  Pictures          translog.20110204103203.log
samsung@ubuntu:~$ ls /home/samsung/downloads/
ls: cannot access /home/samsung/downloads/: No such file or directory

This is odd cos the first ls command says "downloads" exists the second says it cant find it

---

### Post by migs73 on 2011-02-08
> **Steve Moss said:**
> OK

Tried CTL H and found the folder is there

However what is strange is I tried this (this has been copy/paste from console)


samsung@ubuntu:~$ ls /home/samsung
Desktop    examples.desktop  Public                       Ubuntu One
Documents  Music             Templates                    Videos
**Downloads**  Pictures          translog.20110204103203.log
samsung@ubuntu:~$ ls /home/samsung/downloads/
ls: cannot access /home/samsung/**downloads**/: No such file or directory

This is odd cos the first ls command says "downloads" exists the second says it cant find it

Downloads not downloads. It's the caps again.

---

### Post by ikt on 2011-02-08
> **Steve Moss said:**
> OK

Tried CTL H and found the folder is there

However what is strange is I tried this (this has been copy/paste from console)


samsung@ubuntu:~$ ls /home/samsung
Desktop    examples.desktop  Public                       Ubuntu One
Documents  Music             Templates                    Videos
Downloads  Pictures          translog.20110204103203.log
samsung@ubuntu:~$ ls /home/samsung/downloads/
ls: cannot access /home/samsung/downloads/: No such file or directory

This is odd cos the first ls command says "downloads" exists the second says it cant find it

Capital D, yeah I stuffed that up the first time as well :p

---

### Post by Joeb454 on 2011-02-08
Remember the terminal is case sensitive, so you would need ```
ls /home/samsung/Downloads
```

---

### Post by migs73 on 2011-02-08
You would think the default folder names would not be capitalised as EVERYBODY makes this mistake. I still do!

---

### Post by Steve Moss on 2011-02-08
Success. Thanks guys!!!

So to copy a file I have to navigate to it's folder in the console?

Is there an easier way?

---

### Post by migs73 on 2011-02-08
Go to the folder in Nautilus, right click, select copy. Paste it where you want it.

If the file/folder is owned by root not you you can run;

```
gksudo nautilus
```

This gives nautilus (the file browser) sudo permissions.

---

### Post by Steve Moss on 2011-02-08
> Go to the folder in Nautilus, right click, select copy. Paste it where you want it.

Sorry to be so thick

I go to folder in Nautilus

It is empty

What do I right click?

---

### Post by migs73 on 2011-02-08
If the folder is empty, I expect you'll have to Ctrl+H to make the file you want visible ( must be a hidden file, file name starts with a .  ie  .filename). Then you can right click on it.

---

### Post by cyb3r_sn4k3 on 2011-02-08
Even I found it hard when I started with the terminal. Mostly just be careful of case,space and permissions :)

---

### Post by Steve Moss on 2011-02-08
Ok still having trouble with Nautilus

The folder is empty and there are no hidden files

---

### Post by ikt on 2011-02-08
> **Steve Moss said:**
> Success. Thanks guys!!!

So to copy a file I have to navigate to it's folder in the console?

Yep, technically you don't have to but it makes things easier, if you don't want to navigate to the right folder you would need to use the full path when copying, so if the file you wanted to copy is in your home folder but you are currently in the /etc folder, you could do:

cp /home/username/file.file /where/you/want/to/copy/it/to

If you would like to know more give this a quick read:

[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

I promise you'll be better off in the long run :)

---

### Post by Steve Moss on 2011-02-08
> Even I found it hard when I started with the terminal. Mostly just be careful of case,space and permissions

Tell me about it!!!

I have spent HOURS trying to solve it on my own before I tried posting...and thanks for all your helpful comments :)

---

### Post by Steve Moss on 2011-02-08
Thanks IKT

I may be quiet for a while as I digest this

Reminds me of DOS commands I used to know in the early nineties before I became dependant on Windows

---

### Post by migs73 on 2011-02-08
> **Steve Moss said:**
> Ok still having trouble with Nautilus

The folder is empty and there are no hidden files

Can you browse into other folders and see files?

Nautilus is the name of the file browser, just open the file you want to look in side ie. Places>Documents then it should have all your document files in it.

Is the file you want in Downloads? (Places>Downloads)

---

### Post by Steve Moss on 2011-02-08
Thanks migs73

I think I got it now

---

### Post by Steve Moss on 2011-02-08
> Even I found it hard when I started with the terminal. Mostly just be careful of case,space and permission

Great article. Thanks a lot. This was really helpful

---

