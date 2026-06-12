---
title: "Cannot create profile for thunderbird.."
date: 2010-11-05
forum: New to Ubuntu
---

### Post by karthick87 on 2010-11-05
I have installed thunderbird and when i open thunderbird a windows opens for creating a profile but i am unable to create the profile.I have attached the snapshots below..Can someone help..?

---

### Post by TeoBigusGeekus on 2010-11-05
Try this from terminal
```
sudo chown yourusername /home/
```

---

### Post by karthick87 on 2010-11-05
Now i get another problem.I have closed thunderbird and when i open now it says"[COLOR=Red]Thunderbird is already running, but is not responding. To open a new window, you must first close the existing Thunderbird process, or restart your system.[/COLOR]"But its not running..I have seen in System--->Administration---->System Monitor but no process running in the name of thunderbird.How can i kill this process..?

---

### Post by NickJones on 2010-11-05
"Have you tried turning it on and off again?"
This happens to me all the time, in impatiently tripple click and open multiple instances, re-start it, and make sure you open it *once*

---

### Post by peculiar penguin on 2010-11-05
If it really isn't running check the profile directory for lock files:[ http://kb.mozillazine.org/Profile_in_use]("http://kb.mozillazine.org/Profile_in_use")

---

### Post by karthick87 on 2010-11-05
> **NickJones said:**
> "Have you tried turning it on and off again?"
This happens to me all the time, in impatiently tripple click and open multiple instances, re-start it, and make sure you open it *once*

Tried turning it off but no use..

---

