---
title: "BeagleBone Black Wireless with Ubuntu Xenial 16.04 Wifi Not Working"
date: 2018-03-10
forum: Networking &amp; Wireless
---

### Post by ghio on 2018-03-10
I have the BeagleBone Black **Wireless**, and I have flashed **Ubuntu 16.04**  to it. I am trying to make the WiFi to work but have so far failed. I  have already tried to modify the /etc/network/interfaces file by adding  the following commands for wlan0, without any luck:
```
   auto wlan0
      iface wlan0 inet static
      address 192.168.1.2
      netmask 255.255.255.0
      gateway 192.168.1.1
      wireless-mode ad-hoc
      wireless-essid BBB
```

In some forums, people suggest using &#8220;connmanctl&#8221;, however, there is  no such preinstalled package in Ubuntu. Also I can&#8217;t download it to the  BBBw, because its WiFi is not working. I tried connecting the BBBw to  the internet via a usb connection with a PC, I edited this connection to  &#8220;shared to other computers&#8221; but again, I had no Internet connection to  the BBBw.

  To sum up, my question is: Is there an easy way to make the WiFi of  the BBBw (with Ubuntu) to work, without the need to use the  &#8220;connmanctl&#8221;? 
  If not, any detailed information on how to install the &#8220;connmanctl&#8221; would be very much appreciated.
  I am including the whole /etc/network/interfaces file, with the part  that I added, which appears after the comment &#8220;The following lines for  the wlan0 were added by me&#8221;.

```
    # This file describes the network interfaces available on your system
    # and how to activate them. For more information, see interfaces(5).

    # The loopback network interface
    auto lo
    iface lo inet loopback

    # The primary network interface
    auto eth0
    iface eth0 inet dhcp
    # Example to keep MAC address between reboots
    #hwaddress ether DE:AD:BE:EF:CA:FE

    # The following lines for the wlan0 were added by me
    # Ad-Hoc wifi
    auto wlan0
       iface wlan0 inet static
       address 192.168.1.2
       netmask 255.255.25a5.0
       gateway 192.168.1.1
       wireless-mode ad-hoc
       wireless-essid BBB

    ##connman: ethX static config
    #connmanctl services
    #Using the appropriate ethernet service, tell connman to setup a static IP address for that service:
    #sudo connmanctl config <service> --ipv4 manual <ip_addr> <netmask> <gateway> --nameservers <dns_server>

    ##connman: WiFi
    #
    #connmanctl
    #connmanctl> tether wifi off
    #connmanctl> enable wifi
    #connmanctl> scan wifi
    #connmanctl> services
    #connmanctl> agent on
    #connmanctl> connect wifi_*_managed_psk
    #connmanctl> quit

    # Ethernet/RNDIS gadget (g_ether)
    # Used by: /opt/scripts/boot/autoconfigure_usb0.sh
    iface usb0 inet static
        address 192.168.7.2
        netmask 255.255.255.252
        network 192.168.7.0
        gateway 192.168.7.1
```

Thanks in advance

---

### Post by jeremy31 on 2018-03-10
Please see the wireless script link in my signature and post results?

Some of the lines you added to the interfaces file make it look to me like you are trying to make a wifi hotspot with the wireless instead of trying to connect to a network

---

### Post by ghio on 2018-03-12
You are right, this is what I want to do. I want to create an AD-HOC wireless network on the BBBw. The reason I mentioned having internet on the BBBw is to point out that some suggestions I found on several forums need an internet connection on the BBBw, which I don't have.

Here are the results of the script link: [https://www.dropbox.com/s/54x384ceca7vbcw/wireless-info.txt?dl=0](https://www.dropbox.com/s/54x384ceca7vbcw/wireless-info.txt?dl=0)

---

### Post by jeremy31 on 2018-03-12
I did notice the wifi interface was not UP
```
sudo ifconfig wlan0 up
```
See if it works then

---

### Post by ghio on 2018-03-13
I tried your suggestion, executing the command gave me the following results. It did not work, but gave me some error messages. What should I do next?

[https://www.dropbox.com/s/0op218l2tixggez/wlan.png?dl=0](https://www.dropbox.com/s/0op218l2tixggez/wlan.png?dl=0)

---

### Post by jeremy31 on 2018-03-13
Shows a firmware issue
```
cd /lib/firmware/ti-connectivity
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/ti-connectivity/wl18xx-fw-4.bin
```
Reboot

---

### Post by ghio on 2018-03-14
I downloaded the bin file to a PC and transferred it to the BeagleBone via SSH. I put it in the directory you suggested, and the wi-fi LED finally opened on the board. I edited the /etc/network/interfaces file and added wlan0 reference. However I could not find the wireless network that was supposed to be up, from any other device. I am putting a link with the changes I made to the /etc/network/interfaces file. Also, i ran the wireless script again, in case it gives you anything useful:
[https://www.dropbox.com/s/lf6pi9ft2gssj5o/SCRNSHT_2.png?dl=0](https://www.dropbox.com/s/lf6pi9ft2gssj5o/SCRNSHT_2.png?dl=0)
[https://www.dropbox.com/s/cw4yh41mspbih0t/wireless-info_latest.txt?dl=0](https://www.dropbox.com/s/cw4yh41mspbih0t/wireless-info_latest.txt?dl=0)

---

### Post by jeremy31 on 2018-03-17
The problem with ad-hoc is that a lot of OS's won't display them, my Android phone will not show one

---

### Post by ghio on 2018-03-17
I see. I can't find it either from my linux laptop, nor from android devices. So, supposing that the ad-hoc network is up, can I connect to to it somehow? I need to connect to the Beaglebone via Wifi. Any other ideas, if the ad-hoc can't work?

---

### Post by jeremy31 on 2018-03-18
See if can be used in access point mode.  I usually do it in Network Manager and not in the interfaces file

---

### Post by ghio on 2018-03-19
I tried another procedure: I set up an ad-hoc connection (I chose "shared to other computers" method in the "IPv4 Settings" tab) on my Ubuntu Laptop (device A). This is the ifconfing on device A: [https://www.dropbox.com/s/qpb3ggutgos9jfd/scrnshot_19-3_HOSTPC.png?dl=0](https://www.dropbox.com/s/qpb3ggutgos9jfd/scrnshot_19-3_HOSTPC.png?dl=0)
Then I created a connection on another ubuntu laptop (device B) with ad-hoc DHCP(auto) settings, and its ESSID was set the same with the ESSID of the initial connection that was created on device A ("adHocPC"). Here is the ifconfig on device B: [https://www.dropbox.com/s/wjcijyeehq3080m/scrnshot_19-3_CLIENTPC.png?dl=0](https://www.dropbox.com/s/wjcijyeehq3080m/scrnshot_19-3_CLIENTPC.png?dl=0)
The above steps created a perfectly working connection between devices A and B.
After that i tried replacing device B with the BBBw. I edited the /etc/network/interfaces, and I added the following lines for wlan0: [https://www.dropbox.com/s/yw5ux8k6x1wtqke/interfaces_19-3.png?dl=0](https://www.dropbox.com/s/yw5ux8k6x1wtqke/interfaces_19-3.png?dl=0)
Once more, I could not establish a connection between BBBw and device A.
I also ran ifconfig on the BBBw (you can see that it has taken no IP): [https://www.dropbox.com/s/s3viflkdwufx6yx/scrnshot_19-3_BBBW.png?dl=0](https://www.dropbox.com/s/s3viflkdwufx6yx/scrnshot_19-3_BBBW.png?dl=0) 
Lastly, once more, i reran the wireless script and I am posting the results: [URL="https://www.dropbox.com/s/9ihnkysc3lhs5tv/wireless-info_19-3_BBBW.txt?dl=0"]https://www.dropbox.com/s/9ihnkysc3lhs5tv/wireless-info_19-3_BBBW.txt?dl=0

[/URL]**EDIT: **I ran a diagnostics script for Beagleboards named version.sh. Here are the results: [https://www.dropbox.com/s/kimbj5ntao1v7nk/version_sh.txt?dl=0](https://www.dropbox.com/s/kimbj5ntao1v7nk/version_sh.txt?dl=0)
In line 10 it shows a warning about a firmware package not having been installed.

---

### Post by ghio on 2018-05-19
I have found a way to make the WiFi of BBBw to work. 

 1. Firstly add the following lines to the etc/network/interfaces file of the BBBw (you need to access it by another way, for example a serial connection with a laptop):
   
        auto wlan0
            iface wlan0 inet dhcp
            wpa-ssid yourSSID
            wpa-psk yourPass

 2. Reboot BBBw
 3. Then you have to update the firmware (exactly as you suggested!):

        sudo wget [https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/ti-connectivity/wl18xx-fw-4.bin](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/ti-connectivity/wl18xx-fw-4.bin)

copy the abovementioned .bin file to the lib/firmware/ti-connectivity directory of BBBw

 4. Reboot BBBw

After doing these you have to set up a connection to your linux PC for the BBBw to connect to. This connection should be "Shared to other computers", hotspot mode, WPA/WPA2 Personal, and have the SAME ssid as the one in the interfaces file. 

After that your BBBw should be able to connect to your PC. If you want your BBBw to have internet access, you have to connect an internet ethernet cable to your PC. The "shared to other computers" hotspot connection will share the PC's ethernet internet to the BBBw.

More issues:

 - There is a good chance that, in order for the BBBw to connect to the PC's hotspot connection, you should NOT have the internet ethernet cable of the PC connected during the BBBw's boot (it is at boot time that BBBw tries to find a network to connect).
 - Wifi was still not working until the latest ubuntu armhf console image (i.e. the 2018-03-09 version) was flashed. I haven't managed to make the older 2018-02-09 version to work.

Thanks a lot for your help @jeremy31

---

