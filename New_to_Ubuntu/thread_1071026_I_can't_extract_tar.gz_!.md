---
title: "I can't extract tar.gz !"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by cosmicappuccino on 2009-02-15
I'm a complete Linux newbie, and I've just installed Hardy Heron. I have a new wireless USB adapter that needs a driver to be installed. In the instruction pdf for Linux, I'm instructed to extract a tar.gz file -- but it won't work, and I think it's because the archive is read-only!

Can anyone suggest what I should do to extract the file, please?

---

### Post by binbash on 2009-02-15
go to the directory you have the tar.gz file

sudo chmod 777 asd.tar.gz
tar -zxvf asd.tar.gz

---

### Post by TCSnyder on 2009-02-15
right click it and go to "Properties" and give yourself Read write Permissions. 

if you can't then it is owned by the root user so go to the command line and type

```
sudo chown "username" /path/to/file
```

change "username" to your usename after that right click the archive and click "extract"

Good luck

---

### Post by cosmicappuccino on 2009-02-15
Thanks guys; really helpful!

---

### Post by cosmicappuccino on 2009-02-15
Hm.. I have extracted the files but now am more confused.

In the instructions, it says that there is a Makefile in the extracted directory, and that you just need to type "make" to generate the driver module and install.

I wasn't really sure what to do, so I went to the extracted directory using Terminal, and I typed in "make". A lot of text came up in Terminal, and it ended with:

> make: *** [all] Error 2

...which I assume means it didn't work..?

---

### Post by ibuclaw on 2009-02-15
What application are you attempting to compile?

You are most likely required to install all build dependancies for the application before you can successfully make it.

Can you post more of the output you got from the make command?

Usually any line that begins with "Error" is a sign of what libraries are missing.

But before you do
```
sudo apt-get install build-essential
```
and try running **make** again.

Regards
Iain

---

### Post by cosmicappuccino on 2009-02-15
Thanks for the reply Iain...

It's a USB wireless adapter -- mainly intended for Windows, but it boasts that it's Linux-compatible and the driver CD contains a Linux folder, that I opened and am following instructions from. (Including the instructions about the Makefile.)

When I tried your code and ran make again, I don't think there was any change. This is what I got out when I typed in *"sudo apt-get install build-essential"*:

> Reading package lists... Done
Building dependency tree
Reading state information... Done
Package build-essential is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package build-essential has no installation candidate

Also, here are some more lines from the beginning of the output after I try "make":

> make both
make[1]: Entering directory 'home/user/directory'
make clean
make[2]: Entering directory 'home/user/directory'
rm -rf .tmp_versions .*.cmd *.ko *.mod.c *.mod.o *.o src/*.o src/.*.o.cmd menudbg apdbg winevl_iface
make[2]: Leaving directory 'home/user/directory'
make ZD1211REV_B=0
make[2]: Entering directory 'home/user/directory'
/lib/modules/2.6.24-23-generic/build
/home/user/directory
-I/home/user/directory/src/include -fomit-frame-pointer -02 -Wall -Wstrict-prototypes -pipe -Wno-unused -DZDCONF_WE_STAT_SUPPORT=1 -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZDCONF_MENUDBG -DZDCONF_APDBG -DPRODUCTION -DZDCONF_BANDEDGE_ADJUST -DZDCONF_SES_SUPPORT=1 -DAAAA03_FIX=1 -DZD1211 -DZDCONF_LP_SUPPORT=0


Any insights..?

---

### Post by ibuclaw on 2009-02-15
I was not aware that build-essential had been made obsolete in Hardy.

oh well, try this instead:
```
sudo apt-get install dpkg-dev g++ libc6-dev make
```

Regards
Iain

---

### Post by cosmicappuccino on 2009-02-15
> **tinivole said:**
> I was not aware that build-essential had been made obsolete in Hardy.

oh well, try this instead:
```
sudo apt-get install dpkg-dev g++ libc6-dev make
```

Regards
Iain

The output from this seems similar to before:

> Reading package lists... Done
Building dependency tree
Reading state infromation... Done
Package dpkg-dev is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package dpkg-dev has no installation candidate

...

---

### Post by cosmicappuccino on 2009-02-16
I've now installed build-essential, but the makefile still won't work - this is what I get out:

> user@mydesktop:~/ZD1211LnxDrv_2_16_0_0$ make
make both
make[1]: Entering directory `/home/user/ZD1211LnxDrv_2_16_0_0'
make clean
make[2]: Entering directory `/home/user/ZD1211LnxDrv_2_16_0_0'
rm -rf .tmp_versions .*.cmd *.ko *.mod.c *.mod.o *.o src/*.o src/.*.o.cmd menudbg apdbg winevl_iface
make[2]: Leaving directory `/home/user/ZD1211LnxDrv_2_16_0_0'
make ZD1211REV_B=0
make[2]: Entering directory `/home/user/ZD1211LnxDrv_2_16_0_0'
/lib/modules/2.6.24-23-generic/build
/home/user/ZD1211LnxDrv_2_16_0_0
-I/home/user/ZD1211LnxDrv_2_16_0_0/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -Wno-unused -DZDCONF_WE_STAT_SUPPORT=1 -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZDCONF_MENUDBG -DZDCONF_APDBG -DPRODUCTION -DZDCONF_BANDEDGE_ADJUST -DZDCONF_SES_SUPPORT=1 -DAAAA03_FIX=1 -DZD1211 -DZDCONF_LP_SUPPORT=0
src/zd1205.o src/zdreq.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zddebug2.o src/zdlpmgt.o src/zdturbo_burst.o src/zdusb.o src/zdmisc.o src/zd1211.o
make -C /lib/modules/2.6.24-23-generic/build SUBDIRS=/home/user/ZD1211LnxDrv_2_16_0_0 modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.24-23-generic'
CC [M] /home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.o
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:34:26: error: linux/config.h: No such file or directory
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:451: warning: initialisation from incompatible pointer type
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:479: error: expected declaration specifiers or ‚Äò...‚Äô before ‚Äòwrite‚Äô
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:479: error: expected declaration specifiers or ‚Äò...‚Äô before ‚Äòfd‚Äô
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:479: error: expected declaration specifiers or ‚Äò...‚Äô before ‚Äòbuf‚Äô
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:479: error: expected declaration specifiers or ‚Äò...‚Äô before ‚Äòcount‚Äô
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:480: warning: type defaults to ‚Äòint‚Äô in declaration of ‚Äò_syscall3‚Äô
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:480: error: expected ‚Äò,‚Äô or ‚Äò;‚Äô before ‚Äò_syscall3‚Äô
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:485: error: ‚Äòdot11A_Channel‚Äô undeclared here (not in a function)
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‚Äòzd1205_rx_isr‚Äô:
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:4218: error: ‚Äòstruct sk_buff‚Äô has no member named ‚Äòmac‚Äô
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‚Äòzd1205_xmit_frame‚Äô:
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:5025: warning: ISO C90 forbids mixed declarations and code
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:5026: warning: assignment from incompatible pointer type
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:5029: warning: assignment from incompatible pointer type
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‚Äòzd1205_load_card_setting‚Äô:
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:8708: error: implicit declaration of function ‚Äòopen‚Äô
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:8725: error: implicit declaration of function ‚Äòread‚Äô
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:8729: error: implicit declaration of function ‚Äòclose‚Äô
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‚Äòzd1205_save_card_setting‚Äô:
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:8881: error: implicit declaration of function ‚Äòwrite‚Äô
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‚Äòzdcb_rx_ind‚Äô:
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:9913: error: implicit declaration of function ‚Äòeth_copy_and_sum‚Äô
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function ‚Äòzd1205_set_zd_cbs‚Äô:
/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10344: warning: assignment from incompatible pointer type
make[4]: *** [/home/user/ZD1211LnxDrv_2_16_0_0/src/zd1205.o] Error 1
make[3]: *** [_module_/home/user/ZD1211LnxDrv_2_16_0_0] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.24-23-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/user/ZD1211LnxDrv_2_16_0_0'
make[1]: *** [both] Error 2
make[1]: Leaving directory `/home/user/ZD1211LnxDrv_2_16_0_0'
make: *** [all] Error 2 

Any ideas, please? :confused:

---

### Post by Bablefish on 2009-02-16
You have access to an unzipping tool in Add/Remove it's called 7Zip

---

### Post by dox_drum on 2009-02-16
It's not the ideal... but there's a programm called 7z, which unzip almost anything. Try to install it,

```
sudo apt-get install 7z
```

Perhaps it'll work.

[CENTER]Enjoy![/CENTER]

---

### Post by cosmicappuccino on 2009-02-16
Thanks for your replies, Bablefish and doxdrum :)

I've solved the extraction problem now, but if anyone has any input on my problems trying to run the makefile in the extracted directory (described in previously in this thread and also more specifically [[COLOR="DarkOrchid"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1071511")) that would be immensely helpful...

---

### Post by snova on 2009-02-16
Try installing the **linux-headers** package.

Those are some... interesting errors...

---

### Post by cosmicappuccino on 2009-02-16
> **snova said:**
> Try installing the **linux-headers** package.

Those are some... interesting errors...

Interesting indeed! ;)
I've managed to get my USB adapter working now, but thanks for your advice in any case!

---

