---
title: "How do I make a script to change font sizes?"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by Boslow on 2010-08-19
Hi, i need some help please!

Iv been using ubuntu for a year or so and iv installed 10.04 on a friends computer. He is partially blind and has a 30" monitor for his PC. Moving from windows to Ubuntu has mostly increased the usability of the computer for him and is very impressed.

However, to be able to read he has to use a system font of 42px which even on a high resolution means that dialog boxes are missing the buttons. As I am continually adapting the computer id like to have a simple desktop shortcut that switches the Application font from 18px to 42px as i have to keep going backwards and forwards to see if the changes work at that res. 

Unfortunately I have no idea where to start for this.

the other only main problem is the size of the min/max/close buttons which need to be 4 times bigger. I cant seem to find a setting or anything on google for it, which is pretty frustrating as i have been able to fix everything else with google :P

Many Thanks!!
Boslow

---

### Post by SoFl W on 2010-08-19
System-> Preferences-> Appearance->  [Fonts tab]   Would that work for your friend?

*EDIT:*
  I am sorry, I re-read your question.  You want a simple way of switching between two sizes.  I think I found a link a while ago to do some desktop switching, I will see if I can find it again.

---

### Post by no2498 on 2010-08-19
? does setting the screen res lower help
that makes mine bigger
i also set the browser size fonts bigger

---

### Post by Vaphell on 2010-08-19
not that i have a solution to your problem, but have you tried to use that compiz plugin with different levels of zoom? I think it would greatly help in many situations. I enabled mine for kicks and configured it so win+1 is normal view, win+2 zoom, win+3 hardcore zoom, maybe 1/16 of desktop visible.

bumping dpi up is the best if we want to enlarge stuff globally, because it affects everything and it fonts are not blurry, unlike in the case of lower resolution. Also icons on desktop can be scaled up manually.

another useful trick to know is to alt-drag the windows. If your window gets too big and some parts of it go offscreen, you can simply move it so the desired part is shown again

ask some theme making guys, maybe it's possible to increase font size for buttons globally.



familiarize yourself with gconf-editor and especially with gconftool-2 - it can set any gnome variable from terminal
[http://ubuntu-tutorials.com/2008/01/10/gconftool-2-gconf-editor-from-the-shell/](http://ubuntu-tutorials.com/2008/01/10/gconftool-2-gconf-editor-from-the-shell/)

desktop > gnome > font_rendering > dpi looks promising, as do parameters under desktop > gnome > interface, some good stuff may be under apps > metacity too

---

### Post by fatality_uk on 2010-08-19
[https://help.ubuntu.com/community/Accessibility](https://help.ubuntu.com/community/Accessibility)

Look here for lots of help/ideas to help make you friend's Ubuntu experience a lot better. Hope it helps.

---

### Post by Boslow on 2010-08-22
> **Vaphell said:**
> another useful trick to know is to alt-drag the windows. If your window gets too big and some parts of it go offscreen, you can simply move it so the desired part is shown again

Brilliant!! Thanks mate, just what I was looking for, saves the hassle of even changing font size!!

Mostly the system is set up well for him with the fonts this size so he has a reference to what he's looking at/for. He uses the compiz zoom  function a lot when hes found the part of the page hes looking for, but its easy to get lost, which is why he still needs big fonts. 

Lowering the res does increase font size, but also the amount of whitespace between buttons (which is why I ditched Winblows and installed Ubuntu:P). He now has about twice the usable area while web browsing, which is alot when you can only fit 3 lines of text on the screen.

I'll have a look at gconf editing as well.

On a side note, Iv managed to increase the width of the scrollbars using a script found on here, is there one to increase the size of the arrows that appear in the system and application menus to scroll up and down??

Many thanks for all your help guys, Ubuntu has another happy user!!!
Boslow


Oh, and Orca is useless! we have 3 10.04 systems and none render properly under magnification! and now that its uninstalled, the narrator still speaks all of the system settings on boot, and does it corruptedly...

---

### Post by SoFl W on 2010-08-23
I am sorry I took so long to respond and I think you might have the answer you are looking for but check out the "display --help" command, there is a font option.

---

### Post by LewRockwellFAN on 2011-04-04
> **Vaphell said:**
> not that i have a solution to your problem . . .

familiarize yourself with gconf-editor and especially with gconftool-2 - it can set any gnome variable from terminal . . .
[http://ubuntu-tutorials.com/2008/01/10/gconftool-2-gconf-editor-from-the-shell/](http://ubuntu-tutorials.com/2008/01/10/gconftool-2-gconf-editor-from-the-shell/) . . .

 
I know this is old and marked solved but someone might read it searching as I was and since I almost missed it maybe I should point out that Vaphell is too modest - that little bit in the middle of his post is EXACTLY what the OP was asking for, a script to change all fonts changeable through System/Preferences/Appearance/Fonts_tab all at once to any preset scheme of font sizes you want. Cool!!!!! This will make life for the nearsighted sooo much easier. I made one script to change them all to 10, which I think was the installation default, and another to change them all to 20. I made launchers for each script, made icons for the launchers with Gimp and put the launchers on the top panel. Now I just have to click once on the big white "10" to lower my font sizes to the installation defaults to see the pesky buttons or whatever and click once on the big white "20" to restore sane font sizes. Maybe later I'll make a whole range of them and put them in a drawer. Another approach would be to use some sort of graphical pop up to set an environment variable from user input and have the script set the text sizes all to that if you wanted more flexibility. For that matter that sort of script could be simpley another choice in the drawer if you wanted it. 

Many thanks to Vaphell for the link and Christer Edwards for the script. Little things like this make a big difference for some of us.

And if OP is still around, yes, I think most everyone who has used orca agrees it's pretty useless. Try Kmag for a magnifier. And if you want decent text to speech there are excellent non-free aps, starting with Cepstral. Some Windows aps running under Wine are even better.  Several of them work great and they mostly have free trials. I wouldn't buy one unless you can get the trial to run for a few days. For a free locally installed ap the best I've heard is the java ap Mary. There are good free web based aps though like ispeech.org.

---

