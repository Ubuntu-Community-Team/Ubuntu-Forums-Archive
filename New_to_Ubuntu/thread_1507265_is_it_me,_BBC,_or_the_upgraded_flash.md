---
title: "is it me, BBC, or the upgraded flash?"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by the.phantom on 2010-06-11
i did the upgrade to adobe flash (10.1) on 10.4
and can't watch flash on bbc
and in windows it won't work(xp)
voutube seems to work

all are 32 bit

i fired up my old Ubuntu 7.10 and works fine


anyone else having troubles with the new version on bbc news?

or just me?

---

### Post by tom.swartz07 on 2010-06-11
> **the.phantom said:**
> i did the upgrade to adobe flash (10.1) on 10.4
and can't watch flash on bbc
and in windows it won't work(xp)
voutube seems to work

all are 32 bit

i fired up my old Ubuntu 7.10 and works fine


anyone else having troubles with the new version on bbc news?

or just me?

Type 
```
about:plugins
```
into the address bar on both, see what versions and build numbers you have. Post em back here.

---

### Post by the.phantom on 2010-06-11
> Shockwave Flash

    File: libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r53

on both the 10.4 systems

and neither will show any f the flash of BBC news main page

i tried to uninstall and installed the free flashplayer and no work either

on 7.10 it works fine and it is 10.0.R45

and windows (xp) 10.1.R53 and doesn't load either

can (if you updated from the official Ubuntu repositories with update manager)check and see if 
[http://news.bbc.co.uk/](http://news.bbc.co.uk/)
and just click 1 min news at the top
does it play
or any of the flash 1/2 way down the page?

thanks

---

### Post by tom.swartz07 on 2010-06-11
> **the.phantom said:**
> on both the 10.4 systems

and neither will show any f the flash of BBC news main page

i tried to uninstall and installed the free flashplayer and no work either

on 7.10 it works fine and it is 10.0.R45

and windows (xp) 10.1.R53 and doesn't load either

can (if you updated from the official Ubuntu repositories with update manager)check and see if 
[http://news.bbc.co.uk/](http://news.bbc.co.uk/)
and just click 1 min news at the top
does it play
or any of the flash 1/2 way down the page?

thanks

Thats the version I have and the video works for me..

Do you have Ubuntu x64 or 32 bit installed?

---

### Post by mkvnmtr on 2010-06-11
I am hearing that linux 64 bit does not work and Adobe does not want to talk about it.

---

### Post by the.phantom on 2010-06-11
all are 32 bit as i said in first post
strange and to have windows do the "same thing?
 i run "noscript" and "adblock plus and disabled both with the same results

i will get the spinning circle and then see i stop downloading anything

on bbc they have some audio using flash and that works
just get the spinning circle then the pic and then stops downloading


and all systems pass the flash player test

and it appears to be just with BBC!!!
i ran several flash sites and even cnn news and all work, just not BBC?
(on all systems)

even uninstalled and reinstalled the flash player on one system

---

### Post by migs73 on 2010-06-11
Try this

[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

I had problems with flash (ITV Player) and it worked for me!  :p

PS Just checked iplayer (have'nt used it since 10.04) and it works fine too

---

### Post by kelvin spratt on 2010-06-11
I think its the BBC that is having probs.

---

### Post by the.phantom on 2010-06-11
well the Ubuntu 7.10 worked good this morning , it just crapped out with the same thing
so can't believe that xp. Ubuntu 10.4, 10.4, 7.4, and netbook xp
on different computers are bad?

so going to reset my router and stop going to bbc news for a bit and maybe it will fix itself ;-(

---

### Post by JohnMoriarty on 2010-06-15
Anyone any more thoughts on this?

Last couple of days BBC iplayer won't go into full screen (just blank white screen), but works fine in browser. YouTube works fine. I presume it was the upgrade to 10.1.

I've forced a downgrade on flashplugin-installer back to 10.0.45 as originally comes with Lucid and everything is working fine again.

I'm running 32bit plugins on a 64bit system.

---

### Post by reidi on 2010-06-22
> **JohnMoriarty said:**
> Anyone any more thoughts on this?

Last couple of days BBC iplayer won't go into full screen (just blank white screen), but works fine in browser. YouTube works fine. I presume it was the upgrade to 10.1.

I've forced a downgrade on flashplugin-installer back to 10.0.45 as originally comes with Lucid and everything is working fine again.

I'm running 32bit plugins on a 64bit system.

This worked for me too, but... What are the security implications of going back to the earlier plugin?

---

### Post by the.phantom on 2010-06-23
the way i understand it, the update fixed some secvere leaks in flash player

NOTE: i figured out a solution for most of my problem

i can see the bgc video IF i give firefox root  "gksudo firefox"

but i only have to use it on bbc and should be safe there.

same with my windows system  (XP),if i am admin on 2 boxes it works, but not as user.

i did the update by the ubuntu software center so don't know why OR HOW to CHANGE to allow for user and not root???

---

### Post by no2498 on 2010-06-23
sounds like you need to give permission,for all users for video
its a #  and i do not know it sorry

---

### Post by Windows Nerd on 2010-06-24
> **the.phantom said:**
> the way i understand it, the update fixed some secvere leaks in flash player

NOTE: i figured out a solution for most of my problem

i can see the bgc video IF i give firefox root  "gksudo firefox"

but i only have to use it on bbc and should be safe there.

same with my windows system  (XP),if i am admin on 2 boxes it works, but not as user.

i did the update by the ubuntu software center so don't know why OR HOW to CHANGE to allow for user and not root???
I wouldn't ever even think of using a browser with root privlages. That's just asking for a security breach. 

Scott

---

### Post by AggravatedGestalt on 2011-03-14
No sarcasm intended, but how is this "solved"?  Aside from giving root permissions to anything, I see no answer.

---

### Post by SuperFreak on 2011-03-14
[http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/](http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/)

I used the above like to get BBC working on my 64 bit Ubuntu 10.10 system but I think there are directions for 32 bit  systems also. For the first month of installing 10.10 or so I was not able to watch BBC videos until I found the patch above

---

### Post by ramjet_1953 on 2011-03-14
If you are using Firefox, install the add-on 'Flash-Aid'.

This often overcomes problems with flash.

Regards,
Roger

---

