---
title: "SuperTux crashes"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by steigerjb on 2009-12-19
Why can't I play SuperTux anymore with Karmic Koala? It worked fine in Jaunty-

I'll launch it and then it'll immediately close. 

I wanna play it. I love that game!

---

### Post by earthpigg on 2009-12-19
can you run it in a terminal and show us the output?

to find the terminal command, right click on 'applications, places, system' and hit 'edit menus'. navigate to it, and find out what command the menu entry runs. thats the command to run in terminal.

---

### Post by steigerjb on 2009-12-19
> **earthpigg said:**
> can you run it in a terminal and show us the output?

to find the terminal command, right click on 'applications, places, system' and hit 'edit menus'. navigate to it, and find out what command the menu entry runs. thats the command to run in terminal.

```
joe@joe-laptop:~$ supertux
Datadir: /usr/share/games/supertux
Warning: Could not open joystick -1.
The Simple DirectMedia error that occured was:
There are 1 joysticks available

Segmentation fault
joe@joe-laptop:~$ 
```

---

### Post by earthpigg on 2009-12-19
what if you unplug the joystick? just so we can confirm that the joystick is the issue, and then go from there.

---

### Post by steigerjb on 2009-12-20
> **earthpigg said:**
> what if you unplug the joystick? just so we can confirm that the joystick is the issue, and then go from there.

what joystick? i don't have one

---

### Post by Chakra_ on 2009-12-20
I have the same problem. It says segmentation fault when I try to run supertux and no joystick here either. JOYstick....haha! :lolflag:

---

### Post by earthpigg on 2009-12-20
just out of curiosity... are there any config files in your ~?

if the program never started correctly, there shouldn't be.

see if there is a /home/username/.supertux or .super or .games/supertux or something like that folder that couldn't possibly be anything except supertux config files that should not exist yet.

if they are there, delete them.

---

### Post by a20365354 on 2009-12-21
Same problem here. :(
Please help...
If you have /home/username/.supertux/config , please post the content of the file here so we can copy the file in our computer,I think that can solve the problem.
Thanks a lot.

---

### Post by earthpigg on 2009-12-21
> If you have /home/username/.supertux/config , please post the content of the file here so we can copy the file in our computer

almost as good: folks that have this problem please post yours. there may be some "True" that needs to be changed to a "False" or something silly like that.

```

cat ~/.supertux/config
```

---

### Post by a20365354 on 2009-12-21
Aha!I know how to solve the problem!! Go to your package manager and install BOTH supertux and supertus-stable It's works for me!! :):)  EDIT: Uh oh .... It only works for super tux development version... :( Sorry for that...I think I must test before post next time... :(

---

### Post by steigerjb on 2009-12-21
> **earthpigg said:**
> just out of curiosity... are there any config files in your ~?

if the program never started correctly, there shouldn't be.

see if there is a /home/username/.supertux or .super or .games/supertux or something like that folder that couldn't possibly be anything except supertux config files that should not exist yet.

if they are there, delete them.

deleted everything but config but it still crashes

---

### Post by steigerjb on 2009-12-21
> **a20365354 said:**
> Same problem here. :(
Please help...
If you have /home/username/.supertux/config , please post the content of the file here so we can copy the file in our computer,I think that can solve the problem.
Thanks a lot.

my supertux config file

```
(supertux-config
	;; the following options can be set to #t or #f:
	(fullscreen #f)
	(sound      #t)
	(music      #t)
	(show_fps   #f)

	;; either "opengl" or "sdl"
	(video      "sdl")

	;; joystick number (-1 means no joystick):
	(joystick   -1)
	(joystick-x   0)
	(joystick-y   1)
	(joystick-a   0)
	(joystick-b   1)
	(joystick-start  2)
	(joystick-deadzone  4096)
	(keyboard-jump  120)
	(keyboard-duck  274)
	(keyboard-left  276)
	(keyboard-right 275)
	(keyboard-fire  122)
)
```

---

### Post by slughappy1 on 2009-12-21
When things mess up like that I usually delete the config folder and then load the program again.

I would try ```
cp /home/username/.supertux /home/username/.supertux_backup
``` then ```
sudo rm -rf /home/username/.supertux
``` Then load the program and see if that helped. If not then you could move the old file back. ```
mv /home/username/.supertux_backup /home/username/.supertux
```

---

### Post by earthpigg on 2009-12-21
if slughappy1's suggestion doesn't work, give this a shot:

change all the joysticks stuff to -1 just for kicks.

```
;; joystick number (-1 means no joystick):
	(joystick   -1)
	(joystick-x   -1)
	(joystick-y   -1)
	(joystick-a   -1)
	(joystick-b   -1)
```

alternatively, does anyone have supertux installed on a 9.04 or earlier machine? we could try comparing that file on the two to see where something went awry.

---

### Post by running_rabbit07 on 2009-12-21
> **steigerjb said:**
> Why can't I play SuperTux anymore with Karmic Koala? It worked fine in Jaunty-

I'll launch it and then it'll immediately close. 

I wanna play it. I love that game!

I have had the same problem with my daughter's Karmic machine. I installed the dev version and it works great other than some graphics flickering from time to time. My daughter is addicted to the game. The dev version is the supertux in the Synaptic that doesn't have stable beside it.

---

### Post by mkvnmtr on 2009-12-21
I have had this problem with Supertux. It seems that every other release it does not work. This has happened since 6.06 on several machines. I have 9.10 mostly because it works and did not in 9.04. I never have figured out why or seen any updates that look like theychanged from one release to another.

---

### Post by steigerjb on 2009-12-21
> **earthpigg said:**
> if slughappy1's suggestion doesn't work, give this a shot:

change all the joysticks stuff to -1 just for kicks.

```
;; joystick number (-1 means no joystick):
	(joystick   -1)
	(joystick-x   -1)
	(joystick-y   -1)
	(joystick-a   -1)
	(joystick-b   -1)
```

alternatively, does anyone have supertux installed on a 9.04 or earlier machine? we could try comparing that file on the two to see where something went awry.

nope

---

### Post by Marvin666 on 2009-12-21
I'm making a new install of jaunty in a few days. I'll try installing supetux on it and post the config files on here.

---

### Post by steigerjb on 2009-12-22
> **Marvin666 said:**
> I'm making a new install of jaunty in a few days. I'll try installing supetux on it and post the config files on here.

k

---

### Post by gypsumwolf on 2009-12-24
When I first installed super tux it worked great, then I quit the program and tried it again and it gave me the similar error.

```
wolf@voyager:~$ supertux
Datadir: /usr/share/games/supertux
open /dev/sequencer or /dev/snd/seq: No such file or directory
Warning: No joysticks are available.
Segmentation fault
wolf@voyager:~$ 

```

Ps. Mine is a very fresh install. 9.10 Minimal.

---

### Post by thomz92 on 2009-12-24
i got a similar error message with a fairly recent install of ubuntu 9.10. it doesn't mention anything about a joystick though.

```
thomas@thomas-desktop:~$ supertux
Datadir: /usr/share/games/supertux
Warning: Unable to open the file "/home/thomas/.supertux/config" for read!!!
Segmentation fault
thomas@thomas-desktop:~$
```

---

### Post by mkvnmtr on 2009-12-25
I have never gotten Supertux to work on 9.04. This morning I used Ubuntu Tweek to enable the stable xorg repositories. I did the updates and then I thought of Supertux. I installed and for the first time it worked in 9.04. You might give it a try. I would make a note or any upgrades it makes so you can go back if you have other problems.

---

### Post by earthpigg on 2009-12-25
> Warning: Unable to open the file "/home/thomas/.supertux/config" for read!!!


open nautilus, navigate to the file, and see if its owner/group is thomas and that you have read/write/execture permissions

---

### Post by thomz92 on 2009-12-25
> open nautilus, navigate to the file, and see if its owner/group is thomas and that you have read/write/execture permissions

there is no folder called "config" in .supertux...

---

### Post by earthpigg on 2009-12-25
oh. then create the file. blank text file. maybe it will work, maybe not.

---

### Post by thomz92 on 2009-12-25
> oh. then create the file. blank text file. maybe it will work, maybe not.

doesn't say unable to open the file anymore but still gives a segmentation error.

---

### Post by sbassett on 2009-12-27
tried this in a terminal just for laughs:
supertux --opengl

and lo and behold, it works. Wish there was a way to globally change this (daughter uses guest account), will check into the global configs (if there are any).

---

### Post by thomz92 on 2009-12-28
> tried this in a terminal just for laughs:
supertux --opengl

and lo and behold, it works.

wow, it does work. whats up with that?? i guess its not too much trouble to change the command for the launcher, but still why does the command "supertux" give a segmentation error and not "supertux --opengl"?

---

### Post by steigerjb on 2009-12-28
> **sbassett said:**
> tried this in a terminal just for laughs:
supertux --opengl

and lo and behold, it works.

yep, that makes Supertux run for me now too!! I changed the launcher command so i don't need to use the terminal.

---

### Post by Chakra_ on 2009-12-29
supertux seems to work with this comand fine , but supertux 2 however not. 

Invalid button '0' in buttonmap
Invalid button '1' in buttonmap
Invalid axis '-2' in axismap
Invalid axis '-1' in axismap
Invalid axis '1' in axismap
Invalid axis '2' in axismap
Warning: tinygettext: expected 'msgid' keyword, got msgstr at line 358
Warning: tinygettext: expected 'msgid' keyword, got msgstr at line 358
Warning: Unknown option '--opengl'. Use --help to see a list of options

it has worked quite badly : showing warnings in the beginning and crashing randomly after death.

---

