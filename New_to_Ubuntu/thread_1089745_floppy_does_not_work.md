---
title: "floppy does not work"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by minsf on 2009-03-07
remember those things called floppies?
i always wanted to move the data on my floppies to more modern external hard disk, but my floppy drive has never worked with 8.10 and i just assumed it's a hardware failure (i thought the drive was broken). 

however, i recently installed windows7 (not that i like windows a single bit- for me it's more like a "know your enemy" experiment...) and yesterday i noticed that the floppy works great there...

this makes me jealous! if win7 made it work, then there's got to be a way to make it work with my beloved ubuntu!

the problem is that i dont know how to approach this, since the floppy does not show on "sudo lshw".
so i would appreciate your help. obviously you are going to need more info- just let me know exactly what info and i'll post it here. by the way, i prefer command line hacks if possible.

---

### Post by gandaran on 2009-03-07
do you have a floppy icon mounted in media or nautilus»computer? if not see this[ bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/255651"), the fix is easy.

---

### Post by rhcm123 on 2009-03-07
Alrighty, lets start. Ubuntu likes to have people using floppies to be in the floppy group. So much that it requires it. This can be done in the gui, but first i wanna see what the extent of the problem is.

Run this with a floppy in the drive to see if ubuntu can mount it at all:
```
sudo mount /media/floppy
```

If it can but you can't read its contents without gksu nautilus, then you are not in the floppy group (or there is a much bigger problem.) Run this command to output your groups (It's very simple):
```
groups
```

If you don't see floppy in there, run this command:
```
<snip>
```

---

### Post by minsf on 2009-03-07
> **gandaran said:**
> do you have a floppy icon mounted in media or nautilus»computer? if not see this[ bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/255651"), the fix is easy.
i'm pretty sure it's not mounted as i cannot see it with the "mtab" command. maybe this is because there is no floppy line in my /etc/fstab file...
anyway, i'll check your link.
thanks

---

### Post by minsf on 2009-03-07
**_WATCH OUT:_** post #3 may break your system! if one runs the "sudo usermod -G floppy <usename>" command suggested in post #3 with the -G option alone as suggested, one will be left only with the floppy group, and all other groups will be removed. for instance, this means that one will not be able to run "sudo" (after reboot), since one is not in the administrative group anymore! 
(also, i think one needs some floppy line in fstab to be able to mount it with a simple "mount /media/floppy")
_if you did run this command like me..._ here's how i recovered (use at your own risk, as i am not an expert): press esc during a reboot to get the grub menu, choose to boot into "recovery mode" and after the boot choose to drop to root shell (option 4 i think). use "less /var/log/auth.log" and search for the time when you entered that command. you'll see exactly what groups you have been removed from, say A and B (one of these groups is probably admin). write them down. then quit with "q". and enter the command "usermod -aG A,B <username>". this will add your username back to these groups. now you can reboot normally.
--------------------------------------------------------------------

anyways, thread is solved!

_SOLUTION:_ (i found the link in the 2nd post very useful) all one has to do is enter "sudo modprobe floppy" and you'll see (and hear) the floppy in "Places" menu. if it is not there, you can also try "mkdir /media/floppy" and "sudo mount -t vfat /dev/fd0 /media/floppy". 
also, instead of loading the floppy module every time manually, one can add "floppy" to /etc/modules
many thanks to poster #2!

EDIT1: warning others of dangerous command
EDIT2: changed words to be sure nothing bad is implied about poster #3. he tried to help and just made a mistake.

---

### Post by rhcm123 on 2009-03-09
> **minsf said:**
> **_WATCH OUT:_** post #3 may break your system! if one runs the "sudo usermod -G floppy <usename>" command suggested in post #3 with the -G option alone as suggested, one will be left only with the floppy group, and all other groups will be removed. for instance, this means that one will not be able to run "sudo" (after reboot), since one is not in the administrative group anymore! 
(also, post #3 is not useful since there is no floppy line in fstab so one cannot mount it with a simple "mount /media/floppy" anyway...)
_if you fell victim to this command_, here's how i recovered (use at your own risk, as i am not an expert): press esc during a reboot to get the grub menu, choose to boot into "recovery mode" and after the boot choose to drop to root shell (option 4 i think). use "less /var/log/auth.log" and search for the time when you entered that command. you'll see exactly what groups you have been removed from, say A and B (one of these groups is probably admin). write them down. then quit with "q". and enter the command "usermod -aG A,B <username>". this will add your username back to these groups. now you can reboot normally.
--------------------------------------------------------------------


I just realized i was an idiot. I was not trying to be mailcious, but i just realized the command i wrote will break your system. It just broke mine. :) Ooops, oh well. (Logs in as root, fixes problem.)

First, don't separate groups on the command line with commas (e.g. alpha,beta,gamma) but instead use spaces (alpha beta gamma) or ubuntu interprets it as one group. Anyways, as inicated by your own solution, the symbolic link in /media/floppy was broken, and, if repaired, floppies can be mounted with the simple command sudo mount /media/floppy (similar to mounting an external drive with sudo mount /media/foobar) and this can be fixed.

Honestly, don't accuse me of being an idiot, i take it personally. I'm just here trying to have a good time helping people with their computers.

---

### Post by minsf on 2009-03-09
> **rhcm123 said:**
> I just realized i was an idiot. I was not trying to be mailcious, but i just realized the command i wrote will break your system. It just broke mine. :) Ooops, oh well. (Logs in as root, fixes problem.)
Honestly, don't accuse me of being an idiot, i take it personally. I'm just here trying to have a good time helping people with their computers.
appology accepted, mistakes happen, and i thank you for trying to help buddy! (by the way, i did not claim you were trying to be malicious, and sorry if this was interpreted this way; i just wanted to warn other newbies to not follow that command. thanks for removing it, though i think that changing the -G to -aG should fix it, that is appending "floppy" instead of replacing with "floppy". not sure though). 

the manpage of usermod suggests separating with a comma and no spaces between. at least, it worked for me. 
i still think one needs something in the fstab to be able to run "mount /media/floppy". if there's nothing in the fstab, one should probably run "mount /dev/fd0 /media/floppy". of course, the directory /media/floppy should exist before running these.
thanks again for informing me about this floppy group!
cheers

---

### Post by rhcm123 on 2009-03-09
> **minsf said:**
> appology accepted, mistakes happen, and i thank you for trying to help buddy! (by the way, i did not claim you were trying to be malicious, and sorry if this was interpreted this way; i just wanted to warn other newbies to not follow that command. thanks for removing it, though i think that changing the -G to -aG should fix it, that is appending "floppy" instead of replacing with "floppy". not sure though). 

the manpage of usermod suggests separating with a comma and no spaces between. at least, it worked for me. 
i still think one needs something in the fstab to be able to run "mount /media/floppy". if there's nothing in the fstab, one should probably run "mount /dev/fd0 /media/floppy". of course, the directory /media/floppy should exist before running these.
thanks again for informing me about this floppy group!
cheers

According to the usermod help pages, the -G flag impies -a. It obviously dosen't work, but that's what it says. Also, separating groups with commas is apparently what you do with usermod, but with useradd you have to use spaces. DAARGH!!!

No, you don't have to add anything to the fstab, you just have to make /media/floppy a symbolic link to /media/floppy0, and ubuntu *should* know to automatically mount the /dev/fd0. (At least, thats how my vanilla system works) If your in the floppy group though, HAL should mount it automatically.

---

### Post by clemm on 2009-03-12
I have the same problem. I do not have a floppy mounted and it wont let me mount one. I have changed all the permmissions I could find and I still have no floppy.
I need my floppy. I am user not a programmer. If I was capable of programming a computer I would probably be using my own OS. I really like Linux but these are the problems that irritate me. I have spent 4 hours tonight trying to get the damn floppy drive to work only to find its ANOTHER BUG!
These BUGS! are why i am still forced to use windows for everything except playing with a partially functioning os. I assume the excuse is the same, floppy disk manufactures havent been around long enough to write the drivers for linux? 
[email]clemm@cableone.net[/email]

---

### Post by teamcoltra on 2009-03-12
> **clemm said:**
> I have the same problem. I do not have a floppy mounted and it wont let me mount one. I have changed all the permmissions I could find and I still have no floppy.
I need my floppy. I am user not a programmer. If I was capable of programming a computer I would probably be using my own OS. I really like Linux but these are the problems that irritate me. I have spent 4 hours tonight trying to get the damn floppy drive to work only to find its ANOTHER BUG!
These BUGS! are why i am still forced to use windows for everything except playing with a partially functioning os. I assume the excuse is the same, floppy disk manufactures havent been around long enough to write the drivers for linux? 
[email]clemm@cableone.net[/email]

1) This isn't a bug
2) The post above explains how he got his floppy working
3) none of the steps that have so far been listed require a "programer" to understand, as long as your not afraid to open the terminal you should be fine.

---

### Post by minsf on 2009-03-12
@clemm
first, i would not recommend posting your email online-this generates spams most of the time.
second, even though it is not a "real" bug, i do agree that it would have been better for ubuntu to make the floppies work out of the box.
last but not least, here's what you should do in very simple steps(i assume you are using ubuntu, let us know if you are using kubuntu or something else):
a) go to Applications>Accessories>Terminal
b) type ```
echo "floppy" | sudo tee -a /etc/modules
```
c) double check that you typed this exactly as i did. no capitalization.
d) press enter.
e) you'll be asked for you password. enter it. don't worry if you dont see ****** as you type. after you type the password press enter.
f) reboot
g) after reboot the floppy should appear in the "Places" menu

---

### Post by rhcm123 on 2009-03-21
Who, calm down there. One step at a time. No need to get all upset -we've all gotten frusturated by these machines every once in awhile, but people will always be there to help. Lets take a look see.

> **clemm said:**
> I have the same problem. I do not have a floppy mounted and it wont let me mount one. I have changed all the permmissions I could find and I still have no floppy.
Don't randomly chmod/chown things. I chowned everything in the root directory to my name when i was scewing around one day - bad idea.

are you sure you don't have a floppy mounted? run di (probably will have to install it) to see if you have anything mounted to /media/floppy0 (post if you have trouble interpreting the output).

> **clemm said:**
> 
I need my floppy. I am user not a programmer. If I was capable of programming a computer I would probably be using my own OS. I really like Linux but these are the problems that irritate me. I have spent 4 hours tonight trying to get the damn floppy drive to work only to find its ANOTHER BUG!

I must say i loled a little at "probably be using my own OS." I'm a programmer and building my own OS is so daunting i stay with the commerically maintained distros. :) -nobody want's the hassle of OS programming. There are problems that irritate me too - like my IE using friends (idiots) not being able to use my server's FTP system. That irritates me.

This problem probably isn't a bug, as floppy drives are very generic and have been around for ages. You probably have a misconfiguration somewhere.

> **clemm said:**
> 
These BUGS! are why i am still forced to use windows for everything except playing with a partially functioning os. I assume the excuse is the same, floppy disk manufactures havent been around long enough to write the drivers for linux? 
Forced to use windows? What problems are you having? The manufactures of the drives don't write the drivers - the community does that for them now. Welcome to our world - if a big buck$ company won't do it, we get up and write our own!


Chillout man. We'll help you - read the posts above, they solved the problems ambically.

---

