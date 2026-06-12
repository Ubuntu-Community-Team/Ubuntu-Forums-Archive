---
title: "Extended Desktop (dual screen) in Jaunty"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by Jense on 2009-04-23
Hi Everybody,

so this is about dual screen in Jaunty. Basicly I can't get it to work anymore.
It used to work in 8.10 using the xrandr command 
```
xrandr --output VGA-0 --left-of LVDS
```
in combination with the attached xorg.conf (virtual screen size..)

Now nothing works anymore. The xrandr command just causes the desktop to behave wiredly. It feels like the extended desktop is there, but not being displayed on my externel VGA.
The gui-tools (grandr / kde-display-setting) can produce a cloned/mirrowed, etc.. output, but not an extended one.

I read somewhere starting from 8.10 the xorg.conf shouldn't be necessary anymore, so maybe I am configuring to much by hand, but I don't see how it would work out of the box.

I am on a T41 with the horribly supported ATI 7500 using the radion driver (at least I think so, but this is beginners talk :))

---

### Post by holdie on 2009-05-01
I've also got this problem...running GNOME, but grandr used to work great for me, now it won't let me drag and drop the screens to position them as an extended desktop...only lets me clone

has anyone figured out how to fix this?

---

### Post by rodbotic on 2009-05-02
I just got it to work after some fighting!!:) :D \\:D/


I have a ATI 9550.

Xrandr wasn't detecting anything attached to the VGA output.
so I had to manually add the mode I needed by hand
[INDENT]
xrandr --addmode VGA-0 1280x1024[/INDENT]

then force the output, with the DVI port on.(note disable desktop effects)

[INDENT]xrandr --output DVI-0 --auto --output VGA-0 --mode 1280x1024 --right-of DVI-0[/INDENT]

and it worked. 

if I didn't put the first section of the xrandr code, the 
.... --output DVI-0 --auto
it would just mirror.

now I just have to figure out how to put this into my xorg.conf file. any ideas?

---

### Post by mikey_likesit on 2009-07-13
So I've just installed Jaunty and tried plugging my old CRT tv to my laptop using an S-vid cable. Used to work easy under xp but with Jaunty it limits my laptop screen to 1024X768 (4:3), otherwise I can go to 1280X800 (16:10), and the TV doesn't get 800X600.

I've looked through a zillion forums and see that people have had similar problems, though most of the solutions I was able to find were for much earlier versions of ubuntu.

I kind of get the feeling this may be a bug with no workaround yet in Jaunty, is this right? If not, can someone point me to a thread where a solution was found?

I can tell you that I'm running a Dell Inspiron 6400, but beyond that, because I'm new to this, I don't actually know how to look up what my drivers are in linux... :-( Help, anyone?

---

