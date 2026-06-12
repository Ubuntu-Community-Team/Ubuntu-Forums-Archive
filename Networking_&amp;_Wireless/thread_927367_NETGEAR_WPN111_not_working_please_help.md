---
title: "NETGEAR WPN111 not working please help"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by funkyhair143 on 2008-09-22
ok now I know im a noob to ubuntu im just installed it because i got a bit tired of XP and wanted to try something new. So now im dual booting XP and Ubuntu. 

The problem is the my wireless NETGEAR WPN111 won't work. It works fine when I boot back on to XP but on Ubuntu it doesn't work. Ive tryed this tutorial but it didn't work for me [http://ubuntuforums.org/showthread.php?p=5670733](http://ubuntuforums.org/showthread.php?p=5670733). I get to part 3 where it says the lights should be blinking and it should search for networks, but nothing happens. Like I said im new to Ubuntu and im thinking im not installing the packages right or something along those lines. 

Any help would be appreciated

---

### Post by AstraCD08 on 2008-09-22
Check the revision number on your card. If it has been purchased in the last 12 months it is probably revision 3. This is not supported by default unfortunately. The only way to get this card to work that I know of it is to use NDiswrapper. This program allows linux to use windows native drivers for the card. Try googling NDiswrapper.

---

### Post by AstraCD08 on 2008-09-22
OOps sorry. I just read your link. The main thing to make sure of is that you are using the correct drivers for your card. The ones linked to in the how-to may not be the ones for your revision of the card.

The best way would be to install the card on a windows box and get the .inf files from there and copy them to ubuntu so that ndiswrapper (ndisgtk) can use them.

If you substitute these drivers for the ones from the tutorial all should work. Not sure if the light will work though. WPA security may also not work. Try WEP to start with, or even turn off the routers security whilst checking. This has risks, however minor - so be warned.

---

### Post by funkyhair143 on 2008-09-23
so all i need is the ndswrapper or all of the other packages?

---

### Post by ashleyslaterwinter on 2008-10-18
Here is my guide to NDISwrapper that i wrote myself to give to my friends

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

