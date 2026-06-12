---
title: "how to add 'detect new hardware' to startup"
date: 2011-01-06
forum: New to Ubuntu
---

### Post by mystmaiden on 2011-01-06
I've accidentally removed the 'detect new hardware' from startup in Karmic. How do I replace it? If I don't will the system recognize new keyboards, etc. and my video card? I can't use the newest nvidia proprietary drivers, so I would not need it for that.

thanks

mystmaiden

edited to add - so far google hasn't helped much. I did try to reinstall my video card, and have been unsuccessful, so I'm thinking I definitely need to restore that file. I have the live cd if I can pull a file off there, I just do not know what file to copy.

---

### Post by CaptainMark on 2011-01-06
Do you mean you erased it from the Startup Applications menu in preferences, if you did then just click add and use the following ive copied from my menu.

Name:
Check for new hardware drivers

Command:
sh -c 'test -e /var/cache/jockey/check || exec jockey-gtk --check'

Comment:
Notify about new hardware drivers available for the system

If ive mistaken your meaning sorry perhaps someone might have the answer you need
EDIT: This is for Lucid not Karmic, im assuming its the same but you could always load up a Karmic Live CD and check the menu there, I have one somewhere if you dont.

---

### Post by mystmaiden on 2011-01-06
Thank you, CaptainMark.

 I believe that's exactly what I needed. I also need to know how to use a .run file from the terminal. A search only turned up one reference to that and it was such an old post, I'm not at all sure it would apply now.

thanks all,

mystmaiden

---

### Post by CaptainMark on 2011-01-07
You should really start a new thread to ask a different question, just to help people who have a similar question,

you cd to the directory the file is in and type ```
./file_name.run
```
if that doesnt work you need to make executable first by using ```
sudo chmod +x file_name.run
```

---

### Post by mystmaiden on 2011-01-09
You're right, CaptainMark, thanks for the heads up on starting a new thread.

And thanks for the .run command!

---

