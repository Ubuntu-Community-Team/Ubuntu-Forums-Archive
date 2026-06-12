---
title: "Enabled effects in 11.04, restarted computer, gfx went away?"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by JDM_SOHC on 2011-05-14
So last night I installed 11.04 on my HP 1015dx, to get wobbly windows I installed Compiz Config, went in and enabled effects, and once I did that my theme went from black, to a white theme with colorful 3d icons in the taskbar for wifi, battery, etc.. So i was playing on the computer for a bit, shut it off, and turned it on today to see it's back @ the old black theme with not so vibrant graphics..? I right clicked on desktop and thought maybe it was the white theme in the list, but nope, still no colorful 3d'ish taskbar icons... Anyone know what may have happened..?? thanks..

---

### Post by wildmanne39 on 2011-05-14
> **JDM_SOHC said:**
> So last night I installed 11.04 on my HP 1015dx, to get wobbly windows I installed Compiz Config, went in and enabled effects, and once I did that my theme went from black, to a white theme with colorful 3d icons in the taskbar for wifi, battery, etc.. So i was playing on the computer for a bit, shut it off, and turned it on today to see it's back @ the old black theme with not so vibrant graphics..? I right clicked on desktop and thought maybe it was the white theme in the list, but nope, still no colorful 3d'ish taskbar icons... Anyone know what may have happened..?? thanks..

Hi, compiz does not work with natty, you need to open a terminal by typing alt f2 or ctrl alt +t and type unity --reset, give it about three minutes and then reboot. Dont worry about the errors it will list and you may have to manually restart but afterwards it should be back to normal.:)

---

### Post by Hedgehog1 on 2011-05-14
+1 ON THE UNITY RESET:

Please do a **<ctrl> + <alt> + t** to get the terminal.

From the terminal, please do this to reset your Unity to a functional state (factory defaults):

```
unity --reset
```

There will be some error messages - ignore them please.

Logout **<ctrl> + <alt> + <Delete>** and reboot...


YOU CAN GET COMPIZ EFFECTS IN NATTY 'UBUNTU CLASSIC' MODE: [**_Natty Info: Your UI options_**]("http://ubuntuforums.org/showthread.php?t=1741293")


***The Hedge***

:KS

---

### Post by wildmanne39 on 2011-05-15
> **Hedgehog1 said:**
> +1 ON THE UNITY RESET:

Please do a **<ctrl> + <alt> + t** to get the terminal.

From the terminal, please do this to reset your Unity to a functional state (factory defaults):

```
unity --reset
```

There will be some error messages - ignore them please.

Logout **<ctrl> + <alt> + <Delete>** and reboot...


YOU CAN GET COMPIZ EFFECTS IN NATTY 'UBUNTU CLASSIC' MODE: [**_Natty Info: Your UI options_**]("http://ubuntuforums.org/showthread.php?t=1741293")


***The Hedge***

:KS

Hi, do you think they might make compiz effect like the cube compatible in the next release, I know that there is a work around for this but I am hesitate to tell new people about it.:P

---

### Post by Hedgehog1 on 2011-05-15
> **wildmanne39 said:**
> Hi, do you think they might make compiz effect like the cube compatible in the next release, I know that there is a work around for this but I am hesitate to tell new people about it.:P

Right now I can only get a reliable 'cube' and 'Wobbly Windows' in the 'Ubuntu Classic' mode.  I also don't want folks doing that work-around to get the cube sorta-working with Unity. Any settings changes later they can mess up Unity.

I understand that Unity will be retooled to use Qt rather than Compiz for 11.10.  Once that happens, I don't know if the cube will be OK in Unity or not.

***The Hedge***

:KS

---

### Post by wildmanne39 on 2011-05-15
> **Hedgehog1 said:**
> Right now I can only get a reliable 'cube' and 'Wobbly Windows' in the 'Ubuntu Classic' mode.  I also don't want folks doing that work-around to get the cube sorta-working with Unity. Any settings changes later they can mess up Unity.

I understand that Unity will be retooled to use Qt rather than Compiz for 11.10.  Once that happens, I don't know if the cube will be OK in Unity or not.

***The Hedge***

:KS
Hi, thank you for that information, I really appreciate it.I want to ask you a question but I do not want to hijack this thread is there a thread I can ask it on?

---

### Post by fidamehran on 2011-05-15
I mentioned in another of my threads, ([http://ubuntuforums.org/showthread.php?t=1758685]("http://ubuntuforums.org/showthread.php?t=1758685")) that I also found out that Compiz and Unity do not coexist very well. But I have it installed in Unity and it works quite good. Only if I don't go changing ay effects in CCSM or turning on the water effects, the Wobbly Windows is good.
But Desktop Cube doesn't work.

---

### Post by JDM_SOHC on 2011-05-15
Oh alright, so maybe when I installed the CCIM or whatever Compiz Config is called, it messed up something but why did it make my taskbar icons into cool little 3d icons..?? Is there a way we can do that without it being an accident lol..??

---

### Post by wildmanne39 on 2011-05-15
> **fidamehran said:**
> I mentioned in another of my threads, ([http://ubuntuforums.org/showthread.php?t=1758685]("http://ubuntuforums.org/showthread.php?t=1758685")) that I also found out that Compiz and Unity do not coexist very well. But I have it installed in Unity and it works quite good. Only if I don't go changing ay effects in CCSM or turning on the water effects, the Wobbly Windows is good.
But Desktop Cube doesn't work.
Hi, I have the cube and all working in unity, by logging out and logging in under ubuntu classic then you can set up all the effects you want.:P

---

### Post by wildmanne39 on 2011-05-15
> **JDM_SOHC said:**
> Oh alright, so maybe when I installed the CCIM or whatever Compiz Config is called, it messed up something but why did it make my taskbar icons into cool little 3d icons..?? Is there a way we can do that without it being an accident lol..??

Hi, I am really not sure about the icons changing, but I installed awn launcher and I boot in ubuntu classic now and I have nice icons with the awn launcher.You can find it in synaptic.:D

---

### Post by fidamehran on 2011-05-16
> **wildmanne39 said:**
> Hi, I have the cube and all working in unity, by logging out and logging in under ubuntu classic then you can set up all the effects you want.:P

Cool input, Buddy. Will try it out.

---

### Post by wildmanne39 on 2011-05-16
> **fidamehran said:**
> Cool input, Buddy. Will try it out.

Hi, I wish you the best, i sure missed the cube I am glad to have it back.

---

