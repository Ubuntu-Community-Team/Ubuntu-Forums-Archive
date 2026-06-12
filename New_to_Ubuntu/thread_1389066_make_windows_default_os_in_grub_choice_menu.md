---
title: "make windows default os in grub choice menu"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by GazRockK on 2010-01-23
I've looked around for an answer to this problem and couldn't seem to find one. I DID find something relevant however, but what they were looking at was a "menu.lst", and as you can see in my screenshot, i don't have one. [the file browser window]

--
what I looked at:
[http://ubuntuforums.org/showthread.php?t=170757](http://ubuntuforums.org/showthread.php?t=170757)
--

I found a file similar to the menu.lst called "grub.cfg"

I tried doing what the thread said, but unfortunately I wasn't able to edit any fields as I didn't have permissions. I only made one account, so I can't see why I don't have any permissions, but then i found something called "/root". I tried logging in as "/root" but came out with nothing. 

Any help on this? If there isn't enough info just ask and I'll do my best to give an answer. Any other helping thread would be appreciated as well.

---

### Post by SoFl W on 2010-01-23
I believe it depends on which version of grub you are running.  When you boot, above the OS selection it might tell you.

---

### Post by cariboo on 2010-01-23
You can use startupmanager to set boot order, it is in the repositories. It works for grub-legacy and grub2, but your are limited to setting boot order only when running grub2.

> I tried doing what the thread said, but unfortunately I wasn't able to edit any fields as I didn't have permissions. I only made one account, so I can't see why I don't have any permissions, but then i found something called "/root". I tried logging in as "/root" but came out with nothing

You have to be root in order to do anything in all directories except your home directory. If you want to edit grub.cfg, even though there is a big note at the top of the file not to, you would first have to make the file read/writable, as by default it is set to read only. Then you would have to use the follow command to edit the file:

```
gksu gedit /boot/grub/grub.cfg
```

after editing the file you would have to set the permissions back to read only.

---

### Post by SoFl W on 2010-01-24
If you are using grub2 this wiki might help you.
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by drs305 on 2010-01-24
Or Item 2 of [Grub 2 - 5 Common Tasks]("http://ubuntuforums.org/showthread.php?t=1302743")

---

### Post by Drcyclops on 2010-01-24
I have the same problem, I have managed to get a dual system working with 
Windows 7 & Ubuntu 9.10 using the Grub2 loader.  I have tried setting the default to 4 using the set-grub-default command but this fails because the file grubenv cannot be found.

---

### Post by Thingymebob on 2010-01-24
in a terminal enter
```
sudo gedit /etc/default/grub
```
Change 'GRUB_DEFAULT=0' to wherever windows appears if it appears 2nd on your list change to 1, 3rd chang to 2 etc, save and close the file then in a terminal enter:
```
sudo update-grub
```

---

### Post by ozbolt on 2010-01-24
The easiest is to install Start-up manager.

---

### Post by GazRockK on 2010-01-24
how do I log in as root? I can't set the file [gryb.cfg] as read/writable until I get root privilege apparently

---

### Post by drs305 on 2010-01-24
> **GazRockK said:**
> how do I log in as root? I can't set the file [gryb.cfg] as read/writable until I get root privilege apparently

First, the grub.cfg file is not meant to be edited. Grub 2 is much different than Grub legacy. You can see a lot has changed by reviewing some of the links in my signature line. If you are trying to change some of the basic default settings of Grub 2, refer to my post above on "5 Common Tasks" or review what others have posted here.

The file you would normally edit is /etc/default/grub and you would use *gksudo* to open gedit, since gedit is a graphical app:
```
gksudo gedit /etc/default/grub
```

---

### Post by candtalan on 2010-01-24
> **GazRockK said:**
> how do I log in as root? 

In Ubuntu it is not usual and not recomended to actually log in as root. In fact by default, the actual root account is not set up. This is optimal for security because if ever root existed and then was hacked, your system is wide open and resistance is futile.

It is usual to make use of root level privilidges by use of the sudo or gksu (is similar) command. This temporarily makes you as root, for the actions requested. A limited range of priviliges, and safer.

> 
 I can't set the file [gryb.cfg] as read/writable until I get root privilege apparently

Just use the gksu command mentioned earlier
gksu gedit /boot/grub/grub.cfg
 and save and exit when finished. You might like to consider  first, saving the existing file as .old for reference?

hth

---

### Post by J V on 2010-01-24
Better yet take the other advice of the easy way that woulden't require you to spend forever learning about sudo, and install [startupmanager]("apt://startupmanager")!

---

### Post by drs305 on 2010-01-24
Although I didn't mention it in my previous post, I'm a big fan of Startup-Manager. So much so I wrote some guides about using it. See the "SUM" link in my signature line.

SUM won't work with a lot of the capabilities in Grub 2, but it can easily set the default selection if that is all the user wants to do.

---

### Post by GazRockK on 2010-01-25
SOLVED

Thx to Thingymebob who's solution helped me. I now have Windows as the default boot option.

I also learned a bit more about Linux thanks to everyone else's posts

---

### Post by SSyar on 2011-01-15
> **cariboo907 said:**
> You can use startupmanager to set boot order, it is in the repositories. It works for grub-legacy and grub2, but your are limited to setting boot order only when running grub2.



You have to be root in order to do anything in all directories except your home directory. If you want to edit grub.cfg, even though there is a big note at the top of the file not to, you would first have to make the file read/writable, as by default it is set to read only. Then you would have to use the follow command to edit the file:

```
gksu gedit /boot/grub/grub.cfg
```after editing the file you would have to set the permissions back to read only.



startupmanager works for me like a charm :)....

---

