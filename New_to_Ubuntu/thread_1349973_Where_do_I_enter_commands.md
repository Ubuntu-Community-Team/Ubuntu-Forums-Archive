---
title: "Where do I enter commands?"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by Clueless In NC on 2009-12-08
I warned you I was clueless. I just turned on Ubuntu for the first time. I am preparing to run a program that I had installed by the previous owner (they updated everything for me). When I asked how to get started I was told 2 things.
1. make sure apache2 is running
2. type in an http command (I put the command in firefox and it was not happy, told me localhost wasn't right).

Question 1: What have I gotten myself into (used windows since its inception)
Question 2: How do I know if Apache2 is running, other than when I shut down I can see the screen before powering down.
Question 3: Where do I type in these magic commands? I have a nice Ubuntu  orange screen with applications (played some games), Places, and System.

The last time a computer frustrated me like this was in college when I dropped my Fortran cards! I haven't programmed since.

Any help or direction would be nice.

---

### Post by D3M0L1$H3® on 2009-12-08
Applications -> Accessories -> Terminal  for the commands

---

### Post by sgosnell on 2009-12-08
You don't need apache2.  That's server software, and I doubt you're running a server.  If you just want to browse the internet, open Firefox (the orange and blue icon in the panel) and type in the URL you want, or put something in the Google search box.

Everything can be accessed from the menus.  Windows uses the Start button, Ubuntu uses Applications, Places, and System menus.  Applications gives you most installed apps, Places opens the file manager which will let you browse the files on your computer, and System lets you make changes to your system.  It's not all that different from Windows, it's just that the menu choices are different.  Poke around and figure out where things are.  It won't break.

---

### Post by ssulaco on 2009-12-08
> **Clueless In NC said:**
> 
Question 1: What have I gotten myself into (used windows since its inception)
Question 2: How do I know if Apache2 is running, other than when I shut down I can see the screen before powering down.
Question 3: Where do I type in these magic commands? I have a nice Ubuntu  orange screen with applications (played some games), Places, and System.

Clueless here is some good reading:
[http://www.psychocats.net/ubuntu/installingsoftware#addremove](http://www.psychocats.net/ubuntu/installingsoftware#addremove)
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)
once you get the hang of synaptic and the terminal,installing and removing software is as easy as pancakes......have fun

---

### Post by Clueless In NC on 2009-12-09
Let me elaborate a bit on what I am doing.  My company will be using this computer along with a sharing program as a server for the other members of management and employees. We are small (less than 10 people) and scattered across the state. 
 
It sounds like apache2 is then needed since this is a server. 
 
The sharing program runs through firefox, so it sounds like something is not configured when it was installed.
 
Thanks for the reading info, that should help.

---

### Post by julianb on 2009-12-09
Since I can't remember the commands, I'll suggest you do what I would do:

do a google search for "how to start apache in ubuntu".

use the terminal to enter any commands. (see post #2 if you don't know how to open the terminal)

if it turns out Apache is not installed, use the "add new programs" feature of Ubuntu to get Apache. You might have to look around in the menus to find the "add new programs" feature. It might be in the "system" menu. It also might be in the "nameless" menu (the one that just has an icon) which is next to the menus that have names.

---

### Post by lykwydchykyn on 2009-12-09
The command to start apache is:
```

sudo service apache2 start

```

It is usually configured to start automatically on a default installation, though.

---

### Post by al071771 on 2009-12-09
im new myself but i have found out that if you press alt + f2 at the same time it gives you a command screen i found it on a linux help site hope it helps you too

---

