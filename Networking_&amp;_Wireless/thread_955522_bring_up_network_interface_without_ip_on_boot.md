---
title: "bring up network interface without ip on boot"
date: 2008-10-22
forum: Networking &amp; Wireless
---

### Post by monkeyanengineer on 2008-10-22
I searched the forums but couldn't find anything to solve this... i am sure i missed it but i can't find it so i'm asking for help.  i have ubuntu server 7.10 and i run vmware server 2.  What i need is to bring up eth1 on bootup so that my vm can access the internet.  i don't want eth1 to have an ip or to look for dhcp.  all i want is for the network interface to be up.  i can do it manually by typing 

'sudo ifconfig eth1 up'

 but i want that to run automatically on boot so that i don't have to run it manually on reboot. thanks in advance!

---

### Post by EagleIJoe on 2008-12-05
Have a look a the man page of interfaces. Specifically the inet section will tell you that "manual" is what you are looking for.

---

### Post by Iowan on 2008-12-05
There IS another thread that posed the same question - I'll look for it. 
Found it: [http://ubuntuforums.org/showthread.php?t=830481]("http://ubuntuforums.org/showthread.php?t=830481")

---

