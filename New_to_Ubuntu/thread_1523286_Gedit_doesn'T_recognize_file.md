---
title: "Gedit doesn'T recognize file"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by etiennechausse on 2010-07-03
This is the message i get when i try to install my NVIDIA driver

gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again.

help plz ^_^

---

### Post by sanderd17 on 2010-07-03
What do you do to install the driver? are you double clicking a file? (I hope it isn't an exe file)

Or are you installing it via the notification thingy in ubuntu?

The error says you want to open a binary file with a text editor.

---

### Post by wojox on 2010-07-03
Why are you trying to open the driver file with gedit?

---

### Post by yossell on 2010-07-03
Can you give some information about the steps you've followed to install the nvidia driver?

gedit is a text editor and that message sounds like a complaint that gedit is being used to open a file it can't read - maybe you've been trying to use it to open a driver file? But I'm not sure why a text editor is being used to install a driver at all here - so more information would be helpful.

---

### Post by wojox on 2010-07-03
Use this to install manually [Nvidia]("http://ubuntuforums.org/showthread.php?t=1467074&highlight=install+nvidia+lynx")

---

### Post by sanderd17 on 2010-07-03
Ok, it's not via the notification thingy. See [http://ubuntuforums.org/showthread.php?p=9542713]("http://ubuntuforums.org/showthread.php?p=9542713")

---

### Post by lkjoel on 2010-07-03
> **etiennechausse said:**
> This is the message i get when i try to install my NVIDIA driver

gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again.

help plz ^_^
For HoN?
If all fails, check my second last post in your HoN discussion.
In a terminal, type this:
```
chmod +x NVIDIAdriverfile
./NVIDIAdriverfile
```

---

