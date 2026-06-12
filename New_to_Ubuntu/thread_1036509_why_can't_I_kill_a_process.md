---
title: "why can't I kill a process?"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by mdsmedia on 2009-01-10
I've just finished watching a live stream on firefox.

I shut down the page and totem is still using all my CPU.

I've tried killing totem in top and ps x. It won't die.

What am I missing?

---

### Post by Cypher on 2009-01-10
Does the process have []'s around the name by any chance? If so, the process has been zombied (abandoned by the parent) and the only way to kill that process will be to restart your machine..

---

### Post by anewguy on 2009-01-10
Interesting.....I thought you could always kill any process via sudo kill -kill nnnnn

Guess I learned something here as well - thanks!

dave :)

---

### Post by mdsmedia on 2009-01-10
This is the process I want to kill...no [] around it

24852 ?        Dl   118:20 totem mmsh://tinopolis-pokerstarlive-eng-256k.wm.llnw

---

### Post by handydan918 on 2009-01-10
> **Cypher said:**
> Does the process have []'s around the name by any chance? If so, the process has been zombied (abandoned by the parent) and the only way to kill that process will be to restart your machine..

Uh, yeah, except for killing or restarting the parent process...
About the only thing that mandates a reboot with Linux is a kernel install.
Certainly not a zombie.

---

### Post by damis648 on 2009-01-10
Try
```
sudo killall -9 processname
```

---

### Post by mkvnmtr on 2009-01-10
damis what is the -9 for? I don't find it on the man page.

---

### Post by damis648 on 2009-01-10
> **mkvnmtr said:**
> damis what is the -9 for? I don't find it on the man page.

9 is the signal for a force kill. That should kill anything.

---

### Post by SunnyRabbiera on 2009-01-10
You can also use the force quit applet for your gnome panel, just right click and select "add to panel"
and scroll down to "force quit"
drag and drop it to the panel
done :D

---

### Post by handydan918 on 2009-01-11
Seems to be a lot of "noise"  around killing zombies....
What, nobody ever watched "night of the living dead"?
You can't kill zombies...they're already dead!

See [here]("http://www.cyberciti.biz/tips/killing-zombie-process.html") and [here]("http://www.linuxsa.org.au/tips/zombies.html")  for pretty good explanations of the problems and workarounds.

---

### Post by SunnyRabbiera on 2009-01-11
> **handydan918 said:**
> Seems to be a lot of "noise"  around killing zombies....
What, nobody ever watched "night of the living dead"?
You can't kill zombies...they're already dead!


Zombies: BRAAAAAAAAAAAAAAAINS! BRAAAAAAAAAAAAAAAAAAINS!

---

### Post by hotweiss on 2009-01-11
I always use htop to kill processes:

> sudo apt-get install htop

It has a many options to kill a process. I try *sigterm* first, and if that doesn't work *sigkill* works for sure.

---

### Post by ithanium on 2009-01-11
you can type xkill in terminal and press on the window which is not responding. Worked perfect so far

---

### Post by handydan918 on 2009-01-11
> **SunnyRabbiera said:**
> Zombies: BRAAAAAAAAAAAAAAAINS! BRAAAAAAAAAAAAAAAAAAINS!

Nice.
The eyeballs are a nice garnish, too.

---

### Post by stevoo on 2009-01-11
If you try normally and the process doesnt die. 
Then force it as said above and use -9 
sudo -9 kill .....

Zombies do die, like in all the movies(mostly). I remember i had the same problem with a process that wouldnt shut down. I eventually killed it. Let me see if i can find out again :) 

Ill keep you posted. But this seldom happens. What you usually need is -9

---

### Post by handydan918 on 2009-01-11
> **stevoo said:**
> If you try normally and the process doesnt die. 
Then force it as said above and use -9 
sudo -9 kill .....

Zombies do die, like in all the movies(mostly). I remember i had the same problem with a process that wouldnt shut down. I eventually killed it. Let me see if i can find out again :) 

Ill keep you posted. But this seldom happens. What you usually need is -9

Agreed. kill -9 usually works. When it doesn't, it's time for a recursive abortion...kill the parent!

---

### Post by afrodeity on 2010-04-02
kill a process by PID when it doesn't want to die?

---

