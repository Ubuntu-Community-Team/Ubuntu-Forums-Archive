---
title: "getting an error when trying to install nvidia drivers + creative sound"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by HamHamT on 2009-01-02
i just installed the latest ubuntu about like an hour ago and have been messing around with it but i have two problems that are really holding me back, and ive searched around but cant make much of the linux commands and what not

first off with my nvidia drivers

when i just finished installing, ubuntu lets me know something about my nvidia driver to get it going, so i click through it and everytime i try to activate it i get the following error:

```
SystemError: Failed to lock /var/cache/apt/archives/lock
```

have no idea what it means or what im supposed to do to fix it

(i searched around the forums but didnt really find anything that applied to me, sorry if this is a common problem)




the second problem i'm having is that im getting this sort of hissing sound from my speakers 

i use a creative audigy 2 sound card (heard that theres been problems with this driver but its recently been fixed with something called an alsa driver)

the only problem is that i dont know how to install this alsa driver or where to get it


i know im completely new to this but bear with me, this OS looks very promising and hope to become very involved in the community

thanks for your help in advance!:popcorn:

---

### Post by Tim Sharitt on 2009-01-02
I'm not real sure with your first problem, sound like maybe you have another package manager open (i.e synapic, Add/Remove).

To get your sound working goto System > Preferences > Sound on the top menu bar. There are differnt pulldown menus for Sound Events and Music and Movies that are set to auto detect. Change these to ALSA. That should solve your sound problem.

---

### Post by HamHamT on 2009-01-02
so i've fixed the first error by completing the needed updates, once that was done i was easily able to update my nvidia driver no problem

the only problem im having now is the whole no-sound thing

---

### Post by Michael.Godawski on 2009-01-02
Concerning your first issue see here: 


[LIST]
[*][http://ubuntuforums.org/showthread.php?t=391742&highlight=11+Resource+temporarily+unavailable](http://ubuntuforums.org/showthread.php?t=391742&highlight=11+Resource+temporarily+unavailable)
[/LIST]

---

### Post by HamHamT on 2009-01-02
hey tom, theres a bunch of options i have that regard to alsa, could you possibly narrow it down?

[IMG]http://i44.tinypic.com/2mxons7.png[/IMG]

(p.s. i just love that dedicated screenshot taker its so convinenint)

---

### Post by Michael.Godawski on 2009-01-02
When you click one of these entries and click on the Test button do you hear any sound?

And if you change the entry does the test sound disappear?

---

### Post by Tim Sharitt on 2009-01-02
I would say one of the first two audigy options. Or test a few and se what works best. I only have five options and just one alsa, so I guess my answer did seem kinda vague :).

---

### Post by HamHamT on 2009-01-02
theres some where i get

[IMG]http://i43.tinypic.com/2uh3i1t.png[/IMG]

and the hissing either stays the same or gets higher 

or ill get 
[IMG]http://i39.tinypic.com/6ftqb5.png[/IMG]


edit:
ive tried ubuntu in the past (version 7 i believe when it just came out) and stopped using it for this same reason
ive just heard that theres been a patch or support for creative drivers recently

it has something to do with creative drivers in specific (anyone else usin g one?)

---

