---
title: "Installing JAVA DEVELOPMENT KIT ..!!"
date: 2011-01-20
forum: New to Ubuntu
---

### Post by vamsi_spr on 2011-01-20
Hello guys , i just downloaded JDK from the website and its been downloaded as .bin file , now when i try to install this on my laptop it says the file is of unknown type ..plz help i wanna install JDK ..!!

---

### Post by gmargo on 2011-01-20
You can installing it using the package system if you enable the "partners" repository and install the **sun-java6-jdk** package.

---

### Post by galfly on 2011-01-22
Silly question: Have you changed the permissions of the bin file by any chance? Maybe something like
```


chmod +x /home/user/Downloads/jdk-6u23-linux-i586-rpm.bin
```Of course you may as well have downloaded jdk-6u23-linux-x64.bin

---

### Post by galfly on 2011-01-22
One more thing:

I actually moved the bin file to /usr/lib/jvm/ to make sure it installs the right location. It first extracted everything under Downloads/ the first time I tried.

Perhaps there's a better way of doing it.

---

