---
title: "Installing dialup internal modem driver"
date: 2008-01-24
forum: Networking &amp; Wireless
---

### Post by Jessica's on 2008-01-24
Hi all
I am very new to this and im having problems installing the martian driver on my internal Lucent winmodem.
I opened up the terminal and only typed:
$ make -C kmodule/ modules   (as it says in the instructions below)
I get a message that says =  make: *** Kmodule/: No such file or directory.    Stop.)
I cant work it out, has it something to do with permissions or do i need to be in a special place in terminal? I have tried the other commands but i get a don't have permission message. Could someone please help me I'm really stuck.





These are the instruction to install the modem driver.
x86_64 platform.
----------------
martian_modem is a 32-bit application. It can be built on x86_64 the
way prescribed, but you need 32-bit development environment for that.
Second option is to use binary built on i386.

To compile and install module only do
$ make -C kmodule/ modules 
$ sudo make -C kmodule/ install
------------------
attached is martian_modem.gz compiled in my 32 bit environment.
Under Linux do:
$ gunzip martian_modem.gz
$ sudo cp martian_modem  /usr/sbin/ (/usr/sbin/ is not a directory: No such file or dir
$ sudo chmod +x  /usr/sbin/martian_modem
completes the installation

$ martian_modem --help
for command guidance

Once martian_dev.ko has been installed your steps are:
$ sudo modprobe martian_dev
loads the driver.
$ sudo martain_modem --country=us
sets up the modem and creates the modem port.
Leave it running

Open another console
$ sudo wvdialconf  /etc/wvdial.conf
should report finding the modem.

With
$ sudo gedit /etc/wvdial.conf
delete the ;  <  >  symbols while adding your personal info and adding a line:
Carrier  Check  =  no

Save
Try a dialout with
$ sudo wvdial

---

