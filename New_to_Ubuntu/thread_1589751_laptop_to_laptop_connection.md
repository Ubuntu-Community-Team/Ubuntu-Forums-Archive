---
title: "laptop to laptop connection"
date: 2010-10-06
forum: New to Ubuntu
---

### Post by musendrophilus on 2010-10-06
I have two laptops. One has a dead screen but perfectly servicable using Win2K. The other one just received Ubuntu within the last half hour.
How do I go about connecting each computer so I can bring my files over to the Ubuntu machine?

---

### Post by e79 on 2010-10-06
The best way to do it if you have Ethernet connection and you know the IP addresses for both machines would be to try to connect to the default Administrative share of your Windows (represented by **c$**) and copy the files over to your Ubuntu machine. This method assume you have administrative rights on your Windows. See the attached screenshot for example only and change the info accordingly.

From your Ubuntu installation, go to :
Places --> Connect to Server

and enter the information accordingly to your installation. You should then be able to access the whole C: drive on your Win2K. This will NOT work if you don't have a password set for your username in Windows, just so you know.

Hope this helps

---

### Post by jtarin on 2010-10-06
As e79 states.....a lot depends on your ability to connect. How are you connecting?

---

