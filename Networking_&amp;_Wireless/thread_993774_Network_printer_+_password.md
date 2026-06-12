---
title: "Network printer + password"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by naoli on 2008-11-26
Hi ubunteros,

I'm trying to print on a network shared, canon IR3100C printer.
It is login/password protected : when under Windows, I have to enter a login/password just after asking to print before the machine begins to work.

Under Ubuntu, I added the printer by **System / Admin / Print**

and then I specified **lpd://10.xx.xx.xx** as the printer address. Nothing happens when I try to print.

Browsing the forums, I stumbled upon [http://ge.ubuntuforums.com/showthread.php?t=963792](http://ge.ubuntuforums.com/showthread.php?t=963792) where it's said :

> Open /etc/cups/printers.conf as root and change the URL of your printer to something like this:
Code:

[http://username:password@domain.net/folder/.printer](http://username:password@domain.net/folder/.printer)

Only add username: password, don't change the rest. Then restart cups:
Code:

sudo /etc/init.d/cups restart

My /etc/cups/printer.conf file currently is :
```

# Printer configuration file for CUPS v1.3.9         
# Written by cupsd on 2008-11-20 14:51               
<Printer CanonI>                                  
Info Canon                                      
Location Couloir                                     
DeviceURI lpd://10.xx.xx.xx                           
State Idle                                           
StateTime 1227189086
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>
```

I tried to change **DeviceURI lpd://10.xx.xx.xx** by **DeviceURI lpd://1111@2222//10.xx.xx.xx** where 1111 is the login and 2222 the password, but still no change.

I'm stuck, any idea will be greatly appreciated :D

---

### Post by naoli on 2008-11-28
up ?

---

### Post by olivesandtrees on 2008-11-28
You are using CUPS not the Berkeley printing system so using the LPD command is incorrect (well CUPS does have a backend to support LPD but it probably better to use something else).

If Windows machines are having no problems printing to it, I would try adding the printer through Samba 
smb://username:password@server/printersharename

---

### Post by naoli on 2008-11-28
Ok thanks a lot for the answer.

How can I know the printer share name ? (it's on a network, I've got no idea what the admins have decided). Since it is a Canon IR3100C, I tried :

smb://xx@yy/10.xx.xx.xx/IR3100C

When trying to print a test : 
> 
Unable to connect to CIFS host.

:(

---

### Post by olivesandtrees on 2008-11-28
Try deleting the printer and adding it again in the CUPS browser interface by typing [http://localhost:631/](http://localhost:631/) into Firefox's address bar.

---

### Post by naoli on 2008-11-28
Hum, I've just tried, no change... :(

---

### Post by naoli on 2008-12-01
Does anyone have the same problem OR*has any idea ?

:)

---

