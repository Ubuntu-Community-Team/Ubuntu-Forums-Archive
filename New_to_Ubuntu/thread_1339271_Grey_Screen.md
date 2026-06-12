---
title: "Grey Screen"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by Beansof57 on 2009-11-27
I am using Ubuntu on two different computers (ine with Vista and one with XP) and they both keep "Grey Screening" on me.

I have seen a number of threads, but nobody seems to have a solution. I clean installed in both cases.

Is there NOTHING we can do about this? I use the PCs for work and I cabn't keep sitting back for 10/15 minutes every couple of hours.

I would HATE to have to go back to Mr Gates, but I DO have to sort it out. I am in the absolute beginners talk because that is very much what I am.

Thansk

---

### Post by ajgreeny on 2009-11-27
What exactly do you mean by "grey screening"?  It could mean that your screen goes to a command line, not a GUI, or it could mean that your system is working hard on something and all windows, and desktop, simply fade down to a grey colour.

Which is it please, then we can perhaps try to sort it out.

---

### Post by Beansof57 on 2009-12-01
Sorry about delay I've been away.

The screen fades to grey and the systems freezes up. Sometimes it's only a matter of waiting, but it often means rebooting.

Thanks.

---

### Post by lotharmat on 2009-12-01
I've had applications do this while they are chugging away, but never the whole Desktop.

Maybe an uninstall and reinstall of Gnome Desktop manager would help

Anyone?

---

### Post by Beansof57 on 2009-12-01
I have tried a complete re-install to no avail. How would I just re-install the Desktop Manager?

---

### Post by halitech on 2009-12-01
what video card do you have and have you installed the drivers for it? Also, try turning off the visual effects and see if you still have the same issue.

---

### Post by Beansof57 on 2009-12-01
NVIDIA GeForce 8400M GS
nvidia driver 173 installed.

---

### Post by NoaHall on 2009-12-01
Was it both from the same disk? Check the disk. 

Also, it might be screensaver.

And that's a old driver you're using.

---

### Post by Beansof57 on 2009-12-02
I have now installed version 185.

Yes, both installations were from the same disk. I'll check it.

---

### Post by 3rdalbum on 2009-12-02
> **Beansof57 said:**
> I have tried a complete re-install to no avail. How would I just re-install the Desktop Manager?

Reinstalling software that's already fresh is a complete waste of time. Maybe not on Windows, but on Linux it is.

It looks like your problem is related to a runaway program that's eating up your CPU and/or IO performance. You can find and kill CPU-intensive programs with the "top" command:

```
top
```

(most intensive is listed first, the list refreshes every 5 seconds)

Or you can find IO-intensive programs with the "iotop" command (needs to be installed in Synaptic first):

```
iotop
```

When you've found the culprits, kill them with the System Monitor program or by using the "killall" command.

---

### Post by Beansof57 on 2009-12-03
Thanks for the help, however the only thing using more than 3/4% of CPU is Firefox which oscillates between 50 - 60%. Is this normal for Firefox? I've got some 15/16 tabs open simultanneously.

---

### Post by carolina on 2009-12-05
> **3rdalbum said:**
> Reinstalling software that's already fresh is a complete waste of time. Maybe not on Windows, but on Linux it is.

It looks like your problem is related to a runaway program that's eating up your CPU and/or IO performance. You can find and kill CPU-intensive programs with the "top" command:

```
top
```(most intensive is listed first, the list refreshes every 5 seconds)

Or you can find IO-intensive programs with the "iotop" command (needs to be installed in Synaptic first):

```
iotop
```When you've found the culprits, kill them with the System Monitor program or by using the "killall" command.



I am having similar grey screen issues suddenly . How does one interpret the top data ? 

Example:

Tasks - 129     Running -  3     Cpu(s) - 93.5% id   CPU Usage - Firefox  varies - 6 -10%   Memory - 10%

None of these numbers look unusual to me but then i am not certain what is usual ..     :-)

---

