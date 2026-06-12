---
title: "what is included in Ubuntu 9.10"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by U-boy on 2009-11-14
Hi there,

I wonder can one find the list of all included packages, utilities, applications and other stuff as well into Ubuntu. More specifically Ubuntu 9.10 

The reason that I'm asking is that when I read the books on  Linux it will say do this and this. But it won't work on my Ubuntu 9.10. Well not always. Sometimes.

---

### Post by Paqman on 2009-11-14
Er, ALL the packages? That's waaaaay too many to list.

Go to System > Admin > Synaptic Package Manager and filter for installed packages. You can search and see what you've got on your system.

Some of the main changes in Karmic:
[LIST]
[*]HAL started getting replaced by DevieKit, mean some power management stuff has changed (Eg: some apps that used to inhibit sleep might not any more)
[*]Pidgin got replaced by Empathy
[*]Usplash got replaced by Xsplash meaning some things like the login window utility have had to change.
[*]Grub is out, Grub2 is in. That means things like startupmanager have had to be modified.
[*]Ext4 is now the default file system instead of ext3.
[*]There's a brand new disk health monitoring utility.
[/LIST]

And there's probably lots i've forgotten about. It was a pretty big update.

---

### Post by slakkie on 2009-11-14
A livecd will could tell you what is installed on a default Ubuntu installation.

---

### Post by camaron1 on 2009-11-14
> The reason that I'm asking is that when I read the books on Linux it will say do this and this. But it won't work on my Ubuntu 9.10. Well not always. Sometimes.

Like what? If you are more specific...

---

### Post by Penguin Guy on 2009-11-14
To create a plain text list on your desktop, run this:
```

dpkg --get-selections > "~/Desktop/Package List"

```
I wouldn't advise this though - it'll be a *very* long list (mine was 1805 lines long).

---

