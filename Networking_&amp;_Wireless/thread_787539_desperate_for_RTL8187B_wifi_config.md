---
title: "desperate for RTL8187B wifi config"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by scholzilla on 2008-05-09
I did my due diligence by researching this issue on various posts and wikis, but can't get my wifi to work. In brief, I'm running Hardy Heron on a gateway laptop (64bit) that uses the RTL8187B chipset, which is on the list of supported chipsets. I used ndiswrapper to install the chipset [recommended here]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek"). Then I checked for installation:

matt@Darwin:~$ ndiswrapper -l
net8187b : driver installed
	device (0BDA:8187) present (alternate driver: rtl8187)

which looks promising, but I see nothing via network manager. I tried going through the [ubuntu help wiki]("https://help.ubuntu.com/8.04/internet/"), but can't get past step 1. Unfortunately, the doc is written as a series of "if then" statements without any corresponding "else" statements...very irritating. Device Manager makes no mention of wireless hardware present. I have gotten wireless previously on this computer (never dependably) so I trust that the hardware is installed. Notably, I also get this:

matt@Darwin:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

likewise, sudo lshw -C network does not list the driver.

If there is no easy solution to this problem, can someone please recommend some sort of external wifi device I can use.

---

### Post by monkeylin on 2008-05-09
You need to install the win 98 drivers from the realtek [website]("ftp://210.51.181.211/cn/wlan/RTL8187B_driver_only.zip"), and don't forget to add "blacklist RTL8187B" in (sudo gedit /etc/modprobe.d/blacklist) and add ndiswrapper to the modules(echo "ndiswrapper" | sudo tee -a /etc/modules), it worked on my gateway t1620. how to, go  [here]("http://ubuntuforums.org/showthread.php?t=771894&highlight=install+ndiswrapper+wireless+drivers+newbies").

im using Hardy Heron(32bit)

Good luck!

---

### Post by treymul on 2008-05-09
You can also use a patched driver found here :  [http://www.datanorth.net/~cuervo/rtl8187b/]("http://www.datanorth.net/~cuervo/rtl8187b/")

---

### Post by scholzilla on 2008-05-09
Thanks for the replies. I haven't tried the patch yet, treymul, but I wanted to follow up with monkeylin's suggestions. First, I already did install the driver and just misspoke in my original post when I said I installed the chipset. 

I did follow your instructions to: "add "blacklist RTL8187B" in (sudo gedit /etc/modprobe.d/blacklist)" but have a question about syntax. The actual driver file is called net8187b.inf, though the chipset is listed at realtek as RTL8187B. Which is the correct name to use RTL8187B or net8187b? I've tried both, but haven't gotten anything to work. 

Second question: when I type ndiswrapper -l I get the output:

net8187b : driver installed
device (OBDA:8187) present (alternate driver: rtl8187)

yet when I use dmesg I get a lot of lines of output that say "ndiswrapper (import:242): unknown symbol: blablabla" followed by a message that says:

ndiswrapper (load_sys_files:210): couldn't prepare driver 'net8187b'
ndiswrapper (load_sys_files:112): couldn't load driver net8187b; check system log for messages from 'loadndisdriver'
usbcore: registered new interface driver ndiswrapper
lp: driver loaded but no devices found

finally, even after restart <sudo lshw -C network> does not list the driver


sooo...I'm getting output saying the device is installed and loaded from <ndiswrapper -l>, output from <dmesg> that says the driver can't be prepared and loaded, and contradictory output from <dmesg> that says the driver is loaded but not devices are found. Arghh!

---

### Post by treymul on 2008-05-09
I think I had problems like that when I tried ndiswrapper.  Try removing both drivers for the card with ndiswrapper and then install only the win98 driver.

---

### Post by treymul on 2008-05-09
forgot to mention you will need to modprobe ndiswrapper when you finish.

---

### Post by prshah on 2008-05-09
> **scholzilla said:**
> 
matt@Darwin:~$ ndiswrapper -l
net8187b : driver installed
	device (0BDA:8187) present (alternate driver: rtl8187)


That's great! Now give the command ```
sudo modprobe ndiswrapper
``` and iwconfig will now show you your wireless activated! 

Edit: If it doesn't show, you may need to blacklist the rtl8187 module by adding the below line to your "/etc/modprobe.d/blacklist"```

blacklist rtl8187
```, then save and exit.

Unfortunately the above code requires a restart.

Why not try my step-by-step guide ([http://ubuntuforums.org/showthread.php?t=756260](http://ubuntuforums.org/showthread.php?t=756260)) to set up your wireless network card? If you run into any problems, post back which step you are stuck at. There's no if..else; it just grabs you by the nose and leads you around. The second part of the above post will also show outputs.

---

### Post by scholzilla on 2008-05-09
rtl 8187 is already blacklisted and I already ran modprobe and restarted. That doesn't help, unfortunately. I just tried uninstalling both drivers and reinstalling just the net8187b driver. Strangely, the native rtl8187 driver reappears, even though it is blacklisted. My errors remain the same (see above).

thanks

---

### Post by prshah on 2008-05-09
> **scholzilla said:**
> rtl 8187 is already blacklisted and I already ran modprobe and restarted. 

You shouldn't restart after running modprobe; modprobe loads the ndiswrapper module, and then restarting it simply means that ndiswrapper is not loaded.

What modprobe command have you given, exactly? And rtl8187 module should not load if properly blacklisted; can you post your /etc/modprobe.d/blacklist file contents?

---

### Post by scholzilla on 2008-05-09
I worded that poorly. In short, though, starting modprobe with 

sudo depmod -a
sudo modprobe ndiswrapper

and then checking dmesg does not yield the desired output that ndiswrapper loaded. Instead it gives the output I listed above.

Basically, I'm following the instructions [given here]("http://ubuntuforums.org/showthread.php?t=771894&highlight=install+ndiswrapper+wireless+drivers+newbies"), if you need more info. I've decide to post on that thread as well. Unfortunately, I can't send you the exact file for /blacklist because I don't have a wired connection to put the laptop on. I'm using another computer to access internet. That being said, I simply have a line that says: 

blacklist rtl8187

at the end of the /blacklist file. No quotes or anything...it's written just like that. I agree that this alternate module should not show up, but it does nonetheless. Thanks.

---

### Post by prshah on 2008-05-09
> **scholzilla said:**
> 
sudo depmod -a
sudo modprobe ndiswrapper


did you earlier give the command ```
sudo ndiswrapper -m
``` to "modularize" ndiswrapper?

---

### Post by scholzilla on 2008-05-09
Yes, I did try that, even though according to the link cited in my last post, dmesg should output:

ndiswrapper version "my version" loaded

*before* modularizing, and it doesn't. Doesn't do it before and doesn't do it after. I think the solution lies somewhere in that dmesg output, but I don't know how to interpret it. 


thanks again for your persistence

---

### Post by liviubero on 2008-05-11
Hy there are more hints about ndiswrapper here:
[https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteL40-14N](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteL40-14N)
The interesting part of that page is this one:

[COLOR=Navy]change to Win98 directory in the unzipped driver
run "sudo ndiswrapper -i net8187b.inf"
check with "ndiswrapper -l" that the driver is listed as installed
run "[COLOR=Red]sudo ndiswrapper -a 0bda:8197 net8187b[/COLOR]" (this forces the driver to recognize this specific chipset)
run "modprobe ndiswrapper"[/COLOR]

It works for me, although my rtl8187 doesn't connect to every access point, even if the wifi network isn't encrypted.
In the command "ndiswrapper -a  0bda:8197 net8187b" one should replace 0bda:8197 with the id of your rtl-thing as it is shown by lsusb, although it should be the same.
Hope it helps...

---

### Post by scholzilla on 2008-05-11
Thanks. I'll check the link you sent me, but when I try these commands:

matt@Darwin:/wifi$ lsusb
Bus 003 Device 010: ID 0bda:8187 Realtek Semiconductor Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
matt@Darwin:/wifi$ sudo ndiswrapper -i net8187b.inf
driver net8187b is already installed
matt@Darwin:/wifi$ sudo ndiswrapper -a 0bda:8187 net8187b
Driver 'net8187b' is already used for '0BDA:8187'
matt@Darwin:/wifi$ modprobe ndiswrapper


I still don't see anything.

---

### Post by liviubero on 2008-05-12
Hmmm, try to ndiswraper -r net8187b and then to install it and associate it with the id number of the card.

---

### Post by scholzilla on 2008-05-12
here's what I get with that:

matt@Darwin:~$ ndiswrapper -r net8187b
couldn't delete /etc/ndiswrapper/net8187b: Inappropriate ioctl for device


thanks.

and btw, I don't know if this is normal, but under the Advanced tab in the BIOS menu, the wireless option is "greyed out" with the word [Restore] written next to it instead of the [Enabled] setting next to other devices in the same menu.

---

### Post by Cphood on 2008-05-12
Toshiba A215-5802 rtl8187b wireless paired with Linksys54GL w/dd.wrt program. Ubuntu Hardy 8.04 dual boot w/Vista.

Thanks for your post.  It got me up and running with wpa2 without issue.

My footprint

I installed the ndiswrapper files from the Synaptic package.

Downloaded the Realtek driver from [ftp://202.65.194.212/cn/wlan/RTL8187B_driver_only.zip](ftp://202.65.194.212/cn/wlan/RTL8187B_driver_only.zip) 

Right clicked the file and extracted it to desktop.

Used "System - Adminstration - Windows Wireless Drivers" application to install the Windows98 file "net8187.inf"

The install window reported "Hardware present: no"

Ran "sudo ndiswrapper -a 0bda:8197 net8187b" in terminal. Note: 0bda is Zerobda

Hardware present: yes, but still no connection.  After a couple of shut downs and an exercise in Vista I went back to Ubuntu and the network manager recognized my network with wpa2 security.  Selected the Network, entered my security code, selected "connect" and got 4 bars. Have had a couple of shutdowns and start-ups without issue.

---

### Post by liviubero on 2008-05-13
> **scholzilla said:**
> here's what I get with that:

matt@Darwin:~$ ndiswrapper -r net8187b
couldn't delete /etc/ndiswrapper/net8187b: Inappropriate ioctl for device


thanks.

and btw, I don't know if this is normal, but under the Advanced tab in the BIOS menu, the wireless option is "greyed out" with the word [Restore] written next to it instead of the [Enabled] setting next to other devices in the same menu.

Well, I think you should sudo...
sudo ndiswrapper -r net8187b

About that greyed out card... does it work in windows (sorry about that, but you have to know if your card hardware isn't actually just broken)?

---

### Post by scholzilla on 2008-05-13
no, I don't know--it used to work, though. And I refuse to install windows :)

---

