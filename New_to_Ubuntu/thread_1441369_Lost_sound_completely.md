---
title: "Lost sound completely"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by johnfrith on 2010-03-28
I clean installed 32bit Karmic a few days ago, but there was no sound at all. Then suddenly it worked, no idea why it kicked in. Then today it's gone again. Don't know if it was anything to do with the system update that came through today.

Sound Prefereces lists "Dummy Output" device.

I promise I've spent a couple of hours trying to find a solution myself. If anyone can help me,  I have very little knowledge, but am reading through the pocket guide.

Intel 82801I (ICH9 Family) HD Audio controller

---

### Post by m4tic on 2010-03-28
delete homefolder/.pulse

---

### Post by johnfrith on 2010-03-28
Thanks m4tic. I renamed it (just in case I needed to get it back), rebooted, but no change.

I note that I get the little drum roll when ubuntu boots.

---

### Post by lidex on 2010-03-28
What is the output of this command:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

In a terminal: "Applications>Accessories>Terminal"

---

### Post by johnfrith on 2010-03-28
> **lidex said:**
> What is the output of this command:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```In a terminal: "Applications>Accessories>Terminal"

Thanks lidex. I get:

john@jf:~$ sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
[sudo] password for john: 
                     USER PID ACCESS COMMAND
/dev/snd/controlC0:  Slmodemd   1313 F.... slmodemd
/dev/snd/pcmC0D6c:   Slmodemd   1313 F...m slmodemd
/dev/snd/pcmC0D6p:   Slmodemd   1313 F...m slmodemd
john@jf:~$ 

I'd read something about a conflict with simodemd, but couldn't see it running in the Processes tab of the System Monitor, so thought it wasn't an issue.

---

### Post by lidex on 2010-03-28
That's your problem. If you're not using a modem run this command:
```
sudo apt-get remove sl-modem-daemon
```

Then reboot.

*[COLOR="Blue"]Edit: fixed command[/COLOR]*

---

### Post by johnfrith on 2010-03-28
Thanks again lidex. I do occasionally use the modem to send faxes, so I'd like to be able to reverse the delete or find an alternative.

At [http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html](http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html)

it says:

"In the meantime, you can either instead load module-detect in /etc/pulse/default.pa (or ~/.pulse/default.pa) or kill slmodemd."

I presume your suggestion is the "kill" option (as opposed to me trying to rename it!).
 I edited the file in etc, by adding this on the end:


### JF: this to fix no sound bug caused by simodemd conflict
load module-detect


But on rebooting I'd lost the sound icon, and System > Preferences > Sound now doesn't even launch the program.

---

### Post by lidex on 2010-03-28
I'd undo that. Another fix is updating to ppa version of PA. Info here:
[https://launchpad.net/~ubuntu-audio-dev/+archive/ppa]("https://launchpad.net/~ubuntu-audio-dev/+archive/ppa")

---

### Post by johnfrith on 2010-03-28
Thanks lidex.

On the page you iink to it says:

"This PPA can be added to your system manually by copying              the lines below and adding them to your system's software              sources."

Sorry for such basic questions but does this mean copy and paste into terminal, or somewhere else?

---

### Post by lidex on 2010-03-28
Try this:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
```

Then:
```
sudo apt-get update
sudo apt-get upgrade
```

Then reboot

---

### Post by sandyd on 2010-03-28
just do
```

sudo apt-get remove pulseaudio pulseaudio-*
```

---

### Post by johnfrith on 2010-03-29
Thanks lidex, carlee.

I tried lidex's suggestion first, but it left the system the same (I did reboot) - dummy output, no sound. I don't know if it's relevant, but the last command didn't seem to have any upgrades in it.
 john@jf:~$ sudo apt-get upgrade  
 Reading package lists... Done  
 Building dependency tree  
 Reading state information... Done  
 The following packages have been kept back:  
 libpulse-browse0 libpulse-mainloop-glib0 libpulse0 pulseaudio  
 pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf  
 pulseaudio-module-x11 pulseaudio-utils  
 0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
 

 I then tried carlee's suggestion, but this left me with no sound icon at all! When I tried System > Preferences > Sound I got the message "Waiting for sound system to respond". This was the same reaction I got when I added "load module-detect" on to the end of /etc/pulse/default.pa, as suggested at:  
 [http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html](http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html)

Now "sudo apt-get remove sl-modem-daemon" doesn't work, which it did before!  Do I do this to reverse out?
sudo apt-get install pulseaudio pulseaudio-* 
 The plot sickens... sorry, thickens. John

---

### Post by lidex on 2010-03-29
I know some people recommend removing pulseaudio for every little sound issue - probably because they've had problems with it - but that really is a last ditch effort, especially for noobs, as it brings about a whole new set of problems. Pulseaudio is your sound server and gives your system the ability to use audio in more than one program at a time. Reinstall it please. This command is probably the easiest way:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by johnfrith on 2010-03-30
Thanks lidex, that recovered me.

So it seems that the only option I have is to remove sl-modem-daemon, and re-install if I need the modem?

Any idea if this is fixed with 10.4?

---

### Post by lidex on 2010-03-30
I believe so but still in beta. But you never completed the pulseaudio upgrade - those packages were held back. Updating PA should fix it.

---

### Post by johnfrith on 2010-03-30
Thanks for all your help lidex.

---

