---
title: "installing java"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by bubbave3 on 2009-04-14
l finally got Ubyntu 8.10 up and running. l can now surf a bit and would like to install java on the system now.  l have tried but have got lost big time... being the first time in linux and or ubuntu is a great feat for me... so now it is onward to install the java from microsun.  l have the file dloaded but installing it has brought me to a halt... anyone willing to assist me with out laughing too hard would be a ppreciated... lol.. l have Ubuntu 8.10 installed and not sure what info anyone needs to help
thanks.. Pierre

---

### Post by Jakey_TheSnake on 2009-04-14
Assuming you got your java from here: [http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com:80](http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com:80)

There are instructions on site ;)

Other then that, I believe the package ubuntu-restricted-extras will download and install java for you.

---

### Post by ajgreeny on 2009-04-14
Have you searched for sun-java in synaptic?  Enable the multiverse repos and it's all there.

---

### Post by mattyB on 2009-04-14
If you're confused about how to enable different repositories here a brief how to I found on google. Note my search terms were: ubuntu 8.10 install jre 6

[http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/](http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/)

Follow the section of the tutorial through the **Install Sun Java 6** section, ignore the **Setup the default Java version** section onward. The directions may or may not exactly match your install but it should be close enough.

Hope this sends you in the right direction.

Cheers, mattyB

---

### Post by den160593 on 2009-04-14
How would I install Java for the new Firefox 3.1 Beta 3?

---

### Post by Gilabuugs on 2009-04-14
for the runtime environment

install the sun-java6-jre package from synaptic or aptitude

> $ sudo aptitude install sun-java6-jre

and if you want the browser plugin install sun-java6-plugin

> $  sudo aptitude install sun-java6-plugin

$ indicates a terminal prompt

hope that helps, EDIT: didn't see the firefox3 beta question this may or may not work for that

---

