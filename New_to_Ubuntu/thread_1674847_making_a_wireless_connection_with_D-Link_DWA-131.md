---
title: "making a wireless connection with D-Link DWA-131"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by tedwils on 2011-01-24
Hi. I'm new here and new to Ubuntu (or  any other Linux).  I have been reading many posts in  this forum over the last few weeks to solve installation problems and found there is much to be learned but everyone is helpful and I thank you. I have no problem using a wired network connection as I'm doing right now but I want to install a D-Link DWA-131 USB  wireless adapter and I get the "cannot find the autorun. program" message. Can you suggest a solution?
This is older computer with a 20g HDD,  with nothing but Ubuntu 10.10 installed.
Thanks again

---

### Post by lightningfox on 2011-01-24
Hi

Here's a thread on how to get a D-Link DWA-131 USB wireless adapter working

[http://ubuntuforums.org/showthread.php?t=1457505](http://ubuntuforums.org/showthread.php?t=1457505)

I hope it helps you.

---

### Post by tedwils on 2011-01-24
Thanks very much lightningfox. I'll give it a try.

---

### Post by tedwils on 2011-01-25
I made some progress following the links in the thread you suggested  lightningfox but I still have one problem with wireless connection. This  is where I'm at:
The usb adapter is recognized in lsusb and when I click on wireless  networks my d-link router appears as a choice but when I select it and  enter the authentication password,then choose connect, I get a  connection error. It repeatedly asks for authentication even though the  password is verified correct.
I used Windows Wireless Drivers to load the .inf driver that came on the  DWA-131 cd but I also found and downloaded a file from D-link support  that is for Linux. This download has 3 folders and a number of  additional files but I can't see any .inf files to load. So the folder,  rtl8192su-linux-2.4-2.6.0003.1019.2009 is sitting unused in my home  folder.
Hope someone can help me through this last hoop.
Thanks

---

### Post by walt.smith1960 on 2011-01-25
This is a popular topic, it seems.  Here is someone with what looks like the same problem and the solution. Assuming this really is a RealTek 8192SU chipset, You don't have to compile anything:

[http://ubuntuforums.org/showthread.php?t=1674994](http://ubuntuforums.org/showthread.php?t=1674994)

Here's a thread that talks about the problem:

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html)

The good news is that no patch or fix will be necessary with the next release of Ubuntu, this adapter will work "out of the box".

---

### Post by tedwils on 2011-01-26
I followed your instruction to create a new folder in lib -.> firmware named RTL8192SU and then copied the rtl8192sfw.bin into it, then closed down and rebooted but it didn't resolve the problem. No wireless option is available.  Then from chili555's post I tried using:
 	Code:
 	lsmod | grep 8712
dmesg | grep -e 8712 -e wlan 
This is what resulted:
ted@ted-desktop:~$ lsmod | grep 8712
ted@ted-desktop:~$ dmesg | grep -e wlan
ted@ted-desktop:~$ 
One thing I just realized is that the bin I copied was from an earlier version for linux shown below.
/home/ted/Downloads/rtl8192su_linux_2.4_2.6.0003.1019.2009
I went back to the more recent version to look for the bin file but couldn't find one. I checked every folder to be sure. This is the more recent file:
/home/ted/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111

Can you please suggest what I might try next.
Thank you.

---

### Post by gordintoronto on 2011-01-26
What is the ssid of your router? One word, all lower-case is good, anything else, not so much.

If it's rejecting your password, your drivers are fine.

---

### Post by tedwils on 2011-01-26
Thanks for chipping in gordintoronto.
The ssid is 401dlink.

---

### Post by walt.smith1960 on 2011-01-26
Does your DWA-131 have a light and is it on?  The files you reference are to build drivers.  If you have a light on your device, the device is likely functioning. If the light is not on the device could still be working. When you left click on network manager, what do you see? There should be entries for wired and wireless networks. You could also *right* click network manager and make sure 'enable networking' & 'enable wireless' are checked.  If left clicking network manager shows wireless networks, that's also an indication your hardware is working & you gotta solve the connection problem.  Hang in there, you'll get it.

---

### Post by tedwils on 2011-01-26
The unit has a light and it is on. In case it matters, I have reconnected with wire so I could continue on line. Network manager? There is nothing to verify it but I'm guessing that might be the Wired Icon on the top bar of the screen. Right click gives a box with: checked Enable Networking, checked Enable Notification. Left clicking shows: Wired Connection 1 and below it, DSL  connection 1 (as available) and VPN Connections. When I click on the DSL, the wired connection is disconnected and the circling symbol over the icon goes for maybe 30 sec., stops, and wired connection is reconnected. Under Preferences there are 2 references to network, namely Network Connections and Network Proxy and under Administration, there is Network Tools. Under tools, I found 2 network devices listed: Loopback Interface (lo) and Ethernet Interface (eth0).
"Hanging in". Heck, I am enjoying the puzzle (so far) because it is making me look all the harder and, as a result, learn a great deal about Ubuntu and the people who use it. I am so happy to have tried this great OS. I'm a convert. 
Thanks again for your generous help.

---

### Post by walt.smith1960 on 2011-01-27
What happens if you shut down, disconnect any network cables and restart? I'm pretty sure that if network manager/ubuntu have both wired & wireless connections, it will use the wired connection.I'll have to try plugging a network cable into my notebook and see if the wireless connection in network manager goes away--in the morning.  It sure seems like if the light on the device is on, the device is functional.  Yes, network manager is the two green dots that move in a circle in the upper right hand corner of the screen.

---

### Post by tedwils on 2011-01-27
No light. No luck. lsusb shows Bus 004 Device 002: id 07d1:3303 D-Link system.
Shutting down, removing wired connection and rebooting made no difference. I have been reading further and have tried a suggestion from another post, namely [B]Installing the WiFi Driver (for RTL8192SU) from July8,2010. From here i tried the .tar.gz. that came with the latest version of the Linux download from D-Link. (sorry, i can't get out of this bold). I rebooted after unpacking the software but, again, no light on the usb. Worse than that, my desktop comes up without the top and bottom bars. The only things I can see are the directory holding the latest downloaded rtl8192su and my cd icon. I have rebooted a few times but it remains the same.
When using .tar.gz. i followed the instruction from the thread mentioned above, that is,
[/B]before you run unzip in the terminal make sure you have the .zip file in  your current directory. type "ls" this list whats in your current  directory. This can also be done by just double clicking the .zip file  in a file viewer, it should normaly open with archive manager.
This post is coming by way of my old windows machine, since I can't use Ubuntu now. Boy do I need help. Please!
OK this seems serious and besides, the practice should help perfect, so I am going to reload the Ubuntu program and start again. I'll probably get on this forum later when I get stuck again so I hope I haven't frustrated my helpers. Thanks for all your help thus far.

---

### Post by tedwils on 2011-01-27
I'm up again with a fresh start. I might try the latest D-Link download once more using the tar-gz package it contains. If that doesn't work I will either wait for rescue , reload the OS if necessary, or wait until Ubuntu brings out the patch. Meanwhile I'll just keep the wire connection.

---

### Post by walt.smith1960 on 2011-01-28
There's one other thing you could try. If you feel like downloading an alpha release of 11.04 desktop, 11.04 has a different RTL8192SU driver in it. My device is recognized and works without downloading or modifying anything.  Alpha versions are not suitable for everyday use but would at least let you know that plug-and-play for your device is on the way.

---

### Post by tedwils on 2011-01-28
Thanks a lot Walt. I think I'll have to wait until future updates take care of this D-Link adapter. The last thing I did was download the latest Linux version for this adapter and extracted the contents in Downloads. I opened the rtl directory then "document" where I found a "quick installation guide.ppt". I read it and tried to follow the instructions but every time I tried to enter the code it wouldn't work. I must be entering things wrong. For example, Step 2. make 8712USB driver module followed by " > make". I tried this and got "no target specified (etc.)". I then tried it again adding RTL8712USB and got "no rule make target (etc)". Obviously, I have a lot to learn about (I think its called) gnome and entering codes.
Thanks again.

---

### Post by Spyderkid on 2011-01-29
i've made a thread to fix this problem for the RTL8192SU wireless

[here]("http://ubuntuforums.org/showthread.php?t=1671814")

---

### Post by walt.smith1960 on 2011-01-29
One of the ways Linux is different is the way it handles hardware recognition.  Windows uses an installer; the Linux equivalent is the .rpm or .deb file depending on distro.  I'm sure Linux packages & windows installers are not exactly the same but they seem functionally similar.  You've been downloading source code; there is no commonly available equivalent in Windows.  Source code may need to be edited then compiled which is what Spyderkid's post tells you how to do.  The files from RealTek are _not_ installers like windows .exe files. 

I'm still curious why once your device seemed to have come alive with the light on, you were not able to connect.  Perhaps D-Link's implementation of the RTL8192SU chipset is different than TrendNet's which I have.  Perhaps there was an issue with WiFi encryption.  There are numerous threads where people were able to connect with WiFi encryption disabled but not with WiFi encryption enabled. Or it could be something else entirely.

---

### Post by tedwils on 2011-01-29
Spyderkid I'm trying your solution but just before that, would you suggest I use a more recent version? You had v2.6.0005.20091112.p4.zip and I found v2.6.6.0.20101111.zip.
I started following your directions (using the zip version you suggested) and quickly ran into a snag in step 2. Check what I entered from the terminal.
ted@ted-desktop:~$ cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091112.p4/cd driver
bash: cd: rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091112.p4/cd: No such file or directory
ted@ted-desktop:~$ cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091112.p4/cd driver
bash: cd: rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091112.p4/cd: No such file or directory
ted@ted-desktop:~$ cd driver
bash: cd: driver: No such file or directory
As you can see I tried a few times. What am I doing wrong? and if you don't mind, tell me first if I should follow the directions you gave using that later version.
Thanks very much for your help.

---

### Post by walt.smith1960 on 2011-01-29
Ted-

You might take a look at this thread if you haven't.
[http://ubuntuforums.org/showthread.php?t=1457505](http://ubuntuforums.org/showthread.php?t=1457505)
It looks like the DWA-131 might have some interference issues.

---

### Post by tedwils on 2011-01-30
Thanks again Walt. This is where I'm at now.
I followed your suggested  link and eventually wound up at a thread from last April called **Help with D-Link DWA-131 Wireless N USB Adapter driver needed[B]. **[/B]From  bmjbmj and mattthewp131 I got instructions for installing the driver.  That all seemed to go well but after shutting down, plugging in the usb  adapter and unplugging the wire, then rebooting, the adapter light  didn't come on and no wireless networks were available (at least that  message was there in the network manager). I will need to do some more  digging to see what remains to be done.

---

### Post by tedwils on 2011-02-01
Still need help with connecting this adapter. This is as far as I got so far. I have found and downloaded the latest driver, created a directory /lib/firmware/rtl8192su and moved rtl8192sfw.bin into it. I have rebooted and connected the adapter. The blue light comes on in the adapter, network manager shows both wired and wireless networks available, including my own SSID. When I try to connect to my network, it asks for the password, and begins trying to connect but, after a few cycles of trying, it gives me the "wireless network disconnected" sign. Code lsusb shows the device. I have tried using Network Tools in Administration, selected the Wireless Interface wlan0 and clicked on configure but nothing resulted. In Preferences I tried Network Connections, chose Wireless, clicked on wlan0, edit, made sure it was set to connect automatically, the SSID was correct, tried both Infrastructure and Ad-hoc. On the Wireless Security tab, I set it to WPA and WPA Personal and verified the password. On the IPv4 settings tab the Method was Automatic (DHCP). The IPv6 settings was on ignore. I pressed Apply. Nothing!
I have searched many posts throughout Ubuntu and even elsewhere but I can't get past this point. I must be missing a vital piece of the puzzle. Please, can somebody walk me through the last little bit. Thank you.

---

### Post by A-rap on 2011-02-02
Damn we need to make it. I have exactly the same problem.....
Actually got this **** a little bit more working with the NDISWrapper, but still like u said it  is connecting something and then comes a notice that disconnected... :( Atleast it worked first time i installed the linux driver! WTF?

---

### Post by walt.smith1960 on 2011-02-02
Tedwils you're almost there!!!!:guitar:  Any chance you could try connecting to an open network?  If you're seeing your own and other networks, the hardware seems like it's working.  I don't know if WICD would be more helpful than network manager or not.  I assume you've tried restarting?

---

### Post by tedwils on 2011-02-02
Yes the hardware does seem to be working because I can usually see two available networks when I check Network Manager. I have indeed tried various ways of turning off, unplugging the adapter, plugging it in before rebooting, plugging it in after Ubuntu was up but nothing seems to change. I had to look up WICD since I never heard of it before. Think I will try it since nothing else has worked so far. I'll get back after to let you know if it worked.
A-Rap, good luck. Nice to know I'm not alone in this.

---

### Post by tedwils on 2011-02-04
Walt, trying to get this adapter working is becoming a saga. Wicd made a mess of my desk-top so I wound up reloading Ubuntu from scratch. Of course that meant losing everything I had done up to that point. So I'm back up with /lib/firmware/RTL8192SU in place with the rtl8192sfw.bin loaded into it. Usb light is on, Network Manager shows (today) 3 available wireless networks and, when I boot up, the NM tries to make the connection 3 times then gives up with the Wireless Connection disconnected. I have looked at numerous threads on this problem and have tried many solutions but the problem persists. One thread involved ([http://ubuntuforums.org/showthread.php?t=1522815&highlight=rtl8192sfw.bin](http://ubuntuforums.org/showthread.php?t=1522815&highlight=rtl8192sfw.bin)) a different brand of adapter but with the same chip. This is what it suggested;

1.) First I had to add the device to r8192s_usb(both files are likely empty):

Use this command in the terminal to open the first file:
 	Quote:
 	 	 		 			 				sudo gedit /etc/udev/rules.d/network_drivers.rules 			 		 	 	 
and add this line:
 	Quote:
 	 	 		 			 				ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="050d", ATTR{idProduct}=="945a", RUN+="/sbin/modprobe -qba r8192s_usb" 			 		 	 	 
Save it then run this command to open the second file:
 	Quote:
 	 	 		 			 				sudo gedit /etc/modprobe.d/network_drivers.conf 			 		 	 	 
and add this line:
 	Quote:
 	 	 		 			 				install r8192s_usb /sbin/modprobe --ignore-install r8192s_usb  $CMDLINE_OPTS; /bin/echo "050d 945a" >  /sys/bus/usb/drivers/rtl819xU/new_id 			 		 	 	 

2.) Then I obtained the firmware from here:
 	Quote:
 	 	 		 			 				[http://svn.debian.org/wsvn/kernel/di...rtl8192sfw.bin]("http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin") 			 		 	 	 
and copied it to /lib/firmware/RTL8192SU/ with these commands:

 	Quote:
 	 	 		 			 				wget [http://svn.debian.org/wsvn/kernel/di...rtl8192sfw.bin]("http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin")
sudo mkdir /lib/firmware/RTL8192SU
sudo cp rtl8192sfw.bin /lib/firmware/RTL8192SU 			 		 	 	 
Afterwards, I restarted and all worked well. Perhaps others with this device will be able to get it running well too.

To expand on this process further, r8192s_usb is the kernel  module("device driver") for devices with the RTL8192SU chipset.[COLOR=Red] Since  the module does not contain the device id for the wireless card, we use  the trick demonstrated above to add it to the module without having to  recompile it.[/COLOR] This works on most distros newer than the stable branch of  debian. On some like Suse, you have to install the staging package  first(kmod-staging). I also had to add the firmware, dmesg is good for  debugging that part. This same process can be used with other devices as  long as you can find a module for the chipset and change the info in  the lines accordingly.
Do you know if this "Trick" is something I can try? If so, does it have to be modified for the D-Link brand? Hope I'm not driving you around the bend with this problem.

---

### Post by walt.smith1960 on 2011-02-08
Saga indeed!!! I'm glad you were able to prevail.:KS

---

