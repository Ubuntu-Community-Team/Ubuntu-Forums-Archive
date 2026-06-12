---
title: "few queastions"
date: 2011-04-13
forum: New to Ubuntu
---

### Post by Avidanborisov on 2011-04-13
Hey there, I got a few questions so:

No video in skype. There is audio but no video, but for example video is working in cheese webcam. My webcam is Logitech S7500.

About Empathy - 
1. When Someone is sending me a message, I only get a notification, but I need to manually launch Empathy and then select the contact and start a chat, is there any way to do this automatically?
2. Is there any way to NOT show the offline people?
3. Video and voice chat just don't work...

More general

1. Is there any way to configure an application to be always in a certain workspace? for example I have a workspace for instant messaging with skype and empathy. Is there any way to configure all the windows from these application to be in that workspace?
2. I want to be able to drag a windows to a different workspace by dragging it with the left mouse, how to configure it, maybe in compiz?
2. Can I set a hotkey for showing all the workspaces, instead of clicking on the "Workspace Switcher" on the Launcher?
3. Is there any way to show in the upper panel what workspace I am currently on? Maybe a number?

Thanks :)

---

### Post by sanderd17 on 2011-04-13
> **Avidanborisov said:**
> Hey there, I got a few questions so:

No video in skype. There is audio but no video, but for example video is working in cheese webcam. My webcam is Logitech S7500.

if you have 64 bit, try the command
```

LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so /usr/bin/skype

```

if you have 32 bit, try
```

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype

```

> 
About Empathy - 
1. When Someone is sending me a message, I only get a notification, but I need to manually launch Empathy and then select the contact and start a chat, is there any way to do this automatically?

maube try gnome 3, it's a lot better there (don't know about unity)
> 
2. Is there any way to NOT show the offline people?

CTRL+H
> 
3. Video and voice chat just don't work...

More general

1. Is there any way to configure an application to be always in a certain workspace? for example I have a workspace for instant messaging with skype and empathy. Is there any way to configure all the windows from these application to be in that workspace?

Not that I know, maybe you can find something in the compiz settings
> 
2. I want to be able to drag a windows to a different workspace by dragging it with the left mouse, how to configure it, maybe in compiz?

if you use the cube, it's the default
> 
2. Can I set a hotkey for showing all the workspaces, instead of clicking on the "Workspace Switcher" on the Launcher?

CTRL+ALT+DOWN? If you use the cube
> 
3. Is there any way to show in the upper panel what workspace I am currently on? Maybe a number?

There used to be an applet in the gnome panels. I think (by reading your post) that you use unity, so you don't have gnome panels.
> 
Thanks :)

No prob, I hope I solved some of your questions.

---

### Post by madjr on 2011-04-13
> 3. Is there any way to show in the upper panel what workspace I am currently on? Maybe a number? 

[http://www.omgubuntu.co.uk/2011/01/the-omg-guide-to-must-have-indicator-applets/](http://www.omgubuntu.co.uk/2011/01/the-omg-guide-to-must-have-indicator-applets/)

---

### Post by rosencrantz on 2011-04-13
> **Avidanborisov said:**
> 
1. Is there any way to configure an application to be always in a certain workspace? for example I have a workspace for instant messaging with skype and empathy. Is there any way to configure all the windows from these application to be in that workspace?

It's not exactly what you are looking for and irrelevant for confirmed Gnome users, but it's possible with KDE window/application settings. Also, have a look at KDE's Desktop Activity feature.  
[http://maketecheasier.com/use-kde-plasma-activities/2010/09/01I](http://maketecheasier.com/use-kde-plasma-activities/2010/09/01I) 
Apart from that, look into tabbing and window rules (should be featured in both Compiz and Plasma/KDE)

Cheers,
rosencrantz

---

### Post by Avidanborisov on 2011-04-13
> **sanderd17 said:**
> if you have 64 bit, try the command
```

LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so /usr/bin/skype

```

if you have 32 bit, try
```

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype

```


maube try gnome 3, it's a lot better there (don't know about unity)

CTRL+H

Not that I know, maybe you can find something in the compiz settings

if you use the cube, it's the default

CTRL+ALT+DOWN? If you use the cube

There used to be an applet in the gnome panels. I think (by reading your post) that you use unity, so you don't have gnome panels.


No prob, I hope I solved some of your questions.

thanks for of the answers! any ideas how to make that option for skype default?

> **madjr said:**
> [http://www.omgubuntu.co.uk/2011/01/the-omg-guide-to-must-have-indicator-applets/](http://www.omgubuntu.co.uk/2011/01/the-omg-guide-to-must-have-indicator-applets/)

Thanks! although it is not really compatible with natty, it displays the workspace number, just what I needed!

> **rosencrantz said:**
> It's not exactly what you are looking for and irrelevant for confirmed Gnome users, but it's possible with KDE window/application settings. Also, have a look at KDE's Desktop Activity feature.  
[http://maketecheasier.com/use-kde-plasma-activities/2010/09/01I](http://maketecheasier.com/use-kde-plasma-activities/2010/09/01I) 
Apart from that, look into tabbing and window rules (should be featured in both Compiz and Plasma/KDE)

Cheers,
rosencrantz

The link is broken..

And if someone could answer the other questions. ill be thrilled!
Also another question - How can I launch the system monitor with Ctrl+Alt+Del?

---

### Post by rosencrantz on 2011-04-13
Sorry, typo sneaked in...
[http://maketecheasier.com/use-kde-plasma-activities/2010/09/01](http://maketecheasier.com/use-kde-plasma-activities/2010/09/01)

---

### Post by sanderd17 on 2011-04-14
> **Avidanborisov said:**
> thanks for of the answers! any ideas how to make that option for skype default?

Dirty method: you will probably have to redo this when skype updates. In the terminal do the following:

```

sudo mv /usr/bin/skype /usr/bin/skype.original
sudo gedit /usr/bin/skype

```
then in gedit type
```

#! /bin/bash
LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so /usr/bin/skype.original

```
for 64-bit
OR
```

#! /bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype.original

```
for 32-bit

save the file and close gedit, then in the terminal do
```

sudo chmod 755 /usr/bin/skype

```

Now you can try if it works.

> 
And if someone could answer the other questions. ill be thrilled!
Also another question - How can I launch the system monitor with Ctrl+Alt+Del?

You should have a "hotkeys" program, I don't know where it is under unity or what the command is to call it. It just appears when I search it with the gnome-shell search. There you can add a custom command to a custom hotkey. The command you need is 
```

gnome-system-monitor

```

---

