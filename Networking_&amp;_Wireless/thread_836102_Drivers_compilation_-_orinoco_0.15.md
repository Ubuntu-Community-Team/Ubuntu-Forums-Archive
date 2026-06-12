---
title: "Drivers compilation - orinoco 0.15"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by Zielevitz on 2008-06-21
Hello  :)

I use Kubuntu 7.10 and I have problem with compilation of orinoco 0.15x drivers. Here is what I do:

* Download the drivers in version 0.15 from [official site]("http://www.nongnu.org/orinoco/downloads/") and unpack them
* make - I get following output:
```
ziells@inferno:~/Desktop/orinoco-0.15$ make
make -C /usr/src/linux-headers-2.6.22-14-generic M=/home/ziells/Desktop/orinoco-0.15 KERNELRELEASE=2.6.22-14-generic modules
make[1]: Wej&#347;cie do katalogu `/usr/src/linux-headers-2.6.22-14-generic'
/home/ziells/Desktop/orinoco-0.15/Kbuild:34: *** Wireless extensions are not enabled. Stop.
make[1]: *** [_module_/home/ziells/Desktop/orinoco-0.15] B&#322;&#261;d 2
make[1]: Opuszczenie katalogu `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] B&#322;&#261;d 2
```

* I found information about this bug and the way to fix it is to edit 33th line of Kbuild file and replace ```
ifndef CONFIG_NET_RADIO
``` with ```
ifndef CONFIG_WIRELESS_EXT
```

* also, there is nesecarry to comment those lines: ```
ifdef CONFIG_HERMES
$(error This driver is already enabled in the kernel)
endif
```

* Now, after **make** command, the output is following:

```
ziells@inferno:~/Desktop/orinoco-0.15$ sudo make
make -C /usr/src/linux-headers-2.6.22-14-generic M=/home/ziells/Desktop/orinoco-0.15 KERNELRELEASE=2.6.22-14-generic modules
make[1]: Wej&#347;cie do katalogu `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/ziells/Desktop/orinoco-0.15/orinoco.o
/home/ziells/Desktop/orinoco-0.15/orinoco.c: In function &#8216;orinoco_stat_gather&#8217;:
/home/ziells/Desktop/orinoco-0.15/orinoco.c:720: error: &#8216;struct sk_buff&#8217; has no member named &#8216;mac&#8217;
/home/ziells/Desktop/orinoco-0.15/orinoco.c: In function &#8216;orinoco_rx_monitor&#8217;:
/home/ziells/Desktop/orinoco-0.15/orinoco.c:801: error: &#8216;struct sk_buff&#8217; has no member named &#8216;mac&#8217;
/home/ziells/Desktop/orinoco-0.15/orinoco.c:2466:67: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/ziells/Desktop/orinoco-0.15/orinoco.c: In function &#8216;alloc_orinocodev&#8217;:
/home/ziells/Desktop/orinoco-0.15/orinoco.c:2466: error: &#8216;INIT_WORK&#8217; undeclared (first use in this function)
/home/ziells/Desktop/orinoco-0.15/orinoco.c:2466: error: (Each undeclared identifier is reported only once
/home/ziells/Desktop/orinoco-0.15/orinoco.c:2466: error: for each function it appears in.)
/home/ziells/Desktop/orinoco-0.15/orinoco.c:2467:68: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/ziells/Desktop/orinoco-0.15/orinoco.c:2468:75: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/ziells/Desktop/orinoco-0.15/orinoco.c: In function &#8216;orinoco_get_drvinfo&#8217;:
/home/ziells/Desktop/orinoco-0.15/orinoco.c:4330: error: &#8216;struct net_device&#8217; has no member named &#8216;class_dev&#8217;
/home/ziells/Desktop/orinoco-0.15/orinoco.c:4331: error: &#8216;struct net_device&#8217; has no member named &#8216;class_dev&#8217;
make[2]: *** [/home/ziells/Desktop/orinoco-0.15/orinoco.o] B&#322;&#261;d 1
make[1]: *** [_module_/home/ziells/Desktop/orinoco-0.15] B&#322;&#261;d 2
make[1]: Opuszczenie katalogu `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] B&#322;&#261;d 2
```

My iwconfig return this:```
ziells@inferno:~/Desktop/orinoco-0.15$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"essid"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:F0:89:0C:70
          Bit Rate:1 Mb/s   Sensitivity:1/3
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=17/92  Signal level=-87 dBm  Noise level=-104 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:339
          Tx excessive retries:121  Invalid misc:0   Missed beacon:0
```

Is this the fault of wrong version of linux-headers? Is the problem known by someone?

---

### Post by chili555 on 2008-06-21
This is from the official site you linked:> Q2: How do I compile/install the driver?

The easiest way is to use the version included in the kernel source ...Your iwconfig looks very healthy, like your interface is all set up and ready to go. First, let's check to see if the module is loaded:```
lsmod | grep orinoco
```I'll bet *orinoco* is already loaded. Next, let's see if we can find your network:```
sudo iwlist eth1 scan
```Now, let's try to connect:```
sudo iwconfig eth1 essid <network_you_scanned>
sudo iwconfig eth1 key <any_encryption_here?>
sudo dhclient eth1
```The only thing that concernes me is:> Link Quality=17/92

---

