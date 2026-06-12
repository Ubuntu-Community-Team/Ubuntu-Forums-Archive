---
title: "Virtualbox 3.0 Dependencies Problem"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by terrykiwi83 on 2009-10-25
Currently am running Virtualbox OSE on 9.04 64bit and am looking at upgrading to Virtualbox 3.0. Only problem is I get the below error about dependencies. I have searched the net to no avail and also searched through the Virtualbox website again to no avail. And as I have always been able to find my answers here am hoping you guys can help me.

```

virtualbox-3.0:
  Depends: libstdc++6 (>=4.4.0) but 4.3.3-5ubuntu4 is to be installed

```

Thanks in advance

---

### Post by yeats on 2009-10-25
Are you downloading the .deb directly, or using the VirtualBox repositories?  I use the repositories and have no issues...

---

### Post by terrykiwi83 on 2009-10-25
> **chrissharp123 said:**
> Are you downloading the .deb directly, or using the VirtualBox repositories?  I use the repositories and have no issues...

I have tried both methods and both have the same problem.

---

### Post by howefield on 2009-10-25
Are you using the appropriate package for your version of Ubuntu ?

The version of the file you need is the one found in Karmic, so just wondering which Virtualbox file you are using.

---

### Post by terrykiwi83 on 2009-10-25
Have just checked and it seems in the software sources I was using the Karmic packages :| (how embarassing) have changed it to the Jaunty ones and gonna try it again.

Thanks for the help :) sorry for my stupidity.

---

### Post by howefield on 2009-10-25
No worries, if you need some more help, you know where to come :)

---

