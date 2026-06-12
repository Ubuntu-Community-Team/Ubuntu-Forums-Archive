---
title: "cant edit xorg"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by usedtobeacity on 2009-06-17
sorry, probably a noob question.....

I am running juanty on a powerbook. 

Prob is I cant edit xorg.conf, when I go to gedit it just gives me a blank page, if I type anything in and try to save I get " can't find .ect/x11/xorg.conf" 

checked in file browser, it's there, when i try to open in text edit(or any thing) all I get is a blank page.

any one know whats going on here?

---

### Post by madnessjack on 2009-06-17
Try this ```
sudo gedit /etc/X11/xorg.conf
```

Things to consider, correct case (ie "X11" not "x11" - two different things ;) ) and leading foward slash ("/etc/..." no "etc/...") beacuse they mean different things.

Hope this helps :)

---

### Post by _Purple_ on 2009-06-17
> **madnessjack said:**
> Try this ```
sudo gedit /etc/X11/xorg.conf
```

Things to consider, correct case (ie "X11" not "x11" - two different things ;) ) and leading foward slash ("/etc/..." no "etc/...") beacuse they mean different things.

Hope this helps :)

Please use gksudo instead of sudo for graphical applications.
```
gksudo gedit /etc/X11/xorg.conf
```

For more details, check this link:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by madnessjack on 2009-06-17
Wow, that's good to know! Thanks for the heads up :)

---

### Post by _Purple_ on 2009-06-17
> **madnessjack said:**
> Wow, that's good to know! Thanks for the heads up :)

You are welcome. :)

To the OP, you can use tab completion to avoid typing errors. For example,
```
gksudo gedit /e<tab>/X<tab>/xo<tab>
```

---

### Post by super kim on 2009-06-17
> **_Purple_ said:**
> You are welcome. :)

To the OP, you can use tab completion to avoid typing errors. For example,
```
gksudo gedit /e<tab>/X<tab>/xo<tab>
```

oh my freaking god that is sooo usefull. ha i love learning little things like this, it makes the critical sytem errors seem not so bad lol :)  definately one to remember tab completion eh. i am such a clumbsy typer and i often have to re-type terminal commands, not anymore yay!!

---

### Post by usedtobeacity on 2009-06-17
Hey, still can't edit the bugger! It is opening correctly, just nothing there!

I looked at the properties and it's telling me xorg.conf is 0 bytes, it seems to me that that cant be right? but it is there(at least the icon is).

any thoughts?

thanks all.

---

### Post by _Purple_ on 2009-06-17
Which version of Ubuntu are you using?

---

### Post by madnessjack on 2009-06-17
I think it's time to go
```
sudo dpkg-reconfigure xserver-xorg
```and get it to reconfigure your xorg stuff, that don't sound right to me :P

---

### Post by overdrank on 2009-06-17
> **usedtobeacity said:**
> Hey, still can't edit the bugger! It is opening correctly, just nothing there!

I looked at the properties and it's telling me xorg.conf is 0 bytes, it seems to me that that cant be right? but it is there(at least the icon is).

any thoughts?

thanks all.

In Jaunty 9.04 it will be more than likely be empty. What is the model of the graphics card?

---

### Post by usedtobeacity on 2009-06-17
jaunty 9.04, and I think an ATI Mobility Radeon(thats what should be in here).

---

### Post by overdrank on 2009-06-17
> **usedtobeacity said:**
> jaunty 9.04, and I think an ATI Mobility Radeon(thats what should be in here).

Ok I have a feeling that I cant help, but what is the specific model.
You mays use this command ```
lspci | grep VGA

```

---

### Post by usedtobeacity on 2009-06-17
sorry, its a Nvidia GeForce FX Go5200 on this thing, any rate, how can I make shure the right driver is enabled if xorg.conf is not an option?

---

### Post by overdrank on 2009-06-17
> **usedtobeacity said:**
> sorry, its a Nvidia GeForce FX Go5200 on this thing, any rate, how can I make shure the right driver is enabled if xorg.conf is not an option?

Ok are the drivers located under system, administration, hardware drivers?

---

### Post by regala on 2009-06-17
> **_Purple_ said:**
> Which version of Ubuntu are you using?

good to know that commentors are just as clueless as commentees with respect to READING what is written on the screen or in the original post...

:popcorn:

---

### Post by usedtobeacity on 2009-06-17
nope, only thing in there is fwcutter, thanks for responding to this by the way, never actually posted in forms before, but have slowly been converting everyone I know to team penguin for a couple of years now.

---

### Post by super kim on 2009-06-17
sorry i'm only a noob lol but i have been having trouble with nvida drivers and found this program usefull,
EnvyNG you can find it in your synaptic package manager and it should be a one stop solution to the OP's problem.
please tell me to shut up if i'm wrong, i dont want to cause confusion with wrong help :)

---

### Post by overdrank on 2009-06-17
> **usedtobeacity said:**
> nope, only thing in there is fwcutter, thanks for responding to this by the way, never actually posted in forms before, but have slowly been converting everyone I know to team penguin for a couple of years now.

super kim has a good idea to try Envy. I have little experience with that model in 9.04 and Envy would be easier than manually installing the nvidia drivers.

---

### Post by usedtobeacity on 2009-06-17
just to restate this this is running on a powerbook g4 PPC, so no drivers from nvidia , I understood it that you had to use the drivers in kernel and manualy set to "NV" haven't found any other info on it.

---

### Post by overdrank on 2009-06-17
> **regala said:**
> good to know that commentors are just as clueless as commentees with respect to READING what is written on the screen or in the original post...

:popcorn:

Can be easily missed. ;)

---

### Post by usedtobeacity on 2009-06-17
nope, envyng wont install, tells me unresolved dependencies
 "Depends: nvidia-common  but it is not installable
 Depends: fglrx-modaliases  but it is not installable"

any other Ideas? 

feel free to make me experiment, don't mind screwing up my sys, can always reinstall

---

### Post by overdrank on 2009-06-17
> **usedtobeacity said:**
> just to restate this this is running on a powerbook g4 PPC, so no drivers from nvidia , I understood it that you had to use the drivers in kernel and manualy set to "NV" haven't found any other info on it.

Jaunty handles the xorg differently then passed editions. If you are not installing the drivers then you may try and manually reconfigure your xorg. But I believe that Jaunty would default to the nv driver.

---

### Post by usedtobeacity on 2009-06-17
well, i cant get any compositing manager going and I get about 90fps with glxgears. how dose one reconfigure with an empty xorg.conf file?

---

### Post by overdrank on 2009-06-17
> **usedtobeacity said:**
> well, i cant get any compositing manager going and I get about 90fps with glxgears. how dose one reconfigure with an empty xorg.conf file?

Ok you may try the command ```
sudo dpkg-reconfigure -phigh xserver-xorg 
```in the terminal, or you may try and use the xfix option when booting from the grub. But I believe the ppc does not use the grub, :(
You may be better off searching [here]("http://ubuntuforums.org/forumdisplay.php?f=328") where you posted earlier on installing. :)

---

### Post by regala on 2009-06-17
> **overdrank said:**
> Can be easily missed. ;)

I strongly agree.
Just wanted to be sure I am right to find such threads totally "surréalistes" (overrealistic ?) with respect to "people talk to each other", "people are talking about the same thing", "people didn't care to read the body after reading the title", or "people are trying to destroy one's system" :)

---

### Post by oldos2er on 2009-06-17
> **usedtobeacity said:**
> nope, envyng wont install, tells me unresolved dependencies
 "Depends: nvidia-common  but it is not installable
 Depends: fglrx-modaliases  but it is not installable"


 Do you have all repositories enabled? Check System, Administration, Software Sources.

---

