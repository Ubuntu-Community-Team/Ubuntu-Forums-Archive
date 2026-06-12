---
title: "Fixing my wireless after kernel update"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by kmashraf on 2007-08-06
Well I hope this will help people with similar problems.
Though I should mention that this problem is being bandied about all over cyber space as a failure of Ubuntu on upgrade. To make myself clear, Ubuntu isn' t from the proprietary world. It is GNU/Linux, free and the price to pay in making it work is well worth my time and money! And best of all i am learning all the time.
I am running Kubuntu 7.04, on a AMD 2200 CPU, nVidia chipset motherboard, 512 MB RAM, 20 + 10 GB HDD' s, Compex WLP54G PCI adapter upgraded from Dapper thru to Feisty.
Dapper to Edgy went off very well and smooth. But not so from Edgy to Feisty.few things broke,mainly my X, and my wireless. The default Network Manager utility for Feisty is a dud as far as I am concerned. It is unable to acquire a ip from my GNU/Linux firewall box connected via a Linksys WRT54GS wireless router. It is not running DHCP, I trust my Vector Linux 3.2 firewall box connected to my service providers ADSL router more since it has been doing the job for well over 2 years now to the outside world.
Since it did not work I continued to use Wireless Assistant which requires me to manually start it.
In the meanwhile I updated via Adept Notifier to kernel 2.6.20-16 and that again broke my X and wireless. With the help of these here forums I was able to resolve my X problems by reverting to the older nVidia drivers which suit my onboard nVidia adapter. 
Wireless I found that the card itself was not detected when I booted the new kernel. So I for some time continued using the older 2.6.20-15 kernel where the wireless worked 
But I was restless to get the latest kernel to work too. So I looked around and under and found that the restricted drivers modules aren't installed by default with kernel updates. It has to be downloaded and installed.
So all I had to do was to download "linux-restricted-modules-2.6.20-16-386_2.6.20.5-16.29_i386" from here [http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Frestricted%2Fl%2Flinux-restricted-modules-2.6.20%2Flinux-restricted-modules-2.6.20-16-386_2.6.20.5-16.29_i386.deb&md5sum=730d682b84a5b872f17cd24e8808cf0e&arch=i386&type=security](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Frestricted%2Fl%2Flinux-restricted-modules-2.6.20%2Flinux-restricted-modules-2.6.20-16-386_2.6.20.5-16.29_i386.deb&md5sum=730d682b84a5b872f17cd24e8808cf0e&arch=i386&type=security)
and do a dpkg -i above package name.
after a reboot everything works as it does in kernel-2.6.20-15
Thanks to the Ubuntu forums and the GNU/Linux community at large.

---

