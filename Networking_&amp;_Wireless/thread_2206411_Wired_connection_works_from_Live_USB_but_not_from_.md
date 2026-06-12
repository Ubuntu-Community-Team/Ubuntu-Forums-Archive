---
title: "Wired connection works from Live USB but not from HDD"
date: 2014-02-18
forum: Networking &amp; Wireless
---

### Post by paul100 on 2014-02-18
Hello, this is my first time working with Linux. I had an old laptop, a Dell Inspiron E1505, that I wasn't using, so I thought I'd install Ubuntu 12.04 LTS over the existing OS, Windows Vista. I'll start from the beginning, just so you have all the info.

I couldn't get Ubuntu to boot from a Live CD, so I went the USB route which worked great. Great, except I couldn't get the WIFI to connect to my network. I figured it was probably a driver problem. So I figured I'd connect to the internet via a wired connection and worry about the driver issue after the install was finished. Well, the wired connection worked great while booted from the USB, and still does when I boot from the USB, but I can't get the wired, or wireless, connection to work when it boots from the HDD. Any ideas, how to get the wired connection working? And after that, was I right in assuming its a driver problem causing my wireless not to work?

Thanks, 
Paul

---

### Post by papibe on 2014-02-18
Hi paul100. Welcome to the forum ):P

Could you open a terminal run this commands and post back its results? (you can copy paste the output):
```
sudo lshw -C network

lspci -nnk | grep -iA2 eth

ifconfig

route -n

nm-tool 

cat /etc/network/interfaces
```
Regards.

---

### Post by paul100 on 2014-02-18
Hi! Here are the results...

stitchme2gether@StephsOldLaptop:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=wl latency=0
       resources: irq:16 memory:dfdfc000-dfdfffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
       resources: memory:df9fe000-df9fffff




stitchme2gether@StephsOldLaptop:~$ lspci -nnk | grep -iA2 eth
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Dell Inspiron 6400 [1028:01af]
	Kernel modules: b44




stitchme2gether@StephsOldLaptop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9184 (9.1 KB)  TX bytes:9184 (9.1 KB)




stitchme2gether@StephsOldLaptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface




stitchme2gether@StephsOldLaptop:~$ nm-tool


NetworkManager Tool


State: asleep


stitchme2gether@StephsOldLaptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by papibe on 2014-02-19
Thanks.

What happens if you do try to re load the ethernet module (with the cable connected):
```
sudo modprobe b44
```
Also, is there any additional driver offered when you open 'Additional Drivers'?

Regards.

---

### Post by paul100 on 2014-02-19
No additional drivers listed

When I input the sudo command, it just asks for my password, then nothing. Cursor is blinking, but no command prompt.

---

### Post by papibe on 2014-02-19
Let's see if there's a block. Could you post the result of this command:
```
rfkill list
```
Regards.

---

### Post by paul100 on 2014-02-19
That command appears to do nothing.

---

### Post by fdrake on 2014-02-19
are you sure ? check the spelling

---

### Post by paul100 on 2014-02-19
Yep, I entered it 3 times...rfkill list...nothing.

---

### Post by paul100 on 2014-02-19
Anyone else have any ideas?

---

### Post by chili555 on 2014-02-19
I have a pretty good idea; I've seen tis exact problem a few hundred times. Please hook up the ethernet. Open a terminal and do:```
sudo modprobe b44
```When it asks for your password, enter it and press Enter. For security reasons,your password is not echoed back and not even *** but if it is correct, it will be accepted. If not, you will get this:```
chili@Think410:~$ sudo modprobe b44
[sudo] password for chili: 
Sorry, try again.
[sudo] password for chili:
```Once the command is accepted, your wired ethernet will be working. Then do:```
sudo apt-get update
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
```After everything is done, detach the ethernet, reboot and everything should be working as expected. Of course, post back if you get stuck.

---

### Post by paul100 on 2014-02-19
Hmm, someone earlier suggested just that, but the sudo command yielded no results. It asked for and accepted my password, but the cursor just kept blinking at the far left with no command prompt. I let it sit for a few minutes thinking it was doing something but nothing changed. When I attempted to close the terminal, got a message saying a process had been started and closing the terminal would cancel it. So I let it sit for a few more minutes and nothing happened.

---

### Post by chili555 on 2014-02-19
Please reboot and try again. If it happens again, open a terminal and run:```
top
```See if you have a process that's runaway; that is using 80-90-100% of your CPU cycles. Jot down the result and tell us. Get out of 'top' with q.

---

### Post by paul100 on 2014-02-19
Rebooted with same results. Tried the top command, no process using more than 1% of CPU. Did a reinstall and nothing has changed. Any more suggestions? By the way, I really appreciate you guys trying to help. Thanks!

---

### Post by chili555 on 2014-02-19
You needn't have an ethernet connection for this. Please try:```
sudo apt-get purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```Post back any errors, warnings, etc. If none, reboot and do:```
sudo modprobe -v b44
```Don't make my fly over there and take your laptop apart!

---

### Post by paul100 on 2014-02-19
I'll try that when I get a chance, thanks! Another thing thats odd...Ubuntu won't shut down properly. It gets to a screen that just says Ubuntu, with 5 dots that blink and just stays there.

---

### Post by paul100 on 2014-02-19
Here's what I have so far...right now the terminal screen is just sitting with a blinking cursor and no command prompt



stitchme2gether@StephsOldLaptop:~$ sudo apt-get purge bcmwl-kernel-source
[sudo] password for stitchme2gether: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 14 not upgraded.
After this operation, 3,668 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 145846 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.11.0-15-generic

---

### Post by fugu2 on 2014-02-19
try
 ```
reset && clear
```
 to reset the terminal and try and get your cursor back
also 
```

echo $PS1

```
this is how your command promt get styled and should be something like
\[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}\u@\h:\w\$

can you also try a
```
ifconfig -a

```
this will list all of the wired and wireless interfaces that your couputer 
currently recognizes,even the ones that are down right now

---

### Post by paul100 on 2014-02-20
okay, I just decided to install 13.10 instead and see what happens. I went through all the above steps again and nothing seemed different until I got to the "purge bcmwl-kernel-source" command. It finished this time and gave me a command prompt. I then entered in the next part, "sudo rm /etc/modprobe.d/blacklist-bcm43.conf", but got the message that there is no such file or directory

---

### Post by paul100 on 2014-02-20
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12656 (12.6 KB)  TX bytes:12656 (12.6 KB)

---

### Post by paul100 on 2014-02-20
by the way, here are the results of 'ifconfig -a'


lo
        
Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12656 (12.6 KB)  TX bytes:12656 (12.6 KB)




Thanks again, guys!

---

### Post by paul100 on 2014-02-20
update...alright, I got the wired connection working. after running the '[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get purge bcmwl-kernel-source' command, I unplugged the ethernet cable and rebooted. When Ubuntu was loaded, I plugged the ethernet cable back in and Voila!! Thank you guys! Now on to getting the wireless to work properly...any suggestions there?[/FONT][/COLOR]

---

### Post by fugu2 on 2014-02-20
you might want to take a look here, but I can't vouch for this at all
```
http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers-bcm43xx
http://wireless.kernel.org/en/users/Drivers/b43

```and I suspect that the wifi drivers are the same as your ethernet ones, so by trying to fix the wifi theres always a chance you can lose the ethernet again :(

---

### Post by varunendra on 2014-02-20
> **chili555 said:**
> I have a pretty good idea; I've seen tis exact problem a few hundred times.
Maybe you forgot a zero sir.. :lolflag:

> **paul100 said:**
> Now on to getting the wireless to work properly...any suggestions there?
Now that the cake is ready, let me have the privilege to put the cherry on it. Please run the following command in a terminal, while you are connected to internet via cable -
```
sudo apt-get install linux-firmware-nonfree
```
Then either reboot or manually (re)load the driver -
```
sudo modprobe -rv b43
sudo modprobe -v b43
```

Party time?

---

### Post by Scott_Hagin on 2014-02-22
fugu2 and Varun ... I don't know about paul100, but I'm partying!!! Thank you for the great instruction and willingness to share. My problem was EXACTLY the same as Paul100 described (down to the eternal Ubuntu screen at shutoff) and now I'm in Ubuntu 12.04 bliss with my Dell Inspiron E1405.

---

### Post by paul100 on 2014-02-22
Yes!! Party time indeed!! I tip my hat to you, sir. Worked perfectly! Thank you!!

---

