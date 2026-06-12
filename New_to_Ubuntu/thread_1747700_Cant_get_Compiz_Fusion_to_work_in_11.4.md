---
title: "Cant get Compiz Fusion to work in 11.4?"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by Ashley04 on 2011-05-02
[B][COLOR=Purple][SIZE=2]Hello All,

just started using Ubuntu about a month or 2 ago & was using 10.10 & got compiz fusion working great on my Netbook(eee PC) i had all the window stuff working for opening, closing, minimizing. I just upgraded to 11.4 last week & installed compiz fusion & have tried to set it up again on here to get the cool effects for opening, closing, & minimizing windows, but cant seem to get it to work? Not sure what im doing wrong? is there a new version your suppose to get for 11.4? 
i downloaded the fusion from the synaptic package like i did with 10.10
can anyone help me with this?
thanks! :D
[/SIZE][/COLOR][/B]

---

### Post by RoflHaxBbq on 2011-05-03
```
compiz --replace
```

---

### Post by treasonvoice on 2011-05-03
11.04 actually has compizfusion enabled by default. Perhaps you wanted to know how to get emerald to work? Not that I know how to do that in Natty, but I just thought you might want to rephrase your question.

---

### Post by Ashley04 on 2011-05-03
[SIZE=2][COLOR=Purple][B]what is emerald? 
i just wanted to get my effects working for opening, closing, etc. windows.
i was using the fire & razor effects for opening & closing windows.
i actually posted a youtube video on what i did on my 10.10 here is the link to it..
this is what i would like to be able to do again here on 11.4....

[http://www.youtube.com/watch?v=8OGCEqHcb6U&feature=channel_video_title](http://www.youtube.com/watch?v=8OGCEqHcb6U&feature=channel_video_title)
[/B][/COLOR][/SIZE]

---

### Post by treasonvoice on 2011-05-03
> **Ashley04 said:**
> [SIZE=2][COLOR=Purple][B]what is emerald? 
i just wanted to get my effects working for opening, closing, etc. windows.
i was using the fire & razor effects for opening & closing windows.
i actually posted a youtube video on what i did on my 10.10 here is the link to it..
this is what i would like to be able to do again here on 11.4....

[http://www.youtube.com/watch?v=8OGCEqHcb6U&feature=channel_video_title](http://www.youtube.com/watch?v=8OGCEqHcb6U&feature=channel_video_title)
[/B][/COLOR][/SIZE]

Sorry, was just me being stupid apparently. Emerald is a different window decorator that you can use to get transparent window borders and customizable toolbar layouts etc. Was very cool but because of some issues (which are compizfusion related), it doesn't seem to work in natty. It worked with compizfusion to create a really good looking desktop.

Anyway, compizfusion is SUPPOSED to be enabled in natty by default, but there seems to be too many clashes with the unity plugin settings when you try and enable the fire and raindrop effects. I know what you're referring to. Hopefully the folks doing compiz can try and sort out compatibility issues.

I think that until you figure it out, you'll just have to use the standard settings. Sorry.

---

### Post by Ashley04 on 2011-05-03
[SIZE=2][B][COLOR=Purple]thats ok. thanks for trying to help, very much appreciated :)
i guess i will just keep reading up to see if anyone else is having this problem.
maybe it will get fixed. Ive just been trying to get it to work through doing..
Compiz Config > Effects > Animations. 
If anyone else got this to work on 11.4 let me know :)
[/COLOR][/B][/SIZE]

---

### Post by Keffr3n on 2011-05-31
I think Canonical is trying to get us to use Slakware or worse... Windows. What's this $#%$# called Unity? And no compiz?? God, I'm going back to 10.10.

P.S. Emerald not working here either.

---

### Post by wildmanne39 on 2011-05-31
> **Keffr3n said:**
> I think Canonical is trying to get us to use Slakware or worse... Windows. What's this $#%$# called Unity? And no compiz?? God, I'm going back to 10.10.

P.S. Emerald not working here either.
Hi, I have the cube and all effect working perfectly.

---

### Post by garvinrick4 on 2011-05-31
Check to see if your machine is 3d capable before:
```
/usr/lib/nux/unity_support_test -p
```

---

### Post by garvinrick4 on 2011-05-31
Install ccsm if you have not: click on screenshot of Ubuntu software center:

---

