---
title: "Wifi not working, wl module doesn't exist"
date: 2018-06-19
forum: Networking &amp; Wireless
---

### Post by rasaborio on 2018-06-19
I just update my laptop as usual and after reboot the Wi-Fi disappeared, I've followed anything I found in this forum and Google, but nothing fix the problem, the most similar case is the one [here]("https://ubuntuforums.org/showthread.php?t=2386370"), but any solution given there worked for me.

My system [wireless info]("http://paste.ubuntu.com/p/MB92Hqzt85/").

```
sudo lshw -class network
``` shows this:

```
 *-network NO RECLAMADO  
       descripción: Network controller
       producto: BCM43142 802.11b/g/n
       fabricante: Broadcom Limited
       id físico: 0
       información del bus: pci@0000:07:00.0
       versión: 01
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress bus_master cap_list
       configuración: latency=0
       recursos: memoria:f7c00000-f7c07fff
```


Kernel according to ```
 uname -r
``` is: ```
4.15.0-24-generic
```


```
sudo dpkg -s bcmwl-kernel-source | grep Version
``` shows:
```
[COLOR=#ff0000]**Version**[/COLOR]: 6.30.223.271+bdcom-0ubuntu1~1.2
```


The log file ```
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/make.log
```

```
DKMS make.log for bcmwl-6.30.223.271+bdcom for kernel 4.15.0-24-generic (x86_64)
mar 19 jun 20:06:46 CST 2018
make: se entra en el directorio '/usr/src/linux-headers-4.15.0-24-generic'
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.o
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.c: In function ‘osl_os_get_image_block’:
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.c:1083:26: warning: passing argument 2 of ‘kernel_read’ makes pointer from integer without a cast [-Wint-conversion]
  rdlen = kernel_read(fp, fp->f_pos, buf, len);
                          ^
In file included from ./include/linux/huge_mm.h:7:0,
                 from ./include/linux/mm.h:463,
                 from /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/include/linuxver.h:65,
                 from /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.c:25:
./include/linux/fs.h:2858:16: note: expected ‘void *’ but argument is of type ‘loff_t {aka long long int}’
 extern ssize_t kernel_read(struct file *, void *, size_t, loff_t *);
                ^
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.c:1083:37: warning: passing argument 3 of ‘kernel_read’ makes integer from pointer without a cast [-Wint-conversion]
  rdlen = kernel_read(fp, fp->f_pos, buf, len);
                                     ^
In file included from ./include/linux/huge_mm.h:7:0,
                 from ./include/linux/mm.h:463,
                 from /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/include/linuxver.h:65,
                 from /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.c:25:
./include/linux/fs.h:2858:16: note: expected ‘size_t {aka long unsigned int}’ but argument is of type ‘char *’
 extern ssize_t kernel_read(struct file *, void *, size_t, loff_t *);
                ^
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.c:1083:42: warning: passing argument 4 of ‘kernel_read’ makes pointer from integer without a cast [-Wint-conversion]
  rdlen = kernel_read(fp, fp->f_pos, buf, len);
                                          ^
In file included from ./include/linux/huge_mm.h:7:0,
                 from ./include/linux/mm.h:463,
                 from /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/include/linuxver.h:65,
                 from /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.c:25:
./include/linux/fs.h:2858:16: note: expected ‘loff_t * {aka long long int *}’ but argument is of type ‘int’
 extern ssize_t kernel_read(struct file *, void *, size_t, loff_t *);
                ^
symbolmap: la: invalid section
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.o
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.c: In function ‘wl_init_timer’:
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.c:2359:2: error: implicit declaration of function ‘init_timer’ [-Werror=implicit-function-declaration]
  init_timer(&t->timer);
  ^
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.c:2360:10: error: ‘struct timer_list’ has no member named ‘data’
  t->timer.data = (ulong) t;
          ^
/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.c:2361:20: error: assignment from incompatible pointer type [-Werror=incompatible-pointer-types]
  t->timer.function = wl_timer;
                    ^
cc1: some warnings being treated as errors
scripts/Makefile.build:332: fallo en las instrucciones para el objetivo '/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.o'
make[1]: *** [/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.o] Error 1
Makefile:1552: fallo en las instrucciones para el objetivo '_module_/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build'
make: *** [_module_/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build] Error 2
make: se sale del directorio '/usr/src/linux-headers-4.15.0-24-generic'
```


gcc version: gcc (Ubuntu 5.5.0-12ubuntu1~16.04) 5.5.0 20171010

gcc-5 version: gcc-5 (Ubuntu 5.5.0-12ubuntu1~16.04) 5.5.0 20171010


This is the results when trying to install bcmwl-kernel-source:

```
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se instalarán los siguientes paquetes NUEVOS:
  bcmwl-kernel-source
0 actualizados, 1 nuevos se instalarán, 0 para eliminar y 0 no actualizados.
Se necesita descargar 0 B/1 544 kB de archivos.
Se utilizarán 8 064 kB de espacio de disco adicional después de esta operación.
Seleccionando el paquete bcmwl-kernel-source previamente no seleccionado.
(Leyendo la base de datos ... 1238639 ficheros o directorios instalados actualmente.)
Preparando para desempaquetar .../bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu1~1.2_amd64.deb ...
Desempaquetando bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu1~1.2) ...
Configurando bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu1~1.2) ...
Loading new bcmwl-6.30.223.271+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 4.15.0-24-generic
Building for architecture x86_64
Building initial module for 4.15.0-24-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/bcmwl-kernel-source.0.crash'
Error! Bad return status for module build on kernel: 4.15.0-24-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/make.log for more information.
modprobe: ERROR: ../libkmod/libkmod-module.c:832 kmod_module_insert_module() could not find module by name='wl'
modprobe: ERROR: could not insert 'wl': Unknown symbol in module, or unknown parameter (see dmesg)
modprobe: ERROR: ../libkmod/libkmod-module.c:977 command_do() Error running install command for wl
modprobe: ERROR: could not insert 'wl': Operation not permitted
update-initramfs: deferring update (trigger activated)
Procesando disparadores para initramfs-tools (0.122ubuntu8.11) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-24-generic
```

Also, it's shown as if succesfully installed, but the wireless continue as before.

I'm a newbie programming, I just migrated from Windows because I feel better with Ubuntu, I can follow instructions and run commands, but I have no idea about the results the terminal is showing me when it comes to an error.

Thanks for any help

---

### Post by chili555 on 2018-06-20
You have:> Version: 6.30.223.271+bdcom-0ubuntu[COLOR="#FF0000"]1~1.2[/COLOR]On my 4.15.0-xx system, I have:> 6.30.223.271+bdcom-0ubuntu[COLOR="#FF0000"]4[/COLOR]Please try:```
sudo apt update
sudo apt purge bcmwl-kernel-source
sudo apt install bcmwl-kernel-source
```Let's see if you get the later, working package.

---

### Post by rasaborio on 2018-06-20
Hi!!! I've tried the code you suggested, but it continue to get the old package, so i did a quick research and found the most recent package is ```
6.30.223.271+bdcom-0ubuntu[COLOR=#FF0000]8[/COLOR]
``` so I downloaded if and installed it manually, but didn't work.

I went over to the version you had: ```
6.30.223.271+bdcom-0ubuntu[COLOR=#FF0000]4[/COLOR]
``` and tried with that package and finally terminal showed me something different:

```
Seleccionando el paquete bcmwl-kernel-source previamente no seleccionado.
(Leyendo la base de datos ... 1238639 ficheros o directorios instalados actualmente.)
Preparando para desempaquetar bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu4_amd64.deb ...
Desempaquetando bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu4) ...
Configurando bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu4) ...
Loading new bcmwl-6.30.223.271+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 4.15.0-24-generic
Building for architecture x86_64
Building initial module for 4.15.0-24-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.15.0-24-generic/updates/dkms/

depmod........

DKMS: install completed.
modprobe: ERROR: could not insert 'wl': Exec format error
modprobe: ERROR: ../libkmod/libkmod-module.c:977 command_do() Error running install command for wl
modprobe: ERROR: could not insert 'wl': Operation not permitted
update-initramfs: deferring update (trigger activated)
Procesando disparadores para initramfs-tools (0.122ubuntu8.11) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-24-generic


```

Still not working...

---

### Post by chili555 on 2018-06-20
Is secure boot turned off?

---

### Post by rasaborio on 2018-06-20
Yes, its disabled, I've checked that

---

### Post by chili555 on 2018-06-20
When you installed 0ubuntu8 manually and it didn't work, did you purge it? What does this tell us?```
sudo dkms status
cat /var/lib/dkms/bcmwl/6.30.223.271+bdcom/4.15.0-24-generic/x86_64/log/make.log
```

---

### Post by rasaborio on 2018-06-20
> **chili555 said:**
> When you installed 0ubuntu8 manually and it didn't work, did you purge it?

Yes, I did, the installation progress was the same as the oldest package, so I didn't even verified the log.


```
sudo dkms status
```
Responds: 
```
bcmwl, 6.30.223.271+bdcom, 4.15.0-24-generic, x86_64: installed
```

I have installed right now the 0ubuntu4, this is the log file:

```
DKMS make.log for bcmwl-6.30.223.271+bdcom for kernel 4.15.0-24-generic (x86_64)
mié 20 jun 09:16:21 CST 2018
make: se entra en el directorio '/usr/src/linux-headers-4.15.0-24-generic'
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.o
symbolmap: la: invalid section
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.o
symbolmap: la: invalid section
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_iw.o
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_cfg80211_hybrid.o
symbolmap: la: invalid section
  LD [M]  /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/wl.o
  Building modules, stage 2.
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  MODPOST 1 modules
  CC      /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/wl.mod.o
  LD [M]  /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/wl.ko
make: se sale del directorio '/usr/src/linux-headers-4.15.0-24-generic'
```

---

### Post by sreetamdas on 2018-06-20
Facing the same issue here as well, is there any solution to this?

---

### Post by jackpinto on 2018-06-20
*-network UNCLAIMED       
       description: Network controller
       product: BCM43142 802.11b/g/n

I also has same problem any suggestions

---

### Post by chili555 on 2018-06-20
> **jackpinto said:**
> *-network UNCLAIMED       
       description: Network controller
       product: BCM43142 802.11b/g/n

I also has same problem any suggestionsIn both cases, by "...the same problem..." do you mean the essential error:> symbolmap: la: invalid sectionIn all three cases, if you boot into an earlier kernel version at the GRUB menu, such as 4.15.0-23, does the package install and work as expected? 

It installs without error for me on 4.15.0-23. I haven't a Broadcom device, so I can't test further.

---

### Post by rasaborio on 2018-06-20
> **chili555 said:**
> if you boot into an earlier kernel version at the GRUB menu, such as 4.15.0-23, does the package install and work as expected?

Absolutely, yes, you are my hero right now!!! I tried at first with the oldest kernel version which was 4.15.0-13-generic and it installed the 0ubuntu8 package and started working at once... 

Now I have a few questions more: is it possible to set this kernel as default? should I have to wait for a new kernel version and hope to this won't happen again???

---

### Post by chili555 on 2018-06-20
Once you are booted into -23 or whatever works for you, remove the kernel version that doesn't work: ```
sudo apt remove linux-image-4.15.0-24-generic
```And hold it: [https://askubuntu.com/questions/678630/how-can-i-avoid-kernel-updates](https://askubuntu.com/questions/678630/how-can-i-avoid-kernel-updates)

Then, I'd file a bug against bcmwl-kernel-source here: [https://bugs.launchpad.net/](https://bugs.launchpad.net/)

---

### Post by rasaborio on 2018-06-20
Thank you a lot!!! I'll do that at once, but first will verify if another kernel version is working previous removing them... also, after you file the bug, I'll be able to follow the report in case further info is required.

Update: -23 is also working, it states the package was installed for -23 AND -24, but I won't take the risk...

---

### Post by sreetamdas on 2018-06-21
Worked for me as well! Thanks a lot :)

---

### Post by chili555 on 2018-06-21
> **sreetamdas said:**
> Worked for me as well! Thanks a lot :)Please look for and add to rasaborio's bug report, please. [https://bugs.launchpad.net/](https://bugs.launchpad.net/)

Perhaps he will give us the link here.

It is important that everyone affected add to the bug report as it appears to be pretty serious and we hope the fix will be released soon.

---

### Post by rasaborio on 2018-06-21
> **chili555 said:**
> Perhaps he will give us the link here.

For sure, the bug report is [here]("https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1778097").

Hope I provided enough info, it's my first report...

---

### Post by chili555 on 2018-06-21
> **rasaborio said:**
> For sure, the bug report is [here]("https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1778097").

Hope I provided enough info, it's my first report...Thank you.

You will be asked for lots more data soon.

---

