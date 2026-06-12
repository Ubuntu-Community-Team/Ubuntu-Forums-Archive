---
title: "Wireless not working."
date: 2010-07-01
forum: New to Ubuntu
---

### Post by jeffymarts on 2010-07-01
Hello,

I'm having a problem with connecting to my wireless access point at the moment. I checked to see if wireless networking is enabled and it is. But no networks show up and I know that there is a working wireless signal because I can connect with another device. My wireless capabilities vanished after I turned the computer on from a cold start. (It was working before I shut it off.) Also, I can connect to the internet over a wired connection. Anyone have any ideas of what might be wrong? I would gladly give more information if you need to know something about my system, connection, etc.

Thanks.

---

### Post by cariboo on 2010-07-01
Open a terminal and type:

```
sudo lshw -C network
```

and paste the output in your next post.

---

### Post by warfacegod on 2010-07-01
See if this gives you any results:

```
sudo iwlist scanning
```

---

### Post by jeffymarts on 2010-07-02
I ended up figuring it out on my own. My computer has a button that's supposed to turn wireless on and off right next to the power button. When I went to shut my computer down I missed the power button and pressed that instead of the power button. After that I just shut it down because I didn't think that pressing that button would do anything... but it did. Thanks for trying to help though!

---

### Post by warfacegod on 2010-07-02
Glad to here it. I've read so many Threads about the wireless switch not working but wireless still works that it never occurred to me to suggest that. Please mark this as Solved under Thread Tools.

---

