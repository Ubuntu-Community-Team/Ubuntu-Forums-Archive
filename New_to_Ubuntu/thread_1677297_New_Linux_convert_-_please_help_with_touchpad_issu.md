---
title: "New Linux convert - please help with touchpad issues"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by omniwing on 2011-01-28
So I recently switch my HP mini 5103 to Xubuntu linux 10.10 and I really like it. It took me a while to get my touchpad working with features like two finger scrolling. Finally, I found the "latest synaptics drivers" (Synaptics is the name of the touchpad company, not to be confused to "synaptic package manager"). 

Anyway, here is the problem. My 'right click' on my touchpad actually left clicks instead. In order to 'right click' on something, I have to left click on it, hold in left click, then tap the middle of my touchpad. This is ineffective and I really need to learn how to just set my touchpad how it used to be..

If I had to speculate, I need some kind of setting to allow me to map the buttons on my touchpad correctly. I would prefer to be able to simulate a middle mouse button as well, but that is just extra - really I am interested in just getting my right touchpad button to mean 'right click'! 

I've downloaded like 5 different 'touchpad configuration' packages and none of them do this. All of them are like 'double tap speed' and other useless settings that have nothing to do with me being able to right click on stuff.

Please advise.

---

### Post by mharrison on 2011-01-28
Check out [http://www.unicom.com/blog/entry/300](http://www.unicom.com/blog/entry/300)

Careful as the article is actually about switching the mouse for left handed people.

Basically it looks like you want to run
```
xmodmap -pp
```
as a user and make sure the numbers line up...

1 to 1
2 to 2
3 to 3
and so on.

If they don't run 
```
xmodmap -e "pointer = 1 2 3 4 5"
```

HTH

---

### Post by omniwing on 2011-01-28
my xmod -pp shows my values are all lined up. 

What I learned from that article is synclient -l shows me a long list of values and numbers. I'd paste it here but I don't know how to select text in my xterm. 

How can I configure these values? Is there a list of what these values are when the HP mini came from HP? The touchpad worked a lot better then, even with things like pointing on stuff (my fingers seem to nudge/drift the cursor, it was more precise when the HP had stock windows on it)

---

### Post by mharrison on 2011-01-28
This is a bit beyond me as I don't use a touchpad but you might read through [http://ubuntuforums.org/showthread.php?t=1401645](http://ubuntuforums.org/showthread.php?t=1401645)

---

### Post by omniwing on 2011-01-28
from further studying synclient -l I figured out that 'tapping' my right bottom touchpad button DOES in fact right click. Now I need to figure out how to do it if I hold it in. 

RTCornerButton =2
RBCornerButton=3
LTCornerButton=0
LBCornerButton=0
TapButton1=1
TapButton2=2
TapButton3=3


But there are like 100 other variables on this list, basically I need help understanding and configuring this. (Not just the above 7 variables but all of them)

---

### Post by omniwing on 2011-01-28
> **mharrison said:**
> This is a bit beyond me as I don't use a touchpad but you might read through [http://ubuntuforums.org/showthread.php?t=1401645](http://ubuntuforums.org/showthread.php?t=1401645)


This seems to be what I need, ty for your reply

---

