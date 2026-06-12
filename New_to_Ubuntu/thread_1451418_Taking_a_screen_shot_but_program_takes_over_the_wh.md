---
title: "Taking a screen shot but program takes over the whole screen"
date: 2010-04-10
forum: New to Ubuntu
---

### Post by LepricahnsGold on 2010-04-10
OK. Here's what's up. I contribute to the web site [MobyGames](http://www.mobygames.com) and want to contribute screen shots of the Linux version of the remake of [Humphrey](http://retrospec.sgn.net/users/ignacio/humpi.htm). The problem I have is that when you run [Humphrey](http://retrospec.sgn.net/users/ignacio/humpi.htm), it takes the entire screen (including the bars top and bottom). I cannot access the Applications menu to do screen shots that way and the PrintScreen key option also fails. Is there a program that will let me take screen shots when the game takes over the entire screen? 
[COLOR="Red"][SIZE="5"]****WARNING: N00b alert! Keep it simple.****[/SIZE][/COLOR] :lolflag:

---

### Post by skyeric on 2010-04-10
Okay, I just played about with it a bit and the only way I can see to do it, is to set the screenshot to taken after a delay of say 1 minute. Then after clicking take screenshot open the game and start playing, after a minute close the game and they'll be a screenshot waiting for you.
hope this helps, I reckon there must be an easier way to do it I'll keep looking.

---

### Post by spiky001 on 2010-04-10
You could use a camara or mobile phone then cut and shut in gimp

---

### Post by codemaniac on 2010-04-10
try scrot..very simple to use..
$sudo apt-get install scrot

ALT+F2 ->>>scrot

---

### Post by ackley on 2010-04-10
I have to ask.

What's the point in this game?

And I don't mean that as in, "Why did they make this game at all?"

I mean...I don't understand the first level & how to beat it.

---

### Post by skyeric on 2010-04-10
haha i thought exactly the same thing, I'm pretty sure you have to just run over all the squares so they change colour, use shift to jump over the blue slidy thing and yea, I keep losing my last life on the far right.. seems quite a random game!

has the actual problem here been solved?

---

### Post by skyeric on 2010-04-10
Yea i was right just run over all the squares so they change colour, pretty easy once i realised you could hold shift/space and jump for an unnatural amount of time

---

### Post by LepricahnsGold on 2010-04-10
> **skyeric said:**
> Okay, I just played about with it a bit and the only way I can see to do it, is to set the screenshot to taken after a delay of say 1 minute. Then after clicking take screenshot open the game and start playing, after a minute close the game and they'll be a screenshot waiting for you.
hope this helps, I reckon there must be an easier way to do it I'll keep looking.

That wouldn't work as I want to take several screen shots, not just one.
[QUOTE=spiky001]You could use a camara or mobile phone then cut and shut in gimp [/QUOTE]

No good also, as taking a pict of a computer screen usually doesn't come out that great (MobyGames  is picky about quality)
[QUOTE=codemaniac]try scrot..very simple to use..
$sudo apt-get install scrot

ALT+F2 ->>>scrot [/QUOTE]
OK, I typed "sudo apt-get install scrot" in Terminal (minus quotation marks). It then asked for my password and, after some lines appeared, asked if I wanted to continue. I said "Y", several more lines ran then it returned to the start line that is there when it is first opened. I then pressed ALT+F2. The "Run Application" comes up. I type in "scrot". Nothing in the window and nothing happens when I press enter. I even tried restarting, just in case. Still no scrot. Why am I scrot-less? I have Ubuntu 9.10 (Karmic Koala), BTW.

---

### Post by mechro on 2010-04-10
You could run the screenshot application you normally use in the Alt+F2 run dialog,

---

### Post by LepricahnsGold on 2010-04-10
[QUOTE=mechro]You could run the screenshot application you normally use in the Alt+F2 run dialog, [/QUOTE]
Well, ordinarily, when it is not a full screen game, I just press PrintScreen. That doesn't work with Humphrey plus I just found ALT+F2 also doesn't work when in the game. <sigh> I may be S.O.L.

---

### Post by skyeric on 2010-04-16
If you're still interested then some cameras/video camera have the ability to plug into your pc via USB as if you were about to transfer photos/videos and then instead of transferring files actually take pictures or videos of the monitor. I know my video camera has this ability, if you're still looking for a solution, might be worth a shot.

---

### Post by DM was on fire! on 2010-04-16
skyeric, wouldn't that depend on Windows software though? Or have you tried it on Linux?

---

### Post by skyeric on 2010-04-16
Ah dam good point, one second i will try it right now

---

### Post by Cope57 on 2010-04-16
To get screenshots from fullscreen games, I use the gimp.   Open gimp, File > Create > Screenshot...

Then you can manipulate the settings to your preference.  You may take a screenshot of entire screen, or just a region of the screen, and also delay the seconds (up to 100) before the screenshot occurs.

---

### Post by skyeric on 2010-04-16
Yea you were right, didn't work, althought I can't get it to work on windows either now.. I'm sure im not making this up :S

Cope57 - I'm pretty sure that was suggested but he wanted to take multiple screenshots and timing them how he wanted them would probably be awkward as it doesnt seem to be possible to alt-tab in and out of the game..

---

### Post by ed-koala on 2010-04-16
Could it be that the game is commandeering keyboard input thus making Ubuntu's shortcuts not work?  If so, perhaps making a new shortcut for printscreen using the mouse might work.  I'm not sure if you can make mouse shortcuts tho, I haven't looked it up as I never had the need to do that.

---

### Post by skyeric on 2010-04-16
> **ed-koala said:**
> Could it be that the game is commandeering keyboard input thus making Ubuntu's shortcuts not work?  If so, perhaps making a new shortcut for printscreen using the mouse might work.  I'm not sure if you can make mouse shortcuts tho, I haven't looked it up as I never had the need to do that.

Good idea, System>Preferences>Keyboard Shortcuts, I seem to be struggling with getting the shortcuts to assign to the mouse though.

---

### Post by LepricahnsGold on 2010-04-16
Hmm. I must try a couple of these and see what happens.

---

### Post by Rayve on 2010-04-16
I don't know how it would work with a full-screen game ongoing, but you can try "Shutter" from Synaptic.  Lots of dependencies, but it was similar to "zapgrab" which I loved using in Windows, so hopefully it will help.

---

### Post by skyeric on 2010-04-17
> **LepricahnsGold said:**
> Hmm. I must try a couple of these and see what happens.

I still haven't figured out how to apply mouse short cuts but if you have any unusual keys on your keyboard (I have things like volume up and down as well as open email and search) it might be worth trying to change that to the print key as its unlikely the game will automatically take control of them as it wouldn't anticipate them being there.

Let us know how it goes,
Eric

---

