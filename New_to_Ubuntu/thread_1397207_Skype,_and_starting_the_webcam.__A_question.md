---
title: "Skype, and starting the webcam.  A question"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by VinnyJ1701 on 2010-02-03
Hi Gang, 

What is the proper way to insert this..

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```into skype's launcher properties, so it all loads in one click?

Thanks for your help.

Vince

:guitar:

---

### Post by KIAaze on 2010-02-03
Put it in the command field of the launcher properties window.

If that doesn't work, you can create a script /usr/bin/skype.sh with the following in it:
```
#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype

```

Make it executable:
```
sudo chmod +x /usr/bin/skype.sh
```

Change the launcher command to "/usr/bin/skype.sh".

---

### Post by VinnyJ1701 on 2010-02-07
> **KIAaze said:**
> Put it in the command field of the launcher properties window.

If that doesn't work, you can create a script /usr/bin/skype.sh with the following in it:
```
#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype

```Make it executable:
```
sudo chmod +x /usr/bin/skype.sh
```Change the launcher command to "/usr/bin/skype.sh".

Hey,
I followed the instructions and made the file, and changed the launcher command..

I got an error that said  "failed to execute child process.. /usr/bin/skype.sh (no such file or directory)"

Does the 'skype.sh' file need to be saved in a particular place?

Thanks, 

Vince

---

### Post by KIAaze on 2010-02-07
Well yes: in /usr/bin
That's why I called it "/usr/bin/skype.sh". :roll:

If you save it somewhere else (which is possible), just make sure you give the correct path in the launcher command (and that skype.sh is executable).

---

### Post by VinnyJ1701 on 2010-02-09
> **KIAaze said:**
> Well yes: in /usr/bin
That's why I called it "/usr/bin/skype.sh". :roll:

If you save it somewhere else (which is possible), just make sure you give the correct path in the launcher command (and that skype.sh is executable).
Thanks!  

After learning a little more about the terminal (I'm liking the terminal more and more)  the file copied well and seems to work.  Your help was appreciated

Vince

---

### Post by mblemieux on 2010-02-23
Thanks you so much for this little script. This was incredibly helpful.

---

