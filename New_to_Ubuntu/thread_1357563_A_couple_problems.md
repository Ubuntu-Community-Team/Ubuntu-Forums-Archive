---
title: "A couple problems"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by Caldur06 on 2009-12-17
First, I can't get my display settings to save whenever I restart my computer. I'm using nVidia's X server. Once I got the desired settings with the GUI, I did this from the terminal to save:

sudo nvidia-xconfig

And it said it did. Although, when I restart my computer, I'm back to one monitor with low resolution. Am I missing something? I'm using the 190.42 driver.

Flash movies stopped working in Firefox. I'm running 64-bit ubuntu, and so I got Adobe's new 64-bit flash plugin for linux. And it worked! But then it just randomly stopped working. All I did to install this was to copy the libflashplayer.so into the firefox plugins directory. Since it worked for awhile I figured that's all I needed to do.

Also, my about:plugins looks fine. It shows flash enabled for both swf and spl, and it's showing the correct plugin version (10.0 r42).

Any ideas? Thanks and much appreciated!

---

### Post by doas777 on 2009-12-17
nvidia-xconfig will reset your xorg and nvidia-settings to default. you should only have to use it yourself when something is wrong.

try running, 
```
gksu nvidia-settings
```and once you have everythign configured, click "Write configuration to X config" (or whatever the exact text is).

check your update manager. there should be an update for flash. try to avoid ever manually installing a plugin into FF. I;ve seeen a few threads where people really ended up borking their systems to make it work.

---

### Post by northern lights on 2009-12-17
It is advisable to use a descriptive topic title. Threads with titles such as "Need assistance", "Please help", "A problem" or "Few questions" will inevitably get less people to read your post. It will further make people read it that have no knowledge on the topic and would have saved time by skipping it, had they been informed what it is about by the title. So please, refrain from generic titles. Imagine every thread was titled like that...

---

### Post by Caldur06 on 2009-12-17
Hm, interesting. I looked through Synpaptic and noticed I had a couple of flash packages installed, which were flashplugin-installer and flashplugin-nonfree. I wondered if they might be conflicting with the plugin I manually installed, so I uninstalled those packages and it fixed my problem!

As far as I know, there isn't a 64-bit version of the flash plugin in Synaptic. It was only released about a week ago or so. So I think manual installation for that is the only way possible...?

I didn't know about the gksu command. That let me save the file without the permission error, so thanks! I'll restart now and test if it worked.

---

### Post by Caldur06 on 2009-12-17
> **northern lights said:**
> It is advisable to use a descriptive topic title. Threads with titles such as "Need assistance", "Please help", "A problem" or "Few questions" will inevitably get less people to read your post. It will further make people read it that have no knowledge on the topic and would have saved time by skipping it, had they been informed what it is about by the title. So please, refrain from generic titles. Imagine every thread was titled like that...

Yeah, I normally wouldn't do that, but since I had a couple of different questions I didn't want to put two different descriptions in one title.

Ok, my settings saved after my restart. Thanks a bunch!

I do have a new problem now though. A button on my main panel (the top panel with Applications, Places, and System) are in the center of the screen for some reason. This button is the one that says my name where you click it and you can restart, shut down, etc. It doesn't appear that I can drag it back over to the right (over by the date and time). Any ideas?

---

### Post by doas777 on 2009-12-17
> **Caldur06 said:**
> Hm, interesting. I looked through Synpaptic and noticed I had a couple of flash packages installed, which were flashplugin-installer and flashplugin-nonfree. I wondered if they might be conflicting with the plugin I manually installed, so I uninstalled those packages and it fixed my problem!

As far as I know, there isn't a 64-bit version of the flash plugin in Synaptic. It was only released about a week ago or so. So I think manual installation for that is the only way possible...?

I didn't know about the gksu command. That let me save the file without the permission error, so thanks! I'll restart now and test if it worked.

gksu runs a graphical app as admin/root. sudo does the same thing, but is for command line apps. 

if you wanna install flash, my best recomendation is to just install the restricted extras package, so you get flash, some codecs, sun java, and a few FF plugins as well.
```
sudo apt-get install ubuntu-restricted-extras
```it will take care of the 32/64bit problem for you. it's only a problem if you try to download it from adobe.

---

### Post by cholericfun on 2009-12-17
untick the lock-to-panel option and then you can move your icon

---

### Post by northern lights on 2009-12-17
> **Caldur06 said:**
> It doesn't appear that I can drag it back over to the right (over by the date and time). Any ideas?Right-click > Move

---

### Post by Caldur06 on 2009-12-17
Arg, how did I not see that? I even unticked lock to panel to see if I could drag it, but I never saw the Move option. Thanks everyone!

Ok thanks doas, I'm installing the restricted extras at the moment!

---

