---
title: "can't start firestarter"
date: 2007-11-30
forum: Networking &amp; Wireless
---

### Post by alan-1 on 2007-11-30
wired connection thro router to internet works fine (eth0)
but firestarter will not start, shows (eth1not ready) 
eth1used to have usb wireless device attached but not any more (no longer needed)
please tell me how to enable firestarter i am a total novice.

---

### Post by edm1 on 2007-11-30
look [here]("http://ubuntuforums.org/showthread.php?t=468630"). I thiink it may be a bug with network manager rather then the firestarter daemon.

---

### Post by Majorix on 2007-11-30
Reconfigure Firestarter to disinclude eth1. In the main menu Firewall > Run wizard.

---

### Post by Majorix on 2007-11-30
> **edm1 said:**
> look [here]("http://ubuntuforums.org/showthread.php?t=468630"). I thiink it may be a bug with network manager rather then the firestarter daemon.

The OP says he actually no longer has eth1. The two threads are not related.

---

### Post by alan-1 on 2007-11-30
running firestarter wizard does not show eth1, network settings only shows eth0 but firestarter refuses to start saying eth1 not ready

---

### Post by edm1 on 2007-11-30
Scrap my first post for the time being. During bootup you are given the message "External network device eth1 is not ready. Aborting..." even though now you are using eth0 not eth1?

Try

```
gksudo gedit /etc/firestarter/configuration
```
then replace all instances of 'eth1' with 'eth0', save and reboot.

Then to test if this has worked: Immediately after booting, open a terminal, type
```
sudo iptables -L
```
and post the results.

---

### Post by alan-1 on 2007-11-30
before i change anything this fire starter configuration file

#-----------( Firestarter Configuration File )-----------#

# --(External Interface)--
# Name of external network interface
IF="eth1"
# Network interface is a PPP link
EXT_PPP="off"

# --(Internal Interface--)
# Name of internal network interface
INIF="eth0"

# --(Network Address Translation)--
# Enable NAT
NAT="off"
# Enable DHCP server for NAT clients
DHCP_SERVER="off"
# Forward server's DNS settings to clients in DHCP lease
DHCP_DYNAMIC_DNS="on"

# --(Inbound Traffic)--
# Packet rejection method
#   DROP:   Ignore the packet
#   REJECT: Send back an error packet in response
STOP_TARGET="DROP"

# --(Outbound Traffic)--
# Default Outbound Traffic Policy
#   permissive: everything not denied is allowed
#   restrictive everything not allowed is denied
OUTBOUND_POLICY="permissive"

# --(Type of Service)--
# Enable ToS filtering
FILTER_TOS="off"
# Apply ToS to typical client tasks such as SSH and HTTP
TOS_CLIENT="off"
# Apply ToS to typical server tasks such as SSH, HTTP, HTTPS and POP3
TOS_SERVER="off"
# Apply ToS to Remote X server connections
TOS_X="off"
# ToS parameters
#   4:  Maximize Reliability
#   8:  Maximize-Throughput
#   16: Minimize-Delay
TOSOPT=

# --(ICMP Filtering)--
# Enable ICMP filtering
FILTER_ICMP="off"
# Allow Echo requests
ICMP_ECHO_REQUEST="off"
# Allow Echo replies
ICMP_ECHO_REPLY="off"
# Allow Traceroute requests
ICMP_TRACEROUTE="off"
# Allow MS Traceroute Requests
ICMP_MSTRACEROUTE="off"
# Allow Unreachable Requests
ICMP_UNREACHABLE="off"
# Allow Timestamping Requests
ICMP_TIMESTAMPING="off"
# Allow Address Masking Requests
ICMP_MASKING="off"
# Allow Redirection Requests
ICMP_REDIRECTION="off"
# Allow Source Quench Requests
ICMP_SOURCE_QUENCHES="off"

# --(Broadcast Traffic)--
# Block external broadcast traffic
BLOCK_EXTERNAL_BROADCAST="on"
# Block internal broadcast traffic
BLOCK_INTERNAL_BROADCAST="off"

# --(Traffic Validation)--
# Block non-routable traffic on the public interfaces
BLOCK_NON_ROUTABLES="off"

# --(Logging)--
# System log level
LOG_LEVEL=info

---

### Post by edm1 on 2007-11-30
yep you have eth1 set as the device connected to the internet.

if you want to back up the file first do

```
sudo cp /etc/firestarter/configuration /etc/firestarter/configuration_backup
```

---

### Post by alan-1 on 2007-11-30
please forgive my ignorance but firestarter configuration file displays as **read only** how do i make the changes you suggest?

---

### Post by edm1 on 2007-11-30
Open the terminal (Applications>Accessories>Terminal), type/copy this

```
sudo gedit /etc/firestarter/configuration
```

Reason:
sudo - (should strictly be gksudo) gives you root access (administrator privileges)
gedit - is the name of the text editor that will read the file
and of course the file.

Just realised you could just change the setting using firestarter's GUI by System>Administration>Firestarter then Preferences>Network Settings and change them both to eth0.

---

### Post by alan-1 on 2007-11-30
still read only, the gui shows shows eth0 connected to internet
local network field is grayed out

---

### Post by edm1 on 2007-11-30
thats very strange, not sure why it's doing that. for a temporary/crude solution my first suggestion (in post #2) should allow the firestarter daemon to load on booting.

---

### Post by alan-1 on 2007-11-30
thankyou for trying edm1 I might look at it try again tommorow.

---

### Post by cari on 2007-12-10
Hi!

I have exactly the same problem:
[http://dcmdb.planet.ee/Screenshot.png](http://dcmdb.planet.ee/Screenshot.png)
this shows, that I have wireless device ra0, and it is active (data transferred etc), but still firestarter refuses to initialize.

in the preferences menu, I basically can't change anything: [http://dcmdb.planet.ee/Screenshot2.png](http://dcmdb.planet.ee/Screenshot2.png)

When I boot up, console shows something like: Starting firestarter [failed], I assume, it's because firestarter thinks that my device isn't active

Any help appreciated :)

---

### Post by edm1 on 2007-12-10
I'm not sure whats going on here, are there any [bug reports]("http://bugzilla.gnome.org/buglist.cgi?query=firestarter") for it? It shouldnt matter that this setting isn't working unless you are using your computer to share the internet connection through a second network card. Firestarter will not load unless the interface is ready but you should be able to force it to start with the hack on [this thread]("http://ubuntuforums.org/showthread.php?t=468630").

---

