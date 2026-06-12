---
title: "Windows Explorer"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by frigate13 on 2010-06-05
Quick Question.  I have an mp3 player that I want to add some music to, and when I was using Windows I used Windows Explorer.  What is the equivalent of that on Ubuntu, and how do I access it.

Thanks.

---

### Post by Morbius1 on 2010-06-05
Just to be sure we're talking about the same thing, Windows Explorer is Windows' file manager. In Ubuntu it's Nautilus.

---

### Post by lordppm on 2010-06-05
On the panel, Places => Computer or On the keyboard,Control+`

---

### Post by roger_1960 on 2010-06-05
Hi
Go to places>computer  This open the file browser (nautilus) which is the equivalent of Explorer.  Select "tree" from the dropdown at top left and it should look reasonably familiar.

---

### Post by ashwinhgtx on 2010-06-05
When you connect your mp3 player to your computer, a box will pop up asking you what you want to do with it. 

Select 'Open Folder' from the drop down list. You will be presented with an interface similar to Windows Explorer.

Drag and drop your songs to the folder in the mp3 player like you used to do in Windows Explorer.

When you are done, close the window and go to the desktop. There you will see an icon for your mp3 player. Right click it and select 'Safely Remove Drive'.

This will eject the mp3 player for you. 

Or you could use Rhythmbox, which is the default musci player in Ubuntu to copy the music. :)

Enjoy Ubuntu.

---

### Post by pizza-is-good on 2010-06-05
Yep, nautilus will do the job.

you can go to Places >> Computer to see all devices attached to your computer.

or you can type ```
nautilus &
``` in a terminal. (the & is to separate the process from the terminal window so you can close the terminal.)

or you can type ```
ls /media/
``` on your terminal to see which devices are connected to the computer, and then do ```
cd /media/"your device name"
``` and then do ```
ls -a
``` to see what's in the device. And I won't go on preaching about the terminal, because I caught myself doing so and then I realized what you asked for was a windows explorer, not how to copy files to your mp3 player... :lolflag: if you want me to go on I can, but I know that its easier to just use the GUI, at least for me, unless I want to do complicated stuff..

Happy ubunting,

~pizza

---

### Post by John Bean on 2010-06-05
Opening a terminal inside a pointy-clicky graphics environment just to launch Nautilus is a bit perverse considering that clicking on pretty much anything in "Places" does the same thing...

---

### Post by pizza-is-good on 2010-06-05
> **John Bean said:**
> Opening a terminal inside a pointy-clicky graphics environment just to launch Nautilus is a bit perverse considering that clicking on pretty much anything in "Places" does the same thing...

It is... Oh welll.

I open a terminal (well, I don't anymore, I have a custom icon for it) to shutdown the computer. sudo shutdown -P now thing. It asks me for password of course, but I'm faster at typing that than actually going to the menu >> shutdown >> shutdown (or OK, I'm not sure about the confirmation box). It takes less clicks :P

But then again, doing anything in the terminal makes people think that you are super smart, so anything to impress (or make people afraid of you...)

---

### Post by John Bean on 2010-06-05
> **pizza-is-good said:**
> But then again, doing anything in the terminal makes people think that you are super smart, so anything to impress (or make people afraid of you...)

Heh, honest anyway :-)

I'm long past any need to do things just to impress others, but I still remember my younger days... at least I think I do.

Edit: PS: I have a terminal launcher on a GNOME panel, and a shortcut to cmd.exe on the launch bar of my Windows XP VM, that's how much I use command lines. But I don't use them as gratuitously as you did in your examples ;-)

---

