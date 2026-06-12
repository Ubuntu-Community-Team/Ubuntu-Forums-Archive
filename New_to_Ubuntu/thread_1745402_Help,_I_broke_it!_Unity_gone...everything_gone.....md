---
title: "Help, I broke it! Unity gone...everything gone...."
date: 2011-05-01
forum: New to Ubuntu
---

### Post by dpeer on 2011-05-01
Hi all!
   I saw a cool video of Ubuntu with a 3D desktop changer and thought I'd set it up...I am running 11.04 and when I disabled the wall and some other settings while enabling the cube, I broke something.

   I am posting from another install, but would like to get the other working again.  There is literally nothing on its desktop, no menus, no bars, just wall paper.  Any Ideas how to repair it?

Thanks for reading.

Dave

Tried:  unity --reset  command from tty1, no luck...any other ideas?

---

### Post by jnr2820 on 2011-05-01
Yeah, I have a similar problem...
I messed with the desktop cube options then I turned back off and unity was acting strange, but it didn't break completely until i ran 'unity --reset' in tty4

---

### Post by zilmar on 2011-05-05
Open a terminal window and execute ccsm, then you can check Unity option and everything else.

You can try CTRL+ALT+T or create a new shortcut in the desktop, when you click it it'll open a terminal also, then press CTRL+SHIFT+T to open a new tab and execute ccsm.

---

### Post by CrimzonEyed on 2011-05-05
Open terminal with the CTRL+ALT+T shortcut(or CTRL+ALT+F1 on login scren):
```

Sudo rm -rf .gnome .gnome2 .gconf .gconfd .metacity

```
Then restart your computer :) 
Did exactly the same thing when tried to get the 3D box working :P

---

### Post by lvharten on 2011-05-09
> **CrimzonEyed said:**
> Open terminal with the CTRL+ALT+T shortcut(or CTRL+ALT+F1 on login scren):


What if I can open Terminal with those shortcuts?! I'm kinda out of options.

---

### Post by bcooperb on 2011-05-10
I was having this problem as well @Ivharten, I couldn't get to a terminal after I broke unity. Pressing CTRL + ALT + T, pressing SuperKey, Pressing ALT + F2... nothing brought up a terminal. I don't remember if I could get to another TTY by pressing CTRL+ALT+F5

I will try: > Sudo rm -rf .gnome .gnome2 .gconf .gconfd .metacity

and see if that works.

---

### Post by Frogs Hair on 2011-05-10
If you get up and running and want to take a crack at getting a basic cube running use the link . I would not recommend 3d windows or cube deformation without more documentation . I have a basic cube running in Unity.  

[http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/](http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/)

---

### Post by bcooperb on 2011-05-10
> Sudo rm -rf .gnome .gnome2 .gconf .gconfd .metacity

This didn't seem to work for me. However what I did was(because it was the only thing I could execute) was make a Launcher(shortcut) on the Desktop by right clicking and going to "Create Launcher..."

Then I created one named CCSM with the command ccsm

This allowed me to launch CompizConfig Settings Manager. I then tried to go to Preferences and Reset to Default. This again I don't think worked at first. Because it didn't seem to turn on Unity.

I went back to the main area on CCSM and checked Ubuntu Unity Plugin. It had conflicts to resolve. I told it to Disable the one so that Unity could do what it needed to do. This time everything seemed to take and I restarted and Things seem to be working for now.

Hope this helps someone.

---

### Post by balbecdaze on 2011-05-19
Cheers bcooperb, this worked for me.

---

### Post by wildmanne39 on 2011-05-19
> **Frogs Hair said:**
> If you get up and running and want to take a crack at getting a basic cube running use the link . I would not recommend 3d windows or cube deformation without more documentation . I have a basic cube running in Unity.  

[http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/](http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/)
Hi, I set up cube in classic mode and everything works doing it that way. If you look in my signature below this text you will see one that says reset unity or compiz, this is a very nice howto to fix your problem.

---

