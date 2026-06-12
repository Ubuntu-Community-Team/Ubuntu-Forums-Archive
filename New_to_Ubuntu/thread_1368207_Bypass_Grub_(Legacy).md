---
title: "Bypass Grub (Legacy)"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by RobHK on 2009-12-30
Running Ubuntu 9.04 and Vista with the Legacy Grub automatically installed.

I'd like Windows to boot automatically on this machine, with the Grub menu only appearing if I press a certain key. I believe this is possible and straightforward, but I haven't been able to Google anything useful.

---

### Post by audiomick on 2009-12-30
Hallo.
Grub documentation is here.
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
There is a link on there to one about how to change the default system.

---

### Post by danastasio on 2009-12-30
I'm not entirley sure how to set the default boot order and running GRUB2 I can't just look at the config file to help you, but to make the menu hidden, simply 

```
sudo nano /boot/grub/menu.lst
```

and scroll down to a line that looks akin to
> ##uncomment the following to enable hidden menu
##hiddenmenu

I'm going off of memory and while I know that the file name is right, i dont know about the comment. But that will get you the hidden menu feature that you want.

---

### Post by audiomick on 2009-12-30
@ danastasio
The Grub documentation page I posted the link to says you can hide the grub menu by effectively doing the reverse of what you suggest, so I think you are right.

---

### Post by oldfred on 2009-12-30
There are several additional settings you may want to change:

You can set the default to the entry that it will run, or the windows stanza can be moved above the automagic area rather than below it. If it is in the automagic area it will get overwritten on a grub update or new kernel.
Change this entry or move windows.
default        0

You will want to restrict how many kernels it shows or the default number above will change whenever a new kernel is downloaded:
# howmany=2

Note that parts of menu.lst need no # to function and some need one # as a parameter for rewriting the automagic area.

If moving the windows stanza put it here:
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST
[COLOR=DarkRed]windows stanza[/COLOR]
### BEGIN AUTOMAGIC KERNELS LIST

---

### Post by RobHK on 2009-12-30
> **danastasio said:**
> I'm not entirley sure how to set the default boot order and running GRUB2 I can't just look at the config file to help you, but to make the menu hidden, simply 

```
sudo nano /boot/grub/menu.lst
```

and scroll down to a line that looks akin to


I'm going off of memory and while I know that the file name is right, i dont know about the comment. But that will get you the hidden menu feature that you want.

No problem changing the default boot order. I've done that.

Your hiddden menu looks like what I need. So I Googled "grub hidden menu" and found this:
[http://www.gnu.org/software/grub/manual/html_node/Hidden-menu-interface.html](http://www.gnu.org/software/grub/manual/html_node/Hidden-menu-interface.html)

Which tells me to use the <Esc> key to see the menu.

Thanks.

---

### Post by RobHK on 2009-12-30
Just done it. It's not 100% what I'd hoped for. It displays "Grub loading" and a brief timeout rather than being totally hidden. But it doesn't show the menu.

---

### Post by audiomick on 2009-12-30
> **RobHK said:**
> Just done it. It's not 100% what I'd hoped for. It displays "Grub loading" and a brief timeout rather than being totally hidden. But it doesn't show the menu.

You can change the length of the Timeout in menu.list. Leave yourself a bit though, that is when you have to press "ESC" to see the menu.  You wont get rid of the "grub loading". Grub loads in stages, and shows that until it gets up to actually booting something.

---

### Post by Old_Grey_Wolf on 2009-12-30
Another way to modify Grub is with the GUI application StartUp Manager. You can get it from the repositories. This is a website describing it as well [http://www.ubuntugeek.com/startup-manager-change-settings-in-grub-grub2-and-usplash.html](http://www.ubuntugeek.com/startup-manager-change-settings-in-grub-grub2-and-usplash.html).

---

### Post by RobHK on 2009-12-31
> **audiomick said:**
> You can change the length of the Timeout in menu.list. Leave yourself a bit though, that is when you have to press "ESC" to see the menu.  You wont get rid of the "grub loading". Grub loads in stages, and shows that until it gets up to actually booting something.

Yes, thanks Michael. I know that one. This timeout is while Grub loads. But it's very brief. I was just mentioning it, but it's not an issue. Ideally I'd have liked it to boot "quiet", i.e. not to display the "Grub loading" message, but it's no big deal.

---

