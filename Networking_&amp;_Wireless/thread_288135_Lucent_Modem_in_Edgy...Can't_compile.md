---
title: "Lucent Modem in Edgy...Can't compile"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by GCR on 2006-10-29
Hey! 

I have been using Edgy for a couple of days ago. Everything went smooth and I really like it. However I have one li'l problem. The drivers for my Lucent Dial-Up modem wont compile. I've installed through apt-get the necessary 'build-essentials' apps and everything. However, whenever I try to type 'Make' so that they compile I get an error.

I was googling around and noticed that it is something related to the kernel used(newer 2.6.17.* and 2.6.18) and that there was a workaround it, but I dont know if there's a workaround in Ubuntu so that I don't have to recompile my kernel again(the instructions were taken from a gentoo-wiki).

Is there a workaround, or by any chances(which I doubt) are there any drivers for Lucent modem specifically for Ubuntu or that are already patched to work for the main Edgy kernel?

Thanks!

---

### Post by GCR on 2006-10-30
Any ideas?

---

### Post by GCR on 2006-10-30
This is the eror I get:
```
ubuntu:/home/gil/lucent/ltmodem-2.6-alk-8# make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/gil/lucent/ltmodem-2.6-alk-
8 modules
make[1]: Entering directory `/usr/src/linux-2.6.18'
  CC [M]  /home/gil/lucent/ltmodem-2.6-alk-8/lt_modem.o
/home/gil/lucent/ltmodem-2.6-alk-8/lt_modem.c:123: error: syntax error before string constant
/home/gil/lucent/ltmodem-2.6-alk-8/lt_modem.c:123: warning: type defaults to `i
nt' in declaration of `MODULE_PARM' /home/gil/lucent/ltmodem-2.6-alk-8/lt_modem.c:123: warning: function declaration isn't a prototype
/home/gil/lucent/ltmodem-2.6-alk-8/lt_modem.c:123: warning: data definition has no type or storage class
/home/gil/lucent/ltmodem-2.6-alk-8/lt_modem.c:125: error: syntax error before string constant
/home/gil/lucent/ltmodem-2.6-alk-8/lt_modem.c:125: warning: type defaults to `int' in declaration of `MODULE_PARM'
/home/gil/lucent/ltmodem-2.6-alk-8/lt_modem.c:125: warning: function declaration isn't a prototype
/home/gil/lucent/ltmodem-2.6-alk-8/lt_modem.c:125: warning: data definition has no type or storage class
/home/gil/lucent/ltmodem-2.6-alk-8/lt_modem.c:130: error: syntax error before string constant
/home/gil/lucent/ltmodem-2.6-alk-8/lt_modem.c:130: warning: type defaults to `int' in declaration of `MODULE_PARM'
/home/gil/lucent/ltmodem-2.6-alk-8/lt_modem.c:130: warning: function declaration isn't a prototype
/home/gil/lucent/ltmodem-2.6-alk-8/lt_modem.c:130: warning: data definition has no type or storage class
make[2]: *** /home/gil/lucent/ltmodem-2.6-alk-8/lt_modem.o] Error 1
make[1]: *** [_module_/home/gil/lucent/ltmodem-2.6-alk-8] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.18'
make: *** [module] Error 2
```

I read in another thread that gentoo proided a patch, apparently that fixes this. The patch is below: 
```
diff -Nru ltmodem-2.6-alk-8.orig/lt_modem.c ltmodem-2.6-alk-8/lt_modem.c
--- ltmodem-2.6-alk-8.orig/lt_modem.c	2005-12-12 03:18:55.000000000 +0200
+++ ltmodem-2.6-alk-8/lt_modem.c	2006-04-19 21:43:32.142640500 +0300
@@ -120,14 +120,14 @@
 static int vendor_id = 0;
 static int device_id = 0;
 
-MODULE_PARM(vendor_id, "i");
+module_param(vendor_id, int, 0);
 MODULE_PARM_DESC(vendor_id, "Vendor ID of the Lucent Modem e.g. vendor_id=0x11c1");
-MODULE_PARM(device_id, "i");
+module_param(device_id, int, 0);
 MODULE_PARM_DESC(device_id, "Device ID of the Lucent Modem e.g. device_id=0x0440");
 
 static int Forced[4] = {-1,-1,-1,0};
 
-MODULE_PARM(Forced, "4i");
+module_param_array(Forced, int, NULL, 0);
 MODULE_PARM_DESC(Forced, "Forced Irq,BaseAddress,ComAddress[,NoDetect] of the Lucent Modem e.g. Forced=3,0x130,0x2f8");
 
 static
diff -Nru ltmodem-2.6-alk-8.orig/serial.c ltmodem-2.6-alk-8/serial.c
--- ltmodem-2.6-alk-8.orig/serial.c	2005-12-12 03:07:17.000000000 +0200
+++ ltmodem-2.6-alk-8/serial.c	2006-09-21 21:53:08.055717500 +0300
@@ -732,7 +732,9 @@
 	.devfs_name		= "tts/LT",
 	.dev_name		= "ttyLT",
 #else
+#	if (LINUX_VERSION_CODE < KERNEL_VERSION(2,6,18))
 	.devfs_name		= "tts/LTM",
+#	endif
 	.dev_name		= "ttyLTM",
 #endif
 	.major			= 62,
```

Questions that I have:

Is the patch applied to the modules or to the kernel? Whichever way, how can I accomplish this patching?

Thanks for your help!

---

### Post by GCR on 2006-10-31
I think I patched the driver...yet it fails to compile. I may be doing something wrong but frankly I have no idea. The driver worked perfectly in Dapper.

Any help? :)

PD: TYhe error is related to MODULE_PARM just in case that helps ;)

---

### Post by Turin Turambar on 2006-10-31
No ideas. I get the similar error..... 

And the more I use Edgy, the more I regret I deleted the Dapper.
I ran into problems the moment I restarted the PC, but that's another story.

Actually, the whole Ubuntu is kind of getting on my nerves, as they didn't even TRY to fix the modem issues! They constantly provide ltmodem drivers (restricted modules) that DO NOT work.

---

### Post by GCR on 2006-10-31
Looks like Im not alone here.

I wouldnt say that my experience is that bad but it certainly ain't as smooth for me as Dapper(though its a bit faster which is good).

I'll wait some more in case someone has done this successfully, if not then I guess I'll go back to Dapper :(

---

### Post by Turin Turambar on 2006-10-31
Fortunately you have something to get back to. I deleted Dapper.

I tried alk8 & martian drivers and got similar errors.
I'm left with Edgy and no internet. :(

---

