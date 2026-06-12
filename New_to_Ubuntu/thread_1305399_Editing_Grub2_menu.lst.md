---
title: "Editing Grub2 menu.lst?"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by Lazy-buntu on 2009-10-29
Back on the legacy Grub, I could edit the menu.lst file to change the appearance of the boot menu (e.g. change Ubuntu 9.10, Linux blah blah blah to just Ubuntu 9.10 Karmic Koala).

It looks like you can't do that with Grub2. Opening menu.lst from terminal results in a blank file.

Where is the new menu.lst (if there is even one associated with Grub2)?

---

### Post by falconindy on 2009-10-29
The new menu.lst is grub.cfg. It's not meant to be edited manually.

---

### Post by autocrosser on 2009-10-29
You REALLY need to look in the closed Karmic-development forum & there is a very good tutorial in the Tutorials & Tips forum...You can't edit grub.cfg directly--there are several files in /etc/grub.d that are edited & then you do a standard sudo update-grub 

Grub2 is quite a bit harder to work with than grub, but grub2 is MUCH more powerful--do the searching & reading before edit work--the testing group has been working with grub2 for 6 months now & I for one am just really getting where I edit it without looking at the posted info.....The developer for SUM (start-up manager) will have a SUM2 out sometime in the next couple of months & that will make things much easier...

---

### Post by powel212 on 2009-10-29
You can run

```
sudo gedit /etc/default/grub
```

change "GRUB_DEFAULT=0" to "GRUB_DEFAULT=[COLOR="Red"]4[/COLOR]" Change the number in red to the coresponding number of your desired boot OS, I used 4 because that is my where my win install is.

then

Code:

```
sudo update-grub
```

The last line is important as i tried it once without running the grub update command and it didn't stick.

I hope that helps

---

### Post by Lazy-buntu on 2009-10-29
I use start up manage also, but I always used to edit menu.lst for aesthetic reasons I mentioned before. I don't want one partition to show up, I want to change the entry names on others, etc.

---

### Post by Lazy-buntu on 2009-10-29
> **powel212 said:**
> You can run

```
sudo gedit /etc/default/grub
```

change "GRUB_DEFAULT=0" to "GRUB_DEFAULT=[COLOR="Red"]4[/COLOR]" Change the number in red to the coresponding number of your desired boot OS, I used 4 because that is my where my win install is.

then

Code:

```
sudo update-grub
```

The last line is important as i tried it once without running the grub update command and it didn't stick.

I hope that helps

Default OS isn't my problem, I'm trying to edit entry names

---

### Post by autocrosser on 2009-10-29
> **Lazy-buntu said:**
> I use start up manage also, but I always used to edit menu.lst for asthetic reasons I mentioned before. I don't want one partition to show up, I want to change the entry names on others, etc.

Understood--I ALWAYS edit my grub entries--you really need to do some reading on grub2 before you do anything--MUCH has changed........Look at the Tutorial thread---it was done by a fellow Alpha-tester & is the best guide on the topic to date.

And there were a couple of great threads in the closed forum about that very topic....

---

### Post by kaibob on 2009-10-29
These are two instructive threads on this issue. The second link has directions to do what you want. Unfortunately, editing grub2 is not as easy as it was with grub1. 

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by The Cog on 2009-10-30
If you're a real control freak, you can remove the executable flag from all the little scripts in /etc/grub.d except for the custom one, and then put all the grub.cfg lines you want in there. That way, when update-grub runs it'll just put the contents you defined. As far as I can tell, that's the only easy way of controlling which bootable partitions get listed in the menu.

---

