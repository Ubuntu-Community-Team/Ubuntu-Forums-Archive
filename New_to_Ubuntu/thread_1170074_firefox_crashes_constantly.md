---
title: "firefox crashes constantly"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by Matt26 on 2009-05-25
for some reason firefox crashes constantly on my system- something in the area of every half hour to an hour... it just closes unexpectedly and without warning, then i have to start it again.

i have had this issue in the past and it was suggested that compiz could be causing the issue, so i set my System/Preferences/Appearance settings back to None and it continues to happen.

since upgrading to 9.04 firefox didn't crash nearly as much, but lately it's been noticeably worse.

any help would be greatly appreciated.

---

### Post by sandyd on 2009-05-25
first question.

run 
```

top

```is xorg and firefox gobbling up ram?

second question

plan a night out with your gf/bf or whatever.
before leaving, open up a terminal, type in
```

firefox
```randomly visit 2-3 pages and get outta there.

if you come back and firefox has vanished from your screen... well...see if you can post the terminal output right from the second where you typed in firefox and hit enter. 

if you come back and firefox still hasn't crashed... well...

type in 
```

firefox

```in the terminal
and use it until it crashes.

Then post the output of the terminal

---

### Post by albinootje on 2009-05-25
> **Matt26 said:**
>  since upgrading to 9.04 firefox didn't crash nearly as much, but lately it's been noticeably worse.


Are you using various different Firefox addons ?
Does it crash while using flash, or sound ?

Can you try, and test running Firefox without the addons activated ?
```

firefox -safe-mode

```

---

### Post by superprash2003 on 2009-05-26
i've been facing issues as well , trying out things myself , im disabling each and every addon individually to see where the problem see , right now flash is disabled , java is on , so far so good , 2 days over :)

---

### Post by Matt26 on 2009-05-27
> **carlee said:**
> first question.

run 
```

top

```is xorg and firefox gobbling up ram?

second question

plan a night out with your gf/bf or whatever.
before leaving, open up a terminal, type in
```

firefox
```randomly visit 2-3 pages and get outta there.

if you come back and firefox has vanished from your screen... well...see if you can post the terminal output right from the second where you typed in firefox and hit enter. 

if you come back and firefox still hasn't crashed... well...

type in 
```

firefox

```in the terminal
and use it until it crashes.

Then post the output of the terminal

it doesn't appear that either xorg or firefox are taking up that much RAM- no more than usual anyways.

and the only thing that the terminal window outputs when firefox crashes is Segmentation fault- what does that mean?

as suggested here, i think that flash may be part of the issue- i do have sites open that are running flash so maybe i can try closing them down and then i'll see what happens after that...

---

### Post by sandyd on 2009-05-28
well, if its flash, ill take a stab in the dark and cliam this to be the problem

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/253800](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/253800)

---

### Post by fatality_uk on 2009-05-28
What are your system specs?
I would also suggest flash as a possible culprit. I does eat ram sometimes

---

### Post by dunkirk on 2009-05-31
This describes what I'm seeing perfectly. I REMOVED all traces of Flash, and it still gets locked up and crashes. Sometimes it even dumps me back out to the login screen.

Considering that a netbook is overwhelmingly used for just running a browser, I'm terribly unimpressed with this particular bug on my Asus Eee. What kills me is that EVERYthing else runs like a TOP.

---

### Post by martini1179 on 2009-06-01
> **dunkirk said:**
> This describes what I'm seeing perfectly. I REMOVED all traces of Flash, and it still gets locked up and crashes. Sometimes it even dumps me back out to the login screen.


Honestly, I think you have a different problem. The OP didn't mention anything about his Firefox getting "locked up" and certainly not dumping him back to the login screen.

---

### Post by martini1179 on 2009-06-01
> **superprash2003 said:**
> i've been facing issues as well , trying out things myself , im disabling each and every addon individually to see where the problem see , right now flash is disabled , java is on , so far so good , 2 days over :)

I seem to have the same problem as both of you. What addons do you have installed?

---

### Post by philinux on 2009-06-01
Run firefox from the terminal and post any errors reported.

---

### Post by robert shearer on 2009-06-01
> dunkirk;7379047]This describes what I'm seeing perfectly. I REMOVED all traces of Flash, and it still gets locked up and crashes. Sometimes it even dumps me back out to the login screen.

since about a week ago the same has been happening on my Debian Lenny install.
Firefox closes and occasionally drops me back to the login screen.
I am running a Pentium 3 desktop machine with 512Mb ram and it has performed ok until recently.I suppose it is some update or has Firefox increased its ram usage.??

I have found that by dropping caches prior to opening Firefox the problem is reduced if not removed altogether. Note to self- must try Lenny some more.

Any way, dropping caches here....
[http://www.timesys.com/blogs/joseph/freememory](http://www.timesys.com/blogs/joseph/freememory)

and don't forget to sync first.

Edit  posting this from my mepis machine but I think the code for Ubuntu would be...

```
sudo sync ; echo 3 > /proc/sys/vm/drop_caches
```

run ```
free
``` before and after to see the effect.

---

