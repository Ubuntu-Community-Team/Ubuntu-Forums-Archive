---
title: "Internet on VMware"
date: 2008-02-29
forum: Networking &amp; Wireless
---

### Post by Lichig0 on 2008-02-29
OK so far so good, I have VMware Installed and I i have Windows XP emulated in it. But now my problem how do I get that online. Im connected via wireless so how would I change the .vmx to have it recognize my wireless card?

edit: this is what I have for the .vmx file....
#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "3"
ide0:0.present = "TRUE"
ide0:0.filename = "WindowsXPPro.vmdk"
memsize = "228"
MemAllowAutoScaleDown = "FALSE"
ide1:0.present = "TRUE"
ide1:0.fileName = "CDone.iso"
ide1:0.deviceType = "cdrom-image"
ide1:0.autodetect = "TRUE"
floppy0.fileType = "file"
floppy0.fileName = "cdboot1.img"
floppy0.startConnected = "True"
ethernet0.present = "TRUE"
usb.present = "TRUE"
sound.present = "TRUE"
sound.virtualDev = "es1371"
displayName = "Windows XP Pro"
guestOS = "winxppro"
nvram = "WindowsXPPro.nvram"
MemTrimRate = "-1"
ide0:0.redo = ""
ethernet0.addressType = "generated"
uuid.location = "56 4d 65 6f 71 3d a4 72-95 51 f1 4b ca d3 06 a1"
uuid.bios = "56 4d 65 6f 71 3d a4 72-95 51 f1 4b ca d3 06 a1"
ethernet0.generatedAddress = "00:0c:29:d3:06:a1"
ethernet0.generatedAddressOffset = "0"
tools.syncTime = "TRUE"
ide1:0.startConnected = "TRUE"
uuid.action = "create"
checkpoint.vmState = "WindowsXPPro.vmss"
tools.remindInstall = "TRUE"

floppy0.clientDevice = "FALSE"
extendedConfigFile = "WindowsXPPro.vmxf"
virtualHW.productCompatibility = "hosted"
tools.upgrade.policy = "manual"

fileSearchPath = "/home/mark;."

---

### Post by superprash2003 on 2008-03-01
are you using vmware player??then in the OS properites in vmware.. just select the network card.. and choose bridge mode..

---

### Post by Lichig0 on 2008-03-01
> **superprash2003 said:**
> are you using vmware player??then in the OS properites in vmware.. just select the network card.. and choose bridge mode..
Do i have to change my settings in linux? I have it set to that and windows is saying it has limited or no connection

edit:
It (windows) said that the "network" didn't assign an address to the computer(windows)

---

### Post by Lichig0 on 2008-03-01
oh i forgot to mention that it says the connection speed is 10.0 MBps when im usually going 54MBps in linux I don't get whats going on so I need help with pretty much everything....

---

### Post by superprash2003 on 2008-03-01
then you may have to manually type in the ip in windows.. in ubuntu have you set the DHCP optoin or are you manually typing in the ip?? if your not sure.. just to the ubuntu terminal , type ifconfig and post the results here

---

### Post by Lichig0 on 2008-03-01
> **superprash2003 said:**
> then you may have to manually type in the ip in windows.. in ubuntu have you set the DHCP optoin or are you manually typing in the ip?? if your not sure.. just to the ubuntu terminal , type ifconfig and post the results here

Im connected via wireless so I dont do much with my Ethernet port, but i believe that its set to DHCP. But just in case

eth0      Link encap:Ethernet  HWaddr 00:1D:7D:98:3E:C8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0xe000 

eth0:avah Link encap:Ethernet  HWaddr 00:1D:7D:98:3E:C8  
          inet addr:169.254.7.192  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16157 (15.7 KB)  TX bytes:16157 (15.7 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.115.1  Bcast:192.168.115.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:123 errors:0 dropped:0 overruns:0 frame:0
          TX packets:170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.37.1  Bcast:172.16.37.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:87 errors:0 dropped:0 overruns:0 frame:0
          TX packets:165 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:14:6C:83:F2:1F  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:6cff:fe83:f21f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49769 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43214 errors:0 dropped:4 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45992857 (43.8 MB)  TX bytes:480

---

### Post by superprash2003 on 2008-03-01
make sure you have selected wlan0 as the network device in the vmware's OS Properties.. .then once you switched on the OS.. make sure you go to the network connections and connect again...i think you will have to type in the WEP or connect to the wireless network again.. just try that!!

---

### Post by Lichig0 on 2008-03-01
Is it at least possible for me to share files between VMware(windows) and my computer(ubuntu)

---

### Post by Lichig0 on 2008-03-02
> **superprash2003 said:**
> make sure you have selected wlan0 as the network device in the vmware's OS Properties.. .then once you switched on the OS.. make sure you go to the network connections and connect again...i think you will have to type in the WEP or connect to the wireless network again.. just try that!!
I can't find the OS propertiesto swich it to wlan0 and if your talking about the Devices drop down only ethernet is there.

---

### Post by scxtt on 2008-03-02
i'd recommend bridging your wireless device for use w/ your VMs ... so in effect /dev/vmnet0 = wlan0, then set the VM's to use that ... you should have files like /proc/vmnet/bridge* if bridged was setup during config, if you don't you can rerun the config script to bridge devices ...

i suppose there is an off chance that you **can't** bridge a wireless device, but if the device is present and *up*, i don't see why you couldn't ...

---

### Post by Lichig0 on 2008-03-02
> **scxtt said:**
> i'd recommend bridging your wireless device for use w/ your VMs ... so in effect /dev/vmnet0 = wlan0, then set the VM's to use that ... you should have files like /proc/vmnet/bridge* if bridged was setup during config, if you don't you can rerun the config script to bridge devices ...

i suppose there is an off chance that you **can't** bridge a wireless device, but if the device is present and *up*, i don't see why you couldn't ...
I don't know how to do that, and to clear up any confusion I didnt write the .vmx file

---

### Post by superprash2003 on 2008-03-03
ok.. since you can see ethernet in your vmware OS list.. add that and set it to bridge mode.. go to the OS in vmware and set an ip for it.. say 1.1.1.1 and in ubuntu go to the same ethernet card and manually type the ip as 1.1.1.2  .. make sure they both are in the same subnet i.e. 255.255.255.0 ...and if you have enabled sharing in your vmware OS or in your ubuntu (using samba)..you should be able to access each other's files!!

---

### Post by Lichig0 on 2008-03-03
OK so then what do i put for default gateway, prefered DNS surver and alternate server(the IP and supnet i.e didnt work alone) and now the OS sais that the connection is fiewalled.

---

### Post by Lichig0 on 2008-03-04
hello?

---

### Post by scxtt on 2008-03-04
when you use bridged, you'll base your network settings off of your router, so if your wireless has output like this:

IP: 192.168.1.100
broadcast: 192.168.1.255
netmask: 255.255.255.0

you can set the bridged VM device very similarly:

IP: 192.168.1.101
broadcast: 192.168.1.255
netmask: 255.255.255.0

as far as your DNS goes, use whatever is listed in /etc/resolv.conf on ubuntu

---

### Post by Lichig0 on 2008-03-05
ummm this is what i got to fill in [http://s159.photobucket.com/albums/t138/sords4/?action=view&current=Screenshot-4.png](http://s159.photobucket.com/albums/t138/sords4/?action=view&current=Screenshot-4.png)
and I know what to put for IP and the mask but i didnt know what to put for gateway and alternate DNS,,,,,

---

### Post by Lichig0 on 2008-03-05
OK for some more detail, i set it to do everything automatically and it got everything(IP, mask) but, Default Gateway, DNS Server, and WINS Server. Those fields were empty

---

### Post by Lichig0 on 2008-03-06
Can some one please help, there is an online game i want to play and I can't rely on my Windows partition....

---

### Post by dmizer on 2008-03-06
try this.

add the following two lines:
```
Ethernet0.connectionType = "custom"
Ethernet0.vnet = "/dev/vmnet1"
```

to your vmx file as follows:
```
#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "3"
ide0:0.present = "TRUE"
ide0:0.filename = "WindowsXPPro.vmdk"
memsize = "228"
MemAllowAutoScaleDown = "FALSE"
ide1:0.present = "TRUE"
ide1:0.fileName = "CDone.iso"
ide1:0.deviceType = "cdrom-image"
ide1:0.autodetect = "TRUE"
floppy0.fileType = "file"
floppy0.fileName = "cdboot1.img"
floppy0.startConnected = "True"
ethernet0.present = "TRUE"
usb.present = "TRUE"
sound.present = "TRUE"
sound.virtualDev = "es1371"
displayName = "Windows XP Pro"
guestOS = "winxppro"
nvram = "WindowsXPPro.nvram"
MemTrimRate = "-1"
ide0:0.redo = ""
[COLOR="Red"]Ethernet0.connectionType = "custom"
Ethernet0.vnet = "/dev/vmnet1"[/COLOR]
ethernet0.addressType = "generated"
uuid.location = "56 4d 65 6f 71 3d a4 72-95 51 f1 4b ca d3 06 a1"
uuid.bios = "56 4d 65 6f 71 3d a4 72-95 51 f1 4b ca d3 06 a1"
ethernet0.generatedAddress = "00:0c:29:d3:06:a1"
ethernet0.generatedAddressOffset = "0"
tools.syncTime = "TRUE"
ide1:0.startConnected = "TRUE"
uuid.action = "create"
checkpoint.vmState = "WindowsXPPro.vmss"
tools.remindInstall = "TRUE"

floppy0.clientDevice = "FALSE"
extendedConfigFile = "WindowsXPPro.vmxf"
virtualHW.productCompatibility = "hosted"
tools.upgrade.policy = "manual"

fileSearchPath = "/home/mark;."
```
then configure your windows machine for dhcp ("obtain ip address automatically", and "obtain DNS server address automatically").

just a side note, even if your ubuntu machine is connected wirelessly, you should configure your windows virtual machine as though it was connected via ethernet.

---

### Post by Lichig0 on 2008-03-12
I've found where the problem is comeing from....but i still dont know how to fix it :(

The problem is in the kernel im using and it doesnt work well with VMware so it cant bridge wireless....there are patches out there, but i dont know how to make/use them.....

---

### Post by dmizer on 2008-03-13
that seems strange.

have you tried the suggestion i gave above?

what is the output of:
```
uname -r
```

---

### Post by Lichig0 on 2008-03-14
2.6.22-14-generic

---

### Post by scxtt on 2008-03-15
i'm using 2.6.22-14-generic w/ VMware server 1.0.4
```
scxtt @ vmware [ /home/scxtt ]
:> uname -r; vmware -v
2.6.22-14-generic
VMware Server 1.0.4 build-56528
```

---

### Post by Lichig0 on 2008-03-26
I still dont know how to fix this problem...

---

### Post by scxtt on 2008-03-26
what's the output of:

ls -l /proc/vmnet

---

