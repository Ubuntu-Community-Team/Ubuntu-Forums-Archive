---
title: "Need my internet connection back"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by halovivek on 2009-02-13
HI
i tried to install Virtualization With KVM On Ubuntu 8.10 by using this [thread]("http://howtoforge.com/virtualization-with-kvm-on-ubuntu-8.10").
i have modified but i got internet disconnected.
i have uninstalled some what. but till now i am not getting the internet connection back. i have posted the result below


gurudheva@gurudheva-laptop:~$ sudo su 
[sudo] password for gurudheva: 
[COLOR="Red"]root@gurudheva-laptop:/home/gurudheva#  gedit  /etc/network/interfaces 
root@gurudheva-laptop:/home/gurudheva# /etc/init.d/networking restart 
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0. 
Ignoring unknown interface br0=br0. 
                                                                         [ OK ] [/COLOR]


root@gurudheva-laptop:/home/gurudheva# sudo apt-get remove --purge ubuntu-virt-server python-vm-builder 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
The following packages were automatically installed and are no longer required: 
  texlive-common libsane-dev prelink libsm-dev libjack0.100.0-dev 
  libsgmls-perl libice-dev debootstrap libxrandr-dev libexpat1-dev debhelper 
  libaudiofile-dev libpthread-stubs0 libgpg-error-dev libxslt1-dev bison 
  docbook-utils docbook-dsssl comerr-dev libsp1c2 g++-4.2 libxfixes-dev 
  g++-4.3 lmodern libgl1-mesa-dev libasound2-dev python-cheetah libostyle1c2 
  texlive-pstricks libtiff4-dev x11proto-xinerama-dev docbook-xsl 
  libncurses5-dev texlive-base-bin x11proto-render-dev virtualbox-ose-source 
  libxi-dev m4 texlive-latex-base texlive-fonts-recommended po-debconf 
  libcapi20-3 sp jadetex libxxf86vm-dev libkrb5-dev g++ lib32ncurses5-dev 
  libtiffxx0c2 libfontconfig1-dev liblcms1-dev intltool-debian docbook-to-man 
  x11proto-kb-dev x11proto-randr-dev texlive-generic-recommended 
  libxinerama-dev libstdc++6-4.2-dev texlive-latex-recommended libgif-dev 
  kpartx mesa-common-dev fontforge openjade libelfg0 
  texlive-latex-recommended-doc xtrans-dev dvipdfmx lib32asound2-dev 
  latex-beamer gettext prosper x11proto-input-dev libexif-dev libxcb-xlib0-dev 
  tipa libusb-dev texlive-latex-base-doc sgmlspl latex-xcolor libuninameslist0 
  x11proto-fixes-dev libgphoto2-2-dev libieee1284-3-dev lib32z1-dev 
  libglu1-mesa-dev x11proto-xf86vidmode-dev x11proto-xext-dev libssl-dev 
  libxt-dev libxext-dev libtasn1-3-dev texlive-fonts-recommended-doc pgf 
  zlib1g-dev libcups2-dev libxml2-dev libspiro0 libesd0-dev flex 
  libfreetype6-dev build-essential libxau-dev dpkg-dev libstdc++6-4.3-dev 
  docbook-xsl-doc-html libgcrypt11-dev libhal-dev libaudio-dev texlive-base 
  libkadm55 libxcomposite-dev libxrender-dev texlive-doc-base html2text 
  libx11-dev texlive-base-bin-doc python-libvirt x11proto-composite-dev 
  libgnutls-dev libdbus-1-dev libxcb1-dev libmail-sendmail-perl libjpeg62-dev 
  libcapi20-dev libhal-storage-dev libsys-hostname-long-perl 
  texlive-pstricks-doc tex-common libjack-dev x11proto-core-dev libxdmcp-dev 
  libpthread-stubs0-dev docbook libxcursor-dev libldap2-dev libpng12-dev 
Use 'apt-get autoremove' to remove them. 
The following packages will be REMOVED: 
  python-vm-builder* ubuntu-virt-server* 
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded. 
After this operation, 2712kB disk space will be freed. 
Do you want to continue [Y/n]? y 
(Reading database ... 184396 files and directories currently installed.) 
Removing python-vm-builder ... 
Purging configuration files for python-vm-builder ... 
Removing ubuntu-virt-server ... 
Processing triggers for man-db ... 

root@gurudheva-laptop:/home/gurudheva# ifconfig 
br0       Link encap:Ethernet  HWaddr 00:1e:ec:4b:e0:f7  
          inet addr:82.182.221.135  Bcast:82.182.0.255  Mask:255.0.0.0 
          inet6 addr: fe80::21e:ecff:fe4b:e0f7/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:1026 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:94959 (94.9 KB)  TX bytes:7198 (7.1 KB) 

eth0      Link encap:Ethernet  HWaddr 00:1e:ec:4b:e0:f7  
          inet6 addr: fe80::21e:ecff:fe4b:e0f7/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:1142 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:127242 (127.2 KB)  TX bytes:7428 (7.4 KB) 
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:1f:e2:ae:88:cc  
          inet6 addr: fe80::21f:e2ff:feae:88cc/64 Scope:Link 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:121 
          TX packets:0 errors:5 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:544 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:544 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:42744 (42.7 KB)  TX bytes:42744 (42.7 KB) 

vnet0     Link encap:Ethernet  HWaddr 0a:81:31:b3:86:90  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0 
          inet6 addr: fe80::881:31ff:feb3:8690/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:5942 (5.9 KB)

---

### Post by x33a on 2009-02-13
first of all always keep a backup of your interfaces file.

now, i think you should run pppoeconf and your connection should be back. if it doesn't work, post your /etc/network/interfaces file here.

---

### Post by halovivek on 2009-02-13
root@gurudheva-laptop:/home/gurudheva# gedit /etc/network/interfaces
root@gurudheva-laptop:/home/gurudheva# /etc/init.d/networking restart
* Reconfiguring network interfaces... Ignoring unknown interface eth0=eth0.
Ignoring unknown interface br0=br0.
[ OK ] 

[COLOR="Red"]
i have edited the network interface back to eth0 
restarted the system and it is working fine.[/COLOR]

---

### Post by rgb96 on 2009-02-13
so it's fixed now?

---

### Post by halovivek on 2009-02-13
Yes I have solved by removing the network configuration.

---

