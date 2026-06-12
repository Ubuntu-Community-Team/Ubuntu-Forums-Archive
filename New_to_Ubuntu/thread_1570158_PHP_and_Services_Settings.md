---
title: "PHP and Services Settings"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by JJuel on 2010-09-07
I am having a problem. I am taking a php class, and in the book it shows us how to get everything set up in Ubuntu. I ran through everything got all the packages necessary through synaptic installed, and now one of the steps shows starting the web server (apache). It tells me to go through system -> administration -> services, but that is not listed in 10.04. Can someone tell me where I need to go or what I need to do to get this running in a different way.

Thanks in advance!

---

### Post by alphacrucis2 on 2010-09-07
> **JJuel said:**
> I am having a problem. I am taking a php class, and in the book it shows us how to get everything set up in Ubuntu. I ran through everything got all the packages necessary through synaptic installed, and now one of the steps shows starting the web server (apache). It tells me to go through system -> administration -> services, but that is not listed in 10.04. Can someone tell me where I need to go or what I need to do to get this running in a different way.

Thanks in advance!

I believe that the package associated with that gui menu item was broken so it was pulled. You need to use the command line eg.

```
service apache2 start
service apache2 status
service apache2 stop

```


edit: you may have to put sudo in front of those

---

### Post by JJuel on 2010-09-07
Thank you very much!!

---

### Post by JJuel on 2010-09-07
I do have a new problem now, though. I am doing a test program to make sure the server is working right. It tells me to save a test file in the server's document root folder. He said it is more than likely going to be /var/www, but when I try to save that folder it gives me an error saying I do not have permissions necessary to save the file. How do I go about getting these permissions?

Thanks!

---

### Post by alphacrucis2 on 2010-09-07
> **JJuel said:**
> I do have a new problem now, though. I am doing a test program to make sure the server is working right. It tells me to save a test file in the server's document root folder. He said it is more than likely going to be /var/www, but when I try to save that folder it gives me an error saying I do not have permissions necessary to save the file. How do I go about getting these permissions?

Thanks!

You probably need admin access. Save the file you are working on in a folder under your normal home directory and either use ```
sudo cp <source filename> /var/www/<dest filename>
``` to copy the file into /var/www or if you prefer to copy using a graphical prog then use command ```
gksu nautilus
```. Be extremely careful running nautilus with admin rights as you could blow away your system if you delete or modify system files by mistake.

---

### Post by JJuel on 2010-09-07
Thank you copying them worked great! It is going to be a pain in the butt to do that all the time so I wish there was a way I could give myself permissions to that folder, but this work around is good for now.

Thanks again!

---

### Post by temp3 on 2011-03-08
> **JJuel said:**
> ... I am taking a php class ... It tells me to go through system -> administration -> services ...

hey JJuel isn't this [book]("http://www.wrox.com/WileyCDA/WroxTitle/Beginning-PHP-5-3.productCd-0470413964,descCd-ERRATA.html") !?   [;)]("http://www.wrox.com/WileyCDA/WroxTitle/Beginning-PHP-5-3.productCd-0470413964,descCd-ERRATA.html")

i used ```
service apache2 restart
``` but how can i bring Services Settings menu back ?

---

