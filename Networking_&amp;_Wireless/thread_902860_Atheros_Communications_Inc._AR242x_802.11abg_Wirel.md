---
title: "Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by gabsik on 2008-08-27
Hi All!
I have an acer aspire 5520 amd64 athlon and our dear hardy heron operating on it .
Fresh install , i see the "configure third party and propietary drivers" applet confirming with green flags all drivers are supported , in my case the nvidia , the atheros HAL and the atheros 802.11 .For the nvidia few clicks and the 3d desktop got sorted , no stress , but not the wi-fi ! WHY ? I have installed the hardy heron for amd64 , so drivers should be the right ones , i don't see the presence of any wireless interface , i have removed the "gnome network manager" and i installed wicd , great prog , but it doesn't see a wireless 'if' either . I think i don't need to download and compile anything more than what already is on my pc where also the ndiswrapper module is present . In a previous install , i don't remember if i installed both madwifi and ndiswrapper , but i had two wireless extensions an ath0 and a wifi0 , they handled the connection to the router but no browsing , all really bad !!!!```
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```This is my wireless interface , i don't think i need to download anything more and i'm sure i can already now configure wireless for my pc . I modprobed all the ath* drivers , what else should i do ? Module-assistant ? Am i going all wrong ? :confused:Thanks!

---

### Post by porchrat on 2008-08-27
I had the same card...madwifi worked for me...didn't need ndiswrapper

---

### Post by gabsik on 2008-08-31
**SUCCESS !**
I only installed a subversion madwifi package , after finished i have closed the terminal and i couldn't make any 'copy and paste' of the entire operation to have a detailed share of the success  here . I saw this thread basically in any linux forum of cyberspace , so i will be really short and essential .  
[B]
"The 5 rules to have wifi working with Ubuntu 8.04 Hardy Heron on "AMD64 AthlonX2 Acer ASPIRE 5520 and Atheros AR242x 802.11abg"[/B]  . 

It was a week ago , so they are well tested . 

1 ) First purge any presence or activity of any form of ndiswrapper. After reboot the Hardware drivers listed in System/HardwareDrivers must have a red light aside .

2 ) Remove from /etc/modprobe/blacklist any reference of ath_pci and ath_hal you removed before ...

3 ) Download:
```
svn co https://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6
```

4 ) Install it reading the INSTALL files inside the package.
 
5 ) Enable back both drivers , reboot , enjoy !!!! :popcorn:

P.S. 
If you don't know much of compiling generally ( and this case is about compiling a module ) launch apt-get install module-assistant . Than launch it on its own in a terminal window and it prompts you with a list of options . Choose "PREPARE" it is to prepare the system for compiling modules and it downloads for you all kernel headers and compilers you need . It's best if you do this before you launch "make && make install" after the driver download !!!!

---

### Post by gabsik on 2008-09-01
Still a week later after nvidia drivers gave me propblems on resolution screen ( 900x800 ) and after i have installed the envyng package as last resort (mine is a nvidia geforge 7000m not fully supported ) and sorted out the video , ath_pci stopped working ! Yeah ! You got it ! i have no wireless again now ....

---

### Post by porchrat on 2008-09-01
navigate to the madwifi driver directory and do a make clean then redo the install on the madwifi drivers?

hopefully that will help

---

### Post by reasoner on 2008-09-02
Thanks so much to those above for figuring this out for me. Let me spell out the installation in a little more detail to save those after me some time.

I did this on a fresh Ubuntu 8.04 install on a Compaq Presario C770US Laptop with an ethernet cable plugged into my router.

The device string displayed by lspci -v was as follows:

```
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 137a
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 91300000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
```

First under System/Administration/HarwareDrivers disable both the Atheros HAL and the Atheros wireless thing and then reboot.

The kernel headers and the compiler are needed to build this driver so I started by installing build-essential. In a terminal window (Applications/Accessories/Terminal) enter:

```
sudo apt-get install build-essential
```

The driver code will be downloaded with the subversion source code manager so I installed subversion:

```
sudo apt-get install subversion
```

I needed a place to put the driver source without mixing it up with other stuff so I changed directory to my home directory:

```
cd ~
```

Created a directory:

```
mkdir madwifi
```

And changed to the new dirctory:

```
cd madwifi
```

Use subversion to download (checkout) a copy of the code:

```
svn co https://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6
```

The above command failed for me at first because subversion couldn't find svn.madwifi.org
Madwifi will probably have their DNS problems worked out by the time you read this. But if not then see the section at the bottom of this post titled "Cant find svn.madwifi.org" for a solution before continuing.

After the driver code is downloaded by subversion, change to the directory, which should be madwifi-hal-0.10.5.6

```
cd madwifi-hal-0.10.5.6
```

Run the make script to have the compiler build the driver:

```
make
```

Install the driver

```
sudo make install
```

Add the Atheros kernel module to the list of modules to be automatically loaded at boot by adding "ath_pci" (without the quotes) to the end of the /etc/modules file. I used the vi editor which I won't describe here. Gedit is probably easy to use so try:

```
sudo gedit /etc/modules
```

Now you can reboot and it should work. To get it working without a reboot you need to load the module manually:

```
sudo modprobe ath_pci
```

That should do it. The little wireless button seems to always stay lit orange. When I press it it seems to disable the wireless but it still stays lit orange. WPA works for me. I assume WEP will also. I haven't tried WPA2



CANT FIND svn.madwifi.org

If subversion has a hard time finding svn.madwifi.org then add it's IP address to your hosts file. I found this page [http://madwifi.org/ticket/1982](http://madwifi.org/ticket/1982) at madwifi.org that gives the IP address 217.24.1.142 of svn.madwifi.org in one of the last messages. I tried just giving subversion the command to connect to the IP address instead of the domain name, but it failed before finishing the checkout. Edit the file /etc/hosts and add "217.24.1.142  svn.madwifi.org" (without the quotes). I added it just after the 127.0.1.1 line

```
sudo gedit /etc/hosts
```

Now you can continue with the subversion checkout. You should probably remove this line from your hosts file when you're done with this so that if you want to go back there some day and they've moved it then DNS will give the most recent IP address.

---

### Post by xox on 2008-09-04
this post (reasoner) was a huge help - previous to this i had tried other madwifi install methods and the ndiswrapper with both atheros and broadcom wireless xp drivers.  

i managed to install both xp drivers, but never detected any wireless networks.  with this post, i now see available wireless networks - but - i am unable to connect to them.

i tried connecting both from the wireless drop down list, and through manual configuration, without any luck.

i both followed reasoner's steps (successfully) and tried, and then also re-enabled the two wireless driver in hardware settings as gabsik mentioned - no luck either time.

any suggestions would be great - cheers

---

### Post by gabsik on 2008-09-05
I have formatted and installed back the lot . I have formatted my previous installation cause after madwifi subversion install , if i'm not wrong , nvidia stopped working , giving a really low resolution i could not get around for the low resolution and gave up . 
I will install the package fron madwifi.org and i will tell u ...

---

### Post by gabsik on 2008-09-07
Ok giving for damn sure that if you want wireless working on your acer aspire 5520 with atheros wireless card you have to follow this tutorial [http://forumubuntusoftware.info/viewtopic.php?f=7&t=1278](http://forumubuntusoftware.info/viewtopic.php?f=7&t=1278) ,no ndiswrapper of whatever .
Nvidia also stopped working cause i have upgraded the kernel .
On this new install i have the big orange star of new available updates staying on the top of the desktop and i'm not going to do any update for now . When i will , cause i will , i have to cd back in madwifi sorces dir launch a make clean && make && make install , and then i will have my wireless devices up again , am i wrong ? Thanks !
p.s.
What for nvidia ?

---

### Post by spynga on 2008-09-27
this worked like a charm my windows went down so i had to find a solution for my wireless and this worked after like 50 other tutorials i tried

---

### Post by bpalyshka on 2008-10-02
> **reasoner said:**
> Thanks so much to those above for figuring this out for me. Let me spell out the installation in a little more detail to save those after me some time.

I did this on a fresh Ubuntu 8.04 install on a Compaq Presario C770US Laptop with an ethernet cable plugged into my router.

The device string displayed by lspci -v was as follows:

```
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 137a
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 91300000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
```

First under System/Administration/HarwareDrivers disable both the Atheros HAL and the Atheros wireless thing and then reboot.

The kernel headers and the compiler are needed to build this driver so I started by installing build-essential. In a terminal window (Applications/Accessories/Terminal) enter:

```
sudo apt-get install build-essential
```

The driver code will be downloaded with the subversion source code manager so I installed subversion:

```
sudo apt-get install subversion
```

I needed a place to put the driver source without mixing it up with other stuff so I changed directory to my home directory:

```
cd ~
```

Created a directory:

```
mkdir madwifi
```

And changed to the new dirctory:

```
cd madwifi
```

Use subversion to download (checkout) a copy of the code:

```
svn co https://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6
```

The above command failed for me at first because subversion couldn't find svn.madwifi.org
Madwifi will probably have their DNS problems worked out by the time you read this. But if not then see the section at the bottom of this post titled "Cant find svn.madwifi.org" for a solution before continuing.

After the driver code is downloaded by subversion, change to the directory, which should be madwifi-hal-0.10.5.6

```
cd madwifi-hal-0.10.5.6
```

Run the make script to have the compiler build the driver:

```
make
```

Install the driver

```
sudo make install
```

Add the Atheros kernel module to the list of modules to be automatically loaded at boot by adding "ath_pci" (without the quotes) to the end of the /etc/modules file. I used the vi editor which I won't describe here. Gedit is probably easy to use so try:

```
sudo gedit /etc/modules
```

Now you can reboot and it should work. To get it working without a reboot you need to load the module manually:

```
sudo modprobe ath_pci
```

That should do it. The little wireless button seems to always stay lit orange. When I press it it seems to disable the wireless but it still stays lit orange. WPA works for me. I assume WEP will also. I haven't tried WPA2



CANT FIND svn.madwifi.org

If subversion has a hard time finding svn.madwifi.org then add it's IP address to your hosts file. I found this page [http://madwifi.org/ticket/1982](http://madwifi.org/ticket/1982) at madwifi.org that gives the IP address 217.24.1.142 of svn.madwifi.org in one of the last messages. I tried just giving subversion the command to connect to the IP address instead of the domain name, but it failed before finishing the checkout. Edit the file /etc/hosts and add "217.24.1.142  svn.madwifi.org" (without the quotes). I added it just after the 127.0.1.1 line

```
sudo gedit /etc/hosts
```

Now you can continue with the subversion checkout. You should probably remove this line from your hosts file when you're done with this so that if you want to go back there some day and they've moved it then DNS will give the most recent IP address.



Somebody give this man a round of applause!!!!:popcorn: after a full re-install i forgot to copy the info on getting it working again.  many thanks

ben

---

### Post by lbthrice on 2008-10-08
gabsik and reasoner +99 Karma
respect

note:
worked first try on my toshiba satellite A215
Please note that reasoners step by step worked after reboot
I consulted the INSTALL file in the madwifi folder and ignored the reccommended requirements for kernel option...no change in kernel options needed here on fresh Ubuntu 8.04 (Hardy) install

---

### Post by iliaarpad on 2008-10-09
> **reasoner said:**
> I did this on a fresh Ubuntu 8.04 install on a Compaq Presario C770US Laptop with an ethernet cable plugged into my router.


And what if I don't have an ethernet cable plugged in?
I tried following the guide at madWifi but after modprobing the ath_pci module I still don't have any ath0 or wifi0 device (only eth0 and lo). Make and make install both finished without errors and the ath_pci module seemed to load fine.
If you need the console output or any other info, I will post it as well.

Thanks in advance for any help!

EDIT: I managed to get a cable based internet access for the weekend. I will try reasoner's solution and see if it helps me, too.

EDIT2: I followed the one linked in by gabsik and it seems it worked. Many thanks for both reasoner and gabsik!

---

### Post by 3hough on 2008-10-12
Many thanks!! Works perfectly (after reboot) on my Toshiba L305-5891.

---

### Post by buckman5 on 2008-10-16
hi i did everything that bpalyshka told me to except at the end when he says



" Add the Atheros kernel module to the list of modules to be automatically loaded at boot by adding "ath_pci" (without the quotes) to the end of the /etc/modules file. I used the vi editor which I won't describe here. Gedit is probably easy to use so try:

Code:

sudo gedit /etc/modules

Now you can reboot and it should work. To get it working without a reboot you need to load the module manually:"





when i do this a firefox window opens and tells me this 




# /etc/modules: kernel modules to load at boot time. 
# 
# This file contains the names of kernel modules that should be loaded 
# at boot time, one per line. Lines beginning with "#" are ignored. 

fuse 
lp 
rtc





i dont know what it means or what to do with it. will some one please help me with this?

dylan

---

### Post by feelinggood on 2008-10-20
> **buckman5 said:**
> hi i did everything that bpalyshka told me to except at the end when he says



" Add the Atheros kernel module to the list of modules to be automatically loaded at boot by adding "ath_pci" (without the quotes) to the end of the /etc/modules file. I used the vi editor which I won't describe here. Gedit is probably easy to use so try:

Code:

sudo gedit /etc/modules

Now you can reboot and it should work. To get it working without a reboot you need to load the module manually:"





when i do this a firefox window opens and tells me this 




# /etc/modules: kernel modules to load at boot time. 
# 
# This file contains the names of kernel modules that should be loaded 
# at boot time, one per line. Lines beginning with "#" are ignored. 

fuse 
lp 
rtc





i dont know what it means or what to do with it. will some one please help me with this?

dylan

put this just below rtc,  ath_pci  then save it and reboot your computer.  Steve

---

### Post by tlaud on 2008-11-01
After 5 weeks of search I finaly find your solution.  It worked very fine.  I have two wireless network and I change from one to the other without problem with an Compaq Presario c700US :popcorn:
I will spread your solution to the french board.  Thanks !

---

### Post by tlaud on 2008-11-01
A question to REASONER or the one who have the answer.  I do an update, and lost my wireless connection. When it worked, the programm WIFI RADAR show my SSID the signal, the mode to MAster ans the 802.11 to b.  Now (when not working it show the SSID mode to G, but no connection... I change my source for update and uncheck (Canonical (main) re make the last line of REASONER setup, reboot and recover the connection in b mode.  IF I right b mode is less rapid than G ? (for my writing faults)

---

### Post by reasoner on 2008-11-13
The wireless stopped working on my Presario C770US after an update, I think, so I did these things. I'm not sure which solved it.

Before doing these things try pressing the wireless button once to re-enable the wireless if you might have disabled it by accidentally pressing the button.

And make sure that in System/Administration/HardwareDrivers you have NOT enabled the Atheros HAL and Support for Atheros wireless stuff while you were trying to fix the problem (in my system it says that the status is "In Use" but make sure the "Enabled" boxes are empty).


First I rebuilt the atheros driver. If you followed my intructions above then at the terminal prompt you can change into the driver directory like this:

```
cd ~/madwifi/madwifi-hal-0.10.5.6
```

Then clean out old make settings so it will be built to match the new kernel:

```
make clean
```

Build the driver

```
make
```

I don't know if it's necessary but this might be a good place to remove the old driver from the running kernel:

```
sudo modprobe -r ath_pci
```

Now install the driver:

```
sudo make install
```

I tried reloading the ath_pci module with modprobe but it still wouldn't work. I think a reboot is necessary at this point.

It should work now after a reboot. Good luck.

---

### Post by greymoose58 on 2008-11-13
Reasoner,
Thanks for this How To. It saved a lot of heartache trying to work out how to get the new laptop working at home. Now I can play!
I couldn't find a thanks button on the post to make this more formal but thanks anyway.

---

### Post by enigmageek on 2008-11-13
Hello all. I have a Toshiba A205 S5843 laptop with AR5007EG chipset. Using the original instructions with the newest ath_hal, wireless works perfectly. I recently built the latest 2.6.27 kernel from kernel.org in Hardy cuz I don't want to give up my KDE 3.5.10 by upgrading to Intrepid. I installed DKMS to recompile certain drivers upon kernel updates, madwifi, virtualbox, etc., automatically. I have the dkms.conf file for madwifi_hal and it works great. Just a thought. If anyone wants, I can post the dkms conf and commands to add, build, etc. Also I use scripts to reset networking, set link speed, etc. after resume from suspend.
Regards,
Ray
Ubuntu Hardy 8.0.4.1- 2.6.27.5
Windows Vista and XP via VirtualBox :)

---

### Post by theundecided on 2008-11-20
I need help... I tryed to install via step by step and it worked the first time...then it stoped working... I deleated the madwifi folder trying to uninstall the driver...then (tried) to reinstall but to no avail... I got this message
```
mjrindewitt@Lappy:~$ sudo apt-get install build-essential
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
mjrindewitt@Lappy:~$ 

```

---

### Post by greymoose58 on 2008-11-20
Undecided,
 
Did you run the code? 

> **theundecided said:**
> 
```
 dpkg --configure -a 
```

You will need to run it as root. As far as I understand it corrects any configuration errors it is able to. Hopefully that will solve your problem. If it doesn't post the output here and someone may be able to suggest another approach.

Whatever the outcome you aren't alone. My wireless died again too. I've been running on a cable network until I have time to get back to it.](*,)

---

### Post by theundecided on 2008-11-20
I did but it didn't do anything...is it best to just format my partition and re install ubuntu... (I just installed it like yesterday)
8-[ thanks for your help

btw here is the code I put in and its output

```
root@Lappy:/home/mjrindewitt# dpkg --configure -a
root@Lappy:/home/mjrindewitt# 


```

---

### Post by nolimits76 on 2008-11-25
Reasors...thanx a million for posting the instructions bro, it saved my rear!  Yes, I'm a noob and the step-by-step guide helped bunches.

My specifics...HP Pavillion dv9999us, 64 bit, Intrepid 8.10

Not alot of info out there for the dv9999us yet, but it does work for those with the same model.

---

### Post by HanDerre on 2008-12-02
*buys a round of Jack Daniels and Jamaican Red-Stripe to all and everyone*
:guitar::popcorn:

You guys helped me finally get my wi-fi up and running on my AAO 110L. After 2 months of pulling nasal hairs in frustration of sending it back to service twice due to software and BIOS-errors, trying to loose the ash-ugly Acer desktop and tweaking the xfce-environment resulting in a dozen revoveries daily the last week and installing and uninstalling: Mandriva 2009, Fedora10, Ubuntu8.04UNR, Ubuntu 8.10lpia-mid and finally 8.10 desktop I FINALLY have a netbook that is eye-candy and chic-magnet at hotspots! 

I have now a EXT2 set-up and wi-fi running smooth and this guide really did it for me so pardon my euforia but the above mentioned beverages are starting to kick in!

*KUDOS*

Best regards,

HanDerre

---

### Post by lionstone on 2008-12-02
Just wanted to add that the approach by gabsik worked like a charm on a new lenovo thinkpad t400 with the standard wifi driver ( the AR242x rev 01 )... Many thanks!

---

### Post by gentlejunk on 2008-12-05
hi, thanx so much for step by step directions for all time nwby like me :)

i have a problem:

after typing make (following the directions):

gj@ubuntu:~/madwifi/madwifi-hal-0.10.5.6$ make
cd: 1: can't cd to /lib/modules/2.6.24-22-rt/build
Makefile.inc:66: *** /lib/modules/2.6.24-22-rt/build is missing, please set KERNELPATH.  Stop.
gj@ubuntu:~/madwifi/madwifi-hal-0.10.5.6$ sudo make install
cd: 1: can't cd to /lib/modules/2.6.24-22-rt/build
Makefile.inc:66: *** /lib/modules/2.6.24-22-rt/build is missing, please set KERNELPATH.  Stop.
gj@ubuntu:~/madwifi/madwifi-hal-0.10.5.6$ make KERNELPATH=/usr/src/linux-2.6.24.22
cd: 1: can't cd to /usr/src/linux-2.6.24.22
Makefile.inc:66: *** /usr/src/linux-2.6.24.22 is missing, please set KERNELPATH.  Stop.
gj@ubuntu:~/madwifi/madwifi-hal-0.10.5.6$ make KERNELPATH=/usr/src/linux-headers-2.6.24.22
cd: 1: can't cd to /usr/src/linux-headers-2.6.24.22
Makefile.inc:66: *** /usr/src/linux-headers-2.6.24.22 is missing, please set KERNELPATH.  Stop.
gj@ubuntu:~/madwifi/madwifi-hal-0.10.5.6$ make KERNELPATH=/usr/src/linux-headers-2.6.24-22
./kernelversion.c:13:30: error: linux/utsrelease.h: No such file or directory
Makefile.inc:91: *** KERNELCONF: /usr/src/linux-headers-2.6.24-22/.config does not exist..  Stop.
gj@ubuntu:~/madwifi/madwifi-hal-0.10.5.6$ make KERNELPATH=/usr/src/linux-headers-2.6.24-22-rt
cd: 1: can't cd to /usr/src/linux-headers-2.6.24-22-rt
Makefile.inc:66: *** /usr/src/linux-headers-2.6.24-22-rt is missing, please set KERNELPATH.  Stop.
gj@ubuntu:~/madwifi/madwifi-hal-0.10.5.6$ 
gj@ubuntu:~/madwifi/madwifi-hal-0.10.5.6$ make clean
cd: 1: can't cd to /lib/modules/2.6.24-22-rt/build
Makefile.inc:66: *** /lib/modules/2.6.24-22-rt/build is missing, please set KERNELPATH.  Stop.
gj@ubuntu:~/madwifi/madwifi-hal-0.10.5.6$ make
cd: 1: can't cd to /lib/modules/2.6.24-22-rt/build
Makefile.inc:66: *** /lib/modules/2.6.24-22-rt/build is missing, please set KERNELPATH.  Stop.
gj@ubuntu:~/madwifi/madwifi-hal-0.10.5.6$ 

tried different approaches, am somehow inclined to think that its real time kernel that i should direct my path to, but that there is something missing. im not sure where karnel path is but in /usr/src have only linux-headers-2.6.24-22 and same but generic one

?

can anyone

---

### Post by gentlejunk on 2008-12-05
hi again, few hours later

tried with

sudo make install KERNELPATH=/lib/modules/2.6.24-22-generic/build
to install into generic kernel,, it makes whole proces, but after rebooting i stil dont have wireless

here is  lspci -v | less
if thats any help

02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
        Subsystem: Unknown device 1a32:0105
        Flags: fast devsel, IRQ 16
        Memory at f4000000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>




crushed:frown::frown::frown:

---

### Post by abhilashkumar on 2008-12-07
@reasoner

Your guide worked great for me on my fresh install of 8.10 today.
ndiswrapper used to do duty in 8.04, but it refused to compile on 8.10.

Thanks a lot.

By the way I have an Acer 4520 laptop with the same wlan card.

---

### Post by enigmageek on 2008-12-07
theundecided, please prepend sudo to the command
sudo dpkg --configure -a
Good luck.

---

### Post by gentlejunk on 2008-12-08
i have found what was wrong with PATH, so just before doinmg step by step guide i had to

sudo aptitude update && sudo aptitude -y install build-essential linux-headers-$(uname -r)


thnx, it works now :p

---

### Post by kozhi on 2008-12-17
Running Ubuntu 8.10 Intrepid Ibex on Compaq Presario cQ60 104TU with AR242x 802.11abg Wireless PCI Express Adapter. Don't have access to wired lan (I think iliaarpad below also posed a similar issue), so much of what reasoner advised perhaps can't be applied. I downloaded madwifi-0.9.4.tar.gz and madwifi-0.9.4.tar.bz2 from sourceforge site through another machine to my thumb drive. What do I do from here? This is the first time I am ever into linux - so any suggestions must be "safe", preferably with what precautions to take. Thanks a lot.

---

### Post by Deriem on 2008-12-21
thank you reasoner for that awesome post, you have helped me extrordanarily much.
I have an acer aspire 5315 w/ ubuntu 8.10 and your instructions worked like a charm.
This article should be on the ubuntu main page and you would be tech support for the tech support. once again thank you

---

### Post by ufos2010 on 2008-12-26
> **reasoner said:**
> Thanks so much to those above for figuring this out for me. Let me spell out the installation in a little more detail to save those after me some time.

I did this on a fresh Ubuntu 8.04 install on a Compaq Presario C770US Laptop with an ethernet cable plugged into my router.

The device string displayed by lspci -v was as follows:

```
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 137a
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 91300000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
```

First under System/Administration/HarwareDrivers disable both the Atheros HAL and the Atheros wireless thing and then reboot.

The kernel headers and the compiler are needed to build this driver so I started by installing build-essential. In a terminal window (Applications/Accessories/Terminal) enter:

```
sudo apt-get install build-essential
```

The driver code will be downloaded with the subversion source code manager so I installed subversion:

```
sudo apt-get install subversion
```

I needed a place to put the driver source without mixing it up with other stuff so I changed directory to my home directory:

```
cd ~
```

Created a directory:

```
mkdir madwifi
```

And changed to the new dirctory:

```
cd madwifi
```

Use subversion to download (checkout) a copy of the code:

```
svn co https://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6
```

The above command failed for me at first because subversion couldn't find svn.madwifi.org
Madwifi will probably have their DNS problems worked out by the time you read this. But if not then see the section at the bottom of this post titled "Cant find svn.madwifi.org" for a solution before continuing.

After the driver code is downloaded by subversion, change to the directory, which should be madwifi-hal-0.10.5.6

```
cd madwifi-hal-0.10.5.6
```

Run the make script to have the compiler build the driver:

```
make
```

Install the driver

```
sudo make install
```

Add the Atheros kernel module to the list of modules to be automatically loaded at boot by adding "ath_pci" (without the quotes) to the end of the /etc/modules file. I used the vi editor which I won't describe here. Gedit is probably easy to use so try:

```
sudo gedit /etc/modules
```

Now you can reboot and it should work. To get it working without a reboot you need to load the module manually:

```
sudo modprobe ath_pci
```

That should do it. The little wireless button seems to always stay lit orange. When I press it it seems to disable the wireless but it still stays lit orange. WPA works for me. I assume WEP will also. I haven't tried WPA2



CANT FIND svn.madwifi.org

If subversion has a hard time finding svn.madwifi.org then add it's IP address to your hosts file. I found this page [http://madwifi.org/ticket/1982](http://madwifi.org/ticket/1982) at madwifi.org that gives the IP address 217.24.1.142 of svn.madwifi.org in one of the last messages. I tried just giving subversion the command to connect to the IP address instead of the domain name, but it failed before finishing the checkout. Edit the file /etc/hosts and add "217.24.1.142  svn.madwifi.org" (without the quotes). I added it just after the 127.0.1.1 line

```
sudo gedit /etc/hosts
```

Now you can continue with the subversion checkout. You should probably remove this line from your hosts file when you're done with this so that if you want to go back there some day and they've moved it then DNS will give the most recent IP address.

This really helped me out! On Acer Aspire 5315-2326 Thank you for spelling it out so very well!!!:)

---

### Post by kozhi on 2008-12-31
Thanks to reasoner for the solution - it worked out really smoothly for me.

---

### Post by ´silas on 2009-01-02
Thank you for the excellent post, this worked perfectly :D

---

### Post by thewaytolite on 2009-01-06
This is the correct subversion site

svn co [http://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6](http://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6)

Thank you Reasoner it worked like a charm

---

### Post by kozhi on 2009-01-22
> **reasoner said:**
> The wireless stopped working on my Presario C770US after an update, I think, so I did these things. I'm not sure which solved it.

Thanks once again reasoner - the solution worked like a charm. Second time I followed your posts - the first time being to get my ath wireless on a compaq presario laptop  working by installing madwifi.:p

---

### Post by Tuliku on 2009-01-23
Followed all the steps from Reasoner, but wifi does not seem to come up..
I got a Toshiba NB100 with the same wireless card mentioned here.
Anyone got some idea's ?

---

### Post by jms1989 on 2009-01-24
I tried everything Reasoner said to do but I can't even get it to show up when I run ifconfig and iwconfig. The biggest problem is that he mentions that I need to reboot but I can't do that since I'm running from a live cd and rebooting will erase all my efforts. Fortunately, I have a flash drive with 1GB set aside for this project of getting ubuntu 8.10 to work completely on my moms hp pavilion dv7-1135nr.

I downloaded the subversion files but that didn't work. When I try to restart my networking system, the whole system tends to stop functioning properly. Wifi is important so I can show mom ubuntu running with internet access. Also, I use a bash script to prepare the live cd environment for use so any necessary command that need to be ran will run from the script.

lspci
```

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
08:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
08:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
08:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
09:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

---

### Post by Tuliku on 2009-01-28
> **Tuliku said:**
> Followed all the steps from Reasoner, but wifi does not seem to come up..
I got a Toshiba NB100 with the same wireless card mentioned here.
Anyone got some idea's ?

Anyone.....? Pleaseeee.... Pretty pleaseeeeee......?

---

### Post by 3mb0 on 2009-01-29
> **reasoner said:**
> The wireless stopped working on my Presario C770US after an update, I think, so I did these things. I'm not sure which solved it.

Before doing these things try pressing the wireless button once to re-enable the wireless if you might have disabled it by accidentally pressing the button.

And make sure that in System/Administration/HardwareDrivers you have NOT enabled the Atheros HAL and Support for Atheros wireless stuff while you were trying to fix the problem (in my system it says that the status is "In Use" but make sure the "Enabled" boxes are empty).


First I rebuilt the atheros driver. If you followed my intructions above then at the terminal prompt you can change into the driver directory like this:

```
cd ~/madwifi/madwifi-hal-0.10.5.6
```

Then clean out old make settings so it will be built to match the new kernel:

```
make clean
```

Build the driver

```
make
```

I don't know if it's necessary but this might be a good place to remove the old driver from the running kernel:

```
sudo modprobe -r ath_pci
```

Now install the driver:

```
sudo make install
```

I tried reloading the ath_pci module with modprobe but it still wouldn't work. I think a reboot is necessary at this point.

It should work now after a reboot. Good luck.

NEED YOUR HELP!

reasoner, i have an issue, and that issue is this part of your tutorial : "Use subversion to download (checkout) a copy of the code:" Now i installed subversion and all, but i do not know where to access it, or how to get to it. so i do not know how to continue. NEED WIRELESS PLEASE HELP

3mb0

---

### Post by jelle_ on 2009-02-07
Thanks gabsik

this works great on my laptop. 

jelle_

---

### Post by drskartik on 2009-02-14
Hi! Reasoner
I had the same problems in installing the atheros in my Dell laptop. Thanks for your detailed step by step guide. Being a novice i  just  copy/pasted your steps and was finally successful in being wifi enabled!

---

### Post by enternet1988 on 2009-02-18
reasoner your walk though was awesome it worked
I have been trying for 6 months
Thank you for your time and effort I'm so great full

---

### Post by HouseHarpell on 2009-02-19
> **reasoner said:**
> The wireless stopped working on my Presario C770US after an update, I think, so I did these things. I'm not sure which solved it.

Before doing these things try pressing the wireless button once to re-enable the wireless if you might have disabled it by accidentally pressing the button.

And make sure that in System/Administration/HardwareDrivers you have NOT enabled the Atheros HAL and Support for Atheros wireless stuff while you were trying to fix the problem (in my system it says that the status is "In Use" but make sure the "Enabled" boxes are empty).


First I rebuilt the atheros driver. If you followed my intructions above then at the terminal prompt you can change into the driver directory like this:

```
cd ~/madwifi/madwifi-hal-0.10.5.6
```

Then clean out old make settings so it will be built to match the new kernel:

```
make clean
```

Build the driver

```
make
```

I don't know if it's necessary but this might be a good place to remove the old driver from the running kernel:

```
sudo modprobe -r ath_pci
```

Now install the driver:

```
sudo make install
```

I tried reloading the ath_pci module with modprobe but it still wouldn't work. I think a reboot is necessary at this point.

It should work now after a reboot. Good luck.

huge help!! tyvm:popcorn:

---

### Post by binbash on 2009-02-19
[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

---

### Post by icecreamcakez on 2009-02-23
I have a Gateway t6330u
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 04)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
04:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] 

jes

---

### Post by pogztimz on 2009-03-04
> **reasoner said:**
> Thanks so much to those above for figuring this out for me. Let me spell out the installation in a little more detail to save those after me some time.

I did this on a fresh Ubuntu 8.04 install on a Compaq Presario C770US Laptop with an ethernet cable plugged into my router.

The device string displayed by lspci -v was as follows:

```
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 137a
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 91300000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
```

First under System/Administration/HarwareDrivers disable both the Atheros HAL and the Atheros wireless thing and then reboot.

The kernel headers and the compiler are needed to build this driver so I started by installing build-essential. In a terminal window (Applications/Accessories/Terminal) enter:

```
sudo apt-get install build-essential
```

The driver code will be downloaded with the subversion source code manager so I installed subversion:

```
sudo apt-get install subversion
```

I needed a place to put the driver source without mixing it up with other stuff so I changed directory to my home directory:

```
cd ~
```

Created a directory:

```
mkdir madwifi
```

And changed to the new dirctory:

```
cd madwifi
```

Use subversion to download (checkout) a copy of the code:

```
svn co https://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6
```

The above command failed for me at first because subversion couldn't find svn.madwifi.org
Madwifi will probably have their DNS problems worked out by the time you read this. But if not then see the section at the bottom of this post titled "Cant find svn.madwifi.org" for a solution before continuing.

After the driver code is downloaded by subversion, change to the directory, which should be madwifi-hal-0.10.5.6

```
cd madwifi-hal-0.10.5.6
```

Run the make script to have the compiler build the driver:

```
make
```

Install the driver

```
sudo make install
```

Add the Atheros kernel module to the list of modules to be automatically loaded at boot by adding "ath_pci" (without the quotes) to the end of the /etc/modules file. I used the vi editor which I won't describe here. Gedit is probably easy to use so try:

```
sudo gedit /etc/modules
```

Now you can reboot and it should work. To get it working without a reboot you need to load the module manually:

```
sudo modprobe ath_pci
```

That should do it. The little wireless button seems to always stay lit orange. When I press it it seems to disable the wireless but it still stays lit orange. WPA works for me. I assume WEP will also. I haven't tried WPA2



CANT FIND svn.madwifi.org

If subversion has a hard time finding svn.madwifi.org then add it's IP address to your hosts file. I found this page [http://madwifi.org/ticket/1982](http://madwifi.org/ticket/1982) at madwifi.org that gives the IP address 217.24.1.142 of svn.madwifi.org in one of the last messages. I tried just giving subversion the command to connect to the IP address instead of the domain name, but it failed before finishing the checkout. Edit the file /etc/hosts and add "217.24.1.142  svn.madwifi.org" (without the quotes). I added it just after the 127.0.1.1 line

```
sudo gedit /etc/hosts
```

Now you can continue with the subversion checkout. You should probably remove this line from your hosts file when you're done with this so that if you want to go back there some day and they've moved it then DNS will give the most recent IP address.

this worked for me like a charm. i have this atheros card. 

```
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 15)
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

thank you very much reasoner.:D

---

### Post by Galena on 2009-03-04
I have an Acer Aspire 3680 running Atheros Aomm AR 242x 802.11abg.

I followed the instructions from reasoner and restarted. No wireless. I then thought is was because I had installed it using the files I had downloaded before so I cleaned it, removed the old installs and reinstalled madwifi. It is still telling me the network is unclaimed.

Any ideas on what could be going on.

---

### Post by Locke_99GS on 2009-03-04
I got my AR242x wifi working simply by disabling the current wireless, and installing the ath5k module from linux-backports-intrepid-generic. A reboot was involved, but it functions great now.

---

### Post by chrismcnally on 2009-03-07
> **reasoner said:**
> Thanks so much to those above for figuring this out for me. Let me spell out the installation in a little more detail to save those after me some time.



Thanks so much reasoner! This worked for my fresh Ubuntu install on the Thinkpad T500. One note to others, after a new install, if you have not yet you may need to run the command:

```
sudo apt-get update
```

before you can run any other apt-get installs required in this how-to.

---

### Post by SephirothsCraze on 2009-03-10
I can't thank you enough for this man. I've done this a few times and every time I do it I forget it lol. You're a life saver!

---

### Post by takegami on 2009-03-10
help ;) i have same model of aspire as in 1st post.. 

problem is - wifi card can't see all wireless networks..

couple hours ago, when windows was installed all was ok. now i can't see my access point. and: i have another notebook - and he still see my access point.. so - only i can't see it.. why it can be?

---

### Post by takegami on 2009-03-10
> **takegami said:**
> couple hours ago, when windows was installed all was ok. now i can't see my access point. and: i have another notebook - and he still see my access point.. so - only i can't see it.. why it can be?

damn. i don't know who of them are <censored>, but..
problem are solved..
after stupid loading and unloading working driver that included in Ubuntu, i'm tried to use madwifi.. and.. same problem.. strange.. stupid clicking and loading\unloading modules with various options.. nothing.. tried to scan for stations using wlanconfig.. same.. nothing.. BUT.. What the hell?! modules able to see only 11 channels! and my router are living on the channel #12.. damn :-)) 
changed channel on router.. all works fine..

---

### Post by MaLek on 2009-03-16
> **gabsik said:**
> **SUCCESS !**

3 ) Download:
```
svn co https://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6
```

the link didn't work !!!!
svn: OPTIONS of 'http://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6': could not connect to server ([http://svn.madwifi.org](http://svn.madwifi.org))

---

### Post by takegami on 2009-03-18
links works fine.
just replace madwifi.org with the madwifi-project.org in all old links.

---

### Post by Oglon3r on 2009-06-30
um which one of these should we try?

```
http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/
```

thanks

Im unable to get an ethernet cable wired to my dv7-1135nr so im downloading any packets on my windows partition saving and passing them via usb to my linux partition.

Ill bring some feedback if anything goes alright thank you much in advance

---

### Post by greymoose58 on 2009-07-02
I've been following this thread for a while. After trying pretty much every thing I could find on the web I upgraded from Intrepid to Jaunty and the wireless card worked flawlessly.
Just my 10 cents worth for those who want it.

---

### Post by Oglon3r on 2009-07-02
haha how the hell?!?! ill be dammed.... i made it after so many guides, failures and reboots ive finally made it!!!
ahem sorry im rly excited
Im running a Hp dv7-1135nr
check my signature for more of my lappy specs > <
thank you SOOOOO much mr reasoner

If dual booting 
this can be done without internet cable you just need to have a usb or sd card 
learn how to mount a usb drive here (same applies for sd cards etc etc)

```
http://www.novell.com/coolsolutions/feature/11637.html
```you also need to download the most current madwifi **hal** from the snapshot webpage.

```
http://snapshots.madwifi-project.org/
```untar it and install using this guide

if youre having trouble modifying your etc/modules/ do the following

```
echo ath_pci >> /etc/modules
```

that code will add ath_pci to ur /etc/modules automatically
confirm by using

```
vi /etc/modules

```

to confirm use iwconfig
Ive already rebooted several times and now im finally detecting wlan0
lulz now i just need to learn how to connect to my router > < ....
sorry i think i choose a not so noob friendly linux distro 
Thank you again everybody for your support have a great day!:p
:KS:KS:KS:KS:KS

---

### Post by Cloze on 2009-07-24
Hey!

The installation of this driver is successfull but i can't find any wirelless access points.

sudo iwlist ath0 scan:
ath0         No scan results

Remark: I had to manually put the interface up.
i did sudo ifconfig ath0 up and ifconfig wifi0 up

I am working on an Ubuntu 8.04 server. Has anyone got some ideas to troubleshoot my problem?

---

### Post by Oglon3r on 2009-09-04
How about just trying iwlist scan? you dont rly need to specify your device or just add a network manager gnome it will make it feel like windows conect to newtork wizard ^_^

---

### Post by Pengio on 2010-02-09
> **binbash said:**
> [http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

This worked beautifully!  Thank you.

I am new to Linux and was told Ubuntu was something I could probably handle with my level of computer knowledge, which is not much in my opinion.  The friend who recommended it has Fedora and had not tried Ubuntu, so I do not blame him, for he had heard the same thing.  I had tried quite a few different options to fix my wireless connection, including reasoner's, but to no avail.  I have very limited time I can physically link to the modem.  I was getting very VERY frustrated.  In fact, I was actually to the point I wanted Vista back. Yes, you heard me, Vista.  

My biggest issue was the internet connection.  Personally, that should be something that is already taken care of...straight from the box.  After all the searching and reading I did to fix this problem, my first and a pretty major problem, I am extremely sceptical of Ubuntu.  I would have un-installed Ubuntu a long time ago if I was not waiting on my Vista installation disc from HP.  I do understand it is just one problem and people can fix the problem on their own.  However, I see this is something that has been discussed for some time now, and for an OS that is aimed at the average person, possibly new to Linux, it does not feel very 'user-friendly'.  

I just thought I would share my views on this.  I am going to be a good sport and still give Ubuntu a chance.  I just hope it is not as hard to figure out the other programs and features.  Thank you Binbash...and thank you to all of you really; every little bit has helped me learn something.   ^_^

-Pengio

---

### Post by Pengio on 2010-02-10
Sorry to double post...

Anyway, I chose to upgrade, and am now using Ubuntu 9.10 Karmic Koala.  I had to fix the wireless card issues again and successfully accomplished it with the info supplied by Reasoner. It did not work on the the first reboot, but seems to be doing wonderful now after another reboot.  Just thought I would let people know how if fared on 9.10 (I had 9.04 Jaunty Jackalope previously).  

Thank you again,  ^_^

---

### Post by And1945 on 2010-04-24
I have an HP laptop with that wifi card, and no matter what I do, I can not seem to get it to work. I have tried 3 different guides, with no luck whatsoever.

Why is this such a pain in the a**?

Guides I tried:
[http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html)
[http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo)
[http://ubuntumanual.org/posts/185/install-atheros-ar242x-802-11abg-wireless-driver-in-ubuntu](http://ubuntumanual.org/posts/185/install-atheros-ar242x-802-11abg-wireless-driver-in-ubuntu)

PLEASE Ubuntu developers, make this wifi hell end. I beg of you.

---

### Post by bellial on 2011-06-13
Hi guys, I'm having trouble setting up an access point too, and figured I'd put my worries here. So my teacher said that the AP would only work properly on hardy, it's a desktop, btw, and a pretty old one. So I installed it fine, no problems, and started following this how to : [http://ubuntuforums.org/showthread.php?t=376283](http://ubuntuforums.org/showthread.php?t=376283), with help from here: [https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint](https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint), and at some point I have to restart the pc, it never comes back! When it happened the first time I formatted and started all over again, but then it happened again, what could be happening? It halts for a long time on the Starting services part, in the "Starting Hardware abstraction layer hald" to be exact, and then it shows "ata 3.00: exception Emask 0x0 Sact 0x0 SErr 0x0 action 0x2 frozen
ata3.00 status: {DRDY}

Along the lines I noticed that Starting domain name service...bind shows as failed. Could this be me messing with network services or just a case of crappy computer? 
Thanks!

I forgot to mention that my card supports master mode and that in all it should be working!

---

