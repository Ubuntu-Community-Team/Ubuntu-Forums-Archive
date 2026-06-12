---
title: "Static ip with Feisty"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by pressman57 on 2007-04-14
I've been reading that the new network manager does not support static ip addresses, and really cannot be disabled. Is this indeed the case, and if so is there a way to circumvent this problem? My wife's old scsi-based Mac shares a cable modem through a Linksys router and has to have a static ip, so DHCP is not an option.

---

### Post by wieman01 on 2007-04-14
> **pressman57 said:**
> I've been reading that the new network manager does not support static ip addresses, and really cannot be disabled. Is this indeed the case, and if so is there a way to circumvent this problem? My wife's old scsi-based Mac shares a cable modem through a Linksys router and has to have a static ip, so DHCP is not an option.
Ubuntu does support Static IP as long as you use Ethernet or unsecured wireless. Feisty will support Static IP as well. However, if you are using Dapper or Edgy and need to secure your wireless network while using Static IP, there is a HOWTO in my signature. Feel free to use it and post there for help.

---

### Post by TheWizzard on 2007-04-14
> **wieman01 said:**
> Ubuntu does support Static IP as long as you use Ethernet or unsecured wireless. Feisty will support Static IP as well. However, if you are using Dapper or Edgy and need to secure your wireless network while using Static IP, there is a HOWTO in my signature. Feel free to use it and post there for help.

dapper works perfectly with WEP and static IP.

---

### Post by wieman01 on 2007-04-15
> **TheWizzard said:**
> dapper works perfectly with WEP and static IP.
Let me put it this way... WEP does work with Static IP, WPA doesn't because Network-Manager does not support it.

---

### Post by TheWizzard on 2007-04-15
> **wieman01 said:**
> Let me put it this way... WEP does work with Static IP, WPA doesn't because Network-Manager does not support it.

ok, clear.

---

### Post by navsx on 2007-04-15
Hmmm.... don't know whats up, but with recent updates to feisty (since around a week), wireless static ip won't work with network manager. There seem to be some conflict between /etc/network/interfaces and the network manager.

If I disable all interfaces except lo in /etc/network/interfaces, network manager sees my wireless card (eth1 - ipw2200), lists the networks. I can setup the network to connect to, but it insists on dhcp. So, if I select 'Manual Configuration' and enter the ssid and static ip, network manager stops trying to connect, says Manual Configuration and doesn't show the list of wireless networks.

If I disable the newly added lines in /etc/network/interfaces, I am back to square one with a list of networks, but having to use dhcp.

I am using WPA2-PSK and network manager worked extremely well before this. It had no issues picking up the static IP from /etc/network/interfaces. 

Am I missing something?

---

### Post by Shaka84 on 2007-04-20
Hi!
At the moment, network manager in Feisty has a problem to save the right configuration and don't save neither* dns server* nor* ip static* parameters.
Try this:

**- FOR DNS SERVER:**

 open resolv.conf:
 ```

sudo gedit /etc/resolv.conf

```

add opendns nameserver:
```

nameserver 208.67.222.222
# nameserver 192.168.1.1

```

open dhclient.conf:
```

sudo gedit /etc/dhcp3/dhclient.conf

```

search this line:
**#prepend domain-name-servers 127.0.0.1;**
and remove the comment symbol (#) and change the line in:
```

[COLOR="Red"]prepend domain-name-servers 208.67.222.222;[/COLOR]

```

now, search and **delete** the [COLOR="Red"]domain-name-servers[/COLOR], one line below.
Now, you must have this:
```

prepend domain-name-servers 208.67.222.222;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, host-name,
	netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;

```

Let's restart the network:
```

sudo/etc/init.d/networking restart

```


**- FOR THE STATIC IP ADDRESS:**

open /etc/networking/interfaces:
```

sudo gedit /etc/networking/interfaces

```

you might have this:
(*xxx.xxx.xxx.xxx* are your settings!)
```

auto wlan0 (for wireless )/ eth0 (for ethernet)
iface wlan0/eth0 inet **[COLOR="Red"]dhcp[/COLOR]**
address *xxx.xxx.xxx.xxx*
netmask *xxx.xxx.xxx.xxx*
gateway *xxx.xxx.xxx.xxx*

```

change**[COLOR="Red"] dhcp[/COLOR]** to **[COLOR="Red"]static[/COLOR]**:
```

auto wlan0 (for wireless )/ eth0 (for ethernet)
iface wlan0/eth0 inet **[COLOR="Red"]static[/COLOR]**
address *xxx.xxx.xxx.xxx*
netmask *xxx.xxx.xxx.xxx*
gateway *xxx.xxx.xxx.xxx*

```

now restart the network and surf!!
```

sudo/etc/init.d/networking restart

```

---

### Post by Erlander on 2007-04-20
I've got it working on 2 wired pc's by a different method.

I turned DHCP on in my modem and in Administration/network and it recognised the pc.  Then returned to static ip in Admin/Network and finally turned DHCP off in the modem.

Rob

---

### Post by templer666 on 2007-04-22
Hi,
well, I don't get static IP working. After having edited the **/etc/network/interfaces** file it looks like this:

[FONT="Courier New"]root@arthur:/etc/network# cat interfaces
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet static
address 192.168.2.3
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255
gateway 192.168.2.1[/FONT]

When I restart the network interface with **/etc/init.d/networking restart** and check my iface with **/sbin/ifconfig** it prints this:

[FONT="Courier New"]root@arthur:/etc/network# ifconfig
eth0      Protokoll:Ethernet  Hardware Adresse 00:D0:59:9C:32:23
          inet Adresse:192.168.2.114  Bcast:192.168.2.255  Maske:255.255.255.0
          inet6 Adresse: fe80::2d0:59ff:fe9c:3223/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:169003 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81617 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:236136318 (225.1 MiB)  TX bytes:8105294 (7.7 MiB)
...[/FONT]

I did tail the error messages to **/var/log/messages**:

[FONT="Courier New"]...
Apr 22 20:31:10 arthur kernel: [22354.376000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 22 20:31:10 arthur kernel: [22354.380000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
Apr 22 20:31:10 arthur dhcdbd: dhco_input_option: Value -1 cannot be converted to type L
Apr 22 20:31:10 arthur dhcdbd: dhco_parse_option_settings: bad option setting: old_dhcp_lease_time = -1
Apr 22 20:31:11 arthur kernel: [22355.276000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Apr 22 20:31:21 arthur dhcdbd: dhco_input_option: Value -1 cannot be converted to type L
Apr 22 20:31:21 arthur dhcdbd: dhco_parse_option_settings: bad option setting: new_dhcp_lease_time = -1
Apr 22 20:31:21 arthur dhcdbd: dhco_input_option: Value -1 cannot be converted to type L
Apr 22 20:31:21 arthur dhcdbd: dhco_parse_option_settings: bad option setting: old_dhcp_lease_time = -1
Apr 22 20:31:21 arthur dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Apr 22 20:31:21 arthur dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Apr 22 20:31:21 arthur dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
...[/FONT]

x.x.x.114 is a DHCP address assign by my router. I just don't get it, why feisty can't set the static IP! Any suggestions? How to work around it? I need the static IP for the ssh server.
BTW, just to make it clear, I did try it graphically before, but that didn't work so I went back to good old terminal as that always worked well with dapper end edgy up to now,

Thanks for your help!
Rob

---

### Post by templer666 on 2007-04-22
hi again,
how strange is that?! 
I just set the 192.168.2.3 IP using **ifconfig eth0 192.168.2.3**. That worked, _BUT_ no DNS resolving was done although my router at 192.168.2.1 was the only DNS listed in /etc/resolv.conf.
So I tried **/etc/init.d/networking restart** again and it works now even with DNS!

Still, I think this should work right from System Settings->Networking in the first place without all the trouble on the terminal.

rob

---

### Post by Gujs on 2007-04-23
For me it is not possible to setup static  ip with network manager. Every time I set ip to static i get on network manager just Manual configuration option, and if i take it back to dhcp i have to delete this lines
```
address 192.168.0.120
netmask 255.255.255.0
gateway 192.168.0.1

```
 to get network manager detect wired network again. And then I also get vpn connections back in network manager menu when clicking on it.

---

### Post by wieman01 on 2007-04-23
> **Gujs said:**
> For me it is not possible to setup static  ip with network manager. Every time I set ip to static i get on network manager just Manual configuration option, and if i take it back to dhcp i have to delete this lines
```
address 192.168.0.120
netmask 255.255.255.0
gateway 192.168.0.1

```
 to get network manager detect wired network again. And then I also get vpn connections back in network manager menu when clicking on it.
Feisty supports Static IP, believe me. I tried the Live CD over the weekend and I could hook my computer up to my local wireless network.

---

### Post by dannyboy79 on 2007-04-23
> **Gujs said:**
> For me it is not possible to setup static  ip with network manager. Every time I set ip to static i get on network manager just Manual configuration option, and if i take it back to dhcp i have to delete this lines
```
address 192.168.0.120
netmask 255.255.255.0
gateway 192.168.0.1

```
 to get network manager detect wired network again. And then I also get vpn connections back in network manager menu when clicking on it.

this is because your dhclient.conf is asking your dhcp server what the dns servers are and your router/dhcp server is claiming to be one when it really isn't. it only forwards dns requests out to your isp. 

shaka84 wrote exactly how to fix this but apparently you didn't read his post. it's number 7.

---

### Post by Gujs on 2007-04-23
> **dannyboy79 said:**
> this is because your dhclient.conf is asking your dhcp server what the dns servers are and your router/dhcp server is claiming to be one when it really isn't. it only forwards dns requests out to your isp. 

shaka84 wrote exactly how to fix this but apparently you didn't read his post. it's number 7.

I tried his fix, but it still doesn't work for me. If I have static ip I can only se Manual configuration and vpn connection disappear.

---

### Post by Gujs on 2007-04-23
> **wieman01 said:**
> Feisty supports Static IP, believe me. I tried the Live CD over the weekend and I could hook my computer up to my local wireless network.

I know that it supports Static IP, but then network manager has some problems with it. I have set static ip but then i have in network manager when i left click on it, just Manual configuration option. VPN and Wired network disappeared. That is what is anoying to me.

Static ip configuration works.

---

### Post by wieman01 on 2007-04-23
> **Gujs said:**
> I know that it supports Static IP, but then network manager has some problems with it. I have set static ip but then i have in network manager when i left click on it, just Manual configuration option. VPN and Wired network disappeared. That is what is anoying to me.

Static ip configuration works.
Alright... I have to admit I am having some problems as well. Kind of weird behavior concerning Static IP. Hope this will be fixed in the next version.

---

### Post by navsx on 2007-04-25
> **Gujs said:**
> I know that it supports Static IP, but then network manager has some problems with it. I have set static ip but then i have in network manager when i left click on it, just Manual configuration option. VPN and Wired network disappeared. That is what is anoying to me.

Static ip configuration works.
Exactly the same scenario for me like I mentioned earlier.

1. No issues at all with wired network since I only use it with dhcp.
2. With wireless, no issues when using wpa_supplicant, with dhcp and static.
3. With network-manager, no issues with dhcp.
4. With network-manager, the moment I add static ip information in /etc/network/interfaces, network-manager refuses to deal with wireless at all - I just see 'Manual configuration' in its menu and no wireless networks are listed.

I have hacked up a script to use wpa_supplicant for wireless, for now. Looking forward to nm 0.7, which is unfortunately a long way off...

---

### Post by dannyboy79 on 2007-04-25
how about downgrading nm?

---

### Post by wieman01 on 2007-04-25
I cannot believe it... they have messed it up again. I tried several times, disabled and enabled my wireless adapter,  etc. but all in vain. From Kubuntu Live CD that is. It is such a pity, Ubuntu is the distribution of my choice, however, they really have an issue with wireless. Sorry for my ranting, but I was hoping Feisty would do away with this once and forever. Wishful thinking I would say.

DHCP works fine, static IP simply wouldn't...

---

### Post by stchman on 2007-04-25
> **pressman57 said:**
> I've been reading that the new network manager does not support static ip addresses, and really cannot be disabled. Is this indeed the case, and if so is there a way to circumvent this problem? My wife's old scsi-based Mac shares a cable modem through a Linksys router and has to have a static ip, so DHCP is not an option.

I am not aware of any PCs that HAVE to have a static IP address.   The router simply assigns an IP to each ethernet card.    I use static IPs for machine that I do bit torrent downloads as I had to open up ports on the router for a specific IP.

Is your wife's Mac running Ubuntu?  If yes then go to Administration--->Network

Place a check mark next to the ethernet card to tell Ubuntu that is the interface you are going to use.  Otherwise Network-Manager determines which interface you will use.  Select the ethernet card and drop down menu to assign a static IP.  You will put your static numbers in the spots provided.

Hope this helps.

---

### Post by dannyboy79 on 2007-04-26
> **stchman said:**
> I am not aware of any PCs that HAVE to have a static IP address.   The router simply assigns an IP to each ethernet card.    I use static IPs for machine that I do bit torrent downloads as I had to open up ports on the router for a specific IP.

Is your wife's Mac running Ubuntu?  If yes then go to Administration--->Network

Place a check mark next to the ethernet card to tell Ubuntu that is the interface you are going to use.  Otherwise Network-Manager determines which interface you will use.  Select the ethernet card and drop down menu to assign a static IP.  You will put your static numbers in the spots provided.

Hope this helps.

If network-manager is causing issues when assigning static ip's (vpn and whatever else) there is 2 possible solutions

1.) Downgrade network-manager to whatever was used in Edgy (which apparently working for people?)

2.) Setup your router for "static dhcp". This is an option in many routers but not all so you can always look for it. What this does is basically "reserve" an IP adress to a certain MAC address. I have a pretty old Netgear Router and mine has this option. It's under the section, "Attached Devices". I click on that section and it shows me all the computers that I currently connected to the router. If hte machines hostname isn't populating witin the router I don't know how to solve that but you can obviously tell which MAC address is which since you know what ip each machine has by doing a ifconfig -a within linux and a ipconfig /all with msdos if you're running windows. So when you see the list of attazched devices there is an option called "ip reservation". I simply click on the little circle and it fills in which means that no matter what, the MAC addres will always receive that same IP address from the dhcp server everytime. That way you don't have to bother setting static ip within your OS. I think this is a great design within home routers.

Hope 1 of the 2 suggestions will work for everyone that is having issues.

---

### Post by stchman on 2007-04-26
> **dannyboy79 said:**
> If network-manager is causing issues when assigning static ip's (vpn and whatever else) there is 2 possible solutions

1.) Downgrade network-manager to whatever was used in Edgy (which apparently working for people?)

2.) Setup your router for "static dhcp". This is an option in many routers but not all so you can always look for it. What this does is basically "reserve" an IP adress to a certain MAC address. I have a pretty old Netgear Router and mine has this option. It's under the section, "Attached Devices". I click on that section and it shows me all the computers that I currently connected to the router. If hte machines hostname isn't populating witin the router I don't know how to solve that but you can obviously tell which MAC address is which since you know what ip each machine has by doing a ifconfig -a within linux and a ipconfig /all with msdos if you're running windows. So when you see the list of attazched devices there is an option called "ip reservation". I simply click on the little circle and it fills in which means that no matter what, the MAC addres will always receive that same IP address from the dhcp server everytime. That way you don't have to bother setting static ip within your OS. I think this is a great design within home routers.

Hope 1 of the 2 suggestions will work for everyone that is having issues.

I feel that network manager is really for wireless stuff.  Yes you can use it for wired connections but why?  

My old D-Link router had static IP for MAC address but my newer Linksys does not so I have to assign a static IP for a PC through the Admin--->Network.

---

### Post by dannyboy79 on 2007-04-26
> **stchman said:**
> I feel that network manager is really for wireless stuff.  Yes you can use it for wired connections but why?  

My old D-Link router had static IP for MAC address but my newer Linksys does not so I have to assign a static IP for a PC through the Admin--->Network.

so are you aware of how to configure thru system, admin, networking to use a prozy server or how to setup a vpn? if not, than that's what nm was suppose to be for. that's what these people are having problems with. (i think anyway?)

---

### Post by Gujs on 2007-04-26
> **stchman said:**
> I feel that network manager is really for wireless stuff.  Yes you can use it for wired connections but why?  

My old D-Link router had static IP for MAC address but my newer Linksys does not so I have to assign a static IP for a PC through the Admin--->Network.

I have the same feeling, that network manager is developed primary for wireless. I want to use it because it has a vpn connection plugin which is really usable, bacause I don't want to use terminal every time I use vpn connection. So I added static ip address in my router. Now I can live with it!

---

### Post by dannyboy79 on 2007-04-26
you should check out wifi-radar, that might has vpn capablitties. when I used to manage all my wireless connections I loved it but I don't recall whether you could setup a vpn or not.

---

### Post by suedama1756 on 2007-04-29
I'm very new to all this, installed ubuntu yesterday and hit the same problem.

The issue with static ip is that it seems to really mess up all other network manager features, i.e. wireless and vpn configuration are no longer available from the menu, they just disappear. And when you manually re-configure for DHCP they do not re-appear.  

It seems to be an issue with the nm-applet configuration tool not writing back to the /etc/network/insterfaces file  correctly, i have managed to get mine to reliably configured for static IP and maintaining the VPN options by configuring the /etc/network/interfaces file as follows (eth0 section is key):

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth0
iface eth0 inet static
address 192.168.2.50
netmask 255.255.255.0
gateway 192.168.2.1

New ubuntu users, especially those coming from windows see the network manager tool as a one stop place for network management, its kind of implied in the name:). The plugin architecture that allows for VPN access, particularly for me network-manager-pptp really makes life easy and has nothing to do with wireless. (although  I have an issue with vpn not working over wireless through network manager, but that's another issue). 

I don't know about anyone else but I want to use my computer to get things done, not get involved in network admin which to be honest has been easy and reliable on all other platforms for some time now. I get the feeling that very little testing is done before shipping  what is really a fundamental part of the system, I'm a developer so it wasn't too difficult to spot the bad entries being written to the file, shouldn't be too difficult for someone involved in the network-manager project to  fix for a patch.....

---

### Post by wieman01 on 2007-04-30
> **suedama1756 said:**
> I don't know about anyone else but I want to use my computer to get things done, not get involved in network admin which to be honest has been easy and reliable on all other platforms for some time now. I get the feeling that very little testing is done before shipping  what is really a fundamental part of the system, I'm a developer so it wasn't too difficult to spot the bad entries being written to the file, shouldn't be too difficult for someone involved in the network-manager project to  fix for a patch.....
I more than agree. In particular for business users reliable wireless networking is a must. This has been a major drawback in my opinion and I don't see a reason why it should be difficult to come up with a networking applet that just works. There is simply no excuse.

---

### Post by pug on 2007-05-01
For what its worth I could not even get Ubuntu to use static IP on an ethernet card...

I've used Debian for 10+ years, but this is just absurd, how the hell did Ubuntu mess this up?

I tried enabling a static IP using both network manager or by editing /etc/network/interfaces (of course followed by /etc/init.d/networking restart)

All just gave me no route to anything on the subnet, the card would get the right IP (in this case 192.168.1.2) but I could not ping other hosts on the same subnet.

I wonder what kind of tests the developers run for this to happen.

I finally gave up and configured my dhcp server to hand out the correct IP to the machine, after which everything worked, but I guess I'll never get back the hour of my life I spent on this crap.

---

### Post by bvucinic on 2007-05-16
I couldn't agree more!!
Moreover new users don't even know where to look, my system was booting fine but it could take ages for gnome to start-up ... why should a new linux user even think about networking when his GUI is not starting up.

---

