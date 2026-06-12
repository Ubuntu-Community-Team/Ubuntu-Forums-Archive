---
title: "Computer Name"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by muddpup64 on 2010-03-16
How can I change my computer's name?

---

### Post by wojox on 2010-03-16
Just in the terminal:

```
gksudo gedit /etc/hostname/
```

The hostname file will open, displaying the current computer name. Replace the current computer name with the desired new name.

Click Save.

Close all open windows and restart your system.

After your system has restarted, it will have the new computer name.

---

### Post by The Cog on 2010-03-16
You must also change the name in /etc/hosts. /etc/hosts and /etc/hostname should agree.

---

### Post by doas777 on 2010-03-16
the easiest way is to hit alt + F2, and type
```
gksu nautilus
```

enter your password, and a file manager window will appear. this window is running as root so be careful with it.

go to /etc and right click the file called "hostname", selecting "open With Gedit", or another text editor. 
change the name in the file to your new one, and reboot.
that should do you.

---

### Post by J V on 2010-03-16
> **The Cog said:**
> You must also change the name in /etc/hosts. /etc/hosts and /etc/hostname should agree.Ehm... doesn't hosts only contain the localhost alias? It has nothing to do with the hostname :)

Edit: I now see 127.0.1.1 is my computer name... why? I've never seen that before...

---

### Post by ibuclaw on 2010-03-16
> **J V said:**
> Ehm... doesn't hosts only contain the localhost alias? It has nothing to do with the hostname :)

No, it doesn't:

```

[~] cat /etc/hosts
127.0.0.1	localhost
**127.0.1.1	debian**

```
That is what requires updating too. :)

Regards
Iain

---

### Post by julio.tomaschitz on 2010-03-16
You could install ubuntu tweak from [http://ubuntu-tweak.com](http://ubuntu-tweak.com).
so, install it, and go to the advanced options and look for the computer's name, and change it. Open a new terminal and you will see the new name: 'username@new_computer_name".

Ubuntu Tweak is very cool, you do almost everything on it (abotu configurations):guitar:.

---

### Post by ibuclaw on 2010-03-16
> **J V said:**
> 
Edit: I now see 127.0.1.1 is my computer name... why? I've never seen that before...

See [this reference manual]("http://www.debian.org/doc/manuals/reference/ch05.en.html#_the_hostname_resolution") and [this bug report from 2005]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=316099") for your answer.

---

### Post by doas777 on 2010-03-16
> **ibuclaw said:**
> No, it doesn't:

```

[~] cat /etc/hosts
127.0.0.1    localhost
**127.0.1.1    debian**

```That is what requires updating too. :)

Regards
Iain
network-manager has always done that for me on reboot. does it not now? it's rare that i need to change a hostname so...

---

### Post by wojox on 2010-03-16
> **The Cog said:**
> You must also change the name in /etc/hosts. /etc/hosts and /etc/hostname should agree.

When you change /etc/hostname and reboot doesn't it change /etc/hosts automatically?

---

### Post by muddpup64 on 2010-03-16
I tried

```
gksudo gedit /ect/hostname/
```and when I typed my new name in it said error "could not find the file /ect/hostname.

---

### Post by doas777 on 2010-03-16
> **muddpup64 said:**
> I tried

```
gksudo gedit /ect/hostname/
```and when I typed my new name in it said error "could not find the file /ect/hostname.

drop the trailing '/'
you would only use it, if you were accessing a directory, which is not the case
/ect/hostname

---

### Post by wojox on 2010-03-16
It's **/etc/** not /ect/

---

### Post by muddpup64 on 2010-03-16
It worked, cool, but what about for a flash drive?

---

### Post by doas777 on 2010-03-17
> **muddpup64 said:**
> It worked, cool, but what about for a flash drive?
not sure what you are asking. do you mean to change the "Label" of a thumbdrive? if so it depends on the filesystem on the thumb. if it is ext based, then use e2Label, but if it is ntfs, use windows to set it, and you shoudl see it in ubuntu as well.

---

### Post by julio.tomaschitz on 2010-03-17
I've tried change /etc/hostname and /etc/hosts and changed both with the new name, I restarted the system and it's worked.

---

### Post by julio.tomaschitz on 2010-03-17
yeah, if you want to change the usb stick name, you'll have to change it's label. you do it with gparted, not sure, but you will have to format the disk, so it's better _make a backup._

with the opened gparted window, go to the above-right button, and choose the disk (normally sdb1 or sdc). so right click on the bar, and search for label, if this option is not available, choose format it, and on the formatting-option-window appear, put the name you want on it, and apply.

I think there should be another way, it is my contribution.

---

