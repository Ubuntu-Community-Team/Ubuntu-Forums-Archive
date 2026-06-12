---
title: "Ubuntu 14.04 64 bit -- which Realtek driver do I use?"
date: 2014-08-20
forum: Networking &amp; Wireless
---

### Post by xigen on 2014-08-20
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false)

I think I am having an issues with r8169 and I would like to use r8168 as recommended in the forums.  

When I go to the RealTek site (listed at top of post) ... there are two candidates for my AMD64 bit system:  version 8.034= and version 1.07.  Which one do I use?

---

### Post by chili555 on 2014-08-20
You want 8.038. Please note that, in order to compile the driver, you also need to install build-essential and linux-headers-generic.

Also note that version 1.07 is for kernel version 2.4. We haven't used 2.4 since Chili had no gray hair!!

Post back if you need additional assistance.

---

### Post by praseodym on 2014-08-20
Installation instructions here:

[http://ubuntuforums.org/showthread.php?t=2238805&p=13095598#post13095598](http://ubuntuforums.org/showthread.php?t=2238805&p=13095598#post13095598)

---

### Post by xigen on 2014-08-21
Woooo!   That worked. 

Many thanks.

---

### Post by xigen on 2014-08-21
hey Chili...   

Well - that worked perfectly.  Then I ran updates and now it does not work.

I tried to patch the new kernel by repeating your instructions.  That did not work.

What would you suggest I do now?

---

### Post by xigen on 2014-08-21
I had a difficult time with the Realtek 8169 driver.   Networking did not work. (motherboard:  Gigabyte 970A-UD3P  Bios F1)

I installed r8168 and blacklisted r8169.  Then, with networking working, I installed upgrades and rebooted.

Then networking did not work.  I repeated the install of r8168, rebooted, and:  no networking.

```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
sudo service network-manager restart

```

If it works: Ok.
If not: Download these files and save them in "Downloads":

[http://media.cdn.ubuntu-de.org/forum....038.00.tar.gz](http://media.cdn.ubuntu-de.org/forum....038.00.tar.gz)

[http://de.archive.ubuntu.com/ubuntu/...buntu5_all.deb](http://de.archive.ubuntu.com/ubuntu/...buntu5_all.deb)

Do not extract the *tar.gz!

Installation:

```

cd ~/Downloads/
sudo dpkg -i *.deb
sudo tar xvf 3005217-r8168-dkms-8.038.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.038.00
sudo dkms build -m r8168-dkms -v 8.038.00
sudo dkms install -m r8168-dkms -v 8.038.00
sudo depmod -a
sudo update-initramfs -u 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf


```

reboot


...................

How do I go about seeing what is happening and fixing it?

Best. MW

---

### Post by chili555 on 2014-08-21
'Now it does not work' covers a lot of ground. What doesn't work? Did you recompile? Can you repeat the steps and copy and paste the result here so we can try to see what went wrong?

---

### Post by xigen on 2014-08-21
I expected the computer to connect to the network.  

when I ping my router:
$ ping 192.168.2.1

connect: network is unreachable

---

### Post by xigen on 2014-08-21
steps taken:  

1) go to your prior (*and awesome) post.
2) repeat everything line for line
3) reboot ... 

4) try to reinstall driver r8168 and blacklist r8169
5) follow your prior instructions.

Unfortunately, my computer is not connected to the network.

---

### Post by chili555 on 2014-08-21
Did r8168 build without error? Did it modprobe without error? Was an interface, ideally eth0 created?```
ifconfig
```Does Network Manager attempt to connect? Do you see an available connection when you click the NM icon? [http://programcounter.files.wordpress.com/2013/01/systray.png](http://programcounter.files.wordpress.com/2013/01/systray.png) Perhaps Wired Connection 1?

Are there messages or clues here?```
cat /var/log/syslog | grep -e eth0 -e etwork | tail -n20
```

---

### Post by xigen on 2014-08-21
```

meow@MeowBatunde:~$ lspci | awk '/net/ {print $1}' | xargs -i% lspci -ks %
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
	Subsystem: Gigabyte Technology Co., Ltd Motherboard

meow@MeowBatunde:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12000 (12.0 KB)  TX bytes:12000 (12.0 KB)

meow@MeowBatunde:~$ cat /var/log/syslog | grep -e eth0 -e etwork | tail -n20
Aug 21 12:00:24 MeowBatunde NetworkManager[2262]:    SCPlugin-Ofono: Acquired D-Bus service com.canonical.NMOfono
Aug 21 12:00:24 MeowBatunde NetworkManager[2262]:    SCPlugin-Ofono: init!
Aug 21 12:00:24 MeowBatunde NetworkManager[2262]:    SCPlugin-Ofono: end _init.
Aug 21 12:00:24 MeowBatunde NetworkManager[2262]: <info> Loaded plugin (null): (null)
Aug 21 12:00:24 MeowBatunde NetworkManager[2262]:    Ifupdown: get unmanaged devices count: 0
Aug 21 12:00:24 MeowBatunde NetworkManager[2262]:    SCPlugin-Ifupdown: (16354064) ... get_connections.
Aug 21 12:00:24 MeowBatunde NetworkManager[2262]:    SCPlugin-Ifupdown: (16354064) ... get_connections (managed=false): return empty list.
Aug 21 12:00:24 MeowBatunde NetworkManager[2262]:    SCPlugin-Ofono: (16137904) ... get_connections.
Aug 21 12:00:24 MeowBatunde NetworkManager[2262]:    SCPlugin-Ofono: (16137904) connections count: 0
Aug 21 12:00:24 MeowBatunde NetworkManager[2262]:    Ifupdown: get unmanaged devices count: 0
Aug 21 12:00:24 MeowBatunde NetworkManager[2262]: <info> monitoring kernel firmware directory '/lib/firmware'.
Aug 21 12:00:24 MeowBatunde NetworkManager[2262]: <info> WiFi enabled by radio killswitch; enabled by state file
Aug 21 12:00:24 MeowBatunde NetworkManager[2262]: <info> WWAN enabled by radio killswitch; enabled by state file
Aug 21 12:00:24 MeowBatunde NetworkManager[2262]: <info> WiMAX enabled by radio killswitch; enabled by state file
Aug 21 12:00:24 MeowBatunde NetworkManager[2262]: <info> Networking is enabled by state file
Aug 21 12:00:24 MeowBatunde NetworkManager[2262]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Aug 21 12:00:24 MeowBatunde NetworkManager[2262]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Aug 21 12:00:24 MeowBatunde NetworkManager[2262]: <info> urfkill disappeared from the bus
Aug 21 12:00:24 MeowBatunde NetworkManager[2262]: <info> ModemManager available in the bus
Aug 21 12:00:35 MeowBatunde NetworkManager[2262]: <info> WiFi hardware radio set enabled



```

---

### Post by chili555 on 2014-08-21
Please also let us see:```
sudo modprobe r8168
dmesg | grep r816
```Thanks.

---

### Post by xigen on 2014-08-21
```


meow@MeowBatunde:~$ sudo modprobe r8168
modprobe: ERROR: could not insert 'r8168': Exec format error

meow@MeowBatunde:~$ dmesg | grep r816
[    2.585166] r8168: disagrees about version of symbol module_layout
[ 4296.490025] r8168: disagrees about version of symbol module_layout
meow@MeowBatunde:~$ 



```

---

### Post by chili555 on 2014-08-21
The instructions you followed were written by praseodym. I compiled the driver from the tar.gz without error and it modprobes without error.

I suggest you PM praseodym and ask him for guidance.

---

### Post by lisati on 2014-08-21
Threads merged.

---

### Post by xigen on 2014-08-21
it looks like eth0 is not being recognized.  I do not see a mac # for eth0

```


meow@MeowBatunde:~$ sudo modprobe r8168
modprobe: ERROR: could not insert 'r8168': Exec format error

meow@MeowBatunde:~$ dmesg | grep r816
[    2.585166] r8168: disagrees about version of symbol module_layout
[ 4296.490025] r8168: disagrees about version of symbol module_layout
meow@MeowBatunde:~$ 


meow@MeowBatunde:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:179 errors:0 dropped:0 overruns:0 frame:0
          TX packets:179 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12849 (12.8 KB)  TX bytes:12849 (12.8 KB)




```

---

### Post by praseodym on 2014-08-22
Please run:
```

sudo dkms autoinstall
modinfo r8168 | egrep 'versi|filen'
locate r8168.ko | grep lib
lsmod
dmesg | grep r8
```

---

### Post by xigen on 2014-08-22
```

  117  sudo dkms autoinstall
  118  modinfo r8168 | grep 'versi|filen'
  119  locate r 8168.ko | grep lib
  120  lsmod
  121  dmesg | grep r8
  122  history
meow@MeowBatunde:~$ 

  117  sudo dkms autoinstall
no output

  118  modinfo r8168 | grep 'versi|filen'
meow@MeowBatunde:~$ !118
modinfo r8168 | grep 'versi|filen'



  119  locate r 8168.ko | grep lib
Long scroll of text.. no output.
.
.
.
/var/lib/xfonts/excluded-aliases
/var/lib/xkb/README.compiled
/var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
/var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
/var/lib/xml-core/catalog
/var/lib/xml-core/xml-core
meow@MeowBatunde:~$ 



  120  lsmod

meow@MeowBatunde:~$ !120
lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
usb_storage            62209  1 
snd_hda_codec_hdmi     46254  1 
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             391196  10 bnep,rfcomm
hid_generic            12548  0 
kvm_amd                59987  0 
kvm                   451511  1 kvm_amd
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
snd_hda_intel          52355  2 
lrw                    13286  1 aesni_intel
snd_ice1712            75235  2 
gf128mul               14951  1 lrw
snd_cs8427             14258  1 snd_ice1712
snd_hda_codec         192906  2 snd_hda_codec_hdmi,snd_hda_intel
glue_helper            13990  1 aesni_intel
snd_i2c                14147  2 snd_ice1712,snd_cs8427
ablk_helper            13597  1 aesni_intel
snd_ice17xx_ak4xxx     13315  1 snd_ice1712
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hwdep              13602  1 snd_hda_codec
snd_ak4xxx_adda        18703  2 snd_ice1712,snd_ice17xx_ak4xxx
usbhid                 52570  0 
snd_mpu401_uart        14169  1 snd_ice1712
snd_ac97_codec        130285  1 snd_ice1712
hid                   106148  2 hid_generic,usbhid
ac97_bus               12730  1 snd_ac97_codec
nouveau              1097199  3 
snd_pcm               102099  5 snd_ice1712,snd_ac97_codec,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
serio_raw              13462  0 
snd_seq_midi           13324  0 
mxm_wmi                13021  1 nouveau
snd_seq_midi_event     14899  1 snd_seq_midi
wmi                    19177  2 mxm_wmi,nouveau
video                  19476  1 nouveau
snd_rawmidi            30144  2 snd_mpu401_uart,snd_seq_midi
fam15h_power           13119  0 
ttm                    85115  1 nouveau
k10temp                13126  0 
drm_kms_helper         53081  1 nouveau
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
edac_core              62291  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
edac_mce_amd           22617  0 
drm                   303102  5 ttm,drm_kms_helper,nouveau
snd                    69238  24 snd_ice1712,snd_ac97_codec,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_i2c,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_ak4xxx_adda,snd_hda_intel,snd_mpu401_uart,snd_seq_device,snd_cs8427,snd_seq_midi
i2c_algo_bit           13413  1 nouveau
soundcore              12680  1 snd
sp5100_tco             13979  0 
i2c_piix4              22155  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
mac_hid                13205  0 
pata_acpi              13038  0 
psmouse               106678  0 
ahci                   25819  2 
pata_atiixp            13271  0 
libahci                32560  1 ahci

  121  dmesg | grep r8
meow@MeowBatunde:~$ dmesg | grep r8
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88023ec00000 s86336 r8192 d24256 u262144
[    0.000000] pcpu-alloc: s86336 r8192 d24256 u262144 alloc=1*2097152
[    2.546882] r8168: disagrees about version of symbol module_layout




```

---

### Post by praseodym on 2014-08-22
Are the kernel headers installed?
```

sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms
```

---

### Post by xigen on 2014-08-22
```

sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms


meow@MeowBatunde:~$ sudo apt-get install --reinstall linux-headers-generic-$(uname -r) build-essential dkms
[sudo] password for meow: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-generic-3.13.0-34-generic
E: Couldn't find any package by regex 'linux-headers-generic-3.13.0-34-generic'
meow@MeowBatunde:~$ sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev fakeroot g++ g++-4.8 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libfakeroot
  libstdc++-4.8-dev
Suggested packages:
  debian-keyring g++-multilib g++-4.8-multilib gcc-4.8-doc libstdc++6-4.8-dbg
  libstdc++-4.8-doc
The following NEW packages will be installed:
  build-essential dpkg-dev fakeroot g++ g++-4.8 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libfakeroot
  libstdc++-4.8-dev
0 upgraded, 10 newly installed, 3 reinstalled, 0 to remove and 4 not upgraded.
Need to get 9,041 kB/9,755 kB of archives.
After this operation, 32.1 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main libstdc++-4.8-dev amd64 4.8.2-19ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main g++-4.8 amd64 4.8.2-19ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main g++ amd64 4:4.8.2-1ubuntu6
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main dpkg-dev all 1.17.5ubuntu5.3
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main build-essential amd64 11.6ubuntu6
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main dkms all 2.2.0.3-1.1ubuntu5
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main libfakeroot amd64 1.20-3ubuntu2
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main fakeroot amd64 1.20-3ubuntu2
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main libalgorithm-diff-perl all 1.19.02-3
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main libalgorithm-diff-xs-perl amd64 0.04-2build4
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty/main libalgorithm-merge-perl all 0.08-2
  Could not resolve 'us.archive.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main dpkg-dev all 1.17.5ubuntu5.3
  Could not resolve 'security.ubuntu.com'
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.8/libstdc++-4.8-dev_4.8.2-19ubuntu1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.8/g++-4.8_4.8.2-19ubuntu1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.8.2-1ubuntu6_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.17.5ubuntu5.3_all.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.6ubuntu6_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/f/fakeroot/libfakeroot_1.20-3ubuntu2_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/f/fakeroot/fakeroot_1.20-3ubuntu2_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libalgorithm-diff-perl/libalgorithm-diff-perl_1.19.02-3_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libalgorithm-diff-xs-perl/libalgorithm-diff-xs-perl_0.04-2build4_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libalgorithm-merge-perl/libalgorithm-merge-perl_0.08-2_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
meow@MeowBatunde:~$ 



```

---

### Post by praseodym on 2014-08-23
Obviously, you have the proposed and/or backports sources activated. Here, kernel 3.13-32 is active. You need these files:

[http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.13.0-34_3.13.0-34.60_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.13.0-34_3.13.0-34.60_all.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.13.0-34-generic_3.13.0-34.60_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.13.0-34-generic_3.13.0-34.60_amd64.deb)

Save them in "Downloads" and install via
```

sudo dpkg -i ~/Downloads/*.deb
sudo dkms autoinstall
sudo modprobe -v r8168
```

---

### Post by xigen on 2014-08-23
hmmmmm.....  trouble:

Exec format error ... 

```

meow@MeowBatunde:~$ sudo dpkg -i ~/Downloads/ *.deb
[sudo] password for meow: 
dpkg-split: error: error reading /home/meow/Downloads/: Is a directory
dpkg: error processing archive /home/meow/Downloads/ (--install):
 subprocess dpkg-split returned error exit status 2
dpkg: error processing archive *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/meow/Downloads/
 *.deb
meow@MeowBatunde:~$ cd Downloads/
meow@MeowBatunde:~/Downloads$ ls
linux-headers-3.13.0-34_3.13.0-34.60_all.deb  linux-headers-3.13.0-34-generic_3.13.0-34.60_amd64.deb
meow@MeowBatunde:~/Downloads$ sudo dpkg -i *.deb
(Reading database ... 195905 files and directories currently installed.)
Preparing to unpack linux-headers-3.13.0-34_3.13.0-34.60_all.deb ...
Unpacking linux-headers-3.13.0-34 (3.13.0-34.60) over (3.13.0-34.60) ...
Preparing to unpack linux-headers-3.13.0-34-generic_3.13.0-34.60_amd64.deb ...
Unpacking linux-headers-3.13.0-34-generic (3.13.0-34.60) over (3.13.0-34.60) ...
Setting up linux-headers-3.13.0-34 (3.13.0-34.60) ...
Setting up linux-headers-3.13.0-34-generic (3.13.0-34.60) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
meow@MeowBatunde:~/Downloads$ sudo dkms autoinstall


meow@MeowBatunde:~/Downloads$ sudo modprobe -v r8168
insmod /lib/modules/3.13.0-34-generic/updates/dkms/r8168.ko 
modprobe: ERROR: could not insert 'r8168': Exec format error
meow@MeowBatunde:~/Downloads$ 





```

---

### Post by praseodym on 2014-08-23
Obviously, its not compiling with this kernel. Use kernel 3.13-32 instead

---

### Post by xigen on 2014-08-23
still getting the   Exec format error

```

meow@MeowBatunde:~$ cd Downloads/
meow@MeowBatunde:~/Downloads$ ls
linux-headers-3.13.0-32-generic_3.13.0-32.57_amd64.deb  linux-headers-3.13.0-32-generic_3.13.0-32.57_i386.deb

meow@MeowBatunde:~/Downloads$ sudo dpkg -i *.deb
[sudo] password for meow: 

Selecting previously unselected package linux-headers-3.13.0-32-generic.
(Reading database ... 195905 files and directories currently installed.)
Preparing to unpack linux-headers-3.13.0-32-generic_3.13.0-32.57_amd64.deb ...
Unpacking linux-headers-3.13.0-32-generic (3.13.0-32.57) ...
Preparing to unpack linux-headers-3.13.0-32-generic_3.13.0-32.57_i386.deb ...
Unpacking linux-headers-3.13.0-32-generic (3.13.0-32.57) over (3.13.0-32.57) ...
More than one copy of package linux-headers-3.13.0-32-generic has been unpacked
 in this run !  Only configuring it once.
dpkg: dependency problems prevent configuration of linux-headers-3.13.0-32-generic:
 linux-headers-3.13.0-32-generic depends on linux-headers-3.13.0-32.
 linux-headers-3.13.0-32-generic depends on libc6 (>= 2.11).

dpkg: error processing package linux-headers-3.13.0-32-generic (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-3.13.0-32-generic

meow@MeowBatunde:~/Downloads$ sudo dkms autoinstall
meow@MeowBatunde:~/Downloads$ sudo modprobe -v r8168
insmod /lib/modules/3.13.0-34-generic/updates/dkms/r8168.ko 
modprobe: ERROR: could not insert 'r8168': Exec format error



```

---

### Post by praseodym on 2014-08-23
[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.13.0-32_3.13.0-32.57_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.13.0-32_3.13.0-32.57_all.deb)

instead of linux-headers-3.13.0-32-generic_3.13.0-32.57_i386.deb


Edit: here it compiles without error

**3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux**

---

### Post by xigen on 2014-08-23
Source for both i386 and amd64
[http://security.ubuntu.com/ubuntu/pool/main/l/linux/](http://security.ubuntu.com/ubuntu/pool/main/l/linux/)

```

meow@MeowBatunde:~/Downloads$ ls
linux-headers-3.13.0-32_3.13.0-32.57_all.deb  linux-headers-3.13.0-32-generic_3.13.0-32.57_amd64.deb
meow@MeowBatunde:~/Downloads$ sudo dpkg -i *.deb
[sudo] password for meow: 
Selecting previously unselected package linux-headers-3.13.0-32.
(Reading database ... 205570 files and directories currently installed.)
Preparing to unpack linux-headers-3.13.0-32_3.13.0-32.57_all.deb ...
Unpacking linux-headers-3.13.0-32 (3.13.0-32.57) ...
Preparing to unpack linux-headers-3.13.0-32-generic_3.13.0-32.57_amd64.deb ...
Unpacking linux-headers-3.13.0-32-generic (3.13.0-32.57) over (3.13.0-32.57) ...
Setting up linux-headers-3.13.0-32 (3.13.0-32.57) ...
Setting up linux-headers-3.13.0-32-generic (3.13.0-32.57) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
meow@MeowBatunde:~/Downloads$ sudo dkms autoinstall
meow@MeowBatunde:~/Downloads$ sudo modprobe -v r8168
insmod /lib/modules/3.13.0-34-generic/updates/dkms/r8168.ko 
modprobe: ERROR: could not insert 'r8168': Exec format error


2nd try.  I deleted all prior .deb files on the usb drive and re-downloaded the .deb files from security.ubuntu.com   

meow@MeowBatunde:~/Downloads$ sudo dpkg -i *.deb
(Reading database ... 220701 files and directories currently installed.)
Preparing to unpack linux-headers-3.13.0-32_3.13.0-32.57_all.deb ...
Unpacking linux-headers-3.13.0-32 (3.13.0-32.57) over (3.13.0-32.57) ...
Preparing to unpack linux-headers-3.13.0-34-generic_3.13.0-34.60_amd64.deb ...
Unpacking linux-headers-3.13.0-34-generic (3.13.0-34.60) over (3.13.0-34.60) ...
Setting up linux-headers-3.13.0-32 (3.13.0-32.57) ...
Setting up linux-headers-3.13.0-34-generic (3.13.0-34.60) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
meow@MeowBatunde:~/Downloads$ sudo dkms autoinstall
meow@MeowBatunde:~/Downloads$ sudo modprobe -v r8168
insmod /lib/modules/3.13.0-34-generic/updates/dkms/r8168.ko 
modprobe: ERROR: could not insert 'r8168': Exec format error
meow@MeowBatunde:~/Downloads$ 

3rd try with all download files from ubuntu.security.com

linux-image-3.2.0-32-generic_3.2.0-32.51_amd64.deb  linux-image-3.2.0-32-generic_3.2.0-32.51_i386.deb
meow@MeowBatunde:~/Downloads$ sudo dpkg -i *.deb
Selecting previously unselected package linux-image-3.2.0-32-generic.
(Reading database ... 220701 files and directories currently installed.)
Preparing to unpack linux-image-3.2.0-32-generic_3.2.0-32.51_amd64.deb ...
Done.
Unpacking linux-image-3.2.0-32-generic (3.2.0-32.51) ...
Preparing to unpack linux-image-3.2.0-32-generic_3.2.0-32.51_i386.deb ...
Done.
Unpacking linux-image-3.2.0-32-generic (3.2.0-32.51) over (3.2.0-32.51) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-32-generic /boot/vmlinuz-3.2.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-32-generic /boot/vmlinuz-3.2.0-32-generic
More than one copy of package linux-image-3.2.0-32-generic has been unpacked
 in this run !  Only configuring it once.
Setting up linux-image-3.2.0-32-generic (3.2.0-32.51) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-32-generic /boot/vmlinuz-3.2.0-32-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-32-generic /boot/vmlinuz-3.2.0-32-generic
Error! Your kernel headers for kernel 3.2.0-32-generic cannot be found.
Please install the linux-headers-3.2.0-32-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-32-generic /boot/vmlinuz-3.2.0-32-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-32-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-32-generic /boot/vmlinuz-3.2.0-32-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-32-generic /boot/vmlinuz-3.2.0-32-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-32-generic /boot/vmlinuz-3.2.0-32-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found linux image: /boot/vmlinuz-3.2.0-32-generic
Found initrd image: /boot/initrd.img-3.2.0-32-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
meow@MeowBatunde:~/Downloads$ sudo dkms autoinstall
meow@MeowBatunde:~/Downloads$ sudo modprobe -v r8168
insmod /lib/modules/3.13.0-34-generic/updates/dkms/r8168.ko 
modprobe: ERROR: could not insert 'r8168': Exec format error





```

---

### Post by praseodym on 2014-08-23
Ok, uninstall it:

```
sudo dkms remove -m r8168-dkms -v 8.038.00 --all
sudo rm -r /usr/src/r8168-dkms-8.038.00 
```

Reboot and install the driver again.

---

### Post by xigen on 2014-08-23
It finally works!  woot woo.. and thank you.

I went back to fist principals and tried the 'most simple' solution.

1) Go to the RealTek site and look very carefully at the driver instructions
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false)

I took Chili555's advice and got the latest driver:
LINUX driver for kernel 3.x and 2.6.x and 2.4.x
	8.038	2014/3/4

in the README of the tar.gz file:
<Quick install with proper kernel settings>
	Unpack the tarball :
		# tar vjxf r8168-8.aaa.bb.tar.bz2

	Change to the directory:
		# cd r8168-8.aaa.bb

	If you are running the target kernel, then you should be able to do :

		**# ./autorun.sh	(as root or with sudo)**

	You can check whether the driver is loaded by using following commands.

		# lsmod | grep r8168
		# ifconfig -a


2) use the ./autorun.sh file  (*included with the driver download)
Wha!La!  ... it worked.

....

In the future will my r8168 driver continue to work if I update the kernel?

Would it make sense to just spend some money and buy a new NIC card which does not have these issues?  If so - what linux h/w resource would you recommend?

...

As always a big thank you.   I really appreciate your help.

---

### Post by praseodym on 2014-08-23
No, you need to compile again. Tried the dkms one? This one does compile automatically

---

