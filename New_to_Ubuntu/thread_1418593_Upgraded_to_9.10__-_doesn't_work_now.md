---
title: "Upgraded to 9.10  - doesn't work now"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by kiptok on 2010-02-28
Hi guys, I had ubuntu netbook remix 9.09 installed on my asus eee pc 1005ha and it worked fine. but then I selected the option to update to 9.10 and now when I try to turn it on it just goes straight to the command line! I can see my files this way, but there's no desktop, no GUI, etc. Any help? Thanks a lot.

---

### Post by cariboo on 2010-02-28
It sounds like your update may not have completed properly. Seeing as you can only get to the command prompt, type:

```
sudo apt-get -f install
```

The above command will install any missing dependencies. You could also try:

```
startx
```

at the prompt to see if X will start.

---

### Post by kiptok on 2010-02-28
Thanks a lot. I'll see if this works.

---

### Post by kiptok on 2010-02-28
okay it seems it worked! Thank you so much.

---

