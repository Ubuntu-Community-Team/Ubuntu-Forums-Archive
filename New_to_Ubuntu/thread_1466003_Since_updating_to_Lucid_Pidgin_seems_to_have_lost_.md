---
title: "Since updating to Lucid Pidgin seems to have lost alert in System Tray"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by hamstermoon on 2010-04-29
In Karmic I didn't think much of Empathy and deleted it just used Pidgin as I always had done before. I got a small green dot in the Notification Area which turned to a speech bubble when I got a reply. Now there is nothing. 

I also don't seem to be able to close the Buddy List as that just shuts the whole thing down. Before I used to be able to do this and keep the conversation I had open going.

 Am I going to have to switch to back Empathy to get something like that (I LIKE Pidgin!). :confused:

---

### Post by tom.swartz07 on 2010-04-29
> **hamstermoon said:**
> In Karmic I didn't think much of Empathy and deleted it just used Pidgin as I always had done before. I got a small green dot in the Notification Area which turned to a speech bubble when I got a reply. Now there is nothing. 

I also don't seem to be able to close the Buddy List as that just shuts the whole thing down. Before I used to be able to do this and keep the conversation I had open going.

 Am I going to have to switch to back Empathy to get something like that (I LIKE Pidgin!). :confused:

The functionality that youre talking about is built in to empathy.

Unfortunately, in the newest update of pidgin, there were some problems that prevent the application from running in the notification applet, and they hope to get it resolved sometime soon. You CAN however, go into the options in pidgin and select 'display notification area icon' and that will keep pidgin open after you close the window. 


Sometime soon they will fix it so that it plays nice with the me menu, but until then I guess youre stuck! Sorry!

---

### Post by claracc on 2010-04-30
Same problem with latest kernel 2.6.31-21 in Karmic Koala:

[http://ubuntuforums.org/showthread.php?t=1466109](http://ubuntuforums.org/showthread.php?t=1466109)

No workarounds, then?

---

### Post by tom.swartz07 on 2010-04-30
> **claracc said:**
> Same problem with latest kernel 2.6.31-21 in Karmic Koala:

[http://ubuntuforums.org/showthread.php?t=1466109](http://ubuntuforums.org/showthread.php?t=1466109)

No workarounds, then?

Other than checking the option to leave the icon in the notification area, no. If you make it put the icon in the notification area, it works independently of the Me Menu.

---

### Post by hamstermoon on 2010-04-30
> **tom.swartz07 said:**
> The functionality that youre talking about is built in to empathy.

Unfortunately, in the newest update of pidgin, there were some problems that prevent the application from running in the notification applet, and they hope to get it resolved sometime soon. You CAN however, go into the options in pidgin and select 'display notification area icon' and that will keep pidgin open after you close the window. 


Sometime soon they will fix it so that it plays nice with the me menu, but until then I guess youre stuck! Sorry!

Now why didn't I think of that (headdesk) ... many thanks. I think I had to do that with Karmic now I think about it!

---

### Post by tom.swartz07 on 2010-04-30
> **hamstermoon said:**
> Now why didn't I think of that (headdesk) ... many thanks. I think I had to do that with Karmic now I think about it!

HA! its okay, it took me 3 days to realize that it was actually closing the application when i closed the window. then from there it took another hour to figure out how to do what i just explained!

---

### Post by mlissner on 2010-07-09
Install pidgin-libnotify as a plugin, turn it on, and turn off the setting that enables pidgin to stay in your tray, and you should be all set.

---

