---
title: "Problem with Internet (pages won't load)"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by hansoffate on 2007-07-05
I am trying to convince my office to take a look into ubuntu.  I work as IT Help desk in the office.  Sadly, i can't get my network configured correctly in ubuntu.

I have my static ip set up correctly.  I can ping to the box, but I can't ping out of the box.  If I try loading a webpage, it doesn't load.  

Any ideas?
It seems like there is just something that I forgot to check.

Thanks,
Hans

---

### Post by tmatt95 on 2007-07-05
Firstly, welcome to the Ubuntu forum. :D 

Can you try firing up Firefox and typing in "about:config" in the address bar and hit enter.

In the resultant screen type in the filter text box "IPv6"

All the lines should disappear and leave you with just the one. Double click on this line to change its state and restart Firefox. Can you surf the web now?

Matt

P.S We are all learning and if you would like I will fire up a video on how to change the setting if you have difficulties.

---

### Post by hansoffate on 2007-07-05
Thanks for the welcome, but I have been using ubuntu for a while. I use it at home all the time. 

Anyways, the wierd part is, i can't ping out of the box to anything.  Websites, networked computers etc.  I double checked with the network admin, and he gave me the ip to use.  When pinging to the computer, everything returns fine, so obviously it is on the network.  

Any other ideas?
Thanks,
Hans

---

### Post by tmatt95 on 2007-07-05
> **hansoffate said:**
> Thanks for the welcome, but I have been using ubuntu for a while. I use it at home all the time. 

Anyways, the wierd part is, i can't ping out of the box to anything.  Websites, networked computers etc.  I double checked with the network admin, and he gave me the ip to use.  When pinging to the computer, everything returns fine, so obviously it is on the network.  

Any other ideas?
Thanks,
Hans

My bad,for some reason when I saw the thread I thought you had just joined the forum but you have got even more posts to your name than me ( a long day ;) ).

I suggested the Firefox fix because I had a problem like that at home for a while with Firefox not letting me surf the Internet with IPV6 enabled. As soon as I was in another area it would be fine. Then randomly one day it all started to work properly without having IPV6 off

---

### Post by hansoffate on 2007-07-05
Yeah, no problem.  Thought that was the reason.  Thanks for giving me input though.  This is such a wierd problem.  I think I may try to reinstall tomorrow and configure it on the livecd before I install.  

Hopefully, I won't have to if anyone else has any suggestions.

Thanks,
Hans

---

### Post by tmatt95 on 2007-07-05
I have searched around the forum and dug up some interesting threads which may help:

[http://ubuntuforums.org/showthread.php?t=487188&highlight=cant+connect+to+the+internet](http://ubuntuforums.org/showthread.php?t=487188&highlight=cant+connect+to+the+internet)

[http://ubuntuforums.org/showthread.php?t=490178&highlight=connecting+to+the+internet](http://ubuntuforums.org/showthread.php?t=490178&highlight=connecting+to+the+internet)

Although both equally useful I would imagine the top one to be the most valuable to you

---

### Post by hansoffate on 2007-07-09
I feel stupid now.  I realized when I got into to work today that I forgot to put in a DNS Server >.<

Thanks for the help,
Hans

---

