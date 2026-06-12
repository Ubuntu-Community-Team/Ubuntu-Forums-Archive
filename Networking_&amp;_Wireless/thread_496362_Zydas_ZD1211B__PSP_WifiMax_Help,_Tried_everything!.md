---
title: "Zydas ZD1211B / PSP WifiMax Help, Tried everything!"
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by freekaleek on 2007-07-09
Hey, thanks for the help.

Im running feisty, and i have a psp wifimax i need to get working, because i want to use xlink kai. Ive tried tonnes of different ****, ive tried replacing the stuff in the firmware directory with new files like i was told to, nothing. Ive blacklisted the zd1211rw driver. Im really starting to get fed up, as ive been troubleshooting this for like 5 hours now. Ive followed various tutorials on the forum, but none of them work, i can never get to the end of it because i get this damned error:

```

(tonnes of the same lines)
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10515: warning: excess elements in scalar initializer
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10515: warning: (near initialization for ‘X_Constant’)
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10515: warning: excess elements in scalar initializer
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10515: warning: (near initialization for ‘X_Constant’)
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10517: warning: excess elements in scalar initializer
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10517: warning: (near initialization for ‘X_Constant’)
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10521: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10578: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10644: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10681: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10693: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10746: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10764: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10791: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10818: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10828: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10873: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10883: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10909: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10921: error: old-style parameter declarations in prototyped function definition
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:479: error: parameter name omitted
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:479: error: parameter name omitted
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:479: error: parameter name omitted
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:479: error: parameter name omitted
/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10921: error: expected ‘{’ at end of input
make[4]: *** [/usr/src/ZD1211LnxDrv_2_16_0_0/src/zd1205.o] Error 1
make[3]: *** [_module_/usr/src/ZD1211LnxDrv_2_16_0_0] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/usr/src/ZD1211LnxDrv_2_16_0_0'
make[1]: *** [both] Error 2
make[1]: Leaving directory `/usr/src/ZD1211LnxDrv_2_16_0_0'
make: *** [all] Error 2

```

Im running AMD64 Feisty Any help would be greatly appriciated -_-

Thanks a lot guys and gals.

---

