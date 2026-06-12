---
title: "Ultimate N00B Question!!!"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by scubscub on 2009-01-16
This is the sort of question which, I suspect, fundamentally distinguishes us terminal noobs from those who give the impression of knowing what they're doing.

Used as I am to Mac and Windows, I rely on the GUI drop-down (or up) list of programs installed to know ... what ... programs ... are installed...

Now I have discovered that it is really not much trouble to install a program and run it from the command line .. not really more trouble than GUI, as long as I know that it is installed, and know the command to run it.

BUT, six months after installing such a program, I have no way of knowing (ie remembering) what such programs are installed, or how to run them!

So, I ask,

1. is there a way to know or list all the programs installed on my computer, regardless of whether they get themselves listed in the GUI under Applications?

2. Is this not the Ultimate N00b Question?

---

### Post by Paqman on 2009-01-16
> **scubscub said:**
> 
1. is there a way to know or list all the programs installed on my computer, regardless of whether they get themselves listed in the GUI under Applications?


Aye:
```
dpkg --get-selections > installed-software
```

This will spit out a text file with every single package on your machine (and show ones you've removed)

You could of course also open Synaptic and filter just for installed packages.

> 
2. Is this not the Ultimate N00b Question?

Nope, it's a moderately techy one actually.

---

### Post by TVTrukChik on 2009-01-16
Thanks, this is very good to know.  Often, I read about something, try it out, and then forget that I've installed it.  Now I have a list and I can just "man whatever" to refresh my memory about what I've done.

---

### Post by Hospadar on 2009-01-16
use synaptic, it is the graphical frontend for aptitude, the package manager for ubuntu.

System->Administration->Synaptic

---

### Post by scubscub on 2009-01-16
> **Paqman said:**
> Aye:
```
dpkg --get-selections > installed-software
```


Thanks for this.

Though, I run that and it gives me a scary long list, which actually I can only scroll back as far as the letter L on (that I assume is a separate issue regarding terminal)

and I actually can't identify the programs on this which I could (or could I?) run from terminal, versus the ones which are various dependencies of other programs etc. Me, the first thing I see is a lot of xserver.org--etc. files...

So I see this is technically the right answer, but not exactly what I envisioned, though perhaps with more know-how, I could use this...

---

### Post by scubscub on 2009-01-16
> **Hospadar said:**
> use synaptic, it is the graphical frontend for aptitude, the package manager for ubuntu.

System->Administration->Synaptic

Uhhhh....     yeahhh..... like, thanks dude........


No like totally.....



thanks......

yeah, "synaptics".... never thought of that....

hmmmmm........

>thought-provoking<....

---

### Post by steveneddy on 2009-01-16
Maybe......  uh.....

we could.....  huh - mark this...

as......  well.... solved.. :)

---

### Post by handydan918 on 2009-01-16
> **scubscub said:**
> Thanks for this.

Though, I run that and it gives me a scary long list, which actually I can only scroll back as far as the letter L on (that I assume is a separate issue regarding terminal)

and I actually can't identify the programs on this which I could (or could I?) run from terminal, versus the ones which are various dependencies of other programs etc. Me, the first thing I see is a lot of xserver.org--etc. files...

So I see this is technically the right answer, but not exactly what I envisioned, though perhaps with more know-how, I could use this...

No idea how this would work, but it seems like youmight be able to use the dpkg command and pipe the output into which to locate the executables....
Undoubtedly a better way to do it, but that just popped into my alleged mind.

---

### Post by talsemgeest on 2009-01-16
> **steveneddy said:**
> Maybe......  uh.....

we could.....  huh - mark this...

as......  well.... solved.. :)
Threads can no longer be marked as solved due to the recent forum problems. The [solved] plugin has been disabled along with the thanks plugin for stability.

Also, to the original poster, please refrain from creating thread titles such as "Ultimate N00B Question!!!". This tells us absolutely nothing about your post and it is rather irritating when everyone does it.

---

### Post by Denestria on 2009-01-17
> **scubscub said:**
> 
Though, I run that and it gives me a scary long list, which actually I can only scroll back as far as the letter L on (that I assume is a separate issue regarding terminal)


> dpkg --get-selections **> installed-software**

The output of this command was redirected to a file so you could view it easily in a text editor.  The > means redirect and installed-software is the name of the file.

---

### Post by chriscross93 on 2009-01-17
> Quote:
2. Is this not the Ultimate N00b Question?


Nope, it's a moderately techy one actually.

*agree*:)

---

### Post by 73ckn797 on 2009-01-17
A simple way to see what is installed, as has been mentioned, is to  go to System/Administration/Synaptic Package Manager and select installed programs under section (at lower left side).

You can also, while in Synaptic Package Manager, go to File/History and see when something was installed to give you a map to  your activity for package installations.

See attached image.

---

### Post by scubscub on 2009-01-17
> **Denestria said:**
> The output of this command was redirected to a file so you could view it easily in a text editor.  The > means redirect and installed-software is the name of the file.

AHA! This is the answer then. Beautiful.

Installed programs in Synaptic works too, but will that show me anything that wasn't installed through synaptic, eg deb packages?

Anyway, thanks everyone. 

And Talsemgeest, I apologize for bad thread title protocol. What's worse, I am fully aware of the proper way to phrase a title, but went ahead with "Ultimate Noob Question" with the full intention of drawing attention.  No need to point out, it worked quite well...

---

### Post by seagullplayer77 on 2009-01-17
> **Hospadar said:**
> use synaptic, it is the graphical frontend for aptitude, the package manager for ubuntu.

System->Administration->Synaptic

Yup. This would probably be your best choice. Synaptic will list all the packages you've installed to your computer---libraries, plugins, programs---everything. If you go Applications > Add/Remove, that will list most of the programs you've installed, but I've noticed that it won't list them all.

Btw, if you've installed things from outside sources (Skype, Cairo-Dock, AIM, etc.) that aren't in the Ubuntu repos, then you might have some trouble finding those, because they certainly won't show in Synaptic and they might not show up in Add/Remove either.

---

