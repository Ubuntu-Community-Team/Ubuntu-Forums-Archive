---
title: "How to"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by Jynxx on 2009-01-20
I'm having some issues with my graphics in ubuntu. I have onboard i945 on my HP pavilion dv6000. My question is, is there a way that I can install the graphics driver from the original disk that came with my laptop? Or can I install it after downloading it from HP website? Not sure how to do that.

---

### Post by Jynxx on 2009-01-20
Bump

---

### Post by handydan918 on 2009-01-20
The drivers on your disk are unlikely to be written for Linux. They are most likely Windows programs.
What kind of problems are you having?

---

### Post by Jynxx on 2009-01-20
When I change windows or close a window, lines show on the screen for a brief moment. Resolution is decent but I'm not sure if my video is being used to its full ability.

---

### Post by wolfen69 on 2009-01-20
what is the problem? there is no need to install drivers for intel.

---

### Post by mjheagle8 on 2009-01-20
can you please post the output of ```
lspci
```

---

### Post by blackened on 2009-01-20
The drivers on HP's website are Windows specific. You cannot use them in Linux.

Try installing the intel video driver, which should be in the universe repo, so make sure universe is available:

```
sudo apt-get install xserver-xorg-video-intel
```

That or you could post the output of

```
lspci -v
```

---

