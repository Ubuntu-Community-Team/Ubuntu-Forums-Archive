---
title: "FTP help for a beginner"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by hoptimusPrime on 2010-06-16
hello

i would like to be able to access my files at home over the internet using FTP and VNC

when connected to my LAN at home, i can type my 192.168... IP in windows explorer on my laptop, and i am able to view my files on my "server" desktop (running Ubuntu).  In Firefox, if i type the [ftp://192.168](ftp://192.168)... into the browser, it says:

**[SIZE=1]It works![/SIZE]**

 This is the default web page for this server.
 The web server software is running but no content has been added,  yet.


i can also use VNC from within my LAN.  i think all sharing is enabled

ive signed up for a DynDNS account and created a host name or whatever, but im not sure what to do next

i would like to be able to connect to my Ubuntu computer at home from school or work over the internet, but i am unfamilliar with FTP and networking and am stuck here.

How do i 'add content' to my FTP / DynDNS server? 


any help would be great, thanks!

---

### Post by spiky001 on 2010-06-16
What have you installed on Ubutnu server i.e ssh or samba?

---

### Post by hoptimusPrime on 2010-06-16
i have Lucid desktop on my server computer, samba is installed and folders are shared.

in my quest for a solution, i may have also installed ssh

thanks for the quick reply

---

### Post by cj.surrusco on 2010-06-16
You need to open your sever up in either a web or file browser. It is the same as doing it from a network computer, you just have to use your actual IP instead of your local IP. 
```
ftp://(your IP adress)
```

---

