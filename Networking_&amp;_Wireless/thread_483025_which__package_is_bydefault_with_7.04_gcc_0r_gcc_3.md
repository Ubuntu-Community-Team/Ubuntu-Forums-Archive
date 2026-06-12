---
title: "which  package is bydefault with 7.04 gcc 0r gcc 3.4 or etc"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by umairsaeed219 on 2007-06-24
i have to compile my modem driver(intel536ep) soo i want to download required ubuntu packages which iam unable to find plz send me there link and describe in detail which one i needed
i have tried to download the packages written on if compiling from source [https://help.ubuntu.com/community/DialupModemHowto/Intel536EP](https://help.ubuntu.com/community/DialupModemHowto/Intel536EP)

---

### Post by kevdog on 2007-06-24
If you have nternet connection
sudo aptitude install build-essential

If you dont have internet connection but install Cd. Put cd in drive then
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential

---

### Post by umairsaeed219 on 2007-06-25
My dear i have compiled(intel 536ep modem ) the driver using build essential and for almost hundrad times on both 6.06 and 7.04 exactly acccording to instruction still i am unable to install the modem so plz tell me preciesly which one of these  either gcc3.4 or simple gcc required  both in case of 
6.06 and 
7.04 thanks

---

### Post by kevdog on 2007-06-25
my dear, not to be rude, but how the heck would I know since I am not privy to the documentation.  With ubuntu I know that you can have both versions of the compiler present on your system.  They will not overwrite each other.  Why dont you just install both versions, and then just manually try each??

---

### Post by chili555 on 2007-06-25
```
cat /proc/version
```reports that my Feisty machine is using gcc version 4.1.2. As kevdog reports, you can certainly install a different version of gcc if you require it.

---

