---
title: "Any great text-based tools to recommend?"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by Miter_J on 2011-03-29
I'm gonna use Ubuntu without its GUI and for now I've only got several useful tools for me, such as moc, mplayer,lynx(kinda bored cuz lynx doesn't support showing images)...

Anyone gets any recommendations of great tools(of course, text-based, supported in the console)?

Thanks in advance~~~:D

---

### Post by arochester on 2011-03-29
Look here: [http://kmandla.wikispaces.com/](http://kmandla.wikispaces.com/)

---

### Post by andrew.46 on 2011-03-29
All the cool guys are using mutt with gmail:

Using Mutt with Gmail
[http://www.andrews-corner.org/mutt.html](http://www.andrews-corner.org/mutt.html)

Andrew

---

### Post by Nutria on 2011-03-29
> **Miter_J said:**
> I'm gonna use Ubuntu without its GUI and for now I've only got several useful tools for me, such as moc, mplayer,lynx(kinda bored cuz lynx doesn't support showing images)...

Anyone gets any recommendations of great tools(of course, text-based, supported in the console)?

That's too broad and non-specific to answer.  However, I do congratulate you for trying the CLI.  It lets you automate repetitive tasks that aren't practical for GUI apps.

---

### Post by arochester on 2011-03-29
^^^ LOL!Then I mustn't be cool. I use Alpine with Gmail

---

### Post by Miter_J on 2011-03-29
Yeap, this question is indeed broad. Because I've actually no idea about those softwares  - -~ LOL. So any recommendations would help`~

Thank u guys~ I'm checking them out~ And if possible, please keep talking about this~  :)

---

### Post by Nutria on 2011-03-29
> **Miter_J said:**
> So any recommendations would help.

Help you do **what**?  Without knowing that, people are just throwing out ideas hoping they'll stick.

Do you just want to surf and read mail?  Or do you also want to convert 1000 movies from MPEG2 to MPEG4?

---

### Post by nothingspecial on 2011-03-29
> **Miter_J said:**
> ,lynx(kinda bored cuz lynx doesn't support showing images)...


You sir need to take control of your framebuffer.

First make sure you are in the video group
```

sudo usermod -a -G video *username*
```

Then make a udev rule to give you permissions for the framebuffer.
```

sudo nano /etc/udev/my-rules.d/framebuffer.rules
```

Then put this in that empty file
```

KERNEL=="fb0",  OWNER="root", MODE="0660"
```

or this, not both
```

KERNEL=="fb0",  OWNER="user", MODE="0640"
```

The first elevates permissions for others on the framebuffer, the second (you have to change user to your actual uaername), makes you the owner but has more restrictive permissions for others. It's up to you.

Reboot.

Now you will be able to see images if you use links2 with the -g flag

```
links2 -g
```

You can watch videos with mplayer and view photos and stuff with fbi

Bear (or bare???) in mind that you cannot use the framebuffer within a terminal multiplexer such as screen (which is the first console app you should learn to use) or dvtm etc.

So screen on one tty videos etc on another.

You can even take screen shots with fbgrab (sorry about the video example, some ballet thing of my wife's but you get the point) :D

[ATTACH]187460[/ATTACH]

---

### Post by Nutria on 2011-03-29
> **nothingspecial said:**
> You sir need to take control of your framebuffer.

But that's only valid if he's at the actual *console*.  Which might be true were he using Debian, but as a n00b using Ubuntu, he's "safely" cocooned by gdm.

---

### Post by nothingspecial on 2011-03-29
Not if he turns it off ;)


........ if you are going to do that though, you'd better learn how to set up your wireless (if you use it). Networkmanager connects when you login to gnome.

The easiest way would be to install wicd-curses which gives you an easy ncurses interface for setting it up. It starts at boot.

---

### Post by Miter_J on 2011-03-29
Aha, just like I said, anything would help, whether that is a browser or a music player. I don't know so much stuff on these text-based softwares, so I hope u to be free to recommend any softwares u feel good.

Just feel free to share, that's all :)

---

### Post by Miter_J on 2011-03-29
It's said that lynx doesn't support videos or images. So it seems that I would have to switch to links2~ Thank u.
Btw, after reading ur work, I find that I've got such a long way to go to really understand Linux...

---

### Post by Nutria on 2011-03-29
> Btw, after reading ur work, I find that I've got such a long way to go to really understand Linux...

:)

The cli programs that I use most are the simple ones: cd, mv, cp, rm, su, du, df, tail, grep.  Not to mention "|", "for/done", "if/fi" and seq.

Find an online tutorial for vi or vim.  Use it instead of gedit.

---

### Post by Tmcarr on 2011-03-29
If you ever get to the point where you want to learn screen (you will. :D ) I should point you to byobu. Its pretty slick and offers some really nice features for people just starting out with screen. 

[https://launchpad.net/byobu](https://launchpad.net/byobu)

---

### Post by Miter_J on 2011-03-30
Thank u guys~ I'm checking them out~~~

U guys r great!~:D

---

