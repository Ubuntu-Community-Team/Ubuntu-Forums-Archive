---
title: "How to dump a shot / frame of the webcam /dev/video0 from command line?"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-01-30
I know streamer but is there better or something else? 

thank you

---

### Post by frenchn00b on 2010-01-30
I tried this but not working :( 

```
 scanimage -d v4l2:/dev/video0  > shot-of-thewebcam.ppm
```

OK

I found : 
> 
mplayer -tv driver=v4l:fps=15 -vo jpeg tv://

mplayer -tv driver=v4l2:fps=15 -vo jpeg tv://

---

### Post by frenchn00b on 2010-01-30
[http://mydebian.blogdns.org/?p=120](http://mydebian.blogdns.org/?p=120)

---

