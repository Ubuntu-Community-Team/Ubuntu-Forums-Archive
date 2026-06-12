---
title: "Internet through Virtualbox?"
date: 2011-06-04
forum: New to Ubuntu
---

### Post by r2d211 on 2011-06-04
Okay, first of all, I have no internet connection. The only way I can do it is using Tether for Blackberry in Win XP. Now I have installed Natty 11.04 with wubi and managed (after many downloads in windows) to have Virtualbox installed. I'll put an XP on it.

My stupid question is: would I be able to update ubuntu through tethering in an XP virtual environment? My gut is telling me no, but I would like your opinion.

---

### Post by r2d211 on 2011-06-05
Bump!

---

### Post by r2d211 on 2011-06-05
I have ubuntu Natty installed along WinXP. Natty has no internet because I go online only using Tether for Blackberry in windows. My stupid question is: Using virtualbox in ubuntu to create a virtual XP environment, will give me the possibility to update ubuntu by tethering in the virtualbox!
My mind is telling me no, but what do you think?

---

### Post by howefield on 2011-06-05
Duplicate threads merged. Please do not create multiple threads on the same topic.

Feel free to bump your original post every 24 hours(ish) if no reply.

---

### Post by r2d211 on 2011-06-05
Howefield, thanks for your intervention! I wanted to post it in Absolute Beginner forum but then I said that Virtualisation is better. Anyway, I was looking for a button labeled 'move thread to' or something, but couldn't find. 

Thank you again for merging my thread and placing it in this forum!

---

### Post by wolfen69 on 2011-06-05
The bottom line is, if the host OS can't get online, the guest OS will not be online.

---

### Post by r2d211 on 2011-06-05
Even is the guest OS has the software/hardware to get online? (Tether for Blackberry installed and the Blackberry itself???????

Wolfie, that's bad news...

---

### Post by hakermania on 2011-06-05
I guess that wolfen69's answer is correct but... there is the option 'Bridged' adapter in the network settings of the virtualbox which gives another local IP address to the guest (different from the host)..
I don't know if this can practically work if the host hasn't got access  to network...

---

### Post by wildmanne39 on 2011-06-05
> **r2d211 said:**
> Even is the guest OS has the software/hardware to get online? (Tether for Blackberry installed and the Blackberry itself???????

Wolfie, that's bad news...
Hi, you must have connect in the host for you to have a connection in the guest. Why can you not get your internet in the host to work?

---

### Post by migs73 on 2011-06-05
It seems possible that you can connect using Ubuntu/Bluetooth/Blackberry.

See Here;  [http://ubuntuforums.org/showthread.php?t=1281463](http://ubuntuforums.org/showthread.php?t=1281463)

---

### Post by r2d211 on 2011-06-05
Yes, I have seen the bluetooth solution but for the moment I have no Bluetooth adapter.

Anyway, in XP I didn't need the network manager, the Tether software takes care of everything and you get instant access.

The goal is to obtain a connection in ubuntu, for updates and repositories. So the bluetooth solution is the best since berry4all failed to help me (working on it for a week now but no success).

Thanks for helping!

---

