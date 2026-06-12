---
title: "Firefox 3.6.3pre Namoroka Doesn't work and I can't remove it"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by WhatTheHell? on 2010-03-25
Ok, here's what's going on.

I had version 3.5.8 and I tried to update to version 3.6.2
Somewhere along the line I ended up with version 3.6.3pre 
It does not play flash
I completely removed it with synaptic
Then, I re-installed firefox through the ubuntu software center
and, WHALA! ...I get Namoroka ...version 3.6.3pre back!

All I want is a stable version of firefox that works.  It was so easy with windows, you just uninstall the version you dont want, then run the installer for the one you do want. I don't even know where to start with this.

---

### Post by FreezWay on 2010-03-25
go to the package in synaptic and see what is under "force version"

---

### Post by WhatTheHell? on 2010-03-25
> **FreezWay said:**
> go to the package in synaptic and see what is under "force version"

Ok.  
Synaptic
I typed in firefox and highlighted it
>package>Force version
There are 4 listings

3.6.3~hg20100324r33787+nobinonly-0ubuntu1~umd~karmic (karmic)
3.6+nobinonly-)ubuntu5~mfs~karmic1 (karmic)
3.5.8+build1+nobinonly-0ubuntu0.9.10.1 (karmic-updates)
3.5.3+build1+nobinonly-0ubuntu6 (karmic)

I selected the second one and clicked force
It then took me back to the main synaptic window, but apply wasn't highlighted, and firefox remained unchecked.

---

### Post by wojox on 2010-03-25
How did you update? Did you add a ppa to your sources.list?

---

### Post by WhatTheHell? on 2010-03-25
> **wojox said:**
> How did you update? Did you add a ppa to your sources.list?

Yes, I'm pretty sure I did 
[COLOR=#000000][FONT=Arial][FONT=Tahoma]sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
[/FONT][/FONT][/COLOR][COLOR=#000000][FONT=Arial][FONT=Tahoma]sudo apt-get update

This is not exactly what I put in, but just an example.  (I dont remember)
And some other stuff.  I don't really know what it was all about, I was just following directions on forums.  I probably did this 5+ times at least.
[/FONT][/FONT][/COLOR]

---

### Post by wojox on 2010-03-25
You need to go into Software Sources > Other Software and remove the ppa's for the mozilla-daily-builds.

---

### Post by WhatTheHell? on 2010-03-25
Problem solved.  Version 3.5.8 restored.

Thanks

---

### Post by wojox on 2010-03-26
Welcome.

---

### Post by ebruzzone on 2010-04-12
Hi. I am having the same problem (why oh why did I have to upgrade FF!!) anyway, before I follow your suggestions I want to make sure that none of my plugins will be deleted (specially my Scrapbook saved pages). 

thanks! 

Eric

---

### Post by ebruzzone on 2010-04-12
fyi I did the process of uninstalling 3.6.3 without loosing anything when reinstalling firefox 3.5 

cheers!

---

### Post by pearsonb on 2010-04-12
I'm having the same problem, I followed the directions above: I went into Software Sources > Other Software and I removed the ppa's for  the mozilla-daily-builds.

But I sill have Namoroka.  Which I guess is my curse for trying to update firefox without understanding what I'm doing.  Anyone know if I'm missing a step or what I need to do to rid myself of Namoroka?

Nvm! I got it.  No more updating firefox for me.

---

