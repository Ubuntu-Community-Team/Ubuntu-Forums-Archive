---
title: "Streamin Music to my Nintendo DS"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by Bolleke on 2008-05-03
I found an application to stream music from WinAMP to my DS, but since I don't use Windows at home, I can't use WinAMP. The program works with a small WinAMP Plugin(a dll file) and a .nds rom file for the DS. I was wondering if there was another way to use the plugin(or maybe not use the plugin at all) so it would work on another application like RythmBox or something.

Information on the program SylphAMP can be found here:
[http://www.sylphds.net/ev2/contentview.php?id=461](http://www.sylphds.net/ev2/contentview.php?id=461)

ps: this is my first thread ever, sorry if it's in the wrong section!
I'm assuming this is the right one, since it's about streaming music via the network

---

### Post by SpaceTeddy on 2008-05-04
i am using the Winamp DSP plugin for streaming to a shoutcast server. Since the DSP is not really supported in Ubuntu, and all the replacements suck hard in quality, i simply installed wine and then started winamp in ubuntu from there. it's quite easy, acctually.

first, install wine via this command:
```
sudo apt-get install wine
```

then go and download winamp as you usually would. place the exe file on your desktop, right-click on it and say "star with wine".

that should take you through your normal setup, and leave you (at the end) with a new menu item called wine where you will find (in some subfolders) the winamp start button. it takes a while until it loads, but it works flawlessly for me.

i know this is not "a real solution" but only a work around... 
but i hope it works anyway :)

---

### Post by Bolleke on 2008-05-04
Yeah, I read something about installing wine. I'll give it a shot, but I'm just affraid that the plugin isn't gonna work decently.

Thanks and I'll let you know if it worked!

---

### Post by Bolleke on 2008-05-04
Winamp doesn't seem to work under Wine... But I was kind off hoping that someone else was using this program too and could maybe help me out by giving me another program that streams music through the network(and that Sylpamp could recognize)

---

### Post by SpaceTeddy on 2008-05-04
mhm - strange, it does for me. Nevermind tho.

but here are a few things i have found usefull when streaming to shoutcast servers (they had poor quality back then to - i don't know why)

first, there is [[COLOR="Blue"]icecast[/COLOR]]("http://www.icecast.org/")

i never got icecast to work properly tho... but it should be in the respositories (only tried to use it on debian etch)

hope this helps :)

---

### Post by Bolleke on 2008-05-04
Maybe it's the version of WinAMP I'm using that doesn't work in Wine. Which one are you using?

The problem is that SylphAMP doesn't just play the music which WinAMP sends out, it also gives you control over the playlist etc(it's a really cool program!) So I'm not sure if it's gonna work with any stream. 

I'm gonna give icecast a shot though.

---

### Post by SpaceTeddy on 2008-05-04
attached is a screenshot of my winamp running in ubuntu (gnome) with compiz enabled. Also loaded is the DSP Plugin for streaming music to a shoutcast server. 

i must say - i did not install the windows on my computer. I have a second partiton with windows on it (for games) which has winamp installed. I just went into the Progamms/winamp folder, right clicked on the winamp exe and started it. 

cheers :)

---

### Post by Bolleke on 2008-05-04
I've got a Windows partition too(for schoolwork). I never use it at home though(it's rather slow and I don't feel like formatting). I'm gonna install it over there now. I'll let you know if it works

Thanks for all the feedback!

---

### Post by Bolleke on 2008-05-04
I installed it in Windows and it works over there. When I start it in Ubuntu 2 items appear on my window selecter panel, but then they just close again after 4 seconds or so. I don't even get a real window :(
The 2 items on the panel are Winamp Equaliser(with a winamp thubmnail in front of it) and one with the text "untitled window".

---

### Post by Bolleke on 2008-05-04
I downloaded WinAMP lite and now it works!
Thanks a lot!

---

