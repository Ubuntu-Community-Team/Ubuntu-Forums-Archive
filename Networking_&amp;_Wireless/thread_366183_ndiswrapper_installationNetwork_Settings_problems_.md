---
title: "ndiswrapper installation/Network Settings problems for wireless on Edgy"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by mt granny on 2007-02-20
I have been struggling w/ 2 linux books and my 25 years of general computer knowledge and can't get my newly installed Ubuntu 6.10 (Edgy) OS (on "PC 2") to connect to the Internet via the USB Linksys (wirelesss) adapter to the DSL gateway (wired ethernet) installed on the Windows XP PRO on "PC 1". Ubuntu is now the only OS on "PC 2"- before the Ubuntu Install I was running Windows XP PRO and it connected to the Internet through the USB Linksys wireless adapter using a wireless connection through "PC 1".  There is no modem installed in "PC 2" and it is located on a second story so a wired connection to PC 1 is not feasible. 
I have searched hundreds of posts and tired various solutions over the past week but am now more confused then ever. Yesterday I used my Windows connection on PC 1 to download the ndiswrapper (1.37.tar) and latest Linksys driver (WPC54G_driver_utility_1.3.1) for Ubuntu to a USB thumb drive. I can read the contents of the USB drive on Ubuntu's desktop (PC 2), "copy and paste" it to my home folder and even have successfully extracted them. I can't get the Synaptic Program Manager to find the file(s) to install them. I also tried using an APT command from a terminal window but it says that ndiswrapper is not in the root directory and I can't figure out how to accomplish that. 

Finally, I'm still struggling a bit filling in the Network Setting boxes. It displays choices for activating Wireless, Ethernet, and Modem. I would be very grateful if someone could take me through this in detail. My "PC 1" uses a gateway router to connect to the Internet through a DSL line and also tp establish a LAN (home network) that connects my other PC and laptop. Do I use PC 1's primary and secondary IP addresses somewhere in Ubuntu's network settings? 
Do they go in the IP Address, the Subnet mask, or the Gateway address? 
Under the Host Settings tab is Host name: ubuntu1 (this is the name I gave it upon installation). Do I leave that as is? In the The Domain name: (currently blank) I have tried the name of my Windows Home Network, my ISP provider and the ISP address. What should I put in here? What goes in the DNS tab/Location box? What about the Search Domains box? 

Thanks in advance for any assistance you can offer to me. Sandi (Montana Granny):confused:

---

### Post by d.j.schroeder on 2007-02-20
I had the same problem which is now solved.  I suggest a different approach.  My experience is with 6.06, hopefully it will apply.

Don't use the ndiswrapper you downloaded and transferred, just delete it.  Put the 6.10 install disk back in the drive.  Then open up the synaptic package manager and add the CD itself to the repositories.  Then you can use the package manager to install the ndiswrapper-utilities package automatically.  Then follow the steps you had planned to use before to use ndiswrapper.

---

### Post by OldGaf on 2007-02-20
>  I can't get the Synaptic Program Manager to find the file(s) to install them. I also tried using an APT command from a terminal window but it says that ndiswrapper is not in the root directory and I can't figure out how to accomplish that. 

I think I see what you are doing here...... you cannot use Synaptic or APT to install the drivers or ndiswrapper you downloaded. 

You did the right thing by extracting the drivers and you do need to have ndiswrapper in your home folder (or the desktop)

Follow these instructions (substituting your driver ver and paths etc.) and it should work for you.

> 1.Make sure you have the headers:
sudo apt-get install linux-headers-`uname -r`

2.Grab the latest version of Ndiswrapper: 
[http://sourceforge.net/projects/ndiswrapper](http://sourceforge.net/projects/ndiswrapper)

3.Go to the downloaded file and extract it:
tar -zxvf ndiswrapper-version.tar.gz

4.This will create the ndiswrapper-version directory. Change to that directory:
cd ndiswrapper-version

5.Once in the source-directory run:
make distclean

6.Then run:
make

7. making sure you are still in the source-directory, As root, run:
make install

8. Then run the following to install the drivers (put in the full path)
ndiswrapper -i filename.inf


(Example below for DWL-132)

$ ndiswrapper -l 

Installed ndis drivers:
neta5agu                driver present, hardware present

$ lsusb
Bus 005 Device 005: ID 2001:3a02 D-Link Corp. [hex]
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 003: ID 0a5c:3535 Broadcom Corp.
Bus 001 Device 004: ID 0a5c:200a Broadcom Corp.
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 002: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 002 Device 001: ID 0000:0000


$ ndiswrapper -d 2001:3a02 neta5agu
$ ndiswrapper -m 
$ sudo depmod -a
$ sudo modprobe ndiswrapper

---

### Post by OldGaf on 2007-02-20
> **d.j.schroeder said:**
> I had the same problem which is now solved.  I suggest a different approach.  My experience is with 6.06, hopefully it will apply.

Don't use the ndiswrapper you downloaded and transferred, just delete it.  Put the 6.10 install disk back in the drive.  Then open up the synaptic package manager and add the CD itself to the repositories.  Then you can use the package manager to install the ndiswrapper-utilities package automatically.  Then follow the steps you had planned to use before to use ndiswrapper.

I have to say that I have had much better success with 1.37. The packages in the repos' are only 1.18 and they did not work for the two diff. USB nics I have now.

---

### Post by mt granny on 2007-02-26
I was able to work on this over the weekend and am pleased to say that I was able to get the Internet connection up and running. I thought it best to use the downloaded ver of ndiswrapper since I had trouble finding it on the CD version (I got from a friend). What a difference a bit of help makes! Thanks again

---

