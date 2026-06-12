---
title: "HP Pavilion dv6 wireless and finger scanner not working"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by Abualderda on 2011-02-24
Hi everybody

I just bought an HP dv6 3225dx and i installed Ubuntu 10.04.
everything seems to work OK
but the finger scanner and the wireless are not working. 

can someone give me a **simple** instructions on how to get them both working 
i would highly appreciate it.


thank you

PS.   I'm a beginner to the Ubuntu world

---

### Post by komputes on 2011-02-24
Can you post the actual device ID's. You can do this by running the following commands in a terminal:

```
$ echo \n\n-------- PCI Devices --------\n\n > uf10490009_devices.txt
$ lspci -nnk >> uf10490009_devices.txt
$ echo \n\n-------- USB Devices --------\n\n >> uf10490009_devices.txt
$ lsusb >> uf10490009_devices.txt
```

Then please attach the uf10490009_devices.txt (by default in your home directory) to this forum thread.

---

### Post by _0R10N on 2011-02-24
I have a DV6 myself, and when installing Ubuntu, it doesn't automatically enable any driver for my wireless card (Broadcom) at all, although it detects it properly. You need to manually enable the driver on the aditional drivers window.

Kind regards!

---

### Post by Abualderda on 2011-02-25
[komputes]("http://ubuntuforums.org/member.php?u=128198")

 Can you post the actual device ID's. You can do this by running the following commands in a terminal:

     Code:
     $ echo \n\n-------- PCI Devices --------\n\n > uf10490009_devices.txt
$ lspci -nnk >> uf10490009_devices.txt
$ echo \n\n-------- USB Devices --------\n\n >> uf10490009_devices.txt
$ lsusb >> uf10490009_devices.txt 
Then please attach the uf10490009_devices.txt (by default in your home directory) to this forum thread.
                                                                                               __________________


here is the file (attached)

---

### Post by Abualderda on 2011-02-25
[_0R10N]("http://ubuntuforums.org/member.php?u=1052866")

I have a DV6 myself, and when installing Ubuntu, it doesn't  automatically enable any driver for my wireless card (Broadcom) at all,  although it detects it properly. You need to manually enable the driver  on the aditional drivers window.



the one i have is an intel but when i open hardware drivers it's empty and it says

no proprietary drivers are in use on this system
what does that mean ??????????????

---

### Post by komputes on 2011-02-25
The bug for wireless: fixed in maverick (10.10):
[https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/532451](https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/532451)


For the fingerprint reader, here are instructions from a c:
Fprint is a fingerprint reading library, which allows using the  fingerprint reader found of many of the more decent notebooks (package: **fprint-demo**). The package also includes a PAM module (package: **libpam-fprint**), which enables you to authenticate (log-in etc.) using the fingerprint reader.

The fprint-demo package provides a graphical application to enroll  fingerprints and set different options. After installing that package,  fprint-demo can be invoked from command line only (no menu entry yet) by  issuing this command:
 ```
$ sudo fprint-demo
``` In order to enable fingerprint authentication in Ubuntu install the **libpam** and **libfprint** packages and then edit **/etc/pam.d/common-auth** so it contains
 ```
auth    sufficient    pam_fprint.so
auth    required      pam_unix.so nullok_secure
``` At your next login attempt or sudo command from terminal, this will  first try to read your fingerprint before asking your password. For  testing purposes, you can expire the sudo password caching by issuing  "sudo -k". Do not try to disable password login completely; this is  alpha software and you might lock out yourself.
 Example of command-line fingerprint enrollment:
 ```
$ sudo pam_fprint_enroll --enroll-finger 7
```

---

### Post by Abualderda on 2011-02-26
komputes

thanks alot man
i got my wireless to work by updating to 10.10 ( i didn't want to).

but fprint did not work

 i have found this thread it explained it in a very simple way
[http://ubuntuforums.org/showthread.php?t=760018](http://ubuntuforums.org/showthread.php?t=760018)

i did everything but when i got to the enrolment it says 

no devices found 

can you try to help in a simple instruction

thanks

---

