---
title: "I don't have permission to do copy files?"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by rob86 on 2009-09-02
I'm trying to install a skin for aMSN which simply tells me to extract the ZIP to usr/share/amsn/skins.

Sounds simple enough, except Ubuntu denies me permission to do this simple task. I've tried extracting it directly, and copying it there and nothing works. What's the deal?

---

### Post by credobyte on 2009-09-02
```
gksudo nautilus /usr/share/amsn/skins

```

---

### Post by Viva on 2009-09-02
usr/share/amsn/skins is outside your home folder, so you don't have the permissions to edit the files there. Extract the files somewhere, Run "gksudo nautilus" from your terminal, navigate to the folder and paste them there. Alternatively, you can install [nautilus-gksu]("apt:nautilus-gksu"), navigate to the folder, open it as administrator using right click and paste the files there.

---

### Post by rob86 on 2009-09-02
thanks nautilus worked

---

### Post by sanderd17 on 2009-09-02
Maybe, if you have some time left, it would be handy for you if you learned some shell scripting, the part you needed is mentionned here: [http://linuxcommand.gds.tuwien.ac.at/lts0070.php#su]("http://linuxcommand.gds.tuwien.ac.at/lts0070.php#su") but it would be better to start from the beginning: [http://linuxcommand.gds.tuwien.ac.at/index.php]("http://linuxcommand.gds.tuwien.ac.at/index.php").

I know I learned a lot from this course, maybe you will to (btw: you don't have to read everything, writing shell scripts can be handy if you want to automate your work but I think it's enough if you know the basic commands)

---

### Post by sourav123 on 2009-09-02
In general, use sudo when you want to write to any directory outside of your home directory.

---

