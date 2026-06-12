---
title: "virtual box ctrl"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by misswham on 2010-03-22
The ctrl button stopped working in virtual box.  When i press ctrl f, i cant get to fulllscreen and when i press the ctrl i cant get the mouse back.  It worked forever and now it stopped.  what does this sound like?  i noticed a lot of settings dont stick in linux.  i have to always go back and reset some things when i havent touched or changed anything.

---

### Post by Michael Dooley on 2010-03-22
I think that you have to press the right-side Ctrl key and follow by pressing the F key. Does that work?

I generally press Rt-Ctrl and then (while holding down the Rt-Ctrl key) press F twice to cycle from almost full screen to small and then to full.

---

### Post by gadolinio on 2010-03-22
In my case, i had to press Ctrl and the right arrow. No F. No idea why, but this was the default. Then changed it to something else.

---

### Post by misswham on 2010-03-22
yes i have done what i have been doing forever but i just realized the control keys arent working at all.  When I press ctrl v to paste it wont.  I logged out of linux and logged into windows 7 and it works there.  this just started last night.  it has worked fine but now it has stopped.  i have changed 3 keyboards and the same thing is happening.  any ideas?

now when i right click and hit paste it will paste but for some reason my ctrl keys arent working.

---

### Post by Michael Dooley on 2010-03-22
Start Sun Virtual Box, File, Preferences, Input. See if the host key is still right-control. 

The other setting you might investigate is System, Prefeences, Keyboard and/or System, Prefeences, Keyboard Shortcuts - although I found no specific setting in these settings for virtual box.

---

### Post by misswham on 2010-03-22
yes it is checked also i went to keyboard and i dont know what setting would have changed to disable my ctrl keys.  keyboard preferences was on default and that said Ireland but i changed it to USA.  I assume that is what it should be on but I dont understand what could have happened because I didnt do anything to disable my ctrl keys.  i use them alot ctrl-v for pasting and ctrl-z for undoing.  any other ideas?

---

### Post by Michael Dooley on 2010-03-22
I'm fresh out of ideas here. Have you tried Googling the problem yet?

---

### Post by misswham on 2010-03-23
My ctrl buttons are totally dead now. not only in VIRTUAL BOX but in mint also. I cant get to fullscreen in VB and I cant get the cursor out of VB because I have to use the right ctrl key. I have checked the HOST KEY and everything is set fine.

Now in mint, I cant copy n paste using ctrl-c ctrl-v or undo ctrl-z.

I REALLY need to use my VB and I need to be able to use my ctrl buttons. Someone in an Ubuntu forum said that they did some reasearch and found a thread where someone elses ctrl keys went dead and they put a command in the terminal

setxkbmap

i tried the command in the terminal

setxkbmap

and nothing happened. I hit enter afterwards and it didnt even ask me for my passwordl

Any ideas?

---

### Post by Michael Dooley on 2010-03-23
Open a terminal and type "man setxkbmap"

You'll see how this command can be used, the various arguments that the command requires to do anything (I think) involving changing the keyboard settings.

Myself, I would rather use System, Preferences, Keyboard to change keyboards or keyboard layouts. You can also change keyboard layouts (and graphics settings) in the recovery console accessed at boot-up. 

Good luck and please post back on how things go.

---

### Post by JKyleOKC on 2010-03-23
> **misswham said:**
> I REALLY need to use my VB and I need to be able to use my ctrl buttons.To get the use of VB back while trying to fix the problem, try changing the VB Host Key to something other than Right-Control. I switched it to Menu (the key just to the left of Right-Ctrl on most Win keyboards) in order to free up the control key for other uses.

To make the change, open up VB and select File->Preferences->Input. Then highlight the host key edit box, and just press the new key. It will change automatically, and the change will apply to all VMs.

It won't help with cut and paste operations but it should let you get back to using VB...

---

### Post by misswham on 2010-03-23
Thank you sooo much.  I changed the host key and it worked. 

Now, is there a way to change the function of the ctrl keys to another in mint?

---

### Post by misswham on 2010-03-24
Didnt fix the issue but went around it. I went to VB and changed my HOST KEY to the windows key by going to file preferences and input. so that problem was taken care of and as for the regular mint, i just went into keyboard options and then layouts option and swapped the ctrl key with the caps lock key.

i dont know what happened but I guess this is how it is going to be until i get another OS.

---

### Post by misswham on 2010-03-25
I just reinstall the whole OS and in VIRTUAL BOX, i made the menu key the host from jump, just in case VB was the culprit in the first place.

thanks everyone.

---

