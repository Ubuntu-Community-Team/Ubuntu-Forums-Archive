---
title: "installing java6-docs in ubuntu 9.04"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by bhargava470 on 2009-05-17
Hi ,

Can someone tell me how to install java6-docs in ubuntu 9.04. IT shows some error everytime i try to install it. it asks me to go to  the java website and download the files and place in /tmp ... i couldnt get exactly what it means....

Thanks

---

### Post by Joeb454 on 2009-05-17
You need to go to [this site]("http://java.sun.com/javase/downloads/index.jsp") and download Java SE 6 Documentation, and then run the following command, and try to install again :)

Assuming you download the .zip file to your desktop:

```
sudo mv ~/Desktop/jdk-6u10-docs.zip /tmp && sudo chown root:root /tmp/jdk-6u10-docs.zip
```

It should then install :)

---

### Post by bhargava470 on 2009-05-17
> **Joeb454 said:**
> You need to go to [this site]("http://java.sun.com/javase/downloads/index.jsp") and download Java SE 6 Documentation, and then run the following command, and try to install again :)

Assuming you download the .zip file to your desktop:

```
sudo mv ~/Desktop/jdk-6u10-docs.zip /tmp && sudo chown root:root /tmp/jdk-6u10-docs.zip
```It should then install :)



Thank you Joeb454. That worked....

---

