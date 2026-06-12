---
title: "Remote desktop picture problem"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by AlanR8 on 2008-11-07
I've upgraded all my machines to 8.10, please note KUBUNTU. I've got a "server" that is headless in that it has no keyboard, monitor and mouse and the arrangement has always worked fine under Hardy.

Last night I upgraded the "server" and set up the remote desktop using KRFB on the "server" and access it with KRDC from the "clients". After a few minutes of fiddling I had the show on the road!

However, whilst I can connect, the remote window graphics break up into coloured boxes. With a little patience I can get what I want done but how can I solve this?

I've just tested the remote desktop from a Windows XP box running Tight VNC and get the same result.

I've attached a screen shot below.

---

### Post by AlanR8 on 2008-11-08
Bumpity BUMP!!

---

### Post by AlanR8 on 2008-11-13
Come on guys.......someone must have an answer to this issue! Is it something to do with the plasma desktop in KDE 4.1.*?

Help me out here. :):)

---

### Post by brexsis on 2008-12-04
i have similar problem too, i can use vnc (i tried many configurations and 3 versions) or KRDC - result very similar. only in my case there are a few misplaced desktop parts, and i only see the desktop picture. i can do anything, but in my remote deskopt client i cant see what i doo - all time the first deskop picture, on server things happen, but on my client i can`t see anything what i am doing, because all the time the desktop picture doesnt change.example -  if i press mouse2 button on desktop, on my server machine menu opens, but on my client nothing happen, picture doesnt change :(

video nvidia 6600gt AGP, restricted nvidia drivers enabled, i am using compiz too.

kubuntu 8.10, kde4.1, 64bit

---

### Post by AlanR8 on 2008-12-04
We need some help here guys.......

---

### Post by brexsis on 2008-12-09
anyone? maybe some link to bug or smthng?

---

### Post by brexsis on 2008-12-28
bump-purum-pum-pum...

anyone?...

---

### Post by AlanR8 on 2009-02-01
And again.

BUMP BUMP BUMP.......please:p

---

### Post by AlanR8 on 2009-03-06
Now this is beginning to p**s me off big time!

Now running KUBUNTU (please note) 4.2.1 on the server and the client machines and am still having the same issues.

Can somebody PLEASE come up with a solution!!!!!!!

HELP!!!!

---

### Post by metro2003 on 2009-04-03
BUMP !

wooow...we have some REAL winners here helping out the nubies !! 

i'm actually having the same EXACT problem and I have no clue how to fix it...I tried everything from re-installing to actually rebuilding the box..seriously...

so now when I have to do something on my server, I have to stand on my washmashine in my basement cuz I can't get this simple remote desktop to work!!! when instead I can just sit in my comfortable chair in my bedroom...sorry if I sound a bit frustrated.

for some reason I NEVER had an issue with <oh ohhh> Windows Remote Desktop Connection in a windows network...that thing just seemed to gel just fine !!

yeah...come on guys/gals !!! some HELP IS NEEDED here..

thanks !!

info:
my server: Kubuntu 8.10 32 bit all pached up. AMD proc.
remote comp: yep, a real winner here: Windows Vista 32 bit.

---

### Post by Aristide on 2009-04-05
I'm facing the same problem here though in one direction.
From pc A to pc B it works fine, but not vice versa. The computer with the best graphic card can take over the one with lower resolution. The other way around, it's an unusable mess.
I found a thread about the problem here :
[http://forum.kde.org/kde4-looks-awful-over-vnc-t-16651.html](http://forum.kde.org/kde4-looks-awful-over-vnc-t-16651.html)
and threads here and there from people with the same problem.
Couldn't solve my problem so far. I tried using NX from [www.nomachine.com](www.nomachine.com) but couldn't get it working.

---

### Post by marksthespot on 2009-04-16
Also seeing this issue.


GeForce 9500 GT

I do have TV out enabled.  Does anyone else?

Previously I connected and just saw the boxes and couldn't move the mouse or anything.  Just coloured boxes.

I disabled Desktop Effects in System Settings -> Desktop -> Enable Desktop Effects.

I could then see my Desktop, however I can't see the mouse.  I can see when it is hovered over something, but not the actual mouse arrow.

This is a fresh install of Kubuntu 8.10.

Any help or suggestions would be appreciated.  Seems like there is a few of us out here.

---

### Post by marksthespot on 2009-04-21
See Screen shot. Same as original post'ers issue.

---

### Post by Nova5555 on 2009-06-15
Any update to this issue? I'll probably just go ahead and install another vnc server tonight but it would be nice to know more about this problem...

---

### Post by AlanR8 on 2009-08-16
Never did solve this in Kubuntu but swapped over to the Gnome desktop environment on the "server" and client and job sorted.

---

