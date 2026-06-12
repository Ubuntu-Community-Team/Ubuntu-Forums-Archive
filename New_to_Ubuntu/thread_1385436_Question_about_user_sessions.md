---
title: "Question about user sessions"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by Paullus_N on 2010-01-19
Hello all,

I'm playing around with ubuntu a bit, and love it! Just got one question for. 
When I switch users from A to B, do the services (webserver, file shares etc) stay active?

Since my folks will use the system also (and they are not to well adapted to modern technology) I would like two user accounts. One for me ( for server tasks) and one for my parents. So if my folks log in, do my services halt?

Any help is welcome!
Thanks

Paul

---

### Post by jward3010 on 2010-01-19
Crap, I was about to say yes, but now I'm not so sure. I think network manager restarts on every login but, YES, there are ways to set up those services to run before Gnome starts... How exactly is another experts area.

---

### Post by Paullus_N on 2010-01-19
hmm, I spoke to soon I guess.
Tried a quick install of playstation Media server, switched users, test. 

Question answered

---

### Post by lambengolmor on 2010-01-19
It depends: if for "server tasks" you mean apache, I'm 99% sure you won't have any problem. Instead if "server tasks" are programs you start from your user (for example bittorrents) they stay active if you "switch user" but not if you "log out". That is important since the user session is not closed, so every program running keeps running, even the media player, even though in the latest versions of ubuntu you quit hearing sounds. If you can explain more about "server tasks" you can have better help :D

---

### Post by Paullus_N on 2010-01-19
Yeah, the music player got me worried. It stops playback (understandable) but also stops updating its library. 
And server tasks also include bittorrent in my case, but since PMS (who ever made that name up) keeps active I have hope for the future!

on a side note: I'm pretty supprised that my ols 'n crappy laptop runs ubuntu smoothly. Need to check if all my needed programs function in linux (or if I can find a replacement for them) and it's bye bye windows. I feel like a rebel! :D

---

