---
title: "How to change the ownership of a file?"
date: 2010-04-01
forum: New to Ubuntu
---

### Post by karthick87 on 2010-04-01
I want to change the ownership of a file to root..How to do this?

---

### Post by mikewhatever on 2010-04-01
sudo chown root:root /path_to/file_name

;)

---

### Post by karthick87 on 2010-04-01
> **mikewhatever said:**
> sudo chown root:root /path_to/file_name

;)


This worked for me,thanks a lot :)

---

### Post by TheNerdAL on 2010-04-01
Mark the thread as [SOLVED] if it is solved. :)

---

### Post by suaf on 2010-04-08
Is there a way to do it without the terminal?

---

### Post by plucky on 2010-04-08
> **suaf said:**
> Is there a way to do it without the terminal?

Yes ```
gksudo nautilus
``` and then navigate to the file you would like to change the ownership and then select **Properties** and change the ownership and permissions.

Good Luck

---

### Post by suaf on 2010-04-08
> **plucky said:**
> Yes ```
gksudo nautilus
``` and then navigate to the file you would like to change the ownership and then select **Properties** and change the ownership and permissions.

Good Luck

Thanks a lot. I had a problem, though. I copied my files from another PC to mine through a local network and I don't know how they lost their owner ("nobody"). The way you told me worked perfectly for the files that already had an owner. For the ones I copied it didn't allow me to change it. If anyone has a suggestion, I'd love to learn something. If not - Cheers : ) I'll use the terminal

---

