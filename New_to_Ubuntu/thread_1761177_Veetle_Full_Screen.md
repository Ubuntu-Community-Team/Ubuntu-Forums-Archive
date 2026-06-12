---
title: "Veetle Full Screen"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by mikedanben on 2011-05-17
Hi,
Watching Movies on Veetle is good :popcorn:

Annoying problem is that when I click Full Screen, there is still the bar up on top.
Anyone able to get an actual f11 type of full screen? 
Works for Youtube.

---

### Post by Morderwurst on 2011-05-26
I have this same problem with Natty. You can circumvent it by watching veetle streams in vlc :D


To do this:
go to open network stream (in vlc) and type in                                    **[http://](http://)[localhost]:[remote port]/[IP for ["]www.veetle.com]]("http://www.veetle.com),[view #]**
                                  
where 'view #' is the 4dd0bdae905b5 in (for example)
<http://www.veetle.com/index.php/channel/view#4dd0bdae905b5>

**remote port may be obtained by running netstat, and searching for the 'vlcori' process ID

**e.g.**
**[http://127.0.0.1:58998/77.67.109.220,4d31422bd033c](http://127.0.0.1:58998/77.67.109.220,4d31422bd033c)**
 
 
Hope this helps!

---

### Post by gbrowne on 2011-08-27
Thanks for this information Morderwurst.  This works fine for me - but only for a short time.

In my case the channel is displayed on VLC, then the browser (Firefox) stops streaming but then after a few seconds of working fine, the feed closes in VLC and the browser says please retry in 5 mins.  Only F5 in the browser get the feed back.  VLC was not running prior to the attempt.

Any ideas how I can get round this time limit of a few seconds please as it unusable as is ?

Many thanks.
G.

---

