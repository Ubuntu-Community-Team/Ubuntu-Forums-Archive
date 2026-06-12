---
title: "Wireless network"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by Stjames on 2008-03-27
I have a Hp Pavilion dv5000 with the 43xx chipset family my main problem is that i cant connect to the wireless network.  

so far i have downloaded the drivers then i ran some commands 

     gksu gedit /ect/network/interfaces

then it opened a folder and i put pound (#) signs around all the lines except for 
  
      Auto lo
      iface lo 

now my computer can see the wireless net work but i cant connect and if i restart my computer my wireless singles disappear and i need to reinstall the drivers to get the seetings right so it shows the wireless network. any ideas? any seen this problem before?

---

### Post by dstew on 2008-03-27
Post the output of```
lspci
ifconfig
iwconfig
```

---

### Post by lswest on 2008-03-27
also, post the output of: ```
lshw -C network
``` (make sure you run the command with "C" and not "c")

---

