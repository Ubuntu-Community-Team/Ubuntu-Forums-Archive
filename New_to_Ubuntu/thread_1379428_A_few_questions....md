---
title: "A few questions..."
date: 2010-01-12
forum: New to Ubuntu
---

### Post by Dreakon on 2010-01-12
I tried out Ubuntu on my flash drive last night and it was pretty interesting to say the least.  It worked pretty well, my wireless could connect and despite lowering from 60% signal to about 15% after a few minutes, it seemed to stay pretty stable after that.  My desktop was at 1280x800 upon startup and stayed that way, so I guess my integrated video chipset (Intel x4500HD) was working well enough.  I have a couple of questions though...

1. If I were to play a game or two with Wine, would I be able to put shortcuts that will directly launch the games into the bar at the top of the desktop?  Or will I always have to fumble around in the Terminal or whatever to run games?  I don't care if it's terribly complicated, as long as I eventually can get it to a point where the game is in the top bar (Applications>Games>etc) and launchable with a single click.

2. I noticed that my touchpad worked pretty well, but clicking with the touchpad only seemed to work like half of the time.  I don't mean the buttons below the actual pad, but like tapping the pad to left click.  It was enabled in the preferences, and it worked sometimes, but id sit there tapping the pad like 4-5 times before it'd actually click.  Anyone else notice that, and/or is there anything I can do about it?

3. I didn't notice anything like this, but is there any way to disable the fancier things for the sake of performance?  Like the animations when minimizing and maximizing things?  That kinda stuff?  I like my laptop to be running fast and cool, if at all possible.

4. On that same note as 3, in Windows Vista and 7, I can limit my CPU to lower speeds which makes it run cooler (at the cost of running slower).  It also increases battery life.  Is there anything like that in Ubuntu?

Thanks guys, hope my questions don't annoy anyone. Have some popcorn! :popcorn:

---

### Post by nothingspecial on 2010-01-12
Right click on the desktop, choose change desktop appearance (or whatever it says) and change visual effects to none.

---

### Post by lisati on 2010-01-12
2. My preference is to use a USB mouse
4. There's a CPU preference monitor which I have on my top panel. One of its capabilities is to assist in controlling cpu speed. You can add it by right clicking on the panel, then add-to-panel. There's probably something suitable in the list that pops up.

---

### Post by patchwork on 2010-01-12
1.  I just write a quick script in a text editor to start my games in wine.  A quick example:
        
        #!/bin/bash
         cd /home/kevin/.wine/drive_c/Program_Files
         wine SoFMP.exe
  
After making this script executable using chmod, this script can be run.  Creating a launcher to this script will enable you to put it in the panel.

---

### Post by Dreakon on 2010-01-12
Heh, alrighty... I think that's everything. ;)

Anyone have any more information on getting my touchpad to function optimally?  I have a bluetooth mouse I forgot to test, but I still prefer to use my touchpad if I take my laptop to school or to someone elses house, or if I opt to use my laptop in bed like last night.

Thanks guys!  Very fast responses around here lol.

---

### Post by TBABill on 2010-01-13
I think it's something with Linux that isn't just inherent to Ubuntu. I have both it and Mandriva 2010 (and used others recently) and they all have sensitivities to the touchpad when trying to click. One thing I found helped a little was disabling scrolling via touchpad (it was irritating anyway to me). But, even with the buttons I had to click more than once, but usually during Internet browsing and clicking a hyperlink.
 
Wish I had a fix for you, but at least you know you're not alone on that one.

---

### Post by 3rdalbum on 2010-01-13
> **Dreakon said:**
> 4. On that same note as 3, in Windows Vista and 7, I can limit my CPU to lower speeds which makes it run cooler (at the cost of running slower).  It also increases battery life.  Is there anything like that in Ubuntu?

I think you'll find that it actually doesn't increase battery life. Intel wrote a program for Linux called "Powertop" that helps you work out what programs and settings are causing battery drain, and in their testing they found that it's better to upscale the speed of the CPU whenever it's hard at work, and then downscale its speed again when done.

The aim is to get the CPU to the deepest sleep state as quickly as possible. If your CPU is running at the slowest speed without scaling, then it works inefficiently for longer before being able to sleep again.

The CPU should actually be cooler with scaling on, assuming you're not doing long CPU intensive operations on it. And if you're doing long CPU intensive operations... then get a desktop, it'll be an order of magnitude faster.

---

