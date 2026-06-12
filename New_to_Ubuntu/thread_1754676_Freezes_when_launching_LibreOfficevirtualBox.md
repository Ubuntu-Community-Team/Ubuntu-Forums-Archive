---
title: "Freezes when launching LibreOffice/virtualBox?"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by OneWingedPegasus on 2011-05-10
Hello, I'm a total nub when it comes to Linux stuff, recently I got the urge to try Ubuntu.
After 3 days of configuring stuff and mofying it to my liking, pretty much in OS heaven, Ubuntu started freezing; I first noticed it when launching libreOffice Writer, the splash screen comes up and then the whole desktop freezes, I can only move the mouse around. it also freezes randomly and when launching virtualBox, I haven't tested other than that. what did I do wrong :confused:

I've only installed a bunch of themes, conpiz stuff, gimp, mediaplayers, messengers and the cairo dock. I use Ubuntu classic.
I also have problems with my wacom tablets but that's for another thread, I guess.

I would appreciate any help. thanks. :KS

---

### Post by wildmanne39 on 2011-05-11
> **OneWingedPegasus said:**
> Hello, I'm a total nub when it comes to Linux stuff, recently I got the urge to try Ubuntu.
After 3 days of configuring stuff and mofying it to my liking, pretty much in OS heaven, Ubuntu started freezing; I first noticed it when launching libreOffice Writer, the splash screen comes up and then the whole desktop freezes, I can only move the mouse around. it also freezes randomly and when launching virtualBox, I haven't tested other than that. what did I do wrong :confused:

I've only installed a bunch of themes, conpiz stuff, gimp, mediaplayers, messengers and the cairo dock. I use Ubuntu classic.
I also have problems with my wacom tablets but that's for another thread, I guess.

I would appreciate any help. thanks. :KS

Hi, are you using natty? compiz can mess up natty. Also what video card do you have? This information will help us help you.:)

---

### Post by OneWingedPegasus on 2011-05-11
Oh hi, I was just about to hit the hay ^^ I have a xfx Radeon hd 4850. let ubuntu install the drivers and everything.
The compiz config panel was one of the first things I installed and didn't have a problem till much later.

---

### Post by OneWingedPegasus on 2011-05-13
Nobody want to help this gal out? I still have this problem :( I don't want to throw Ubuntu away.

---

### Post by astex on 2011-05-13
If any of your virtual machines in VirtualBox is allocated to much ram, this can lead to poor performance, and possibly the error you describe.  Which settings have you tweaked in CompizConfig?

---

### Post by astex on 2011-05-13
Also are you using the newest Ubuntu installation (11.04 natty narwhal), the previous installation (10.10), or the LTS installation (10.04)?  These each behave VERY differently when interacting with compiz.

---

### Post by OneWingedPegasus on 2011-05-13
> **astex said:**
> If any of your virtual machines in VirtualBox is allocated to much ram, this can lead to poor performance, and possibly the error you describe.  Which settings have you tweaked in CompizConfig?

I'm not using VirtualBox at all, Ubuntu freezes as soon as I launch the program doesn't even go into the window. also, I have 4gb of ram.

I've enabled the cube and the rotation, also tweaked some genie effects.

I'm using 11.04 on Ubuntu classic. updated through the terminal and all.

---

### Post by chrisod on 2011-05-13
Disable Compiz and see how it behaves. If it keeps crashing then we know Compiz is not the problem. It it stops Compiz you just solved your problem.

---

### Post by wildmanne39 on 2011-05-13
> **OneWingedPegasus said:**
> I'm not using VirtualBox at all, Ubuntu freezes as soon as I launch the program doesn't even go into the window. also, I have 4gb of ram.

I've enabled the cube and the rotation, also tweaked some genie effects.

I'm using 11.04 on Ubuntu classic. updated through the terminal and all.

I had the same problem, if you will run unity --reset in a terminal and let it run a couple of minutes and dont worry about the errors it will fix unity after a couple of minutes reboot and everything should be fine.The cube does not work in unity with out some major tweaking.

---

### Post by OneWingedPegasus on 2011-05-14
@chrisod
I don't know how to disable compiz completely. but I disabled the cube and still crashed.

@wildmanne39
I ran that command and it didn't finish executing it, it ran for about an hour till Ubuntu froze again, and I wasn't doing anything but dragging a window.

I'm going to try executing it again. :oops:

---

### Post by wildmanne39 on 2011-05-14
> **OneWingedPegasus said:**
> @chrisod
I don't know how to disable compiz completely. but I disabled the cube and still crashed.

@wildmanne39
I ran that command and it didn't finish executing it, it ran for about an hour till Ubuntu froze again, and I wasn't doing anything but dragging a window.

I'm going to try executing it again. :oops:

Thats ok,if it doesnt finish that is how it does it, if you reboot after a few minutes everything should be back to normal, you may have to go into compiz and reactivate the unity plug in after you reboot, that I do not remember for sure.:)

---

### Post by OneWingedPegasus on 2011-05-14
> **wildmanne39 said:**
> Thats ok,if it doesnt finish that is how it does it, if you reboot after a few minutes everything should be back to normal, you may have to go into compiz and reactivate the unity plug in after you reboot, that I do not remember for sure.:)

Okay so I'm in Unity reseted to default and everything seems to be working right :KS Writer no longer crashes at launch and neither does virtualBox.
I didn't like Unity at first but its starting to grow on me. (especially since it doesn't crash)


Thank you very much for your help guys!

---

### Post by wildmanne39 on 2011-05-15
> **OneWingedPegasus said:**
> Okay so I'm in Unity reseted to default and everything seems to be working right :KS Writer no longer crashes at launch and neither does virtualBox.
I didn't like Unity at first but its starting to grow on me. (especially since it doesn't crash)


Thank you very much for your help guys!

Hi, I am glad to hear it. You can get compiz working if you log out and go to the bottom of the screen and click on ubuntu classic,I have not tried it but I am told it works nicely. I have not tried it because I was told that the next release will not have that option so I figured why get use to it.I really do miss the cube and other effects that I have been using for years. Please go to the top of the page and click on forum tools and mark this thread solved. Thank you very much happy ubuntuing.):P

---

### Post by Hedgehog1 on 2011-05-15
To reset unity so it stops crashing:

Please do a **<ctrl> + <alt> + t** to get the terminal.

From the terminal, please do this to reset your Unity to a functional state (factory defaults):

```
unity --reset
```

There will be some error messages - ignore them please.

Logout **<ctrl> + <alt> + <Delete>** and reboot...

***The Hedge***

:KS

p.s. You can run Natty/11.04 and still use the 'Classic’ UI for Cubes and Wobbly Windows: [**_Natty Info: Your UI options_**]("http://ubuntuforums.org/showthread.php?t=1741293")

---

### Post by audeojude on 2011-05-15
I was having x crash when running virtualbox, calibre and several other apps.. resetting unity fixed this for me... it has been a months long ordeal with both maverick and natty... :) glad to finally seem to have a solution.

---

