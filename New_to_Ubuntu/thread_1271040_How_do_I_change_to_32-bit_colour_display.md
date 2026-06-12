---
title: "How do I change to 32-bit colour display?"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by Harlequin. on 2009-09-20
I don't know what it's on now but I don't think it defaults to 32 so how do I change it? Thanks.

---

### Post by Harlequin. on 2009-09-20
Err bump.. Obviously so many of you people know how to do this why can't you help me out?

---

### Post by Harlequin. on 2009-09-20
Bump

---

### Post by mc4man on 2009-09-20
read here
[http://en.wikipedia.org/wiki/Color_depth](http://en.wikipedia.org/wiki/Color_depth)

---

### Post by Harlequin. on 2009-09-21
> **mc4man said:**
> read here
[http://en.wikipedia.org/wiki/Color_depth](http://en.wikipedia.org/wiki/Color_depth)

Ummm... Why? I need to change it to 32 bit, not read a wikipedia article on colour depth. WTF did you even post that for?

---

### Post by AMDBuntu on 2009-09-21
It may depend on your hardware and how it's supported...

Try looking at system>preferences>display

My desktop has a Nvidia card which has a lot more options than the Intel chip-set on the laptop which doesn't offer color depth settings.

---

### Post by mc4man on 2009-09-21
> I need to change it to 32 bit, not read a wikipedia article on colour depth. WTF did you even post that for? 

Yeah I'm sorry. I guess that your too smart for such a simple explanation

here's the basic xfree86.org spec's, maybe have a go a changing them

[http://www.xfree86.org/4.3.0/XF86Config.5.html#sect11](http://www.xfree86.org/4.3.0/XF86Config.5.html#sect11)

note that 3X8 = 24 actual bits used 

if you have  an actual use for the alpha channel then then i'm sure your more than capable of figuring a solution (vs. 8 padded bits

---

### Post by Harlequin. on 2009-09-21
> **mc4man said:**
> Yeah I'm sorry. I guess that your too smart for such a simple explanation

here's the basic xfree86.org spec's, maybe have a go a changing them

[http://www.xfree86.org/4.3.0/XF86Config.5.html#sect11](http://www.xfree86.org/4.3.0/XF86Config.5.html#sect11)

note that 3X8 = 24 actual bits used 

if you have  an actual use for the alpha channel then then i'm sure your more than capable of figuring a solution (vs. 8 padded bits

Dude all I need to know is how to edit xorg.conf. Never had much luck with this website...

---

### Post by theozzlives on 2009-09-21
> **Harlequin. said:**
> Dude all I need to know is how to edit xorg.conf. Never had much luck with this website...

```
man xorg
```you'd get more help if you weren't so belligerent.

---

### Post by Perfect Storm on 2009-09-21
> **Harlequin. said:**
> Dude all I need to know is how to edit xorg.conf. Never had much luck with this website...

```
sudo nano /etc/X11/xorg.conf
```
Now you can edit it. Just be careful.

---

### Post by Chaaaaaaaalie on 2009-09-24
When I open the display properties dialogue, it has little drop down menus to change screen resolution and depth, but it won't let me use them.  It says I have to change my configuration file or something like that. 
 
Unfortunately, I can't change and save the configuration file....
 
My question is why they bothered making a nice menu to edit the properties, but force you to edit it via the terminal anyway.  Confused.

---

### Post by Perfect Storm on 2009-09-25
The instruction is shown in nano's lower part.

[img]http://www.imageviper.com/displayimage/143986/0/nano.png[/img]

^O = [ctrl]+[o] = save
^X = [ctrl]+[x] = exit
etc.

nano is a cli (commandline interface) text editor. If you sudden messing up the xorg, you can edit/fix xorg from CLI.

---

### Post by coolbrook on 2009-09-25
blank

---

