---
title: "Dissappearing/Finding Lost Files In Xubuntu"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by faron45 on 2009-04-18
Okay,darnit ! I've had it ! It's now time I learned how to do this,I suppose.There have been other instances of me losing files I have made within this operating system.And,now,well,what's just happened has taken the cake ! 

 I particularly cannot afford to lose my "to do" lists.Which is why I had decided to use a program that's already on the pc instead of using something online to make one [which was usually the way I went.You see,I may be in danger of losing my internet connection.At least temporarily.Until we can get caught up on the bill.] 

 I had just made a file with the "notepad" program that's on my Xubuntu system,added a few things to it,Titled it "to do",saved it as "to do" to the desktop,and,closed it.Went to the desktop,attempted to open it with a quick left double click & "poof" ! Off it went to never,never land.Where did it go ? Can someone PLEASE teach me how to find files within thiis operating system ? PLEASE !!!???

---

### Post by Elfy on 2009-04-18
I've used find

```
sudo find / -type f -iname *strings* -print
```

replace strings with name/part of name to look for

---

### Post by faron45 on 2009-04-18
Thank you forestpixie.I shall try this.

Well,that didn't work all that well.What I got was...

[sudo] password for bobby: 
find: paths must precede expression
Usage: find [-H] [-L] [-P] [path...] [expression]

---

### Post by bruce2000 on 2009-04-18
Ubuntu comes with a search applet that can be added to a panel, I find it quite handy.
To use it, right click on the top panel, choose "Add to panel..." and select the "Search for files" applet. HTH

Edit: oh you have Xubuntu, I didn't notice sorry. I don't know whether my advice still applies to that version.

---

### Post by Sir Jasper on 2009-04-18
Hi,

Try,
Accessories>Search for Files and type txt into Name Contains and click Find.

alternatively try,

Other>Notepad then click on File then Open a try the most likely folders.

My regards

PS Failing those google xubuntu recover deleted file

---

### Post by faron45 on 2009-04-18
Bruce-My Xubuntu system does not seem to have this little item available.Aaaaaagh !!

 Jas...under "accessories" "search for files" is not available.

Jas-I did indeed find the file with that last little option you proposed.Now,why the heck is it not on the desktop like it's supposed to be ?? Hmmmmmm.I'm betting,that if I were to reboot my pc that all would probably be fine.Hmmmmmmmmmmmm ?

---

### Post by ac_d600 on 2009-04-18
Try looking at your Desktop in Thunar, it may still be there..

---

### Post by faron45 on 2009-04-18
ac_d600 - Thanks for that info my friend.Now,can you explain to me how to do that ? I know,it sounds like a stupid question.But,just for my benefit.Just this once.

---

### Post by ac_d600 on 2009-04-18
I have no idea why it happens.. I just started using xubuntu (been using ubuntu 
for about 6 months) and noticed a couple of times that files I have placed on the desktop just don't show up, very frustrating.. hopefully its fixed in 9.04.

---

