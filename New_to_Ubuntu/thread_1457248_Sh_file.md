---
title: "Sh file"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by UpSignal on 2010-04-18
Hi guys, weird thing going on here. I have a script .SH that launchs a java program, anyway, i made the script executable with the "sudo chmod +x" , so, if i click on it and choose execute, it opens no problem, but when i add a shortcut on my main menu, i just point to the .SH file, and it doesn't run! Maybe some parameter missing? my shortcut goes directly to the file, no extra commands. it was supposed to open, or at least give an error. :s
any ideas?

---

### Post by xumuk37 on 2010-04-18
> **UpSignal said:**
> Hi guys, weird thing going on here. I have a script .SH that launchs a java program, anyway, i made the script executable with the "sudo chmod +x" , so, if i click on it and choose execute, it opens no problem, but when i add a shortcut on my main menu, i just point to the .SH file, and it doesn't run! Maybe some parameter missing? my shortcut goes directly to the file, no extra commands. it was supposed to open, or at least give an error. :s
any ideas?



try with ```

sudo chmod 777 file.sh
sh /pathto/file.sh
```

---

### Post by Perfect Storm on 2010-04-18
Try making the launcher like this;

```
sh -c "cd <distination> && ./<script file>"
```

---

### Post by UpSignal on 2010-04-18
> **Artificial Intelligence said:**
> Try making the launcher like this;

```
sh -c "cd <distination> && ./<script file>"
```

That worked for me. thanks for the replies guys :) always learning, everyday.
cheers

---

