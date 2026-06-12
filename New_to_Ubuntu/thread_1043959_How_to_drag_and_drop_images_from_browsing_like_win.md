---
title: "How to drag and drop images from browsing like windows"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by icyest on 2009-01-19
I want to be able to drag and drop individual images (eg jpeg) from when I'm browsing directly to my desktop. Notice i specifically said "drag and drop" instead of "save image as."

It's not a difference of browsers. This worked with windows. I just want to know how to customize and establish this ability with linux.

---

### Post by Partyboi2 on 2009-01-19
You can drag and drop images to your desktop from Firefox.
[http://linuxhelp.blogspot.com/2006/06/lesser-known-drag-and-drop-tips-in.html](http://linuxhelp.blogspot.com/2006/06/lesser-known-drag-and-drop-tips-in.html)

---

### Post by dubhear on 2009-05-29
[HTML]http://linux.oneandoneis2.org/LNW.htm[/HTML]

might want to read this link, before you type windows one more time, i don't mean to be rude but, it really helped me out to clear thigs a bit.

hope it will do you the same. it's a good link if you havent seen it already? 

btw: i have ubuntu 8.04 and windows as dual boot. most problems i get is my messed up xp... it's just natural behavior for it to be messed up. I have tamed it somehow. 

i've been there too where you stand now, i think big part of us here have some sort of common history behind us.

ps. **tldr**(too long didn't read is not an excuse) you propably want to read things like this, sooner or later.

---

### Post by dubhear on 2009-05-29
how the **** could i manage to quote my own message.
losing my mind, must be...

---

### Post by mkvnmtr on 2009-05-29
I deon't understand why you are asking how to drag and drop from a browser. This has worked for me on every Ubuntu or Mac distro I have used in the last oh maybe 8 years. Does it work different in windows?

---

### Post by UbuntuNerd on 2009-05-29
mine also works fine I can drag and drop links and images from my browser to the desktop anytime :)

---

### Post by desperado665 on 2009-05-29
I see what he is referring to, when I drag n drop a photo from firefox to my desktop, what I get is a firefox link to the pic instead of the pic itself.

I'm using Jaunty 64 bit with Firefox 3.0.10

---

### Post by SunnyRabbiera on 2009-05-29
well right click and selecting "save image as" is easy for me as drag and drop from the browser.

---

### Post by Bradtek on 2009-05-29
Never tried it until now.

I tried dragging UbuntuNerd's avatar to desktop and I got a link

If I click on his avatar and go to his profile page I can drag it to desktop

Google image search, nothing happens if I try to drag the pics on the results page, but if I go to the page where the pic is, it works fine.

9.04, FF 3.0.10

---

### Post by doas777 on 2009-05-29
> **desperado665 said:**
> I see what he is referring to, when I drag n drop a photo from firefox to my desktop, what I get is a firefox link to the pic instead of the pic itself.

I'm using Jaunty 64 bit with Firefox 3.0.10

well, what looks like an image is actually an hyperlink with an <img> inner tag, or somthing like that. 
if you look at the page source for this thread and look at the avatars (with somthing like firebug), you will note that the avatar is actually an href to the users profile, and uses an image tag to present the link, instead of text. 

since the object you are dragging to the desktop is a link, it logically follows that gnome would save it as ... well ... a link.

for instance if you look at the code for my avatar, it looks like this:
```

<a href="member.php?u=451394">
     <img width="77" height="90" border="0" alt="doas777's Avatar" src="customavatars/avatar451394_3.gif" title="doas777's Avatar"/>
</a>


```however if the image is outside an <a href /> block then it shoudl work.

---

### Post by ad_267 on 2009-05-29
> **doas777 said:**
> well, what looks like an image is actually an hyperlink with an <img> inner tag, or somthing like that. 
if you look at the page source for this thread and look at the avatars (with somthing like firebug), you will note that the avatar is actually an href to the users profile, and uses an image tag to present the link, instead of text. 

since the object you are dragging to the desktop is a link, it logically follows that gnome would save it as ... well ... a link.

for instance if you look at the code for my avatar, it looks like this:
```

<a href="member.php?u=451394">
     <img width="77" height="90" border="0" alt="doas777's Avatar" src="customavatars/avatar451394_3.gif" title="doas777's Avatar"/>
</a>


```

however if the image is outside an <a href /> block then it shoudl work:
try it:
<img width="77" height="90" border="0" alt="doas777's Avatar" src="customavatars/avatar451394_3.gif" title="doas777's Avatar"/>

Exactly, if you drag a link it makes a link. If you drag an image outside of a hyperlink it copies the image into the directory.

---

