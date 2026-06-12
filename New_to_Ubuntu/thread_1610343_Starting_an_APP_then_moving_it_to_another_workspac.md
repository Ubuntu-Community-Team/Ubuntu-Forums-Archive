---
title: "Starting an APP then moving it to another workspace"
date: 2010-10-31
forum: New to Ubuntu
---

### Post by d58e7 on 2010-10-31
I'm trying to setup TweetDeck so that it either loads up and is moved to another workspace or loads up as a background application.

I tried writing a script but it still loads up on the main workspace

```
/opt/TweetDeck/bin/TweetDeck
wait
wmctrl -r TweetDeck -e 0,2560,0,-1,-1
```

Not sure what I'm doing but does that look right?

---

### Post by migs73 on 2010-10-31
I'm not sure about the rest of the script, but try using sleep instead of wait. You can then put a time after it i.e. sleep 10    
It'll then wait 10secs before carrying on with the script.

---

### Post by TeoBigusGeekus on 2010-10-31
```
wmctrl -l 
```
to find the id of your window, lets say 0x0140008a

Then

```
/opt/TweetDeck/bin/TweetDeck
sleep 5
wmctrl -i -r 0x0140008a -t 1
```

Replace -t 1 with the number of the desktop you want to send your app to.

---

### Post by migs73 on 2010-10-31
Nope it's not that, I just tryed your script with 'sleep' and did nothing (opened file but didn't move it).
Must be the latter part for moving that is wrong, I see if I can find out.

---

### Post by migs73 on 2010-10-31
Thanks TBG I'll give that a try for what I was trying to do.

:)

---

### Post by TeoBigusGeekus on 2010-10-31
Better solution:

Using wmctrl with window id will not be a permanent thing, so
```
wmctrl -l 
```
to find the name your window, say Window
and then
```
/opt/TweetDeck/bin/TweetDeck
sleep 5
wmctrl -r Window -t 1
```

---

### Post by d58e7 on 2010-10-31
Sorry, tried both and still doesn't work. I'm pretty sure I might be doing something wrong. When I created the script I opened GEDIT and entered the information exactly 

```
/opt/TweetDeck/bin/TweetDeck; wmctrl -i -r 0x02200003 -t 2
```

and saved it as TweetDeck and did a chmod +x TweetDeck then set the script in the startup applications. It still loads up in the main workspace instead of the 2nd workspace.

---

### Post by migs73 on 2010-10-31
> **TeoBigusGeekus said:**
> 

to find the name your window, say Window
and then


What window?
I am trying to open then move gRun.... what should I use?

wmctrl -l reports,

```
0x01a0434c -1 dell-laptop N/A
0x02000020  0 dell-laptop x-nautilus-desktop
0x01800004 -1 dell-laptop avant-window-navigator
0x00e000b4  0 dell-laptop [ubuntu] Starting an APP then moving it to another workspace - Ubuntu Forums-Mozilla Firefox
0x04400003  0 dell-laptop gRun 0.9.3
0x02a000a4 -1 dell-laptop awn-applet

```

Many thanks

---

### Post by d58e7 on 2010-10-31
> **migs73 said:**
> What window?
I am trying to open then move gRun.... what should I use?

wmctrl -l reports,

```
0x01a0434c -1 dell-laptop N/A
0x02000020  0 dell-laptop x-nautilus-desktop
0x01800004 -1 dell-laptop avant-window-navigator
0x00e000b4  0 dell-laptop [ubuntu] Starting an APP then moving it to another workspace - Ubuntu Forums-Mozilla Firefox
0x04400003  0 dell-laptop gRun 0.9.3
0x02a000a4 -1 dell-laptop awn-applet

```

Many thanks

I think in that case it would be 0x04400003, edit NVM I think it would be gRun

---

### Post by migs73 on 2010-10-31
TBG's last post stated that using the window ID wouldn't be a permanent fix (I assume the window ID is not necessarily static).

EDIT Not that it worked with the window ID anyway!!   :)

---

### Post by d58e7 on 2010-10-31
Yep didn't notice that post before making my reply, but I just tried the newer script posted and still no luck 

> /opt/TweetDeck/bin/TweetDeck
sleep 5
wmctrl -r TweetDeck -t 2

---

### Post by migs73 on 2010-10-31
I had compiz running as my WM which isn't supported (according to the wmctrl website). Disabled it and tried again but still nothing.
Tried using the name reported by wmctrl (gRun 0.9.3) but that doesn't work either.

---

### Post by d58e7 on 2010-10-31
I tried a more controlled run.

After my OS started I loaded TweetDeck manually and then did > wmctrl -r TweetDeck -t 2 and that worked like it should but for whatever reason it doesn't like doing it from the script. I'm guessing it runs TweetDeck which starts the application and then it doesn't continue to the next steps > sleep 5
wmctrl -r TweetDeck -t 2 

---

### Post by migs73 on 2010-10-31
DOH!!! Got it working,

```
**#!/bin/sh**
grun
sleep 5
wmctrl -r grun -t 2
```

forgot to tell it to run in a shell!!!

NB desktop 2 is number 3 as wmctrl starts its count at 0.

BTW  I have tried with another app open on desktop 0 but then the app doesn't move? Without any other app open it moves every time. d58e7 shouldn't be a problem for you if you are adding it to the start up.

---

### Post by d58e7 on 2010-10-31
Is that all that would appear in the script or does it require a line for closing it? I'm still not able to get it to go beyond loading TweetDeck, I ran the script manually and it loads TweetDeck and then never moves onto the next steps and then ends up never moving to Workspace 2. Based off your post  the script looks exactly like this right now

> #!/bin/sh
/opt/TweetDeck/bin/TweetDeck;
sleep 5
wmctrl -r TweetDeck -t 1

and right now firefox is running on Workspace 1 and this fails to load in workspace 2

---

### Post by migs73 on 2010-10-31
I mentioned in my edit at the bottom, that if you have any other app open it doesn't move. Close all your apps then run the script again, see if it works. Why it doesn't work with any other app running , I am afraid I don't know. But were getting closer!


EDIT  Just noticed the script you show above has a ';' after the second line. I don't know if it is a typo on posting or if it is in your script, what it will do. When you write it in Gedit the 'sleep' should change colour (go red)to show it is a recognised command

---

### Post by d58e7 on 2010-10-31
That was a typo, but just tried again with everything closed still no luck.

Is wmctrl the only way to move an application to another workspace when it starts up?

---

### Post by migs73 on 2010-10-31
I'm not sure. Mine has started to only work intermittently now :(
I need to leave it for a while, hope you find a solution soon.

Mike

---

### Post by TeoBigusGeekus on 2010-10-31
As a last resort, you could try
```
wmctrl -s 1
/opt/TweetDeck/bin/TweetDeck &
sleep 5
wmctrl -s 0
```




**[SIZE="2"]EDIT:[/SIZE]**
I've found it.

```
/opt/TweetDeck/bin/TweetDeck &
sleep 5
wmctrl -r TweetDeck -t 1
```

---

### Post by d58e7 on 2010-10-31
> **TeoBigusGeekus said:**
> As a last resort, you could try
```
wmctrl -s 1
/opt/TweetDeck/bin/TweetDeck &
sleep 5
wmctrl -s 0
```




**[SIZE="2"]EDIT:[/SIZE]**
I've found it.

```
/opt/TweetDeck/bin/TweetDeck &
sleep 5
wmctrl -r TweetDeck -t 1
```

I'm sorry to say it but it still didn't work.

---

### Post by TeoBigusGeekus on 2010-10-31
Ok, launch TweetDeck and post the output of 
```
wmctrl -l
```

---

### Post by d58e7 on 2010-10-31
> **TeoBigusGeekus said:**
> Ok, launch TweetDeck and post the output of 
```
wmctrl -l
```

0x01000003 -1 Bottom Expanded Edge Panel
0x01000027  0 Top Expanded Edge Panel
0x0120001d  0 x-nautilus-desktop
0x02c00078  0 Facebook
0x02600003  0 TweetDeck
0x03a0007d  0 [ubuntu] Starting an APP then moving it to another workspace - Page 3 - Ubuntu Forums - Mozilla Firefox
0x03a00a48  0 Library

---

### Post by TeoBigusGeekus on 2010-10-31
```
/opt/TweetDeck/bin/TweetDeck &
sleep 5
wmctrl -r TweetDeck -t 1 -v
```

Add the -v option to the wmctrl command in the script, launch it and post the messages.

---

### Post by d58e7 on 2010-10-31
Unfortunately it didn't return anything

---

### Post by migs73 on 2010-11-01
TBG thanks, that worked for me.
d58e7 what window manager are you using? Just tested it and it doesn't work with Compiz.

---

### Post by Elfy on 2010-11-01
or use devilspie (unless I've got the wrong end of the stick here - I am still half asleep)

[https://help.ubuntu.com/community/Devilspie](https://help.ubuntu.com/community/Devilspie)

---

### Post by migs73 on 2010-11-01
> **forestpiskie said:**
> or use devilspie (unless I've got the wrong end of the stick here - I am still half asleep)

[https://help.ubuntu.com/community/Devilspie](https://help.ubuntu.com/community/Devilspie)

I saw that last night and on this site, [http://live.gnome.org/DevilsPie](http://live.gnome.org/DevilsPie) where it is described as,

"A totally crack-ridden program for freaks and weirdos who want precise control over what windows do when they appear"

Wasn't exactly sure that was me!

I'll give it a try if it will work with compiz.

---

### Post by Elfy on 2010-11-01
Nope - won't work with compiz. There's a place windows plugin in ccsm that achieves the same thing though.

---

### Post by migs73 on 2010-11-01
> **forestpiskie said:**
> Nope - won't work with compiz. There's a place windows plugin in ccsm that achieves the same thing though.

Lol... Just tried that and it worked (after I had worked out what to do in CCSM, it is always very unfriendly to me...) UNTIL I shut down the app that was moved.....then my awn dock disappeared (I don't have any gnome panels). Brought up a terminal and did a shutdown...... then got a black (backlit screen) with computer hung!!!

I think I'll just live with moving stuff. Don't need to do it very often, but looked like a challenge for my new attempts at scripting. :(

---

### Post by Elfy on 2010-11-01
I find sticking my tongue out at compiz to work out best for me - then I just use metacity compositing if I need it ...

---

### Post by TeoBigusGeekus on 2010-11-01
> **forestpiskie said:**
> I find sticking my tongue out at compiz to work out best for me - then I just use metacity compositing if I need it ...

I don't use any compositing, maybe that's why it worked for me.

---

### Post by Elfy on 2010-11-01
The scripty stuff I assume - I know devilspie works with metacity compositing.

---

### Post by migs73 on 2010-11-01
> **forestpiskie said:**
> The scripty stuff I assume - I know devilspie works with metacity compositing.

Yes the "scripty stuff" worked for me with compiz off too.

---

### Post by Elfy on 2010-11-01
Did the OP have compositing off then? Anyway - I shall unsubcribe now I think :)

---

### Post by migs73 on 2010-11-01
> **forestpiskie said:**
> Did the OP have compositing off then? Anyway - I shall unsubcribe now I think :) 

Not sure but I made him aware of the conflict a couple of pages ago.

---

### Post by TeoBigusGeekus on 2010-11-01
> **forestpiskie said:**
> The scripty stuff I assume - I know devilspie works with metacity compositing.

Yep.

---

