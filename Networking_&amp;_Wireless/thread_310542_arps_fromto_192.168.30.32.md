---
title: "arps from/to 192.168.30.32 ?"
date: 2006-12-01
forum: Networking &amp; Wireless
---

### Post by WW78 on 2006-12-01
I just imaged two machines to Ubuntu 6.06 LTS server.  Each machine is generating arp requests with an ARP Sender and Target address of 192.168.30.32.  This address does not match the address I've statically assigned to the NICs.  Any idea what's causing these ARPs?  :confused: 

Thanks very much.

---

### Post by Slim Odds on 2006-12-01
> **WW78 said:**
> I just imaged two machines to Ubuntu 6.06 LTS server.  Each machine is generating arp requests with an ARP Sender and Target address of 192.168.30.32.  This address does not match the address I've statically assigned to the NICs.  Any idea what's causing these ARPs?  :confused: 

Thanks very much.

A little more information about your network would be helpful. A dump of the ARP packet might also be helpful. What else is on the network?

---

### Post by WW78 on 2006-12-01
Each of these two machines are on a single vlan, 500, on a switch and there's nothing else on that vlan other than these two machines.

In other words,

host_A eth0: mgmnt IP
host_A eth1: on Vlan 500, IP 10.20.10.2

host_B eth0: mgmnt IP
host_B eth1: on Vlan 500, IP 10.20.10.3

I'm seeing host_A and host_B both generate these arp requests via their eth1 interfaces.  I'm attemting to attach a packet capture that I obtained by adding a packet sniffer to the VLAN and disabling host_B's eth1.  In case that doesn't work, here's the raw hex of the ARP packet (cut-and-paste from ethereal):

0000  ff ff ff ff ff ff 00 0e  0c 4b 73 d4 08 06 00 01   ........ .Ks.....
0010  08 00 06 04 00 01 00 0e  0c 4b 73 d4 c0 a8 1e 20   ........ .Ks.... 
0020  ff ff ff ff ff ff c0 a8  1e 20 00 00 00 00 00 00   ........ . ......
0030  00 00 00 00 00 00 00 00  00 00 00 00               ........ ....    

0030  00 00 00 00 00 00 00 00  00 00 00 00 

When I disable eth1 for both hosts, then I no longer see the arps (via the packet sniffer).

Thanks in advance for any suggestions.

---

### Post by WW78 on 2006-12-01
Another thought I had is to convey that I configured the addresses on eth1 for both machines via "sudo ifconfig...".  So, nothing exists in /etc/network/interfaces for eth1 for either machine as shown below.  Perhaps this is the cause of the arps being sent?

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 10.89.150.80
        netmask 255.255.255.128
        network 10.89.150.0
        broadcast 10.89.150.127
        gateway 10.89.150.126

---

### Post by Slim Odds on 2006-12-01
Well, something doesn't make sense at all.

ARP is a LAN thing, therefore there is no reason for machine on a 10.X.X.X network to have ARP's for 192.168.X.X address.

Could you perhaps attach a .pcap from Ethereal (or WireShark)? So that I can get a little better look at the data.

---

### Post by WW78 on 2006-12-01
Yes, I can give that a try.  I attempted to attach the file in post #3 above, but it apparently did not work.  I suspect it's because the file extension wasn't one of the accepted types.

Trying again now.  The file is named arp.pcap and I've zipped it to arp.zip.

Thanks again.

---

### Post by Slim Odds on 2006-12-01
Ok, first Ethereal calls this a Gratuitous ARP [http://wiki.ethereal.com/Gratuitous_ARP](http://wiki.ethereal.com/Gratuitous_ARP)

Secondly, the MAC address in the ARP packet tells you where it's coming from-> 00:0e:0c:4b:73:d4

So see who that is.

---

### Post by WW78 on 2006-12-02
Thanks for your help so far.  That MAC belongs to eth1 from my Ubuntu machine that I described previously as host_A.

So, that's what puzzles me.  Each of my Ubuntu machines is generating these gratuitous arps.  I haven't found any service related to that IP address, 192.168.30.32.

Here's the ifconfig output for eth1 from that host_A (in the HWaddr field below, I had to change the D4 to d4 so it wouldn't be interpreted as an emoticon):
eth1      Link encap:Ethernet  HWaddr 00:0E:0C:4B:73:d4  
          inet addr:10.20.2.2  Bcast:10.20.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:cff:fe4b:73d4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:75997 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81035 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5796550 (5.5 MiB)  TX bytes:6116515 (5.8 MiB)
          Base address:0xdf80 Memory:dfee0000-dff00000


So, the question is, why are my Ubuntu machines generating these gratuitous ARPs?

---

### Post by WW78 on 2006-12-03
I'm wondering if this problem may be hardware related instead of software related.  I began thinking this when I rebooted one of the machines generating these ARPs.

I rebooted the machine, but forgot that I still had the Ubuntu 6.06 Server CD in that machine's drive.  So, it booted to the disk.  I can't check it now since I'm remote, but I believe that this Server CD does not automatically start Ubuntu.  Consequently, the machine is likely sitting at a prompt asking to start an install or something like that.

Well, the ARPs are still continuing but I believe Ubuntu isn't up and running.  So, I'm suspecting that the NIC itself is generating these ARPs.

Still investigating...

---

### Post by Naoi on 2008-03-26
This issue cropped up for me just recently so even though this is an old thread I thought I'd use it to document how I turned off the gratuitous arps on my  Intel SE7221BK1-E server board.

Just FYI I'm in no way a network expert, so please forgive any mistakes as I am relying on various threads I came by in Googling this issue. ;)

This [ **link**]("http://buttersideup.com/docs/howto/IPMI_on_Debian.html ") describes the hardware and software involved, which is called IPMI and stands for Intelligent Platform Management Interface.  Although the HOWTO part didn't apply directly to my particular solution it cleared up a lot of my confusion over where these arps were coming from and why.

To quote the link above

> IPMI stands for Intelligent Platform Management Interface and is an open standard for machine health, and control (including remote control), and is implemented by many hardware vendors - Intel is one of the originators, and early adopters of the standard.  Here are some useful things that IPMI can do on the SR2300 with Linux:

    * Check on hardware health, and report on problems (via the OS, or autonomously via the network)
    * Provide a watchdog timer (in case the OS goes away, or programs can otherwise not run, the machine will be reset)
    * Provide remote "lights out" access to both the Linux console, and the BIOS via ethernet (no serial concentrators, multi-port serial cards, or extra cabling required)
    * Provide remote, OS independent control over the reset, and power buttons via ethernet (no funny remote control power sockets, relays, or other hacks required)
    * Provide remote control of a server over a modem connection
    * Make emergency remote management possible from a variety of simple devices (e.g. PDAs)
...

It is useful to know a bit about how IPMI does its stuff - so I'll give an overview, and try to bust some weird IPMI/Intel jargon.  There is a second autonomous computer on the motherboard (or baseboard, in IPMI's politically correct / obfusicated language), this is a very simple, low power-consumption device, which should operate as long as power is connected to the machine (including when the majority of the server is powered down) - in IPMI speak, this computer is called the BMC - the Baseboard Management Controller - it uses its own firmware, which is independent of the system BIOS.

If you have an Intel motherboard it comes with software to control the BMC in various ways, but unfortunately the software only works on Windows or Redhat/Fedora Linux, and after failed tries to get it to work remotely from another Windows machine and reading that the Linux package wouldn't install properly on other versions of Linux (I didn't try it on Ubuntu though) I decided to try the open source versions of IPMI.

[**Freeipmi**]("http://www.gnu.org/software/freeipmi/") and openipmi are two such programs and freeipmi worked for me in the end.

I couldn't find a debian/ubuntu version of freeipmi but I did fine this [ **Fedora rpm version**]("http://rpmfind.net/linux/RPM/fedora/devel/x86_64/freeipmi-0.5.1-3.fc9.i386.html") which I was able to convert to a debian package using alien then install.  I wasn't sure how to compile and install the source version so this was "the path of least resistance" for me. :)

After downloading the .rpm file I did the following to install the package:

[INDENT]sudo alien -d ipmiutil-2.0.9-1.i386.rpm
sudo dpkg -i  ipmiutil_2.0.9-2_i386.deb
sudo ln -s /usr/lib/libcrypto.so.0.9.8 /lib/libcrypto.so.4[/INDENT]

From this long [**thread**]("http://www.nabble.com/problem-with-freeipmi-0.5.3-and-intel-SE7221BK1-E-td14865773.html") I found I decided to try and load the three modules below, the third one gave me an error so it apparently wasn't necessary, and in fact I don't know if I needed to load any of them manually, but I went ahead and did it anyway.

[INDENT]sudo modprobe i2c-dev
sudo modprobe i2c-core
sudo modprobe i2c-i810[/INDENT]

Once freeipmi was working (at least in a basic manner, afaik there are problems reading the sensors but I haven't tried it) I was able to turn off the gratuitous arps by reading this [**user's guide**]("http://gnu.freemirror.de/savannah-checkouts/gnu/freeipmi/freeipmi.pdf")  and using the "bmc-config" command (with a change/correction for the --key-pair option based on "bmc-config --help"):

[INDENT]sudo bmc-config --commit --key-pair  "Lan_Conf_Misc:Enable_Gratuitous_ARPs=No" -D SSIF 
--driver-address=0x42 --driver-device=/dev/i2c-0 --register-spacing=1[/INDENT]

The options in the command are particular to motherboards using the SSIF driver, for other types of boards I'd suggest reading this [**general description**]("http://openipmi.sourceforge.net/IPMI.txt"), this  [**Ubuntu thread**]("https://help.ubuntu.com/community/IPMI") or this [ **other thread**]("http://wiki.adamsweet.org/doku.php?id=ipmi_on_linux") (they didn't work for me but helped my understanding).

If anyone has any tips to add here please do, I arrived at this solution after lots of trial and error and I'm sure there's a better/quicker way but this worked for me.  

I'd like to use the ipmi  software to monitor the hardware so any information on how to get this to work on my type of server board would be greatly appreciated. :)

---

