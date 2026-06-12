---
title: "Having trouble viewing webpages"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by seamonkey09 on 2009-06-18
I just installed Ubuntu and I tried to go to [www.picnik.com](www.picnik.com) to edit a picture and all I get is a big block with a arrow in it, like you'd see for playing a video. I've used the website before on windows but I don't know what to install to get this to work. I surfed around a bit and saw the same block with the arrow in it. Anyone have any ideas? 

I'm also having trouble loading pictures on photobucket. Things just sort of freeze up.

---

### Post by LewRockwell on 2009-06-18
we'll assume you're using the latest Firefox...

we'll assume you've got the latest flash and such...

are you sure you're seeing an arrow and not the "F" denoting that flash is required?

---

### Post by seamonkey09 on 2009-06-18
I don't know if I'm using the latest anything. I did all the updates that I was being prompted to do as soon as it was finished installing and booted up. How do I check? And yes, I'm sure it's an arrow. It looks like a giant 'play' button in the middle of the screen.

---

### Post by seamonkey09 on 2009-06-18
Screenshot of the problem

---

### Post by UbuntuNerd on 2009-06-18
go to firefox under tools > Add-ons > plugins and post a screen shot

---

### Post by seamonkey09 on 2009-06-18
Screenshot of plugins

---

### Post by UbuntuNerd on 2009-06-18
well I see you have flash 9.0 when it should be 10 also you need java, to install java just type this command in a terminal:
```
sudo apt-get install sun-java6-fonts sun-java6-jre sun-java6-plugin
``` 
to get the latest Flash first you need to unistall flash 9 so go to synaptic package manager and search for "flash" once you find it unistall it.
next go to the [adobe ](http://get.adobe.com/flashplayer/?promoid=BUIGP) and install the latest .deb package

---

### Post by seamonkey09 on 2009-06-19
Still having a problem with picnik. Screenshot is what I see when I go to editing page. Opera doesn't seem to have the blue block problem and will load picture to the website, but freezes and the screen goes dark and I have to force quit.

---

### Post by seamonkey09 on 2009-06-19
Now I'm having problems pulling up sites on Opera. This is getting to be a huge hassle. I can't even use my computer.

---

### Post by seamonkey09 on 2009-06-19
I'm still being told I need to install the new flash player from Adobe. I've already done this three times, but when I go to a website that uses it, I can't access anything.

---

