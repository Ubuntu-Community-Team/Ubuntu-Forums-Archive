---
title: "wireless: AR5007EG on Gutsy"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by ntlam on 2007-10-24
I just upgraded feisty to gutsy and the wireless disappeared.
Has anyone got AR5007EG works on gutsy yet?

---

### Post by oedha on 2007-11-01
I have acer aspire 4520 and this unit has prolems in windowsXP and linux
I solved winxp within a week and stuck in linux for few months especially in vga, wireless and sound.
I just make the wireless online yesterday. Here is what i've done

1. download the AR5007EG windriver from [ftp://ftp.work.acer-euro.com/notebook/aspire_5100/driver/](ftp://ftp.work.acer-euro.com/notebook/aspire_5100/driver/)
2. I online by wired to get ndiswrapper
3. after that i go to terminal then type : sudo rmmod ath_pci
4. put the ath_PCI to blacklist by : sudo vi /etc/modprobe.d/blacklist-common
5. type in ( insert ) a line : blacklist ath_pci
6. save it and restart the computer
7. after reboot, i extract the wireless_driver and copy all files to documents folder
8. i removed the folders, so document folder contains single files
9. go to System - Administration - Windows Wireless Drivers
10. I installed the driver by pointing to net5211.inf in documents folder
11. click on configure button 
12. I saw the wireless appeared and then i set it up
13. open terminal then type : sudo ndiswrapper -m
14. reboot

this way was adept from [http://docs.google.com/View?docid=dtvgpkz_46fv8dwf](http://docs.google.com/View?docid=dtvgpkz_46fv8dwf)
i just did something else / way. because when i follow the steps above. it's not working

i hope.....your problem can be fixed.
OedhA

---

