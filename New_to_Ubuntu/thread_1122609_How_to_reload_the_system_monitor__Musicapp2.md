---
title: "How to reload the system monitor?????  Musicapp2"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by Danielcory on 2009-04-11
Hello, I was looking at this linux joke site, and this one guy said "type cat /vmlinuz > /dev/audio  to hear the voice of God. One post down it said, "if it doesnt work, go into system moniter and end the music app 2 process." 

Me being stupid enough to follow that, did exacly what he wrote and now i cant get it back. :(  Now there is no volume control in my task bar and its torturing my soul.  Can you guys plz help me with this problemm? thnx!

---

### Post by feelshift on 2009-04-11
Right-click on the panel -> Add to Panel -> Volume Control ;)

---

### Post by Danielcory on 2009-04-11
Thank you, Will it start up automaticly again? or do i have to set that up?

---

### Post by feelshift on 2009-04-11
It should start up automaticaly.

---

### Post by lfaraone on 2009-04-11
In the future, you could run:
```
$ killall -I "cat /vmlinuz > /dev/audio"
```


Or just press CTRL+C at the prompt, or just close the tty.

---

