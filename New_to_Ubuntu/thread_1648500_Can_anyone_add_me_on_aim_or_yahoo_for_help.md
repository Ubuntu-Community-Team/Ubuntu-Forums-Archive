---
title: "Can anyone add me on aim or yahoo for help"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by confused10 on 2010-12-18
I am new to ubuntu and its so frustrating. My skype mic isnt working yet recorder is. And also i just need to ask questions to someone who is good and can help. Chatting would be easier

---

### Post by cariboo on 2010-12-19
We don't do one-to-one support via the forums, we prefer that you ask your question here, so that others may benefit from it too.

To answer your question about the microphone, I had the same problem on my netbook. to solve it, open an Applications->Accessories->Terminal and type:

```
alsamixer
```

You should see something similar to the screenshot. Use the tab key to navigate between the individual settings, and the arrow keys to change them. Once you have things set to your liking, press the esc key to exit and then at the prompt type:

```
sudo alsactl store
```

to save the settings.

**Note:** the screenshot is form one of my desktop systems, so yours may look a little different.

---

### Post by confused10 on 2011-01-02
I seen but it still is all static and not working on skype but voice recorder sounds fine

---

