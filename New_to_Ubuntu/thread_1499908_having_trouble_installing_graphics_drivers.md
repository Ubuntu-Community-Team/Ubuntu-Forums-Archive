---
title: "having trouble installing graphics drivers"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by coeus89 on 2010-06-02
I am trying to install graphics drivers for my laptop. i think its an nvidia geforce 7600. i downloaded this nvidia-linux-x86-195.36.24-pkg1.run  but i cant get it to run. all i get is this error message 'Could not open the file /home/jonnyk/Desktop/NVI…ux-x86-195.36.24-pkg1.run.' when i open with gedit. what is wrong?

---

### Post by fooman on 2010-06-02
have you tried going to system > administration > hardware drivers

see if there are drivers available there.  if they are,  then choose "(version current)" and click on "activate"

---

### Post by darkdragn on 2010-06-02
Fooman told you the best thing to do. These drivers are updated and tested regularly. Otherwise, if you are hellbent on using the one you downloaded you might need build-essential. (apt-get install build-essential)
Then make the file executable, by cd-ing into the directory with the file in it, and using 'chmod +x $FileName' After that just execute the file as a script, typing ./TheFileName. Good Luck.

---

### Post by halitech on 2010-06-02
> **coeus89 said:**
> I am trying to install graphics drivers for my laptop. i think its an nvidia geforce 7600. i downloaded this nvidia-linux-x86-195.36.24-pkg1.run  but i cant get it to run. all i get is this error message 'Could not open the file /home/jonnyk/Desktop/NVI…ux-x86-195.36.24-pkg1.run.' when i open with gedit. what is wrong?

you don't want to open it with gedit anyway. as darkdragn stated, you need to make it executable then you would run it in the terminal from the directory you have the file in with
```
sudo ./nvidia-linux-x86-195.36.24-pkg1.run
```

---

