---
title: "Installation problum of HUAWEI ETS2288 (Fixed Wireless) Modem  in Ubuntu 8.10"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by smartboy08 on 2008-11-26
Sir,
        I am a new user of Ubuntu. 8.10 ... but i have an internet connection(of BSNL-INDIA),  I am not able to configure my modem ( on  my new ubuntu 8.10), If you can please help me to do that..
 
My Phone is a CDMA Wireless Phone of .....
 
If you can please help me as early as possible....


[http://ubuntuforums.org/images/smilies/smiley-faces-75.gif](http://ubuntuforums.org/images/smilies/smiley-faces-75.gif)


thanks in advance............

---

### Post by virginbala on 2009-06-05
hi i'm from india, i've following error like this can any one help me plz

```
[  963.525150] usb 2-1: configuration #1 chosen from 1 choice

[  963.529128] ti_usb_3410_5052 2-1:1.0: TI USB 3410 1 port adapter converter detected

[  963.529137] usb 2-1: firmware: requesting ti_usb-v0451-p3410.fw

[ 1023.528082] usb 2-1: firmware: requesting ti_3410.fw

[ 1083.528094] usb 2-1: ti_download_firmware - firmware not found

[ 1083.528111] ti_usb_3410_5052: probe of 2-1:1.0 failed with error -5

root@bala-desktop:~# 

```
but i've followed creating rules file... help me asap:(

---

### Post by GeorgeVita on 2009-06-05
Hi **virginbala**,
please take a look at: [http://ubuntuforums.org/showthread.php?t=1119600](http://ubuntuforums.org/showthread.php?t=1119600)

It seems to be a similar situation.
Regards,
George

References are:
[http://ubuntuforums.org/showpost.php?p=6177543&postcount=2](http://ubuntuforums.org/showpost.php?p=6177543&postcount=2)
[https://answers.launchpad.net/ubuntu/+question/51120](https://answers.launchpad.net/ubuntu/+question/51120)
[http://www.ubuntu.or.tz/index.php/technical-assistance/howtos/3-huawei-fixed-wireless-terminal-ets2288-modem-with-ubuntu-804](http://www.ubuntu.or.tz/index.php/technical-assistance/howtos/3-huawei-fixed-wireless-terminal-ets2288-modem-with-ubuntu-804)

---

### Post by virginbala on 2009-06-05
[B]]usb 2-1: USB disconnect, address 2

[   94.220027] usb 2-1: new full speed USB device using uhci_hcd and address 3

[   94.413512] usb 2-1: configuration #1 chosen from 1 choice

[   94.461885] USB Serial support registered for TI USB 3410 1 port adapter

[   94.461914] USB Serial support registered for TI USB 5052 2 port adapter

[   94.461942] ti_usb_3410_5052 2-1:1.0: TI USB 3410 1 port adapter converter detected

[   94.461950] usb 2-1: firmware: requesting ti_usb-v0451-p3410.fw

[   94.472477] usb 2-1: firmware: requesting ti_3410.fw

[   95.064024] usb 2-1: reset full speed USB device using uhci_hcd and address 3

[   95.206258] usb 2-1: device firmware changed

[   95.206283] ti_usb_3410_5052: probe of 2-1:1.0 failed with error -5

[   95.206312] usbcore: registered new interface driver ti_usb_3410_5052

[   95.206317] ti_usb_3410_5052: v0.9:TI USB 3410/5052 Serial Driver

[   95.213492] usb 2-1: USB disconnect, address 3

[   95.324034] usb 2-1: new full speed USB device using uhci_hcd and address 4

[   95.546423] usb 2-1: configuration #1 chosen from 2 choices

[   95.553644] ti_usb_3410_5052 2-1:1.0: TI USB 3410 1 port adapter converter detected

[   95.553664] ti_usb_3410_5052: probe of 2-1:1.0 failed with error -5

[   95.557398] ti_usb_3410_5052 2-1:2.0: TI USB 3410 1 port adapter converter detected

[   95.557480] usb 2-1: TI USB 3410 1 port adapter converter now attached to ttyUSB0

[ 1080.208046] usb 2-1: USB disconnect, address 4

[ 1080.208859] ti_usb_3410_5052_1 ttyUSB0: TI USB 3410 1 port adapter converter now disconnected from ttyUSB0

[ 1080.208900] ti_usb_3410_5052 2-1:2.0: device disconnected
[ 1083.612028] usb 3-2: new full speed USB device using uhci_hcd and address 2
[ 1083.805225] usb 3-2: configuration #1 chosen from 1 choice
[ 1083.809669] ti_usb_3410_5052 3-2:1.0: TI USB 3410 1 port adapter converter detected
[ 1083.809678] usb 3-2: firmware: requesting ti_usb-v0451-p3410.fw
[ 1083.814125] usb 3-2: firmware: requesting ti_3410.fw
[ 1084.396024] usb 3-2: reset full speed USB device using uhci_hcd and address 2
[ 1084.538253] usb 3-2: device firmware changed
[ 1084.538282] ti_usb_3410_5052: probe of 3-2:1.0 failed with error -5
[ 1084.538453] usb 3-2: USB disconnect, address 2
[ 1084.652041] usb 3-2: new full speed USB device using uhci_hcd and address 3
[ 1084.875420] usb 3-2: configuration #1 chosen from 2 choices
[ 1084.881519] ti_usb_3410_5052 3-2:1.0: TI USB 3410 1 port adapter converter detected
[ 1084.881538] ti_usb_3410_5052: probe of 3-2:1.0 failed with error -5
[ 1084.885832] ti_usb_3410_5052 3-2:2.0: TI USB 3410 1 port adapter converter detected
[ 1084.885926] usb 3-2: TI USB 3410 1 port adapter converter now attached to ttyUSB0[/B]

bala@bala-desktop:~$ 
**plz** help me i've ubuntu 9.04.... i did everything ti_usb_3410rules still having problem help me asap:(

---

### Post by virginbala on 2009-06-05
i had typed this line in terminal
lsusb
ls /dev/ttyU* /dev/ttyS* /dev/ttyA*
 it shown on
[B]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 002 Device 004: ID 0451:3410 Texas Instruments, Inc. TUSB3410 Microcontroller

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root 
hub
root@bala-desktop:~# 

[/B]:(

---

### Post by GeorgeVita on 2009-06-05
Hi again, so you fixed the "***[ 1083.528094] usb 2-1: ti_download_firmware - firmware not found***" but the modem still faces some problems. As 9.04 is newer possibly something is different. Continue searching, I will try also...

The commands you mentioned are 3 different commands:
[B]dmesg
lsusb
ls /dev/ttyU* /dev/ttyA* /dev/ttyH*
[/B]
(each line is a different command, press <enter> after typing it)

You missed the: **ls /dev/ttyU* /dev/ttyS* /dev/ttyA***

Regards,
George

---

### Post by virginbala on 2009-06-05
wht that command can do? i did that commands also.........
[B]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 002 Device 004: ID 0451:3410 Texas Instruments, Inc. TUSB3410 Microcontroller

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root 
hub
root@bala-desktop:~# [/B] if u don mind can u come n chat me over gtalk? add me [COLOR="Red"]virginbala@gmail.com:([/COLOR]

---

### Post by GeorgeVita on 2009-06-05
Hi **virginbala**, this is my summary:

I don't have an ETS2288 modem, I am an Ubuntu user as you are (not a developer) and I am trying to give you ideas (not a solution) about your problem.

Your modem worked for user **bmatloob** following some "fixes" in thread:
**[http://ubuntuforums.org/showthread.php?t=1119600](http://ubuntuforums.org/showthread.php?t=1119600)** but with Ubuntu 8.10

At this moment you have fixed the "firmware" download problem resulting to the creation of a communication port (ttyUSB0). Now you need a way use the modem for dial and data connection.

Unfortunately there are many ways to use a modem: Network Manager, wvdial, gnome-ppp, etc. Ubuntu 9.04 has some differences from previous versions that affect some modems and you have to try (or search and find) which is the appropriate for ETS2288.

There is always a possibility a working method with Ubuntu 8.10 (or previous) to be useless on 9.04. If it is more important for you to use the modem _try 8.10_ OR if you need the last Ubuntu version be patient, try and search! Also you can contact user bmatloob and do the tests together.

About the commands used to debug:
The dmesg command will show all system activity after inserting the modem, lsusb will show all USB peripherals attached and their vendor/product IDs and ls /dev/ttyU* will list any configured serial communication ports.
> lsusb
ls /dev/ttyU* /dev/ttyS* /dev/ttyA*
Above are two (2) commands. The **lsusb** (and press ENTER) and the **ls /dev/...** (press ENTER)

>>> NOW the only test to do is: remove the modem from USB port. Boot ubuntu 9.04 WITHOUT the modem. Wait for the system to stabilise (all icons and desktop appears).
Right click the Network manager icon (beside speaker icon on top right panel). Edit Connections, Mobile Broadband, click on any provider name (if exists) and delete it. Close it.

Attach the modem to the USB port and wait up to 1 minute for a wizard to start (we hope!). If it starts follow instructions to setup the connection. After finishing click on Network Manager icon and then to the providers name.

If not appeared (the wizard) try to setup it manually (right click on Network Manager icon, Edit Connections, Add,..., Close).
Click on Network Manager to see if the Mobile Broadband connection exists.

Good Luck!
George

---

### Post by virginbala on 2009-06-06
hi everyone, 
this is ma latest error **on ubuntu 9.04** any help?

[B][    8.217877] USB Serial support registered for TI USB 3410 1 port adapter

[    8.217914] USB Serial support registered for TI USB 5052 2 port adapter

[    8.217955] ti_usb_3410_5052 2-1:1.0: TI USB 3410 1 port adapter converter detected

[    8.217967] ti_usb_3410_5052: probe of 2-1:1.0 failed with error -5

[    8.217981] usbcore: registered new interface driver ti_usb_3410_5052

[    8.217984] ti_usb_3410_5052: v0.9:TI USB 3410/5052 Serial Driver

[    8.221618] ti_usb_3410_5052 2-1:2.0: TI USB 3410 1 port adapter converter detected

[    8.221725] usb 2-1: TI USB 3410 1 port adapter converter now attached to ttyUSB0

[/B]

---

### Post by GeorgeVita on 2009-06-06
Hi again, from terminal window try:```
ls /dev/ttyU*
```

If you see **/dev/ttyUSB0** then try to setup Network Manager:

- Right click the Network manager icon (beside speaker icon on top right panel). Edit Connections, Mobile Broadband, Add, choose country and Provider, leave all defaults, Close.

- Click on Network Manager to see if the Mobile Broadband connection exists.

G

---

### Post by virginbala on 2009-06-06
i tryed it's shown ttyusbo only.... how to i fix this one?

---

### Post by GeorgeVita on 2009-06-06
With 9.04 this is more complicate. I will try to explain:

**[COLOR="Magenta"]You have a communication port created: /dev/ttyUSB0[/COLOR]**

I assume that you try setup a Network Manager Mobile Broadband connection and this NOT worked.

So we need to try another method. Open a terminal and try:

```
sudo wvdialconf
```
```
sudo pppconfig
```

Post here the results to see if one of these programs exist in your system.

cannot use it (we do not know why)

---

### Post by virginbala on 2009-06-06
i did following wvdial.conf.. still problem bro

---

### Post by GeorgeVita on 2009-06-06
**[COLOR="Magenta"]You mean that you run [B]wvdialconf** and did NOT found a modem?
Or the wvdialconf is not installed?
[/COLOR][/B]
Do you have any 8.10 disk?

EDIT: this thread was for 8.10, virginbala opened a new one regarding 9.04:
[http://ubuntuforums.org/showthread.php?t=1179710](http://ubuntuforums.org/showthread.php?t=1179710)

---

### Post by virginbala on 2009-06-06
yeah i've ubuntu 9.04 bro........

---

### Post by virginbala on 2009-06-09
still no more resolved

---

### Post by virginbala on 2009-06-09
**[color="magenta"]i don't have 8.10 disk[/color]**

---

### Post by GeorgeVita on 2009-06-10
Hi **virginbala**, I like this [COLOR="Black"]c[/COLOR][COLOR="Brown"]o[/COLOR][COLOR="Red"]l[/COLOR][COLOR="Orange"]o[/COLOR][COLOR="Wheat"]r[/COLOR][COLOR="Green"]f[/COLOR][COLOR="Blue"]u[/COLOR][COLOR="Magenta"]l[/COLOR] way to communicate!

and I also _like to help you solve your problem_! It is just harder to make it with 9.04. Also, as I do not have the same hardware with you, I need to see more technical info in order to think an idea or search in a better way other posts/forums.

Our summary is:
1. **Ubuntu 9.04** Desktop full install, full updated (kernel **2.6.28-11-generic** #42)
>>> check it from terminal with the command: **uname -a**
2. Modem **Huawei ETS 2288**
3. **lsusb** shows **0451 : 3410 Texas Instruments, Inc. TUSB3410 Microcontroller**
4. You solved **ti_download_firmware - firmware not found**
5. **/dev/ttyUSB0** created
6. You installed **wvdial** and assosiated programs [COLOR="Magenta"](Yes or No?)[/COLOR]

Post the output of **sudo wvdialconf**

Also did you found any other info? Other people manage to work with this on 9.04? I did not found anything.

Regards,
George

---

### Post by virginbala on 2009-06-10
hi bro currently on my ubuntu 9.04 having this problem now.. i answered all ur [COLOR="Magenta"]questions[/COLOR]
[B]bala@bala-desktop:~$ uname -a
Linux bala-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

bala@bala-desktop:~$ lsusb
Bus 
001 Device 002: ID 0930:6545 Toshiba Corp. 
Bus 001 Device 
001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 
001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 
002: ID 0451:3410 Texas Instruments, Inc. TUSB3410 Microcontroller
Bus 004 Device 
001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 
001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 
001: ID 1d6b:0001 Linux Foundation 1.1 root hub

bala@bala-desktop:~$
 


[   68.444164] usb 4-2: firmware: requesting ti_3410.fw

[  128.444160] usb 4-2: ti_download_firmware - firmware not found

[  128.444178] ti_usb_3410_5052: probe of 4-2:1.0 failed with error -5

[  128.444208] usbcore: registered new interface driver ti_usb_3410_5052

[  128.444213] ti_usb_3410_5052: v0.9:TI USB 3410/5052 Serial Driver

[  328.024047] usb 4-2: USB disconnect, address 2

[  331.468024] usb 4-2: new full speed USB device using uhci_hcd and address 3

[  331.717171] usb 4-2: configuration #1 chosen from 1 choice

[  331.727175] ti_usb_3410_5052 4-2:1.0: TI USB 3410 1 port adapter converter detected

[  331.727185] usb 4-2: firmware: requesting ti_usb-v0451-p3410.fw



bala@bala-desktop:~$ wvdialconf

The program 'wvdialconf' is currently not installed.  
You can install it by typing:
sudo apt-get install wvdial
bash: wvdialconf: command not found


bala@bala-desktop:~$ sudo wvdialconf
[sudo] password for bala:
 

sudo: wvdialconf: command not found

bala@bala-desktop:~$ su
Password:
 

root@bala-desktop:/home/bala# wvdialconf
The program 'wvdialconf' is currently not installed.  
You can install it by typing:
apt-get install wvdial
bash: wvdialconf: command not found


[COLOR="Red"]root@bala-desktop:/home/bala#[/COLOR]

[/B]

---

### Post by GeorgeVita on 2009-06-11
Hi again,
> ...**The program 'wvdialconf' is currently not installed**...

If you have any other internet connection for the 9.04 (wifi, ethernet) use **System > Administration > Synaptic Package Manager**, search for Package **wvdial**, right click on its name, "Mark for installation", and "Apply" to get it.

[COLOR="Blue"]To install **wvdial** to a PC with 9.04 and **NO internet**[/COLOR] you must download and install 5 packages (from a pc connected to the internet, any O.S.):

1. [http://packages.ubuntu.com/jaunty/i386/libxplc0.3.13/download](http://packages.ubuntu.com/jaunty/i386/libxplc0.3.13/download)
2. [http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-base/download](http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-base/download)
3. [http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-extras/download](http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-extras/download)
4. [http://packages.ubuntu.com/jaunty/i386/libuniconf4.4/download](http://packages.ubuntu.com/jaunty/i386/libuniconf4.4/download)
5. [http://packages.ubuntu.com/jaunty/i386/wvdial/download](http://packages.ubuntu.com/jaunty/i386/wvdial/download)

[COLOR="Blue"]Note that above are all for an **Intel x86** pc. **_If your PC is 64bit or AMD you must find the appropriate._**[/COLOR]

- Copy all (5) .deb packages to a USB memory stick
- Open a terminal window (9.04 PC) and run: **sudo nautilus**
- From **File System** find directory **/var/cache/apt/archives/**
- Copy into /var/cache/apt/archives/ the 5 .deb packages
- Double click icon of **libxplc0.3.13** .deb package ([COLOR="Blue"]first on above list[/COLOR]) to install it
- Continue with **libwvstreams4.4-base**, **libwvstreams4.4-extras**, **libuniconf4.4** and finally **wvdial**.

Try to find the modem, from terminal: **wvdialconf**
If OK, configure wvdial: **sudo gedit/wvdial.conf**
And try to connect: **sudo wvdial**

Post any error messages to follow up.

Regards,
George

---

### Post by virginbala on 2009-06-11
[color=magenta]not yet configured[/color][color=green] /dev/ttyusb0[/color]:(

---

### Post by GeorgeVita on 2009-06-11
Did you installed wvdial?
What found wvdialconf? Did it managed to communicate with /dev/ttyUSB0?
[COLOR="Green"]Can you post the output of wvdialconf?[/COLOR]
G

---

### Post by virginbala on 2009-06-11
hi bro again,

i followed all ur prcedures..now working but.. i can't browse web page,when i going to configure **gnome ppp** didn't showing [COLOR="Red"]/**dev/ttyusb0**[/COLOR]..it showing only [COLOR="Navy"]**/dev/modem,/dev/ttys0,/dev/ttys1,dev/ttys2,/dev/ttys3**[/COLOR] how to i do bro.. problems mostly done..:)

---

### Post by GeorgeVita on 2009-06-11
Hi,

warning: use always UPPER/lower case: [COLOR="Blue"]/dev/ttyUSB0[/COLOR]=OK  [COLOR="Red"]ttyusb0[/COLOR]=error!

The program is **gnome-ppp** and will config the file **/etc/wvdial.conf**

From terminal: **gnome-ppp**
click **Setup**
click inside **Device** and change it (with the keyboard) to:
[COLOR="Magenta"]/dev/ttyUSB0[/COLOR] (<--- exactly like this)

>>> I have not ever use this program! I used to: **sudo gedit /etc/wvdial.conf**

_Try these settings_:
Device: /dev/ttyUSB0
Type: Analog modem (or USB modem)
Speed: 115200 (for this time leave it to 115200)
Phone line: Tone
Volume: High (leave it as is)
Phone Numbers: *99# (at first line)
Init strings: Init3: AT+CGCONT=1,"IP","internet"  [COLOR="Magenta"](this must be checked!)[/COLOR]
NO TICK to "Wait for Dial tone"

networking: TICK on "dynamic IP address" and "Automatic DNS"
options: TICK ONLY "ignore terminal strings (stupid mode)"

Try it and hope for the best!
George

---

### Post by virginbala on 2009-06-12
Hi bro, my curent connection n [COLOR="Indigo"]baud[/COLOR] [COLOR="DarkRed"]dial no[/COLOR] also vari...
[B][[COLOR="Red"]Dia[/COLOR][COLOR="Orange"]ler hu[/COLOR][COLOR="Cyan"]awei[/COLOR]]
Modem = [COLOR="Purple"]/dev/ttyUSB0[/COLOR]
Baud = [COLOR="Green"]230400[/COLOR]
Phone = [COLOR="DarkOrange"]#777[/COLOR]
Init1 = [COLOR="Lime"]ATZ[/COLOR]
Stupid Mode = [COLOR="Indigo"]1[/COLOR]
Dial Command = [COLOR="Blue"]ATDT[/COLOR]
Username = &#8220;[COLOR="Red"]bala[/COLOR]&#8221;
Password = &#8220;[COLOR="DeepSkyBlue"]9840046472[/COLOR]&#8221;
PPPD Options =[COLOR="Orange"] crtcts multilink usepeerdns lock defaultroute[/B][/COLOR]

---

### Post by virginbala on 2009-06-12
when i configure on [COLOR="Red"]**gnome**[/COLOR] [COLOR="DarkOrange"]**ppp**[/COLOR] 
i've changed abt ur setings but it shown error on **[COLOR="Lime"]connection log[/COLOR]**,
**--> Ignoring malformed input line: ";[COLOR="Red"][B]Do NOT edit this file by hand**[/COLOR]!"
--> WvDial: Internet dialer version 1.60
--> Cannot open [COLOR="MediumTurquoise"]**/dev/ttyusb0**[/COLOR]: No such file or directory
--> Cannot open [COLOR="RoyalBlue"]**/dev/ttyusb0**[/COLOR]: No such file or directory
--> Cannot open [COLOR="Purple"]**/dev/ttyusb0**[/COLOR]: No such file or directory[/B]

reply me **[COLOR="Yellow"]A[/COLOR][COLOR="Lime"]S[/COLOR][COLOR="Cyan"]A[/COLOR][COLOR="DeepSkyBlue"]P[/COLOR]**

---

### Post by GeorgeVita on 2009-06-12
OK, stop colors by now! Just B&W, colors again when you make the connection!

YOU MUST USE: **/dev/ttyUSB0**

below shown /dev/ttyusb0   <--- usb=error

> **virginbala said:**
> ...--> Cannot open /dev/ttyusb0: No such file or directory

Also other parameters YOU are correct! Phone number in your country/provider is #777 (?)

Let's get the connection with the modem and you/I will fix them.

---

### Post by virginbala on 2009-06-12
can't open **/dev/ttyusb0**
tel me nxt step bro:(

---

### Post by GeorgeVita on 2009-06-12
> **virginbala said:**
> can't open **/dev/ttyusb0**
tel me nxt step bro:(

When you write to me **/dev/ttyusb0** I understand that the error is at what you type.

PLEASE tell me did you used **/dev/ttyUSB0**
and NO **/dev/ttyusb0**
into the setup?

EDIT >> Also give me Country and Provider Name to check other parameters.

Network Managers lists:
BSNL India, Dial No: *99# and Init3: AT+CGCONT=1,"IP","celloneportal"
BSNL prepaid (West Bengal): *99# and Init3: AT+CGCONT=1,"IP","www.e.pr"

---

### Post by virginbala on 2009-06-12
this is [COLOR="Red"]**BSNL WLL LANDLINE CONNECTION**[/COLOR], DEVICE [COLOR="Cyan"]**HUAWEI TI ETS 2288**[/COLOR] search this device on google,... aftr that tel me bro........

how to set serial port on /dev/ttyusb0

**gnome-ppp** setup modem can't be shown this port **/dev/ttyusb0**

**understood?**:popcorn:

---

### Post by virginbala on 2009-06-12
how to configure modem on gnome-ppp **/dev/ttyusbo** not shown this port :(:(:(:(:(:(:(

---

### Post by GeorgeVita on 2009-06-12
Look at: [http://www.heman-hemanathan.blogspot.com/](http://www.heman-hemanathan.blogspot.com/)
> BSNL CDMA WLL INTERNET CONNECTION PROCEDURE IN LINUX
> Blogger  Heman said...
    The procedure that i've given is tested in fedora core linux 9 and ubuntu 7.10 linux versions.. you can try in other versions of linux also and tell me what you get i'll solve your problems

> **GeorgeVita said:**
> ...
From terminal: **gnome-ppp**
click **Setup**
[SIZE="3"]click inside **Device** and change it (with the keyboard)[/SIZE] to:
/dev/ttyUSB0 (<--- exactly like this)
...
[IMG]http://acomelectronics.com/GeorgeVita/pppco.jpg[/IMG]
Your mouse over the box. Click INSIDE box. Type with the keyboard to change.
Click on **Detect** to test if 9.04 detects your modem.

---

### Post by virginbala on 2009-06-13
again hi,
i typed over my hand, when i pressing detect **[COLOR="Red"]modem not found[/COLOR]** also my speed is **[COLOR="Blue"]230400[/COLOR]**... tel me another way bro:(

---

### Post by virginbala on 2009-06-14
hi george vita any idea.... :(

---

### Post by virginbala on 2009-06-14
[B]--> Ignoring malformed input line: ";
Do NOT edit this file by hand!"

--> WvDial: Internet dialer version 1.60

--> Initializing modem.

--> Sending: ATZ
ATZ
OK

--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK

--> Modem initialized.

--> Sending: ATM0L0DT#777

--> Waiting for carrier.
ATM0L0DT#777
CONNECT

--> Carrier detected.  Starting PPP immediately.

--> Unable to run /usr/sbin/pppd.

--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.

--> Ignoring malformed input line: ";Do NOT edit this file by hand!"

--> WvDial: Internet dialer version 1.60
--> Initializing modem.

--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK

--> Modem initialized.
--> Sending: ATM0L0DT#777
--> Waiting for carrier.
ATM0L0DT#777
CONNECT

--> Carrier detected.  Starting PPP immediately.
--> Unable to run /usr/sbin/pppd.

--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.

--> Timed out while dialing.  Trying again.
--> Maximum Attempts Exceeded..Aborting!!

--> Disconnecting at Sun Jun 14 20:56:56 2009
[/B] [COLOR="Blue"]WHAT IS THIS ERROR ?[/COLOR]

---

### Post by GeorgeVita on 2009-06-14
Hi,
this is a BETTER output!

1. Please tell me how did you succeed to connect with the modem to fix the new problem.

2. Post here the /etc/wvdial.conf file to check it.

Regards,
George

---

### Post by virginbala on 2009-06-15
hi,
 again i did clean installtion **[COLOR="Green"]ubuntu 9.04[/COLOR]**,and u gave me some files link on earlier,also i downloaded that instslled then configure manually,here below my **[COLOR="Red"]wvdial.conf [/COLOR]**
[Dialer huawei]
Modem = /dev/ttyUSB0
Baud = 230400
Phone = #777
Init1 = ATZ
Stupid Mode = 1
Dial Command = ATDT
Username = bala
Password = 9840046472
PPPD Options = crtcts multilink usepeerdns lock defaultroute


**username&password vary**
i've one small error internet connected over terminal **[COLOR="Purple"]wvdial huawei[/COLOR]**
but gnome-ppp does't **detect modem**
however can u tel me,i can't work internet over terminal connection any idea to work internet, also some bug on **gnome-ppp ** _damn conform_

---

### Post by virginbala on 2009-06-15
I tryed near [color="red"]30[/color] days to connect internet, feel how i interested on **ubuntu 9.04**, [color="deepskyblue"]**i love ubuntu**[/color]

---

### Post by GeorgeVita on 2009-06-15
Hi **virginbala**,

I am Happy because you give now BETTER INFO about the problem!
We can make it work. I do not have the modem, you have it. So you are testing! I can see tests from your posts.

NOT GOOD:
> can't open /dev/ttyusb0

BETTER:
> --> Ignoring malformed input line: ";
Do NOT edit this file by hand!"

--> WvDial: Internet dialer version 1.60

--> Initializing modem.

--> Sending: ATZ
ATZ

The only you have to remove or change is your username and password bacause you DO  NOT want other users to know it! So as you post it now you have to change your real password after tests!

Make your /etc/wvdial.conf

```
[Dialer huawei]
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
ISDN = 0
Baud = 230400
Phone = #777
Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0
Stupid Mode = 1
Dial Command = ATM1X3DT
Username = bala
Password = 9840046472

```

[COLOR="Blue"]Open a terminal window and type: **sudo wvdial huawei**[/COLOR]

This will use wvdial to connect.In any error Copy Paste ALL terminal output (from your command ... to the last line).

**[COLOR="Violet"]In case you are connected, Start FireFox and check if "File > Work Offline" is enabled. Click on it to make it online![/COLOR]**

G

---

### Post by virginbala on 2009-06-15
hi geroge bro,
 that's not my real username & password,.. hmmm n ur **[COLOR="SandyBrown"]wvdial.conf[/COLOR]** files
working over terminal?
may i work internet over terminal via?

---

### Post by virginbala on 2009-06-15
i tryed ur **wvdial.conf ** no more working bro:(

**[COLOR="Red"]GNOME-PPP NOT WORKING [/COLOR]**i've connected internet via terminal, but i can't browse web page how to browse internet through terminal?

---

### Post by virginbala on 2009-07-02
i can't fix this error.................. no more solutions.........:guitar:

---

### Post by virginbala on 2009-07-07
finally **my huawei ets 2288** working properly.. 

but some bug in gnome-ppp
hope u'll resolve in karmic koala version..:popcorn::lolflag::p

thx

---

### Post by virginbala on 2009-07-28
finally working fine...... over gnome-ppp no more errors............ if anyone need help about huawei ets 2288 wll phone modem feel free to ask..

thx

---

### Post by abr on 2009-11-03
Friends, I have faced the same problem - bsnl - Huawei ETS 2288 modem - issue, I observed the following: -

1. With puppy linux 4.30 - I am able to connect 
      I created new rules file 
      edited wvdial.conf and resolv.conf
   connected to internet - success

2. With Ubuntu 9.04 - I did create/change files as i did above
   in addition I installed wvdial program gnome-ppp and copied firmware files (I got all info from various ubuntu forum threads and other forums) - tried to load modules at boot up by editing kernel line in menu.lst(GRUB) file. Tried modprobe/setserial/scanmodem - lot of efforts. Finally I noticed one thing - randomly I got success - it means - wvdial worked randomly most of the time failure - some - very rare - it was success - (almost out of 50 shutdown bootups - I got connected only twice or thrice - I am unable to repeat - success - consistently. (I got all input output error and modem not found/no such device exist - error messages). I am using emachine laptop . Fact is I am using laptop as desktop, by connecting external keboard, mouse, pendrive, in addition to huawei ets 2288 modem-telephone - cdma wll Tarang phone provided by bsnl)

I am Finance and accounts professional not an computer hardware engineer/professional - still I doubt that the random success implies that there are problems in Interrupts,  address port related subject - which is really beyond my power to understand.

3. I installed ubuntu karmic - did changes in rules - wvdial.conf - resolv.conf - command line wvdial works successfully (though not every time) - but the success rate increased - It means - every 5 or 10 attempts - `sudo wvdial bsnl` connected - shown me pid of process, (Now also failure attempts are there). I am unable to connect thru' gnome ppp - the log display shows - ATX3 commands -instead of ATZ commands as displayed by wvdial when tried from command line - (once gnome ppp reported - it found fax machine) 

4. Windows XP connects with out any problem/error message (but it is slow)

5. If I am connected to net thru' linux browsing is relatively faster than windows.

6. These points I report to community - as a feed back

Thank you

---

### Post by vrprawinkumar on 2010-01-15
> **virginbala said:**
> finally working fine...... over gnome-ppp no more errors............ if anyone need help about huawei ets 2288 wll phone modem feel free to ask..
 
thx
 
Hi,
I'm also using ubuntu 9.10..But i'm a new user i want to connect huawei ets 2288 (bsnl wll) in ubuntu 9.10...my email is [EMAIL="vrprawinkumar@gmail.com"]vrprawinkumar@gmail.com[/EMAIL] i have been trying to connect for the last 45 days..Please help me:(

---

### Post by vrprawinkumar on 2010-01-15
> **abr said:**
> Friends, I have faced the same problem - bsnl - Huawei ETS 2288 modem - issue, I observed the following: -
 
1. With puppy linux 4.30 - I am able to connect 
I created new rules file 
edited wvdial.conf and resolv.conf
connected to internet - success
 
2. With Ubuntu 9.04 - I did create/change files as i did above
in addition I installed wvdial program gnome-ppp and copied firmware files (I got all info from various ubuntu forum threads and other forums) - tried to load modules at boot up by editing kernel line in menu.lst(GRUB) file. Tried modprobe/setserial/scanmodem - lot of efforts. Finally I noticed one thing - randomly I got success - it means - wvdial worked randomly most of the time failure - some - very rare - it was success - (almost out of 50 shutdown bootups - I got connected only twice or thrice - I am unable to repeat - success - consistently. (I got all input output error and modem not found/no such device exist - error messages). I am using emachine laptop . Fact is I am using laptop as desktop, by connecting external keboard, mouse, pendrive, in addition to huawei ets 2288 modem-telephone - cdma wll Tarang phone provided by bsnl)
 
I am Finance and accounts professional not an computer hardware engineer/professional - still I doubt that the random success implies that there are problems in Interrupts, address port related subject - which is really beyond my power to understand.
 
3. I installed ubuntu karmic - did changes in rules - wvdial.conf - resolv.conf - command line wvdial works successfully (though not every time) - but the success rate increased - It means - every 5 or 10 attempts - `sudo wvdial bsnl` connected - shown me pid of process, (Now also failure attempts are there). I am unable to connect thru' gnome ppp - the log display shows - ATX3 commands -instead of ATZ commands as displayed by wvdial when tried from command line - (once gnome ppp reported - it found fax machine) 
 
4. Windows XP connects with out any problem/error message (but it is slow)
 
5. If I am connected to net thru' linux browsing is relatively faster than windows.
 
6. These points I report to community - as a feed back
 
Thank you
 
hi,
Will u send the procedure of connecting huawei ets 2288 (BSNL WLL) modem in ubuntu 9.10 to my email [EMAIL="spam.magnet"]<snip>[/EMAIL] .Please help me i'm in trouble

---

### Post by pdc on 2010-01-15
well, have you seen this?

[http://www.heman-hemanathan.blogspot.com/](http://www.heman-hemanathan.blogspot.com/)

find this section

> SATURDAY, AUGUST 16, 2008
BSNL CDMA WLL INTERNET CONNECTION PROCEDURE IN LINUX

that was posted about 18 months ago; 

you need to work through it step by step;

( or b), tell us some of the things you have done over the last 45 days)

---

