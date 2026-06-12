---
title: "No internet"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by windows hater on 2009-01-28
hello i been at this since monday and i cant seem to get internet to work wired or wirlessly and its driving me insane and im doing this for a school project and now im showing people how bad ubuntu can be

so is there some help someone can offer for me to get the wired or wireless cards to work

---

### Post by residualbit on 2009-01-28
Did you check to see if there are any restricted drivers available?

---

### Post by cariboo on 2009-01-28
Could open an Applications-->Accessories-->Terminal and type:

```
sudo lshw -C network
```

and paste the output in your next post.

JIm

---

### Post by windows hater on 2009-01-28
it sees the two nic cards but not the wireless but when i go to network connections to change from auto to manual the ips arent staying with the cards and for the usb its disabled and i cant get that to work at all

---

### Post by cariboo on 2009-01-28
What is the output of:

```
sudo dhclient eth0
```

could you paste the out put in your next post. To copy and paste from a terminal highlight the text with your mouse, then if you have a wheel mouse just press the wheel to paste. if you don't have a wheel mouse, press both mouse buttons at once. Make sure the terminal stays open when you are copying and pasting.

Jim

---

### Post by windows hater on 2009-01-28
i cant paste but it says eth0: error while getting interface flags: no such deivce

---

