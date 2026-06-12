---
title: "Wireless driver activated and not in use issue."
date: 2010-08-01
forum: New to Ubuntu
---

### Post by =Melissa= on 2010-08-01
**Wireless driver activated and not in use issue.** 			
 			 			 		   		 		 		Hello, 

I am faily new to Ubuntu but have come across an issue scince getting a  new laptop. I'll give what I think to be the whole picture. I am running  Xubuntu and trying to use a windows installed driver which I have  reasearch and have found it is comatable with Ubuntu. The driver is  Broadcom STA Propriertary wireless dritver. The issue is that the driver  comes up as 'Wireless driver activated and not in use" I cannot ficure  out how to get it to use it. the only way to sort it is to everytime I  switch on to go into hardware drivers and remove the driver and then  reenstate it. After doing that everything works and connects no  problems.

Can anyone help me with this? 

Any help is greatly appreciated.

Regards

---

### Post by mikewhatever on 2010-08-01
Actually, the Broadcom STA driver is the native Linux driver.
I suspect, that you must have installed Ndiswrapper, which is the framework to run Windows wireless drivers under Linux. If that's the case, Ndiswrapper probably prevents the native STA driver being used. Run the following command in Applications->Accessories->Terminal, and post the output (the command will remove Ndiswapper if present).
```
sudo apt-get --purge autoremove ndiswrapper-utils ndiswrapper-common
```

---

### Post by ptn107 on 2010-08-01
Make sure the module is loaded:
```
lsmod | grep ^wl
```

if you don't see it listed load it
```
sudo modprobe -i wl
```

and that it loads at each restart:
```
echo "wl" | sudo tee -a /etc/modules
```

---

### Post by =Melissa= on 2010-08-01
Hello,

I didnt have ndiswrapper however the second reply helped greatly as it has fixed the problem.  

Thank you for helping me 

:KS

---

