---
title: "Why is port 5800 (vnc-http) open on my Kubuntu box?"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by applegrew on 2007-08-08
I am using Kubuntu and have configured krfb to accept uninvited remote connection. I can see port 5900 open (which is ok), but I can also see port 5800 open. NMap shows port 5800 as vnc-http. I was expecting that typing [http://my-ip:5800/]("http://my-ip:5800/") would download the java applet into my web browser and let me access my desktop remotely. But, when I type that url then the browser waits for eternity (it doesn't even time out).

Where am I going wrong? Do I need anything else to be installed to make this work? I have tightvnc-java package installed.

---

### Post by lavinog on 2007-08-08
are you using a different computer to test out the connection or are you using the local machine?

does the browser display anything or is it a blank screen?

do you have java installed on the browser? Which browser are you using?
try testing your java install here:
[http://java.com/en/download/installed.jsp]("http://java.com/en/download/installed.jsp")

---

### Post by applegrew on 2007-08-08
> **lavinog said:**
> are you using a different computer to test out the connection or are you using the local machine?

does the browser display anything or is it a blank screen?

do you have java installed on the browser? Which browser are you using?
try testing your java install here:
[http://java.com/en/download/installed.jsp]("http://java.com/en/download/installed.jsp")
I am tryingt this on the same computer and the browser displays just the white page and it seems it is waiting for the page.

I have Firefox and Java is installed. I have ran java applets in Firefox.

Your given link gives me the result:-
```
Oops! You don't have the recommended Java installed.
Your Java version is 1.6.0. Please click the button below to get the recommended Java for your compute
```
I think JRE 1.6.0 is enough for this.

---

### Post by lavinog on 2007-08-08
it could be your vnc server doesn't have loopback enabled.
if you have another computer handy try seeing if you can connect using that one.

give me a min and I can check on if there is a loopback setting.

> I think JRE 1.6.0 is enough for this.
I think thats right

---

### Post by lavinog on 2007-08-08
ok i found something that says that even if you access it from the local machine you have to use the machine name and not localhost
ie:
[http://kubuntu:5800](http://kubuntu:5800)
(if your machine name is kubuntu)

---

