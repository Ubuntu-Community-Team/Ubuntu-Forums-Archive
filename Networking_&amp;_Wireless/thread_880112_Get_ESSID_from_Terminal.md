---
title: "Get ESSID from Terminal"
date: 2008-08-04
forum: Networking &amp; Wireless
---

### Post by arqbrulo on 2008-08-04
Hi everybody. I've been using Ubuntu for about 18 months, but I still feel like I'm new. I want to write a start-up script that checks if my ESSID is "name", and if it is, automatically mount my Airlink101 anas350 to "/mount/location" and finally make a quick and simple backup using a tip that I found on the IBM's page (thanks to digg) using the command "tar cvzf something something". I want this script on my laptop, and being that it's a laptop, it's not always connected to the same network. Any help will be appreciated, so thanks in advance.

---

### Post by arqbrulo on 2008-08-06
Ok, I've managed to get my essid issuing the following command:

```
iwconfig wlan0 | grep essid | tail --bytes=10
```

now, if someone else reads this and tries to do the same, you might have to change the last "10" to something else. This will give me name "ENAME" (with quotes; not real name). So now, I need to find a way to add that to a variable. I've tried "essid=" before the command, and nothing. I've also tried at the end of the command "> essid=" and "| essid=" and nothing. Once I figure out how to get "ENAME" to that variable, I'll be good to go.

---

