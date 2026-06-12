---
title: "Installing Intel PRO/Wireless 3945ABG"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by Noxieas on 2007-02-09
Starting off sorry, I know this question has been answered in the past. That being said I am completely new to Linux and I know the wireless card in question is a redundant problem with Dell xps M1210 models using this wireless card; I've managed to get all the other drivers not detected working fine with no assistance, however this is what I've gathered.

The website: [http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/) , has a ton of information on installing this card, however being new to the terminal and Linux CLI I am at a loss to translate the guide into clear context for install... Anyone willing to help a newbie out step by step? Thanks in advance =)

---

### Post by mikewhatever on 2007-02-09
Hi, what help do you need? I might mention, that in my case, the driver for the card was loaded. Type lshw in the terminal, and look for the similar part:
>  *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@06:00.0
                logical name: eth1
                version: 02
                serial: 00:13:02:c8:d2:75
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw3945 ip=192.168.1.3 multi
note if ipw3945 driver is present.

---

### Post by appsmanster on 2007-02-09
> **Noxieas said:**
> Starting off sorry, I know this question has been answered in the past. That being said I am completely new to Linux and I know the wireless card in question is a redundant problem with Dell xps M1210 models using this wireless card; I've managed to get all the other drivers not detected working fine with no assistance, however this is what I've gathered.

The website: [http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/) , has a ton of information on installing this card, however being new to the terminal and Linux CLI I am at a loss to translate the guide into clear context for install... Anyone willing to help a newbie out step by step? Thanks in advance =)

Run 'sudo network-admin' from the terminal. Is the wireless connection listed?

---

### Post by Noxieas on 2007-02-09
I've installed the drivers for Debian, no luck, as well as the ipw3945 kernel module. 

lsmod | grep 'ipw3945'
ipw3945               124576  1 
ieee80211              35272  1 ipw3945


iwconfig 

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:224   Missed beacon:0

sit0      no wireless extensions.

Still at a loss as for whats going on.

---

### Post by Noxieas on 2007-02-09
*bump*

---

### Post by Cre8Tive on 2007-02-19
> **Noxieas said:**
> I've installed the drivers for Debian, no luck, as well as the ipw3945 kernel module. 

lsmod | grep 'ipw3945'
ipw3945               124576  1 
ieee80211              35272  1 ipw3945


iwconfig 

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:224   Missed beacon:0

sit0      no wireless extensions.

Still at a loss as for whats going on.


That is the exact same problem that I am having.  Any one out there want to help out 2 birds with one stone?

Thanks

---

### Post by mikewhatever on 2007-02-19
Actually, I had a similar issue and had to install kernel restricted modules. After that, the wireless worked, but in your case, after messing around with the driver, well, I don't think it will harm the system anyway.
Check which kernel are you using > uname -a If you have a wired connection, search in synaptic for linux restricted and install the right package. If not, it can be downloaded from [THIS]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-restricted-modules&searchon=names&subword=1&version=edgy&release=all") page.

---

### Post by Tichondrius on 2007-02-19
what are you doing ? Intel wireless is the BEST supported wireless card. You don't need to install ANYTHING. Your card is already detected and working correctly (all Intel wireless chips are).

All you need to do now is to connect to a wireless network. You will need to know the wireless  network name and encription key.

You can do that either from the command line using the iwlist and iwconfig commands, or using the network properties in Ubuntu (System->Administration->Networking). Also you can use the gnome network manager (although I haven't tried it) which is another GUI that helps connect to a wireless network.

For example, using the command line you can start by scanning for wireless networks using the command

iwlist eth1 scan

Then use iwconfig to associate to your WLAN:

sudo iwconfig eth1 key open 123456789
sudo iwconfig eth1 essid MyNetwork


Now check if it associated successfully:

iwconfig

---

### Post by penvzila on 2007-02-20
I'm having this problem, sort of.  I can connect to my wireless lan fine at home, but I can't get Ubuntu to work with my school's wireless network.  It's unencrypted (you log in with a web form), but I can't ever find it.  It connects fine in Windows, though,

---
Ok, I have resolved my issue.  Turns out I was being a moron.  I just clicked the (-) symbol next to Wireless in the Networking admin applet, and deleted all the entries in the DNS tab, and it automatically connected.

---

### Post by mikewhatever on 2007-02-20
Actually, that's not your problem at all.
Do you use any kind of network manager? If not, install gnome network manager from synaptic. It enables you to see what networks are in range.

---

### Post by chikenbob on 2007-02-22
Tichondrius >> I did what you said and it appears everything worked but I still cannot connect to the internet. Any Ideas? I just installed ubuntu and have made no changes to the configuration of the system. ( all I did was jchange the back ground XD ) any help would be appreciated.

---

