---
title: "blank screen after loading screen"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by crimsonsky69 on 2010-11-01
My screen goes blank after the loading screen when trying to boot in to ubuntu. It does it both recovery mode and the regular. Right before the problem starting happening, i did two things, I update the entire OS and installed driver for nVidia graphics card.

I have tried loading into older versions as well and still the same problem.

any idea in how to proceed?

---

### Post by alexandari on 2010-11-01
May be something with the driver. Proceed with recovery mode and choose the  option to fix X. should return to the default settings.

---

### Post by crimsonsky69 on 2010-11-01
it goes blank in the recovery mode as well

---

### Post by balloooza on 2010-11-01
Can you give much more information about your situation, such as:

What were you using before (version, different OS?)
How did you (Software update, fresh install, distribution update)
What version are you using now?
What nvidia card do you have?
How did you install the Nvidia driver?
What version Nvidia driver
Will recovery mode show anything on the screen?

---

### Post by anewguy on 2010-11-01
Try editing the boot line before Ubuntu boots to include nomodeset and see if that helps.

Dave ;)

---

### Post by crimsonsky69 on 2010-11-10
I have found the problem, I have both an on-board and Dedicated nvidia GPU. The problem occurs only after activating the nvidia driver. It works flawlessly with it de-activated. I tried to startx the server but it says no device detected.

now I'm using Ubuntu 10.10 and haven't updated anything.

---

