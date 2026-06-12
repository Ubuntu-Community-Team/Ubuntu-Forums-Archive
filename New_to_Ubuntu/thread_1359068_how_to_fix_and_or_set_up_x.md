---
title: "how to fix and or set up x"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by farrinux on 2009-12-19
I screwed up xorg.conf and can not seem to get it to work. My questions are-
1. Do I need to leave the desktop environ to edit X (Stop GDM)?

2.What commands are used to edit x ?
I have tried the following sudo gedit /etc/x11/xorg.conf but all this does is want to create a new file. I have been going to root terminal and just using gedit to open the file.

3 Once I have edited x how do I get the system to use it? I spent about an hour editing it and saved it and upon a reboot I was back at square one. I was stuck with only two resoulutions and the wrong graphics card (system defaulted to unkown display and Vesa graphics).

I am using Ubuntu 8.04 LTS Hardy and the graphice card is a Matrox g200 monitor is an LG W2252TQ

---

### Post by lotharmat on 2009-12-19
I think your path to xorg.conf is wrong.

it should be /etc/X11/.... etc.

---

### Post by farrinux on 2009-12-19
> **lotharmat said:**
> I think your path to xorg.conf is wrong.

it should be /etc/X11/.... etc.

My path is fine I just forgot to use a capital X when I typed the post However is Sudo gedit the required command to edit xorg?

---

### Post by lotharmat on 2009-12-19
I'd use
```
gksudo gedit /etc/X11/xorg.conf
```
gksudo is used instead of sudo for graphical apps

---

### Post by audiomick on 2009-12-19
Hallo.

First first of all ;) : upon reading over what I read, I believe you could have the feeling that I think you are an idiot. This is not the case, I am simply trying to cover all the pitfalls that I am aware of, because what you describe of your actions seems essentially correct :)

First of all, it is recommended to use "gksu" instead of "sudo" to use gedit, as gedit is a graphical text editor. Both commands effectively call up the same process, I think, but "sudo" is intended for text based operations, and can mess up your permissions if used for graphic based things. gksu keeps things in order.
```
gksu gedit /file/name
```

Presumably, when you say "edit x" you mean the configuration, and not the programme x server.

You don't need to leave the GUI (desktop environment) to do this. You do need to log out and log back in (just user log out, not reboot) for the chnages to take effect.

If gedit wants to create a new /etc/X11/xorg.conf, it may be that it is not there. On 9.10 it  isn't always. Some installations get by with defaults and don't need it.

Note: please check to see if it is etc or ect. I saw a thread recently where the problem was a simple typing error. He had it mixed up, and now I can't remember which is correct:redface:, and can't check because I am not at home.

Also, don't forget that file and directory names are case sensitive. X11 must have a capital X ( and it is X one one, not X el el...)

Once you have edited / created xorg.conf **and it is in the right place** the system should find it and use it.

ps: when you write something like this
> ...tried the following sudo gedit /etc/x11/xorg.conf but all this...,

use the code tags, that is the # button at the top of the post window, to make it look like this
> ...tried the following
```
 sudo gedit /etc/x11/xorg.conf
``` 
but all this...

it makes the post much easier to understand :)

---

### Post by farrinux on 2009-12-19
Michael 

> Presumably, when you say "edit x" you mean the configuration, and not the programme x server. Yes

> Note: please check to see if it is etc or ect. I saw a thread recently where the problem was a simple typing error. He had it mixed up, and now I can't remember which is correct, and can't check because I am not at home. I will

GKSU I never knew about and a majority of all Ubuntu documentation uses the SUDO command that I see, that is why I used it. 

Thank you

---

### Post by ST3ALTHPSYCH0 on 2009-12-19
I can make your life a little easier.... maybe.
First, run this command:
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```

Right click on the main menu, select "edit menus" and enable the "Screens and Graphics" menu item under . Open Screens and Graphics (Applications>other>screens and graphics). Now click on the model of your monitor and choose the type (in my case I chose Generic Monitor 1600x1200). Choose ok. Choose ok again. At this point it will tell you that the changes won't take effect until you reboot.
This should do you.

---

### Post by audiomick on 2009-12-19
Found this just now. Don't know how much help it is....
[https://help.ubuntu.com/community/BinaryDriverHowto/MatroxParhelia](https://help.ubuntu.com/community/BinaryDriverHowto/MatroxParhelia)

---

### Post by joes7 on 2009-12-19
If you are unsure, re-install.

---

