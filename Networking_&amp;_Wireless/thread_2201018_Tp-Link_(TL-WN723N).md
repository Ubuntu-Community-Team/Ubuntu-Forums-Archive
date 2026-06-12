---
title: "Tp-Link (TL-WN723N)"
date: 2014-01-22
forum: Networking &amp; Wireless
---

### Post by big_j2 on 2014-01-22
HELLO,
I'M kinda new to linux UBUNTU 12.04.3  
And i am trying  to HOOK UP my USB Wireless Network Thumbdrive  to make my OLD desktop in to make a media center pc that can surf the web and do internet radio and play music and as well some movies its a OLD system it has 

3 gigs of ram i think :P if not its 3 sticks of 512 it been soo long mind You BUT the system RUNS pretty FAST for her AGE :P 
amd cpu
BFG nvidia Grafics Card 
dvd burner and curently runing windows pro 32 bit)
 the resion for the change to UBUNTU is WINDOWS XP is ALL DONE & looking to extend the life of my OLD SYSTEM !!
and of course 1 floppy drive LOL 
& 2, 500gig HDD Drives

its a home built system shes been good to me !!!
heres what im trying to hook up heres the link 

[http://www.tp-link.us/products/details/?categoryid=243&model=TL-WN723N](http://www.tp-link.us/products/details/?categoryid=243&model=TL-WN723N)

it works great with xp and other windows OS's and i seen that someone even got it to work on LINUX mint heres the link 

[http://community.linuxmint.com/hardware/view/5413](http://community.linuxmint.com/hardware/view/5413)

MY question is will it work in UBUNTU 12.04.3 32Bit the same way it would in LINUX MINT ?? if soo PLEASE tell me the steps i need to do to get it to WORK !!! 

i  also need to Know if this would work as well  WICD for my Problem  link below ??

[https://launchpad.net/wicd](https://launchpad.net/wicd)

THANK YOU for taking the TIME in READING this and ANY HELP PROVIDED !!!

---

### Post by chili555 on 2014-01-22
When I go to the link you gave, I see there are versions 1, 2 and 3. Which do you have? Have you installed Ubuntu or Mint? Can you identify the device from the terminal?```
lsusb
```We need more information.

[http://www.tp-link.us/Article/?id=46](http://www.tp-link.us/Article/?id=46)


----
Possible reference if v.3: [http://askubuntu.com/questions/370833/tl-wn723n-v3-driver-install](http://askubuntu.com/questions/370833/tl-wn723n-v3-driver-install)

---

### Post by big_j2 on 2014-01-23
UBUNTU 12.04.3 

& Tp-link (TL-WN723N) V.2

& have not INSTALLED it or TRYED IT yet Just HOPING that there is a way that it will WORK ???
SO i CAN INSTALL IT or USE IT !!!

---

### Post by chili555 on 2014-01-23
> **big_j2 said:**
> UBUNTU 12.04.3 

& Tp-link (TL-WN723N) V.2

& have not INSTALLED it or TRYED IT yet Just HOPING that there is a way that it will WORK ???
SO i CAN INSTALL IT or USE IT !!!So you haven't actually purchased it yet? I believe V2 uses the driver rtl8192cu. I believe it is covered in 12.04.3. If not, it can easily be compiled.

Caps lock stuck??

---

### Post by big_j2 on 2014-01-25
YES I HAVE IT HERE in FRONT OF ME when i sayd i have not tryed it yet means i have not plugged it in yet LOL to the system mind u its USB THE wireless thumb drive for the internet I HAVE EVERYTHING  JUST NEED TO GET GET TO RUN I HAVE SKYPE IDK if u can understand english THO I AM NOT SHURE &
IS THERE A DIFFERENCE between LINUX MINT and UBUNTU other then the cosmedic look of them both & I know ppl have there favorites BUT I like the feel of ubuntu & just need to know is there  really a difference betwen the 2 OS's like is the SUDA code the same for both os's again i have skype & i COULD USE THE HELP ON SOME STUFF with ubuntu SOO PM ME !!! IF INTERESSTED DO SOO AND ILL HOOK U UP !!!! & WELL TALK BIG J OUT

---

### Post by chili555 on 2014-01-25
Although my wife sometimes disagrees, I understand English reasonable well. What I do *not *do is answer by Skype, PM, email, etc. I think there are many new users out there that have the same wireless device and they will be interested in how to get it going. We will help many, thousands, perhaps, if we have our discussions right here on the forum so they can read and follow along.

So, once again, insert the device, open a terminal Ctrl+Alt+t and run and post:```
lsusb
```

---

### Post by lindevox on 2014-04-30
Hi,
Please allowed me to join this thread cause got same problem here.
 I also use TP-LINK TL-WN723N.V1 and previously it orks well with ubuntu server 12.10 and 13.10, but when I decided to upgrade my server to Ubuntu server 14.04 and install unity desktop on it, then wlan0 didn't up on boot. 

When I  :

```

$ sudo lsusb : Bus 001 Device 003: ID 0bda:8171 Realtek Semiconductor Corp. _**RTL8188SU**_ 802.11n WLAN Adapter

```

It was _**RTL8188SU**_ but when I  : 

```
lshw -C network : 

*-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:1.3
       logical name: wlan0
       serial: b0:48:7a:8b:a5:4e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes _**driver=r8712u**_ multicast=yes wireless=IEEE 802.11bgn


```

Which one is correct?

---

### Post by chili555 on 2014-04-30
> Which one is correct?Both. The first is Realtek's description of the chipset. r8712u is the name of the Linux driver. In some cases, they are the same. In most cases, they are not. For example, I have:> *-network
       description: Wireless interface
       product: [COLOR="#FF0000"]Centrino Advanced-N 6200[/COLOR]
       vendor: [COLOR="#FF0000"]Intel Corporation[/COLOR]
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 35
       serial: xx:94:6b:99:55:xx
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes [COLOR="#FF0000"]driver=iwlwifi[/COLOR] driverversion=3.13.0-24-generic firmware=9.221.4.1The name of the chipset and the name of the driver are often different.

> then wlan0 didn't up on boot.Can you get it going through Network Manager or how?

---

### Post by lindevox on 2014-05-01
I removed network manager :

```
 $ sudo apt-get remove --purge network-manager
```

can bring it up and get it connected to tplink wifi router tl-WR1043ND by typing :

```
$ sudo iwconfig wlan0 essid XXXX 
```

but after reboot, It doesn't bring up wlan0 neither get connected to wifi router.

another problem is when I managed to get it connected to wifi router, other pc cannot get connected to server 
isc-dhcp-server was installed and running tho and was assigned to wlan0 interface network : 192.168.3.0/24

here is my /etc/network/interfaces :
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# The secondary network interface
# auto wlan0
iface wlan0 inet static
wireless-essid XXXXXX
address 192.168.3.1
netmask 255.255.255.0

---

### Post by chili555 on 2014-05-01
> another problem is when I managed to get it connected to wifi router, other pc cannot get connected to server > # The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# The secondary network interface
#auto wlan0
iface wlan0 inet static
wireless-essid XXXXXX
address 192.168.3.1
netmask 255.255.255.0Yikes!! It appears you have given the server the router's address! Second, you are asking  the ethernet to start automatically, but *NOT* the wireless. As well, you have specified no encryption key. Isn't your network protected with WPA2-AES? It certainly should be.

I suggest:```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
iface eth0 inet dhcp

# The secondary network interface
auto wlan0
iface wlan0 inet static
address 192.168.3.100  [COLOR="#FF0000"]<--or any address outside the DHCP range in the router[/COLOR]
netmask 255.255.255.0
gateway 192.168.3.1
wpa-ssid XXXXXX
wpa-psk ZZZZZ
dns-nameservers 8.8.8.8 192.168.3.1
```Reboot and give us your report.

---

### Post by lindevox on 2014-05-01
> Yikes!! It appears you have given the server the router's address!

" Be it far for me from the evil" :wink: 

I purposely change server IP to 192.168.3.1/24 and router's to 192.168.3.2/24

>  Second, you are asking  the ethernet to start automatically, but *NOT* the wireless.

previous /etc/network/interface configuration is auto wlan0 but also didn't work

> As well, you have specified no encryption key. Isn't your network protected with WPA2-AES? It certainly should be.

Yes it was protected with WPA2-AES, but IMHO, initially I would prefer to setup the connection without any encryption overhead.
After get connected then would implement the wireless encryption. (well, I could be wrong) :)

>  address 192.168.3.100  [COLOR=#FF0000]<--or any address outside the DHCP range in the router [/COLOR]

FYI: wireless router's DHCP was disabled because any clients will get its lease from ISC-DHCP-SERVER runs on my Ubuntu 14.04 server
and the lease IP range configured is 192.168.3.100 - 192.168.3.200

would you please kindly show me how to install tp-link TL-WN723N.V1 usb wlan driver?

---

### Post by chili555 on 2014-05-01
Oh! Pardon me. It wasn't clear to my 150-year-old-eyes that the server in question *IS* the DHCP server. Please disregard my suggestions entirely. It also wasn't clear that the question is actually about the driver and not the network configuration. Again, pardon me. 

If you are trying to get the wireless device to be in managed mode and connect to the router and simultaneously to be in master mode to allow connections from other computers, then I don't believe such a thing is at all possible, at least in Linux. 

Everything I see above suggests that you have a working driver.

---

### Post by lindevox on 2014-05-02
> If you are trying to get the wireless device to be in managed mode and  connect to the router and simultaneously to be in master mode to allow  connections from other computers, then I don't believe such a thing is  at all possible, at least in Linux. 

Ah...Yes! Thanks! 

Pardon my 150.01-year-old-Alzheimer-Syndromed-memory. I agreed it won't work that way.

This was my pevious working network topology:

[internet]--<[COLOR=#0000ff]wired[/COLOR]>---[ADSL MODEM]--<[COLOR=#0000ff]wired[/COLOR]>---[Wifi Router] --<[COLOR=#ff0000]wireless link[/COLOR]>----[usb wlan plugged to serverUSB]-----[Ubunt Server]----<[COLOR=#0000ff]wired lan/eth0[/COLOR]>----[Wifi Router] --<[COLOR=#ff0000]wireless Link[/COLOR]>---[PCs]

reason : Because my CPU has only one LAN port, so lan/eth0 goes to TPLINK TL-WR1043ND wifi router (WR#2) to server internal network and the USB wifi (TPLINK TL-WN723N) connects wirelessly to another  TPLINK TL-WR1043ND wifi router (WR#1) where its WAN port connected to the ADSL MODEM.

ADSL modem's build in DHCP server will serve any connections from WR #1. This would allow USB wifi (TPLINK TL-WN723N) plugged on the server
 to gets its IP, bla..bla..bla....
ofcourse client pc will get its IP from server becasue WR#2 connection is wired (eth0)

such mistake I did was changing the network topology to:

[internet]--<[COLOR=#0000ff]wired[/COLOR]>---[ADSL MODEM]--<[COLOR=#0000ff]wired[/COLOR] to LAN (eth0) >----[Ubunt Server]------[USB wifi (TPLINK TL-WN723N)] --<[COLOR=#ff0000]wireless Link[/COLOR]>---[TPLINK TL-WR1043ND wifi router]---<[COLOR=#ff0000]wireless link[/COLOR]>--[PCs]

'Tho I can't remember well, I believe i've made the same mistake before :) 

Would you enlightenned me further if let say with the later topology above, and I enable the Wireless router DHCP, is it possible for clients PCS to get connected to the server that serves ROUTING from internal to internet, SAMBA, FTP, SQUID,DNS SERVER, etc.
 
What configuration do I need either on the WR & server?

---

