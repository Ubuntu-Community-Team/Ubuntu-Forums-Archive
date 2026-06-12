---
title: "Problem with D-Link DWA171 on ubuntu 16.04 LTS"
date: 2018-12-15
forum: Networking &amp; Wireless
---

### Post by kamil-bartczak06839 on 2018-12-15
I have a problem with an external network card D-LINK DWA-171 - model C on Ubuntu 16.04


When trying to compile official drivers downloaded from [https://support.dlink.com/ProductInfo.aspx?m=DWA-171](https://support.dlink.com/ProductInfo.aspx?m=DWA-171) an error occurs


    ```
praca@Praca:~/Pobrane/20180518_DWA-171C_RTL8811CU_Linux_driver_v5.2.15.2/rtl8821CU_WiFi_linux_v5.2.15.2_27778.20180515_COEX20171114-2525$ make
    make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.15.0-42-generic/build M=/home/praca/Pobrane/20180518_DWA-171C_RTL8811CU_Linux_driver_v5.2.15.2/rtl8821CU_WiFi_linux_v5.2.15.2_27778.20180515_COEX20171114-2525  modules
    make[1]: Entering directory '/usr/src/linux-headers-4.15.0-42-generic'
    CC [M]  /home/praca/Pobrane/20180518_DWA-171C_RTL8811CU_Linux_driver_v5.2.15.2/rtl8821CU_WiFi_linux_v5.2.15.2_27778.20180515_COEX20171114-2525/core/rtw_cmd.o
    In file included from /home/praca/Pobrane/20180518_DWA-171C_RTL8811CU_Linux_driver_v5.2.15.2/rtl8821CU_WiFi_linux_v5.2.15.2_27778.20180515_COEX20171114-2525/include/osdep_service.h:47:0,
                    from /home/praca/Pobrane/20180518_DWA-171C_RTL8811CU_Linux_driver_v5.2.15.2/rtl8821CU_WiFi_linux_v5.2.15.2_27778.20180515_COEX20171114-2525/include/drv_types.h:27,
                    from /home/praca/Pobrane/20180518_DWA-171C_RTL8811CU_Linux_driver_v5.2.15.2/rtl8821CU_WiFi_linux_v5.2.15.2_27778.20180515_COEX20171114-2525/core/rtw_cmd.c:17:
    /home/praca/Pobrane/20180518_DWA-171C_RTL8811CU_Linux_driver_v5.2.15.2/rtl8821CU_WiFi_linux_v5.2.15.2_27778.20180515_COEX20171114-2525/include/osdep_service_linux.h: In function &#8216;_init_timer&#8217;:
    /home/praca/Pobrane/20180518_DWA-171C_RTL8811CU_Linux_driver_v5.2.15.2/rtl8821CU_WiFi_linux_v5.2.15.2_27778.20180515_COEX20171114-2525/include/osdep_service_linux.h:299:8: error: &#8216;_timer {aka struct timer_list}&#8217; has no member named &#8216;data&#8217;
    ptimer->data = (unsigned long)cntx;
            ^
    /home/praca/Pobrane/20180518_DWA-171C_RTL8811CU_Linux_driver_v5.2.15.2/rtl8821CU_WiFi_linux_v5.2.15.2_27778.20180515_COEX20171114-2525/include/osdep_service_linux.h:300:2: error: implicit declaration of function &#8216;init_timer&#8217; [-Werror=implicit-function-declaration]
    init_timer(ptimer);
    ^
    cc1: some warnings being treated as errors
    scripts/Makefile.build:332: polecenia dla obiektu '/home/praca/Pobrane/20180518_DWA-171C_RTL8811CU_Linux_driver_v5.2.15.2/rtl8821CU_WiFi_linux_v5.2.15.2_27778.20180515_COEX20171114-2525/core/rtw_cmd.o' nie powiod&#322;y si&#281;
    make[2]: *** [/home/praca/Pobrane/20180518_DWA-171C_RTL8811CU_Linux_driver_v5.2.15.2/rtl8821CU_WiFi_linux_v5.2.15.2_27778.20180515_COEX20171114-2525/core/rtw_cmd.o] B&#322;&#261;d 1
    Makefile:1551: recipe for target '_module_/home/praca/Pobrane/20180518_DWA-171C_RTL8811CU_Linux_driver_v5.2.15.2/rtl8821CU_WiFi_linux_v5.2.15.2_27778.20180515_COEX20171114-2525' failed
    make[1]: *** [_module_/home/praca/Pobrane/20180518_DWA-171C_RTL8811CU_Linux_driver_v5.2.15.2/rtl8821CU_WiFi_linux_v5.2.15.2_27778.20180515_COEX20171114-2525] Error 2
    make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-42-generic'
    Makefile:1856: recipe for target 'modules' failed
    make: *** [modules] Error 2



```



So I found another solutions 
[http://startusingubuntu.blogspot.com/2014/08/install-driver-for-d-link-dwd-171.html](http://startusingubuntu.blogspot.com/2014/08/install-driver-for-d-link-dwd-171.html) 
However, after making the whole manual, the external network card still does not work.


I was also interested in the mention in readme attached to the official drivers


    ```
Please note that DWA-171C support auto install driver function in Windwos OS,
    user should exit Flash disk mode(default) to active adapter mode.



```The > lsusb command also finds nothing with the name "D-Link".


    ```
praca@Praca:~$ lsusb
    Bus 002 Device 004: ID 0bda:1a2b Realtek Semiconductor Corp. 
    Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
    Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 001 Device 004: ID 1d57:0005 Xenta Wireless Receiver (Keyboard and Mouse)
    Bus 001 Device 003: ID 1a2c:0c21 China Resource Semico Co., Ltd 
    Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
    Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```



PS. External network card works perfectly on Windows10
 
How can I solve this problem?


Thank you in advance for your help.

---

### Post by chili555 on 2018-12-15
Is usb_modeswitch installed?```
sudo dpkg -s usb_modeswitch
```Possibly helpful: [https://askubuntu.com/questions/1080944/automatically-use-usb-modeswitch-for-wifi-usb](https://askubuntu.com/questions/1080944/automatically-use-usb-modeswitch-for-wifi-usb)

---

### Post by kamil-bartczak06839 on 2018-12-15
I did everything that was in the link. And now > lsusb actually returns usb with the name "d-link". 
```

praca@Praca:~$ lsusb
Bus 002 Device 003: ID 2001:331d D-Link Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 1d57:0005 Xenta Wireless Receiver (Keyboard and Mouse)
Bus 001 Device 003: ID 1a2c:0c21 China Resource Semico Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

However, after reinstalling the drivers form link [http://startusingubuntu.blogspot.com/2014/08/install-driver-for-d-link-dwd-171.html](http://startusingubuntu.blogspot.com/2014/08/install-driver-for-d-link-dwd-171.html) .I still don't have a wireless network.

---

### Post by chili555 on 2018-12-15
> However, after reinstalling the drivers form link [http://startusingubuntu.blogspot.com...k-dwd-171.html](http://startusingubuntu.blogspot.com...k-dwd-171.html) .I still don't have a wireless network.That was a very smart guy that gave those instructions; however, the driver is for a different revision of your device and a different chipset.

Please see posts #4 and 5 here: [https://ubuntuforums.org/showthread.php?t=2407625&highlight=rtl8821CU](https://ubuntuforums.org/showthread.php?t=2407625&highlight=rtl8821CU)

---

### Post by kamil-bartczak06839 on 2018-12-15
At the beginning I would like to thank you for your time :) 

Unfortunately, the external network card still does not work.

I used 
```

sudo apt update
sudo apt install build-essential git dkms
git clone https://github.com/whitebatman2/rtl8821CU.git
DRV_NAME=rtl8821CU
DRV_VERSION=5.2.5.3
sudo mkdir /usr/src/${DRV_NAME}-${DRV_VERSION}
cd rtl8821CU
git archive master | sudo tar -x -C /usr/src/${DRV_NAME}-${DRV_VERSION}
sudo dkms add -m ${DRV_NAME} -v ${DRV_VERSION}
sudo dkms build -m ${DRV_NAME} -v ${DRV_VERSION}
sudo dkms install -m ${DRV_NAME} -v ${DRV_VERSION}

```

However, despite the lack of any errors or warnings, it still does not work.
Did I do something wrong?

---

### Post by kamil-bartczak06839 on 2018-12-22
Any help?

---

### Post by chili555 on 2018-12-22
What is the exact response to the terminal command:```
sudo modprobe 8821cu
```Thanks.

---

