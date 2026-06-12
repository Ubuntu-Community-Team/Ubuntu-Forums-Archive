---
title: "i deleteted my destop sreen   help!!  8.04"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by blake7 on 2009-01-21
help how can i get this back

i did my deleteing gimp for some reason when i tpyed in gimp to delet it also brought up my desktop. i did not know that it was a that hopless that it would bring up non gimp files and deleed all that came up.


thank you and i hjope you can  help

---

### Post by Michael.Godawski on 2009-01-21
hi,

boot into the recovery mode and re-install the ubuntu-desktop if it is really removed.

```
sudo apt-get install ubuntu-desktop
```But ubuntu-desktop is only a meta-package and removing it should not remove your desktop really:

[LIST]
[*][http://ubuntuforums.org/showthread.php?t=42453](http://ubuntuforums.org/showthread.php?t=42453)
[/LIST]

Are you able to log into Ubuntu? Or is your whole desktop gone?

---

### Post by taurus on 2009-01-21
> **Michael.Godawski said:**
> hi,

boot into the recovery mode and re-install the ubuntu-desktop if it is really removed.

```
**sudo** apt-get install ubuntu-desktop
```


If you boot into recovery mode from GRUB menu, there is no need to include sudo in there since you're already logged in as root.

---

### Post by blake7 on 2009-01-21
hi it loads what i can only call a ternaiml like screen
where it ask for login codes then boots programes but no desktop.


does this help

---

### Post by taurus on 2009-01-21
What happens when you run this command from a prompt, after you've logged in?

```
startx
```

---

### Post by Troll_the_Great on 2009-01-21
> **blake7 said:**
> hi it loads what i can only call a ternaiml like screen
where it ask for login codes then boots programes but no desktop.


does this help

Yep, it helps.It looks that you deleted your desktop manager.No problem.Log on in the "terminal like screen" and after that type:
```
sudo apt-get install gdm
```
That should do the trick.Tell me if that solved your problem.
Cheers!

---

### Post by handydan918 on 2009-01-21
> **blake7 said:**
> hi it loads what i can only call a ternaiml like screen
where it ask for login codes then boots programes but no desktop.


does this help

logged in at the terminal, what does ```
sudo startx
```

give you?

---

### Post by blake7 on 2009-01-21
hi i did this

sudo apt-get install ubuntu-desktop 

but i think it failed, thier are lots of failed to fetch [http://and](http://and) then a line of file address names

what would happy if it worked????????


help

---

### Post by Troll_the_Great on 2009-01-21
Wow, taurus, over 25,000 posts... Since when do you use Ubuntu? And how much do you spend on this forums?

---

### Post by blake7 on 2009-01-21
sudo startx

that gives me a very odd sreen a small rectangal in the top left corner saying 
root@a-laptop:"#


does that help ??

thank you for your time

---

### Post by blake7 on 2009-01-21
it does say this when i turn on my laptop 


kinit: no resume image, doing normal boot...

---

### Post by blake7 on 2009-01-21
Re: help what does this mean. kinit: no resume, doing.....
kinit: no resume, doing normal boot...

ubuntu 8.04.1 a-laptop tty1
a-laptop login:



but it does not load the destop screen, just a ternamel like screen

also can i start any programs????

---

### Post by taurus on 2009-01-21
Log in with your username and password.  Then, see what happens when you start X server from the prompt.

```
startx
```

p.s.  Looks like this is the third thread of the same problem!

---

### Post by overdrank on 2009-01-21
> **blake7 said:**
> Re: help what does this mean. kinit: no resume, doing.....
kinit: no resume, doing normal boot...

ubuntu 8.04.1 a-laptop tty1
a-laptop login:



but it does not load the destop screen, just a ternamel like screen

also can i start any programs????

Please do not create multiple threads on the same issue. Threads merged 
Thanks taurus :)

---

### Post by blake7 on 2009-01-21
no one is helping at the moment and iam running out of time in this internet cafe.
all so now iam very worried that this can not be solved 
so help if you can,
and try to understand what i ddi

---

### Post by overdrank on 2009-01-21
> **blake7 said:**
> no one is helping at the moment and iam running out of time in this internet cafe.
all so now iam very worried that this can not be solved 
so help if you can,
and try to understand what i ddi

There are users trying to help you. But creating multiple threads will just cause confusion.
 If you removed the desktop and tried to reinstall the ubuntu-desktop can you post the errors.

---

### Post by RequinB4 on 2009-01-21
[http://ubuntuforums.org/showpost.php?p=6590746&postcount=10](http://ubuntuforums.org/showpost.php?p=6590746&postcount=10)

---

### Post by blake7 on 2009-01-21
/etc/init.d/gdm start


thjis does not work

i typed in 
startx  and then pressed return 

and then 

/etc/init.d/gdm start

and it does nothing

---

### Post by blake7 on 2009-01-21
how can i get my programs up and running from tyhis poition
like firefox    ect

---

### Post by taurus on 2009-01-21
Is there an error message when you run **startx** from the prompt?  Doesn't work is not helping anybody who tries to help you.

Forget about firefox right now because you need to get X running first before you can start all those GUI apps.

---

### Post by blake7 on 2009-01-22
Is there an error message when you run startx from the prompt

no thier no error message it looks like works (small retangle box in the top right)

thanks

---

### Post by taurus on 2009-01-22
Log out of that.  It would put you back to a prompt.  Now, install Gnome.

```
sudo apt-get update
sudo apt-get install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```
Otherwise, take a picture of the screen with that "small retangle box in the top right" with your camera or cell phone so we would know exact what it looks like.

---

### Post by blake7 on 2009-01-28
hi do i need tobe connected to the internet for this???

---

### Post by hotstovejer on 2009-01-28
Yes, you do. To install most things with apt-get, you need to be connected to the internet. Have you been connected this whole time, or no?

Thanks!

Jeremy

---

### Post by blake7 on 2009-01-28
why did no one say a thing how could i be connected with the prob i have 

what can i do now ?????

cheefs

---

### Post by blake7 on 2009-01-28
can i do this from the cd that i made when i frist loaded ubuntu on to my lap top

cheers

---

### Post by blake7 on 2009-01-29
sudo apt-get install ubuntu-desktop

can i do this from live cd

---

### Post by blake7 on 2009-02-04
can i get the dest top back from the live cd ????

---

### Post by blake7 on 2009-02-04
how can i get the dest top back
i have no wi fi 
can you please help

---

### Post by taurus on 2009-02-04
insert the LiveCD into the drive and run

```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ubuntu-desktop gdm
```

---

### Post by blake7 on 2009-02-04
thank you i try that now

---

### Post by blake7 on 2009-02-04
it says failed to mount the cdrom


is thier any thing i can do now

cheers

---

### Post by taurus on 2009-02-04
What kind of disc is that?

---

### Post by blake7 on 2009-02-04
errrm it the one that i downloaded from ubuntu which then i loaded 8.04 on to my x60s
does that help????

---

### Post by taurus on 2009-02-04
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by blake7 on 2009-02-04
that seems not  to do much
hardy backports restricted main multive res universe

---

### Post by blake7 on 2009-02-04
hardy backports restricted main multive res universe

im trying to get the laptop to read a fil;e of live cd

---

