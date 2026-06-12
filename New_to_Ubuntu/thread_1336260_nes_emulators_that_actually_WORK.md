---
title: "nes emulators that actually WORK"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by crowdedelevator on 2009-11-24
ive been looking up emulator after emulator both online from sites, and from synaptic and not a single one work. fceultra, nestra, darcnes,fakenes, nothing works and if i download them, i open them and they dont do anything.
i got nestra from synaptic and it doesnt even show up in games, and fceu doesnt do anything AT ALL.

---

### Post by amingv on 2009-11-24
```
sudo aptitude install zsnes
```

That's about the best one.

---

### Post by crowdedelevator on 2009-11-24
got that one. thats super nintendo. im talking nes the famicom

---

### Post by mgranet on 2009-11-24
I assume that you are using the gfceu frontend, correct? Perhaps the ROMS are bad.

---

### Post by amingv on 2009-11-24
Oh, I missed that.

Have you tried mednafen?

---

### Post by snakeman21 on 2009-11-24
> **amingv said:**
> Oh, I missed that.

Have you tried mednafen?

I second that... I was in your position a few days ago, till someone told me about mednafen.  It works perfectly.  The only drawback is the you have to use the terminal to run it.

```
sudo apt get install mednafen
```

Then, once it's installed:

```
mednafen /path/to/rom/name_of_rom
```

For info on how to change controls or any settings, type:

```
man mednafen
```

---

### Post by Cavsfan on 2009-11-24
Nvm

---

### Post by Steve.G on 2009-11-24
Found this: [http://ubuntuforums.org/showthread.php?t=141766]("http://ubuntuforums.org/showthread.php?t=141766")

which is admittedly a little old, but maybe some leads.. also, the last post makes a great suggestion of just running a windows based emulator (nesticle, nester, etc, etc) through wine.

---

### Post by crowdedelevator on 2009-11-24
well, ive tried running windows based ones through wine and nothing even opens, and as far as the one you have to get through the terminal, medafan, command not found

---

### Post by crowdedelevator on 2009-11-24
> **Steve.G said:**
> Found this: [http://ubuntuforums.org/showthread.php?t=141766](http://ubuntuforums.org/showthread.php?t=141766)

which is admittedly a little old, but maybe some leads.. also, the last post makes a great suggestion of just running a windows based emulator (nesticle, nester, etc, etc) through wine.


funny enough i went and did that just searching the forums, and it didnt work at ALL

---

### Post by Cheesemill on 2009-11-24
> **crowdedelevator said:**
> well, ive tried running windows based ones through wine and nothing even opens, and as far as the one you have to get through the terminal, medafan, command not found

There's a typo in snakeman21's solution, the first command should be:
```
sudo apt-get install mednafen
```

---

### Post by crowdedelevator on 2009-11-24
im not knowledgeable of the terminal so i wouldnt have known. i just copy paste. thanks!

---

### Post by crowdedelevator on 2009-11-24
> **snakeman21 said:**
> 
```
mednafen /path/to/rom/name_of_rom
```For info on how to change controls or any settings, type:

```
man mednafen
```
  another typo? this is the same situation. no file found

---

### Post by snakeman21 on 2009-11-24
> **crowdedelevator said:**
> another typo? this is the same situation. no file found

No, those are both correct... I apologize for the typo, though...  did you copy and paste?  If so, that's your problem.  You have to replace /path/to/rom/name_of_rom  with the actual path to your rom and name of your rom.  For example, let's say you put a rom called "mario.nes" on your desktop, and your username is matt.  You would type:

```
mednafen /home/matt/Desktop/mario.nes
```

Or if you put the rom in your home folder:

```
mednafen /home/matt/mario.nes
```

EDIT:  To give you a better idea of what's going on, here's what you're doing.  You are telling the computer to run mednafen, and use it to open a specific file.  You have to tell it where that file is located, and what it's name is.  It sounds complicated, but once you do it a couple times, you'll realize how easy it is.  Here's a suggestion.  It's what I did:  Make a folder to keep all of your roms in.  Call it 'nintendo' or 'mednafen' or something that's easy to remember.  And here's a tip:  When you're typing folder names and file names into the terminal, just type the first couple of letters, and hit TAB.  It will auto-complete the folder or file name.

---

### Post by snakeman21 on 2009-11-24
As a side note, I am currently planning on making a GUI for mednafen.  If and when I get around to it and finish it, I'll certainly upload it and post a link in the gaming and leisure forum for people to try out.  Mednafen is the best linux NES emulator IMO, so I think it deserves a GUI so it can be more easily enjoyed.

---

### Post by crowdedelevator on 2009-11-24
i cant thank you enough. im new to ubuntu  and linux as a windows user since i was like, 5. so no one has explained what to do in the terminal and i have all kinds of issues.

---

### Post by crowdedelevator on 2009-11-24
i put in the terminal
medafen/home/scott/desktop/dirtyharry.nes
no such file or directory.
its sitting on my desktop, as the file Dirty Harry.nes
like i said, im not too saavy on this os, but that seems 100% right to me.

---

### Post by snakeman21 on 2009-11-24
> **crowdedelevator said:**
> i put in the terminal
medafen/home/scott/desktop/dirtyharry.nes
no such file or directory.
its sitting on my desktop, as the file Dirty Harry.nes
like i said, im not too saavy on this os, but that seems 100% right to me.

Ah.  I see your problem.  The Terminal is case-sensitive.  And, you must include spaces.  Here is what you would type (notice the slash-spaces and caps):

```
mednafen /home/scott/Desktop/Dirty\ Harry.nes
```

Note the space after "mednafen."  If dirty harry is still on your desktop, just copy/paste the above command.

And as far as getting used to the Terminal goes, it comes with time.  The more you use it, the more comfortable with it you will become.  Eventually you will find yourself using it because it is easier for a lot of tasks.

---

### Post by crowdedelevator on 2009-11-24
> **snakeman21 said:**
> Ah.  I see your problem.  The Terminal is case-sensitive.  And, you must include spaces.  Here is what you would type (notice the slash-spaces and caps):

```
mednafen /home/scott/Desktop/Dirty\ Harry.nes
```Note the space after "mednafen."  If dirty harry is still on your desktop, just copy/paste the above command.

And as far as getting used to the Terminal goes, it comes with time.  The more you use it, the more comfortable with it you will become.  Eventually you will find yourself using it because it is easier for a lot of tasks.
i copy pasted, and it was case sensitive, but it didnt work. should i just rename it dirtyharry.nes

---

### Post by snakeman21 on 2009-11-24
> **crowdedelevator said:**
> i copy pasted, and it was case sensitive, but it didnt work. should i just rename it dirtyharry.nes

That is also an option... But what do you mean by "it didn't work"?  did you get an error?  or did the mednafen window come up without loading the game?  If the window opens, but the game does not work, then that means you have a bad rom.  If you got an error message, post it here.

I actually rename all of my NES roms so they don't have spaces or caps in them... Just makes it simpler.

---

### Post by TheNosh on 2009-11-24
in my experience nestopia works in wine.

---

### Post by crowdedelevator on 2009-11-24
nestopia worked. now how do i fix that horrid lag!? its killing me watching the intro to dirty harry all chopped up!

---

### Post by snakeman21 on 2009-11-24
I'm not sure... I couldn't get it working on my 64-bit system, so I can't offer any advice.

---

### Post by crowdedelevator on 2009-11-24
Well it doesnt work with  anything on the desktop, and when the mouse goes over it, it screws everything up. Its crappy but it works

---

