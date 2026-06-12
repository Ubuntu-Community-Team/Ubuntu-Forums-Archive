---
title: "No wifi after BIOS update and suspend THINKPAD E540"
date: 2015-05-15
forum: Networking &amp; Wireless
---

### Post by bystricanp on 2015-05-15
Hello,
I have a Thinkpad E540 notebook with Ubuntu 14.04 installed. All worked perfectly, since I today updated BIOS from version 2.12 to 2.18.
Now, afrer suspend and wake-up, wifi not working, I must restart the computer. After this wifi work.

I tried several tips:
-when I use "nmcli nm sleep false" it returns "Error in sleep: Already awake"

-the command "nmcli nm" says:
```
>before awake:
RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN     
running         connected       enabled         enabled    enabled         disabled 

>after awake:
RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
running         disconnected    disabled        disabled   enabled         enabled  

Adding a line to "/etc/pm/config.d/config" (2nd post here) not works too.

Command "sudo service network-manager restart" now work too.

Hardware info:
network
       description: Wireless interface
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 73
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
```




Can anyone help please? Thank you and have a nice day :)

---

### Post by wildmanne39 on 2015-05-15
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here.  Hopefully someone will stop in to help, I am going to be driving most of the day and will not be available much.
Thanks

---

### Post by bystricanp on 2015-05-18
Hello,
thank for your reply. I executed your script before and after suspend. Both outputs are here as attachment. 

[ATTACH]262055[/ATTACH]
[ATTACH]262056[/ATTACH]

---

