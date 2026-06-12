---
title: "linux mint-trying to install java runtime"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by irish66 on 2009-10-15
Hi, I'm trying to install java runtime envoirment
downloaded as 
/home/martin/Desktop/jre-6u16-linux-i586.bin
when i try to open it, i get message that there is no application to open.
it is on the desktop.
i googled for help
and tried
chmod 700 jdk-1_5_0_06-linux-i586.bin
but am told there is no such file or directory

i also tried
sudo chmod jre-6u16-linux-i586-rpm.bin
but get message
chmod: missing operand after `jre-6u16-linux-i586-rpm.bin'
Try `chmod --help' for more information.

---

### Post by sandyd on 2009-10-15
> **irish66 said:**
> Hi, I'm trying to install java runtime envoirment
downloaded as 
/home/martin/Desktop/jre-6u16-linux-i586.bin
when i try to open it, i get message that there is no application to open.
it is on the desktop.
i googled for help
and tried
chmod 700 jdk-1_5_0_06-linux-i586.bin
but am told there is no such file or directory

i also tried
sudo chmod jre-6u16-linux-i586-rpm.bin
but get message
chmod: missing operand after `jre-6u16-linux-i586-rpm.bin'
Try `chmod --help' for more information.
```

sudo chmod 777 jre-6u16-linux-i586-rpm.bin

```

and your installing the wrong version - the version listed above is for RPM based distros while linuxmint and ubuntu are debian based.

why don't you just do
```
sudo apt-get install sun-java6-bin sun-java6-plugin

```

---

### Post by irish66 on 2009-10-17
That worked, thank you very much

---

