---
title: "32 bit packages??"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by ave2 on 2009-02-28
Im trying to install the latest radeon 4850 drivers from

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English)

I download the file, and when I click on the .run file I get a message 

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again

I notice that on the download page the following

32-Bit packages must be installed for 64-Bit Linux drivers to install or work.

what is the 32 bit packages? where can I get it

---

### Post by zvacet on 2009-02-28
Right click on that package>properties>check box for make package executable and close.Double click on package to install it.

---

### Post by ave2 on 2009-02-28
ok that worked, it now tells me that I have to run this as the super user? I only have one user, there arent multiple accounts

---

### Post by MarblePanther on 2009-02-28
type sudo in a terminal and drag the package next to sudo and press enter.

---

### Post by SunnyRabbiera on 2009-02-28
Right, sudo is the way to get administrator access.
Its a part of ubuntu's security model.
The sudo password is your password.

---

### Post by ave2 on 2009-02-28
thanks everyone that worked- this is going to be quite a steep learning curve

---

### Post by SunnyRabbiera on 2009-02-28
Well luckily you have us the community.
Its not that steep though, some stuff works better then others in linux, this is no fault of linux mind you as this is a microsoft owned world and most hardware and software companies only know microsoft.
Linux is a real underdog.

---

### Post by ave2 on 2009-02-28
> **SunnyRabbiera said:**
> Well luckily you have us the community.
Its not that steep though, some stuff works better then others in linux, this is no fault of linux mind you as this is a microsoft owned world and most hardware and software companies only know microsoft.
Linux is a real underdog.

yeah im using blender 3d, and some guys report amazing speed increases using linux, so I decided to bite the bullet and learn it- been wanting to for a while, so this was a good opportunity....... but its my first day, so im still trying to unlearn windows haha :confused:

you right, iv been mailing a few different companies asking for linux ports of their software- its a huge community and if enough people do it, we may see a lot more support in the future

---

### Post by Kellemora on 2009-02-28
HI Ave2

I'm 61 years old, not to computer literate either, hi hi.........

Yet after using Ubuntu for less than 30 days, I converted my whole company over to it.

Naturally there were a few gripes and groans at first, but two months after the fact and everyone LOVES it better than they ever did the DOZE as for as everything being LOGICAL and as you mentioned, the SPEED is phenomenal!

Most folks run Windows IN Administrative Mode, that's one of the reasons it is so prone to really bad viruses, also, many Doze programs REQUIRE that you be in Administrative mode for them to work.  Shame Shame Shame on those programmers!

Ubuntu is EASIER than most Distro's because your normal password is your Administrative Password.  Some Distro's use THREE levels and each with it's own password.  User, Administrator and ROOT User.
So SEE, you only have to learn TWO levels, User Level and Super User Level!  It's for your own SAFETY it's set up this way!  Security is Job ONE in Linux!!!!!

Just learn the differences between gksu, sudo, su, sudo su, etc. and you'll be almost home free.

Once you have that down pat, THEN they'll pop all the command line things on you, hi hi...........  But there are not all that many.  Just jot them down in a notebook as you learn what each thing does.

Just BEWARE, Don't ever use rm anything unless you KNOW FOR SURE what it will do and to WHAT.  rm can wipe your drive if not used correctly!
It stand for REMOVE!

The easiest way to Learn is NOT to try and compare Linux with the DOZE, it will just drive you batty if you do!
It's like trying to convert French to English!  The French don't have a lot of the words we have, so they have to use a WHOLE PHRASE instead of a single word.  EG:  Pomme de Terre, which translates directly as Apple of the Earth.  In LINUX English that would mean POTATO!  Or Arc en Ciel, which translates to Arc in the Sky.  Now that one you might figure out!  In Linux English it would be simply RAINBOW.
In other words, what takes an arm and a leg in the Doze (if even possible), is only a couple of letters or a short word in Linux.

Also, for nearly every software program written for the doze, you can find 4 to 6 for Linux that have the same basic functions.  In other words MANY MORE CHOICES, so that can be confusing also!

In any case, ENJOY UBUNTU, I know I do!
And if this olde geezer can learn it (I say that with tongue in cheek) anyone can!

TTUL
Gary

---

