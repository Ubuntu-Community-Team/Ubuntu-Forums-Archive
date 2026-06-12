---
title: "PlayOnLinux"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by brianfantastic on 2009-02-13
Hey guys. Well i recently made the switch to ubuntu part time(dual boot) to see what all the fuss is about and i'm impressed. 

Apart from a little problem with installing gfx drivers its been plain sailing. I have however encountered my first glitch.

Ive searched through the forums for an answer but i haven't found one that specifically suits my cause. 

Okay,

Ive got steam and counterstrike source all set up and working with playonlinux. No loading problems or anything like that. But when i run a video stress test in CSS, the max FPS i get is 25.5

Now this is frankly a problem for me because CSS is stable in the menus but causes game crash's when i join servers.

I have an ATI HD 4670 And an Intel Dual Core 2GHz processor over-clocked at 2.55GHz and 2 gig of ram.

I wouldn't mind if i averaged 60FPS or something because that would make the game playable, and in *shudders* windows, i'd average +300FPS. 

So how come i cant get above the 25 mark in ubuntu 8.04?

Im looking to make the switch full time but im afraid, like so many other people, its just not on the cards if i cant get my games running how i need them to.

All help appreciated.

EDIT:
When i go to SYSTMEM>ADMINISTRATION>HARDWARE DRIVERS, should the "ati accelorated graphicsdriver" box be cheked? in the status colum it says "enabled" Screenshot shortly.

[IMG]http://i15.photobucket.com/albums/a356/shayn1986/hardwaredrivers.png[/IMG]

---

### Post by HavocXphere on 2009-02-13
What screen resolution are you running at?

The ati driver is enabled...if it wasn't then you wouldn't even hit 25fps.

[QUOTE=brianfantastic]So how come i cant get above the 25 mark in ubuntu 8.04?[/QUOTE]
The main reasons why gaming on linux isn't on par with windows are:
[LIST=1]
[*]Games mostly output using DirectX instructions. Under linux, these first have to be converted to OpenGL commands before they can hit the gfx card. This means you've got an extra step/translation in between. It also means that some of the optimisations built into the games get lost because DX and OGL don't do everything the same way.
[*]The linux gfx drivers aren't on par with the windows equivalent. Most gamers are on MS boxes, so thats where ati/nvidia focus.
[*]The games weren't written for the a linux environment. Its a tribute to the linux devs that the games even start.=D>
[/LIST]

Also note, that the "stress test" tend to include all the latest effects and try to max out the hardware. Chances are, that the latest shader effects aren't even implemented on OGL, so they have to be improvised in an inefficient way.

Your gear should be able to run the game itself though...Are you using the same resolution & settings as on MS? Chances are, that you'll have to lower the quality to hit a reasonable fps. There are also some xorg.conf tweaks to improve performance...but I think they are mainly for nvidia gear.

I'd suggest "solving" the problem like I did: Do everything on linux, but dual-boot for games. Not exactly a die-hard linux attitude...but it works.:-$

btw, you might want to edit the name out of the screenshot.:lolflag:

---

### Post by jou770d on 2009-02-13
Just a small info that might help you, PlayOnLinux is basically a frontend for Wine. Which means you could check the game's compatibility with Wine in order to know how it will run.
e.g:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731)
There are some posts there about improving FPS. You might want to check them out.

---

### Post by sydbat on 2009-02-13
Do you have Desktop Effects enabled (System > Appearance > Visual Effects)?

If so, this *could* affect your FPS because Compiz is still using graphics resources while you are trying to play your games. Disabling Desktop Effects should solve this.

Let us know.

---

### Post by brianfantastic on 2009-02-13
Ahh i see. I didnt know that it converts to openGL.

I do have desktop effects enabled, and i think ill take your advice and keep with the dual boot option. I like linux, but realistically based on what ive read and what people seem to be saying im never going to be able to game on it in the same way as i will be able to with MS.

I think ill keep trying with linux until windows 7 gets released later this year though.

Thanks for the advice!

---

