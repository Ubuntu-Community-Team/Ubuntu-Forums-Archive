---
title: "Add Serial Mouse after Install with PS/2"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by Shadow Warrior on 2011-03-30
Because of a corrupted Windows XP Professional install and no setup disks available. The only operating system that I was able to afford and install was the latest ubuntu. Now that I'm sharing computers with my wife, the only mouse that works with my ThinkPad laptop (other than it's built in pointing device, which she does not like) is the PS/2 mouse. There are a number of threads about re-attaching a serial mouse to my desktop system.

Do I have to do a fresh install of ubuntu without the PS/2 mouse attached or is there a straight forward way to get ubuntu to recognize my serial mouse?

---

### Post by wolfen69 on 2011-03-31
Check to see if you have **inputattach** installed in synaptic. Did you shut the computer down, attach the mouse and reboot?

---

### Post by Shadow Warrior on 2011-03-31
I recall learning about inputattach. Is synaptic another package that needs to be installed? If so, before or after?

---

### Post by wolfen69 on 2011-03-31
> **Shadow Warrior said:**
> I recall learning about inputattach. Is synaptic another package that needs to be installed? If so, before or after?

No, synaptic is the package manager you can use to install things. It is in system>administration.

Or you could open a terminal and do:
```
sudo apt-get install inputattach
```

---

### Post by Shadow Warrior on 2011-03-31
> **wolfen69 said:**
> No, synaptic is the package manager you can use to install things. It is in system>administration.

Or you could open a terminal and do:
```
sudo apt-get install inputattach
```
Once inputattach is installed, what's the next step? Re-boot without the PS/2 mouse attached? How can I tell that the system is now recognizing the serial mouse?

---

### Post by Shadow Warrior on 2011-04-01
> **Shadow Warrior said:**
> Once inputattach is installed, what's the next step? Re-boot without the PS/2 mouse attached? How can I tell that the system is now recognizing the serial mouse?
I've been able to establish that I have "inputattach" installed. What's next?

---

### Post by Shadow Warrior on 2011-04-06
> **wolfen69 said:**
> Check to see if you have **inputattach** installed in synaptic. Did you shut the computer down, attach the mouse and reboot?
This is one step that I didn't complete. (Check the *inputtattach installation*). Thoughout this whole process the serial mouse has been attached to the serial port along with the PS/2 mouse.

How do I navigate around the GUI interface using the keyboard? When I restart, I don't want to confuse my installation by having 2 mice installed.

---

### Post by Shadow Warrior on 2011-04-07
All right, I've found that input attach is installed. I've shutdown the computer, unplugged the PS/2 mouse and restarted. Ubuntu **STILL** doesn't recognize my serial mouse. I don't know how to navigate around the GUI with the keyboard. Do I need to go to the command line and completely remove the more modern mouse? Is there a config file I need to manually adjust?

Is there an installation of an earlier version of Ubuntu (or any other version of linux) that **WOULD** recognize the serial mouse at the time of installation?

---

### Post by Shadow Warrior on 2011-04-08
> **Shadow Warrior said:**
> All right, I've found that input attach is installed. I've shutdown the computer, unplugged the PS/2 mouse and restarted. Ubuntu **STILL** doesn't recognize my serial mouse. I don't know how to navigate around the GUI with the keyboard. Do I need to go to the command line and completely remove the more modern mouse? Is there a config file I need to manually adjust?

Is there an installation of an earlier version of Ubuntu (or any other version of linux) that **WOULD** recognize the serial mouse at the time of installation?
That's what I've enjoyed about banging my head against the wall while working with computers...damn it feels good when I stop.

I have inputattach installed, I log into root (su) to run it and I continues to ask me for a device. I have 3 button serial mouse in "ms" mode. I have the mouse attached to the only serial port my Dell OptiPlex 2350 has. How do I tell the OS to look at the "right" place?

---

### Post by Perkins on 2011-07-07
As with most all Linux command-line programs, a good place to start is to type "man inputattach" on the command line.  Doing so yields a list of options and how to use the command.

In your case, what you're probably going to want is to type```
sudo inputattach -ms3 /dev/ttyS0 
```

If that works, then you can run it with the --daemon flag to make it go to the background and not bother you anymore.  If it doesn't survive a reboot, add the command to /etc/rc.local and put an & on the end of it and it will run at bootup.

If it doesn't work, then there are two possibilities.  Either you have the wrong kind of mouse selected.  (the -ms3 part is for a microsoft, 3button mouse.) or the wrong serial port.  If changing the type of mouse to match what you have (full list is in the man page, it may take some guess work.  For example, my Kraft trackball uses the mouse systems protocol) doesn't make it work, then you may have the wrong serial port.  (the /dev/ttyS0 part)  Try it with the different ttyS* identifiers in the /dev directory and see if that works.  Otherwise, let me know and I can help you figure out for certain which one it is.

You don't have to remove the PS/2 mouse before doing this.  Linux is perfectly capable of handling two mice.  In fact, there's even a module running around somewhere to let you use two mice to control two different pointers on the same screen.  ;)

---

