---
title: "My desktop is a disaster..."
date: 2009-04-26
forum: New to Ubuntu
---

### Post by projecthikari on 2009-04-26
Alright, here's the story...

I've go my desktop. It was Ubuntu 8.10. So, yesterday I attempted to update to 9.04 and in the middle of installation, my computer suddenly decided to freeze and crash.
It's been a complete disaster ever since. The OS refused to start up, and I was lucky to get into the GRUB menu and somehow start up the desktop. (which was dumb luck... The 8.10 Live CD simply refused to work.)
So, I got all my files and then attempted to install an Ubuntu 9.04 from a disc my boyfriend had made for me. The CD would not read until we DISABLED EVERYTHING from starting except the CD drive in the BIOS. It seems that's the only way we can get the CD to boot up. If we try to, say, make the Hard Drive boot up second, it seems to ignore the CD and take a try at loading the OS.
So, we attempted to install, and in the middle of Installation the first time, it didn't finish. It stopped and just sat there for hours, doing nothing. It'd cleared the computer of Ubuntu 8.10...
But, then when we went in to try again, the CD refused to work ALL NIGHT until I did a Memory check. I waited over night, it did it's thing, said everything was fine, and allowed me to attempt installing again.
I left it to do it's thing, and then It said it was installing the operating system. After awhile, the screen went black, and when I moved the mouse, it showed me the installation progress bar. But, nothing was on it, and it was blacked out. Soon enough, I suddenly got some thick blue and grey bars on the screen...
And, just about 5 minutes ago, my computer made the 'turning off' noise... But the lights are still lit up. I'm afraid to turn it off.

...To be quite honest, I've been working on this for 24 hours and I have no idea what's going on... It's completely draining.:(

We're suspecting that the disc is defective. We want to make a new one. I'm not sure if it's worth the time.

So... uhm... Help?

---

### Post by yoasif on 2009-04-26
that powering off sound sounds like your power supply may be dying. tough to tell what the issue is; you could try using the alternate install cd.

---

### Post by Didius Falco on 2009-04-26
Here is something to try - no guarantees, but it worked for me in a similar situation.

Boot the Live CD with the "Make no changed to the Computer" option.

Open a terminal (Applications/Accessories/Terminal) and type ```
ubiquity --no-migration-assistant
```

That will start the install. If you suspect the screen blanking may be causing a problem, simply move the mouser pointer every couple of minutes.

Good luck, and I hope it helps.

---

### Post by projecthikari on 2009-04-26
When I attempt to load the live CD, I get this message...

"Loading, Please wait..

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _"

The _ on the end is the cursor, of course.

---

### Post by projecthikari on 2009-04-26
I gave up. I even tired to put an XP disc in, and it simply wouldn't read it. I'm using my Laptop as a Desktop now. I'll simply have to buy a new computer.

...Anybody wanna help me with choosing a new desktop? haha~

---

