---
title: "atheros wireless on Toshiba laptop"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by drumkitcat on 2007-03-01
Hi,
I need some fine-tuning help please!  I've just installed a dualboot setup on my Toshiba Satellite A40 laptop (512mb Ram, 2.66 Celeron processor, 40gb hd, Windows XP Home, Ubuntu Edgy 6.1)

Edgy installed beautifully!! It sees that I have the Atheros built-in wireless (AR5212 rev01) and built in wired ethernet card. 

I've installed MadWifi, and I now have a cool little network icon on the upper right corner of the screen, and it shows I have a steady 85% or so connection strength, however I cannot get online!  I have a home network and it's set up through a Netgear wireless router going to an ADSL modem.

Here's the screen output text...

using iwconfig I get:
lo        no wireless extensions.
eth0      no wireless extensions.
wifi0     no wireless extensions.
ath0      IEEE 802.11g  ESSID:"BoomRoom"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:90:4C:7E:00:29   
          Bit Rate:48 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off          Power Management:off
          Link Quality=45/94  Signal level=-50 dBm  Noise level=-95 dBm
          Rx invalid nwid:26188  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
sit0      no wireless extensions.

using lspci I get:
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:05.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
01:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)

please let me know what I'm missing here... it seems like I'm so close to getting it working, just missing some minor details..

thanks
Paul

---

### Post by x64Jimbo on 2007-03-01
You should install NetworkManager and see if that helps. It takes a lot of the pain out of managing network interfaces.

---

### Post by drumkitcat on 2007-03-01
Hi,
thanks for the response.
I tried to install Network manager, but it said "cannot be installed on your system" and something else like it's not supported or has special hardware requirements

If you have any other ideas please let me know

---

### Post by x64Jimbo on 2007-03-02
Did you follow a guide?
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_Configure_Ubuntu.2FKubuntu_with_WPA_using_Network-Manager](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_Configure_Ubuntu.2FKubuntu_with_WPA_using_Network-Manager)

---

### Post by drumkitcat on 2007-03-02
Ok, here's what I did,

I connected an ethernet cable to the builtin ethernet card on my Toshiba laptop, and downloaded all the updates for Edgy, and then installed (was able to now) the Network Manager.  

I took a look at the guide, and followed the instructions there for installing it.  I then unplugged the ethernet cable, turned on the wireless Atheros adapter again, and rebooted.

When it rebooted, the Network Manager icon does show up in the upper right corner as indicated in the guide, however there are no "tunable" options, when I put the mouse over it, it just says "no network available" - and that's all.  I had already re-activated the Atheros wireless card back in the Network Settings dialog box.

Did I miss something?  It is still not working with the wireless adapter... I had installed ndiswrapper with what was listed as the appropriate drivers, however they all currently show up as "invalid driver" when I do the ndiswrapper -l on them... strange!

Any help would be appreciated,
thanks!

---

### Post by calgarystevens on 2007-03-02
To get my Atheros wireless working I did this: 

(You need the wireless files from winblows for this, net5211.inf, etc)
sudo ndiswrapper -i /whereyouputit/net5211.inf
then check it worked with ndiswrapper -l (should show name of driver and other info)
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m  <---these last steps set it up and ensure it will work after a reboot
then go to System Settings->Networking
select wlan0 connection, configure for your router settings and click Enable.

If you've done this, I apologize for sticking my nose in, but hopefully it'll help. I haven't figured out madwifi yet, and my ndiswrapper is working so well why bother I figure.

---

### Post by drumkitcat on 2007-03-03
thanks! I'll give that a try.  I haven't done all those steps - and I can see what I was  missing thanks to your post.  I'll hopefully be responding soon using Ubuntu instead of Winblows. 

Paul

---

### Post by tturrisi on 2007-03-03
You do NOT NOT need ndiswrapper or windows drivers for atheros chipsets.  You need the madwifi drivers.

Remove ndiswrapper and any windows drivers.  Then use synaptic to install the linux-restricted-modules which contain madwifi.  Or build madwifi your self by doing:
# apt-get install module-assistant
# apt-get install madwifi-source 
# apt-get install madwifi-tools
# m-a prepare
# m-a a-i madwifi

source: [http://madwifi.org/wiki/UserDocs/Distro/Debian/MadWifi](http://madwifi.org/wiki/UserDocs/Distro/Debian/MadWifi)

I have several atheros cards and they all work fine.

---

### Post by drumkitcat on 2007-03-03
Ah, ok - I'll give that a try as I do have madwifi installed and everything shows up (apparently) as ath0 ... I will try that approach as I did get ndiswrapper to load the drivers, but it doesn't seem to make any difference.

Right now, I'll uninstall/remove ndiswrapper (ver1.37) and I'll try those other commands for madwifi - thanks for posting that it's the first I've seen of those commands although I haven't checked the wiki.ubuntu listings.

for what it's worth, here's a screen listing of what ndiswrapper has done so far:

paul@paul-laptop:~/atheros$ ls
ar5211.sys  madwifi-0.9.2.1  ndiswrapper-1.37  net5211.inf  SHP5211.sys
paul@paul-laptop:~/atheros$ ndiswrapper -v
utils version: 1.9
driver version:        1.37
vermagic:       2.6.17-11-generic SMP mod_unload 586 REGPARM gcc-4.1
paul@paul-laptop:~/atheros$ sudo ndiswrapper -i ar5211.sys
Password:
installing ar5211.sys ...
couldn't get manufacturer section - installation may be incomplete
paul@paul-laptop:~/atheros$ ndiswrapper -l
ar5211.sys : invalid driver!
net5211 : driver installed
        device (168C:0013) present (alternate driver: ath_pci)
paul@paul-laptop:~/atheros$

---

### Post by drumkitcat on 2007-03-03
Ok, I tried the mad-wifi commands listed, but got an error..

when I used the sudo m-a a-i madwifi, it came up with a screen saying "unable to load madwifi-sources source, you may need to add something to your sources.list

and would not proceed any further... how can I fix that?  where do I find sources.list?

here's a screen listing:

 sudo apt-get install module-assistant
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
module-assistant is already the newest version.
The following packages were automatically installed and are no longer required:
  libnl1-pre6 network-manager libnm-util
 dhcdbd
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
paul@paul-laptop:~/madwifi-0.9.2.1$ sudo apt-get install madwifi-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package madwifi-source
paul@paul-laptop:~/madwifi-0.9.2.1$

---

### Post by drumkitcat on 2007-03-03
how can I totally remove ndiswrapper from my system?  I thought I had, using the sudo rm -rv ndiswrapper, but the driver still gets loaded after a reboot...??

I had to remove it manually as it was installed from  a tar file, and did not show up in the regular graphical interface under Synaptic Package Manager or under Add/Remove..

As for madwifi, in its directory, there's a file called tools, but no file called source.

any ideas?  I'm really messed up here... and yet, at the moment I've booted into the windows xp partition on my laptop to write this email, so I konw the atheros card does work fine, just need the fine tuning in Ubuntu Edgy

---

### Post by tturrisi on 2007-03-03
apt-get --purge remove ndis-wrapper
(may or may not have a hyphen)

or remove it via Synaptic Package Manager.

---

### Post by twidget on 2007-03-04
hmm in Kubuntu you dont need either madwifi or ndiswrapper. my cheapie airlink atheros card just worked out of the box without me installing anything besides edgy. shouldnt it be the same with Ubuntu since they share the same kernel?

---

### Post by drumkitcat on 2007-03-04
thanks, I'll try that to remove ndiswrapper.

The weird thing is though, I had installed ndiswrapper, and the net5211.inf driver with it, and it showed up perfectly - saying driver installed, hardware present, etc.. but back in the ubuntu graphical environment, the network tool said the card was 'active' but the network monitor icon in the upper right corner of the screen said 'no connection'.

hopefully it's a case of madwifi and ndiswrapper not working together and by removing one of them the other will work.... that's my hope, my dream... if not I'll post again and see what can be done next.

Everything else with Edgy on my laptop has installed perfectly out of the box - sound, display, modem, ethernet card - just the atheros wifi - and even that it does see it and know what it is, but it's always showing up as ath0 and not wlan0.

If anyone else has any input, please let me know, I really appreciate everyone's help!!
thanks!
Paul

---

### Post by drumkitcat on 2007-03-04
> **tturrisi said:**
> apt-get --purge remove ndis-wrapper
(may or may not have a hyphen)

or remove it via Synaptic Package Manager.

- yeah, weird thing there is that it didn't show up with Synaptic Package manager!!  Maybe because I had installed it through the 'backdoor' using a tar file I downloaded instead of through add/remove or Synaptic originally...no internet connection on the ubuntu partition of this laptop at the moment aside from the wired ethernet card.

thanks though, I'll try the terminal version to remove it

---

### Post by drumkitcat on 2007-03-05
I think, since it's still early in the process and I've done no actual work with Ubuntu aside from installing it - that I will do a fresh install and then install crucial elements like Network Manager, Linux Restricted Modules, etc... and subsequently madwifi..   

I get the feeling that there may be competing drivers at work, and maybe the best way to clear that up is to clean it all out!

---

### Post by sheds on 2007-09-25
> **tturrisi said:**
> You do NOT NOT need ndiswrapper or windows drivers for atheros chipsets.  You need the madwifi drivers.

Remove ndiswrapper and any windows drivers.  Then use synaptic to install the linux-restricted-modules which contain madwifi.  Or build madwifi your self by doing:
# apt-get install module-assistant
# apt-get install madwifi-source 
# apt-get install madwifi-tools
# m-a prepare
# m-a a-i madwifi

source: [http://madwifi.org/wiki/UserDocs/Distro/Debian/MadWifi](http://madwifi.org/wiki/UserDocs/Distro/Debian/MadWifi)

I have several atheros cards and they all work fine.

What are the repositories needed to find these files? I attempted to do this and i couldn't do it because apt said that package cannot be found.

---

### Post by dmizer on 2007-10-13
madwifi makes the card work, but no dhcp, so still no internet.

i can't/won't uninstall ndiswrapper because i need it for a different card.

same chipset as the op.

edit:
got the card to work flawlessly with ndiswrapper.  problem was that i forgot to reboot the router after updating it with the new card's mac address :oops:

still can't get the thing to work with madwifi though.

---

