---
title: "Hibernation doesn't work in wubi?"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by P-rench on 2011-01-16
I have wubi installed on windows xp as a dual boot and I'm running ubuntu 9.10. I'm new to most of this. My issue is that I can't get hibernation to work. I did some research and as far as I can tell hibernation is one of the functions that is not available on wubi ubuntu installs. So my question, is there anyway I can get around this dilemma and make hibernation work? Or is there an alternative way I can mimic hibernation so I can save my open programs upon shutdown so they will reappear open on start up?

---

### Post by cgroza on 2011-01-16
Wubi does not support Hibernation as far as I know. You need a real Ubuntu install and swap partition of the size of your RAM do do it.

---

### Post by cgroza on 2011-01-16
Wubi does not support Hibernation as far as I know. You need a real Ubuntu install and swap partition of the size of your RAM do do it.

---

### Post by P-rench on 2011-01-16
bummer, there has to be a way, I'll keep looking around, maybe I'll find something.

---

### Post by Elfy on 2011-01-16
> **P-rench said:**
>  Or is there an alternative way I can mimic hibernation so I can save my open programs upon shutdown so they will reappear open on start up?

System - Preferences - Startup Applications - Options

That should help you

---

### Post by alzie on 2011-01-16
I'm not sure if it will do what you are looking for but there is system>preferences>startup applications 

Under options you can set it to "Automatically remember running applications when logging out"  I don't know if it will open your browser to the last page you were looking at but it might be what you are looking for.

Hope this helps.

Edit: Got to type faster

---

### Post by P-rench on 2011-01-16
Start up applications is an idea, but I'm still in a pickle cause lets say I have an open office document open, pidgin running with 3 im box's, and firefox open with say 4 tabs open, I don't think I'll be able to setup startup applications to resume all of this when I boot my computer back up. An other ideas?

---

### Post by Frogs Hair on 2011-01-16
Wubi will support sleep , but the swap isn't large enough to support hibernation . I think the default swap for Wubi is 255 mb .

---

### Post by P-rench on 2011-01-16
Alright, thanks for the replies and advice everyone! =]. Setting startup applications to save my current running applications appears to have somewhat work, except it didn't start up my im windows or openoffice document. Its something though. Any other ideas?

---

### Post by P-rench on 2011-01-16
I did bump the swap up to 3gigs, my ram is 2 gigs. Hibernation still did not work though.

---

### Post by Frogs Hair on 2011-01-16
Increase swap from the Wubi guide.[https://wiki.ubuntu.com/WubiGuide#How](https://wiki.ubuntu.com/WubiGuide#How) do I increase my swap space

---

### Post by Frogs Hair on 2011-01-16
Wubi uses a swap file not a swap partition , so hibernation won't work for all computers.[https://answers.launchpad.net/wubi/+question/141155](https://answers.launchpad.net/wubi/+question/141155)

---

