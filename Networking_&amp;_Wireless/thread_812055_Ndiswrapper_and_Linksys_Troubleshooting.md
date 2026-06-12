---
title: "Ndiswrapper and Linksys Troubleshooting"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by w9tec on 2008-05-29
I recently installed the ndiswrapper program and loaded the required driver for my Linksys WUSB54G USB wireless card. Ubuntu says my card is connected to the wireless network after configuring it though the 'Networks' window, but I am unable to get any internet despite the connection. Has this happened to anyone, or am I just missing something here? Any feedback would be appreciated!

---

### Post by Milardo on 2008-06-11
I would try this-using hardy,open synaptic manager and make sure you check the cd option so it can install stuff from cd, search for ndis and install all those ndis that come up in the search. After installing them in adminstration go to windows wireless drivers. Have your 3 or 2 files from the linksys cd or the one from linksys website. The .cat, .sys, and .inf files. Install new driver the .inf file and next go to the top right icon that looks like a computer monitor. Right click the iconand make sure network and wireless are checked. Next left click it and click the option that is search or find new wireless network not the create or manual option. Now you can enter your wireless security settings and you can easily choose wpa/wpa 2 as well. It should connect pretty fast. I got high speeds as well. To disconnect and unplug adapter (if that is what you have) just uncheck wireless from the icon and then pull out the adapter. To connect to the same wireless network you just have to plug it back in and check wireless if not already checked. You should be connected in about 50 seconds or so. This worked for my linksys wusb54gc.

---

