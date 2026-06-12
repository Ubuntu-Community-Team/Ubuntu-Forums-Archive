---
title: "Ubuntu paralysis"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by Drjim on 2009-12-06
One of the reasons I wanted to try Linux is that I thought there were fewer bugs and glitches than windows. Twice now Ubuntu has frozen up on me. The last time was when I was teaching a class using Openoffice Impress for a slideshow. Everything froze, including the cursor. The only thing I was able to do turn the computer off and then reboot to windows so I could finish the presentation with powerpoint. 

I've added the item to the taskbar that will let me close an unresponsive program but that won't work without a mouse/cursor. 

So my questions are:

1. Is there anything I can do with keys like "ctrl, alt, del" in windows? Anything at all besides just turn off my computer?
2. Any idea what causes this? Something I can adjust to keep it from happening?
3. Is there a vs of Linux that's more stable than Ubuntu that might solve this problem?

Thanks,

Jim

---

### Post by Mrandersonjr on 2009-12-06
Try a new window manager,because it sounds like your computer isn't up to par with a default ubuntu installation and gnome as a Wm. Try xfce or fluxbox. Also,try disabling startup items,or entering in a terminal:

top

and then see what is taking most of your resources.:popcorn:

then:

killall PROCESSNAME

---

### Post by llamabr on 2009-12-06
It's certainly unusual.  Tell us more about the computer you're running it on, and in particular, along with impress, what else you have running.

---

### Post by themusicalduck on 2009-12-06
Some of the earlier versions of Ubuntu might be a bit more stable. 8.04 is supposed to be the most stable version but it might be worth trying 9.04 first. (I'm assuming you have 9.10 at the moment)

There's not much you can do if the cursor locks up, but using this key combination instead of doing a hard reset is better - ctrl + alt + prtscn + REISUB (with a sec between each letter keypress)

Also ctrl + alt + f1 should take you to a terminal but that's only useful if you know how to use it to fix things.

---

### Post by sandyd on 2009-12-06
> **Drjim said:**
> One of the reasons I wanted to try Linux is that I thought there were fewer bugs and glitches than windows. Twice now Ubuntu has frozen up on me. The last time was when I was teaching a class using Openoffice Impress for a slideshow. Everything froze, including the cursor. The only thing I was able to do turn the computer off and then reboot to windows so I could finish the presentation with powerpoint. 

I've added the item to the taskbar that will let me close an unresponsive program but that won't work without a mouse/cursor. 

So my questions are:

1. Is there anything I can do with keys like "ctrl, alt, del" in windows? Anything at all besides just turn off my computer?
2. Any idea what causes this? Something I can adjust to keep it from happening?
3. Is there a vs of Linux that's more stable than Ubuntu that might solve this problem?

Thanks,

Jim
ubuntu is based on the "unstable" branch of debian
perhaps you need debian lenny?

---

### Post by sandyd on 2009-12-06
> **Drjim said:**
> One of the reasons I wanted to try Linux is that I thought there were fewer bugs and glitches than windows. Twice now Ubuntu has frozen up on me. The last time was when I was teaching a class using Openoffice Impress for a slideshow. Everything froze, including the cursor. The only thing I was able to do turn the computer off and then reboot to windows so I could finish the presentation with powerpoint. 

I've added the item to the taskbar that will let me close an unresponsive program but that won't work without a mouse/cursor. 

So my questions are:

1. Is there anything I can do with keys like "ctrl, alt, del" in windows? Anything at all besides just turn off my computer?
2. Any idea what causes this? Something I can adjust to keep it from happening?
3. Is there a vs of Linux that's more stable than Ubuntu that might solve this problem?

Thanks,

Jim
seems like a video issue to me.
whats your video card. got any propriety/open source driver installed on the rig?

---

### Post by Drjim on 2009-12-06
> **llamabr said:**
> It's certainly unusual.  Tell us more about the computer you're running it on, and in particular, along with impress, what else you have running.

I'm running it on a Lenovo laptop, 1.6ghz, 1 gig ram, 120 gig hd. I was only running Impress. 

On windows everything runs pretty fast, ditto Ubuntu so I don't think I was running out of resources. I am running Ubuntu on a 30 gig partition of my hard drive. 

Jim

---

### Post by ArgentStar on 2009-12-06
To add the equivalant of the Windows Task Manager:

System > Preferences > Keyboard Shortcuts

Then add a Custom Shortcut using "gnome-system-monitor" and set Ctrl + Alt + Del as the key combo.

Not quite the same as the Task Manager, but close enough and definitely useful sometimes.

---

### Post by Drjim on 2009-12-06
> **carlee said:**
> ubuntu is based on the "unstable" branch of debian
perhaps you need debian lenny?


Um, are you calling me Lenny or is there a type of debian called lenny?

Jim

---

### Post by silverwood99 on 2009-12-06
i had the same problem with the locking up, but the lock-up included the keyboard...
 I tried installing Xfce, but it froze up even more. The box *is* about 10 years old, so it is probably that, but i thought ubuntu was supposed to be slightly faster than XP ? :confused: 
I do have ubuntu running stably on my new box and a laptop.

---

### Post by Swindlerz on 2009-12-06
> **ArgentStar said:**
> To add the equivalant of the Windows Task Manager:

System > Preferences > Keyboard Shortcuts

Then add a Custom Shortcut using "gnome-system-monitor" and set Ctrl + Alt + Del as the key combo.

Not quite the same as the Task Manager, but close enough and definitely useful sometimes.

Thanks, glad i've read this thread.

alt+ctrl+F1 brings the terminal but loses the vgui, i was like omg what happened? no idea how to start the vgui back in windows i usually run "explorer" but managed to get back by holding alt+f7 (fluke)

---

### Post by ArgentStar on 2009-12-06
> **silverwood99 said:**
> i had the same problem with the locking up, but the lock-up included the keyboard...
 I tried installing Xfce, but it froze up even more. The box *is* about 10 years old, so it is probably that, but i thought ubuntu was supposed to be slightly faster than XP ? :confused: 
I do have ubuntu running stably on my new box and a laptop.

I've got Xubuntu running stable on an 8 year old old PC, using Xfce.  But it's only stable providing I don't update anything.  As soon as I update I get problems with "usplash" wrongly detecting the monitor resolution and that usually stops it from reaching the desktop.

Runs much faster than WinXP on the same machine, though.  Opera loads ~5 seconds, whereas the WinXP install took ~15-20 seconds.  Similar differences across the board from what I can tell.

---

### Post by gradinaruvasile on 2009-12-06
> **Drjim said:**
> I'm running it on a Lenovo laptop, 1.6ghz, 1 gig ram, 120 gig hd. I was only running Impress. 

On windows everything runs pretty fast, ditto Ubuntu so I don't think I was running out of resources. I am running Ubuntu on a 30 gig partition of my hard drive. 

Jim

And what video card?

Open a terminal and type

```
lspci
```

Post the results. But i assume you have intel integrated card.

Also, do you have the visual effects (system -> preferences -> appeareance -> visual effects)  turned off? 
If not, turn them off. They can cause major stability issues on ati/intel cards with the opensource drivers. Also OpenOffice doesnt really like these effects, it had issues on every computer i tried.

Also, you might try 9.04. Its really stable now.

---

### Post by Drjim on 2009-12-06
> **themusicalduck said:**
> Some of the earlier versions of Ubuntu might be a bit more stable. 8.04 is supposed to be the most stable version but it might be worth trying 9.04 first. (I'm assuming you have 9.10 at the moment)

There's not much you can do if the cursor locks up, but using this key combination instead of doing a hard reset is better - ctrl + alt + prtscn + REISUB (with a sec between each letter keypress)

Also ctrl + alt + f1 should take you to a terminal but that's only useful if you know how to use it to fix things.

I'm using vs 8.04 of Ubuntu

---

### Post by Drjim on 2009-12-06
> **gradinaruvasile said:**
> And what video card?

Open a terminal and type

```
lspci
```

Post the results. But i assume you have intel integrated card.

Also, do you have the visual effects (system -> preferences -> appeareance -> visual effects)  turned off? 
If not, turn them off. They can cause major stability issues on ati/intel cards with the opensource drivers. Also OpenOffice doesnt really like these effects, it had issues on every computer i tried.

Also, you might try 9.04. Its really stable now.

I just turned visual effect off. How do I open a terminal?
Jim

---

### Post by mikewhatever on 2009-12-06
You'd better ask for support without mixing in Windows vs Ubuntu points of view. Instead, provide more, or at least some, technical details about the computer and the problem.

---

### Post by Drjim on 2009-12-06
Never mind, I hit ctrl alt f1 to open a terminal but then got confused. I was asked for my login name and then for a pw but when I tried to type in the pw, no letters appeared. is there a tutorial somewhere for using a terminal window?

Jim

---

### Post by venator260 on 2009-12-06
To open a terminal 

Applications>Accessories>Terminal

type ```
lspci
``` at the prompt.

---

### Post by Lyleb on 2009-12-07
...

---

### Post by JBAlaska on 2009-12-07
> **Drjim said:**
>  I was asked for my login name and then for a pw but when I tried to type in the pw, no letters appeared.

This is normal, the PW is being accepted, just not echoed to the screen. Type your PW and hit enter as normal.

To start a terminal, see venator260's post

---

### Post by Drjim on 2009-12-07
> **venator260 said:**
> To open a terminal 

Applications>Accessories>Terminal

type ```
lspci
``` at the prompt.

OK, I was able to do that. Thanks. A whole bunch of driver info came up. The only thing that was obviously about video was: Ricoh co ltd XP-Picture card controller. 

I hope this was what you're looking for. If not, could you give me a tip as to what to look for? Also, how do I close a terminal window and get back to my desktop? right now the only way I can figure to di it is to turn off and restart my computer and I know there must be a better way ;)

Jim

---

