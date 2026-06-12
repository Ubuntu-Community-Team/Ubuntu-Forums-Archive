---
title: "How do I view what users exist via the command-line?"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by TMcKSmith on 2009-08-27
How do I view what users exist via the command-line on my Ubuntu Server?  

Also, how do I go about deleting users completely?

Thanks.

---

### Post by Liolikas on 2009-08-27
**cat /etc/passwd** | cut -d":" -f1
Not bold part just clean up things.


WARNING MASS DESTRUCTION!!!
sudo userdel -r name

---

### Post by zerhacke on 2009-08-27
Via command line, "who" without the quotes shows who is logged on.

---

