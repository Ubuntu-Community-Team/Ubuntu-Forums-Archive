---
title: "How to get fluid wobbly windows in compiz-fusion?"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by 11010110 on 2009-01-24
I have been using CF for a while now and i was looking for some other things i could use to spice things up and i came across this video on some website and followed it to youtube... the wobbly windows are more fluid-like here and when you grab a maximised corner and drag down it flows rather than springs. I think its pretty cool looking and thru research and just messing around i cant seem to find out how to do this. Maybe its because ubuntu isnt used. If anyone could give me a hand that would be great. The link to the video is below. 

Thanks everyone in advance!

[http://www.youtube.com/watch?v=lawkc3jH3ws&eurl=http://lifehacker.com/software/ubuntu/hack-attack-top-10-ubuntu-apps-and-tweaks-195437.php](http://www.youtube.com/watch?v=lawkc3jH3ws&eurl=http://lifehacker.com/software/ubuntu/hack-attack-top-10-ubuntu-apps-and-tweaks-195437.php)

---

### Post by dnRoyston on 2009-01-24
Based on the specs in your signature, it doesn't look like you should be having any problem with lag, but to edit the... er... wobblyness of windows, go to System > Prefrences > CompizConfig-Settings-Manager. From there go to Effects, then Wobbly Windows. The settings you're going to be focused on are the first 3 sliders: Friction, Spring K, and Grid Resolution. Those should be pretty self explanitory. Fiddle with those until you get a setting you like most.

---

### Post by 11010110 on 2009-01-24
Thanks for the reply! I tried fiddling with it but i just couldnt get it to work that way... when it was anywhere close on the corner pull it made it impossible to use when moving un-maximised windows. I sent a message to the video maker seeing if maybe he could offer some insight. 

Thanks again for the reply!

---

### Post by dnRoyston on 2009-01-24
ooh, try going to "Window Management", then disabling "Snapping Windows"

---

### Post by 11010110 on 2009-01-24
i can drag the corners down jsut fine but when i make it more fluid by adjusting the friction and spring k then when im dragging around a terminal window or something it gets kinda messy and outa control... lol the windows tend to stretch way too far and move far too slow to be productive at all. I have no idea how he is able to get the fluidity yet maintain the seemingly normal settings when draggin around windows... so i dont know where to go from here lol. thanks again for the reply though.

---

### Post by dnRoyston on 2009-01-24
Higher Friction + Less Spring K = More like the video. Hopefully he'll reply back with what he uses as far as the variables go. Good luck!

---

### Post by jocko on 2009-01-24
The video was made with compiz-quinn about two years ago, so it may not be possible to replicate the settings exactly. Compiz-quinn was an experimental branch of compiz, which later branched off completely from compiz and became beryl. Compiz-quinn/beryl contained lots of plugins and configuration options that were not included when beryl was fused back to compiz to become compiz-fusion.

But for the behaviour of the wobbly windows, you should be able to achieve something similar by changing the friction/spring parameters.
To be able to peek behind maximized windows instead of unmaximizing them when you pull the decoration, inactivate "snapoff maximized windows" in the move windows plugin.

---

### Post by 11010110 on 2009-01-24
thanks everyone for the replies. Ill wait for his reply and if i cant do it then i guess its no problem. 

Thanks again everyone

---

