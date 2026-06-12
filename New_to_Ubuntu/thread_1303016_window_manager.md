---
title: "window manager"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by vinceROXY on 2009-10-27
Hello Forum,

Please can you help me with some linux commands?

Currently, my system is running the Portable Ubuntu linux version on top of
windowsXP.

Portable Ubuntu usese gnome. I wanted to use a more lightweight window manager. So 
i downloaded and installed "Afterstep" and "window maker".

When i try to run "window maker" window manager.....it tells me it can't because there
is already a window manager running.

My question is.....how do i turn off the gnome window manager with a linux command?....then turn on my new "window maker" window manager...or run it?

what linux commands do i need to type into a terminal to do the above?

thanks,

Vince.

---

### Post by LunaticHiatus on 2009-10-27
install afterstep from synaptic package manager. (although, I would imagine that fluxbox would be better.. I dont really know anyone who uses afterstep. LXDE is nice and light too, but its a full desktop, not just a windows manager). log out, go to "sessions", choose afterstep. log back in.

---

### Post by ajgreeny on 2009-10-27
I agree, lxde is a great way to go.  It's lightning fast compared to gnome, though it doesn't have nearly so much configuration available.  Give it a try, it is available through synaptic, and then logout, and when you get to the login window, go to the options button at bottom left "Change session" ( I think, but can't remember the exact words) and choose lxde.  You may love it.

---

### Post by vinceROXY on 2009-10-27
Hello,

thankyou for your reply....

so if i open a terminal window.....what command do i type to log out of gnome?

logging out of Portable ubuntu in the normal fashion.....just takes you back to a 
dos terminal window...and out of all the desktops and gui front ends.

there is no option to choose sessions.....no graphical screen shows up after log out.

Imagine that i logged out using a terminal window.

What command would i type to get a sessions choice?....and see the choices?

What command would i then type to choose one of the options (window maker) and then
boot back into the graphical Portable Ubuntu with "window maker" running it...

thanks

Vince.

---

### Post by LunaticHiatus on 2009-10-27
btw, what the heck is ubuntu portable edition?
its also not dos. when your in a windowing system its called terminal. When not, its called Command Line.

Well, when you want to run Openbox from command line and you have gnome or kde installed already. I know the command is:

exec openbox-session

I would imagine it would be the same for other desktops and windows managers. So it would probably be exec afterstep or exec afterstep-session, etc. etc. etc.

---

### Post by vinceROXY on 2009-10-27
Hello,

Portable Ubuntu edition is a version of ubuntu that runs on top of windows.

Here

[http://portableubuntu.demonccc.com.ar/](http://portableubuntu.demonccc.com.ar/)


Yes, i will try what you mention with the commands...thanks

Vince.

---

### Post by LunaticHiatus on 2009-10-27
er, I don't believe thats an official ubuntu. just some weird spinoff. odd.

---

### Post by benj1 on 2009-10-27
when you say it exits to dos do you mean a linux shell or windows cmd.exe command prompt?
if it dumps you straight back to windows it may not be posssible to change window managers, although you would probably be better asking on their forums

---

### Post by vinceROXY on 2009-10-27
Hello

Yes, the Portable Ubuntu  forum has the answer...

it turns out that you can use any desktop or window manager you please...

lxde is probably a good bet for me...

also you can edit the conf file so that Portable ubuntu uses 512 or more ram...instead of the standard 256....making it faster...

PU's performance is near identical to a hard drive install of ubuntu....but the benefit is you can flick between windows and linux live..... and also drag files between the two....live...

The reason i use this PU distro is because it allows me to play endlessly with Linux and learn while not ever causing any damage to linux.

I use a special tool inside windowsXP called shadow user....which puts my machine into a shadow session of windows......then Uubntu also runs in a shadow session because it is ontop of my windows....

While i experiment with Linux....if things go bad or wrong....then the windows session can just be dumped....and all changes are forgotten....(all linux changes are lost)

Shadow user is a virtual hard drive...in ram....

When my linnux experiemtnig results in something succesfull...then i COMMITT the windows session to hard disc and thus the linux changes are also committed.

Thisi s a great example here.....messing with windows managers and desktops....non of this experimenting will corrupt my Ubuntu.....simply because of what's detailed above..

this is why i use this version of ubuntu. It's actually really good.

Thanks,

Vince.

---

### Post by LunaticHiatus on 2009-10-27
use could just run regular ubuntu in a virtualbox on windows. Sounds like virtually the same thing.

---

### Post by 3rdalbum on 2009-10-27
You can change window manager (but typically NOT desktop environment) by typing the window manager's name in the terminal, followed by a space, and then --replace. For instance:

```
compiz --replace
metacity --replace
openbox --replace
```

---

### Post by vinceROXY on 2009-10-27
Hi,

uh no.....i don't think Virtual box is the same thing as my set up here....simply because you must intall the OS into the virtual box right?....

maybe virtual box allows you to dump changes to an OS....(a kind of system restore to last session thing?)....

otherwise....any linux changes that were messy...would still remain in the virtualbox os?...right?.....which does not achieve the transparency that my approach achieves...

anyhow, VB is not as good performance as coLINUX distros like Portable Ubuntu.

thanks,

Vince.

---

