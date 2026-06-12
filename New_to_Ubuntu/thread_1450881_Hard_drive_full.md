---
title: "Hard drive full"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by Iknownothing on 2010-04-09
My hard drive is full, how do empty some stuff? I have deleted everything I don't need from my desk top. I stress here I have no photos or music on here and I fail to see how the few files and power points I do have could amount to a single GB, I have also emptyed the waste bin

---

### Post by Rocket2DMn on 2010-04-09
You can clean out downloaded archive packages from Synaptic.  Easily from terminal:
```
sudo apt-get clean
```
Or from Synaptic: Settings->Preferences, Files tab -> Delete Cached Package Files

Are you running in a dual boot setup, or do you have use a particularly small hard disk?

---

### Post by lisati on 2010-04-09
Try the following:
```
sudo apt-get clean
sudo apt-get autoclean
```

There could also be a lot of temporary files in /tmp - these will usually get cleaned out when you restart your system.

---

### Post by Iknownothing on 2010-04-09
I'm on a Dell mini 9. Thank you both,  that gave me a GB back

---

### Post by Iknownothing on 2010-04-09
Any Ideas how to get my flash drives to show up in volumes when I go looking for files?

---

### Post by Rocket2DMn on 2010-04-09
> **Iknownothing said:**
> Any Ideas how to get my flash drives to show up in volumes when I go looking for files?

I haven't used UNR for some time so I don't recall exactly what the UI looks like.  When you plug in a flash drive, it should automount and be available for use.  Is this not happening?

---

### Post by RedRat on 2010-04-09
It would help if you gave some details about your system when you pose questions like this. In your query, it would have helped immensely if you would have given your hard drive size. Hey, electrons are cheap on the web, don't be afraid to give more info.

---

### Post by Iknownothing on 2010-04-09
> **Rocket2DMn said:**
> I haven't used UNR for some time so I don't recall exactly what the UI looks like.  When you plug in a flash drive, it should automount and be available for use.  Is this not happening? No nothing shows up,flash drives fine in other PCs. I deleted some games and aps I was not using that came with net book remix.

---

