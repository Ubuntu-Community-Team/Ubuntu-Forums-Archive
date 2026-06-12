---
title: "Help needed with XSPF player"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by Mariane on 2011-02-27
I am trying to get a web page to play a song. I had it working locally at one point but now I cannot get it to work at all. I don't know if the issue is related to my computer or to the way I wrote the XSPF object. 

So please, can someone go to [http://www.lapf.eu/Jonina/](http://www.lapf.eu/Jonina/) and tell me whether you hear anything? And with which browser? 

And if you know about XSPF, could you please have a look at the source code of this page - the relevant part is only 5 lines - and tell me whether you spot any mistake? 

Or if it is working for you, please tell me how I can find out why it is not working for me. 

Mariane

---

### Post by davidmohammed on 2011-02-27
using chrome on ubuntu - no sounds on that web-page.

---

### Post by Mariane on 2011-02-28
Got it. I was trying to get the best possible sound when converting from .wav into .mp3 so I fiddled with Audacity's settings and ended up with a file which would play locally but not via a browser. 

For anyone finding this thread: 

If it doesn't play via:
<A HREF src="yourfile.mp3">some name</A> it won't play through any player, either. 

If you copy/paste from the web be careful of quotation marks. You need 2 parallel ticks going straight down, anything curling sideways won't do. They have to be like that: 
" 

Files can get corrupted during upload, if it doesn't play it's worth a try to re-upload it. I had to do it 3 times (slow connection). 

Mariane

---

