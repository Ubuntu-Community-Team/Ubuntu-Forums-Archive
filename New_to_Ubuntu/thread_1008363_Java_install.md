---
title: "Java install"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by DeathByChocolate on 2008-12-11
Can I install Java?  I downloaded the Linux "RPM self-extracting file".  Is that OK on Ubuntu? 

After  "sudo ./jre-6u11-linux-i586-rpm.bin" I get the extracted jre-6u11-linux-i586-rpm file, and a message saying "rpm: not found".  

Subsequent steps like "sudo ./rpm -lv jre-6u11-linux-i586-rpm" fail because rpm cannot be found.

---

### Post by Duck2006 on 2008-12-11
I found from the terminal installing

sudo aptitude install ubuntu-restricted-extras

was the easy way to install java.

---

### Post by m_l17 on 2008-12-11
Or follow the instructions on this thread:

[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by gandaran on 2008-12-11
> **DeathByChocolate said:**
> Can I install Java?  I downloaded the Linux "RPM self-extracting file".  Is that OK on Ubuntu? 

After  "sudo ./jre-6u11-linux-i586-rpm.bin" I get the extracted jre-6u11-linux-i586-rpm file, and a message saying "rpm: not found".  

Subsequent steps like "sudo ./rpm -lv jre-6u11-linux-i586-rpm" fail because rpm cannot be found.
rpm's don't install in debian systens (ubuntu), to install java use the repositories, open synaptic, scroll down to **sun-java6-plugin** mark for install and hit the apply button, thats all, it'll install all necessary java packages,

---

### Post by Duck2006 on 2008-12-11
And there is this that may help with the *.rpm file.

[http://www.psychocats.net/ubuntu/installingsoftware#lastresorts](http://www.psychocats.net/ubuntu/installingsoftware#lastresorts)

---

### Post by Paqman on 2008-12-11
+1 for ubuntu-restricted-extras

You can't normally install .rpm's on Ubuntu. They're designed for Red Hat-based distros. Ubuntu is based on Debian, so uses .deb's

---

### Post by dragos_iliescu_2005 on 2008-12-11
Best way, use synaptic. Select sun-java6-jre. Dependencies will be installed too.

---

