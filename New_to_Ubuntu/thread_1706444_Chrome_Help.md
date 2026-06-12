---
title: "Chrome Help"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by h8uthemost on 2011-03-13
Hey guys,

I'm having problems with a certain site. If you go here:

[http://www.simslots.com/](http://www.simslots.com/)

And click on any of the games on that page, you'll be taken to a page which should be the game. But instead of the game for me, I get a message that says Missing Plug-In. But...there's nothing for me to click to install whatever plug-in that I'm missing.

Anyone happen to know what I need to do?

Thanks for the help.

---

### Post by uRock on 2011-03-13
Have you run updates lately? I ask, because the page is loading fine for me.

---

### Post by h8uthemost on 2011-03-13
Yeah the page that I linked to loads, but did you try clicking on one of the slot machines? If you did, then the games are loading for you?

I haven't ran updates lately, but I'll do that right now and give it a shot.

Thanks.

---

### Post by h8uthemost on 2011-03-13
Just ran all my updates, and I still get the text Missing Plug-In when I try one of the games.

Anyone else have any ideas?

---

### Post by Rasa1111 on 2011-03-13
Just tried in chrome..
works fine here.

this is the 2nd one i clicked on,
both loaded right up.
[ATTACH]185999[/ATTACH]

 do you need a restart maybe?
or maybe just log out and back in. :???:

---

### Post by uRock on 2011-03-13
There may be something blocking the Java or your current java is out of date. I am running Windows right now and just installed a fresh version of Java from Oracle. And yes, I opened a game within the link without any problems.

---

### Post by uRock on 2011-03-13
I just opened the link via Chrome in Ubuntu and have the same issue as you. If I find a fix for it, then I'll let you know.

---

### Post by cavalier911 on 2011-03-17
Install sun-java6-jre sun-java6-bin sun-java6-plugin

Find the path to the java libnpjp2.so library:

```
sudo find / -iname libnpjp2.so
```

Replace what's in bold below if your path to libnpjp2.so is different.

Symlink from target libnpjp2.so to chromium-browser plugins folder

```
sudo ln -s **/usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so **/usr/lib/chromium-browser/plugins
```

Shutdown and restart chromium-browser if open.

---

### Post by h8uthemost on 2011-03-17
Are the three things you mentioned to install in your package manager, cavalier? They're not in mine. I'll try doing some searching and see if I can find them(which won't help me if they're not .deb's).

Thanks for a solution.

EDIT: I found a sun-java6-jre.deb, but of course I get a dependency error when tying to install it. This is more work than it's worth so I'll probably just forget about it. But thanks again for the help.

Yeah, I got all three downloaded. And when I try to install one, I get an error dependency of the other. So I try to install the other one, and it says I have an error dependency of the one I just tried installing. Frustrating.

---

### Post by cavalier911 on 2011-03-18
I added [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner to Menu/Preferences/Software Sources on Lubuntu Lucid 10.04 
Menu/Preferences/Synaptic Package Manager
Reload
Mark the java packages for installation.
Synaptic will mark additional dependencies for installation.
Apply

---

### Post by h8uthemost on 2011-03-18
That did it, cavalier. All I had to do was install the three sun-java's that you posted. After I did that I checked the site and the machines are now playing, I didn't have to do your other instructions.

Well, thanks a lot for the fix! I really appreciate it.

---

