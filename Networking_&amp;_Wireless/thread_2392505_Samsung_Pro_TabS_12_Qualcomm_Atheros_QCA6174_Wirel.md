---
title: "Samsung Pro TabS 12 Qualcomm Atheros QCA6174 Wireless Adaptor not Found"
date: 2018-05-22
forum: Networking &amp; Wireless
---

### Post by herbertfish on 2018-05-22
Hi,

I have recently installed 18.04 and I am having the same wireless adapter issues many others have posted. I have tried to follow all the steps in the various other threads but I am getting nowhere fast/slowly.

Link to wireless script below. If anyone could assist that would be excellent.

Thanks in advance!

[http://paste.ubuntu.com/p/vHWVtVqWxj/](http://paste.ubuntu.com/p/vHWVtVqWxj/)

---

### Post by jeremy31 on 2018-05-22
I would try ```
sudo apt update && sudo apt-get install --reinstall linux-firmware
```
Reboot

---

### Post by herbertfish on 2018-05-28
Apologies for the delay in response. I did:

> sudo apt update && sudo apt-get install --reinstall linux-firmware

And mentioned in another post:

> sudo apt-get install git build-essential
git clone [https://github.com/jeremyb31/ath-4.15.git](https://github.com/jeremyb31/ath-4.15.git)
cd ath-4.15
cp /usr/lib/modules/$(uname -r)/build/.config ./
cp /usr/lib/modules/$(uname -r)/build/Module.symvers ./
make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
sudo cp ath.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless/ath

To make it work, I changed this two lines from:   

> 
     Code:

     cp /usr/lib/modules/$(uname -r)/build/.config ./ 
cp /usr/lib/modules/$(uname -r)/build/Module.symvers ./ 

to  

     Code:

     cp /lib/modules/$(uname -r)/build/.config ./ 
cp /lib/modules/$(uname -r)/build/Module.symvers ./

Many thanks for the quick assistance.

---

### Post by jeremy31 on 2018-05-28
Thanks, I finally fixed the other post as I normally use /usr/src/$(uname -r) for the Module.symvers and config files, likely just had a copy paste error

---

