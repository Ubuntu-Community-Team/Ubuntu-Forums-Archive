---
title: "ubuntu forum advice seems to have nuked my computer - help? (/tmp permissions)"
date: 2011-08-12
forum: New to Ubuntu
---

### Post by lakitu on 2011-08-12
was running low on disk space, so i just did the instructions on [http://ubuntuforums.org/showthread.php?p=11143262](http://ubuntuforums.org/showthread.php?p=11143262) (i.e. 

> **bodhi.zazen said:**
> change the location in what way ?

did you make a new partition ?

Or do you have a new directory ?

If you are using a new directory, use mount --bind

mount --bind /new /tmp

add a line to fstab

```
/new  /tmp  none bind
```

You need to set the proper permissions of /tmp

```
sudo chown root.root /tmp[FONT=monospace]
[/FONT]sudo chmod 1777 /tmp
```


)

& it nuked my ubuntu. (for anyone curious i was trying to move my tmp folder so i could do aptoncd.) after doing the above, i couldn't boot - got a command prompt; so i had to live cd gksu gedit my fstab back to before that line --

it kind of seems to be working, except *my file manager won't open* - kind of a big problem. i'm wondering (i'm in ubuntu 10.10) *what do i need to do to restore from doing the above commands* - did he mean /new instead of /tmp? 

i can copy the exact commands i did: 

```
sudo mount --bind /media/data/tmp /tmp
sudo gedit /etc/fstab 
``` & added ```
/new  /tmp  none bind

```
```
sudo chown root.root /tmp
sudo chmod 1777 /tmp

``` 


please pardon any incorrect etc info AS i have aphasia - sorry


- joe

p.s. for clues, the desktop background nor icons will load (not even disks / drives) - opening the file manager just does nothing - BUT WHEN I RESTART, it says "file manager still running" or something.. web works (on it now), & IRC.. cairo dock. dunno. =/

---

### Post by lakitu on 2011-08-12
i freed up more space (800 some mb should be sufficient..), but still same problems. i CAN use gksu nautilus - sometimes the background loads (not a big deal, just a clue to help you figure out what's going on) sometimes it doesn't.

any ideas?

---

### Post by lakitu on 2011-08-13
so - i am currently working on a total format. backing up everything & trying to restore what little i can.

does anyone have a piece of info that could save me the trouble? it is not easy - i don't mean to be a jerk - but it is not easy with aphasia to do all that.

any help in the alps?

- joe

---

