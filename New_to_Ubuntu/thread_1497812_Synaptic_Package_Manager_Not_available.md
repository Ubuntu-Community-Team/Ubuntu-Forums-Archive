---
title: "Synaptic Package Manager Not available"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by ashwani.nair on 2010-05-31
Hi ! I am new to Ubuntu and Linux world.

I have recently downloaded Wubi 10.04 and Installed dual boot in my XP Laptop. (I had to download the Ubuntu ISO separately as the download failed with Wubi). Its all working fine but I couldn't find the Synaptic Package Manager. 

I am looking for Synaptic Package Manager as I wish to Install by USB BB Service. I am currently using TATA Photon (Huawei) USB Modem. 

Not sure If I can download it with XP boot and then burn and CD and try to install it in Ubuntu Boot. Kindly suggest.

I have also tried 'sudo apt-get install wvdial' but dint work. 


thanks a lot in advance.

---

### Post by Paddy Landau on 2010-05-31
You should find Synaptic under System > Administration > Synaptic Package Manager.

Or, try the Ubuntu Software Centre instead of Synaptic.

BTW, if you plan on using Ubuntu long-term, then I don't recommend Wubi. Wubi is great for playing and experimenting, but is too easily corrupted for serious use.

---

### Post by ashwani.nair on 2010-05-31
Thanks a lot Paddy.

I am an absolute beginner so I will hang on with Wubi for at least a couple of weeks. Hope its OK.

I discovered that I have Synaptic by typing it in the terminal. But, it requires admin privilege it seems. I am planning to use 'sudo synaptic'. 

But, eve after launch, I couldnt find 'usbmodeswitch' and 'usbmodeswitch-data'

also, Not sure, how to login as admin. Is it possible. 

PS: Once confortable, i will install ubuntu and discard wubi.

---

### Post by Paddy Landau on 2010-05-31
> **ashwani.nair said:**
> I am an absolute beginner so I will hang on with Wubi for at least a couple of weeks. Hope its OK.
It should be fine, but don't save any important work on it unless you back it up (but that's true of any system, isn't it?).

> **ashwani.nair said:**
> I discovered that I have Synaptic by typing it in the terminal. But, it requires admin privilege it seems. I am planning to use 'sudo synaptic'.
The big advantage of Linux, which seems odd at first to an ex-Windows XP user, is the need to have administration access whenever doing something that affects the system. Generally, that is anything outside your own home computer. You will quickly get used to it.

But...

Never use sudo for graphical programs. For graphical programs, use gksu instead. The correct command to start Synaptic (on my machine, and I presume that it's the same for you) is
```
gksu --description /usr/share/applications/synaptic.desktop /usr/sbin/synaptic
```You can leave off both the description and the path, so a simpler version would be:
```
gksu synaptic
```I'm surprised that you didn't find it in the menu, though.

> **ashwani.nair said:**
> But, eve after launch, I couldnt find 'usbmodeswitch' and 'usbmodeswitch-data'
I too don't have it. I've not heard of them before.

> **ashwani.nair said:**
> Not sure, how to login as admin. Is it possible.
It's possible, but **hugely not recommended.**

I've had Ubuntu for two years, and not once needed to log in as admin. It's unsafe. Linux has proven itself incredibly safe because of the procedures in place; please do follow those procedures.

 > **ashwani.nair said:**
> Once confortable, i will install ubuntu and discard wubi.
That's exactly what I did!

---

### Post by Elfy on 2010-05-31
The package you are looking for is usb-modeswitch and usb-modeswitch-data

[http://packages.ubuntu.com/search?keywords=modeswitch&suite=default&section=all&arch=any&searchon=names](http://packages.ubuntu.com/search?keywords=modeswitch&suite=default&section=all&arch=any&searchon=names)

---

### Post by ashwani.nair on 2010-05-31
Wow... Lightning fast replies. Thanks a lot Paddy and Forestpiskie.

> 
It's possible, but **hugely not recommended.**
Ops..!! I just changed my profile privileges to Admin. Will try to change it back. Don't know how to roll back to the customer priv set by Wubi. 

> 
The package you are looking for is usb-modeswitch and  usb-modeswitch-data
Thanks a lot.. Will try and find them out. By the way... what about the following 
```
wvdialconf/etc/wvdial.conf
```It requested me to install using ```
apt-get install wvdial
``` but when I tried to execute this command, it threw an exception saying unrecognized. 

PS: Sorry, but I have to reboot each time I access the forum as I dont yet have the internet connectivity in Ubuntu.

---

### Post by Paddy Landau on 2010-05-31
> **ashwani.nair said:**
> ... I have to reboot each time I access the forum as I dont yet have the internet connectivity in Ubuntu.
In that case, you won't be able to use Synaptic, as it will need to download the packages that you want to install.

You'll need to fix your connectivity first.

---

### Post by ashwani.nair on 2010-05-31
:(

Is there a way I can download it via windows.. burn a CD and then use it in Linux..? 

Sorry if its a stupid idea. My main efforts are for getting the Huawei USB internet working.

---

### Post by Elfy on 2010-05-31
You can install this in windows apparently - [http://keryxproject.org/download/](http://keryxproject.org/download/) not used it though. 

You could also download the packages from 

[http://packages.ubuntu.com/lucid/usb-modeswitch](http://packages.ubuntu.com/lucid/usb-modeswitch)
[http://packages.ubuntu.com/lucid/usb-modeswitch-data](http://packages.ubuntu.com/lucid/usb-modeswitch-data)

I think that the dependencies are on a default install.

---

### Post by lkraemer on 2010-05-31
wvdial info:
You need to download wvdial and the following dependencies for 10.04.

wvdial & dependencies:
libuniconf4.6
libwvstreams4.6-extras
libwvstreams4.6-base

Located at:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Select 10.04 -> Communications Programs -> wvdial 1.60.3
Download these with XP, then copy the *.deb files to USB Flash Drive,
& then to Ubuntu subdirectory /var/cache/apt/archives & then install
using Synaptic Package Manager.....ie.
```

sudo cp ~/Downloads/mydebs/*.deb /var/cache/apt/archives

```


OR you can go to SYSTEM -> ADMINISTRATION -> SOFTWARE SOURCES
and check the box for installable from CDROM/DVD.........then
insert your LiveCD and install from the CDR.


Boot into Ubuntu, without the USB Modem installed. Open a Terminal
Window and Copy & Paste the following commands. Then post the output here.
```

lsusb

```
Copy the output to a text file opened with gedit. Then plug in the USB
Modem, and wait a minute or two. Repeat the command in the Terminal
Window.
```

lsusb

```
Hopefully, Ubuntu will find the USB Modem.
Post that output.


Then go here:
[http://ubuntuforums.org/showthread.php?t=1483120&highlight=wvdial&page=2](http://ubuntuforums.org/showthread.php?t=1483120&highlight=wvdial&page=2)
Posting #16 and do ONLY these:

[B]SET UP PAP/CHAP:
SETUP WVDIAL:
[/B]

Later you can install Gnome-PPP and use it from the GUI.

lk

---

### Post by ashwani.nair on 2010-05-31
Hi Forestpiskie & IK,

Thanks for this. I will download all the necessary packages from the link mentioned above.

Will try it and post it.

---

### Post by ashwani.nair on 2010-06-01
Hi All,

After all the configuration and different experiments with file in /etc/usb_modeswitch.d/ I tried my best to configure the USB modem only to find out that my equipment was not Huawei but Haier CE100.

I have requested the installation guide with my supplier. Hope I get it soon.

Hi Ik,

I did a 'lsusb' and my system did recognize the USB Modem. Sorry dont have the screenshot or the output handy, but will update this post soon with it. 

Sorry, but couldn't quite follow the 16th Post of the link you passed me. I will give it a try again. As mentioned, the pain is that I have to login to Windows to access net and then boot back to Ubuntu each time I have a doubt. I am happy to take this pain expecting to experience Ubuntu.

---

### Post by lkraemer on 2010-06-01
**SET UP PAP/CHAP**

Locate your userlogin, password, Dialup Provider Info, Phone Number,
and what your ISP uses (PAP or CHAP)

Open a Terminal Window and run the following:
```

sudo pppconfig

```
You will need your userlogin, password, ISP provider information, and
pap or chap information for the connection. (You can set up pap and
then chap, if pap doesn't work.) Basically, you just answer the questions
that are presented. You can delete a configuration and start over if
you need to from the menu selections.

For more information try:
```

man pppd
man pppconfig

```
pap-secrets file contains:
```

# OUTBOUND connections

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.

#       *       password
"yourusername" provider "yourpassword"

```
And the file is located at:
```

/etc/ppp/pap-secrets

```
Use pppconfig to create a modified file or edit the file with:
```

sudo nano /etc/ppp/pap-secrets

```

[B]
SETUP WVDIAL:[/B]

Now ppp is setup and the Drivers are loaded, you will need to set up wvdial.

In a Terminal window do:
```

sudo wvdialconf /etc/wvdial.conf

```
You should get a configuration file that is something like this,
but your modem and some of your parameters may be slightly different
depending on what wvdial detects.
Your PhoneNumber, LoginName, and PassWord will be what you use.
The Modem type ....as in Modem = /dev/ttyACM0 should be determined
by wvdial......hopefully.....
```

sudo nano /etc/wvdial.conf (you may need to edit/add/modify a few things...)

```
wvdial.conf contains:
```

[Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 48800
New PPPD = yes
Stupid mode = yes
;carrier check = no
Modem = /dev/ttyACM0
ISDN = 0
Phone = 4460568
Password = yourpassword
Username = yourusername@yourisp.net

```
You might want to double check the following settings, and the
information provided by pradeepthundiyil in a later posting may apply.
You will need to adjust these as per your testing, then from your feedback
I'll update this guide, so others have good information.
Checking settings of: /etc/ppp/options
```

asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

```
Now assuming that your pap-secrets and or your chap-secrets file is
correct you should be able to use wvdial to dial the connection with:
```

wvdial /etc/wvdial.conf

```
If wvdial gives you an error try:
```

sudo wvdial /etc/wvdial.conf

```
You should hear the modem go OFFHOOK with dialtone, Dial, and connect.
If your config file is correct you should authenticate and then control
will be passed to ppp. You will see several strings of HEX (funny
characters) and then you should stay connected. (you will use CNTL C to
terminate the session when you are done, but for this session you MUST
leave the Terminal window OPEN.....just minimize it) You may have to
uncheck the box marked OFFLINE when you open your browser to make it online.
Surf, then terminate the open session with CNTL C in the open terminal
window where you initiated wvdial.


Finally, when wvdial is working you can Download & Install
Gnome-PPP and then configure/set up Gnome-PPP.

When you get everything working, I'd suggest backing up the pap-secrets,
chap-secrets, and wvdial.conf files....just in case.
You can use:
```

cd /
cd /etc/ppp
sudo cp pap-secrets pap-secrets.sav
sudo cp chap-secrets chap-secrets.sav
cd ..
cp wvdial.conf wvdial.sav

```
to save the backup files.

What was so hard about that?

lk

---

### Post by ashwani.nair on 2010-06-02
Hi Ik,

Thanks for your help and support.

Its my fourth day trying to resolve my internet connection .. phew.. !:(

The hard things currently is that I have to reboot to XP each time, if I have a doubt in Ubuntu. Also, as I am very new to Ubuntu, any command and its result are a bit hard to understand. Sorry for being so lame, and sincerely appreciate your patience in guiding me to resolve the issue. 

The follow are the actions and their results.

I tried listing all the usb attached. 

```
lsusb
```Result

```

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 201e:2009
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```before connecting the USB Device, ```
Bus 003 Device 002: ID 201e:2009
``` was not available, so this is the USB Device I should be configuring. 

According to your guidelines, I did manage to get the username, password and the dial number, but was unable to find out the IP address of Primary name server for ```
pppconfig
```. Its funny, but my ISP call center dont know .. :(

I did an ```
ipconfig
``` in MSDOS prompt and then used the DNS settings to configure ```
pppconfig
```. 

After configuring ```
pppconfig
```I did a 

```
sudo wvdialconf /etc/wvdial.conf
``` - Output window attached in file name "ttyUSB2 conf wvdial". The key parts of output (with my limited knowledge) are.

```
WvModem<*1>: Cannot get information for serial port.
``````
ttyUSB2<*1> Modem Identified: ATI -- Manufacturer: EVDO DataCard
``````
Found a modem on /dev/ttyUSB2.
``````
ttyUSB2<info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
```So, to me it seems ```
wvdial
``` as identified my modem. 

I then saw that Ubuntu tried to connect the net, but then failed. 

I tried to go into the network manager and edit the connection. 

Surprisingly, I have given the password as 'password' in ```
pppconfig
```, but in the network manager it was 'internet'. I tried to edit the password and tried connecting again, but it also failed. 

Following this, I ran ```
wvdial
``` again, but this time, it said 

```
ttyUSB2<Info>: Device or resource busy
``` - screen shot attached 'ttyUSB2 Busy'


----------------------------------------------------------------------------------------

Apart from the above, I have also tried another thing.

My ISP's forum had a Ubuntu configuration PDF for Huawei device, which advice to install ```
usb-modeswitch
``` and ```
usb-modeswitch-data
```. After installing it asked to edit the file 
```
sudo gedit /etc/usb_modeswitch.d/12d1:1446/
```and insert '140b' in the target product list.

I thought, as mine is a Haier device, and mu ```
lsusb
``` command listed 
```
Bus 003 Device 002: ID 201e:2009
```I should have a file named 201e:2009 in the '/etc/usb_modeswitch.d/' folder.

I created a file with the content below.

```

######################
#Haier CE100

Default vendor:0x201e
Default product:0x2009

Target vendor = 0x201e
Target product = '140b'


```I tried to follow the file format for 'Huawei'. I also looked into other files in the folder and realised that each file is for a different vendor and has a different target product list.

This also dint seem to detect my modem. I doubt its the target product which is an issue as '140b' may be for 'Huawei' I should know my product code, which I dont know how to find out.

Pls Note: This action was done prior the pppconfig and wvdial. Wanted to give you an info on other actions I tried to do.

-------------------------------------------------------------------------

One change I have seen after running the pppconfig and wvdial as suggested by you Ik, is that now in the network manager I can see a modem appearing. Earlier no modem was detected.

Before pppconfig and wvdial - (attachment) 'no modem'
after pppconfig and wvdial - (attachment) 'modem'




A very big thanks for your help, support and patience.


---------------------Update-----------------------------------------------------------------------------------

Today Morning, i did tried to do all the settings again.. 

to my surprise, the modem is not detecting any more. 'lsusb' still detects the modem.

'sudo wvdialconf /etc/wvdial.conf' 

says that no modem detected.

Yesterday, it said that the modem at 'ttyUSB2' is busy.

Also, I couldn't see the modem in network manager as well.

I then logged into Windows and opened the USB Modem config files, and the following are some extract from some files.

```

From : 3GDatamdm.inf
------------------------------------------------------------------
[Models]
%QUALCOMM01% = Modem2, USB\VID_201E&PID_1001&MI_00
%QUALCOMM02% = Modem2, USB\VID_201E&PID_1002&MI_00
%QUALCOMM03% = Modem2, USB\VID_201E&PID_1003&MI_00
%QUALCOMM04% = Modem2, USB\VID_201E&PID_1004&MI_00
%QUALCOMM05% = Modem2, USB\VID_201E&PID_1005&MI_00
%QUALCOMM06% = Modem2, USB\VID_201E&PID_1006&MI_02
%QUALCOMM07% = Modem2, USB\VID_201E&PID_1007&MI_03
%QUALCOMM10% = Modem2, USB\VID_201E&PID_1008&MI_00
%QUALCOMM08% = Modem2, USB\VID_201E&PID_2009&MI_00
%QUALCOMM09% = Modem2, USB\VID_201E&PID_2010&MI_00


[QcomSerialPort]
%QcomDevice01% = QportInstall00, USB\VID_201E&PID_1001&MI_02
%QcomDevice02% = QportInstall00, USB\VID_201E&PID_1001&MI_01

%QcomDevice03%  = QportInstall00, USB\VID_201E&PID_1002&MI_02
%QcomDevice04%  = QportInstall00, USB\VID_201E&PID_1002&MI_01

%QcomDevice05%  = QportInstall00, USB\VID_201E&PID_1003&MI_01
%QcomDevice06%  = QportInstall00, USB\VID_201E&PID_1003&MI_02

%QcomDevice07%  = QportInstall00, USB\VID_201E&PID_1004&MI_01
%QcomDevice08%  = QportInstall00, USB\VID_201E&PID_1004&MI_02

%QcomDevice09%  = QportInstall00, USB\VID_201E&PID_1005&MI_01
%QcomDevice10%  = QportInstall00, USB\VID_201E&PID_1005&MI_02

%QcomDevice11%  = QportInstall00, USB\VID_201E&PID_1006&MI_00
%QcomDevice12%  = QportInstall00, USB\VID_201E&PID_1006&MI_01

%QcomDevice13%  = QportInstall00, USB\VID_201E&PID_1007&MI_00
%QcomDevice14%  = QportInstall00, USB\VID_201E&PID_1007&MI_01

%QcomDevice15%  = QportInstall00, USB\VID_201E&PID_2009&MI_01
%QcomDevice16%  = QportInstall00, USB\VID_201E&PID_2009&MI_02

%QcomDevice17%  = QportInstall00, USB\VID_201E&PID_2010&MI_01
%QcomDevice18%  = QportInstall00, USB\VID_201E&PID_2010&MI_02

%QcomDevice19%  = QportInstall00, USB\VID_201E&PID_1008&MI_01

```

---

### Post by lkraemer on 2010-06-04
You only need to do this once:
```

sudo wvdialconf /etc/wvdial.conf

```
But, if you plug the modem into a dfferent USB port the address will
change.  So Plug in the USB Modem in the same USB Port each time.
Then,  use:
```

sudo nano /etc/wvdial.conf

```
to add your information......Only once.......
Something like:
```

[Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 48800
New PPPD = yes
Stupid mode = yes
;carrier check = no
Modem = /dev/ttyACM0
ISDN = 0
Phone = 4460568
Password = yourpassword
Username = yourusername@yourisp.net

```
Your information will be different......according to what wvdial detects
and configures.

Now assuming that your pap-secrets and or your chap-secrets file is
correct you should be able to use wvdial to dial the connection with:
```

wvdial /etc/wvdial.conf

```
If wvdial gives you an error try:
```

sudo wvdial /etc/wvdial.conf

```

lk

---

### Post by ashwani.nair on 2010-06-06
Hi Ik,

Thanks for the reply.

the biggest problem I am facing now is that my Modem is not detected by Ubuntu. 

When I do a 'lsusb' I am getting the output and its listing my USB Modem, but when I configure using 'wvdialconf' it says.. no modem detected. 

More Info on my modem.

Its Haier branded, QualComm modem. 
Vendor ID: 201e
Product ID: 2009

------------------------------------------
Udated:

I will start a new thread as the subject is not related to the post.

---

