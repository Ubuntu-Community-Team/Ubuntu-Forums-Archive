---
title: "Wallpaper Slideshow Help"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by Musick Man on 2009-12-06
Hi, I am using Wallpaper slideshow and it doesnt seem to change pictures. Is there a way that I could it make it change faster?

Thanks,

Musick Man

---

### Post by ranch hand on 2009-12-06
That is run by a script located in /usr/share/backgrounds/cosmos.

You should probably get something other than gedit to try to edit it.  I would use "screem" but I am a noob so there may be something better.
> 
<background>
  <starttime>
    <year>2009</year>
    <month>08</month>
    <day>04</day>
    <hour>00</hour>
    <minute>00</minute>
    <second>00</second>
  </starttime>
<!-- This animation will start at midnight. -->
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/cosmos/cloud.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/cosmos/cloud.jpg</from>
    <to>/usr/share/backgrounds/cosmos/comet.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/cosmos/comet.jpg</file>
  </static>
  <transition>

Jigger around with the <duration>xxxx.xx</duration> numbers.

I have done this with a different screen saver and it works.  With this one it looks like the time measurement for duration is in seconds as it was on the one I modified.  This one uses a different transition than the one I fooled with and I think I would leave it alone (5 seconds isn't that much anyway).

I changed the pictures too.  I just changed the names ot the ones used and left them there and added the ones I wanted with the file names that the old files had.  Worked great and I was to chicken to change the path and file definitions.

I am trying that next time.

---

### Post by Musick Man on 2009-12-06
It worked!!

Thanks Ranch Hand :D

Here is what I did. 

Because the background-1.xml is protected I opened it by typing 

```
gksudo gedit /usr/share/backgrounds/cosmos/background-1.xml

```

into the terminal. 

Then the file opened, and I changed the 

```
<duration>1795.0</duration>
``` 

to

```
 <duration>300.0</duration>
```

The number inside the <duration> tags is seconds, and 1795 is exactly 29 minutes. And I wanted 5 minutes, which is 300 seconds. 

But if you decide to change the times inside the <duration> tags, only change the times on the ones that say

```
<duration>1795.0</duration>
```

Do not change the times to the 

```
<duration>5.0</duration>
```

tags because that is the transition time between each picture. So if you set it to 300 seconds, it would take 5 minutes to change from one picture to another.

Thanks again Ranch hand and hopefully this will help people who want to change it in the future. 

-Musick man

---

### Post by ranch hand on 2009-12-06
Sounds good to me.

FUN too.

---

