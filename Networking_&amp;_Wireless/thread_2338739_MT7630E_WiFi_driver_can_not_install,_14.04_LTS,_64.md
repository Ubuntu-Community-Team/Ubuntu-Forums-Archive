---
title: "MT7630E WiFi driver can not install, 14.04 LTS, 64b"
date: 2016-10-01
forum: Networking &amp; Wireless
---

### Post by m+chael on 2016-10-01
Hello people,

I have a problem with installing WiFi driver  MT7630E on my Ubuntu 14.04 LTS, 64b
It suddenly stopped to work yesterday.
Today I decided to reinstall it, and I got this problem:
[I]
m@mpc:~/Desktop/New folder3/MT7630E-release$ sudo ./install
[sudo] password for m: 
make -C /lib/modules/`uname -r`/build M=/home/m/Desktop/New folder3/MT7630E-release/rt2x00 modules
make[1]: Entering directory `/usr/src/linux-headers-4.4.0-36-generic'
arch/x86/Makefile:148: CONFIG_X86_X32 enabled but no binutils support
Makefile:669: Cannot use CONFIG_CC_STACKPROTECTOR_REGULAR: -fstack-protector not supported by compiler
make[1]: *** No rule to make target `folder3/MT7630E-release/rt2x00'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-4.4.0-36-generic'
make: *** [all] Error 2[/I]

[B][I]Cannot use CONFIG_CC_STACKPROTECTOR_REGULAR: -fstack-protector not supported by compiler  :(

[/I][/B]Maybe, someone knows more about this issue and also how to fix it?

Best regards,
Michael.

---

### Post by jeremy31 on 2016-10-01
Welcome to the forums, please use code tags on terminal output.  See the wireless script link in my signature and post the results as I think your device is supported in the 4.4 kernel

---

### Post by chili555 on 2016-10-01
Please note:> make[1]: *** No rule to make target `folder3/MT7630E-release/rt2x00'. Stop.But you are not trying to 'make' folder3; you are tying to 'make' New folder3.

Make is troubled by unescaped spaces in file names. Please rename the folder to New_folder3 or similar and try again. Post any errors.

---

### Post by m+chael on 2016-10-03
> **jeremy31 said:**
> Welcome to the forums, please use code tags on  terminal output.  See the wireless script link in my signature and post  the results as I think your device is supported in the 4.4  kernel
Thank you, I have performed this operation, but it was redundant because the problem had an other issue. At least now I know about existence such a tool like wireless script.


> **chili555 said:**
> Please note:But you are not trying to 'make' folder3; you are tying to 'make' New folder3.

Make is troubled by unescaped spaces in file names. Please rename the folder to New_folder3 or similar and try again. Post any errors.

You must be Linux Wizard! Many thanks, the problem was exactly like you told. It was a need to change the name of the folder and it started to work.

---

