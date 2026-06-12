---
title: "Restore Default for Terminal"
date: 2011-01-08
forum: New to Ubuntu
---

### Post by J697 on 2011-01-08
I had my terminal and I messed around with the colors, and now it is not transparent anymore :(
I tried a few things around the internet and none of them worked. I just want to restore the default settings for the terminal so it is not so ugly.

Thanks in advance

---

### Post by nothingspecial on 2011-01-08
**[COLOR=Red]WARNING - THIS COULD MESS UP THEME/ETC SETTINGS[/COLOR]**

But, to remove the gnome-terminal settings

```
rm -r ~/.gconf/apps/gnome-terminal
```

---

### Post by star123 on 2011-01-08
> **iou said:**
> I had my terminal and I messed around with the colors, and now it is not transparent anymore :(
I tried a few things around the internet and none of them worked. I just want to restore the default settings for the terminal so it is not so ugly.

Thanks in advance

well open ur terminal->edit->profile.. set to default but other options include
terminal->edit->profile prefernces.to change ur color to default profile prefernces->colors->use color from system theme
to make it transparent profile prefernces->transparent background
default optoin is also present.. but i wud recmmend customise it..its ur own os make it ur own:P:P:P

---

### Post by J697 on 2011-01-08
> **nothingspecial said:**
> **[COLOR=Red]WARNING - THIS COULD MESS UP THEME/ETC SETTINGS[/COLOR]**

But, to remove the gnome-terminal settings

```
rm -r ~/.gconf/apps/gnome-terminal
```

rm: cannot remove `/home/jarid/.gconf/apps/gnome-terminal': No such file or directory

> **star123 said:**
> well open ur terminal->edit->profile.. set to default but other options include
terminal->edit->profile prefernces.to change ur color to default profile prefernces->colors->use color from system theme
to make it transparent profile prefernces->transparent background
default optoin is also present.. but i wud recmmend customise it..its ur own os make it ur own:P:P:P

That was the first thing I tried :)

---

### Post by mikewhatever on 2011-01-08
Try something like this:

```
mv .gconf/apps/gnome-terminal/profiles .gconf/apps/gnome-terminal/profiles-backup
```

Then restart gnome-terminal.

---

### Post by J697 on 2011-01-08
> **mikewhatever said:**
> Try something like this:

```
mv .gconf/apps/gnome-terminal/profiles .gconf/apps/gnome-terminal/profiles-backup
```Then restart gnome-terminal.

mv: cannot stat `.gconf/apps/gnome-terminal/profiles': No such file or directory

---

### Post by nothingspecial on 2011-01-08
Are you using Ubuntu?

or something else Xubuntu, Kubuntu, Lubuntu etc?

---

### Post by nothingspecial on 2011-01-08
Or to rephrase the question --

Are you using gnome-terminal?

---

### Post by J697 on 2011-01-08
Ubuntu, and yes Gnome Terminal.

---

### Post by mikewhatever on 2011-01-08
What version of Ubuntu do you have? Is it Kubuntu? Lubuntu?

Try looking for gnome-terminal settings:

```
find - -name *terminal
```

---

### Post by nothingspecial on 2011-01-08
> **iou said:**
> rm: cannot remove `/home/jarid/.gconf/apps/gnome-terminal': No such file or directory

You should have that directory, weird :-k

---

### Post by J697 on 2011-01-08
> **mikewhatever said:**
> What version of Ubuntu do you have? Is it Kubuntu? Lubuntu?

10.10
AFAIK it is the one you get wgen you go go to:

[www.ubuntu.com](www.ubuntu.com)

---

### Post by nothingspecial on 2011-01-08
> **mikewhatever said:**
> 

```
find - -name *terminal
```

That should be

```
find ./ -name *terminal
```

---

### Post by J697 on 2011-01-08
> **nothingspecial said:**
> That should be

```
find ./ -name *terminal
```

When I do that, the only thing that happens is that the cursor breaks to another line and repetabley flashes.

---

### Post by nothingspecial on 2011-01-08
Does your terminal open in your home directory?

```
ns@ns-net:~$ cd .gconf/apps/gnome-terminal
ns@ns-net:~/.gconf/apps/gnome-terminal$ ls
%gconf.xml  profiles
ns@ns-net:~/.gconf/apps/gnome-terminal$ 

ns@ns-net:~$ find ./ -name *terminal
./.gconf/apps/gnome-terminal
```

See, all this works for me. You have something different going on.

---

### Post by star123 on 2011-01-08
> **iou said:**
> rm: cannot remove `/home/jarid/.gconf/apps/gnome-terminal': No such file or directory



That was the first thing I tried :)

can u pls tell wen u went through the procedure wat result u got i mean didnt u get the option to customize ur terminal or set it to default??

---

### Post by J697 on 2011-01-08
Well, I would rather not reinstall Ubuntu. I guess maybe I can live with how it looks :(

---

### Post by nothingspecial on 2011-01-08
> **iou said:**
> Well, I would rather not reinstall Ubuntu. I guess maybe I can live with how it looks :(

yeah, don`t do that just because you don`t like the way the terminal looks.

I`m interested though, as to why you don`t have that directory -- you should.

---

### Post by sigilbaram on 2011-02-17
It seems gnome-terminal does not use ~/.gconf/gnome-terminal, at least any more. I moved the whole thing to ~/.gconf/gnome-terminal.bak and my customisations stayed the same. I was trying to restore Ubuntu's default color pallet because the "Custom" default one was lost when I looked at the other pallets, which I didn't like as much. From TTY1 I did  

```
killall gnome-terminal
sudo dpkg-reconfigure gnome-terminal
```

which didn't help either. The color pallet isn't that big of an issue but this missing/ignored configuration files thing is kind of interesting.

Edit:
Oh and "find ~/ -name gnome-terminal" found nothing.

---

