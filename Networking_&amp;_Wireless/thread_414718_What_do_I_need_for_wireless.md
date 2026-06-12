---
title: "What do I need for wireless?"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by Mb0742 on 2007-04-20
I have a dlink DWL-G510 chip and I am running Ubuntu 6.10.

Oh and I tried the ndiswrapper package because thats what I thought I needed but that didn't seem to help....

---

### Post by AAM on 2007-04-20
Hi Mb0742

Thanks for contacting the forum for help. Can you tell us a bit more about the problem and what you have done. Do you know the chipset for your device? What commands did you use to invoke ndiswrapper?

And most important, have you sacrificed 4 chickens, 2 cows and 1 chimpanzee before starting? (just kidding, animal sacrifices no longer required!) But it would be helpful to have some more information about the problem.

Another question that might seem irrelevant, but where are you with your system? Have you just installed Ubuntu 6.10 or have you been running it for a while?

Waiting to hear back,

AAM

---

### Post by AAM on 2007-04-20
I have done some searching and found the following on the ndiswrapper website

> # Card: D-Link DWL-G510

    * Chipset: Marvell W8300
    * pciid: 11ab:1fa6
    * Driver: [91]
    * Driver: The asus driver hasn't worked for me. Instead, I used the WinXP driver on the CD. Its available at [ftp://ftp.dlink.com/Wireless/dwlg510/Drivers/dwlg510_driver_100.zip](ftp://ftp.dlink.com/Wireless/dwlg510/Drivers/dwlg510_driver_100.zip)
    * Other: Works with WEP and WPA with TKIP cipher. May need iwpriv wlan0 ndis_reset when changing essid.
    * Other: Dlink driver has worked fairly stable on ndiswrapper 1.2 but is rock solid on ndiswrapper 1.5, at least for me. This was tested on Arch Linux, kernel 2.6.11 up to 2.6.14, SMP, PREEMPT, Pentium3, default stack settings. ndiswrapper 1.4 OOPses and locks hard, unstable, even with uniprocessor kernel. Only WEP was tested.
    * Other: I use this card under ndiswrapper 1.2 on a gentoo 2.6.12 kernel without problem. See this thread. [[http://ndiswrapper.sourceforge.net/forums/viewtopic.php?t=482&highlight=link]](http://ndiswrapper.sourceforge.net/forums/viewtopic.php?t=482&highlight=link]) One thing: if the network goes down, rmmod ndiswrapper FAST and reinsert it to prevent a kernel panic. Only tested with 1.2. 

# Card: D-Link DWL-G510 (Rev B)

    * Chipset: Atheros
    * pciid: 168c:001a
    * Driver: Version 1.0, Provided on CD. Version 2.11 from dlink.com also works.
    * Other: only WEP tested, works fine on 2.6.9 and 2.4.27. The short-named .conf file symlink was pointing to the wrong long-named .conf file - fixed manually. 



So it seems we need to know whether you have a plain or Rev B card also.

AAM

---

### Post by Mb0742 on 2007-04-20
Sadly I am super foreign Australia-Korea -_- And I am running Rev c. I have installed Ubuntu 6.10 by the way. And I have followed all the steps for the included drivers for Ndiswrapper on the rev c drivers however I get up to the bit where it says I need to add this to run in the help files

First of all it says it can find my driver and device secondly I get to the bit where it says something like modprobe ndiswrapper -a and that gives a fatal error saying invalid arguement.

---

### Post by sandyfrench on 2007-04-20
Hi there,
It looks like I have the same wireless card as you ( I'm in NZ ) DWL-G510 Ver C2, and I couldn't get it to work either under 6.10. I installed feisty this morning, and it is detected just fine. Now all I have to do is figure out how to sort out my network...:confused:

---

### Post by AAM on 2007-04-20
Mb0742,

where are you in Oz? near me? just in case you were interested in a LUG group!

I was asking about where you are with installation, because I was going to suggest what *sandyfrench* has done, i.e., put the card in AND THEN INSTALL (emphasis not shouting!). The card may be recognised and the right drivers then loaded with the install. Took me a long time to learn this although Kanotix could do it 2 years ago. You may not need ndiswrapper at all.

Ndiswrapper usually works well if you get the commands right. You may also need to blacklist some of the Ubuntu drivers which are loaded when you boot and put the device in to prevent conflicts. This means running **lsmod** in the terminal and then scouring through the entries to find those that refer to wireless drivers. If you run **lsmod** before and after connecting the card, you can probably assign the differences to the wireless driver. These are then blacklisted in /etc/modprobe.d/blackist.

The ndiswrapper commands are fairly straightforward by themselves and have been listed here before numerous times:
> 
sudo nidiswrapper -i windowdriverfile.inf *(make sure you have all the Windows files in the one directory because the INF file refers to SYS file/s that must be present)*
sudo modprobe ndiswrapper
sudo depmod -a
sudo modprobe -m

*plug in the device*

ndiswrapper -l

*[there should be a driver and device listed as present]*

sudo gedit /etc/iftab *(add your MAC)*

sudo gedit /etc/modules *(add ndiswrapper)*


then you just have to configure the network. Good luck! But try the re-install path first.

---

### Post by Mb0742 on 2007-04-20
> root@mb0742-desktop:~# iwlist wlan0 retry
wlan0     Fixed limit    ;  min limit:0
                            max limit:255
          
root@mb0742-desktop:~# iw
bash: iw: command not found
root@mb0742-desktop:~# iwlist
Usage: iwlist [interface] scanning
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] key
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event
root@mb0742-desktop:~# iwconf
bash: iwconf: command not found
root@mb0742-desktop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"Home"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          
sit0      no wireless extensions.

root@mb0742-desktop:~# iwconfig wlan0 restricted
Error : unrecognised wireless request "restricted"
root@mb0742-desktop:~# iwconfig wlan0 key restricted
root@mb0742-desktop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"Home"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          
sit0      no wireless extensions.

root@mb0742-desktop:~# 


The only problem is that I do have a encryption it is 64 bit (5chars) and for the sake of it lets just say my pword is chess ;) So I just need to know how to add the pword then how to access it, it now fully scans and finds the Essid :)

> 
where are you in Oz? near me? just in case you were interested in a LUG group!

I wish I were we would be great friends plus then there would be a great chance of us hosting a LAN party Vic doesn't seem to have any -_-

---

### Post by AAM on 2007-04-20
Vic is OK, better football than anywhere else. Used to play fullback! Go the 'Pies!

You should hunt around for the correct instructions but you can get your access parameters in with something like:

iwconfig wlan0 essid NAME key TheEntireKeyStringInCharacters

But there are other things required also. You'll need to do some more searching. Many listers suggest taking the encryption off the wireless until you are connected. makes sense and is not likely to cause you problems.

---

### Post by Mb0742 on 2007-04-20
I just get an invaild arguement "pword"

---

