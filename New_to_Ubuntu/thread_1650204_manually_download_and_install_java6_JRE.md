---
title: "manually download and install java6 JRE"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by Gav1991 on 2010-12-21
how can I download JRE and install it manually?
I have downloaded "openjdk-6-jre_6b18-1.8.3-0ubuntu1~8.04.2_i386.deb" with 235 KB .
Can this do something for me and what can I do with it?

---

### Post by Gav1991 on 2010-12-21
I want to run a .jar file.
I downloaded "openjdk-6-jre_6b18-1.8.3-0ubuntu1~8.04.2_i386.deb" . What can I do with It?
Can this do something for me?
How can I download and install JAVA 6 JRE  "Manually"?

---

### Post by seawolf167 on 2010-12-21
To install a .deb file:

Change to the directory where the file is stored

```
cd /path/to/file
```

Probably will be

```
cd ~/Downloads
```

Install the package

```
sudo dpkg -i nameofpackage.deb
```

---

### Post by arochester on 2010-12-21
"How To Install Java (JRE And Java Plugin) In Ubuntu 10.10 Maverick Meerkat [Repository]" - [http://www.webupd8.org/2010/09/how-to-install-java-jre-and-java-plugin.html](http://www.webupd8.org/2010/09/how-to-install-java-jre-and-java-plugin.html)

---

### Post by Gav1991 on 2010-12-21
It says openjdk-6-jre-headless is NOT installed.

---

### Post by Gav1991 on 2010-12-21
I said I want to install it manually with a .deb file.

---

### Post by ppv on 2010-12-21
So you may need to install that first. Rather a simpler way to get java would be to use the software center to search for java and then install the one you want. By using this the dependencies will also be installed.

---

### Post by Gav1991 on 2010-12-21
I knew that.
I want to install it without system internet access. I want to download them and install.
Where can I download "openjdk-6-jre-headless"?

---

### Post by ppv on 2010-12-21
[http://packages.ubuntu.com/search?keywords=openjdk-6-jre-headless](http://packages.ubuntu.com/search?keywords=openjdk-6-jre-headless)

---

### Post by s.fox on 2010-12-21
Please do not create threads on the same problem. Thank you.

Threads Merged.

---

