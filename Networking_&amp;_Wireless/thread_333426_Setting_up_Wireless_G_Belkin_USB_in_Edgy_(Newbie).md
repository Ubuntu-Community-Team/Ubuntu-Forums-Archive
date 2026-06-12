---
title: "Setting up Wireless G Belkin USB in Edgy (Newbie)"
date: 2007-01-07
forum: Networking &amp; Wireless
---

### Post by acheton on 2007-01-07
Hi all,

I'm pretty close to an absolute beginner with Ubuntu. I have got Ubuntu 6.10 up and running with no problems (dual booting with Windows XP) :). I have access to the net through Ethernet and that works fine. However I cannot get my wireless adapter to work with Ubuntu. The adapter is a *"Belkin Wireless G USB Network Adapter"* - Model F5D7050 v4000uk. So far I have done the following:

Installed **ndiswrapper-utils-1.8, ndiswrapper-common **and **ndisgtk**. 

Using **System->Administration->Windows Wireless Drivers** I've added **blkwgu.inf** which is the Windows XP driver for the adapter, downloaded for the Belkin website. 

I've configure the network (wlan0) using the Network Manager, the Network name is the ESSID of my wireless network and the password has been set correctly. I've tried both DHCP and a static IP address however neither seem to work.

Running a **ndiswrapper -l** shows:

Installed drivers:
blkwgu          driver installed, hardware present 

If I then run a **iwconfig**:

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:-2147483648 dBm   Sensitivity=0/3  
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


The wireless network is configured for WPA and is working fine in Windows XP. I've read around a fair bit but don't know what to do in order to take this further. I hope I've provided enough information for someone to help. Any advice would be much appreciated.

Thanks,


Ach

---

### Post by n00b@linux on 2007-01-07
The password in Network Manager is for WEP.
If you use WPA you should read the thread in my sig (it&#347; one of the stickies on this forum).

---

### Post by acheton on 2007-01-07
Thanks for the swift reply!The latest version wpasupplicant was already installed, however when I try an **iwlist scan** I get the following:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results
sit0      Interface doesn't support scanning.

Which I'm guessing means that it cannot detect my network. I followed all of the other steps in case the SSID was not being broadcast, but it's not working. Any other things I can try?

Thanks


Ach

---

### Post by n00b@linux on 2007-01-07
You need to run:```
iwlist wlan0 scan
```Not 'iwlist scan' - you forgot to insert the interface (wlan0).

That should show you the available network.  If yours isn't listed, you'll need to physically move your wireless USB adapter closer to your access point's aerial (or vice versa) and try again.  If it is listed, take a note of the signal strength ("Quality" in the above iwlist output).  If it's too low, your WPA-PSK may not work.  This happened to me.  I fixed it by moving my access point closer to my USB wireless adapter.

Once you've got a good enough signal, you can try and associate your USB adapter to your access point:```
sudo iwconfig wlan0 mode managed essid <the ESSID of your access point>
```Then run```
iwconfig
```to make sure it's associated.  Then - providing you've set up your /etc/network/interfaces file per the 1st thread in my sig - you need to restart networking:```
sudo /etc/init.d/networking restart
```You'll then see it trying to establish a connection for each interface (incl. wlan0) and, with any luck, it will work.

---

### Post by acheton on 2007-01-07
Thanks for the help. I've now run ** iwlist wlan0 scan** which still produces the result:

wlan0     No scan results

As I say I'm a real beginner at this, but I'm wondering whether the device is setup correctly?

---

### Post by n00b@linux on 2007-01-07
If you're getting no results then it looks like your access point is too far away from your wireless USB adapter.  Try physically moving closer to the access point (or vice versa) and see if you get any results with iwlist wlan0 scan.

---

### Post by acheton on 2007-01-08
Even with the access point right next to the Wireless adapter I get no results from  iwlist wlan0 scan.

---

### Post by n00b@linux on 2007-01-08
It's a configuration problem then.
 
It would help if you could post some info about the chipset in the USB adapter. Run```
sudo lsusb -v
```and post the output to this thread - but ONLY that part of the output that relates to your USB device, as the whole output is very long and specifies details about ALL your USB ports. We are only interested in the part that details the wireless USB adapter.

---

### Post by acheton on 2007-01-08
OK, I've run that and I think that this is what you need:


Bus 005 Device 006: ID 050d:705c Belkin Components 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0        64
  idVendor           0x050d Belkin Components
  idProduct          0x705c 
  bcdDevice           48.10
  iManufacturer          16 Belkin
  iProduct               32 USB2.0 WLAN
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

---

### Post by acheton on 2007-01-09
I wonder whether I am running the wrong driver. Any clues from the output?

---

### Post by [L2G] Slapshot on 2007-01-09
Hi Acheton

From the output of the usb list this part ( the device id) pointed me to this that helped someone else with the same device id try this mate.

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29")

cheers
Jacko

---

### Post by acheton on 2007-01-12
Thanks for the advice, I've followed the instructions and still cannot get this working. My device is exactly the same as the one in the article. I've removed ndiswrapper, but maybe there is still something which I need to uninstall/remove/disable in order to get this working?

---

### Post by TheBigF on 2008-01-10
> **acheton said:**
> Thanks for the advice, I've followed the instructions and still cannot get this working. My device is exactly the same as the one in the article. I've removed ndiswrapper, but maybe there is still something which I need to uninstall/remove/disable in order to get this working?

I had a very similar problem to you - the drivers were being loaded, but I couldn't actually connect and saw Tx power of 0 and Rx power of 0 even though the wireless router was within range. So I went "back to basics" - here is what I did (and now I have access okay)

Firstly, I found I was having no luck with the Kubuntu drivers - so I used ndiswrapper. This is on the CD so you don't need internet access. Start up Adept (or similar) and install ndiswrapper.

2. Remove from memory the rt73 drivers (for me these were rt73usb rt2x00usb) using sudo rmmod <driver name>.  You can check afterwards with lsmod |grep rt which will list all loaded drivers containing "rt" in the name.

3. copy the 3 files rt73.sys rt73.inf and rt73.cat to a suitable directory on your computer and install them with ndiswrapper (viz: ndiswrapper -i rt73.inf )

4. ndiswrapper -l (apparently just to check)

5. modprobe ndiswrapper

6. iwconfig wlan0 (at this stage your wireless adapter should appear active, but not connected)

7. set-up the card, this will vary a bit from situation to situation, but assuming an open connection, with dhcp, then the following should work

8. iwlist wlan0 scan (to get the <essid name> )

9. iwconfig wlan0 mode managed
    iwconfig wlan0 essid <essid name>
    dhclient wlan0

at this stage you should see an address being assigned to your card and access.

Hope this helps you - it worked for me!

---

