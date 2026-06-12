---
title: "Cannot install drivers for motherboard/graphics card"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by ilikepaste on 2011-04-03
I just bought a new computer, and decided to put ubuntu 10.10 (x32) on it. HEre are my system specs:


Processor: Intel Core i5-2500 Sandy Bridge 3.3GHz (3.7GHz Turbo Boost) 4 x 256KB L2 Cache 6MB L3 Cache LGA 1155 95W Quad-Core Desktop Processor BX80623I52500

MOBO: GIGABYTE GA-P67A-UD3-B3 LGA 1155 Intel P67 SATA 6Gb/s USB 3.0 ATX Intel Motherboard

Graphics card: SAPPHIRE 100296HDMI Radeon HD 4670 1GB 128-bit DDR3 PCI Express 2.0 x16 HDCP Ready CrossFireX Support Video Card

RAM: Patriot G Series &#8216;Sector 5&#8217; Edition 4GB (2 x 2GB) 240-Pin DDR3 SDRAM DDR3 1600 (PC3 12800) Desktop Memory Model PGV34G1600ELK

Hard drive: Western Digital Caviar Blue WD5000AAKX 500GB 7200 RPM 16MB Cache SATA 6.0Gb/s 3.5" Internal Hard Drive -Bare Drive

PSU: APEVIA ATX-AQ700W-BK 700W ATX12V / EPS12V SLI Ready CrossFire Ready Power Supply

CD/DVD player: LITE-ON Black 24X DVD+R 8X DVD+RW 8X DVD+R DL 24X DVD-R 6X DVD-RW 12X DVD-RAM 16X DVD-ROM 48X CD-R 32X CD-RW 48X CD-ROM 2MB Cache SATA 24X DVD Writer

I've visited the websites for the motherboard and the graphics card, and downloaded the linux driver files they have available :

Realtex LAN files: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168<br>RTL8111C/RTL8111CP/RTL8111D(L)<br>RTL8168C/RTL8111DP/RTL8111E<br>RTL8168E]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168<br>RTL8111C/RTL8111CP/RTL8111D(L)<br>RTL8168C/RTL8111DP/RTL8111E<br>RTL8168E")

Realtex audio codecs: [http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

ATI graphics driver: [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

I have all the files on a USB stick, and i have it plugged into my computer. Now, my question is, how do i install them????

---

### Post by Paqman on 2011-04-03
You probably don't need to install any drivers for the mobo, Gigabyte mobos tend to "just work" with Linux these days. If everything is working (eg: sound, networking, etc) then you're good to go.

Your graphics card is an AMD one, which isn't very well supported. You can try the driver for it at System > Admin > Additional drivers, but I believe a lot of AMD people just use the default open source driver. I've not used an ATI/AMD card for years though, so i'm no expert.

---

### Post by ilikepaste on 2011-04-03
the LAN isn't connecting... haven't tried the sound yet. (The MOBO has integrated LAN on it)

eth0 doesn't get a signal (BIOS reads +100 MBPS)

---

### Post by wolfen69 on 2011-04-03
Here's your linux baptism. :0

Download the Ralink LAN linux driver from the link you posted. Put it in your home folder. (in the general area)

Then open a terminal and copy and paste:
```
tar vjxf r8168-8.022.00.tar.bz2
```
then
```
cd r8168-8.022.00
```
then
```
sudo ./autorun.sh
```

You can check whether the driver is loaded by using following commands.
```
lsmod | grep r8168
```or
```
ifconfig -a
```


If there is a device name, eth0, shown on the monitor, the linux 
	driver is loaded. Then, you can use the following command to activate the eth0. Do:
```
ifconfig eth0 up
```

Let us know if you need further assistance. It's not hard, just take your time.

---

### Post by ilikepaste on 2011-04-03
So I'm going to make myself sound even dumber... which files should I download? There are 5:

-LINUX driver for kernel 2.6.x and 2.4.x (Support x86 and x64)

-FreeBSD 7.x and 8.0

-SCO OpenServer 6 and UnixWare 7.1.x

-SCO Unix 5.0.6 and 5.0.7

-Linux driver for kernel 2.4.x (Support x86 and x64)

---

### Post by Paqman on 2011-04-03
> **ilikepaste said:**
> 
-LINUX driver for kernel 2.6.x and 2.4.x (Support x86 and x64)


This one.

---

### Post by wolfen69 on 2011-04-03
I just figured getting you online should be the first priority. Then we can work on the rest. Once online, it's easier to get the rest of what you need.

---

### Post by ilikepaste on 2011-04-03
So i copied the folder onto the home folder, tried typing in:


[PHP]tar vjxf r8168-8.022.00.tar.bz2
[/PHP]

and got this error:

tar: Old option 'f' requires an argument.
Try 'tar --help' or 'tar --usage' for more information.

What did I do wrong?

---

### Post by realzippy on 2011-04-03
*What did I do wrong?*

Nothing.
try

```
tar -vjxf r8168-8.022.00.tar.bz2
```

---

### Post by JKyleOKC on 2011-04-03
> **ilikepaste said:**
> So i copied the folder onto the home folder, tried typing in:


[PHP]tar vjxf r8168-8.022.00.tar.bz2
[/PHP]

and got this error:

tar: Old option 'f' requires an argument.
Try 'tar --help' or 'tar --usage' for more information.

What did I do wrong?You didn't. The current version of tar apparently requires an option indicator (a dash before the option letters). Try ```
tar [COLOR="Red"]-vjxf[/COLOR] r8168-8.022.00.tar.bz2
```instead and it should work...

---

### Post by ilikepaste on 2011-04-03
typing -vgfx worked... but now im getting the message :

tar: You must specify one of the' '-Acdtrux' or 'test-label' options.

Any ideas?

---

### Post by Paqman on 2011-04-03
You can skip untaring that file on the command line if you want. Just right click on it and "extract here" then move on to the next command.

---

### Post by JKyleOKC on 2011-04-03
The "f" option letter has to be the last one so that it can find the filename which follows the space. Since you typed it with the "x" last, the program could not see the "x" option -- which is the one that tells it to eXtract the content.

Using the right-click is much simpler, though.

---

### Post by ilikepaste on 2011-04-03
Alrighty, never mind... got the internet (i used -jxf to unpack).

Now, how do i auto update my drivers?

---

### Post by realzippy on 2011-04-03
..you mean how to update this particular-just-installed driver in case of a kernel-update (which will happen when you make a system-update)?

Run the auto.sh file again.

..or do you want to update your system?(which you should do after a vanilla install before modifying system/installing software)?

```
sudo apt-get update
```
reads available updates


```
sudo apt-get upgrade
```
installs updates.
Reboot if kernel-update to boot newer kernel.

**EDIT**:

... before installing the ATI graphics driver *manually*,prefer installing the driver via system=>admin=>hardwaredrivers.

---

### Post by Mark Phelps on 2011-04-04
> **vivek027 said:**
> Hi , want 2 make a sarver for a news channel in india ... How its a possibal  ,, its a gudf optation

Your question has absolutely nothing to do with this thread.  You need to start your own thread.

---

