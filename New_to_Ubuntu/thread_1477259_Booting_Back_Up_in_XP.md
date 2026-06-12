---
title: "Booting Back Up in XP"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by lulabelf on 2010-05-08
Hi, I've got Ubuntu 10.04 and want to temporarily make XP Pro. my primary OS again.  What I am really after, since I love Ubuntu, is the ability to run Netflix movie downloads when I feel like it.  I've downloaded Boxee and don't understand how to use it.  Virtual software, I don't understand and not certain it works.  So in my quest, I have done the following:
a) learned about Terminal
b) run    sudo update-grub
3) found the following information:

                                 Found linux image: /boot/vmlinuz-2.6.32-21-generic  
 Found initrd image: /boot/initrd.img-2.6.32-21-generic  
 Found linux image: /boot/vmlinuz-2.6.31-20-generic  
 Found initrd image: /boot/initrd.img-2.6.31-20-generic  
 Found memtest86+ image: /boot/memtest86+.bin  
 Found Microsoft Windows XP Professional on /dev/sda1  
 done  
 
Can anyone help me from here?  I just don't know what I need to do next to get XP to boot up again.  Also, I need specific instructions.  I'm still feeling my way around.

Thanks in advance

---

### Post by wilee-nilee on 2010-05-08
So from your description it sounds like you can't run XP at all is this correct?

---

### Post by cap10Ibraim on 2010-05-08
EDITED : wilee-nilee had replied the same so ..

---

### Post by lulabelf on 2010-05-08
> **wilee-nilee said:**
> So from your description it sounds like you can't run XP at all is this correct?

Right.  Can't run XP.  Computer boots to Ubuntu without giving me a choice as to which OS to use.

---

### Post by wilee-nilee on 2010-05-08
So post this boot script in the thread, highlight while doing so and click on the # symbol in the posting gui panel this will make it easier to read.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by sandyd on 2010-05-08
```

gksudo gedit /etc/default/grub

```Find GRUB_DEFAULT"
If it is commented out (i.e. theirs a "#" in front of the line), remove the "#".
Then make the line look like the one below
```
GRUB_DEFAULT= "Microsoft Windows XP Professional"

```Then, find "GRUB_HIDDEN_TIMEOUT"
change it so that it looks like the one below
```

GRUB_HIDDEN_TIMEOUT=5
```then save the file and run```

sudo update-grub
```

hope netflix eventually adds support for linux.

---

### Post by wilee-nilee on 2010-05-08
> **carlee said:**
> ```

gksudo gedit /etc/default/grub

```Find GRUB_DEFAULT"
If it is commented out (i.e. theirs a "#" in front of the line), remove the "#".
Then make the line look like the one below
```
GRUB_DEFAULT= "Microsoft Windows XP Professional"

```Then, find "GRUB_HIDDEN_TIMEOUT"
change it so that it looks like the one below
```

GRUB_HIDDEN_TIMEOUT=5
```then save the file and run```

sudo update-grub
```

hope netflix eventually adds support for linux.

So your going to advise this without knowing if the Lucid install may have gotten grub in stalled inside XP, or other pertinent information. OP post the bootscript before doing anything. This method might work, but with grub2 if that is what you have then this is not a correct solution as far as I know.

---

### Post by sandyd on 2010-05-08
yawn....
wubi shows the menu options by default unless the OP has been screwing with them. Which is why im not particularly concerned about him not running the boot info script

in other words, whack shift and hold it down while starting up, and youll see the grub menu.

---

### Post by wilee-nilee on 2010-05-08
Here is what mine looks like, with Karmic, and XP no mention of XP in it. I installed XP after Karmic but reloaded grub2 into sda mbr.[ATTACH]156105[/ATTACH]

---

### Post by wilee-nilee on 2010-05-08
> **carlee said:**
> yawn....
wubi shows the menu options by default unless the OP has been screwing with them. Which is why im not particularly concerned about him not running the boot info script

in other words, whack shift and hold it down while starting up, and youll see the grub menu.

carlee I respect your knowledge, but how do we know it's a wubi install, I would appreciate the information so I could recognise this in the future.

---

### Post by sandyd on 2010-05-08
> **wilee-nilee said:**
> carlee I respect your knowledge, but how do we know it's a wubi install, I would appreciate the information so I could recognise this in the future.
we know its a wubi install becasue theirs two main differences.

a) Wubi does not use GRUB 2. Instead it latches onto the windows boot loader.

b) By default, wubi will show the OS choices. This decision was made due to the fact that most developers saw wubi as a way to try out ubuntu. As a result of showing the OS choices, newbies can easily boot to different OSes. If the menu isn't showing, it means that theirs a problem with the WUBI install / C:\boot.ini, and as a result, the commands I posted won't even do anything to his bootloader.

c)If he can already run grub-update, it means he installed grub. And I really don't see why someone would manually install grub if their computer is working fine in the first place.

---

### Post by wilee-nilee on 2010-05-08
> **carlee said:**
> we know its a wubi install becasue theirs two main differences.

a) Wubi does not use GRUB 2. Instead it latches onto the windows boot loader.

b) By default, wubi will show the OS choices. This decision was made due to the fact that most developers saw wubi as a way to try out ubuntu. As a result of showing the OS choices, newbies can easily boot to different OSes. If the menu isn't showing, it means that theirs a problem with the WUBI install / C:\boot.ini, and as a result, the commands I posted won't even do anything to his bootloader.

c)If he can already run grub-update, it means he installed grub. And I really don't see why someone would manually install grub if their computer is working fine in the first place.

I recognise that the commands will do no harm. 

Maybe this is a regular dual-boot and like others during the install grub was put in XP and Lucid. There has also been a grub update that pops up a screen that gives you a choice of where to put grub, with a if you not sure put it in multiple partitions, like the dist-upgrade grup popup. If a person has installed grub manually, or in XP and Lucid then the script is important to get to the matter of things. 

Like I said I recognise that you are probably more experienced and knowledgeable in general, but some more info is needed I believe to get things correct. While keeping the OS intact, and not having cross contamination of differing OS files. And not leaving stuff in another OS from another OS.

peace

---

### Post by lulabelf on 2010-05-08
> **wilee-nilee said:**
> carlee I respect your knowledge, but how do we know it's a wubi install, I would appreciate the information so I could recognise this in the future.


Thanks for info.  It's still a little confusing but I'm going to try the suggestions.  We'll see what happens.

---

### Post by wilee-nilee on 2010-05-08
> **lulabelf said:**
> Thanks for info.  It's still a little confusing but I'm going to try the suggestions.  We'll see what happens.

That's fine it shouldn't cause a problem, is this a wubi or a dual boot with separate partitions and installs? And at any time did you accept multi partitions for the grub install. I you have these codes may even get you up and running, but you may still not be safe in the end.

---

### Post by lulabelf on 2010-05-10
> **wilee-nilee said:**
> So your going to advise this without knowing if the Lucid install may have gotten grub in stalled inside XP, or other pertinent information. OP post the bootscript before doing anything. This method might work, but with grub2 if that is what you have then this is not a correct solution as far as I know.


Hello.  I didn't have success with this procedure.  Instead, I got this feedback:

lydia@Puter:~$ gksudo gedit /etc/default/grub

(gedit:2115): Gtk-CRITICAL **: gtk_widget_is_ancestor: assertion `ancestor != NULL' failed

(gedit:2115): Gtk-CRITICAL **: gtk_widget_is_ancestor: assertion `ancestor != NULL' failed

(gedit:2115): Gtk-CRITICAL **: gtk_widget_is_ancestor: assertion `ancestor != NULL' failed

(gedit:2115): Gtk-CRITICAL **: gtk_widget_is_ancestor: assertion `ancestor != NULL' failed
lydia@Puter:~$ sudo update-grub
/etc/default/grub: 4: Microsoft Windows XP Professional: not found


Does this mean that access to Microsoft Windows is lost to me permanently?  I started out by loading  a cd installation of Ubuntu 9.10 into my XP.  I assumed I would have a choice as to which OS I could use.  Not!  Tried to get help in the forum; gave up and took another direction of downloading Ubuntu 10.4 - because I actually like the OS.   Now it bothers me that I can't access my XP.    Am I going to have to uninstall Ubuntu all together?  I do have directions on that, but at this point, I'm not certain of anything working.  Just plain frustrated!!!!!!!!!!!!

---

### Post by lulabelf on 2010-05-11
> **carlee said:**
> ```

gksudo gedit /etc/default/grub

```Find GRUB_DEFAULT"
If it is commented out (i.e. theirs a "#" in front of the line), remove the "#".
Then make the line look like the one below
```
GRUB_DEFAULT= "Microsoft Windows XP Professional"

```Then, find "GRUB_HIDDEN_TIMEOUT"
change it so that it looks like the one below
```

GRUB_HIDDEN_TIMEOUT=5
```then save the file and run```

sudo update-grub
```hope netflix eventually adds support for linux.


Hello - don't know if you're still out there.   I tried this solution.  Now when I enter sudo update-grub, it reads that my XP Pro file is missing - can't find.   Yet, it shows up in my Gparted screen.     I'm close to blowing up my computer!    Any advice at this point would be helpful.   I'm still just a tinkering novice.   Thanks.

---

### Post by ync333 on 2010-06-19
@lulabelf

I just had the same problem

first run
     
     ```
sudo update-grub
```

 You'll get something similar:
```
Generating grub.cfg ...
Found linux image> /boot blabla
Found initrid
Found blah
Found Microsoft Windows XP ....
```

 count the number of found images, then subtract 1 from it(because computers start counting at 0). So in this example, it would be 4-1=3

Then do everything what you just quoted from carlee EXCEPT that you insert that number :

     ```
GRUB_DEFAULT= 3
``` 
INSTEAD OF:
     ```
GRUB_DEFAULT= "Microsoft Windows XP Professional"
``` 
I don't know what "GRUB_HIDDEN_TIMEOUT=5" means, maybe you have to change it too to the number you calculated before if it doesn't work.

---

