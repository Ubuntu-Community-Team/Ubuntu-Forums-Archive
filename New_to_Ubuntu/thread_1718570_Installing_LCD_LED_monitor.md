---
title: "Installing LCD LED monitor"
date: 2011-03-31
forum: New to Ubuntu
---

### Post by Newuser901 on 2011-03-31
I just bought an Asus VK278Q monitor. This is my first LCD let alone LED. I have the install disk and the monitor hooked up. any hints as to whre to start. I'm not sure if these are more prone to damage from screw ups. CRTs are generally plug and playish so......

Should this work without drivers?

I see It wants me to auto set it up with wine!! 8p. It is party to play EVE. but.. 8p

I'm not finding much in google searches. I think I'm looking it up wrong or something.

Forgot. I have it hooked up and... I set it to DVI which it is hooked up through. But it says no single. The monitor software from Nvidia(from their drivers being installed) says disabled now but was saying the 1920X1080 resolution.

---

### Post by Newuser901 on 2011-03-31
OK. I'm stupid. I restarted the comp and now it's the main monitor. Any idea why it doesn't keep my 1920X1080 res though. I've seen threads on it but since I already started the thread on what turned out to be a stupid situation, I might as well ask another question similarly. 8)

Though I am still curious if I need the drivers for anything. They could be for the webcam. but I'm not sure. Do you want to install monitor drivers in wine for instance if you are running games in wine? Will it get more functionality?

---

### Post by wolfen69 on 2011-03-31
You need to launch the nvidia controls with:
```
gksu nvidia-settings
```
Click X Server Display Configuration in upper left. Make all the necessary adjustments, click apply, and then Save to X Configuration File.

Let us know what happens.

---

### Post by realzippy on 2011-03-31
This used to be so,meanwhile there is no need for running nvidia-settings
as root.It asks for password when saving to xorg.conf,rest goes to nvidia-settings.rc in user's home...but
+1 for Save to X Configuration File

---

### Post by Newuser901 on 2011-04-10
I'm calling this solved. I'm still learning duel monitor stuff and I'll figure any more out later. thanks.

---

