---
title: "webcam"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by dlawler on 2009-02-15
i signed on to my linux partition for the first time in a long while.
webcam didn't seem to be working, tried modprobing it.
not found.

when i redownloaded the drivers and tried the good 'ol sudo make this is what i get.

daniel@daniel-laptop:~/r5u870-0.11.2$ sudo make
[sudo] password for daniel: 
make -C /lib/modules/2.6.24-22-rt/build M=/home/daniel/r5u870-0.11.2 V=0 modules
make: *** /lib/modules/2.6.24-22-rt/build: No such file or directory.  Stop.
make: *** [all] Error 2
daniel@daniel-laptop:~/r5u870-0.11.2$ 


and this is my lsusb

daniel@daniel-laptop:~/r5u870-0.11.2$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 05ca:1839 Ricoh Co., Ltd 
Bus 003 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 054c:02c1 Sony Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
daniel@daniel-laptop:~/r5u870-0.11.2$ 



clearly it's there.
i swear this ricoh r5u870 driver has given me so much woes.

---

### Post by johnjohn2 on 2009-02-15
have you tried to get it working in cheese

---

### Post by dlawler on 2009-02-15
no. it will not work in anything.
it's not loaded.

---

### Post by Nepherte on 2009-02-15
Instead of a kernel module, it has now become a user space module.

First install mercurial:
```
sudo apt-get install mercurial
```

Now get the latest sources:
```
hg clone http://bitbucket.org/ahixon/r5u87x/
```

Now build the driver:
```
cd r5u87x && make
```

And use loader to load the correct firmware:
```
sudo ./loader --reload -f ucode/r5u87x-05ca-1839.fw
```

Since it exists in the user space, you will have to load it every time you start your computer. I created an alias in .bashrc for easy access.

---

### Post by dlawler on 2009-02-15
> **Nepherte said:**
> Instead of a kernel module, it has now become a user space module.

First install mercurial:
```
sudo apt-get install mercurial
```

Now get the latest sources:
```
hg clone http://bitbucket.org/ahixon/r5u87x/
```

Now build the driver:
```
cd r5u87x && make
```

And use loader to load the correct firmware:
```
sudo ./loader --reload -f ucode/r5u87x-05ca-1839.fw
```

Since it exists in the user space, you will have to load it every time you start your computer. I created an alias in .bashrc for easy access.

wellllll,
i tried that.

and i get this.

daniel@daniel-laptop:~/r5u87x$ sudo make
cc -g -Wall -DHAVE_CONFIG_H -DUCODE_PATH=\"/usr/lib/r5u87x/ucode/"r5u87x-%vid%-%pid%.fw"\"  `pkg-config --cflags glib-2.0 libusb` -c loader.c loader.h
Package libusb was not found in the pkg-config search path.
Perhaps you should add the directory containing `libusb.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libusb' found
loader.c:28:18: error: glib.h: No such file or directory
loader.c:29:25: error: glib/gstdio.h: No such file or directory
loader.c:30:17: error: usb.h: No such file or directory
In file included from loader.c:32:
loader.h:42: error: expected declaration specifiers or ‘...’ before ‘gint’
loader.c:38: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
loader.c:39: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘force_clear’
loader.c:40: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘no_load’
loader.c:42: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
loader.c:43: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘dump_ucode’
loader.c:44: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘reload’
loader.c:46: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘entries’
loader.c:71: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
loader.c:89: error: expected declaration specifiers or ‘...’ before ‘gint’
loader.c: In function ‘find_device’:
loader.c:91: error: ‘gint’ undeclared (first use in this function)
loader.c:91: error: (Each undeclared identifier is reported only once
loader.c:91: error: for each function it appears in.)
loader.c:91: error: expected ‘;’ before ‘i’
loader.c:95: warning: implicit declaration of function ‘usb_get_busses’
loader.c:95: warning: assignment makes pointer from integer without a cast
loader.c:96: error: dereferencing pointer to incomplete type
loader.c:99: error: dereferencing pointer to incomplete type
loader.c:99: error: dereferencing pointer to incomplete type
loader.c:101: error: ‘i’ undeclared (first use in this function)
loader.c:102: error: dereferencing pointer to incomplete type
loader.c:103: error: dereferencing pointer to incomplete type
loader.c:105: error: ‘version’ undeclared (first use in this function)
loader.c: At top level:
loader.c:120: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_upload’
loader.c:202: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_status’
loader.c:219: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_version’
loader.c:238: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_enable’
loader.c:255: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘r5u87x_ucode_clear’
loader.c:276: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
loader.c:290: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘load_firmware’
loader.c:410: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘main’
loader.h:21:18: error: glib.h: No such file or directory
loader.h:42: error: expected declaration specifiers or ‘...’ before ‘gint’
make: *** [loader.o] Error 1

could something be wrong with make?

---

### Post by Nepherte on 2009-02-17
```
Package libusb was not found in the pkg-config search path.
Perhaps you should add the directory containing `libusb.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libusb' found
```
See if you have the libusb package installed. You also shouldn't need to use sudo, a simple make suffices.

---

### Post by 0m6 on 2009-02-18
> **Nepherte said:**
> ```
Package libusb was not found in the pkg-config search path.
Perhaps you should add the directory containing `libusb.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libusb' found
```
See if you have the libusb package installed. You also shouldn't need to use sudo, a simple make suffices.

i've been trying this. and i get the same exact error as the other person got. how would i get libusb on my computer?

---

### Post by dlawler on 2009-02-19
i have lsusb on my computer.
i even downloaded the file, and then put it in the folder, tried, and failed again.

---

### Post by Nepherte on 2009-02-20
You don't need lsusb, you need libusb or libusb-dev (probably the latter one). Other than that, I have no idea why it's not compiling.

---

