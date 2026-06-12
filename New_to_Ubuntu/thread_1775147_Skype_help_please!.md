---
title: "Skype /help/ please!"
date: 2011-06-04
forum: New to Ubuntu
---

### Post by dolcefantasma on 2011-06-04
Hi guys, 
I need ur help urgently. My skype is not running currently on my Ubuntu 32. 
I had problems with pulse audio, finally have removed it. Skype was OK, then once it stopped to run . whenever I press skype button it begins to work, straight after showing me signing-in window it disappear.... 
I tried to do find some helpful treat but nothing helps... 
HELP MEE!!!!!!!!!!!!!!!

---

### Post by Zorael on 2011-06-04
Try renaming the **.Skype** folder in your home to make Skype recreate its default settings. The folder is hidden (since it begins with a dot), so you'll have to enable display of hidden files in your file manager.

If it works you can manually copy back your history.

---

### Post by cycling.tux on 2011-06-04
About one or two weeks ago there was a problem with skype on linux and windows. Maybe you could remove and install (the latest version of) skype again? Download the version on [www.skype.com](www.skype.com)

---

### Post by beew on 2011-06-04
> **cycling.tux said:**
> About one or two weeks ago there was a problem with skype on linux and windows. Maybe you could remove and install (the latest version of) skype again? Download the version on [www.skype.com]("http://www.skype.com")


Don't need to reinstall.
[http://www.omgubuntu.co.uk/2011/05/skype-crashed-today-heres-a-fix/](http://www.omgubuntu.co.uk/2011/05/skype-crashed-today-heres-a-fix/)


Also, the latest version of Skype is in the Canonical's Partners repo. Why would you want to download from Skype?

---

### Post by dolcefantasma on 2011-06-05
> **Zorael said:**
> Try renaming the **.Skype** folder in your home to make Skype recreate its default settings. The folder is hidden (since it begins with a dot), so you'll have to enable display of hidden files in your file manager.

If it works you can manually copy back your history.

](*,)](*,)](*,) 

At first tell me please how to watch hidden folders. Have no idea of how to show them on my home .... 
I am so beginner.. you can never imagine ..
:lolflag:

---

### Post by dolcefantasma on 2011-06-05
> **beew said:**
> Don't need to reinstall.
[http://www.omgubuntu.co.uk/2011/05/skype-crashed-today-heres-a-fix/](http://www.omgubuntu.co.uk/2011/05/skype-crashed-today-heres-a-fix/)


Also, the latest version of Skype is in the Canonical's Partners repo. Why would you want to download from Skype?

I've tried to remove and install it 3 times, every time I have download it from different sources it doesn't help! I even download separately libraries and Skype Static, helpless.
The only thing my brain tells me could do the deleting the whole file with its all history and settings and then only install the brand new one.. but unfortunately I don't now how to do that and I'm not sure that will gonna help.
Any suggestions?

---

### Post by gandaran on 2011-06-05
> **dolcefantasma said:**
> ](*,)](*,)](*,) 

At first tell me please how to watch hidden folders. Have no idea of how to show them on my home .... 
I am so beginner.. you can never imagine ..
:lolflag:
go to the file browser menu bar » view » show hidden files

---

### Post by Normand on 2011-06-11
I have exactly the same problem as original poster.
Skype seems to open then within a few seconds it aborts.

Typing skype in a terminal make the same happen and produces:

> /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:4620): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:4620): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:4620): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:4620): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:4620): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:4620): Gtk-WARNING **: Loading IM context type 'ibus' failed
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:4620): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:4620): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:4620): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:4620): Gtk-WARNING **: Loading IM context type 'ibus' failed
Aborted


Maybe someone can make sense of this.

I'm running Natty, Classic desktop on a 64bit machine.

Thanks fro any ideas

---

### Post by Zorael on 2011-06-11
> **Normand said:**
> I have exactly the same problem as original poster.
Skype seems to open then within a few seconds it aborts.
Have you tried the same procedure, renaming the **.Skype** folder? There was a server change recently that introduced a bug causing Skype to crash on all platforms, and deleting/renaming a file in the settings directory (**shared.xml**? I forget) fixes it. Renaming the whole folder should do the trick.

Also make sure that you have the **[ia32-libs](apt://ia32-libs)** package installed. It shouldn't be possible to remove it without also removing Skype.

---

### Post by Normand on 2011-06-11
Thanks Zorael

I stupidly got tangled renaming the .Skype file as .Skype
But now I vave .Skypebeans and launched Skype, it asked for my details and is running fine with a new .Skype folder.

I have copied the chatsynch folder from my old personal folder in .Skypebeans to same in the new .... hope that should recover history when I next launch ...

thanks again

---

### Post by VOT Productions on 2011-06-11
> **gandaran said:**
> go to the file browser menu bar » view » show hidden files

CTRL+H is easier.

---

### Post by dolcefantasma on 2011-07-06
GOD!!!!! I can't stand it any more. I have problems with skype sound it's almost 6 months, right after updating my system.
So I read that pulseaudio has some problems so I installed alsa , then it works, after I have no idea how it repeated many times, i tried everything.
Now i have the same problem again, I tried to change sound options in Skype options, tryed to open Ubuntu's sound options and change them but it doesn't opening as pulse audio was deleted from the computer. 
Now every time to speak with skype I need to restart and enter with my old windows version so that's a big  headache to do that 3 times a day . 
Please give me a solution. I am absolutely new with Ubuntu so that's make me angry that I can't feel free and try new things.. 
Please please please .. help meeeeeeeeeeeee.:confused:

---

### Post by dolcefantasma on 2011-07-06
Thank you!!!!!!!! it helped!!!!!!!!!!!!!!! You are the best ppl :P

---

### Post by candtalan on 2011-07-06
I do not use skype much, but am using it just lately. I guess you are aware that it is proprietary code (secret)) - this means that there is no real chance that any experts can assess what might be going on?

It would be useful to state which Ubuntu version you are using. Also which camera too?

For me, pulseaudio works better than alsa ever did. If you asked which most people here use, you might find not many have gone to the trouble of also installing alsa.

What exactly is the trouble you are having with sound? Skype is a self learning app  to some extent, afaik.

In 10.04.2 I just need to set up audio. I have an external camera, with integral microphone. The camera is a usb device. Video gets recognised easily.
(skype options, video device, test)

For Audio, I am aware the camera mic is also in the usb connection. I am aware of audio settings: 
top panel loudspeaker icon:
sound preferences [select device] [select input] and use lots of skype test calls, to find out what my machine does.
Also within skype options
There is a 
open pulseaudio volume control button.

I make careful use of both controls, and when I am using a headset - (phones and mic) - plugged into the back of the machine I set the input to mic1. Mic2 is for the front panel sockets, and I also disable the camera usb audio facility for this.
hth

---

### Post by Iowan on 2011-07-06
Threads merged to keep all the info in one place.

---

### Post by dolcefantasma on 2011-07-07
GOD!!!!! I can't stand it any more. I have problems with skype sound it's almost 6 months, right after updating my system.
So I read that pulseaudio has some problems so I installed alsa , then it works, after I have no idea how it repeated many times, i tried everything.
Now i have the same problem again, I tried to change sound options in Skype options, tryed to open Ubuntu's sound options and change them but it doesn't opening as pulse audio was deleted from the computer. 
Now every time to speak with skype I need to restart and enter with my old windows version so that's a big headache to do that 3 times a day . 
Please give me a solution. I am absolutely new with Ubuntu so that's make me angry that I can't feel free and try new things.. 
Please please please .. help meeeeeeeeeeeee.

---

### Post by overdrank on 2011-07-07
Please do not create multiple threads on the same issue. Threads merged :)

---

### Post by dolcefantasma on 2011-07-12
hello???????? anyone ?? who have an idea about this ****? Why it is so hard to use ubuntu!!!!! Ppl I don't have skype for 2 months, help me please !

---

