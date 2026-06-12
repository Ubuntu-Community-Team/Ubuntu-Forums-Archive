---
title: "I need a shared folder over www"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by CameronCalver on 2008-03-13
Hello i just set up an epson 4490 photo on ubuntu and i have a problem. I work from home and i scan files etc from home and then put them on a thumb drive and give them to my boss every week but i thought there would be a much easier solution to this problem because the computer at the work is a ubuntu server running edgy i think.
at home i am running gutsy
would there be a way to connect to a folder on the server so i can just drag files from my computer into that folder and then he can check in that folder and there will be the files?
internet speed is no problem we are both on 1.5mb/s and they are only very small files anyone have any idea?

---

### Post by tubasoldier on 2008-03-13
I'm not sure about gnome, but i do know that KDE has an applet that serves as an HTTP file server through your ip address. As in [http://your.ip.address:8080](http://your.ip.address:8080)

Good luck with a gnome equvalent... I personally don't know of any. 
Other than that you could go all out with a webserver...

---

### Post by CameronCalver on 2008-03-13
yeah ok than anyone?

---

### Post by acirilo on 2008-03-13
what about you using FTP to a folder on the server...

fireFTP is too easy... :)

---

### Post by CameronCalver on 2008-03-13
oh that thing is nice but how do u work it what do u do for the host?

---

### Post by acirilo on 2008-03-13
the ftp has a connection manager that ask for host name (the server ip will work) user name & password (your log in on the server) once you make a connection it opens 2 windows for example: left side is local files right window pane is server.. ftp uses commands "put" and "get" to upload files or download "files" 

the setup of ftp on the server is basically making sure the ftp service is install and the process started...

here is some links to give you some more idea

[http://www.cyberciti.biz/faq/ubuntu-vsftpd-ftp-service-server/](http://www.cyberciti.biz/faq/ubuntu-vsftpd-ftp-service-server/)

[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)


there is a command line ftp but i would stick to a gui like fireftp.

---

### Post by CameronCalver on 2008-03-14
but this is all local isnt it i need a way to go over the internet

---

### Post by Eiríkr on 2008-03-14
FTP is over the internet.  FireFTP likewise works over the internet.  I just used it not half a minute ago to upload a bunch of files to a client's FTP server.  They're in Tokyo, I'm in California.  That's definitely not just local.  :o

FireFTP is a small download, and is just an extension in Firefox that you can disable or remove at any time.  Why not just install it and try it out, play around with it, and learn its capabilities that way?  It'll be a heck of a lot faster than having us try to explain it to you.  :)

Cheers,

Eiríkr

---

### Post by CameronCalver on 2008-03-14
yeah i am using it now so all i have to do is set up proftp on the server and then i just can connect to it on my computer here without any port forwarding?

---

### Post by Eiríkr on 2008-03-14
Depends on how your home LAN is set up.  What kind of service do you have: dial-up, DSL, cable, something else?  Do you have a router with multiple computers, or is your computer hooked straight into the modem?  If you've got a router, you'll likely need to work out some kind of port forwarding or similar arrangement.  If you're plugged directly into the modem, you might not need to do that.

PS -- I'm heading out of town over the weekend, so someone else will have to pitch in here.  :)

---

### Post by CameronCalver on 2008-03-14
hahha NO!!
yeah routed and dsl
also with this proftpd thing it will only let me connect with my username and password but i dont want to give that out to people? i want to be able to connect with a username like ftp

---

### Post by CameronCalver on 2008-03-14
ok guys i fixed it please try
 [ftp://124.170.112.137](ftp://124.170.112.137) 
username : cameron
password : wordpass

---

### Post by acirilo on 2008-03-14
it works.. now i would change the passwords and such..before it becomes a "warez" site :) 

i left my avatar up for ya :)

---

### Post by CameronCalver on 2008-03-14
yeah i saw that thanks was wondering if uploads worked thanks and if people upload stuff onto it it wont affect my download cap will it ? wat if someone uploads to it and then someone downloads that uploaded file that wont affect my cap will it?

---

### Post by acirilo on 2008-03-14
well....you can set it up so thru your quota settings to limit the size of your folders. (download, upload) or if you are meaning bandwidth cap..but i think you said you was on a LAN so that shouldn't be an issue.

---

