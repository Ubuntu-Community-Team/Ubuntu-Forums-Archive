---
title: "jnlp from behind proxy"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by realthor on 2008-10-17
Hi, ai am using ubuntu hardy and i have troubles starting a jnlp application from behind a proxy. How is java webstart supposed to be configured so that it picks up gnome global proxy settings. 

Or is there a configuration file for it separate from any global gnome configuration?(i've fount something like:

%java -Dhttp.proxyHost=http://192.168.1.1 -Dhttp.proxyPort=8080 Application

but when run from terminal i get:

bash: fg: %java: no such job

Best Regards.

---

### Post by realthor on 2008-10-17
to be more precise as nobody seems to know or understand what i need: in windows java control panel has a network settings section under general tab where it's set to take the proxy from browser. So when I download the jnlp file from the intranet server I can start the application right away.

What is needed to be set up in ubuntu to achieve this? My Hardy tries to open the file with javaws (java web start) and there is no network settings in javaws.

Thank you for any answer that might help.

---

### Post by ngarthl on 2008-10-28
Make sure you are using sun's webstart
check this with 

sudo update-alternatives --config javaws

if its not:
change it to sun javaws.

Then you can javaws -viewer, which should give you the nework tab.

---

