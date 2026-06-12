---
title: "There is no device in my sound preferences (dummy output)"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by Isyaltut on 2010-02-06
Hi, this is my first post here and i have a problem with my laptop. I've just installed ubuntu karmic on my fujitsu esprimo u9200. Everything works fine althought there is some glitch along the way.

But the next day, when i turn on my laptop again, there is no sound at all. And then i go to Sound Preference-Hardware tab. There is no device at all. And in my output tab, i've got dummy output. 

So please, if anyone has a solution for this, appreciate it very much

---

### Post by mushwars on 2010-02-06
Have you tired looking at lspci to see if your device is there?

you might also need to modprobe the driver, but as you did not tell us what card you have I cannot tell you what driver you might need to load.

you could also try

```
sudo alsaconf
```

and select your device, it will then be in your 

```
alsamixer
```

---

### Post by Isyaltut on 2010-02-06
well, never mind now. I have tried to remove the proprietary hardware drivers (Smart link modem daemon), and then suddenly my sound just works again without even have to reboot.

---

### Post by mushwars on 2010-02-06
cheers ;) I am glad you got it working.

---

