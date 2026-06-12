---
title: "move folders through terminal"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by Messyhair42 on 2009-07-19
after searching through commandlinefu i didn't find the proper command to move folders around. i've got a folder on my desktop with a program, and want to move it under .../wine is the command correct
```
sudo mv /desktop /username/home/...
```

---

### Post by jerome1232 on 2009-07-19
You want to move a folder that's located on your desktop to your wine folder is that correct?

I believe you would want this: note that capitals are important
```
mv ~/Desktop/*foldername* ~/.wine/C:/Program\ Files/
```

---

### Post by Messyhair42 on 2009-07-25
I've got wine installed and i've got programs running under wine, but i can't find my "C:" drive and```
cd /home/username/.wine/C:/Program\ Files/
``` didn't work for making the directory

---

### Post by llamabr on 2009-07-25
To move a full directory, I usually tar it up, move the .tar, and then untar it.  It makes sure everything arrives as it was.

---

### Post by ~sHyLoCk~ on 2009-07-25
> **Messyhair42 said:**
> I've got wine installed and i've got programs running under wine, but i can't find my "C:" drive and```
cd /home/username/.wine/C:/Program\ Files/
``` didn't work for making the directory

mv ~/Desktop/foldername ~/.wine/drive_c/Program\ Files/

---

