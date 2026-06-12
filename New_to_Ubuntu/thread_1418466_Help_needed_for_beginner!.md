---
title: "Help needed for beginner!"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by georgep1993 on 2010-02-28
OKAY, just formatted my Win7 hdd and installed Ubuntu from boot ( i love it btw ;D) only concern is that ive had Ubuntu before and its asked for me to enable my graphics card, so this time i go onto hardware drivers and nothing there, whatsoever, so surely they are already installed? but it wont let me enable desktop effects. this is all ive tried, also with youtube, obviously i need to install java, so i go onto the app store. and all of the apps say theyre not compatible with my hardware or something? if anyone could help would be great, thanks!

---

### Post by themusicalduck on 2010-02-28
You need to enable and update your software sources I think.

Go to System > Administration > Software Sources and check all the boxes under "Downloadable from the Internet" except for Source Code.

Close the window and it should tell you to reload your software information. Click on reload and let it do its thing.

After that you should be able to install your drivers and other software.

By the way, youtube uses flash rather than Java! But you can install java/flash/media codecs if you install the Ubuntu Restricted Extras package (it's in the Software Centre)

---

### Post by jcitguy78 on 2010-02-28
what are the spec/type on your graphics card?

---

### Post by 2hot6ft2 on 2010-02-28
Open a terminal
Application > Accessories > Terminal
and run
```
sudo apt-get update
```
your password wont be displayed just type it in and hit enter
then run
```
sudo apt-get install ubuntu-restricted-extras
```
that will get you the stuff for java and multimedia (which you will have to accept the agreement use the tab and arrow keys to move to the correct answers)

Now go back to
System > Administration >, Hardware Drivers
and it should show a driver for your graphics card being available
Activate it to download and activate it.

After the reboot you should be able to activate special effects.

---

### Post by georgep1993 on 2010-02-28
ahh Thanks, yeah i went on it and theyre all ticks, and i closed it, and went through it all but update manager is running atm so it wont let me but ill check it out after! thanks :) 

and my graphics card is Nvidia Geforce 7500 i think, i know Nvidia Geforce.

---

### Post by georgep1993 on 2010-02-28
Would be great also if anyone knew how i could install Visual Basic on here. Im a computing student and thats what my college uses.

---

### Post by spiky001 on 2010-02-28
i googled this [http://shibuvarkala.blogspot.com/2009/06/gambas-visual-basic-for-linux-how-to.html](http://shibuvarkala.blogspot.com/2009/06/gambas-visual-basic-for-linux-how-to.html)

if not hear is the google page for you to look at

[http://www.google.co.uk/#hl=en&source=hp&q=visual+basics+ubuntu&btnG=Google+Search&meta=&aq=f&oq=visual+basics+ubuntu&fp=c6c9946001627c7b](http://www.google.co.uk/#hl=en&source=hp&q=visual+basics+ubuntu&btnG=Google+Search&meta=&aq=f&oq=visual+basics+ubuntu&fp=c6c9946001627c7b)

---

