---
title: "Dosbox problem"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by rosswmcgee on 2008-12-25
up and down keys and enter key on the num lock side do not work in dosbox, on one Ubuntu 8.10 (intrepid) , works fine on the other. Is this a keyboard issue or is there a fix?

---

### Post by hovzio on 2008-12-26
Sorry, cannot give you a fix, bit I'm guessing its not the keyboard..I am having the exact same problem since I've installed intrepid. Prior to that dosbox worked well.

---

### Post by rosswmcgee on 2008-12-26
Well as I mentioned I am running two machines with Intrepid 8.10 one Dosbox  works fine. On the other I switched keyboards and still had the problem. We need an ubuntu geek for this one. No up and down keys so you can not play a game or use the num lock enter. Now why would one 8.10 work fine and the other not?

---

### Post by scorp123 on 2008-12-26
> **rosswmcgee said:**
> up and down keys and enter key on the num lock side do not work in dosbox That's a problem with the keyboard mapping. What you need is a "**mapper.txt**" file in your home directory that would tell DOSBox how to correctly interpret keystrokes. 

A quickie search on Google came up with these links. Please give this stuff a try:
[http://www.dosbox.com/wiki/Keymapper](http://www.dosbox.com/wiki/Keymapper)
[http://wiki.gp2x.org/wiki/DosBox#mapper.txt](http://wiki.gp2x.org/wiki/DosBox#mapper.txt)
[http://vogons.zetafleet.com/viewtopic.php?t=19851](http://vogons.zetafleet.com/viewtopic.php?t=19851)
[http://ubuntuforums.org/showpost.php?p=6020297&postcount=4](http://ubuntuforums.org/showpost.php?p=6020297&postcount=4)

---

### Post by rosswmcgee on 2008-12-26
I will try these, but would there be a command change in the Dosbox config file that would do the same thing? What is odd to me is that both config files seem to be the same. One works the other does not. Thanks

---

### Post by rosswmcgee on 2008-12-26
Yes I had looked at all of those execpt the last one, but I am not sharp enough to accomplish it.

---

### Post by scorp123 on 2008-12-26
> **rosswmcgee said:**
> but I am not sharp enough to accomplish it. Huh? :confused:

---

### Post by rosswmcgee on 2008-12-26
I do not know how to create the file used in the example. If this is an 8.10 bug why in one computer and not the other, and why not an update fix?

---

### Post by scorp123 on 2008-12-26
> **rosswmcgee said:**
> I do not know how to create the file used in the example. Uhhhm ... you open an editor and then copy & paste the example content, and then use "save as ..." and use the filename they suggest?

Sorry, I fail to see your difficulties here. It would be the same on any other OS too. Open an editor, copy & paste content into the empty file, use "Save as ...", give the thing the right file name ... :confused:

---

### Post by rosswmcgee on 2008-12-26
I did the cut paste as you suggested but it did not fix the problem.

---

### Post by rosswmcgee on 2008-12-26
Some success with key mapper in Dosbox however the keys then do not work in the game

---

### Post by Dedoimedo on 2008-12-26
Hello,
Dosbox config files are simple text files, any text ediror will do.
Did you check with numlock on/off?
Dedoimedo

---

### Post by rosswmcgee on 2008-12-26
I opened up the dosbox config example file, copied it deleted the same file from the offending computer, pasted it saved it but to no avail. Did I do what you suggested?

---

### Post by rosswmcgee on 2008-12-26
I found the easiest solution to the 8.10 dosbox bug at [http://www.dosbox.com/](http://www.dosbox.com/)

I opened terminal and pasted their suggested command. Now dosbox works fine the game still has some bugs but I can work around them. I still wonder why the problem exists in only one of my 8.10 computers. I think ubuntu should issue an update fix.

Thanks for helping. Ross

---

### Post by rosswmcgee on 2008-12-26
I found the easiest solution to the 8.10 dosbox bug at [http://www.dosbox.com/](http://www.dosbox.com/)

I opened terminal and pasted their suggested command. Now dosbox works fine the game still has some bugs but I can work around them. I still wonder why the problem exists in only one of my 8.10 computers. I think ubuntu should issue an update fix.

Thanks for helping. Ross

---

### Post by rosswmcgee on 2008-12-26
CTRL F1 command will not open  dosbox key mapper

---

### Post by Retro Gamer on 2009-03-23
..Well I tried the suggested fix for 8.10 on 9.04 and it doesn't work. Anyone have any ideas?

---

### Post by Merel 469 on 2009-05-12
> **Retro Gamer said:**
> ..Well I tried the suggested fix for 8.10 on 9.04 and it doesn't work. Anyone have any ideas?

Sorry, I can't help. If some "Ubuntu-Dosbox" guru comes with a solution, we would appreciate this solution to appear sufficiently detailed ... in "Absolute Beginner" language.

---

### Post by DhulKarnain on 2009-05-12
did you try changing the line usescancodes=true to **false** in the [sdl] section of the dosbox.conf file? 
my arrow keys too didn't work and that solved it.

---

### Post by rosswmcgee on 2009-05-12
I now have a new computer, keyboard and mouse with a clean install 9.04, but still have the same dos box problem. Yet my other computer now a 9.04 upgrade functions fine in dosbox. I need to use the right hand controls. If any one has an idea on this I would appreciate some more follow up. Question, could it be the monitor?

---

### Post by ashmew2 on 2009-05-12
Hello people , I had the same problems some time back..I dont exactly remember what i did , but as far as i can remember , I just made that ~/.dosboxrc file..Well , i still have it installed with DBoxFE (Graphical Frontend for Dosbox) and the arrow keys etc work flawlessly now.

Remove dosbox :
```

sudo apt-get remove dosbox && purge dosbox
```
```

sudo apt-get clean
```
```

sudo apt-get install dosbox
```

After its installed , Just open up your Home folder : Places > Home Folder.

And paste the file attached in there.


Also make sure that there is a file inside your home folder by the name : .dosboxrc
with the following :
> 
[sdl]
usescancodes=false 

Give your system a reboot.

Try running dosbox again.

---

### Post by rosswmcgee on 2009-05-12
There is no file  .dosboxrc  

I did the rest of your suggenstions. Now what?

---

### Post by ashmew2 on 2009-05-12
If the file has a . in front of its name like .dosboxrc , it will be hidden by default.
To view it , Open Home Folder , Press CTRL + H on your keyboard.

Try to find the file there.
If it isnt there , open a terminal :

```
nano ~/.dosboxrc

```

In the file that opens , copy paste :
> 
[sdl]
usescancodes=false

press Ctrl-X. Press Y.

Reboot.

Try running dosbox again.

---

### Post by rosswmcgee on 2009-05-12
There is a file called .dosboxrc.save 

How do I open it?

Note in the previous instructions there was no purge command.

---

### Post by rosswmcgee on 2009-05-12
I have tried every method to no avail: I wish some one could newby a solution for the dosbox key problem! 

sdl]
# fullscreen -- Start dosbox directly in fullscreen.
# fulldouble -- Use double buffering in fullscreen.
# fullresolution -- What resolution to use for fullscreen: original or fixed size (e.g. 1024x768).
# windowresolution -- Scale the window to this size IF the output device supports hardware scaling.
# output -- What to use for output: surface,overlay,opengl,openglnb.
# autolock -- Mouse will automatically lock, if you click on the screen.
# sensitiviy -- Mouse sensitivity.
# waitonerror -- Wait before closing the console if dosbox has an error.
# priority -- Priority levels for dosbox: lowest,lower,normal,higher,highest,pause (when not focussed).
#             Second entry behind the comma is for when dosbox is not focused/minimized.
# mapperfile -- File used to load/save the key/event mappings from.
# usescancodes -- Avoid usage of symkeys, might not work on all operating systems.

---

### Post by rosswmcgee on 2009-05-12
I had tried this before no dice/ tried it again and it works/ game works/ It is Whoopee time. Problem solved

---

### Post by ashmew2 on 2009-05-13
So its sorted out now ?  The arrows work now i mean ?

---

### Post by rosswmcgee on 2009-05-13
I found the easiest solution to the 8.10 dosbox bug at [http://www.dosbox.com/](http://www.dosbox.com/)

While this did not work for me in 8.10 it did in 9.04

If you are patient eventually a solution is found in the ubuntu forums!

---

### Post by john.ennew on 2010-05-28
In your .dosboxrc, or dosbox.conf file set the following:

usescancodes=false 

This worked for me.

---

