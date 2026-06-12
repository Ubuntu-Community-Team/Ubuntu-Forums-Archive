---
title: "Error message at shutdown"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by expatCM on 2009-05-09
When closing Jaunty a dialogue window appears to tell me that the system will close in 60 seconds.  Fine.  The system does shutdown after 60 seconds.  What I have noticed though is a split second before the system goes down an error message window appears asking some sort of question. There appears to be a yellow warning triangle as well.

This happens so quickly before shutdown that I cannot read what is said at all.

Is there any way to find out what this message is all about?  I have looked at System / Administration / Log File Viewer but really there are far too many logs there to work out where to look ….  if this message is actually logged at all ….

---

### Post by lisati on 2009-05-09
Are you using a laptop or desktop with a Wifi card? Some users have reported that shutdown seems to hang when they have a Wifi card connected.


See [here]("http://ubuntuforums.org/showthread.php?t=1140584&highlight=wifi+shutdown&page=2")

---

### Post by expatCM on 2009-05-09
No, it is a wired desktop.  The only "exotic" element is nfs shares.  Perhaps I would temporarily disable these and see if the message also disappears .....

---

### Post by expatCM on 2009-05-09
Good to explore but taking out the nfs shares had no impact on the error message appearing ...........

---

### Post by Peter09 on 2009-05-09
Try shutting down from the command line - see if you get a better error list.

```
sudo shutdown -h now
```

---

### Post by expatCM on 2009-05-09
Yes, it shuts down but ....  no error notifications.

---

### Post by Peter09 on 2009-05-09
I sometimes get an error window that tells me that composting has been disabled. I assume that this is just an anomaly of the shutdown process.

---

### Post by expatCM on 2009-05-09
How do you know the error message is there -- do you have time to read it and then click through or are you reading a log file?

---

### Post by Peter09 on 2009-05-10
A window pops up center bottom of screen saying compositing has been disabled, almost immediately disappears as the shutdown process continues.and screen goes black, followed by shutdown bar.

---

### Post by expatCM on 2009-05-10
In some respects this sounds similar although I can read nothing at all it happens so quickly.

I can see a yellow triangle in the top right and it looks like there is the option to check a box half way down the window.

---

