---
title: "Update Manager can't install updates"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by vanSnow on 2009-06-04
Hi folks,

I have updated to *Ubuntu 9.04* about one month ago and *Update Manager* worked just fine afterwards. But now it's behaving weird:
[LIST=1]

[*] *Update Manager* reports of 9 updates.
[*] I press the *Install Updates* button.
[*] I type in my password.
[*] It says *Reading package information*.
[*] No updates is installed and I am back to 1.

[/LIST]
I have tried to uncheck all but one of the updates but still Update Manager can't install.

Help needed! Thank you.

//van Snow

---

### Post by Celauran on 2009-06-04
Have you tried from the console? Are there any error messages?

---

### Post by vanSnow on 2009-06-04
Hi Celauran, when I start it from the terminal it just starts up normally but with the same problem. Should I type in some more to open it in troubleshooting mode?

---

### Post by zvacet on 2009-06-05
```
sudo apt-get update && sudo apt-get upgrade
```

What kind of message do you get after these commands?

---

### Post by prvteprts on 2009-06-05
> **zvacet said:**
> ```
sudo apt-get update && sudo apt-get upgrade
```

What kind of message do you get after these commands?

+1

I have experienced this problem. Update us on this.

---

### Post by markharding557 on 2009-06-05
any other error messages is it downloading the updates

---

### Post by vanSnow on 2009-06-05
Hi zvacet, this command downloaded and installed the updates. Nice but what about the next time I need to upgrade? I still don't think the Update Manager is working now. What could I do?

Thank you

---

