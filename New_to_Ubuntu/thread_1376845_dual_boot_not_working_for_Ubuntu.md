---
title: "dual boot not working for Ubuntu"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by tommark on 2010-01-09
Using Wubi I recently set up a dualboot for Ubuntu 9.10. All I needed to do when I turned on the computer was select Ubuntu (second choice after Windows XP)on the first screen, then select Ubuntu a second time, and it booted into Ubuntu immediately.
Now when I select Ubuntu I get a black screen that looks like the old DOS screen: the only thing on it is "sh:grub>"
I'm assuming this is one of the many Linux prompts, and have absolutely no idea how to get from this point into Ubuntu.
1- why the sudden change of boot process?
2- what can I do to return to the previous, easier process?
3- If I can't return to the previous process, what do I tell grub to convince it to let me into my usual Ubuntu operation?
Thank you very (very) much.
Tom Markham

---

### Post by meierfra. on 2010-01-09
Edit: read post 4 first.

Type this at  "grub sh>" prompt:

```

set path=/ubuntu/disks/root.disk
linux /vmlinuz root=/dev/sd[COLOR="Red"]a1[/COLOR] loop=$path ro
initrd /initrd.img
boot 

``` 

You might have to replace /dev/sda1 by /dev/sda2, or some other value.  It has to be the partition containing Wubi.  You can use 

```
search -f $path
```
to determine the partition. hd0,1 usually means /dev/sda1, hd0,2 means /dev/sda2 and so on.



Once booted in Wubi, open a terminal and type

```

sudo update-grub2

```


Hopefully this will take  care of the problem.

---

### Post by meierfra. on 2010-01-09
I just fixed a typo in my first post.

---

### Post by meierfra. on 2010-01-10
Boot into Windows and try this:

[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210")

If this does not work, try the suggestion from my first post.

---

### Post by tommark on 2010-01-10
> **meierfra. said:**
> Boot into Windows and try this:

[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210")

If this does not work, try the suggestion from my first post.
I truly appreciate your several attempts to help me. You need to know that I am really a newbie. Although I was able to write batch files in DOS with recursive parameters, I switched to Win 3.1 so I would no longer have to. Like many (millions)others, I have no desire to learn how to muck around in a command line.
I tried to enter your first suggestion several times. no luck. I changed "linuz" to "linux": no luck. I don't know how to enter several lines at the command prompt. This is not your fault, but I have no desire to learn how to.
If Ubuntu is so fragile that it refuses to boot into a GUI consistently, then it is simply not yet ready for prime time. I truly appreciate all that all of you who are trying to help us newbies are doing. But I believe you are a bunch of gifted sculptors working with really soft clay. Windows, with all its legendary faults, figured out a long time ago that getting newbies like me into a GUI reliably is the secret to success. The real secret to pervasive success in user software is NOT speed - it is ease of use. Dummies like me (Billions) have to be able to turn on a machine, boot up into an easily-useable GUI, and git 'er done. Yes, we will always have to tweak, but we will always have a reliable GUI from which to tweak. Just as when Mercedes Benz moved from a tiller to a steering wheel. Of course they were copied by Ford and Olds, and, of course, Ford and Olds (now defunct), required constant tweaking, but they were bought into by millions upon millions of people who didn't want to mess with a tiller to drive their new automobile. Who is willing to write code to watch TV?
I erased the Ubuntu installation, re-installed with Wubi, and am now faced with reconstructing all the little things I did to make it work my way. And am anxiously awaiting the next time that Ubuntu decides to be capricious.
Again - thank you for your dedication to a cause not yet worthy of you.
Tom Markham

---

### Post by sailthesea on 2010-01-10
Your problem most likely lies with your Windows installation Wubi makes Ubuntu work in a virtual environment inside Windows if your Windows fails so does Wubi
 Try a LiveCD or maybe partition for a dual boot if you have the space
 To further your analogy you are trying to fix a car without opening the bonnet

---

### Post by meierfra. on 2010-01-10
It is very likely that you will run into the same problem again.   I spend several hours yesterday researching the problem, until I found the solution I linked in post 4.  Since then I have recommend it various time, and it worked every single time. 

You just have to download one file and  replace your current file "C:\wubildr". I recommend doing it now, to prevent the same thing to happen again.

> Your problem most likely lies with your Windows installation Wubi makes Ubuntu work in a virtual environment inside Windows if your Windows fails so does Wubi

No. The problem is caused by a bug in the ntfs-module used by  Grub2. There are lots of things you can blame Windows for, but in this case Windows is innocent.

---

### Post by sailthesea on 2010-01-11
Thanks meierfra for pointing that out I had forgotten aboout the problem with 9.10 and Wubi
 I have not tried it yet There seem to be a few too many troubles as yet!:(

---

### Post by warfacegod on 2010-01-11
@meierfra.

Did anybody's wubi install *not* get totally fragged by the last round of updates? Nice work on putting together a fix. I've sent about a dozen folks to it. The ones that posted back all said it worked like a charm.

---

### Post by meierfra. on 2010-01-11
> Did anybody's wubi install not get totally fragged by the last round of updates? 
Not everybody.  It just a game of chance.  Grub2's current ntfs module can only read the first 4GB (or so) of an ntfs partition. If any of the boot files, which where updated, ended up outside the 4GB range, booting fails. 

> Nice work on putting together a fix. 
I have nothing to do with the fix. I'm just a messenger.

---

### Post by warfacegod on 2010-01-11
> **meierfra. said:**
> Not everybody.  It just a game of chance.  Grub2's current ntfs module can only read the first 4GB (or so) of an ntfs partition. If any of the boot files, which where updated, ended up outside the 4GB range, booting fails. 


I have nothing to do with the fix. I'm just a messenger.

Hey, don't kill the messenger, especially when the messenger is yourself.
You may not have made the fix but you found one and brought it here and I'm sure there are allot of grateful wubi users.

---

### Post by tommark on 2010-01-13
I keyed in as you suggested: Launchpad informs me that there is no such location. I can get as far as /ubuntu/, but no further. There seems to be no location: "+s...9/comments/210". I believe you're still assuming I'm more computer literate than I am. for example: I have no idea how to enter the 4 lines of code you suggested in Post 1. When I enter one line, hit Enter, I can't enter the next lines; when I enter the whole thing as one line, all I get is gibberish. I have no idea how to replace "C:\wubildr". What I need (and I'm sure many others also need) is a DETAILED step-by-step cure ***written for the ignorant***, not for linux experts. I train trainers for a living.Based on our several posts, it seems apparent that your expertise is more than sufficient to solve this problem. The problem is that you've walked into the 101 classroom, believing you've entered the 201 room. At best I'm still at 101. Grateful, but still discombobolated. Do you know of a beginner's text that I can buy that explains how to handle these basic problems?
Again - thank you very much.


> **meierfra. said:**
> Boot into Windows and try this:

[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210")

If this does not work, try the suggestion from my first post.

---

### Post by meierfra. on 2010-01-13
> Launchpad informs me that there is no such location. I can get as far as /ubuntu/, but no further

?????? If  I click on the link in post 4. the correct launchpad page opens up.

Anyway, let my revise my instruction:

Boot into Windows and come to this page.
Click on this link:

[http://launchpadlibrarian.net/36920146/wubildr]("http://launchpadlibrarian.net/36920146/wubildr")

Choose "save the file", if asked.

Depending on how your browser is set up,   this will either


asked you to choose a download location

or

 download the file "wubildr" to your default download location.

In the first case:  Choose "My Computer" and then  the  "C:\" drive.

In the second case, open up your File browser and navigate to your default download folder.  Also open a second file browser and navigate to "My Computer" and then  "C:\'. Drag the  file "wubildr" from the download folder to "C:\".

In both cases you should be  given a choice to  overwrite  your current "wubildr" or  to choose a different name or to cancel.  Choose to overwrite your current file.

That should be it. Reboot and  see whether you can get into Wubi.

---

