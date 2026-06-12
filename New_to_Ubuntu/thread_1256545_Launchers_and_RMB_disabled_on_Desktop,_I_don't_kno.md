---
title: "Launchers and RMB disabled on Desktop, I don't know how!!"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by imilio123123 on 2009-09-02
Hi everyone,

I just installed ubuntu 9.04, the version for Dell, after having the Windows XP installed... I got partitions for each, first windows, then archives and finally ubuntu. 

The thing is that at first I could not find the partition "archives", and then I found it, it was on    /archives    , (so dumm, but I am completely new to ubuntu) so I decided to make a launcher on desktop, it worked. On the desktop I the had two launchers, one for archives and a launcher to the windows partition, that was already there, and which I wanted to rename, _when I renamed the launcher to windows my desktop was cleaned out!_ nothing else on it!!:confused:  

I stilled looking and on the root     /home/comp_name/Desktop   I found the launcher  (only the "archives" one, not the renamed "windows"). 
The thing is that I know where is the launcher now, but it is not on the "real desktop", it is only on the "Desktop folder".....

And also after this happend I found out that I couldn't right mouse click on the "real desktop"...     [actually I don't really know if it is possible to RMC on desktop, but I suppose so, I am completely new with Ubuntu...]

I'm sure this is completely easy to solve by someone who knows a bit Ubuntu, because I keep looking and couldn't find any answer.

Thankyou all

---

### Post by NoaHall on 2009-09-02
Don't look in the root home, look in your own. Also, try mounting the drive ( Places -> NameOfDrive)

---

### Post by imilio123123 on 2009-09-02
I have forgotten to say that, I haven't restarted my computer yet, maybe ubuntu is a little bit like windows in that way ;-)  [many problems get solved when you restart on windows]

---

### Post by imilio123123 on 2009-09-02
first of all... what do you mean by "look in your own"... my own what? (I am complete noob, sorry I make you nervous)

in "Places" I haven't got this partition, I can only see the "Computer" and the "windows" partition, and when I enter "Computer" I only see the DVD player, "windows" partition and "filesystem"

[another thing, how did you answer so fast to my first post?]

---

### Post by NoaHall on 2009-09-02
I mean go to Places -> Desktop (that will be your own)
Your problem is you can't access the windows partition or that you can't see the launcher on the desktop?

For launcher -

Okay , open a terminal ( Applications -> Accessories -> Terminal)
And type "killall nautilus"
After that, type "nautilus" - problem solved.

For can't access windows partition -

Double click on windows under computer

---

### Post by imilio123123 on 2009-09-02
thanks, that was the answer I was looking for. It's great having such a fast solution

---

