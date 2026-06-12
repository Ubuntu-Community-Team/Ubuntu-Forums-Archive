---
title: "Can't Install Modem"
date: 2005-04-14
forum: Networking &amp; Wireless
---

### Post by fingerslip on 2005-04-14
Hello!

I am a noob in linux!
I can't instal the modem!
Modem Icedata 500
My ISP has the drivers for linux [http://www.oninet.pt/downloads/USB-APL-1-1.8-0.1.0.1.tar.gz](http://www.oninet.pt/downloads/USB-APL-1-1.8-0.1.0.1.tar.gz) , but can't get them to work!

It give me this error!

> 
fingerslip@fingerslip:~/Linux/USB-APL-1-1.8-0.1.0.1$ cd unicorn_linux
fingerslip@fingerslip:~/Linux/USB-APL-1-1.8-0.1.0.1/unicorn_linux$ make all
for i in adsl_modem_status unicorntest tools ; do make -C $i all ; done
make[1]: Entrando no diretório `/home/fingerslip/Linux/USB-APL-1-1.8-0.1.0.1/uni corn_linux/adsl_modem_status'
make    all-recursive
make[2]: Entrando no diretório `/home/fingerslip/Linux/USB-APL-1-1.8-0.1.0.1/uni corn_linux/adsl_modem_status'
Making all in intl
make[3]: Entrando no diretório `/home/fingerslip/Linux/USB-APL-1-1.8-0.1.0.1/uni corn_linux/adsl_modem_status/intl'
make[3]: Nada a ser feito para `all'.
make[3]: Saindo do diretório `/home/fingerslip/Linux/USB-APL-1-1.8-0.1.0.1/unico rn_linux/adsl_modem_status/intl'
Making all in m4
make[3]: Entrando no diretório `/home/fingerslip/Linux/USB-APL-1-1.8-0.1.0.1/uni corn_linux/adsl_modem_status/m4'
make[3]: Nada a ser feito para `all'.
make[3]: Saindo do diretório `/home/fingerslip/Linux/USB-APL-1-1.8-0.1.0.1/unico rn_linux/adsl_modem_status/m4'
Making all in intl
make[3]: Entrando no diretório `/home/fingerslip/Linux/USB-APL-1-1.8-0.1.0.1/uni corn_linux/adsl_modem_status/intl'
make[3]: Nada a ser feito para `all'.
make[3]: Saindo do diretório `/home/fingerslip/Linux/USB-APL-1-1.8-0.1.0.1/unico rn_linux/adsl_modem_status/intl'
Making all in po
make[3]: Entrando no diretório `/home/fingerslip/Linux/USB-APL-1-1.8-0.1.0.1/uni corn_linux/adsl_modem_status/po'
make[3]: *** Sem regra para processar o alvo `POTFILES.in', necessário por `Make file'.  Pare.
make[3]: Saindo do diretório `/home/fingerslip/Linux/USB-APL-1-1.8-0.1.0.1/unico rn_linux/adsl_modem_status/po'
make[2]: ** [all-recursive] Erro 1
make[2]: Saindo do diretório `/home/fingerslip/Linux/USB-APL-1-1.8-0.1.0.1/unico rn_linux/adsl_modem_status'
make[1]: ** [all-recursive-am] Erro 2
make[1]: Saindo do diretório `/home/fingerslip/Linux/USB-APL-1-1.8-0.1.0.1/unico rn_linux/adsl_modem_status'
make[1]: Entrando no diretório `/home/fingerslip/Linux/USB-APL-1-1.8-0.1.0.1/uni corn_linux/unicorntest'
gcc -DVERS=0x078 -Wall -Wstrict-prototypes -O2 -DLINUX -I../amu/ -I../include/ u nicorntest.c -o unicorntest
make[1]: gcc: Comando não encontrado
make[1]: ** [unicorntest] Erro 127
make[1]: Saindo do diretório `/home/fingerslip/Linux/USB-APL-1-1.8-0.1.0.1/unico rn_linux/unicorntest'
make[1]: Entrando no diretório `/home/fingerslip/Linux/USB-APL-1-1.8-0.1.0.1/uni corn_linux/tools'
gcc -DVERS=0x078 -Wall -Wstrict-prototypes -O2 -DLINUX -I../amu/ -I../include/ m ain.c unicorn_status.c unicorn_device.c  -o unicorn_status
make[1]: gcc: Comando não encontrado
make[1]: ** [unicorn_status] Erro 127
make[1]: Saindo do diretório `/home/fingerslip/Linux/USB-APL-1-1.8-0.1.0.1/unico rn_linux/tools'
make: ** [all_applis] Erro 2
fingerslip@fingerslip:~/Linux/USB-APL-1-1.8-0.1.0.1/unicorn_linux$



Thx in adavnce!

---

### Post by az on 2005-04-14
After a quick look, it seems to be for 2.4 kernels...

---

### Post by fingerslip on 2005-04-14
[QUOTE=azz]After a quick look, it seems to be for 2.4 kernels...[/QUOTE]

which means that this driver wont work on this kernel 2.6.10, and there is any alternative besides buy a new modem? :grin:

---

### Post by alastair on 2005-04-14
Newer version here :

[http://www.bewan.com/bewan/drivers/bast-0.9.0.tgz](http://www.bewan.com/bewan/drivers/bast-0.9.0.tgz)

From a google search for : Icedata 500 linux 2.6

Leading to : [http://www.bewan.com/bewan/users/downloads/index.php](http://www.bewan.com/bewan/users/downloads/index.php)

This APPEARS to be a newer version of the driver you have. Version == 0.9.0 (vs 0.7.8. ).

Who knows? No idea if it works.

I'd always try and avoid USB modems and go for an external DSL router/modem. They're not expensive, and less hassle.

---

### Post by fingerslip on 2005-04-15
[QUOTE=alastair]Newer version here :

[http://www.bewan.com/bewan/drivers/bast-0.9.0.tgz]("http://www.bewan.com/bewan/drivers/bast-0.9.0.tgz")

From a google search for : Icedata 500 linux 2.6

Leading to : [http://www.bewan.com/bewan/users/downloads/index.php]("http://www.bewan.com/bewan/users/downloads/index.php")

This APPEARS to be a newer version of the driver you have. Version == 0.9.0 (vs 0.7.8. ).

Who knows? No idea if it works.

I'd always try and avoid USB modems and go for an external DSL router/modem. They're not expensive, and less hassle.[/QUOTE]

That one i also have and gives me a error too, thx anyway! :grin:

---

### Post by az on 2005-04-15
You have build-essential installed?  Does the readme say you need anythign else?

---

### Post by fingerslip on 2005-04-15
[QUOTE=azz]You have build-essential installed?  Does the readme say you need anythign else?[/QUOTE]
 
  > INTRODUCTION:
 
 The software for the UNICORN ADSL PCI card consists of two loadable drivers, 
 the unicorn_atm.o and unicorn_pci.o. The unicorn driver is a standard Linux 
 ATM driver, that performs segmentation and reassembly (SAR) and flow control.
 The unicorn_pci driver contains the ADSL modem software and hardware related
 functions. It has been tested with the Linux 2.4.x kernels. Note that to use
 PPPoE, PPPoA or RFC2684 protocols, the kernel may need to be patched.
 
 COMPILATION:
 
 To compile the drivers, unzip and untar the file. In the unicorn directory you 
 will find the two subdirectories unicorn_atm and unicorn_bus.
 You may compile the drivers based on the include files in the kernel source
 or standard kernel include files. Set the variable KERNELDIR in the Makefile's
 to point to your kernel sources if the first option in chosen. 
 If you choose the latter, you may need to copy the contents of the kernel 
 source "include/net" directory into "/usr/include/net/".
 Go into these subdirectories and do a "make" and a "make install".
 If the compile option "USE_HW_TIMER" is set, the performance is increased, 
 but the CPU load increased. 
 Use the same compiler as you use when compiling the linux kernel. The driver has
 been tested using gcc-2.96, gcc-2.95.2, gcc-2.91.66 and gcc 3.0.3.
 
 
 INSTALLATION:
 
 To start the ADSL software, do a "modprobe unicorn_pci". Check in the syslog that
 the drivers are started OK. The ADSL line should come up automatically. The status
 can also be checked using the "proc" interface (/proc/net/atm/UNICORN\:0". 
 SHOWTIME in the log or in the status means that ADSL connction is up and ATM cells
 may be transmitted and received.
 Depending on your network setup, you will need additional software as with any other
 ADSL ATM card. For bridged ethernet (RFC2684), the br2684.o module and brctl is needed.
 For PPPoE, any pppoe client over the bridged interface (nas0) should work 
 (Roaring Penguin pppoe client has been tested).
 The scripts directory contains some example startup scripts.
 
 Bridged (RFC2684) and PPP over Ethernet:
 Depending on your kernel, you may need to patch the kernel and enable the option
 "RFC1483/2684 Bridged protcols" under "Networking options". Also ATM support needs
 to be enabled.
 Also the user space daemon "brctl" is needed. Instructions on how to apply the
 patch and the brctl and patch sources can be found at [http://www.zoftware.org/adsl-pppoe]("http://www.zoftware.org/adsl-pppoe").
 
 PPP over ATM:
 For PPP over ATM, the module pppoatm.o is needed, together with the pppd plugin
 pppoatm.so and a version of pppd that supports plugins.
 Currently version ppp-2.4.0b2 supports PPPoATM plugins. A patched version ready for
 PPPoATM can be found at [http://www.sourceforge.net/]("http://www.sourceforge.net/").
 
 PPPoATM specific pppd options:
 llc-encaps: use LLC encapsulation for PPPoATM
 vc-encaps: use VC multiplexing for PPPoATM (default)
 
 
 MODULE PARAMETERS:
 
 Some ADSL paramters can be controlled by setting the moule paramters.
 
 unicorn_pci.o:
 --------------
 
 ActTimeout: Timeout in ms on the duration of the activation state.
 
 ActivationMode: This parameter sets in what mode the ADSL modem should be activated.
 ANSI mode is 1, G.lite is 2, G.dmt is 4 and MULTI mode is 3.
 If you know what mode your DSLAM operates in, use this mode. If not select either
 ANSI or MULTI mode.
 
 DownstreamRate: The maximum downstream rate in Kbit/sec.
 
 AutoActivation: Set this to 1 if you your ADSL modem to start auotmatically (default 1).
 
 DebugLevel: To debug the driver, set this to a value different from 0 and enable DEBUG
 when compiling.
 
 MswDebugLevel: 0 - High level, all traces enabled, 1 - Medium level, info and warnings
 enabled, 2 - Low level, only warnings and errors are traced. 
 
 LCD_Trig: Persistency time (in msec) of Loss of Cell Deliniation defects before
 disorderly shutdown (15000 default).
 
 LCD_LOF_Trig: Persistency time (in msec) of Loss of Signal and Loss of Frame defects before
 disorderly shutdown (5000 default). 
 
 TrainingDelay: Delay in msec used in training sequence. Default 80.
 
 useRFCFixedRate: If 1, rate adaptive disabled. To use with ECI DSLAM in ITU mode.
 
 _no_TS652: If set to 1, enable gain table for use without TS652.
 
 unicorn_atm.o:
 --------------
 
 mac_address: If this is specified, the bridged ethernet (RFC2684) will use this
 mac (ethernet) address instead of a randomly generated address. Specified as a 
 12 character ASCII string of hexadecimal numbers.
 
 atmready_timeout: The time in seconds to wait for ADSL link up when opening the ATM
 socket (default 20 seconds).
 
 DebugLevel: Set this if you need to debug the driver.
 
 DIV:
 
 mswtest contains a simple program to start/stop and get statistics from the ADSL card.
 Depending on your distribution, you may need to install atm support (atm-2.4.0) to
 compile this program.
 

:grin:

---

### Post by alastair on 2005-04-15
No need to post the whole README.

This message :

make[1]: gcc: Comando não encontrado

Means "command not found"?

If you type "gcc -v" in a shell, what is printed?

If you get "Comando não encontrado", you need to install a compiler.

i.e. install the package "build-essential" ...

---

### Post by mrdj1234 on 2005-04-17
Hi!

Just found this thread while looking for an answer to my own probs - thought i'd help out.

It looks like the Icedata is a Globespan/billion based USB ADSL modem. If it is, why not try the usermode drivers from [http://eciadsl.flashtux.org](http://eciadsl.flashtux.org)

the .deb installs straight away - just plug in the info and off you go, works fine with all 2.6 kernels and does work very well with Hoary.

---

### Post by silva on 2005-05-10
hi 
i have the same problem that fingerslip has :P but mine even compiles the drives (same modem too.. even same readme). 
what i just don't know is what to do after the modprobe 
i.e.
i go the the dir where i extrated the thing... after that i do 
make
just that
next modprobe -v -c -s unicorn_pci (or unicorn_usb i 've tried them all)
the next thing that the readme say's if i remember is that the light's on the modem should pop up... welll with me nothing happen... what did i do wrong?
was the compilling part or did i skip something?

thanks :D

---

### Post by Nightwish on 2005-05-19
same problem, maybe i'm missing development libs.

you should probably only insert the cable after the modprobe or smtg. drivers are shit, even in windows.

---

### Post by RMF on 2006-01-14
i'm realy noob soo the readme has too much advanced tecnics knowlegd for me.....plz if some one can explain to me how to install the drivers pass-by-pass i would be very pleased

---

### Post by placide on 2006-03-03
I all!
If you live in Portugal (or not!?!) and have problems with **Icedada 500** modem installation, check my website.

[http://placide.home.sapo.pt](http://placide.home.sapo.pt)

-- Linux -- section
this part of the website is im portuguese since this is a portuguese issue (I think!)

You will found there an automatic installation script and manual installation instructions (use the one you prefer).

Hope this will help.
:mrgreen:

---

### Post by placide on 2006-03-04
Hi all

Check this site

[http://placide.home.sapo.pt](http://placide.home.sapo.pt)

Section: -- Linux --

Lots of goodies

Good luck (portuguese language only... sorry!!!)

---

### Post by www.rzr.online.fr on 2006-05-18
I managed to get it working , if it helps : [http://rzr.online.fr/q/unicorn-modules](http://rzr.online.fr/q/unicorn-modules)

I wish I can take back the debian package, but then I'll need you to test it on a debian system 

Please contact me if interessed

---

