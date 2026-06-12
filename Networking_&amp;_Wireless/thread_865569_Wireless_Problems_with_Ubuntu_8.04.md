---
title: "Wireless Problems with Ubuntu 8.04"
date: 2008-07-20
forum: Networking &amp; Wireless
---

### Post by theturbanator on 2008-07-20
Hi everyone,

I've been trying for a few weeks now to connect to the Internet on Ubuntu 8.04, which I have installed inside of Windows.  I have a Dell Vostro 1400 with the Windows Vista OS.  Running the lspci command in the terminal outputs: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01) as my Network Controller.  I have followed many instructions, but none of them have worked, so I reinstalled Ubuntu and tried this from scratch:

1. install ndiswrapper from these two packages:
[http://ubuntu.secs.oakland.edu/pool/main/n/ndiswrapper/ndiswrapper-common_1.50-1ubuntu1_all.deb](http://ubuntu.secs.oakland.edu/pool/main/n/ndiswrapper/ndiswrapper-common_1.50-1ubuntu1_all.deb) and [http://ubuntu.secs.oakland.edu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb](http://ubuntu.secs.oakland.edu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb)

2. download the alternate Windows driver files from
burnthesorbonne.com/files/alternate_driver.tar.gz and put it on your desktop in Ubuntu.

3. now run these commands (same as before; only difference is that we're installing a different version of the Windows drivers this time) -- I tried it with the other drivers as well.

&#65279;cd ~/Desktop
tar -xzvf alternate_driver.tar.gz
cd alternate_driver

sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -m

The ndiswrapper -l command returns the following output:
bcmwl5: driver present
      device(14E4:4311) present
            (alternate driver: ssb).

Blacklisting b43, b43legacy, and ssb in the /etc/modprobe.d/blacklist file results in, after a reboot, the option for wireless configuration not even showing up, whereas at least the option showed up before blacklisting, so I removed those lines from the file.

I don't know what to do from here... is the problem that ndiswrapper won't work because of the fact that I may be using 32-bit Windows drivers on a 64-bit Linux kernel? I don't think my kernel is 64-bit...

OH YEAH, and one major point of mention: I cannot connect to the internet when I boot into Ubuntu at all because I cannot connect via Ethernet cable due to a hardware problem with my Ethernet port.  So I have to download all my packages from the Windows side and move them over to the Linux side.

I would really appreciate some help on solving this problem!  Thanks!

---

### Post by superprash2003 on 2008-07-20
what output do you get when you type iwconfig in your terminal

---

### Post by theturbanator on 2008-07-20
Hi,

The output to the iwconfig command is:

lo no wireless extension
eth0 no wireless extension
wmaster0 no wireless extension
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by pytheas22 on 2008-07-21
The command:
```

uname -m
```

should tell you what kind of kernel you're using (32-bit or 64-bit).  If it says i686, it means 32-bit; I think it would say amd64 for 64-bit.  Which is it?

---

### Post by theturbanator on 2008-07-21
Hi, the uname -m command outputs:
i686

---

### Post by rogier.de.groot on 2008-07-21
You just blacklisted ssb and the other modules? That *may* not always work...
Try what happens after the following commands:
sudo rmmod ndiswrapper
sudo rmmod ssb
sudo modprobe ndiswrapper
(now wait a while for the system to catch on & try your wireless)

---

### Post by theturbanator on 2008-07-21
Hi everyone, thank you so much for all of your help.

Rogier, thank you for those commands:  I am writing this post connected to the internet from the Ubuntu OS!

One point of concern:  Whenever I reboot into Ubuntu, it does not automatically load ndiswrapper;  I have to type in the three commands that rogier gave me before Ubuntu recognizes the wireless networks in the area.

Is there a way to make this permanent so that I don't have to do this every time?  Of course, I could always just write a shell script, "ConnectToInternet.sh", but if there is a way, I would appreciate your letting me know!

Thank you to all.

---

### Post by theturbanator on 2008-07-21
I tried using the following command:

echo 'ndiswrapper' | sudo tee -a /etc/modules

This loaded ndiswrapper automatically, but nonetheless, Ubuntu only recognized wireless networks once I did the three commands...

---

### Post by rogier.de.groot on 2008-07-22
The 'ssb' module may actually be loaded by your 'initrd' image, it was in mine; that's why blacklisting it didn't work for me. There's some make-init-something command which fixes/update the 'initrd' image, just type "sudo make-init" and press tab for autocompletion, that should do the trick. And you might want to check if /etc/modprobe.d/ndiswrapper exists (which is what loads the ndiswrapper module at boot time).

P.S. You can thank people who helped using the 'thanks' button (yellow star thing on the bottom-right of posts)

---

### Post by theturbanator on 2008-07-22
Hi Rogier, it turns out that I didn't need the last few commands you gave me; this time when I booted into Ubuntu, the wireless automatically loaded.... so the command that I said didn't work two posts earlier actually does, I guess.

Thank you to everyone who helped me; I will try this "Thanks" button...

---

### Post by theturbanator on 2008-07-22
Hi everyone... I just wanted to provide a summary of what I did to make wireless work in Ubuntu that runs from inside Windows Vista on my Dell Vostro 1400. I have a Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01) Network Controller. I had no access to the internet due to a hardware problem with my ethernet port.
These are the instructions I followed:
 
1. install ndiswrapper from these two packages:
[[COLOR=#000000]http://ubuntu.secs.oakland.edu/pool/...buntu1_all.deb[/COLOR]]("http://ubuntu.secs.oakland.edu/pool/main/n/ndiswrapper/ndiswrapper-common_1.50-1ubuntu1_all.deb") and [[COLOR=#000000]http://ubuntu.secs.oakland.edu/pool/...untu1_i386.deb[/COLOR]]("http://ubuntu.secs.oakland.edu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb")
 
2. download the alternate Windows driver files from
burnthesorbonne.com/files/alternate_driver.tar.gz and put it on your desktop in Ubuntu.
 
3. now run these commands:
&#65279;cd ~/Desktop
tar -xzvf alternate_driver.tar.gz
cd alternate_driver
 
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -m
 
4. blacklist b43, b43legacy, and ssb in the /etc/modprobe.d/blacklist file
 
5. now run these commands:
sudo rmmod ndiswrapper
sudo rmmod ssb
sudo modprobe ndiswrapper
(now wait a while for the system to catch on & try your wireless) 
 
6. to make sure that the ndiswrapper module is automatically loaded when Ubuntu is first started:
echo 'ndiswrapper' | sudo tee -a /etc/modules
 
After a few restarts, wireless networks should automatically appear as soon as Ubuntu comes up...
 
Problem solved.

---

