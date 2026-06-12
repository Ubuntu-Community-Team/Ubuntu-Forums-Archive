---
title: "[SOLVED] Running an Executable File?"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by beastrace91 on 2008-12-23
So I just installed the MMO Regnum ([www.regnumonline.com](www.regnumonline.com)) and install installed fine how ever I am slightly lost as how to load the game... it did not auto add to my games menu and when I browse my way to where it installed I find a file called "game" that is marked as type "executable" how ever clicking the file yields nothing... I have also tried running chmod +x game in terminal followed by ./game but that does not work either... How do I make this work?

~Jeff

---

### Post by antmenj on 2008-12-23
What is the full file name game.exe game.deb or what.  I just went to that site (with .fr added) and the first file I found was an exe file for windows.

---

### Post by nhasian on 2008-12-23
they have a 32 and 64 bit .bin installer file.  i was gonna download it to try to install the game myself but it was gonna take an hour to download so I gave up on it hehe

---

### Post by jasonralston on 2008-12-23
You can't run .exe on Ubuntu linux. Please download the file as a ".tar.gz" or a ".deb" if you download the .deb you can install it by typing dpkg "[filename].deb"

---

### Post by beastrace91 on 2008-12-23
The installer was a .bin (which worked fine running with chmod +x <filename>.bin and then ./<filename>.bin) how ever the "game" file does not have a file type listed (at least not that I see) when I run ls in terminal it displays game in green (if that helps at all) and when viewing it in the window manager it's file type says "executable" like I said before... I am confused as to why it won't just load for me :( I feel very stupid atm...

~Jeff

---

### Post by beastrace91 on 2008-12-23
> **jasonralston said:**
> You can't run .exe on Ubuntu linux.\ I may be stupid but I am not quiet THIS stupid... check my above post please.

~Jeff

---

### Post by jrusso2 on 2008-12-23
> **beastrace91 said:**
> The installer was a .bin (which worked fine running with chmod +x <filename>.bin and then ./<filename>.bin) how ever the "game" file does not have a file type listed (at least not that I see) when I run ls in terminal it displays game in green (if that helps at all) and when viewing it in the window manager it's file type says "executable" like I said before... I am confused as to why it won't just load for me :( I feel very stupid atm...

~Jeff

What you did is the correct way to run a .bin file on Linux.  Are you starting the game from inside the directory in which you have the .bin file?  Because to run it ./ you must be in that directory.

Also try using sudo ./filename.bin because it might be the installer has to be run with root privlidges if it installs into /opt or somewhere else requiring rights.

---

### Post by beastrace91 on 2008-12-23
I reinstalled the game with root privileges and still nothing... is someone wouldn't mind downloading and seeing what I am talking about I would be very grateful... also going to go over to their forums now and see if they have a support or linux section.

~Jeff

---

### Post by RomeReactor on 2008-12-23
Hi. Did the installer ask you for a location where to dump all the files? I have Regnum installed, but it's been a while since I downloaded the installer. There should be a file called **rolauncher**; you can start the game by running it like this:
```
sh -c "cd /PATH/TO/FILE && ./rolauncher"
```
where "/PATH/TO/FILE" is the actual location of "rolauncher"; in my case:

```
sh -c "cd /home/romereactor/RegnumOnline && ./rolauncher"
```

The Regnum site does have a [Linux support section]("http://www.regnumonline.com.ar/forum/forumdisplay.php?f=15").

---

### Post by beastrace91 on 2008-12-23
Thank you! Running the rolelauncher is what I need to load up the game... odd that they would call the file that starts the game that and not "game" lol

~Jeff

---

