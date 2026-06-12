---
title: "Setting Up a Static IP"
date: 2008-04-09
forum: Networking &amp; Wireless
---

### Post by azurepancake on 2008-04-09
I am planning on setting up a static IP on this machine and I wanted to be sure what I am about to do is correct. If anyone can give me the thumbs up I'd be ever grateful. 

First, here are my network credentials:

IP I wish to use: 192.168.1.100
Subnet mask: 255.255.255.0
Gateway: 192.168.1.254

While searching how to configure a static IP through the shell, I learned that I need to access the /etc/network/interfaces configuration file and enter:


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.0.1


After configuration, run a good sudo service networking restart for good measure.

The thing is that my card is wireless. It is fully functional with DHCP, I would just like a static IP for my services. So should I simply replace all the "eth0's" in the file with "wlan0's"? Also I am afraid to say I've never heard of this "network" part listed as 192.168.1.0 (and I am Network+ certified) ! 

Any advice would be much appreciate and if you need anymore information please let me know, Thanks!

---

### Post by Eiríkr on 2008-04-09
Open a terminal and have a look at **man interfaces** -- that'll show you what each of these options is for.  As it appears, the "network" line is only for older kernels in the 2.0.x group.  

I have no clue about wireless, but replacing the "eth0" with "wlan0" (or whatever your interface is called) sounds correct.  I suspect there are also some lines including "essid" or about your WEP or WPA security in the interfaces file, which you should leave intact.  

My (wired) static IP setup looks like (just the relevant lines):
```
auto eth0
iface eth0 inet static
address 192.168.10.10
netmask 255.255.255.0
gateway 192.168.10.1
```
The gateway should be the address of your router.  

HTH,

Eiríkr

---

### Post by azurepancake on 2008-04-09
Okay, I spent some time trying to set this up and did all that I had the knowledge to do, but unfortunately I ended up not getting it to work.

I simply reedited the interfaces file with the follow lines: 

auto lo
iface lo inet loopback
mapping hotplug
script grep
map wlan0
auto wlan0
iface wlan0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.254

I then saved the file and attempt to restart the networking service and I get the following error:

 * Reconfiguring network interfaces...                                          /etc/network/interfaces:1: too many parameters for iface line
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:1: too many parameters for iface line
ifup: couldn't read interfaces file "/etc/network/interfaces" [fail] 

After doing this, I couldn't even see any wireless networks, let alone connect to them. The gateway address is correct, the IP unique to this network and the subnet mask is correct for the "class C" IP address. 

The error says that there are too many parameters for the iface line. I am not sure if this means I should shorten it.

Thanks again.

---

### Post by Eiríkr on 2008-04-09
I had some question marks in my head last night but didn't have the time to track them down until this morning -- I rather suspect that the "mapping" lines are not what you need; at any rate, I found the following in **man interfaces**:
> Stanzas beginning with the word "mapping" are used to determine how  a  logical  interface name  is  chosen  for  a physical interface that is to be brought up.  The first line of a mapping stanza consists of the word "mapping" followed by a pattern in shell glob  syntax. Each  mapping  stanza  must contain a script definition.  The named script is run with the physical interface name as its argument and with the contents of all following "map" lines (without the leading "map") in the stanza provided to it on its standard input. The script must print a string on  its  standard  output  before  exiting.  See  _/usr/share/doc/ifupdown/examples_ for examples of what the script must print.

Mapping a name consists of searching the remaining mapping patterns and running the script corresponding to the first match; the script outputs the name to  which  the  original  is mapped.[/code]

Following the suggestion and looking at the /usr/share/doc/ifupdown/examples directory, the only file that seemed apt for your situation was "network-interfaces.gz".  Running less on this file to show the contents confirms that your whole "mapping" stanza is incorrect, in that the "script" line requires a path to a script, and that mapping seems to go far beyond what you require anyway.  

With these points in mind, I'd suggest changing your interface line to look more like the following:
```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.254
```

Even so, your wlan0 interface definition is missing a number of required lines that define how to access your wireless router.  I mentioned these in my previous post; they should begin with "wireless-".  From **man interfaces**:
[quote]Additional options can be made  available  by  other Debian packages.  For example, the wireless-tools package makes available a number of options prefixed with "wireless-" which can be used to configure the interface using iwconfig(8).  (See wireless(7) for details.)

**man wireless** doesn't show much, but it does give the example line:
```
wireless-essid HOME
```
Replace the caps with the name of your wireless network, and add the line to the bottom of your /etc/network/interfaces file as part of the "iface wlan0" section.  

Looking at **man iwconfig** gives a few more options.  Note that these should all be preceded by "wireless-" when adding to the /etc/network/interfaces file.  I think for your purposes that the only one you need to worry about is "key" or "enc" (they're synonyms, you should only need one or the other):
> **key/enc**[ryption]

Used to manipulate encryption or scrambling keys and security mode. To set the current encryption key, just enter the key in hex digits  as  **XXXX-XXXX-XXXX-XXXX**  or **XXXXXXXX**.  To set a key other than the current key, prepend or append **[index]** to the key itself (this won&#8217;t change which is the active key). You can also enter  the  key  as an ASCII string by using the **s:** prefix. Passphrase is currently not supported.

To change which key is the currently active key, just enter **[index]** (without entering any key value). 

**off** and **on** disable and reenable encryption. 

The  security  mode  may be **open** or **restricted**, and its meaning depends on the card used. With most cards, in **open** mode no authentication is used and the card may also accept  non-encrypted  sessions, whereas in **restricted** mode only encrypted sessions are accepted and the card will use authentication if available.

If you need to set multiple keys, or set a key and change the active key, you  need to  use  multiple  key  directives. Arguments can be put in any order, the last one will take precedence.

**Examples:**
```
iwconfig eth0 key 0123-4567-89
iwconfig eth0 key [3] 0123-4567-89
iwconfig eth0 key s:password [2]
iwconfig eth0 key [2]
iwconfig eth0 key open
iwconfig eth0 key off
iwconfig eth0 key restricted [3] 0123456789
iwconfig eth0 key 01-23 key 45-67 [4] key [4]
```

So in your case, you'd add the following line to the bottom of your /etc/network/interfaces file, as part of the "iface wlan0" section:
```
wireless-key s:PASSCODE
```
Replace the caps as appropriate.  Note that this assumes you're using ASCII (i.e. regular alphanumerics) for your passcode and not hexadecimal (looks like "A56C48F8E"); delete the "s:" prefix for hexadecimal.  

HTH,

Eiríkr

PS -- The above will apparently work if you have WEP, but not WPA.  Post if you run into problems.

---

