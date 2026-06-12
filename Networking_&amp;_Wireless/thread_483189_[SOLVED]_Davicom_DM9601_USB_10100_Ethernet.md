---
title: "[SOLVED] Davicom DM9601 USB 10/100 Ethernet"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by bobpaul on 2007-06-24
I have a USB ethernet adapter that I can't get working. *lsusb* shows *Device: ID 0a46:9601 Davicom Semiconductor, Inc.*. The windows driver is DM9601. I found a driver for the 2.6 kernel on [their website](http://www.davicom.com.tw/eng/download/Driver/driver_9601.htm) but I get errors when I try to do *make*. I also found a website stating [it's in the 2.6.21 kernel tree](http://alcopop.org/unix/linux/dm9601/) and uses the usbnet interface, but I don't see any info about it on the usbnet website and Ubuntu Feisty uses the 2.6.20 kernel.

Here's what happens when I try to make their driver:

```
/home/bobpaul/dm9601-2.6/dm9601.c:55:26: error: linux/config.h: No such file or directory
In file included from /home/bobpaul/dm9601-2.6/dm9601.c:65:
/home/bobpaul/dm9601-2.6/dm9601.h:100:1: warning: "ALIGN" redefined
In file included from include/asm/system.h:4,
                 from include/asm/processor.h:18,
                 from include/asm/thread_info.h:16,
                 from include/linux/thread_info.h:21,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:49,
                 from include/linux/capability.h:45,
                 from include/linux/sched.h:46,
                 from /home/bobpaul/dm9601-2.6/dm9601.c:56:
include/linux/kernel.h:35:1: warning: this is the location of the previous definition
/home/bobpaul/dm9601-2.6/dm9601.c: In function &#8216;__check_reg5&#8217;:
/home/bobpaul/dm9601-2.6/dm9601.c:125: warning: return from incompatible pointer type
/home/bobpaul/dm9601-2.6/dm9601.c: In function &#8216;__check_reg8&#8217;:
/home/bobpaul/dm9601-2.6/dm9601.c:126: warning: return from incompatible pointer type
/home/bobpaul/dm9601-2.6/dm9601.c: In function &#8216;__check_reg9&#8217;:
/home/bobpaul/dm9601-2.6/dm9601.c:127: warning: return from incompatible pointer type
/home/bobpaul/dm9601-2.6/dm9601.c: In function &#8216;__check_rega&#8217;:
/home/bobpaul/dm9601-2.6/dm9601.c:128: warning: return from incompatible pointer type
/home/bobpaul/dm9601-2.6/dm9601.c: In function &#8216;__check_nfloor&#8217;:
/home/bobpaul/dm9601-2.6/dm9601.c:129: warning: return from incompatible pointer type
/home/bobpaul/dm9601-2.6/dm9601.c: In function &#8216;get_registers&#8217;:
/home/bobpaul/dm9601-2.6/dm9601.c:192: warning: passing argument 7 of &#8216;usb_fill_control_urb&#8217; from incompatible pointer type
/home/bobpaul/dm9601-2.6/dm9601.c: In function &#8216;set_registers&#8217;:
/home/bobpaul/dm9601-2.6/dm9601.c:230: warning: passing argument 7 of &#8216;usb_fill_control_urb&#8217; from incompatible pointer type
/home/bobpaul/dm9601-2.6/dm9601.c: In function &#8216;set_register&#8217;:
/home/bobpaul/dm9601-2.6/dm9601.c:269: warning: passing argument 7 of &#8216;usb_fill_control_urb&#8217; from incompatible pointer type
/home/bobpaul/dm9601-2.6/dm9601.c: In function &#8216;update_eth_regs_async&#8217;:
/home/bobpaul/dm9601-2.6/dm9601.c:303: warning: passing argument 7 of &#8216;usb_fill_control_urb&#8217; from incompatible pointer type
/home/bobpaul/dm9601-2.6/dm9601.c:317: warning: passing argument 7 of &#8216;usb_fill_control_urb&#8217; from incompatible pointer type
/home/bobpaul/dm9601-2.6/dm9601.c:331: warning: passing argument 7 of &#8216;usb_fill_control_urb&#8217; from incompatible pointer type
/home/bobpaul/dm9601-2.6/dm9601.c: In function &#8216;read_bulk_callback&#8217;:
/home/bobpaul/dm9601-2.6/dm9601.c:486: warning: passing argument 6 of &#8216;usb_fill_bulk_urb&#8217; from incompatible pointer type
/home/bobpaul/dm9601-2.6/dm9601.c: In function &#8216;dm9601_start_xmit&#8217;:
/home/bobpaul/dm9601-2.6/dm9601.c:605: warning: passing argument 6 of &#8216;usb_fill_bulk_urb&#8217; from incompatible pointer type
/home/bobpaul/dm9601-2.6/dm9601.c: In function &#8216;dm9601_open&#8217;:
/home/bobpaul/dm9601-2.6/dm9601.c:804: warning: passing argument 6 of &#8216;usb_fill_bulk_urb&#8217; from incompatible pointer type
/home/bobpaul/dm9601-2.6/dm9601.c:813: warning: passing argument 6 of &#8216;usb_fill_int_urb&#8217; from incompatible pointer type
/home/bobpaul/dm9601-2.6/dm9601.c: In function &#8216;dm9601_disconnect&#8217;:
/home/bobpaul/dm9601-2.6/dm9601.c:1017: warning: ISO C90 forbids mixed declarations and code
make[2]: *** [/home/bobpaul/dm9601-2.6/dm9601.o] Error 1
make[1]: *** [_module_/home/bobpaul/dm9601-2.6] Error 2
make: *** [default] Error 2
```

---

### Post by xdivider on 2007-07-06
Juz in case someone needs an answer for this. 

If your lsusb output is not 0a46:9601, e.g. 0a46:6688, add  DM9601_DEV( "USB Ethernet", 0x0a46, 0x6688, DEFAULT_GPIO_RESET ) to the include file. Also change the line linux/config.h to linux/configfs.h. This is for 2.6.20 and earlier.

---

### Post by bobpaul on 2007-07-06
Well that's cool. Actually, it looks like I might have to do that for my device, too.
```
DM9601_DEV( "Davicom Semiconductor, Inc.", 0x0a46, 0x9601,
		DEFAULT_GPIO_RESET )
```

Any idea why my module is failing to compile, though?

---

### Post by xdivider on 2007-07-07
Id 9601 is in the dm9601.h file. This worked for me on a dapper and feisty kernel. Did u do the linux/config.h to linux/configfs.h change?

---

### Post by cobrn1 on 2007-07-08
EDIT: so i see that there's an official manufacturer 2.6 driver. Not sure what's wrong with that... sorry i can't help you more. You could, however, try the method below - it wored for me...

EDIT2: tell us if the method above works tho - sounds interesting...

***EDIT3: Ok, i had a quick look at the code for both the driver i suggest and the one you're trying, and they're by the same guy, except the one you're using is slightly tweaked (to compile under some older kernel, blah,blah blah - doesn't make a real difference to us). Anyway, sounds like the best bet is to try what thay're suggesting and ignore most of the post below. However, if you _do_ get this working then you might want to look at the second half of the post, ie, getting the module to run at startup so you don't constantly have to insmod it...***

Hi, i too have this usb->ethernat adaptor. I managed to get it working on 6.10, but have no idea if it'll work on 7.04. The original thread is here ([http://ubuntuforums.org/showthread.php?t=389330]("http://ubuntuforums.org/showthread.php?t=389330")), but I'll sum up here for you (cos i'm just that nice :D)

Basically, the diriver thay give on the website is for a different kernel version, so it won't work. There is a native version of the driver in the 2.6.21 kernel, but that's no goot for us until gutsy (where we'll be using 2.6.22 - until now we're stuck at 2.6.20, which doesn;t have the driver). However, some nice dude made a driver for us! The web page is here:

***GETTING THE DRIVER***

[http://alcopop.org/unix/linux/dm9601/]("http://alcopop.org/unix/linux/dm9601/")

It's the 'alternative 2.6 port' that you want. For the incredibly lazy here is a direct link (but please remember that you're sapping his bandwidth without looking at his webpage - please, try to find the option without the direct link:

[http://www.silencio.ro/DM9601.GZ](http://www.silencio.ro/DM9601.GZ)

Now i recommend making a directory to move this file into:

```
sudo mkdir /lib/modules/**2.6.17-10-generic**/dm9601
```

***NOTE: the bold bit will change depending on which kernel you are looking at - go and look in /lib/modules to see what the folder name is. Now substitute that for the bold bit and run the command***

You will probably need to change the permissions of the folder so that everyone can read the file. Have a look at the permissions that the other folders in that directory have and change the new folder to that.

***MAKING THE DRIVER***

Now, unzip the DM9601.GZ file into that folder. Read the 'readme'. Pretty easy, just open a terminal in the folder and run the makefile. Can't remember gow, but it does explain in the readme. I think its something like sude makefile or sudo make. It does say in the readme tho...

now you should have a lovely new file called dm9601.ko - this is your new driver!

***USING THE NEW DRIVER***

In order to get it working now, simple open a terminal in that folder (or cd your way into that folder) and type:

```
sudo insmod dm9601.ko
```

Like magic, your internet should now work! Check the internet configuration utility to check that ubuntu is now recognising a ethernet device. If so - horay, everything should be fine. You might need to tell it to use that device in the configurer, but i don't think so... oen up firefox and check that it works.

Note that this will only work once. Next time you boot up you will have to insmod again. If you want to avoid this then you can follow the steps below:

***GETTING THE MODULE TO RUN AT STARTUP***

First, insmod the module if you haven't already. It must be being used for this to work.

Now, open a terminal (or keep the current one open if you only just did that) and type:

```
sudo /sbin/depmod -ae
```

I believe that this updates ubuntu's driver list and their dependancies.

now type:

```
gksudo gedit /etc/modules
```

at the bottom of the (probably very short file) you need to add:

```
dm9601
```

on its own new line.

Save the file and exit. Now when you start up the module should be loaded and the adaptor should work straight off.




If this doesn't work then feel free to come back and comment, give error messages, etc, but at the mo I can't help anymore because i'm lacking an ubuntu installation to mess about with. All feedback appreciated.

This would be worth making a how-to on if it wasn't going to stop being a problem come october...

---

### Post by bobpaul on 2007-07-09
> **xdivider said:**
> Id 9601 is in the dm9601.h file. This worked for me on a dapper and feisty kernel.
Yes, it's in there twice, but both have different names. I guess that doesn't matter.

> **xdivider said:**
>  Did u do the linux/config.h to linux/configfs.h change?

No, I hadn't, but that would explain the "File or directory not found" error in my make output. 

That fixed it. To clarify for others, line 55 in dm9601.c should read ```
#include <linux/configfs.h>  
```

---

### Post by Jubo07 on 2007-08-03
Can someone give me step by step (complete noob here to Ubuntu) on how to activate the Davicom usb to Ethernet adapter (DM9601). I need fully typed code, please help. And I cannot use the internet on my ibook G3 because the Ethernet port no longer works. I have the file... 

[http://www.silencio.ro/DM9601.GZ](http://www.silencio.ro/DM9601.GZ) 

on my iBook via a USB drive. Please help, really important that I get the internet working on my iBook G3. :)

---

### Post by bobpaul on 2007-08-04
**Pre-Requirements**
You will need the "build-essential" and "linux-headers-generic" packages to install. If you do not have these packages, you can find them on packages.ubuntu.com, download the *.deb files and manually install them.

linux-headers-generic is a virtual packages that installs the correct headers for the current kernel you're running. You can find that out by typing 'uname -r' in the terminal. Mine is '2.6.20-16-generic'. That means what I should really download is the 'linux-headers-2.6.20-16-generic' package. Once you have your ethernet work, 'apt-get install linux-kernel-headers' so you always have the correct headers.

The 'build-essential' package has a lot of dependancies, and when you attempt to install the .deb file it will tell you what is missing. Go back to packages.ubuntu.com and download all of the *.debs for the packages it complains about.

If you're running Ubuntu, *.deb files can be installed by double clicking on them. On Kubuntu, you need to right click and choose the install option.

**Build the module**
[LIST=1]
[*]Goto [Davicom's website](http://www.davicom.com.tw/eng/download/Driver/driver_9601.htm) and download the "LINUX 2.6 Driver" to your home folder.
[*]Open up the Terminal and type 'tar -xzvf dm9601-2.6.tgz' to extract it.
[*]Type 'cd dm9601-2.6' to enter the newly created folder.
[*]Type 'gedit dm9601-2.6.c' to edit the broken source file.
[*]Change '#include <linux/config.h>' to '#include <linux/configfs.h>'
[*]Save the file and close gedit.
[*]Type 'make' to build the module.
[/LIST]

Ok, now you've built the module. At this point we can test it. With your Davicom USB adapter plugged in, type 'sudo insmod dm9601.ko' to temporarily insert the module. If everything works, we need to make this module insert automatically on bootup.

**Insert the module on bootup**
[LIST=1]
[*]Type 'sudo cp dm9601.ko /lib/modules/$(uname -r)/kernel/ubuntu/net/'
[*]type 'sudo gedit /etc/modules'
[*]Add 'dm9601' on it's own line at the end of the file
[*]Save and exit gedit.
[/LIST]

Your module should now work on reboot. Congratulations! You will need to repeat steps 2,3 & 7 from the Build stage and step 1 from the Insert stage whenever you install a kernel update.

**Troubleshooting**
If insmod failed to work, you probably need to add your USB device ID to the header file.

Type 'lsmod' and look for a line that belongs to your Davicom USB adapter. It should look similar to "Bus 001 Device 006: ID 0a46:9555 Davicom Semiconductor, Inc." If you have doubt, unplug all other USB devices and find the only line that doesn't have "0000:0000".

For the example above, type 'gedit dm9601.h" and insert 2 lines that look like:
```
DM9601_DEV( "Davicom Semiconductor, Inc", VENDOR_ACCTON, 0x0a46, 0x9555,
                DEFAULT_GPIO_RESET )
```

Your module source code is now configured to recognize your module. Continue from Step 6 in the Build stage of the instructions.

---

### Post by Jubo07 on 2007-08-04
Hi thanks for reply, but I ran into a problem...when i type in 'gedit dm9601-2.6.c' to edit the broken source file nothing comes up in the document. Also I am not sure how to install the build-essential for Dapper.

---

### Post by bobpaul on 2007-08-05
After step 3 the prompt should look like
```
user@host ~/dm9601-2.6$ _
```

If it doesn't then something went wrong in step 1 or 2. Perhaps you didn't save the .tgz file to your home folder?

If your prompt looks correct (ie, your in the dm9601-2,6 folder) then it's possible I mistyped the name of the .c file. Type 'ls' to list the files in that folder. I believe there's a .h file, a .c file, and a couple of other files.

To install build-essential on dapper type 'apt-get update; apt-get install build-essential'. This of course requires working internet, which I believe you said you didn't have. In that case, goto [http://packages.ubuntu.com](http://packages.ubuntu.com), choose dapper, and find the build-essential package.

If you have another machine that has internet running dapper, you can use that to build the kernel module provided both machines are running the same version. Kernel version can be checked, as I said, using 'uname -r'

**Edit**: Corrected typo: build-essential, not build-essentials :p

---

### Post by Jubo07 on 2007-08-05
Hi thanks again for the reply. I have one more thing to ask and I'm pretty sure that I will be on my way to getting this problem solved. How do you install build essential into dapper. I have the file in my home folder but I'm not sure what the code is to install it manually.

---

### Post by bobpaul on 2007-08-06
For dapper you should have downloaded build-essential_11.1_i386.deb Find that file and double click on it. It should open "Package Installer" and give the option to install the package. It might complain that you also need package x and y first, in which case you have to find and download those, as well.

From you terminal you can use 'dpkg -i build-essential_11.1_i386.deb'

---

### Post by Jubo07 on 2007-08-06
New problem 

When installing lib6.dev i recieved error:

[COLOR="Red"]Error: Dependency is not satisfiable: lib6[/COLOR]

What is lib6 ? How do I get this.

** Note: I am using powerpc not i386. I have build-essential_11.1_powerpc.deb on my laptop but I cannot install it yet because of the lib6 error. I have lib6-dev_2.6-2_powerpc.deb on my laptop but it cannot install because of the lib6 error above.

---

### Post by bobpaul on 2007-08-06
> **Jubo07 said:**
> 
[COLOR="Red"]Error: Dependency is not satisfiable: lib6[/COLOR]

What is lib6 ? How do I get this.

**[Edit]** I'm going to assume you meant lib**c**6, as there is neither a lib6 nor lib6-dev that I can find. There is, however, both a libc6 and a libc6-dev.**[/edit]**

That's one of those missing packages I told you about. Build-essential is dependent on a number of other packages (libc6-dev being one of them). If these aren't already installed, you can't install build-essential. Each of these packages may also have dependencies (such as libc6). Install libc6, then libc6-dev, then install build-essential. Repeat for any other dependencies it complains about.

You can get libc6 from packages.ubuntu.com, just like you got the build-essential package. This is a pain, and that's why we normally use apt-get, synaptec, or add/remove programs. Fortunately, when Gutsy is released you can upgrade to that and have native support for your network adapter so you shouldn't ever have to do this again.

> **Jubo07 said:**
> ** Note: I am using powerpc not i386. I have build-essential_11.1_powerpc.deb on my laptop
Oh, good call. You're correct to download the powerpc file.

---

### Post by Jubo07 on 2007-08-09
Hi again, I found this in another forum and I'm wondering if this would work, could you explain it to me like how to get to /etc/modules


Ubuntu, iBook and ethernet

When I first installed Ubuntu Dapper on my iBook, I couldn’t get the ethernet connection to work. Searching the forums gave this pearl: add the lines

    genrtc

    bmac

to the top of “/etc/modules.” Beautiful, it worked. I’m not sure what it all means, but it worked.&nbsp;

---

### Post by bobpaul on 2007-08-09
> **Jubo07 said:**
> Hi again, I found this in another forum and I'm wondering if this would work, could you explain it to me like how to get to /etc/modules

Step 2 in the "Insert Modules on Bootup section" of my first reply to you.

> **Jubo07 said:**
> > 
Ubuntu, iBook and ethernet

When I first installed Ubuntu Dapper on my iBook, I couldn&#8217;t get the ethernet connection to work. Searching the forums gave this pearl: add the lines

    genrtc

    bmac

to the top of &#8220;/etc/modules.&#8221; Beautiful, it worked. I&#8217;m not sure what it all means, but it worked.&nbsp;

To be clear, that won't do anything for your Davicom, but it might get your internal ethernet working. Unless we're talking about the Davicom, you should post in another thread or start a new one.

---

### Post by root.veg on 2007-09-03
Hi people - does anyone know where on earth you can get a Windows driver for this thing?!

I've been trying to work out how to use the exact same USB-ethernet adaptor under feisty, not got it going yet, but this thread has helped.

Anyway, I've got a dual-boot set-up (feisty / Win98 ) where the only working internet connection was using this USB-ethernet adaptor under Win98. I have since broken the connection while trying to get USB mass storage working on Win98 (which works OK, btw!).

Result: no internet connection and apparently no driver available. And no I don't have the software that came with it... It's a shared computer (hence dual-boot, not complete re-install) and the hardware just came as I found it.

Anyway, sorry for off-topicness, but this thread seems to contain the most knowledgeable comments on the subject I've found.

Thanks,

Andrew.

---

### Post by root.veg on 2007-09-03
NB I have actually found the manufacturer's website:

[http://shenztech.com/code/ui/product/product.aspx?prdid=SUSBE-ZT6688+&catid=4](http://shenztech.com/code/ui/product/product.aspx?prdid=SUSBE-ZT6688+&catid=4)

but they have no drivers for download, no manual, no FAQs, nada.

---

### Post by bobpaul on 2007-09-03
> **root.veg said:**
> Hi people - does anyone know where on earth you can get a Windows driver for this thing?!

In the first post in this thread I gave a link titled "[their website]("http://www.davicom.com.tw/eng/download/Driver/driver_9601.htm")" to davicomm's website. Davicomm makes the wifi chip used in your usb wifi unit. They have drivers for WinME, Win2k, WinXP, and linux on the same page. The WinME driver should work for Win98, I believe.

If that doesn't work...

> **root.veg said:**
> NB I have actually found the manufacturer's website:

[http://shenztech.com/code/ui/product/product.aspx?prdid=SUSBE-ZT6688+&catid=4]("http://shenztech.com/code/ui/product/product.aspx?prdid=SUSBE-ZT6688+&catid=4")

but they have no drivers for download, no manual, no FAQs, nada.

... either ask the Shenztech or do a google search for something like "dm9601 win98". I no longer have my device CD, or I'd copy the drive off it for you. (In fact, I just ran that google search and found this on the first page: [driverstock.info]("http://www.driverstock.info/Davicom-DM9801-Network-Driver-155021029-Windows-98-download_7747_0.html").)

---

### Post by root.veg on 2007-09-04
Well, I've been answered very efficiently by someone I contacted through the Shenztech website who pointed me here:

[http://pluscom.cn/Tech/Prd/USB2Ethernet/UE-ZT6688/WinDrivers.zip](http://pluscom.cn/Tech/Prd/USB2Ethernet/UE-ZT6688/WinDrivers.zip)

Which contains the correct drivers. Very nice of them.

Now to get it going under Feisty...

---

### Post by KaLiF101 on 2008-01-21
Hi everybody!
I don't know anything about linux, i am new and i have installed ubuntu 7.10. I got the same adaptor usb lan for davicom DM9601. I don't speak english very well so my english is bad. :(
Can you explain me  step by step from the beginning how can i install this driver please?
I am waiting for your response !
Thank you very much!

KaLiF101 : [email]reza_2000mg@hotmail.com[/email]

---

### Post by bobpaul on 2008-01-23
Step 1)
Install Ubuntu 7.10 (Gutsy)

Step 2) 
Plug in the device.

It's supported natively in the 2.6.21 and later kernels. Gutsy uses the 2.6.22 kernel.

---

### Post by IamAcoconut on 2008-07-14
Why cannot it be compiled on pre-Gutsy?
I did correct the dm9601.c, yet still I get the following:
- on Hardy:
```
make -C /lib/modules/2.6.24-19-generic/build M=/home/coconut/Desktop/9601 LDDINCDIR=/home/coconut/Desktop/9601/../include modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/coconut/Desktop/9601/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/coconut/Desktop/9601] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
```

- on Mepis6.5 - Dapper-based:
```
make -C /lib/modules/2.6.15-27-desktop/build M=/home/coconut/Desktop/dm9601 LDDINCDIR=/home/coconut/Desktop/dm9601/../include modules
make: *** /lib/modules/2.6.15-27-desktop/build: No such file or directory. Stop.
make: *** [default] Error 2
```

BTW Anyone knows where to get "complete" windows drivers for ndiswrapper? All linked in this thread seem to be broken, and I only found dm9usb.INF which ndiswrapper sees as corrupt without dm9usb.SYS accompanying it. Spent two hours googling and clustying to no avail.

---

### Post by bobpaul on 2008-07-16
> **IamAcoconut said:**
> Why cannot it be compiled on pre-Gutsy?
I did correct the dm9601.c, yet still I get the following:
- on Hardy:
Hardy is *post*-Gutsy. Support for this device has been included in the kernel since Gutsy. You shouldn't need to compile it on a Hardy based system.


I found a copy of the Windows driver [still hosted here]("http://www.lostmydrivers.com/network-drivers/davicom-semiconductor/davicom-dm9601-network-driver-2.10.02.0315-whql-windows-2000.html"), though. It looks like Davicom doesn't have any of the drivers on their website, still. Where did you download the linux driver you're attempting to compile from?

---

### Post by afterstep13 on 2008-07-22
i got a davicom 9601 usb ethernet adapter.

i use hardy-32 bit

when i plugin the device, i get a new device eth1

eth1      Link encap:Ethernet  HWaddr 00:60:6e:00:06:be  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:2 dropped:0 overruns:0 frame:2
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lsusb shows
Bus 003 Device 004: ID 0a46:9601 Davicom Semiconductor, Inc.

dmesg | tail
[  881.378032] usb 3-3: new full speed USB device using ohci_hcd and address 5
[  881.474647] usb 3-3: configuration #1 chosen from 1 choice
[  881.517244] eth1: register 'dm9601' at usb-0000:00:02.0-3, Davicom DM9601 USB Ethernet, 00:60:6e:00:06:be
[  881.624562] eth1: link down
[  881.645816] ADDRCONF(NETDEV_UP): eth1: link is not ready

but then i can't connect to the LAN using it. Network Manager gives a zero ip. dhclient fails with no connection.

The device wriks well in windows, so there isn't any hardware defect.

Please help

---

### Post by IamAcoconut on 2008-07-22
[QUOTE="bobpaul"]Hardy is post-Gutsy. Support for this device has been included in the kernel since Gutsy. You shouldn't need to compile it on a Hardy based system.[/QUOTE]
I know, I don't want it for Hardy, but for another computer, which is using Dapper-based distro. Still no idea why I couldn't compile it?


[QUOTE="bobpaul"]I found a copy of the Windows driver still hosted here, though. [/QUOTE] Thanks a lot! It works with ndiswrapper!
[QUOTE="bobpaul"]Where did you download the linux driver you're attempting to compile from?[/QUOTE] I think I tried all linked here but the one for old kernel.

[QUOTE="afterstep13"]but then i can't connect to the LAN using it. Network Manager gives a zero ip. dhclient fails with no connection.[/QUOTE]
Strange it doesn't work in Hardy, it was OK on my pc 'out of the box'. Did you try ndiswrapper? Maybe you have windows drivers on a CD, I'm uploading mine anyway, as it's hard to find them on the net. I'm using the driver linked by bobpaul, yet I just found the CD that came with my adapter, so here they are.

---

### Post by afterstep13 on 2008-07-22
i tried ndiswrapper, but it didn't work.
gave errors such as

[  262.845055] ndiswrapper: driver dm9usb (DAVICOM Semiconductor, Inc.,03/19/2002, 1.60.0319.2002) loaded
[  262.852927] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
[  262.852937] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[  262.852949] ndiswrapper (mp_halt:259): device f4246480 is not initialized - not halting
[  262.852952] ndiswrapper: device eth%d removed
[  262.852970] ndiswrapper: probe of 3-3:1.0 failed with error -22

with the above (win xp) drivers.

specifically did anyone successfully use this usb-lan card on hardy ?
could you please post dmesg, ifconfig  etc when you plug the device in ?

---

### Post by bobpaul on 2008-07-23
[quote="afterstep"]specifically did anyone successfully use this usb-lan card on hardy ?
could you please post dmesg, ifconfig etc when you plug the device in ? [/quote]
Just plugged mine in and it worked on hardy.

dmesg:
```
[247193.676751] usb 1-3: new full speed USB device using ohci_hcd and address 12
[247193.786884] usb 1-3: configuration #1 chosen from 1 choice
[247194.100012] eth1: register 'dm9601' at usb-0000:00:13.0-3, Davicom DM9601 USB Ethernet, 00:60:6e:df:0d:10
[247194.100062] usbcore: registered new interface driver dm9601
[247194.423233] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[247205.262049] eth1: no IPv6 routers present

```

lsusb 
```
Bus 001 Device 012: ID 0a46:9601 Davicom Semiconductor, Inc. 
```

ifconfig eth1
```
eth1      Link encap:Ethernet  HWaddr 00:60:6e:df:ff:ff  
          inet addr:192.168.2.187  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::260:6eff:fedf:d10/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:342 errors:0 dropped:0 overruns:0 frame:0
          TX packets:390 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:173931 (169.8 KB)  TX bytes:76782 (74.9 KB)

```

lsmod | grep net
```
lsmod | grep net
usbnet                 23304  1 dm9601
mii                     7552  4 dm9601,usbnet,8139too,8139cp
usbcore               169904  10 dm9601,usbnet,usb_storage,libusual,ftdi_sio,usbserial,usbhid,ehci_hcd,ohci_hcd

```

I would suspect you have some other problem with your system than a driver related issue. If the dm9601 kernel module is autoloading when you plug it in, it's recognizing your usb device id (0a46:9601) and should be functional.

Try booting from a Hardy LiveCD and plugging it in once you're on the desktop. This would simulate a clean installation. Out of curiousity, you said it works on windows... it's not getting an IP address of 169.x.x.x, is it? The only thing I can think of off hand is that your network lacks a DHCP server and windows is making up it's own IP. Ubuntu will not do that, but you can set a Static IP and test that way. Perhaps if the LiveCD doesn't work you should briefly explain how your network is setup.

[quote="IamAcoconut"]scripts/Makefile.build:46: *** CFLAGS was changed in "/home/coconut/Desktop/9601/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
[/quote] This is the error that caused it to stop. It appears the make file is no longer compatible with how things are done on Hardy?? My guess would be to edit the make file line 46 and change CFLAGS to EXTRA_CFLAGS.

[quote="IamAcoconut"]make: *** /lib/modules/2.6.15-27-desktop/build: No such file or directory. Stop.
[/quote]
As for the dapper system, I'm not sure why it gave this error. Did you do "sudo make install"? Or maybe you don't have 2.6.15-27 kernel sources installed? "make" should just need read access and compile to the local folder, but "make install" will need to write the module file into the right location, and thus needs to be done with as root.

---

### Post by afterstep13 on 2008-07-23
> Out of curiousity, you said it works on windows... it's not getting an IP address of 169.x.x.x, is it?

no it works well, infact i'm using it right now.

and my network has a dhcp server too. (I have an ethernet port, and can connect using it)

---

### Post by angel5446 on 2008-07-24
I've uploaded the whql drivers for windows xp that downloaded from davicom time ago and the linux 2.6 driver that was in the davicom website it took me a day to found it. enjoy :)

---

