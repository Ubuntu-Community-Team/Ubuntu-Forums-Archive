---
title: "Cant install my Intel e1000e Ethernet/Network Adapter"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by abhinav90 on 2008-10-03
Hey 
i am on Ubuntu 7.10 Gutsy

in Network Manager i only get a modem connection option, the wired connection and wireless networks are missing.

To solve this problem i first installed Ndiswrapper and successfully installed the driver of my Broadcom network card onto ubuntu.

However, the problem still not solved i realised that on lscpi command i got ethernet controller: Intel **unknown device**. 

Then i downloaded the required e1000e folder driver for my Intel PRO PCI-E 825667 from intels website.

However when i access the directory and start install using make install the operation starts but then it comes cannot create directory "lib/modules/2.6.22-14-generic/kernel/drivers/net/e1000e": Permission denied.

On reaching this directory i found that an e1000 directory was already present and maybe thats why i cannot install the e1000e folder driver. What should i do as my ethernet card is not getting senesed and i cannot use the internet.

I have a Dell E6400 Latitude Laptop.

Please help

---

### Post by Kuroyume on 2008-10-03
did you run make install as root? it seems it cannot write top the modules directory.

---

### Post by abhinav90 on 2008-10-03
I am sorry i am a linux newbie how do you make install as root and do you think that this is the reason why no wired or wireless network links are showing in the network manager.

Would it help to upgrade to version 8

Thanks for your help

---

### Post by abhinav90 on 2008-10-03
hey i got about installing it from root but now i am getting some cannot copy catman cache error what should i do

---

### Post by abhinav90 on 2008-10-03
hey thanks for the help i got it to work, now wired connection is coming and it goes on the internet,

However, the wireless connection icon is still not coming.

I still have to sort that out.
In Ndisgtk it shows one icon for bcmwl6 and hardware present = yes. This happened after i installed this driver for my broadcom wireless card. However, the problem was still not solved. What should i do??

---

### Post by Ayuthia on 2008-10-03
> **abhinav90 said:**
> hey thanks for the help i got it to work, now wired connection is coming and it goes on the internet,

However, the wireless connection icon is still not coming.

I still have to sort that out.
In Ndisgtk it shows one icon for bcmwl6 and hardware present = yes. This happened after i installed this driver for my broadcom wireless card. However, the problem was still not solved. What should i do??

I would create another thread for your wireless issue.  It will allow others who have more experience with your wireless to be able to find your question and help.

Anyway, the issue with your wireless is with the driver.  You are trying to use bcmwl6 and that is not currently supported (it is Vista's wireless driver).  You will need to find a bcmwl5 version.

---

### Post by abhinav90 on 2008-10-03
Thanks for the tip i think that will work

Thanks once again

---

