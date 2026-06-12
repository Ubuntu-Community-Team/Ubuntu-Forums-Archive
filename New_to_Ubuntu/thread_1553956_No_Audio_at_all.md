---
title: "No Audio at all"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by penalt on 2010-08-15
I'm desperately looking for some help with this problem.  I have posted this to two other areas but from the lack of response I am assuming I posted them in the wrong spot...

/ repost

I'm currently in the process of joining the Dreddit corporation in Eve  Online.  On of the things they use is the Mumble program.  So, to  anticipate, I downloaded Mumble via the Ubuntu Software Center but I  couldn't seem to get it to recognize my mic.  I closed down the program  in frustration and since then I have had no sound anywhere with Ubuntu.

My volume indicator seems to indicate that things have been muted but I  have been unable to find anything in my Sound Preferences that seems to  indicate muted sounds.  I previously did have Wine set to use OSS  drivers instead of ALSA because that was the only way I had sound in Eve  at all.

Since the problem developed even the audio settings panel in Wine has changed.  Help!  

ps. I have since noticed that Ubuntu is not showing any audio hardware in anything that I can access.

/ end repost

If this is also the wrong place for this I am absolutely fine with a mod moving this post to the correct area.  thx.

---

### Post by jmfal on 2010-08-15
Applications>accessories>terminal  type in

    ```
  alsamixer
```

make sure mic is not muted (use arrows on keypad, l/r to change selection up/dwn to raise/lower in/output)

---

### Post by penalt on 2010-08-16
I get 'cannot open mixer: no such file or directory'......

---

### Post by mastablasta on 2010-08-16
you need to restart alsamixer.
 
set it up and then save settings. sorry i dont' know the commands at the moment as they are written down on piece fo paper i left at home... but someone else here might know them.

---

### Post by penalt on 2010-08-16
I may not HAVE alsamixer.   There is a Gnome Alsamixer in the software center and a search of my installed alsa softwares shows an Alsa Utilities but no alsa mixer....

---

### Post by khelben1979 on 2010-08-16
I suspect that Ubuntu have made an kernel upgrade through the regular Ubuntu updates system.

If that is the case, then you can try with restarting the Ubuntu Linux system to see if anything changes. If that don't solve the problem, the solution is to reinstall the ALSA sound system and there's different methods of achieving that, but for now let's wait and see if a reboot fixes the problem, I guess you've tried it?

Using Gnome Alsamixer or just Alsamixer doesn't matter in this case, they both have the same functionality and features. Alsamixer don't require a working X server since it's text based.

---

### Post by penalt on 2010-08-16
> **khelben1979 said:**
> I suspect that Ubuntu have made an kernel upgrade through the regular Ubuntu updates system.

If that is the case, then you can try with restarting the Ubuntu Linux system to see if anything changes. If that don't solve the problem, the solution is to reinstall the ALSA sound system and there's different methods of achieving that, but for now let's wait and see if a reboot fixes the problem, I guess you've tried it?

Using Gnome Alsamixer or just Alsamixer doesn't matter in this case, they both have the same functionality and features. Alsamixer don't require a working X server since it's text based.

Yes, I have rebooted the system a few times.  How would I go about reinstalling the Alsa sound system?

---

### Post by penalt on 2010-08-16
Extra information that may help.  Did a command of:[SIZE=2]lspci -v[/SIZE]
And got:

00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
    Subsystem: Acer Incorporated [ALI] Device 0126
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at f2680000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

Which would seem to indicate that my drivers are there at least.



Edit: Did a full alsa purge, followed by a reinstall.  Same result with aplay -l command:

aplay: device_list:223: no soundcards found...

---

### Post by penalt on 2010-08-16
Oh, this is comedy....

I have 2 Ubuntu installations on my computer.  In frustration I went and booted the old one.  Lo and behold SOUND!!!!!

I go wtf and reboot back to my main linux install, and I have sound again and now my sound card is detected and running.  I'm not sure what happened but I have sound.

---

### Post by khelben1979 on 2010-08-17
Nice that you got it working! I recommend you mark the thread as solved.

---

