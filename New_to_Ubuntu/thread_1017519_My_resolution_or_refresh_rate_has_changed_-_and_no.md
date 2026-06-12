---
title: "My resolution or refresh rate has changed - and now my screen wont work!"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by phantomjoker on 2008-12-21
Hi

I have been playing around with the appearance of my system to make it look like a Mac X OS. I followed the instructions here - 

[http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23]("http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23")

I got half way then stoped turned off the computer and turned it on again - so i know it wasn't the first half that caused the problem, it was when i did the following that i got the problem -

> Next, we are going to install globalmenu so as to display the menubar for each application. In your terminal,

```

cd Mac_files
wget http://gnome2-globalmenu.googlecode.com/files/gnome-globalmenu-0.4-svn964.tar.gz
tar zxvf gnome-globalmenu-0.4-svn964.tar.gz
cd globalmenu
sudo dpkg -i *.deb
```
If you have any errors when installing the package, try
```

sudo dpkg -i –force-overwrite *.deb
```
If you are having some installation problems with the gnome-globalmenu-applet, try

```
sudo apt-get install -f
```
Once finished, right click on the top panel and select ‘Add to panel‘. Scroll down the list and add ‘Global Menu Applet‘.



I only needed to do the first set of commands, as there seemed to be no error with the download and install, but when i went to see if the menu icon could be added - it was not there. So i tried to go to 'appearance' under 'preferances' and it would not open, so i restarted - the computer will not show on the monitor - on my TV it shows the message [not signal input] on the monitor it shows [out of range]!

I think my resolution and/or refresh rate has been changed - as i had the same message on my tv, but all i had to do then was plug in the moniter - change both resolution [to 1280 by 720 (i think)] and refresh rate [to 60Hz].

EDIT
I have found a screen that connects, but as the title emplies - i just get a mouse on a black background!
EDIT

What have I done?

cheers

---

### Post by phantomjoker on 2008-12-21
Ok, big leap forward - and huge step back! 

I have a screen that is working with the computer - but when it loads, i just get the mouse on a black background!

I can't click anything because there is nothing - and nothing happens if i right click either...

---

### Post by phantomjoker on 2008-12-21
Something else to add -

If i do CTRL ALT BACKSPACE the mouse disapears as though i was refreshing the gui, if i tap the combination fast it brings up a screen which reads


> Starting System tools Backends system-tools-backends
statrting anachironistic cram anacram
starting.......... goes on and on

Another thing to mention is the screen goes orange first (after a restart) like its starting up - then the theme kicks in (the Mac X os theme) and the orange turns to black and the mouse changes to the mac mouse.

Also when i do CTRL ALT BACKSPACE the mouse changes every time i do it- it switches between the standard mouse, the Mac Os mouse and the X - mouse!

WHATS GOING ON? Please help..

---

