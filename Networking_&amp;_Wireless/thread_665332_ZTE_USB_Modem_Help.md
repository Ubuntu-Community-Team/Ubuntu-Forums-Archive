---
title: "ZTE USB Modem Help"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by viking777 on 2008-01-12
I decided that I wanted to try out 3 Mobile for mobile internet instead of  the Vodafone connection I am using at present as they appear to have better coverage where I live. The modem they supplied my is a ZTE MF622. I thought that I would be able to make it work in the same manner as the Huawei modem I have used up till now, but it doesn't seem to be so easy, the problem is this.

If I plug in the device and perform a cold boot, the device is listed as ID 19d2:0001. If I modprobe this it creates the necessary device nodes and behaves as a proper modem should (at least for a while). However if I perform anything other than a cold boot the device is listed as ID 19d2:2000 and no amount of modprobing that will make any difference, it never creates the necessary device nodes. The problem is further complicted by the fact that if the modem fails to connect for any reason and I have to unplug it the ID changes back to 19d2:2000 and the whole thing becomes useless. 

Does anyone know how I can deal with this?

3 mobile give you 3 days to return the modem if you are not satisfied with it which gives me until Monday to get it working or take it back for a refund, so I don't have long to sort this out.

Needless to say the whole thing works perfectly in my wife's windows computer so the modem is not faulty and the connection it gives from her machine appears to be very good, so I would like to get it going if I could, but having to do cold boots every time I mess around with it is not exactly convenient.

Incidentally, the modem comes with a driver cd for a mac. Is there any way I could get that to run on Kubuntu? (I think I can guess the answer!).

---

### Post by Llywelyn on 2008-02-03
I can't find anything to confirm whether this ZTE modem works with linux, at least in an easy to do way.

However, don't despair. Three can supply a Huwee E220 USB dongle and this definitely works with Linux and works easily thanks to Vodafone's generous contribution of OSS to the community.

Follow:
[http://mybroadband.co.za/vb/showthread.php?t=74067]("http://mybroadband.co.za/vb/showthread.php?t=74067") for the driver and GUI.
Follow:
[https://forge.vodafonebetavine.net/forum/forum.php?thread_id=208&forum_id=20]("https://forge.vodafonebetavine.net/forum/forum.php?thread_id=208&forum_id=20")
for information on settings to use with Three's network.

I've tried the setup and it works.

Hope this helps

Llywelyn Owen

---

### Post by JimmyI on 2008-02-13
Hi,

I've managed to botch a method to get my ZTE MF622 working within ubuntu. Its on the UK 3G network. Only problem is you loose USB based storage device functionality  I still havn't found a way to get them working along with the modem!  If your still wanting to give it a go let me know and I'll dig up my txt files.

---

### Post by JimmyI on 2008-02-13
Okay scrap the problems, Here is how to do if for people out there (none of this is my doing really, I've just played around with the information out there)

First you need to set up the ZTE MF622 as a modem rather than a usb drive. This is done by inserting the following script.

ACTION!="add", GOTO="ZTE_End"

# Is this the ZeroCD device?
SUBSYSTEM=="usb", SYSFS{idProduct}=="2000",
SYSFS{idVendor}=="19d2", GOTO="ZTE_ZeroCD"

# Is this the actual modem?
SUBSYSTEM=="usb", SYSFS{idProduct}=="0001",
SYSFS{idVendor}=="19d2", GOTO="ZTE_Modem"

LABEL="ZTE_ZeroCD"
# This is the ZeroCD part of the card, remove
# the usb_storage kernel module so
# it does not get treated like a storage device
RUN+="/usr/src/usb_modeswitch-0.9.2/usb_modeswitch -d 1 -v 0x19d2 -p 0x2000 -V 0x19d2 -P 0x0001" 

LABEL="ZTE_Modem"
# This is the Modem part of the card, let's
# load usbserial with the correct vendor
# and product ID's so we get our usb serial devices
RUN+="/sbin/modprobe usbserial vendor=0x19d2 product=0x0001",
# Make users belonging to the dialout group
# able to use the usb serial devices.
MODE="660", GROUP="dialout"

LABEL="ZTE_End"



Make this in gedit and save it in etc/udev/rules.d and make sure the file name ends in .rules e.g. sudo gedit /etc/udev/rules.d/ZTEMF622.rules


Now you need to set up the dialing mechanism. This is done using wvdial, what you need to do is create the following wvdial.conf file if you are using the ZTE in England with Three

[Dialer Defaults]

Init2 = ATZ

Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

Stupid Mode = 1

Modem Type = Analog Modem

ISDN = 0

Phone = *99#

Modem = /dev/ttyUSB0

Username = user

Dial Command = ATDT

Password = pass

Baud = 460800

That file is saved in etc/wvdial.conf. So you put in the terminal sudo gedit /etc/wvdial.conf then paste the dialer defaults code into that and save.

Then reboot with the modem plugged in form the begging of the reboot. Activate the modem by typing sudo wvdial in the terminal. If all is well you should be on the internet. Note: if the modem light is red then it's not going to work you need to unplug it plug it back in. It should then go green. You will need to reboot in order to get it working again.

Hope that helps

Jim

---

### Post by ercork on 2008-04-13
Hi - I've been trying to get my zte mf622 working all weekend. No success yet. I've copied the instructions exactly but everytime I reboot the 3 modem icon is there on the dektop and the USB drive is mounted. If When I try "sudo wvdial" I get:



satellite@satellite-laptop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
satellite@satellite-laptop:~$ 

Any suggestions?

---

### Post by ercork on 2008-04-16
Problem solved - a reboot didn't work for me. I had to shut down and then bootup again (don't know how this would make a difference).

For anybody in Ireland add in the line 

Init5 = AT+CGDCONT=1,"IP","3ireland.ie"

after init3 in the instructions above - otherwise everything is the same.

---

### Post by steve_pearce on 2008-04-23
Thanks for this thread and JimmyI in particular. My minutes old ZTE-MF622  is now connected and running well under Debian on an Eee.

Using the same process above but with the small addition of adding the wvdial package.

Sadly the coverage where I am is 'so so'. Its good to know it is usable though for when I am on the move again.

Thanks again :)

---

### Post by Marcellus on 2008-04-24
> **ercork said:**
> When I try "sudo wvdial" I get:

satellite@satellite-laptop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
satellite@satellite-laptop:~$ 

Any suggestions?
which was followed by the note that a cold reboot did the trick.

However, no amount of restarting and (un)plugging devices works for me, and I get exactly the same message (only it says version 1.56 because... well, I don't have internet so I cannot update my system decently).  It seems that I'm stuck by my ignorance.  

So: any suggestions where I go wrong?  It's a standard 7.10 gutsy, updated until Xmas 2007.  A complication seemed to be that I put the USB modem in a hub, not directly into the PC, so it kept power during shutdown.  However, directly pluggin it in the pc's usb ports didn't make a difference.  

All the best & thanks in advance,
M.

---

### Post by N0_Named_Guy on 2008-05-01
Hello there...

I am trying to put my MF622 working, but I think gnome doesn't let use the ppp0 interface to access the internet :S

I've done the dial scripts for my area and ISP. In terminal, I run the usbmodeswitch, then gcom and finally wvdial...

In the terminal, after running these commands, it appears that I've been connected to the internet. It says my IP and other stuff...


I run the network tools app, and there it is the ppp0 with all its information... But when I get to firefox, it simply doesn't work... :(

What can I do??

Best Regards,
David Serrano

---

### Post by collegecotbuc on 2008-05-04
Hi Jimmy,
I got my machine dialling out perfectly Linux worked a treat ,I turned the machine off removed the modem ZTEMF ,restarted the machine ,used wvdial in the terminAL got the message can't find ttyUSB0 ,any ideas please



> **JimmyI said:**
> Okay scrap the problems, Here is how to do if for people out there (none of this is my doing really, I've just played around with the information out there)

First you need to set up the ZTE MF622 as a modem rather than a usb drive. This is done by inserting the following script.

ACTION!="add", GOTO="ZTE_End"

# Is this the ZeroCD device?
SUBSYSTEM=="usb", SYSFS{idProduct}=="2000",
SYSFS{idVendor}=="19d2", GOTO="ZTE_ZeroCD"

# Is this the actual modem?
SUBSYSTEM=="usb", SYSFS{idProduct}=="0001",
SYSFS{idVendor}=="19d2", GOTO="ZTE_Modem"

LABEL="ZTE_ZeroCD"
# This is the ZeroCD part of the card, remove
# the usb_storage kernel module so
# it does not get treated like a storage device
RUN+="/usr/src/usb_modeswitch-0.9.2/usb_modeswitch -d 1 -v 0x19d2 -p 0x2000 -V 0x19d2 -P 0x0001" 

LABEL="ZTE_Modem"
# This is the Modem part of the card, let's
# load usbserial with the correct vendor
# and product ID's so we get our usb serial devices
RUN+="/sbin/modprobe usbserial vendor=0x19d2 product=0x0001",
# Make users belonging to the dialout group
# able to use the usb serial devices.
MODE="660", GROUP="dialout"

LABEL="ZTE_End"



Make this in gedit and save it in etc/udev/rules.d and make sure the file name ends in .rules e.g. sudo gedit /etc/udev/rules.d/ZTEMF622.rules


Now you need to set up the dialing mechanism. This is done using wvdial, what you need to do is create the following wvdial.conf file if you are using the ZTE in England with Three

[Dialer Defaults]

Init2 = ATZ

Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

Stupid Mode = 1

Modem Type = Analog Modem

ISDN = 0

Phone = *99#

Modem = /dev/ttyUSB0

Username = user

Dial Command = ATDT

Password = pass

Baud = 460800

That file is saved in etc/wvdial.conf. So you put in the terminal sudo gedit /etc/wvdial.conf then paste the dialer defaults code into that and save.

Then reboot with the modem plugged in form the begging of the reboot. Activate the modem by typing sudo wvdial in the terminal. If all is well you should be on the internet. Note: if the modem light is red then it's not going to work you need to unplug it plug it back in. It should then go green. You will need to reboot in order to get it working again.

Hope that helps

Jim

---

### Post by JimmyI on 2008-05-12
Hi,

Well I'm sorry to hear that people have had problems. Sadly I'm a complete newb too! I just persisted just long enough to get mine working (took me 3 weeks!!!)

Quick question has anyone experienced any problems with upgrading to Hardy? I upgraded yesterday and couldn't get online with the modem.... could be a big problem!

collegecotbuc, the message can't find ttyUSB0 sounds to me as if the modem hasn't been loaded properly. This could be because the .rules file is wrong and the modem is mounting as a drive or it could be that your wvdial.conf isn't being directed to the modem. My understanding is that ttyUSB0 is sort of the code name given to the modem portion of the ZTE.

Has anyone any other thoughts?

Jim

---

### Post by JimmyI on 2008-05-25
Just wanted to say that the modem works fine in Hardy. The error I was seeing is from a bug in Firefox, whereby it always loads in offline mode. All you need to do to solve it(ish) is uncheck the offline mode in file. As far as I'm aware there is no full fix for this yet.

---

### Post by al_skidoo on 2008-05-29
I'm getting it to look like it's working too, everything seems ok, I get an IP address and all of that good stuff but then nothing, no way of getting my firefox to actually use the modem, very frustrating as I can tell it's really close!

Anybody?

AL


> **N0_Named_Guy said:**
> Hello there...

I am trying to put my MF622 working, but I think gnome doesn't let use the ppp0 interface to access the internet :S

I've done the dial scripts for my area and ISP. In terminal, I run the usbmodeswitch, then gcom and finally wvdial...

In the terminal, after running these commands, it appears that I've been connected to the internet. It says my IP and other stuff...


I run the network tools app, and there it is the ppp0 with all its information... But when I get to firefox, it simply doesn't work... :(

What can I do??

David Serrano

---

### Post by daveball on 2008-07-04
Very helpful post by JimmyI - Thanks for that. It's just what I needed to get my ThinkPad / Xubuntu 7.10 working with a ZTE MF622 on Three UK.

**BUT an important thing to note** if you're using the udev script is that it depends on you having installed (and in the correct location) a very useful utility called usb_modeswitch - its this useful tool, called by the udev script, that unmounts the mass storage device part of the MF622 and triggers it to connect as a serial modem instead.

For instructions on how to compile and install usb_modeswitch go here (its very simple):

[http://www.draisberghof.de/usb_modeswitch/]("http://www.draisberghof.de/usb_modeswitch/")

Once compiled I installed usb_modeswitch to /usr/local/sbin/ (personal preference) and modified the line in the udev script that calls it to use this location.

Before I did this I needed to cold boot with the modem already connected to have any joy. After getting usb_modeswitch installed things worked better than I had ever managed with 3G modems before (I had a run in with a huawei 220 earlier this year).

I can attach the modem with the PC already on and then connect to Three using wvdial using JimmyI's settings. 

Looking closely at what is now happening when I connect the MF622, it is initially picked up as a USB mass storage device (do lsusb -v and look for the device where idVendor=ox19d2 and idProduct=0x2000). At this point on my ancient laptop there's a delay of about 20 seconds, after which the modem disconnects, and then reconnects as a serialmodem (this is what usb_modeswitch and the udev script are doing for you). You know when this has happened because lsusb -v now reports the device as idVendor=ox19d2 and idProduct=0x0001. Once this has happened, wvdial finds the modem and off I go.

The 20 second delay is important - if I start wvdial before the usb switch has completed I get the "Cannot open /dev/ttyUSB0" error familiar to us all.

Hope this helps a few people.

---

### Post by michalpelszyk on 2008-07-09
Hi people, I just logged in to share how I managed to make this damn thing work. It's not the best solution out there (yet), but I have to share it before I lose momentum and interest.

My modem is ZTE MF622 HSDPA Mobile Modem from THREE Mobile UK network. I have Debian Linux. Should work with Ubuntu and other derivatives without too much trouble.

I followed the instructions posted by zaurus6k on eeepc forum: [http://forum.eeeuser.com/viewtopic.php?pid=100536#p100536](http://forum.eeeuser.com/viewtopic.php?pid=100536#p100536)

> **zaurus6k]It is quite easy. No need to replace the kernel image. Just need to rebuild a single kernel module named usbserial with an option. I think Asus should have done that with the default installation. 

Here is the step-by-step for what I did to make u727 working:

0) open a terminal window. Either connect to internet via wire lan or copy files from anther computer using a USB sticker. 
1) Follow wiki at [http://wiki.eeeuser.com/howto:rebuildthekernel](http://wiki.eeeuser.com/howto:rebuildthekernel) "Rebuilding the kernel on eeePC" part. 
   
    You can also try to download ASUS official release of linux on eee pc at  
    [http://dlsvr03.asus.com/pub/ASUS/EeePC/701/Linux_Kernel_071127.rar](http://dlsvr03.asus.com/pub/ASUS/EeePC/701/Linux_Kernel_071127.rar)

2) make usbserial kernel module with following cmd at the root where the linux kernel source code is located:
      make CONFIG_USB_SERIAL_GENERIC=y M=drivers/usb/serial
   
3) 
cd /lib/modules/2.6.21.4-eeepc/kernel/drivers/usb/serial
sudo mv usbserial.ko usbserial.ko.keep ( keep the old one)
sudo cp <to linux source>/drivers/usb/serial/usbserial.ko .

4) 
sudo modprobe &#8211 said:**
> http://samat.org/weblog/20070128-sprints-evdo-mobile-broadband-on-ubuntu-linux.html[/url]

   Then you are connected to internet.


Following link talks about using airprime instead of usbserial to get higher speed. I'll try it later.

[http://samat.org/weblog/20070127-high-speed-cellular-wireless-modems-in-ubuntu-linux-6-10.html](http://samat.org/weblog/20070127-high-speed-cellular-wireless-modems-in-ubuntu-linux-6-10.html)
So: check for usbserial module in your kernel (/boot/config-yourkernel or by zgrep /boot/initrd-yourkernel), go to step 4) if you have it

The difference is, in step 4) you give different parameters:

4) 
sudo modprobe &#8211;r usbserial
sudo eject /dev/sda ( the cd with "Default OS" drivers, I prefer to unmount it first )
sudo modprobe usbserial **vendor=0x19d2 product=0x0001**  (this is the infamous MF622 modem )
sudo dmesg|grep &#8211;i ttyUSB (not necessary but makes sure the driver loaded correctly, you should see ttyUSB0 for example)
NOTE: as in "Default OS", when you run a control program, you need to wait about 30-60 seconds after ejecting CD before modem becomes available.
NOTE2: modprobe -r usbserial and modprobe usbserial vendor=0x19d2 product=0x0001 are possibly unnecessary. This should achieved by adding correct kernel parameter or compiling usbserial as a module and adding line "usbserial vendor=0x19d2 product=0x0001" to /etc/modules. Please, correct me if I am wrong.

Then you go setting up your favorite dialling program. I use wvdial. This again is something found on the internet ( [http://ubuntuforums.org/archive/index.php/t-665332.html](http://ubuntuforums.org/archive/index.php/t-665332.html)  )
Contents of /etc/wvdial.conf, change owner to root and read access to anyone

[Dialer Defaults]
Phone = *99#
Username = user
Password = pass
Stupid Mode = 1
Dial Command = ATDT

Modem = /dev/ttyUSB0
Baud = 460800
ISDN = 0
Modem Type = Analog Modem
Init2 = ATZ
Init3 = ATE0 V1 &D2 &C1 S0=0 +IFC=2,2

Now, invoke wvdial and you have internet connection, that's utterly unusable.

Disconnect. For some strange reason the THREE assigns 4.2.2.4/3 as DNS. They DON'T work. "Default OS" shows WINS servers being used, this may be the hint to correct name resolution, but I have no idea about that.

I'm using OpenDNS for now, but they are slooooow. I'll try to find something faster later. This solution comes from [http://gentoo-wiki.com/HARDWARE_HUAWEI_E220_HSDPA_USB_MODEM#DNS_problem](http://gentoo-wiki.com/HARDWARE_HUAWEI_E220_HSDPA_USB_MODEM#DNS_problem)

Edit /etc/resolv.conf, put those lines close to the top.
#Open DNS server
nameserver 208.67.222.222
nameserver 208.67.220.220

This propably won't work permanently (as resolv.conf is modified each time a new connection is established), but I don't know where Debian hides his counterparts of gentoo's /etc/conf.d/net and /usr/ppp/peers/. Yet.

Now, I didn't go as far as making an udev script to automate this procedure. Everything is done manually.
Maybe one day I will go further with this, but now I have another things to work out. Hey! I went through patching and adding custom DSDT to my initrd! Forget kernel recompilation.

I hope this helps some people out there.

---

