---
title: "Access windows files ?"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by Drakkor on 2010-05-05
Installed 10.4 yesterday,and how can I access my music,movies,etc. on the
windows installation ? In places,I have "System" and "Factory Image",but
they only seem to show boot files and such.  Thanks

---

### Post by CharlesA on 2010-05-05
It'll probably say "320GB file system" or something similar. When I boot off a LiveCD, it shows the drives in my machine.

Did you install it as dual boot?

---

### Post by unixisfreedom on 2010-05-05
Well I don't know what's different in your situation, but when I installed 9.1 recently, my windows drive just appears automatically for me under Ubuntu.  Now I _am_ prompted for my password if I ever go there, but then I can read everything just fine...  Maybe is something security related they changed in 10?

---

### Post by Drakkor on 2010-05-05
I installed it with Wubi,the windows installer, here's what it looks like

---

### Post by Bölvaður on 2010-05-05
ohhh wubi is very different because of how it is "installed"

this is from the wubi hompage's faq

>              **Can I access my Windows files from a Wubi installation?**

             Yes, the Windows partitions will be available within the directories /host and /media.
         


---

### Post by _0R10N on 2010-05-05
You should take a look at the Places option of your menu. It lists, among other things, the detected drives. If it's a windows partition, you have probably gave it a name, like "My Win Partition". You should find a "My Win Partition" entry in that menu. After clickin in the menu item, it will probably prompt for a password, that's alright, just enter your password (Ubuntu user).

If everything goes right, you can now access all your Windows data.

---

### Post by paul88 on 2010-05-05
Yours windows files will be on there somewhere.. On the hard disk system. It should ask you for a password try both windows and ubuntu password.
Once on the windows drive locate the folder Users and have a look around there.


Because this is classed as a new drive use ```
cd /media
```

in the terminal and then go from there,  but it might be easier using the GUI file system.

---

### Post by Drakkor on 2010-05-05
Thanks, Bölvaður found them ! :p

---

