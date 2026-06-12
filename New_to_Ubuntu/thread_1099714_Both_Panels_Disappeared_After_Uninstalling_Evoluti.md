---
title: "Both Panels Disappeared After Uninstalling Evolution Kit and Kaboodle"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by AvocadoNia on 2009-03-18
**ISSUE: I need to reinstall/re-appear the panels. They disappeared after I uninstalled Evolution from the Synaptic Manager area and re-booted. **

Background and random thoughts: 

...It took me a few minutes to find an active URL/link in the ubuntu offline pages so that I could get back online...;)


Do I do a forced quit and then power up and select the place (forgot what it is called) where I can type in some ccommand like "gnome-panel" or something.

It has been ages since my Ubuntu class November 2008 and I haven't been on the forums in so long....I've forgotton lots of the vocabulary. 

Thanks. Oh, yeah...I am running Intrepid Ibex...8.10 if I recall correctly. I am on an eeePC with a partitioned hard-drive.

---

### Post by mcduck on 2009-03-18
just re-install the gnome-panel (by running "sudo apt-get install gnome-panel" or using Synaptic.)

You probably tried to remove all Evolution components, which caused gnome-panel to be removed as well since it depends on some of them (the calendar in the panel is pretty closely integrated to evolution and needs some Evolution components even if you don't use the Evolution itself).

---

### Post by AvocadoNia on 2009-03-18
Thanks so much! I'll try this now! :)

---

### Post by AvocadoNia on 2009-03-18
I restarted machine in recovery mode.
I went to root, entered the root password and got this prompt:
root@ANA~# (or something like that)
...right after the prompt I entered "sudo apt-get install gnome-panel"
and after severl lives of stuff the message was that some stuff was missing and I was given this sfuggestion:
"run apt-get update" or try "with --fix-missing"
So I tried lots of stuff, one at a time:
apt-get update-fix-missing
--fix-missing
run apt-get update fix-missing
sudo apt-get update fix-missing
apt-get update fix-missing
get istall gnome-panel
...there are 3 more permutations that I came up with that I haven't tried yet butI decided to pst first. Maybe I'm barking up the wrong tree.

Once I am in the root directory (if that's the right term) what should I type?

---

### Post by LowSky on 2009-03-18
you dont need sudo if you are root... so remove that

what i think you did was uninstall evolution which is part of a large ubuntu-dektop package which you somehow removed stuff from at the same time, normally doesn't happen but this is a cure all so, sorry evolution will get reinstalled, but hey panels are more important right!!!

so when logged in (under root)

```
apt-get update && apt-get upgrade && apt-get install ubuntu-desktop
```

---

### Post by mcduck on 2009-03-18
If you are in the recovery mode you are already logged in as the root user so you don't need to use "sudo".
```

apt-get update
apt-get install gnome-panel
```
("apt-get update" reloads the latest information about available packages from Ubuntu's servers, "apt-get install" installs the package(s) listed after the command.)

edit: You *could* just re-install the complete ubuntu-desktop, but that would also bring Evolution back. If you just install the gnome-panel it will only install those Evolution components that it needs to work.

Evolution is indeed part of the ubuntu-desktop package, but that's just a metapackage you don't really need for anything. Since you removed Evolution the ubuntu-desktop was removed as well but that doesn't mean removing any of the actual programs, just the metapackage itself. Gnome-panel was removed simply because it needs some of the evolution components. (you should, however, re-install the ubuntu-desktop metapackage when you upgrade to next Ubuntu version, just to make sure you get all the new applications and components that should come with the upgrade. But until that time, you don't need to have that package installed)

---

### Post by AvocadoNia on 2009-03-18
Thank you very much.
This (apt-get update && apt-get upgrade && apt-get install ubuntu-desktop) resulted, bottom line with this message:
"Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?"

I'm game.But I don't understand instructions. Looks like I am being give a choice of two differnt strings of characters to put in the command line from root.

Choice 1
apt-get update

Choice 2
--fix-missing

Please clarify the two choices and I will try them one at a time, as needed. Thanks for your help. :)

---

### Post by AvocadoNia on 2009-03-18
Thanks very much mcduck...
I will try these, one at a time at the command line in root:
apt-get update
apt-get install gnome-panel

have a good night. :)

---

### Post by mcduck on 2009-03-18
> **AvocadoNia said:**
> Thanks very much mcduck...
I will try these, one at a time at the command line in root:
apt-get update
apt-get install gnome-panel

have a good night. :)

That's actually starting to sound a bit like you haven't got a working network connection (or connection to Ubuntu's repositories). Does the "apt-get update" give any errors or does it find every repository?

---

### Post by LowSky on 2009-03-18
they want you to run I know it looks confusing but you will get the hang of it 

[code]apt-get update --fix-missing[code]

---

### Post by AvocadoNia on 2009-03-18
prior to the bottom line I quoted I saw 4 specifically cited items that, for lack of a better word, were un-fetch-able. 
3 indicated a URL that begins:
[http://us.archive.ubuntu.com/blah](http://us.archive.ubuntu.com/blah) blah blah
1 began:,
[http://security.ubuntu.com/blaw](http://security.ubuntu.com/blaw) blaw

Does this additional information help you help me? You two are great...mcduck and LowSky

Take care.

---

### Post by AvocadoNia on 2009-03-18
Am I to type this, exactly, after the prompt in root? 

[code]apt-get update --fix-missing[code]

(two spaces between the word "update" and "--")

---

### Post by mcduck on 2009-03-18
> **AvocadoNia said:**
> prior to the bottom line I quoted I saw 4 specifically cited items that, for lack of a better word, were un-fetch-able. 
3 indicated a URL that begins:
[http://us.archive.ubuntu.com/blah](http://us.archive.ubuntu.com/blah) blah blah
1 began:,
[http://security.ubuntu.com/blaw](http://security.ubuntu.com/blaw) blaw

Does this additional information help you help me? You two are great...mcduck and LowSky

Take care.

That would explain why you weren't able to install the package. For some reason or other you are not able to connect to some of the repositories, and the packages might be in that exact repository..

Did all other repositories work fine? And did you have any repository errors before? It seems that you need to get this working before you can re-install the panel.

In general I would solve that by changing to some other repository instead of the US one, but actually I'm able to connect to us.archive.ubuntu.com so it *should* be working..

---

### Post by kansasnoob on 2009-03-18
From the desktop (knowing you have no panels) hit Alt > F2. You'll see this:

[ATTACH]106874[/ATTACH]

Make sure "run in terminal" is ticked. Then type:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by AvocadoNia on 2009-03-18
Thanks for the tip. It saves me from rebooting in the recovery mode and going to root.Only thing the Alt/F2 command on the desktop isn't taking. Nothing happens. But this is great reference for future when I am trying to get to a terminal quickly, Thankss very much.

---

### Post by kansasnoob on 2009-03-18
Not what I'd hoped to hear!

Last ditch effort before reinstalling:

Boot into recovery mode and let it run, when it's done you'll be presented with a few options - STOP THERE - install the Ubuntu live CD but don't reboot.

Wait a couple of minutes for the CD to boot and choose to "repair broken blah-blah".

I doubt it will work without changing software sources and you don't seem to be able to get there!

---

### Post by AvocadoNia on 2009-03-18
Thank you.I will try this. I have the live CD and peripheral device close at hand.

---

### Post by rinrada on 2009-10-08
Exact same thing happened to me. I removed Evolution with the Synaptic Package Manager and when I rebooted the panels were gone. Fortuately I had set a short-cut key for the terminal and was able to use,
>sudo apt-get install ubuntu-desktop
to restore my panels. I was happy to see that the were returned to me with all my customizations.

I removed Evolution again with the same result.
I think the panels may still be there, but off the edge of the screen because when I pressed F11 in Firefox it expanded beyond the edges of my screen.

---

### Post by altplusf on 2010-12-23
> **mcduck said:**
> If you are in the recovery mode you are already logged in as the root user so you don't need to use "sudo".
```

apt-get update
apt-get install gnome-panel
```("apt-get update" reloads the latest information about available packages from Ubuntu's servers, "apt-get install" installs the package(s) listed after the command.)

edit: You *could* just re-install the complete ubuntu-desktop, but that would also bring Evolution back. If you just install the gnome-panel it will only install those Evolution components that it needs to work.

Evolution is indeed part of the ubuntu-desktop package, but that's just a metapackage you don't really need for anything. Since you removed Evolution the ubuntu-desktop was removed as well but that doesn't mean removing any of the actual programs, just the metapackage itself. Gnome-panel was removed simply because it needs some of the evolution components. (you should, however, re-install the ubuntu-desktop metapackage when you upgrade to next Ubuntu version, just to make sure you get all the new applications and components that should come with the upgrade. But until that time, you don't need to have that package installed)
Thanks alot this two commands worked like a charm.. thnx a ton

---

