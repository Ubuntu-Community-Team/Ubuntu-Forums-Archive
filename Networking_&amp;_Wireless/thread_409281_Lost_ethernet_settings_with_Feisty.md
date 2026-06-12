---
title: "Lost ethernet settings with Feisty"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by hdotcom on 2007-04-14
Hi,

I am a linux newbie and thought i'd start off learning linux by using ubuntu. I installed ver 6.10 on my ThinkPad T60 (without updating it) and faced several problems with the display and the overall performance despited following the online guides for T60.

So i decided to install feisty and it was great...it detected the ATI drivers and even my wireless card. For some odd reason it wont detect my Intel ethernet card although 6.10 did !! I tried to run the commands ifup/ifdown eth0 but it insisted that i dont have it installed.

Are there any commands to manually install the network card?

Cheers!

H.

---

### Post by chili555 on 2007-04-14
Sometimes, they can be shy, can't they? What kind of card is it?```
sudo lshw -C network
```I think we can wake it up!

---

### Post by hdotcom on 2007-04-17
Hi There..

Sorry to get back late but i was on leave. I tried the command u suggested but it didnt wake it up. The output that i got is as follows:

 *-network UNCLAIMED     
       description: Ethernet controller
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: iomemory:ee000000-ee01ffff ioport:3000-301f irq:16

The network card is an Intel PRO/1000 LAN adapter. I really dont get it ! it was working fine on 6.10 i would really appreciate your assistance guys am looking forward to this upgrade.

Rgds,

H.

---

### Post by hdotcom on 2007-04-17
Guys...

Just found something interesting after running the dmesg command..

[  401.580000] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[  401.580000] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[  401.580000] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.

I think the kernel has considered my card as a PCMCIA card. Any hints ?

Rgds,

H.

---

### Post by chili555 on 2007-04-17
> I think the kernel has considered my card as a PCMCIA card.I don't think so. I think it detected a PCMCIA slot that's empty when you did lshw. I think we can safely ignore that scary message.

Your ethernet adapter uses a module e1000. Please do:```
sudo modprobe e1000
ifconfig
```and see if your ethernet has awakened. If so, and if the cable is connected, please do:```
sudo dhclient eth0
```You will probably connect.

If it does not 'stick' on reboot, you can *sudo gedit /etc/modules* to add a line:```
alias eth0 e1000
```Post back and let us know.

---

### Post by hdotcom on 2007-04-17
Hi there..

Running the command below only shows that atho, lo and wifi0 have been detected. So eth0 is not up yet.

```
sudo modprobe e1000
ifconfig
```

And running the following command...
```
sudo dhclient eth0
```

outputs the following:
```

wifi0: unknown hardware address type 801
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
wifi0: unknown hardware address type 801
Bind socket to interface: No such device

```

Unfortunately still not working. Any ideas?

Rgds,

H

---

### Post by hdotcom on 2007-04-18
Just tried a fresh new installation of feisty and applied all updates and the problem still persists :confused: !

---

### Post by amarkovits on 2007-04-20
hy, i have the same problem (also on a T60 laptop)
i'm not 100% sure but i think it a problem with the 2.6.20 kernel.
When I boot-up in the old kernel that i have since edgy, the ethernet card is working fine, but when  i boot-up in the new kernel the eth0 interface is not visible.

---

### Post by amarkovits on 2007-04-20
ok, i managed to fix it:
just run the script provided by lenovo:

[http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-67166](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-67166)

so easy :)

---

### Post by hdotcom on 2007-04-20
That script didnt work with me :(  Which kernel are you running?

---

### Post by SpaceTeddy on 2007-04-21
i have the same Problem (Samsung X60). i would really appreciate it if someone could tell me what is wrong. Neither the module load nor anything else mentioned in this thread worked for me. 

and i am running 2.6.20-15-generic kernel

---

### Post by SpaceTeddy on 2007-04-21
ok guys, i figured out how to get the network-card working again - but but warned, this is an UGLY HACK and no real solution. It is also quite possible that you will have to do this EVERY TIME the kernel gets an update...

i will run you through what i have done:
Quick note: [COLOR="Red"]red are commands[/COLOR], [COLOR="RoyalBlue"]blue is file or console output[/COLOR]
first, check if you have the same problem as me...
[COLOR="Red"]
sudo rmmod e1000
sudo modprobe e1000
sudo dmesg |tail
[/COLOR]
now check if you have errors looking like this in the log :
[COLOR="Blue"]
[ 4390.968000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[ 4391.024000] e1000: 0000:02:00.0: e1000_probe: The EEPROM Checksum Is Not Valid
[ 4391.044000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[ 4391.044000] e1000: probe of 0000:02:00.0 failed with error -5
[/COLOR]
if you do, then you have the same problem as me - namely the checksum for the network card does not come out correctly. Either you buy a new computer, or you have to make it ignore the checksum and continue anyway. i must stress again, that this might break somethng - but it did not for me.

ok - you are warned - here is how you make it ignore that checksum

download the sources for the network card here [http://belnet.dl.sourceforge.net/sourceforge/e1000/e1000-7.4.35.tar.gz]("http://belnet.dl.sourceforge.net/sourceforge/e1000/e1000-7.4.35.tar.gz")
unzip them somewhere and go edit the file e1000_main.c in the src subdirectory

around line 1136 (for me it was that line) you will find something like :
[COLOR="Blue"]
if (e1000_validate_nvm_checksum(&adapter->hw) < 0) {
      DPRINTK(PROBE, ERR, "The NVM Checksum Is Not Valid\n");
       err = -EIO;
       goto err_eeprom;
}
[/COLOR]
change this to 
[COLOR="Blue"]
if (e1000_validate_nvm_checksum(&adapter->hw) < 0) {
      DPRINTK(PROBE, ERR, "The NVM Checksum Is Not Valid\n");
}
[/COLOR]
by deleteing the last two lines in that block. then save and close the file
now you driver is patched - lets install it:
run the following commands in the src directory of the driver:
[COLOR="Red"]
sudo make
sudo make install
[/COLOR]
this wil build the driver, delete the old one and rebuild the new one. if you get any errors for building, you might not have the kernel-headers installed - you can do that by running
[COLOR="Red"]
sudo apt-get install libstdc++5 linux-headers-$(uname -r)
[/COLOR]
then retry the make commands.

if you see something like
[COLOR="Blue"]
install -D -m 644 e1000.ko /lib/modules/2.6.20-15-generic/kernel/drivers/net/e1000/e1000.ko
/sbin/depmod -a || true
install -D -m 644 e1000.7.gz /usr/share/man/man7/e1000.7.gz
man -c -P'cat > /dev/null' e1000 || true
man: 
Kann im catman Modus nicht nach /var/cache/man/cat7/e1000.7.gz schreiben
e1000.
[/COLOR]
the driver is most likely installed. now check if the new module loads again by using
[COLOR="Red"]
sudo rmmod e1000
sudo modprobe e1000
dmesg |tail
[/COLOR]
the output should now be something like :
[COLOR="Blue"]
[ 4929.880000] e1000: 0000:02:00.0: e1000_probe: The NVM Checksum Is Not Valid
[ 4929.880000] e1000: 0000:02:00.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:13:77:04:cd:26
[ 4929.940000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[ 4930.400000] e1000: eth0: e1000_request_irq: Unable to allocate MSI interrupt Error: -22
[ 4930.404000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4931.812000] e1000: eth0: e1000_watchdog_task: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 4931.812000] e1000: eth0: e1000_watchdog_task: 10/100 speed: disabling TSO
[ 4931.812000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[/COLOR]
and issuing
[COLOR="Red"]
ifconfig
[/COLOR]

should also show you your network card again.

i hope this helps... it worked for me. 

me tired - me go to bed now...

---

### Post by hdotcom on 2007-04-21
Hey there...

Found an easier fix to my problem. Downloaded the ProBoot.exe file from Intel.com and extracted the files to a floppy disk (system files included). Booted using the disk and reset network card and ROM included. It worked beautifully after that. Lets hope i don't jinx it !

Lata,

H.

---

### Post by SpaceTeddy on 2007-04-21
> **hdotcom said:**
> Hey there...

Found an easier fix to my problem. Downloaded the ProBoot.exe file from Intel.com and extracted the files to a floppy disk (system files included). Booted using the disk and reset network card and ROM included. It worked beautifully after that. Lets hope i don't jinx it !


can you please provide a link to the tool since i do not know what you mean exactly. also, is it possible to get that thing on cd's ? my computers don't have floppys anymore (for years now) and i would need to buy a usb-floppy drive and a pack of floppys just to apply the fix...

but big thanks for the help

---

### Post by hdotcom on 2007-04-22
Hey there..

Am sorry it seems my post wasn't clear. Basically the tool Proboot.exe will reset the Expansion Rom on the network adapter. For some odd reason mine was corrupted perhaps due to a previous BIOS update.

The steps to follow are as follows:

1)Just [download   ]("http://downloadfinder.intel.com/scripts-df-external/download.aspx?url=/8242/eng/PROBOOT.exe&DwnldId=8242&ProductID=412&lang=eng") the tool and extract it to folder
2) Create a boot able CD and copy the contents of that folder to the CD
3) Boot with the CD and run the command IBAUtil.exe -DEFCFG
4) Wait for the process to complete and restart your computer. Now check if feisty detects your network adapter.

You might also want to check more info on the subject from [Intel]("http://www.intel.com/support/network/adapter/pro100/bootagent/sb/cs-008362.htm")

Rgds,

H.

---

### Post by SpaceTeddy on 2007-04-23
thank you !
thank you !!
thank you !!!

> **hdotcom said:**
> 
2) Create a boot able CD and copy the contents of that folder to the CD


i don't know f i am just too stupid... but... um... i know how to create a bootable cd - but what shall it boot ? linux, dos, windows ? is windows vista even capable of creating boot cd's ? or do i need xp for that - the rest is clear to me, but i still don't know how to create that disk so i can run the intel tools on... confusion on my head... 

i think i have been away from boot medias for too long... 
if you could answer that last quest, i will be grateful for a long time :)

thanks in advance for all the trouble

---

### Post by hdotcom on 2007-04-25
Hi..

First you need to get a breather....inhale ....now exhale :) Its easy mate, first you need to create the bootable CD and make sure the files you extracted are on the same CD. You will need to boot into DOS (or command prompt). So you will be prompted with the CD Drive letter -> D:\ once you've booted. Finally you just need to run the command i gave you earlier. Let me know how it goes ;).

Rgds,

H.

---

### Post by BingMan on 2007-04-25
Hey, 

got the same problem with Feisty and a Thinkpad T60 with the same ethernet card. Actually, the wireless is sitting at eth0, and the pro/1000 is nowhere to be seen. Actually, the system sees it in hardware, but just doesn't use it as an ethernet card. I did your trick with ibautil.exe, but didn't get any results. :(

A complete newbie here - just switched (or in the process of switching) to Linux from a lifelong Windoze addiction. Time to get clean.:)

---

### Post by SpaceTeddy on 2007-04-25
ok - got it working... 

i will rewrite again what i have done although this only works thanks to hdotcom ! so credits for this go to him :)

first - go to the intel webpage and download the tool proboot.exe or use this link :
[http://downloadfinder.intel.com/scripts-df-external/confirm.aspx?httpDown=http://downloadmirror.intel.com/df-support/8242/eng/PROBOOT.exe&agr=&ProductID=871&DwnldId=8242&strOSs=&OSFullName=&lang=eng](http://downloadfinder.intel.com/scripts-df-external/confirm.aspx?httpDown=http://downloadmirror.intel.com/df-support/8242/eng/PROBOOT.exe&agr=&ProductID=871&DwnldId=8242&strOSs=&OSFullName=&lang=eng)

If the Link doesn't work go to:
[www.intel.com](www.intel.com)
-> Support & downloads 
-> search for proboot.exe 
-> choose (from the results) the link stateing (should be the third)
    Intel® Boot Agent - How to Update the Intel® Boot Agent on Your ...
-> click on the Link PROBOOT.EXE (right at the start of the text)
-> navigate to the appropriate network card ( for me it was number 14 - named: Intel® PRO/1000 MT Desktop Adapter
-> click on PROBOOT.EXE - NOT THE NETWORK CARD DESCRIPTION
-> from there is is simple... or should be....

once you have (successfully) downloaded the file, take any windows and create a normal bootable disk or floppy. This can usually be done with (for a floppy) with a right click on the drive and choose format. there you will find a small button called something like "make disk bootable" (i only know what it says in german :) )

once you have the boot disk, install the Proboot.exe, remeber where it installed (probably c:\intel12) and copy everything from that folder also into the floppy.

now reboot from the floppy - once you have the command line, run the command ibautil -defcfg.

then reboot and Linux should once again accept your network card... hopefully anyway. It worked for me too.

big thanks to everyone who helped.

---

### Post by tux_rox on 2007-04-25
Does this always happen with Thinkpad T60s?  They look nice.

---

### Post by corte123 on 2007-11-25
Hi everyone , I dont have a windows os on my hardrive , wil this work with vmware ?

---

