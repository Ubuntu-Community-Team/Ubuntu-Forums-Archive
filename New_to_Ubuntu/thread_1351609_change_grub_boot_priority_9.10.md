---
title: "change grub boot priority 9.10"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by nutpants on 2009-12-10
just installed ubuntu 910 dual booting with windows xp
now i want to make it so windows boots by default and ubuntu is the next choice.

normally i would edit /boot/grub/menu.lst

but that is gone

how do i change grub now?

nutz

---

### Post by fooman on 2009-12-10
you could always use "startupmanager"...it is available in synaptic, or in a terminal:

```
sudo apt-get install startupmanager
```

after it installs,  find it in system > administration > startup-manager

look under the boot options tab > default operating system

hope that helps

---

### Post by dansar99 on 2009-12-10
[QUOTE=nutpants;8476434]just installed ubuntu 910 dual booting with windows xp
now i want to make it so windows boots by default and ubuntu is the next choice.

normally i would edit /boot/grub/menu.lst

but that is gone

how do i change grub now?

nutz[

go to System>Administration>startup manager

---

### Post by joes7 on 2009-12-10
> **fooman said:**
> you could always use "startupmanager"...it is available in synaptic, or in a terminal:

```
sudo apt-get install startupmanager
```after it installs,  find it in system > administration > startup-manager

look under the boot options tab > default operating system

hope that helps

Start Up Manager is awesome. It helped me solve the same problem, believe me, it will work.

---

### Post by joes7 on 2009-12-10
> **nutpants said:**
> just installed ubuntu 910 dual booting with windows xp
now i want to make it so windows boots by default and ubuntu is the next choice.

normally i would edit /boot/grub/menu.lst

but that is gone

how do i change grub now?

nutz

It isn't gone, by the way, it isn't visible because you don't have enough permissions. If you want to edit it manually, you'll have to log in as the "root" user. I recommend Star Up Manager.

---

### Post by nutpants on 2009-12-10
> **joes7 said:**
> It isn't gone, by the way, it isn't visible because you don't have enough permissions. If you want to edit it manually, you'll have to log in as the "root" user. I recommend Star Up Manager.

how can i not have enough permissions when i run gedit under sudo?
 i should have permission to do anything good or bad.

has that changed?

nutz

(thanks for the info.)

---

### Post by nutpants on 2009-12-10
ok it worked
but i hate it..
i liked being able to change the list
so that they were in order of preference
1 windows
2 linux
3 other
4 yet another.


although this makes it easier for the cli limited.

any way to reorder the list?

nutz

---

### Post by joes7 on 2009-12-10
> **nutpants said:**
> ok it worked
but i hate it..
i liked being able to change the list
so that they were in order of preference
1 windows
2 linux
3 other
4 yet another.


although this makes it easier for the cli limited.

any way to reorder the list?

nutz

By using Start Up Manager you can change the GRUB menu timeout (time it is shown) and select any OS to be the first one to be selected.
E.g, Ubuntu can be the first one on the list, but Windows can be the first one to be auto-highlighted. If you have any doubts, reply, I will help you :)

---

### Post by oldfred on 2009-12-10
When you run update-grub it processes the files in order. If you copy 30_osprober to 09_osprober and set executable on and turn off executable on 30_osprober, the prober will put the files it finds first.

If your windows entry never changes you can do the same thing by copying 40_custom to 09_custom and copy the entry from grub.cfg into the 09_custom. Make it executable and run update grub.

You can turn off osprober also with an entry in /etc/default/grub 
GRUB_DISABLE_OS_PROBER=true

Grub2 info by ranch hand and many links to other grub2 info sites 
[http://ubuntuforums.org/showthread.php?p=8191211#post8191211](http://ubuntuforums.org/showthread.php?p=8191211#post8191211)

---

### Post by Crash~Override on 2009-12-10
hmmm i did not know about the startup manager....i always went into Grub's menu and manually edited it to set windows to default...

Well another thin i learnt!

---

### Post by murthy on 2009-12-16
I dual boot with win vista and ubuntu.  Changing the default in startup-manager has not changed the default to vista. Please help.

---

### Post by oldfred on 2009-12-16
I found another way to edit boot order. You have to copy the entry from grub.cfg exactly.

If you refer to Windows by its number, you will have to edit on every update. But Grub 2 also lets you use the title. Suppose your Windows title is "Windows Vista (on /dev/sda1)". Then you can use in /etc/grub/default, and you won't have to edit Grub after kernel updates.

GRUB_DEFAULT="Windows Vista (on /dev/sda1)"

---

### Post by MaggiesDad on 2009-12-16
I also had a failure of startup manager. Tried the order of boot change and the timeout and both failed. This may be caused by a failed update to grub2. I had 9.10 loaded and the update manager called for a bunch of updates. (156 I think.) When done I had an extra entry in the boot screen and the loader failed on the first one which was the newest. Would load on the second that was the original one (for linux) could step to the xp on either. 
I located the grub 2 and removed it but now the entries are the same and either one will boot to linux. I am not really broke but would like to change the order of boot and hate to have errors around that will come back to haunt later. 
Looks like this.

Ubuntu.linux.2.6.31 -16-generic
Ubuntu.linux.2.6.31 -16-generic recovery
Ubuntu.linux.2.6.31 -14-generic
Ubuntu.linux.2.6.31 -14-generic recovery
Memory test (not exact text)
Memory test (same as above)
windows xp
(generic 14 was the original entry)

Not sure this is all update problem or grub but this thread looked real appropriate, hope I have not intruded, if so can create new thread.

---

### Post by rmjohnson144 on 2009-12-28
> **fooman said:**
> you could always use "startupmanager"...it is available in synaptic, or in a terminal:

```
sudo apt-get install startupmanager
```

after it installs,  find it in system > administration > startup-manager

look under the boot options tab > default operating system

hope that helps

Thank you so much, I have been searching for a few hours for this simple solution.

-=Mark=-

---

