---
title: "Apache web server"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by mash.ky on 2009-01-22
I have installed netbeans 6.5 in to my laptop. My ubuntu version is 8.10. I ahv installed the full package with Apache Tomcat. But when i type localhost in a browser and enter it says failed to connect. how can i solve this problem?](*,)

P.S: i hav installed lokkit in my laptop and DHCP is selected.

---

### Post by utnubuuser on 2009-01-22
You restarted x  to make sure the server is running.  ctrl+alt+backspace

maybe: sudo /etc/init.d/apache2 restart  or something similar.

---

### Post by hyper_ch on 2009-01-22
Xserver has nothing to do with apache.

how did you install apache?

---

### Post by mash.ky on 2009-01-22
hey i think now it's working. first i haven't install apache2 seperately. after intalling it (sudo aot-get install apache2) now it's working nicely i think. when i type 'localhost' in my browser and enter then a page displayed saying it works! is tomcat depending on apache or is it another version of apache? and one more thing. i need to do some configurations on apache and see what's around it as i'm new to apache. advice me!:p

---

### Post by mash.adict on 2009-04-16
My understanding is that the Apache web server serves port 80 - the default http port, whilst tomcat provides JSP and application server support and responds on port 8080 by default, although tomcat can be configured to respond on port 80.

Mighty MASH Adict

---

### Post by mash.ky on 2009-04-16
nw i hav configured my tomcat server to port 8080 and installed axis on it. it works fine.

---

### Post by plukich on 2009-06-17
Hi, I'm having some issues setting up Tomcat6 on Ubuntu 8.10 to host a personal website.  I've searched around and read through a few HowTo's but can't seem to get a complete handle on it.

I'm pretty new to Ubuntu and still getting used to installing programs through apt-get.  I've used "sudo apt-get install tomcat6" to download & install Tomcat.  This apparently placed everything in /usr/share/tomcat6/.  However, when I try to start/stop the server using "sh /usr/share/tomcat6/bin/shutdown.sh" I recieve the message:
"Cannot find /var/lib/tomcat6//bin/setclasspath.sh
 This file is needed to run the program."

To my knowledge, I haven't done anything under /var/lib/tomcat6/ but as I said I'm still somewhat new to this OS and filesystem. Can anyone tell me what should have been my first step after letting "sudo apt-get install tomcat6" complete?

---

### Post by kirgy on 2009-07-02
Im having problems with an apache server too.

When I type in the 'localhost' i get the server showing the 'www' directory. But when I try and access this on another PC but typing in the local IP (192.168.0.9) im just geting the following after a fairly long wait:

[INDENT][I]You tried to access the address [http://192.167.0.9/](http://192.167.0.9/), which is currently unavailable. Please make sure that the Web address (URL) is correctly spelt and punctuated, then try reloading the page.
[/I][/INDENT]

What could be the problem? Do I have to configure apache in some way?

---

### Post by alphacrucis2 on 2009-07-02
> **kirgy said:**
> Im having problems with an apache server too.

When I type in the 'localhost' i get the server showing the 'www' directory. But when I try and access this on another PC but typing in the local IP (192.168.0.9) im just geting the following after a fairly long wait:

[INDENT][I]You tried to access the address [http://192.167.0.9/](http://192.167.0.9/), which is currently unavailable. Please make sure that the Web address (URL) is correctly spelt and punctuated, then try reloading the page.
[/I][/INDENT]

What could be the problem? Do I have to configure apache in some way?

Was that a typo? The error message says 192.**167**.0.9 which suggests you tried to browse to the wrong address?

---

