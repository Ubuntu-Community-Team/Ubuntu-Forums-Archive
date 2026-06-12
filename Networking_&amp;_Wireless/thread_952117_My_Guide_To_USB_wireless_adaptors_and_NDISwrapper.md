---
title: "My Guide To USB wireless adaptors and NDISwrapper"
date: 2008-10-18
forum: Networking &amp; Wireless
---

### Post by ashleyslaterwinter on 2008-10-18
ndiswrapper install instructions

1. open terminal and type "su" then the password

2. then type "lsusb" then "lsusb -n" and write down the device id eg 1a2b:3c4d

3. download the ndiswrapper source code and save it in "usr/src/ndiswrapper-X.XX" were X is the version. if the folder if not there then create it

4. then go back to the terminal and type "su ashley" were ashley is your username

5. then type "cd /usr/src/ndiswrapper-X.XX"

6. then type "tar -xzf *"

7. then type "cd *"

8. then type "make"

9. then type "su" then the password

10. then type "make install"

11. now you should have a working version of ndiswrapper

12. now you have to download the development pakages for your device from the ndiswrapper website

13. then save it to "usr/src/ndiswrapper-X.XX"

14. if you should download a "EXE" files then type "cd .." then "mv ../*.EXE ." then "mkdir temp" then "mv *EXE temp" then "cd temp"

15. now type "unzip XXXXX.EXE" were XXXXX is the name of your driver

16. now you will need to look for a ".inf" file and a ".sys" file with the same name eg driver345.inf and driver345.sys

17. then type "ndiswrapper"

18. then type "ndiswrapper -i driver345.inf" were driver345.inf is the name of your driver

19. now you have installed the Windows driver for you device

20. then type "ndiswrapper -m"

21. then type "ifconfig wlan0 up"

22. then type "ifconfig"

23. then type "iwlist wlan0 s" this will scan for wireless networks

And now you shoudl be able to connect to a wireless network

---

