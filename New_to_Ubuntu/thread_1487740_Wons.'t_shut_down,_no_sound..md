---
title: "Wons.'t shut down, no sound."
date: 2010-05-19
forum: New to Ubuntu
---

### Post by Zappanale on 2010-05-19
This is a problem that occurs every now and again, in 10.04. One of these times is right now.

Firstly, there's no sound. The sound icon doesn't look as it normally does, it's a sort of outline of the volume control icon, and no sound plays.

Secondly, the laptop won't shut down. Going to "shutdown" merely logs out. Trying to use the shutdown command in the terminal tells me that I need to be root. The only way to shut down is press down the power button until it turns off itself.


Yeah. Very odd. Any ideas on what's wrong? Thanks.

---

### Post by brennydoogles on 2010-05-19
How many user accounts are on this computer? If you don't have sudo privs, you won't be able to shut down the computer via terminal. If you do, then the command ```
sudo shutdown -hP now
``` should shut you right down. Hope that helps!

---

