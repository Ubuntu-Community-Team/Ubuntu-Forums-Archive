---
title: "Is there any way to test my wireless modem?"
date: 2016-04-13
forum: Networking &amp; Wireless
---

### Post by james214 on 2016-04-13
I had a fairly serious problem a few days ago where my laptop was unable to detect wireless signals. That problem has been solved, but I was getting an intermittent connection at the library yesterday, an intermittent connection at Panera Bread last night, and an intermittent connection in my home this morning. Is there any way for me to test my modem to make sure everything is working properly?

Edit: I don't seem to have any problems connecting with my Motorola (Android) smartphone. My HP Stream 13 with Ubuntu keeps dropping the connection though.  :(

---

### Post by james214 on 2016-04-17
Anyone? Anyone? Bueller?

---

### Post by Bucky Ball on 2016-04-17
If you don't have an issue connecting with the modem via your Android device, then it's not the modem. Can you ping the modem okay from your Ubuntu machine? You'll need the IP address of the modem/router. Open a terminal and:

```
ping 192.168.0.1
```

Replace the number with the IP of your modem/router. Hit enter and watch the output for awhile. If you're not getting a ping from the modem/router, there's a problem. I wouldn't think it would be a hardware issue with the router but a software or hardware one with the local device, your computer.

Once you've finished with the above, or prior to then, please run the wirelessinfo script linked in my signature at the bottom of this post and post the output of that here between code tags, please (code tags 'how to' also linked in my signature).

---

