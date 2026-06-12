---
title: "Self opening terminal"
date: 2011-05-27
forum: New to Ubuntu
---

### Post by fractalman on 2011-05-27
everytime i open my sound manage i get a terminal open as well, when i try and close the terminal it just reopens, if i shut the sound manager it still keeps reopening and i have to reboot  to be able to use my system without the terminal showing

Any ideas please?

---

### Post by fractalman on 2011-05-27
OK, when the terminal was opening itself, the speech dispatcher was starting too and i was hearing the speech, on closing my browser after the previous post the pc went into overdrive so i checked the system monitor and the speech dispatcher was showing 80% cpu usage. Not sure why as i disabled all assistive tech. Anyway i removed the speech dispatcher package through the synaptic package manager and now i can open the sound manager without the terminal automaticly opening as well.

sorry for the pointless thread! :confused:

---

### Post by ipatfrmww on 2011-05-27
The exact same thing happened to me about 2 weeks ago.
It really freaked me out the first time cause there was this strange voice telling me I was using unity (orca welcome message).
It took me a long time to work out how to stop it too. I think I uninstalled orca.
you'd think sudo killall orca would do the trick, but nooo, that just made it angry.

---

### Post by ubu2008 on 2011-05-28
I just installed Ubuntu 11.04 2 days ago. As post install I did not do much, but I downloaded Adobe. I know we are not supposed to get in Ubuntu malware and viruses. I hope this will help to somebody. I visited few websites about Ubuntu in particular few that were talking about the Unity vs Gnome. I wrote my opinion on Unity vs Gnome. Somehow, I caught a bug attacking Ubuntu, more exactly I caught a malware program.  I chose  to use Gnome. The way the malware exhibited itself, if I started sound-preferences applet, the malware would  say an annoying sentence something about testing the Gnome. It would also open a Terminal which you could not kill, if you try to close it, it would again say the sentence. I tried to figure out what happened and I did reinstall everything in package manager that had the word sound in it, which did not help. As I was staring on the running processes, I saw that when I click on the close the terminal, the speech-dispatcher moves in the list. I killed the speech-dispatcher and I removed the package. It seems that it was attacked and become malware.

---

### Post by ipatfrmww on 2011-07-22
First lesson for new ubuntu users is this:
That thing that went wrong with that other thing is not a virus, its just a bug (they're everywhere).

Honest. You don't get viruses in linux. And if you got one for real then count yourself lucky. (and then tell everybody about it cause we don't want it to spread).
You could count all of the malware for linux on one hand. And even those 4 are not very good viruses.

However you would need an enourmous database to record all the bug's: [B][https://launchpad.net/](https://launchpad.net/)
807,957[/B] apparently, and thats just ubuntu.

The problem you described sound just like what happned to me, and i'm pretty sure it is a bug not a virus. 
Its the accessibility program getting all confused and turning itself on when it shouldn't. If you were blind then you would want it to do that. The reason you can't kill the window is cause it's being restarted by some other proccess (in-case you accidentaly close it, which if your blind would be a problem).

I think know now what causes it. It's cause we were all using classic ubuntu (gnome) at some point, and then we opened the sound-preferences applet. Which triggers the accessibility daemon (somehow). This bug probably wasn't noticed in beta cause the development focus was on unity. Unless I'm completely wrong that is.

I heard that classic gnome isn't going to be in oneiric so probably no point reporting this bug on launchpad.

---

