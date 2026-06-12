---
title: "internet attach req'd for install?"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by wayne_newbie on 2009-04-27
I am a complete linux novice and wanted to install Ubuntu on a used computer I picked up. The computer is pretty barren at this time, but I'll add hard drives if it works well.
It's an IBM eServer 206 type 8482, 3.0ghz P4 cpu, 2gb memory, with only a diskette reader, CDrom, and 2 scsi drives (9gb and 1gb). It has an ethernet port, but I don't have it attached at this time. 

I downloaded the 9.04 iso (on my regular computer) and burned a CD.
The CD seemed to work fine, walked me through some questions (BTW, why MUST
you create a userid and password?) and then it created 2 partitions on a 9gb scsi drive, and downloaded for a considerable time. Finally it opened the CDrom drawer and asked 
me to remove the CD and press enter. My computer then re-booted and showed a few lines of text momentarily, then an Ubuntu logo for perhaps 10 seconds, then... nothing.
The logo disappeared and the screen just sat there blank for hours, apparently hung. Tried Kubuntu with the same result. So it seems it's trying to boot, and hanging shortly into the boot.

Could it be that it's trying to call home but can't find a connection (wouldn't it give an error message?), or is there something very wrong?

---

### Post by kanikilu on 2009-04-27
No, you shouldn't need an internet connection to boot up. Do a [search]("http://www.google.com/search?q=ubuntu+blank+screen") for "ubuntu blank screen", it seems to be a pretty common problem...

---

### Post by The Cog on 2009-04-27
See if Ctrl-Alt-F1 gets you a text console. If so, try these two commands:
[B]sudo /etc/init.d/gdm stop
startx[/B]
which should stop the gnome desktop manager (which is not working anyway) and then tries to start the X server from the command line. The error messages from startx might be enlightening.

---

### Post by wayne_newbie on 2009-04-27
> **kanikilu said:**
> No, you shouldn't need an internet connection to boot up. Do a [search]("http://www.google.com/search?q=ubuntu+blank+screen") for "ubuntu blank screen", it seems to be a pretty common problem...

OK, I'll do some searching... my first search hit didn't pan out, so I'll look some more.

Thanks.

---

### Post by wayne_newbie on 2009-04-27
> **The Cog said:**
> See if Ctrl-Alt-F1 gets you a text console. If so, try these two commands:
[B]sudo /etc/init.d/gdm stop
startx[/B]
which should stop the gnome desktop manager (which is not working anyway) and then tries to start the X server from the command line. The error messages from startx might be enlightening.

Thanks for helping... unfortunately nothing happened when I did Ctrl-Alt-F1

---

### Post by wayne_newbie on 2009-04-27
> **wayne_newbie said:**
> OK, I'll do some searching... my first search hit didn't pan out, so I'll look some more.

Thanks.

All right, I made a little progress from stuff I found in Google, but don't know where to go from here. Currently I have Kubuntu on the hard drive...
 
- I hit the esc key during bootup,
- then selected "ubuntu 9.04. kernel 2.6.28-11-generic (recovery mode),
- then waited as a rush of text messages went by
- then entered "exit" by trial & error after nothing else I tried worked ("not found"),
    including the "sudo" command that Cog suggested 
- that brought up a slew of messages, followed by a recovery menu window; I selected
    "resume normal boot" off that menu
- a graphical interface/desktop came up (shades of blue with out-of-focus lights on it)

Now, all those machinations and "recovery mode" are not a good way to operate...
perhaps this will give somebody a clue as to how I can correct Kubuntu on the hard drive so that it will come up normally. From my reading I suspect there is a problem with the display settings ...wherever they are, and however they may be altered. 

Can someone help? ...with the understanding that I've never even looked at an Ubuntu desktop before... I'm a WinXP user, so any instructions need to be very basic, although I do have a background in old mainframe computers, so I understand the command line and directory concepts, I just don't know what & where.
I can remove Kubuntu and re-install Ubuntu if I need to (it had the same problem).

I am using a Dell (Sony-built trinitron type) 19" model P992 display, but I know nothing about the integrated display adapter on the IBM eServer motherboard (which brings up a side question: if I add a display adapter later, can Ubuntu handle two displays like WinXP does to extend the desktop?).

---

### Post by wayne_newbie on 2009-04-27
Another addendum... I found the Dell P992 specs, and I found the setting in Kubuntu "display system settings", and they are the same... ([FONT=Arial]1024 x 768 at 85 Hz)...[/FONT] so maybe the display settings are NOT the issue on bootup?

---

### Post by wayne_newbie on 2009-04-28
Well, I got the problem resolved :P, and it probably was not the display.

I've had a minor problem with the cdrom I attached to the computer; it gave me an error message during bios bootup, but then went right on and worked fine... I ignored that as a minor glitch. So I first installed Ubuntu, which had the blank screen problem, and then I had the same issue when I installed Kubuntu. But, when I got past the blank screen issue with manual intervention, I noted that Kubuntu didn't show the cdrom device.

I went back and tried several other bios setup options for the cdrom and finally got rid of the bios bootup error message. Then I re-installed Ubuntu (just to have a look at its user interface compared to Kubuntu), and this time Ubuntu came up fine, and it sees the cdrom device!

I surmise that the blank screen problem was cdrom-related, not display-related as my Google search had led me to believe.

---

