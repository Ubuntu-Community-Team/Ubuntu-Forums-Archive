---
title: "Blank Screen on boot"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by Ratscallion on 2009-07-23
When I boot into Ubuntu (9.04, either non-recovery kernel) I get the normal usplash screen which loads fine, but then I simply get nothing. A blank screen.
I'm not sure why this is happening, help?
I've an HP G7094 laptop with 9.04 installed via Wubi in Vista.

---

### Post by abbec on 2009-07-23
I described the same behaviour in this thread: [http://ubuntuforums.org/showthread.php?t=1178990]("http://ubuntuforums.org/showthread.php?t=1178990") but did not get any response. I will follow this thread closely... :D

---

### Post by keplerspeed on 2009-07-23
Can you drop to a virtual console? when you get the blank screen press ctrl-alt-f1 and try to log in there. From there we can see what is going on.

---

### Post by Little Bit on 2009-07-23
The same sort of thing happened after a couple of days with my computer too. My problem turned out to be the video driver. So try this (from the Live CD if need be).

Open the terminal and type

```
lspci |grep VGA
```

When I did it, I got back this: [FONT=monospace]
[/FONT]
 ```
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller 
``` 

which means I have the Intel graphics card. But Ubuntu didn't load that driver by default. So I want Ubuntu to use the Intel driver. Here's how I did that:

I opened a terminal and typed:

```
gksudo gedit /etc/X11/xorg.conf
```

and you'll see a line that looks like this:
```

Section "Device"
    Identifier    "Configured Video Device"
EndSection
```


I changed mine it to this (because mine is an Intel. Just substitute yours in place of Intel):

```

Section "Device"
    Identifier    "Videocard0"
    Driver        "intel"
EndSection
```


Then save the file, exit, and reboot into Ubuntu. That tells Ubuntu to use the Intel driver. It completely fixed my problem. I hope it's that easy for you too.

Amy

[FONT=monospace]
[/FONT]

---

### Post by Ratscallion on 2009-07-23
Well, if I try running gedit from within the Terminal in the Recovery boot, I can't, as it's a GUI, and, as I mentioned, Ubuntu is installed via Wubi, so there's no hope of accessing it from anywhere else.

Also, if it helps, I'm being told I have a read-only file system. Is this supposed to be the case in Wubi based Ubuntus? I can't partition as I haven't got an external yet :(

As for the virtual console, there's an option in recovery kernel, it says I can use a root terminal to use the system from there. Will that do?

---

### Post by Ratscallion on 2009-07-24
Ok... So I boot into Ubuntu, press escape (graphical boot does nothing except splash screen, then blank) and go into a recovery kernel. Then, the only way I can get into the terminal is going to a root prompt from the choices (one of the bottom ones)... So, now, what do I do here? Bit helpless as I haven't got a clue!

---

### Post by Ratscallion on 2009-07-24
Help maybe?

---

### Post by Ratscallion on 2009-07-24
Bump! Help?

---

### Post by balgaltz on 2009-07-24
Use nano instead of gedit, this one is for console/terminal.

---

### Post by Ratscallion on 2009-07-24
The problem is I'm using Wubi (so cannot access my Ubuntu files from anywhere besides the installed Ubuntu) and have figured out it's because of root.disk, it's got some error of input/output. Do I need to reinstall?

---

### Post by balgaltz on 2009-07-24
Enter in Recovery Mode and follow **Little Bit**'s suggestion, and instead of using gedit, replace it with nano because this one works in console/terminal.
You will need to change gksudo(graphical) to sudo(terminal).

---

### Post by Ratscallion on 2009-07-24
Is nano installed by default? root.disk is missing and I have the intra#### prompt... Bit confusing for me. I can't do a sudo apt-get install nano on this prompt, so I'm sorta stuck.

---

### Post by balgaltz on 2009-07-24
Are you in Recovery Mode?
Yes, nano is installed by default.

---

### Post by Ratscallion on 2009-07-24
The problem (as I seem to have worked out) is not that of graphics, but because of something in Wubi. Root.disk (the Wubi harddrive) has an input/output error and forces a root prompt. Help?

---

### Post by balgaltz on 2009-07-24
Hmm, can you screenshot?

---

### Post by Ratscallion on 2009-07-24
I can't screenshot a prompt. It's a full screen Terminal telling me to do allsorts. Made a new thread because the error has changed..: [http://ubuntuforums.org/showthread.php?t=1221959](http://ubuntuforums.org/showthread.php?t=1221959)

---

