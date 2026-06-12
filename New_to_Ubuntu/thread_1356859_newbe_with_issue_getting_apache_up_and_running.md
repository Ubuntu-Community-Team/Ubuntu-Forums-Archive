---
title: "newbe with issue getting apache up and running"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by gibbo1715 on 2009-12-16
Hi all, im new to ubuntu (Installed it for the first time today :) ) and have to say im impressed so far having only ever used windows before but I have one problem and thats getting apache up and running (If i get that working I also want php and mysql)
 
I ve downloaded the latest version (Desktop) and i ve made sure i ve created the cd slowly to get the best copy and i have no errors, i have updated once installed as it suggests and i have tried folowing the instructions for installing the package but for the life of me i cant get it to work
 
The error i get is along the lines of cant install dependancies
 
If anyone can assist me id be very greatful, i do have my linux box linked to my windows home pc and laptop but all the network seems to work fine as does internet access, i really wanted to do my web dev stuff on my linux box so this is really frustrating me :(
 
thanks 
 
Gibbo

---

### Post by cj13579 on 2009-12-16
I would suggest installing LAMP which is a complete web server. It's in the repositories:

```
sudo apt-get install lamp-server
```

Also, try reading this HOWTO: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

