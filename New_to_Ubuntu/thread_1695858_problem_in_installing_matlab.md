---
title: "problem in installing matlab"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by tiwaria9034 on 2011-02-26
Can somebody please help me in getting matlab installed in ubuntu 10.10 ?

Assuming I am in the matlab folder, I typed the following code in terminal
"sudo sh ./install -t"

then I got a screen stating matlab terms & condition which I agreed to accept by pressing a key.

Just after this I get an error message saying
"/home/abhishek/Desktop/matlab/update/install/main.sh: 582: /home/abhishek/Desktop/matlab/update/bin/glnx86/xsetup: Permission denied"

I feel myself in deep trouble.

---

### Post by TeoBigusGeekus on 2011-02-26
Could it be that xsetup is a script that doesn't have execution permissions?
Try
```
chmod +x home/abhishek/Desktop/matlab/update/bin/glnx86/xsetup
```

---

