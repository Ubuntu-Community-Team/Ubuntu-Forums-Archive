---
title: "Use terminal to change speakers?"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by siretfel on 2011-02-20
Hi all,

I bought logitech usb speakers and I'd like to ask if there is a way to change between internal speakers (laptop) to external usb through terminal.
For now if i want to change speaker output i have to go to Sound Preferences>Hardware set interal Off and exteral On.
Is there a way to do this through a command?

Thanks

---

### Post by cariboo on 2011-02-20
You should be able to do what you want using alsamixer. Once it is up and running press F6 to select what sound device you want to use. Once you have everything set to your liking, press esc to exit. To save your changes type:

```
sudo alsactl store
```

---

### Post by siretfel on 2011-02-21
It worked!:popcorn:
Thank you sooooooooooooooooooooooo much!

---

