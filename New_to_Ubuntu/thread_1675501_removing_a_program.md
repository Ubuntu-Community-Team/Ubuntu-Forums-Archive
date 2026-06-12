---
title: "removing a program"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by musendrophilus on 2011-01-25
I installed Cortex Command and want to remove it. This wasn't installed through the Ubuntu Software Center (I think I used deb) and I know in BSD I'd use dpkg and don't rightly know the equivalent for Ubuntu to remove the program.

---

### Post by howefield on 2011-01-25
Have you checked the Software Centre, most installed debs will show there, even when downloaded from a third party source.

---

### Post by musendrophilus on 2011-01-25
> **howefield said:**
> Have you checked the Software Centre, most installed debs will show there, even when downloaded from a third party source.

Yep, it's not in there.

---

### Post by ajgreeny on 2011-01-25
So did you double click on the .deb to install it or use the terminal command ```
sudo dpkg -i packagename
```

Either way you should be able to remove it with ```
sudo dpkg -P packagename
```but this time it will not need the version number as the install did.

---

