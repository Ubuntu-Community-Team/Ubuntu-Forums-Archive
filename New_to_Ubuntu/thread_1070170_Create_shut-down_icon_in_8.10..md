---
title: "Create shut-down icon in 8.10."
date: 2009-02-14
forum: New to Ubuntu
---

### Post by bob brazie on 2009-02-14
Create shut-down icon in 8.10.

How can I create a shut down icon that will just shut down my machine and turn it off and not ask about switching users or other options.

I would like to put this one function icon on my desktop or a panel. It would be nice to have it movable too.

Thanks in advance. Bob.

---

### Post by N4zgu1 on 2009-02-14
Right click on the desktop, create new launcher

the command is

```
sudo shutdown -h now
```

---

### Post by RomeReactor on 2009-02-14
> **N4zgu1 said:**
> Right click on the desktop, create new launcher

the command is

```
sudo shutdown -h now
```

That should probably be:
```
gksudo shutdown -h now
```
Otherwise, the user wouldn't see the prompt for the password.

---

### Post by bob brazie on 2009-02-15
Thanks but I don't want to be asked anything about a password. All I want is for it to shut down. 

Bob

---

### Post by RomeReactor on 2009-02-15
> **bob brazie said:**
> Thanks but I don't want to be asked anything about a password. All I want is for it to shut down. 

Bob

In that case, why not just use "shutdown" from the fast-user-switcher-applet on the top right of your screen?

---

### Post by bob brazie on 2009-02-15
I have removed that panel and use the MAC like icon bar. 

I am looking for other ways to just shut down, no questions asked. <G>

I can't seem to put the icon I created using "sudo shutdown -h now" in that icon bar though. I am still working on it.

Bob.

---

### Post by RomeReactor on 2009-02-15
> **bob brazie said:**
> I can't seem to put the icon I created using "sudo shutdown -h now" in that icon bar though. I am still working on it.

Bob.

Remember that the command should be:
```
gksudo shutdown -h now
```
If you use "sudo" you won't see the prompt for your password, meaning that nothing would happen.

---

### Post by geirha on 2009-02-15
I just looked around the system a bit for possible candidates, and I think this might do the trick, but I don't feel like trying it myself right now (in case it works ;) ). 
```
gnome-power-cmd.sh shutdown
```
Let me know what happens.

---

### Post by RomeReactor on 2009-02-15
> **geirha said:**
> I just looked around the system a bit for possible candidates, and I think this might do the trick, but I don't feel like trying it myself right now (in case it works ;) ). 
```
gnome-power-cmd.sh shutdown
```
Let me know what happens.

This is indeed a much better solution.

---

### Post by Grukmuck on 2009-02-16
cool, i was thinking about doing this too. just thought i'd bump this up in case anyone else was curious about how to do it.

thanks

-gruk

---

### Post by bob brazie on 2009-02-16
That does the trick nicely!

Thanks to everyone who helped me on this one.

Bob.

---

