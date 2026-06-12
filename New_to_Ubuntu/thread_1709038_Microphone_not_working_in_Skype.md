---
title: "Microphone not working in Skype"
date: 2011-03-17
forum: New to Ubuntu
---

### Post by Phelixfil on 2011-03-17
I'm having problems getting my mic to work on Skype.  Looks like it's an ongoing problem as I've seen several posts regarding this.  Tried various things but to no effect.  Anyone got any ideas?

---

### Post by LowSky on 2011-03-17
could you list your hardware? What steps have you tried? is it an internal mic, or headset?

---

### Post by weezyrider on 2011-03-18
While I haven't tried the mike in Skype, I did the system test thing, and the mike wasn't under USB where I thought it should be. (It is USB). It turned up elsewhere in the test and it did work in the test. There were 3 microphone tests. One was internal, the second USB and the third was after that. 
W

---

### Post by Phelixfil on 2011-03-23
Thanks for that.  Still ahven't found the solution.  I posted this in two places by mistake and can really only follow the one thread.  I'm not sure how to paste you into that but maybe we'll meet again.  Thanks again, P

---

### Post by ajgreeny on 2011-03-23
Run ```
alsamixer
``` in terminal and check that the levels of inputs and outputs are not set too low.

Move from side to side, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture" to "All"
Esc will save and exit.

---

