---
title: "Open location as? Where to find the appropriate app..."
date: 2009-03-19
forum: New to Ubuntu
---

### Post by simiot on 2009-03-19
I click on link to play audio streams but it only gives me the option for Totem. Totem won't play this stream. It just freezes. So, I want to choose VLC to play the stream but, I don't know where to browse for the VLC app. I could do this in Windows... But, the file system is arranged differently in Ubuntu. So, how do I locate VLC when I have to browse to select it? This will probably give me some idea where all apps are stored, I hope.

Thanks in advance!

---

### Post by bruno9779 on 2009-03-19
You can set different apps to open a file by right clicking, Properties > open with

After you have set an app here it will also show up when you right click on a file with the same extension

---

### Post by simiot on 2009-03-19
> **bruno9779 said:**
> You can set different apps to open a file by right clicking, Properties > open with

After you have set an app here it will also show up when you right click on a file with the same extension

Thanks for this. That helps a little but, I am still trying to open a link on a webpage & it prompts me to 'open with' or 'save'. I need to 'open with' but I don't know where to browse the folders to find where the VLC app is located...

---

### Post by issih on 2009-03-19
Most likely its exact path is /usr/bin/vlc

Note that you can find things with tracker (little magnifying glass in top panel), using the locate command in a terminal (e.g I did "locate *bin*vlc*" to find any files named something with vlc in them located in a bin directory which is where executables usually are) and also you can go to synaptic, and in the properties of any installed package it will tell you exactly where the installed files are.

Hope that helps

---

### Post by aeiah on 2009-03-19
i find that to be annoying too. it doesnt happen too often but when it does i think my tactic is:

- save the file to the desktop

- click properties and set the default program in there for the filetype

- reload the page and this time you should see vlc (or whatever else you set) show up in the open with.. section.


but you should be able to find vlc in usr/bin

---

### Post by bruno9779 on 2009-03-19
> **simiot said:**
> ... I am still trying to open a link on a webpage & it prompts me to 'open with' or 'save'. I need to 'open with' but ...

From what you say the problem is when opening multimedia files from Firefox.

I am not in front of my ubuntu machine, but i recall you can set this once for all in options > Applications in firefox.

alternatively VLC plugin for mozilla also help

---

### Post by billgoldberg on 2009-03-19
I don't have VLC installed but let's take Totem as the example:

```
whereis totem
```> 
totem: **/usr/bin/totem** /usr/lib/totem /usr/share/totem /usr/share/man/man1/totem.1.gz


---

### Post by Bölvaður on 2009-03-19
you do not have to browse for the executable file, as it accepts just typing  vlc (as vlc is in your PATH variable...)

so you do not need the full path, just the command vlc

---

### Post by simiot on 2009-03-19
> **issih said:**
> Most likely its exact path is /usr/bin/vlc

Note that you can find things with tracker (little magnifying glass in top panel), using the locate command in a terminal (e.g I did "locate *bin*vlc*" to find any files named something with vlc in them located in a bin directory which is where executables usually are) and also you can go to synaptic, and in the properties of any installed package it will tell you exactly where the installed files are.

Hope that helps

Thanks! I found VLC, with many other apps, in /usr/bin. This will be helpful in the future with other Open as links, I'm sure.


I can't see the magnifying glass on mine. I might get something off synaptic.

:-)

---

### Post by simiot on 2009-03-19
> **issih said:**
> Most likely its exact path is /usr/bin/vlc

Note that you can find things with tracker (little magnifying glass in top panel), using the locate command in a terminal (e.g I did "locate *bin*vlc*" to find any files named something with vlc in them located in a bin directory which is where executables usually are) and also you can go to synaptic, and in the properties of any installed package it will tell you exactly where the installed files are.

Hope that helps

> **aeiah said:**
> i find that to be annoying too. it doesnt happen too often but when it does i think my tactic is:

- save the file to the desktop

- click properties and set the default program in there for the filetype

- reload the page and this time you should see vlc (or whatever else you set) show up in the open with.. section.


but you should be able to find vlc in usr/bin

Originally I saved the stream booting file to the desktop and right clicked on it and 'opened with' and launched VLC this way. I thought then it might suggest it as when I click on the link again but, it didn't. But, everything is fine now I know where to find the apps. I browsed for it now and ticked 'always do this' (or whatever it says) so its good now. I am learning more about ubuntu every day :D

---

### Post by simiot on 2009-03-19
> **Bölvaður said:**
> you do not have to browse for the executable file, as it accepts just typing  vlc (as vlc is in your PATH variable...)

so you do not need the full path, just the command vlc

When clicking on a link I tried this too but, it didn't work. I know what you mean though. Like, I can open VLC in a command line by just typing 'vlc' but I wished using web links then browse & select worked this way also it worked that way.

:)

---

