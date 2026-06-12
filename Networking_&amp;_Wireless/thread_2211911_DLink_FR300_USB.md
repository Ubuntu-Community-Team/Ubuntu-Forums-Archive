---
title: "DLink FR300 USB"
date: 2014-03-18
forum: Networking &amp; Wireless
---

### Post by Ed_Wolfman on 2014-03-18
I just installed an Ubuntu client for kicks.  I have no UNIX background.  I am trying to set up a wireless connection using a DLink FR300 USB device.  The system is not recognizing the device. I've tried rebooting the system, but it does not recognize the device on bootup.  I believe it is compatible.  Can you give me cookbook instructions on how to coax the system to recognize the device? If necessary, I can connect the system to the internet via a ethernet just to download drivers, etc.

---

### Post by NM5TF on 2014-03-18
open a terminal by holding CTRL + ALT then tap T key.....

copy & paste this code into terminal then hit enter.....

```
nm-tool
```

copy & paste results here using the code tag # in the menu above reply...paste between the #'s

you should get something looking like my example below....

```
tommy3@tommy3-Inspiron-531s:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [xxxxx] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connected
  Default:           yes
  HW Address:        <removed for security>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *xxxx:          Infra, xxx:xxx:xxx:, Freq 2412 MHz, Rate 8 Mb/s, Strength 100 WPA

  IPv4 Settings:
    Address:         192.168.1.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


```

tommy

---

### Post by Ed_Wolfman on 2014-03-18
thanks, Tommy.  Here is what I got when I input nm-tool:

NetworkManager Tool


State: connected (global)


- Device: wlan0  [xxxxx] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connected
  Default:           yes
  HW Address:        <removed for security>


  Capabilities:
    Speed:           72 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *xxxx:          Infra, xxx:xxx:xxx:, Freq 2412 MHz, Rate 8 Mb/s, Strength 100 WPA


  IPv4 Settings:
    Address:         192.168.1.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254


    DNS:             192.168.1.254
tommy


State: disconnected


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000
  State:             unavailable
  Default:           no
  HW Address:        00:C0:9F:1C:62:84


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off

---

### Post by NM5TF on 2014-03-19
OK Ed...now try this....

open a terminal & copy/paste this code into it...

```
sudo apt-get install linux-firmware-nonfree
```

it will ask for your password, but you won't see it while typing it in...a safety feature...

let it finish, then reboot to see if it now works....

tommy

---

### Post by 3rdalbum on 2014-03-19
Note that the directions above require an internet connection of some sort. Ethernet, 3G or phone tethering, whatever is easiest for you.

Edit: It looks like your WiFi card is connected to an access point / router already? Did you find your network listed in the Network management menu in the panel on the top of your screen? What happens if you try to use Firefox?

---

### Post by Ed_Wolfman on 2014-03-19
question:  Do I need to be connected to the internet via wired connection for this to work?

---

### Post by NM5TF on 2014-03-19
> **Ed_Wolfman said:**
> question:  Do I need to be connected to the internet via wired connection for this to work?

yes you do need to be connected as you will be downloading/installing some files....

you said that your wired ethernet was working if I remember correctly...

tommy

---

### Post by Ed_Wolfman on 2014-03-19
here is the result:

ed@ed-desktop:~$ sudo apt-get install linux-firmware-nonfree
[sudo] password for ed: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-firmware-nonfree
ed@ed-desktop:~$ 


Doesn't seem to be working.

---

### Post by NM5TF on 2014-03-19
> **Ed_Wolfman said:**
> here is the result:

ed@ed-desktop:~$ sudo apt-get install linux-firmware-nonfree
[sudo] password for ed: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-firmware-nonfree
ed@ed-desktop:~$ 


Doesn't seem to be working.

hmmmmmm......I am not logged into 12.04 at the moment....I am logged into 14.04 now...
just tried the above command & it worked just fine for me using 14.04.....

will log into 12.04 & try it again....will be back shortly..

tommy

---

### Post by Ed_Wolfman on 2014-03-19
OK.  FWIW:  I did check to make sure the USB connection that the adapter is connected to is working and it is, so that is not the issue.

---

### Post by NM5TF on 2014-03-19
I am back...now logged into 12.04...

just tried the command above with these results....

```
tommy2@tommy-Inspiron-531s:~$ sudo apt-get install linux-firmware-nonfree
[sudo] password for tommy2: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  linux-firmware-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,952 kB of archives.
After this operation, 8,980 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/multiverse linux-firmware-nonfree all 1.11ubuntu2 [3,952 kB]
Fetched 3,952 kB in 24s (159 kB/s)                                             
Selecting previously unselected package linux-firmware-nonfree.
(Reading database ... 267639 files and directories currently installed.)
Unpacking linux-firmware-nonfree (from .../linux-firmware-nonfree_1.11ubuntu2_all.deb) ...
Setting up linux-firmware-nonfree (1.11ubuntu2) ...
tommy2@tommy-Inspiron-531s:~$ 

```

sooooo...it obviously worked for me.....now we need to find why it didn't work for you..

question #1 can you verify that you ***were connected to internet*** when you tried the above command...
the error message almost says it wasn't because it could not find the files....

can you try it again ???

edit: just saw your reply where you said it is connected...please try again...

---

### Post by Ed_Wolfman on 2014-03-19
Ok.  I tried it again.  Same response to inputing the command.  Rebooted.  Same result.
And I am connected to the internet. In fact I'm writing to you from the machine.

---

### Post by NM5TF on 2014-03-19
> **Ed_Wolfman said:**
> Ok.  I tried it again.  Same response to inputing the command.  Rebooted.  Same result.
And I am connected to the internet. In fact I'm writing to you from the machine.

very strange....we need to see if your adapter is being recognized by the system, so do this 1st...

```
 lsusb
```

post your results before going on by using the code tags # in the reply menu...
you may need to use the "go advanced" button to see them...paste the results between
the #'s....

then try this code...

```
sudo lshw -C network
```

paste the results here...

we will proceed based on the results from the above...

tommy

---

### Post by Ed_Wolfman on 2014-03-19
Thanks, Tommy.  I need to get to work, so I'll have to try this later.  Meanwhile, I suppose it is also a possibility the the adaper itself is a piece o crap.  So before I go further, I'll try to connect using a Windows partition and see if I have the same problems.  If that works out, I'll try your suggestions later and let you know.

---

### Post by westie457 on 2014-03-19
Have you set your Software Sources to accept 'restricted' packages

---

### Post by Ed_Wolfman on 2014-03-19
Yes.  I have SW Sources set to accept restricted packages.  Nice thought though.  Thanks.

---

### Post by Ed_Wolfman on 2014-03-19
OK.  some progress here.
I upgraded Ubuntu to the latest version
I tested the adapter in Windows and it works.
I ran the "sudo apt-get install linux-firmware-nonfree" command and this time it went through a procedure to download some things.

Then I ran nm-tool and the received the following:
ed@ed-desktop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            e1000
  State:             connected
  Default:           yes
  HW Address:        00:C0:9F:1C:62:84

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.9
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


ed@ed-desktop:~$ 


However, I am still not able to connect the adapter.  

One thing I didn't do was reboot though.  So I'll do that now.  Fingers crossed.

---

### Post by Ed_Wolfman on 2014-03-20
Rebooted. Ran nm-tool again.  Same result:
d@ed-desktop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            e1000
  State:             connected
  Default:           yes
  HW Address:        00:C0:9F:1C:62:84

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.9
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


ed@ed-desktop:~$ 



Any ideas?

---

### Post by Ed_Wolfman on 2014-03-20
```

ed@ed-desktop:~$ lsusb
Bus 001 Device 002: ID 07d1:3304 D-Link System 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ed@ed-desktop:~$ ^C
ed@ed-desktop:~$ 
```

---

### Post by Ed_Wolfman on 2014-03-20
[CODE} ed@ed-desktop:~$ lsusb
Bus 001 Device 002: ID 07d1:3304 D-Link System 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ed@ed-desktop:~$ ^C
ed@ed-desktop:~$ sudo lshw -C network
[sudo] password for ed: 
  *-network               
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       logical name: eth0
       version: 02
       serial: 00:c0:9f:1c:62:84
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k5-NAPI duplex=full firmware=N/A ip=192.168.1.9 latency=32 link=yes mingnt=255 multicast=yes port=twisted pair speed=1GB/s
       resources: irq:17 memory:fe100000-fe11ffff ioport:ecc0(size=64)
ed@ed-desktop:~$ 
[/CODE]

---

### Post by NM5TF on 2014-03-20
OK Ed...

the lsusb command does show your adapter as Bus 001 Device 002, but 
the lshw command does not show it being enabled...it only shows your
wired ethernet that is working...

you may get lucky...very lucky if these directions make it work for you...

go here to watch a short video...try what he suggests...go here:

[http://www.youtube.com/watch?v=VP3dvzuukJA](http://www.youtube.com/watch?v=VP3dvzuukJA)

if this works that would be great....if not, then we need to go a little
further into using the terminal to install ndiswrapper....

1st things 1st tho...try additional drivers 1st.....good luck

tommy

---

### Post by NM5TF on 2014-03-20
dupe

---

### Post by Ed_Wolfman on 2014-03-23
I watched the video, but it didn't help, since the device was not listed in Additional Drivers.  So, I'm still stymied.  I can't find any drivers for this device...and I don't exactly know how to load them even if I do finds them.  Any help would be appreciated.

---

### Post by chili555 on 2014-03-23
Please discontinue trying to install linux-firmware-nonfree. It contains mostly Broadcom firmware and nothing whatever for your:> 07d1:3304 D-Link System ...which is a Realtek. Please note that there is currently no Linux native driver for this device.

---

### Post by chili555 on 2014-03-23
> **NM5TF said:**
>  install ndiswrapper....

try additional drivers 1st.....good luck

tommyndiswrapper, maybe. Additional Drivers? Nope.

---

### Post by NM5TF on 2014-03-23
> **Ed_Wolfman said:**
> I watched the video, but it didn't help, since the device was not listed in Additional Drivers.  So, I'm still stymied.  I can't find any drivers for this device...and I don't exactly know how to load them even if I do finds them.  Any help would be appreciated.

the driver for your device is on the realtek site....go here & download the ***Unix/Linux driver 2.6.6.0.20120403 ***

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SU](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SU)

it will download a zip file called rtl819xSU_usb_linux_v2.6.6.0.20120405.zip

it will most likely be in your ***Download*** directory

you need to unzip the file 

```
unzip rtl819xSU_usb_linux_v2.6.6.0.20120405.zip
```

then change directory to the unzipped driver folder

```
cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/driver
```

then you need to unpack another compressed file

```
tar xvfz rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405.tar.gz
```

and then double click on the new folder and find the os_intf folder...double click this folder...

double click the linux folder and you will see a file called usb_intf.c

right click this file and select open with gedit

scroll down to your driver which is labeled /* RTL8192SU */

copy & paste this code after the last USB_DEVICE entry, but BEFORE the closed brackets {}

```

/* Frys */
	{USB_DEVICE(0x07D1, 0x3304)},


```

save & close the file....

this a good time take a break & a deep breath ;)

OK Ed...here we go again...it's been a lot of work, but, you are almost there...now do this

```
sudo apt-get install build-essential linux-headers-`uname -r`
```

and then

```
sudo apt-get install linux-headers-generic build-essential 
```

get back to the driver folder...

```
cd /driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405
```

then do 

```
make
```

followed by

```
./clean
```

followed by

```
sudo insmod 8712u.ko
```

followed by

```
sudo chmod 644 8712u.ko
```

and then do this

```
cp 8712u.ko /lib/modules/'uname -r'/kernel/drivers/net/wireless
```

and finally, do this

```
sudo depmod -a
```

This got to be pretty long, I hope you can wrap your head around it. I also hope this gets your wireless working, which was the point of all this! 

let us know if it is working now.....

tommy

---

### Post by Ed_Wolfman on 2014-03-24
Thank you so much.  i'll do all of this tonite after I get home from work. Let you know how it works out, but I'm optimistic.

---

### Post by NM5TF on 2014-03-24
> **Ed_Wolfman said:**
> Thank you so much.  i'll do all of this tonite after I get home from work. Let you know how it works out, but I'm optimistic.

this has worked for others using your wifi adapter, so hope it works for you as well :)

if you copy & paste the codes it will eliminate any chance of typo's that could cause
unwanted consequences...:(

tommy

---

### Post by Ed_Wolfman on 2014-04-06
Hi, I'm back.  I did all that you suggested, but when I get to:
cd /driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405

I get the message that there is no such directory.  I do have a directory in my downloads with that name, but it appears that it can't be found using these commands.

Any suggestions?

---

### Post by NM5TF on 2014-04-06
> **Ed_Wolfman said:**
> Hi, I'm back.  I did all that you suggested, but when I get to:
cd /driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405

I get the message that there is no such directory.  I do have a directory in my downloads with that name, but it appears that it can't be found using these commands.

Any suggestions?

maybe try 

```
cd /Downloads/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405
```

then continue onwards...

tommy

---

### Post by Ed_Wolfman on 2014-04-08
ed@ed-desktop:~$ cd /Downloads/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405
bash: cd: /Downloads/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405: No such file or directory
ed@ed-desktop:~$

---

### Post by NM5TF on 2014-04-08
> **Ed_Wolfman said:**
> ed@ed-desktop:~$ cd /Downloads/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405
bash: cd: /Downloads/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405: No such file or directory
ed@ed-desktop:~$

sorry Ed...am using a new keyboard & keys don't always work like my old 1....:(

try this...

```
cd ~/Downloads/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405
```

just a little typo makes all the difference.....the tilde (~) says it is in your home directory...:D

tommy

---

### Post by Ed_Wolfman on 2014-04-09
ed@ed-desktop:~$ cd ~/Downloads/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405
bash: cd: /home/ed/Downloads/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405: No such file or directory
ed@ed-desktop:~$

---

### Post by NM5TF on 2014-04-09
> **Ed_Wolfman said:**
> ed@ed-desktop:~$ cd ~/Downloads/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405
bash: cd: /home/ed/Downloads/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405: No such file or directory
ed@ed-desktop:~$

in post #29 you said there IS a file with that name in your Downloads directory....is it there or not ???

can you go there & copy/paste the entire file name here ???

tommy

---

### Post by Ed_Wolfman on 2014-04-09
/home/ed/Downloads/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405.tar.gz

---

### Post by NM5TF on 2014-04-10
> **Ed_Wolfman said:**
> /home/ed/Downloads/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405.tar.gz

OK...I see the problem now....\\:D/

try this now...

```
cd ~/ed/Downloads/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405
```

Linux wants it to be EXACTLY like the file is named, or it won't find it...#-o

---

### Post by chili555 on 2014-04-10
About once in every five years I go off like a crazy person. I'm sorry, but this is the thread and this is the day.

OH MY (expletive deleted) UBUNTU!!! The driver you are trying so valiantly to compile won't drive your device even if you somehow manage to find and build it!!!!!!!! This could be a 250 post thread and it still will never work. It's *killing* me to see you chasing a dead end.

End tantrum.

Do you have the driver r8712u in your system? Check:```
modinfo r8712u
```Either you will get a whole lot of data (good!) or a  ERROR: Module r8712u not found (bad!). If you do have it, detach the ethernet, insert the device and run these commands carefully. Proofread twice before you press Enter:```
sudo -i
modprobe r8712u
echo -n "07d1 3304" > /sys/bus/usb/drivers/r8712u/new_id
exit
```Does your device come to life?```
iwconfig
```If so, we'll write to one file and make it permanent.


--------------

Reference: [http://ubuntuforums.org/showthread.php?t=2095623](http://ubuntuforums.org/showthread.php?t=2095623)

---

### Post by kurt18947 on 2014-04-10
Listen to Chili555, he's forgotten more about this stuff than I know.  I'm addressing this thought to Chili555 but it's applicable to this thread.  Would it be wise or make a mess to consider this solution?

[https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

I've used it on releases >12.10 and it has worked well, including on 14.04 so far.  I've used it with generic RTL-8192CU adapters & one RTL8188CUs adapter.

---

### Post by NM5TF on 2014-04-10
thanx for jumping in Chilli555....

I am about at my wit's end trying to get his wifi working....](*,)

I have googled & googled for info on his device, but found nothing other than what I've
been telling Ed.....#-o

like I said before, I'm just a hardware guy...not a software guru by any means...:icon_frown:

---

### Post by Ed_Wolfman on 2014-04-10
Success!!!!!

---

### Post by chili555 on 2014-04-10
> **kurt18947 said:**
> Listen to Chili555, he's forgotten more about this stuff than I know.  I'm addressing this thought to Chili555 but it's applicable to this thread.  Would it be wise or make a mess to consider this solution?

[https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

I've used it on releases >12.10 and it has worked well, including on 14.04 so far.  I've used it with generic RTL-8192CU adapters & one RTL8188CUs adapter.As it is written now, the modalias for his device isn't included in 8192cu:```
chili@Think410:~/rtl8192cu-fixes$ modinfo 8192cu.ko | grep 3304
chili@Think410:~/rtl8192cu-fixes$
```We could, with some guesswork, add it to some .c file or three before we compile it, but I'm more convinced it's an r8712u device than an rtl8192cu device. Note here: [https://wikidevi.com/wiki/Fry's_Electronics_FR-300USB_rev_A1](https://wikidevi.com/wiki/Fry's_Electronics_FR-300USB_rev_A1)  Also, in the reference I linked, the device works (!!!) with the technique I propose. See posts #9 and 10.

---

### Post by NM5TF on 2014-04-10
> **Ed_Wolfman said:**
> Success!!!!!

the best news I've had all day Ed !!!

thanx to Chilli555 once again !!!

now you can mark it solved....use the thread tools at top of thread screen...

---

### Post by chili555 on 2014-04-10
> **Ed_Wolfman said:**
> Success!!!!!LOLOLOL!!

Finally! Here is what you do to make it permanent:```
gksudo gedit /etc/rc.local
```At the end, above exit 0, add two lines:
```
modprobe r8712u
echo -n "07d1 3304" > /sys/bus/usb/drivers/r8712u/new_id
```
Proofread twice carefully, save and close gedit.

After you shutdown and then restart in the normal course of your day, if the wireless is working as expected, please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

### Post by Ed_Wolfman on 2014-04-10
That worked!   I'm working now from the wifi connection!  How do I make it permanent?

---

### Post by Ed_Wolfman on 2014-04-10
Thanks for your help Tommy.  I appreciate your sticking with me on this!  Chili mentioned something about making it permanent. Once I do that, I'll mark it solved.

---

### Post by Ed_Wolfman on 2014-04-10
OK,  We're golden!  Thanks for your help!!!

---

