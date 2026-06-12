---
title: "microphone"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by suajio on 2011-01-25
Hello my ubuntu friends, I want to learn putting my microphone on 

(by default in the program of voice recordings the links are in grey). 

Please help me, or at least told me about where I find this information. Thank you.

---

### Post by cariboo on 2011-01-25
Open an Applications->Accessories->Terminal, and type:

```
alsamixer
```

Use the arrow keys to navigate, and make sure your microphone isn't muted and the volume is turned up.

Once you are happy with the changes you have made, press esc to close the program, then in the same terminal type:

```
sudo alsactl store 
```

to save your settings.

**Note:** Your password will not be echoed back when you type it.

---

