---
title: "N52te still not working."
date: 2010-10-25
forum: New to Ubuntu
---

### Post by Furi on 2010-10-25
After trying Pystromo to no avail, I've resorted to [this thread]("http://ubuntuforums.org/showthread.php?t=538319"). I followed all of the instructions up to the daemon, which closes immediately after the startup. I looked through the replies and none of them helped. The reply mentioning "daemon.cxx" I tried to follow, but I couldn't find the file. Any help, anyone? If there's any difference, I'm using 10.10.

---

### Post by Furi on 2010-10-25
I forgot to mention that when starting the daemon the lights do not blink.

---

### Post by Furi on 2010-10-25
Will anyone reply to this? I really need help.

The daemon only blinks on then off when I add "sudo" to the beginning. Otherwise, it doesn't even appear.

---

### Post by Furi on 2010-10-25
Guys, come on. I don't want $60 to be wasted.

---

### Post by Furi on 2010-10-25
Darn it, I never get help when I really need it. Happened with Music Applet; nobody told me how to fix the errors when trying to add it to the panel.

---

### Post by Furi on 2010-10-25
Bump...again...

---

### Post by Furi on 2010-10-25
I have successfully managed to get the daemon up and running without shutting off immediately, but the lights do not change between the 3 indicators on the side of it, and the mappings do not change from the factory default. What now?

---

### Post by Objekt on 2010-10-29
I'm wondering about this as well.  I just spent several minutes fiddling with pystromo to no avail.  

FWIW, I have the regular (older?) Nostromo n52.  I think the only difference between the n52 and n52te is that the "te" has backlighting and is slightly streamlined.  The two devices look like they have exactly the same buttons, and therefore should be the same for pystromo purposes.

I tried the pystromo instructions in a thread here: [http://ubuntuforums.org/showthread.php?t=948833&highlight=pystromo]("http://ubuntuforums.org/showthread.php?t=948833&highlight=pystromo")

but they don't work.  I get stopped cold at the step where you run the command:
```
./pystromo-remap.py -m default.map
```

Here's how it goes:
```
user4@user4-desktop:~/.config/pystromo$ ./pystromo-remap.py -m default.map
Traceback (most recent call last):
  File "./pystromo-remap.py", line 51, in <module>
    output = devices.OutputDevice()
  File "/home/user4/.config/pystromo/lib/devices.py", line 665, in __init__
    self.node = ioctl.OutputNode()
  File "/home/user4/.config/pystromo/lib/ioctl.py", line 237, in __init__
    raise LookupError ('no uinput device-nodes found')
LookupError: no uinput device-nodes found
user4@user4-desktop:~/.config/pystromo$ 
```

It appears something has changed in the 2 years and 2 Ubuntu versions since those instructions were last updated (17 Oct. 2008 ), something which breaks Pystromo.

For now, I can only use my n52 in default mode.

I'm also seeing this really strange bug, where running Rhythmbox makes all 3 LEDs on the n52 blink.  No idea what's going on there.

---

