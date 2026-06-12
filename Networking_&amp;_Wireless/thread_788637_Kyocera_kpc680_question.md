---
title: "Kyocera kpc680 question"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by kingofnoobs on 2008-05-09
Hi i am an inspiring linux learner and also one of the many that does not have a high speed connection so i am resorting to use a aircard from alltel a kyocera kpc680 it works great under windows but i wanna get into some linux so i been searching for a couple of days no and the only thing that i could find was on the kpc650 so i tryed doing what they did.

did the lsusb and it returned " bus 002 device 007: ID 0c88:180a kyocera wireless corp.

so then i type rmmod usbserial ; modprobe usbserial vendor=0xc88 product=0x180a and it returns with no error

then

mknod /dev/ttyUSB0 c 188 0 ; mknod /dev/ttyUSB1 c 188 1

good still


so i configure my wvdial.conf

[Dialer alltel]
Phone = #777
Password = alltel
Username = {my.alltel.phone#}@alltel.net
[Dialer Defaults]
Modem = /dev/ttyUSB0
Baud = 115200
Init = ATZ
Dial Command = ATDT
Stupid mode = 1

after that is all done i typed wvdial alltel and it dials and get a ip address and then stops

so i tryed to get on the internet and nothing so i rebooted and whent back to terminal and typed wvdial alltel and it cannot open /devttyUSB0: no such file or directory


any ideas i starting to get feed up with it

Thanks in advance

John

---

### Post by kingofnoobs on 2008-05-10
Bump

---

### Post by kingofnoobs on 2008-05-11
Bump does not look like i'm going to get any help with this.

---

### Post by coaltown on 2008-08-09
I had (still have) a similar problem with my kpc680. I got mine to get to the dialing stage by adding the device and vendor number to the airprime and option drivers. Once I could get it to dial using wvdial, my problem was that I could download about 20 K worth of internets before it would almost completely stop receiving data.

At first I thought this might be a problem with my PPP, so I started tweaking any /etc/ppp/options settings that I thought might be applicable. This yielded some good results, because sometimes, after changing a setting, it would dial and work perfectly until I disconnected. I now know that the intermittent success I was having was purely coincidental.

My latest messing around has revealed that the longer I wait between dialing and attempting to download content, the worse it works. This also might be coincidental, but, I'll keep trying. This time I got it to work by dialing and the second I had an IP, I loaded a web page. Again. this is probably coincidental.

Despite the seeming randomness of my success, I have determined for sure that under a still undetermined set of circumstances, the Kyocera KPC680 will work on Ubuntu. The question is, what are those circumnstances? Perhaps some people with some knowledge of drivers could lend us a hand?

Anyway, the long story short is this: Bump

---

### Post by Jim March on 2008-09-22
I'm wrestling with this nasty thing now after having lost my dead-simple-and-working USB720 device.

I'm on Verizon's version of the card and Ubuntu Hardy.  After much struggle I've got a working connection that doesn't die out very often; I'm on the Verizon version.  Here's WVDial:

---
[Dialer Defaults]
Init = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Auto Reconnect = on
Phone = #777
Password = vzw
Username = [email]myphonenumber@vzw3g.com[/email]
Modem = /dev/ttyUSB0
Baud = 460000
Dial Command = ATDT
Stupid mode = 1
---

I also had to do a "sudo modprobe airprime" first thing.

I briefly tried out Intrepid Alpha5 and while the Intel-based video and sound systems had glitches, Network Manager 7 recognized and used that USB720 device perfectly right off the bat, and without a wvdial script at all (indicating that the drivers and setup are internal to NM7.

I'm about to try Intrepid Alpha6 in the hope that the video/sound issues are better AND netmanager7 knows how to cope with a KPC680.  I'll report back over the next couple of days if that goes well.

---

### Post by Jim March on 2008-09-22
Posting so I can subscribe...

---

### Post by coaltown on 2008-09-22
Ok people. I think I finally have it. I added the nodeflate option to my /etc/ppp/options, and it seems to have done the trick. So far I've been able to connect first try every time with no problems loading pages even hours later. Give it a shot

---

### Post by warr85 on 2008-10-03
hello everybody, i'm new in ubuntu and i'm also new at this forum... i have a kyocera kpc680 xpress card and i would like to make it run under ubuntu 8.04, but i have no clue... i read that you make it run... so i asking for your help... can you explain me step by step how to configure de card under ubuntu. 

thanking you in advance...

---

### Post by Jim March on 2008-10-04
OK, I'm getting TOTAL success here.  This is how I did it.

First, note that I'm running Intrepid Beta 1, however I've tested it with AND without Network Manager 7, so, the option without NM7 should work for somebody with Hardy.  OK?

[COLOR="Red"]**THIS NEEDS TESTING IN REAL HARDY!!!**[/COLOR]

Second note: I'm telling you how to do this under Verizon's network - under some others WVDIAL's script will be a tad different.  If you can find a wvdial.conf script for your network (for any type of cellmodem), you should be able to splice it's bits in with my wvdial.conf script to make something workable.  Basically, the structure of the username/password stuff may differ, the "modem settings" will be the same.  Very basic hacking.

STEP ONE, needed with EITHER Hardy or Intrepid:

You need to edit /etc/ppp/options - at the command line do:

sudo gedit /etc/ppp/options

Make it look like this:

```
# /etc/ppp/options
# 
# Originally created by Jim Knoble <jmknoble@mercury.interpath.net>
# Modified for Debian by alvar Bray <alvar@meiko.co.uk>
# Modified for PPP Server setup by Christoph Lameter <clameter@debian.org>
#
# To quickly see what options are active in this file, use this command:
#   egrep -v '#|^ *$' /etc/ppp/options

# Specify which DNS Servers the incoming Win95 or WinNT Connection should use
# Two Servers can be remotely configured
# ms-dns 192.168.1.1
# ms-dns 192.168.1.2

# Specify which WINS Servers the incoming connection Win95 or WinNT should use
# ms-wins 192.168.1.50
# ms-wins 192.168.1.51

# Run the executable or shell command specified after pppd has
# terminated the link.  This script could, for example, issue commands
# to the modem to cause it to hang up if hardware modem control signals
# were not available.
#disconnect "chat -- \d+++\d\c OK ath0 OK"

# async character map -- 32-bit hex; each bit is a character
# that needs to be escaped for pppd to receive it.  0x00000001
# represents '\x01', and 0x80000000 represents '\x1f'.
asyncmap 0

# Require the peer to authenticate itself before allowing network
# packets to be sent or received.
# Please do not disable this setting. It is expected to be standard in
# future releases of pppd. Use the call option (see manpage) to disable
# authentication for specific peers.
#auth
noauth
# ... Unfortunately, fixing this properly in the peers file
# (/etc/ppp/peers/ppp0, typically) is apparently incompatible with the
# paradigm used by gnome-system-tools and system-tools-backend for
# managing the peers files.  So in Ubuntu Feisty we change the default.

# Use hardware flow control (i.e. RTS/CTS) to control the flow of data
# on the serial port.
#crtscts

# Use software flow control (i.e. XON/XOFF) to control the flow of data
# on the serial port.
#xonxoff

# Specifies that certain characters should be escaped on transmission
# (regardless of whether the peer requests them to be escaped with its
# async control character map).  The characters to be escaped are
# specified as a list of hex numbers separated by commas.  Note that
# almost any character can be specified for the escape option, unlike
# the asyncmap option which only allows control characters to be
# specified.  The characters which may not be escaped are those with hex
# values 0x20 - 0x3f or 0x5e.
#escape 11,13,ff

# Don't use the modem control lines.
#local

# Specifies that pppd should use a UUCP-style lock on the serial device
# to ensure exclusive access to the device.
lock

# Don't show the passwords when logging the contents of PAP packets.
# This is the default.
hide-password

# When logging the contents of PAP packets, this option causes pppd to
# show the password string in the log message.
#show-password

# Use the modem control lines.  On Ultrix, this option implies hardware
# flow control, as for the crtscts option.  (This option is not fully
# implemented.)
modem

# Set the MRU [Maximum Receive Unit] value to <n> for negotiation.  pppd
# will ask the peer to send packets of no more than <n> bytes. The
# minimum MRU value is 128.  The default MRU value is 1500.  A value of
# 296 is recommended for slow links (40 bytes for TCP/IP header + 256
# bytes of data).
#mru 542

# Set the interface netmask to <n>, a 32 bit netmask in "decimal dot"
# notation (e.g. 255.255.255.0).
#netmask 255.255.255.0

# Disables the default behaviour when no local IP address is specified,
# which is to determine (if possible) the local IP address from the
# hostname. With this option, the peer will have to supply the local IP
# address during IPCP negotiation (unless it specified explicitly on the
# command line or in an options file).
#noipdefault

# Enables the "passive" option in the LCP.  With this option, pppd will
# attempt to initiate a connection; if no reply is received from the
# peer, pppd will then just wait passively for a valid LCP packet from
# the peer (instead of exiting, as it does without this option).
#passive

# With this option, pppd will not transmit LCP packets to initiate a
# connection until a valid LCP packet is received from the peer (as for
# the "passive" option with old versions of pppd).
#silent

# Don't request or allow negotiation of any options for LCP and IPCP
# (use default values).
#-all

# Disable Address/Control compression negotiation (use default, i.e.
# address/control field disabled).
#-ac

# Disable asyncmap negotiation (use the default asyncmap, i.e. escape
# all control characters).
#-am

# Don't fork to become a background process (otherwise pppd will do so
# if a serial device is specified).
#-detach

# Disable IP address negotiation (with this option, the remote IP
# address must be specified with an option on the command line or in
# an options file).
#-ip

# Disable IPCP negotiation and IP communication. This option should
# only be required if the peer is buggy and gets confused by requests
# from pppd for IPCP negotiation.
#noip

# Disable magic number negotiation.  With this option, pppd cannot
# detect a looped-back line.
#-mn

# Disable MRU [Maximum Receive Unit] negotiation (use default, i.e.
# 1500).
#-mru

# Disable protocol field compression negotiation (use default, i.e.
# protocol field compression disabled).
#-pc

# Require the peer to authenticate itself using PAP.
#+pap

# Don't agree to authenticate using PAP.
#-pap

# Require the peer to authenticate itself using CHAP [Cryptographic
# Handshake Authentication Protocol] authentication.
#+chap

# Don't agree to authenticate using CHAP.
#-chap

# Disable negotiation of Van Jacobson style IP header compression (use
# default, i.e. no compression).
#-vj

# Increase debugging level (same as -d).  If this option is given, pppd
# will log the contents of all control packets sent or received in a
# readable form.  The packets are logged through syslog with facility
# daemon and level debug. This information can be directed to a file by
# setting up /etc/syslog.conf appropriately (see syslog.conf(5)).  (If
# pppd is compiled with extra debugging enabled, it will log messages
# using facility local2 instead of daemon).
#debug

# Append the domain name <d> to the local host name for authentication
# purposes.  For example, if gethostname() returns the name porsche,
# but the fully qualified domain name is porsche.Quotron.COM, you would
# use the domain option to set the domain name to Quotron.COM.
#domain <d>

# Enable debugging code in the kernel-level PPP driver.  The argument n
# is a number which is the sum of the following values: 1 to enable
# general debug messages, 2 to request that the contents of received
# packets be printed, and 4 to request that the contents of transmitted
# packets be printed.
#kdebug n

# Set the MTU [Maximum Transmit Unit] value to <n>. Unless the peer
# requests a smaller value via MRU negotiation, pppd will request that
# the kernel networking code send data packets of no more than n bytes
# through the PPP network interface.
#mtu <n>

# Set the name of the local system for authentication purposes to <n>.
# This is a privileged option. With this option, pppd will use lines in the
# secrets files which have <n> as the second field when looking for a
# secret to use in authenticating the peer. In addition, unless overridden
# with the user option, <n> will be used as the name to send to the peer
# when authenticating the local system to the peer. (Note that pppd does
# not append the domain name to <n>.)
#name <n>

# Enforce the use of the hostname as the name of the local system for
# authentication purposes (overrides the name option).
#usehostname

# Set the assumed name of the remote system for authentication purposes
# to <n>.
#remotename <n>

# Add an entry to this system's ARP [Address Resolution Protocol]
# table with the IP address of the peer and the Ethernet address of this
# system.
proxyarp

# Use the system password database for authenticating the peer using
# PAP. Note: mgetty already provides this option. If this is specified
# then dialin from users using a script under Linux to fire up ppp wont work.
# login

# If this option is given, pppd will send an LCP echo-request frame to the
# peer every n seconds. Normally the peer should respond to the echo-request
# by sending an echo-reply. This option can be used with the
# lcp-echo-failure option to detect that the peer is no longer connected.
lcp-echo-interval 0

# If this option is given, pppd will presume the peer to be dead if n
# LCP echo-requests are sent without receiving a valid LCP echo-reply.
# If this happens, pppd will terminate the connection.  Use of this
# option requires a non-zero value for the lcp-echo-interval parameter.
# This option can be used to enable pppd to terminate after the physical
# connection has been broken (e.g., the modem has hung up) in
# situations where no hardware modem control lines are available.
lcp-echo-failure 0

# Set the LCP restart interval (retransmission timeout) to <n> seconds
# (default 3).
#lcp-restart <n>

# Set the maximum number of LCP terminate-request transmissions to <n>
# (default 3).
#lcp-max-terminate <n>

# Set the maximum number of LCP configure-request transmissions to <n>
# (default 10).
#lcp-max-configure <n>

# Set the maximum number of LCP configure-NAKs returned before starting
# to send configure-Rejects instead to <n> (default 10).
#lcp-max-failure <n>

# Set the IPCP restart interval (retransmission timeout) to <n>
# seconds (default 3).
#ipcp-restart <n>

# Set the maximum number of IPCP terminate-request transmissions to <n>
# (default 3).
#ipcp-max-terminate <n>

# Set the maximum number of IPCP configure-request transmissions to <n>
# (default 10).
#ipcp-max-configure <n>

# Set the maximum number of IPCP configure-NAKs returned before starting
# to send configure-Rejects instead to <n> (default 10).
#ipcp-max-failure <n>

# Set the PAP restart interval (retransmission timeout) to <n> seconds
# (default 3).
#pap-restart <n>

# Set the maximum number of PAP authenticate-request transmissions to
# <n> (default 10).
#pap-max-authreq <n>

# Set the maximum time that pppd will wait for the peer to authenticate
# itself with PAP to <n> seconds (0 means no limit).
#pap-timeout <n>

# Set the CHAP restart interval (retransmission timeout for
# challenges) to <n> seconds (default 3).
#chap-restart <n>

# Set the maximum number of CHAP challenge transmissions to <n>
# (default 10).
#chap-max-challenge

# If this option is given, pppd will rechallenge the peer every <n>
# seconds.
#chap-interval <n>

# With this option, pppd will accept the peer's idea of our local IP
# address, even if the local IP address was specified in an option.
#ipcp-accept-local

# With this option, pppd will accept the peer's idea of its (remote) IP
# address, even if the remote IP address was specified in an option.
#ipcp-accept-remote

# Disable the IPXCP and IPX protocols.
# To let pppd pass IPX packets comment this out --- you'll probably also
# want to install ipxripd, and have the Internal IPX Network option enabled
# in your kernel.  /usr/doc/HOWTO/IPX-HOWTO.gz contains more info.
noipx

# Exit once a connection has been made and terminated. This is the default,
# unless the `persist' or `demand' option has been specified.
#nopersist

# Do not exit after a connection is terminated; instead try to reopen
# the connection.
#persist

# Terminate after n consecutive failed connection attempts.
# A value of 0 means no limit. The default value is 10.
#maxfail <n>

# Initiate the link only on demand, i.e. when data traffic is present. 
# With this option, the remote IP address must be specified by the user on
# the command line or in an options file.  Pppd will initially configure
# the interface and enable it for IP traffic without connecting to the peer. 
# When traffic is available, pppd will connect to the peer and perform
# negotiation, authentication, etc.  When this is completed, pppd will
# commence passing data packets (i.e., IP packets) across the link.
#demand

# Specifies that pppd should disconnect if the link is idle for <n> seconds.
# The link is idle when no data packets (i.e. IP packets) are being sent or
# received.  Note: it is not advisable to use this option with the persist
# option without the demand option.  If the active-filter option is given,
# data packets which are rejected by the specified activity filter also
# count as the link being idle.
#idle <n>

# Specifies how many seconds to wait before re-initiating the link after
# it terminates.  This option only has any effect if the persist or demand
# option is used.  The holdoff period is not applied if the link was
# terminated because it was idle.
#holdoff <n>

# Wait for up n milliseconds after the connect script finishes for a valid
# PPP packet from the peer.  At the end of this time, or when a valid PPP
# packet is received from the peer, pppd will commence negotiation by
# sending its first LCP packet.  The default value is 1000 (1 second).
# This wait period only applies if the connect or pty option is used.
#connect-delay <n>

# Packet filtering: for more information, see pppd(8)
# Any packets matching the filter expression will be interpreted as link
# activity, and will cause a "demand" connection to be activated, and reset
# the idle connection timer. (idle option)
# The filter expression is akin to that of tcpdump(1)
#active-filter <filter-expression>

# ---<End of File>---
```

The keys are the "0" parameters for the lines "lcp-echo-failure" and "lcp-echo-interval".  I *suspect* those need to be set to "0" for any cellular or EVDO modem.

Again: this step is for Hardy and Intrepid.

INTREPID STEP TWO:

Stick card in, use it in the Network Manager panel applet.  Bingo-presto :).

HARDY STEP TWO:

You'll have to use wvdial, which means creating a text file at /etc/wvdial.conf:

sudo gedit /etc/wvdial.conf

Here's my script - yours (if you're on Verizon) will change ONLY at the phone number part - we all use the same password.

```
[Dialer Defaults]
Dial Command = ATDT
Stupid mode = on
Carrier Check = no
ISDN = 0
Init = ATZ
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Auto Reconnect = on
Phone = #777
Password = vzw
Username = [*your phone number goes here, with area code, no "1" first, no brackets*]@vzw3g.com
Modem = /dev/ttyUSB0
Baud = 690000
[Dialer shh]
Init3 = ATM0
[Dialer pulse]
Dial Command = ATDP
Auto Reconnect = on
Carrier Check = no

```

**[COLOR="Red"]REAL HARDY NOTE: if anything in wvdial.conf needs tweaking, it will be in the line "Modem = /dev/ttyUSB0"...it might load as something other than ttyUSB0 (1, 2, godonlyknows...for that matter it might change if you already have a USB modem...USB WiFi or something...?)[/COLOR]**

Note that the "speed" is based on my own experimentation in my case, and performed just about identically with Network Manager 7 which auto-detects speed.  Default is 460000 - I tried incrementing it up and down in 230000 steps and hit on 690000.  There may be room for tuning and tweaking for specific cases, use [http://speedtest.net](http://speedtest.net) to check.

**To use the modem in Hardy, open a terminal window and do "sudo wvdial", put your password in, then leave that terminal window open.  It will take a bit for the connection to be functional - you'll know it's up when you see IP addresses for your connection and DNS.  Use "ctrl-c" to kill the connection when desired.**

A basic script can be created and run as well, but I would do it as "run in terminal" if you go that route.

Hope this helps.

**Credits:** the tweaks to /etc/ppp/options and some of the wvdial.conf tweaks are from user "MJamesd" at:

[http://ge.ubuntuforums.com/showthread.php?t=433405](http://ge.ubuntuforums.com/showthread.php?t=433405)

Many thanks...

---

### Post by mg620 on 2008-11-16
Thank you!  I just found this thread, thinking "no way is this going to work.  It (kpc680) has never worked."  It works!  Amazing!  I love Intrepid!  

I can't tell how fast it is, since I have barely any coverage at my home anyway, but will find out tomorrow when I'm out and about.  If anyone has a quick tip of how I might be able to check speed, that'd be great (but just icing on the cake).

Thanks again!  (Two major issues down, two to go, and then BYE WINDOWS!  And yes, I am shouting that.)

---

### Post by Jim March on 2008-11-27
The best website I've found to test your Internet access performance (regardless of connection type) is at:

[http://speedtest.net/](http://speedtest.net/)

---

### Post by dwouters on 2009-04-11
Mr. March, You are the man!!! The only thing that has kept me from converting 100% to Ubuntu was this dang card. I love Ubuntu. I have read all your posts and would like to say thank you very much for all the hard work you have put into getting this card working. You have worked with the developers and played hit and miss on your own. It's people like you that make Ubuntu great.

---

### Post by Jim March on 2009-04-11
Cool, thanks.  I've now done an upgrade to Jaunty beta from the working Intrepid install, and everything is still working (and yeah, I still use that card).

I just double-checked /etc/ppp/options and the lcp-echo parameters are still both set to "0".  So I would assume that's still needed for Jaunty.

---

### Post by dwouters on 2009-04-12
I just upgraded to Jaunty myself tonight. I will check the card in the morning but I'm confident that all will be fine. I too had to set the lcp-echo to "0". Minor adjustment for me to have to do so I can get rid of "you know who".

---

### Post by dwouters on 2009-04-14
> **Jim March said:**
> Cool, thanks.  I've now done an upgrade to Jaunty beta from the working Intrepid install, and everything is still working (and yeah, I still use that card).

I just double-checked /etc/ppp/options and the lcp-echo parameters are still both set to "0".  So I would assume that's still needed for Jaunty.

Update to this posting. Fresh install of Ubuntu 8.10 then upgrade to Jaunty. No modifications to /etc/ppp/options, this card works out of the box. The default settings appear to be fine.

---

### Post by urbangeek on 2009-05-16
Hey folks I just wanted to add some feedback on this as well since I use the card as tell on my HP dv7-1273CL I only changed the ppp options as stated and the card works fine as well now. before I didnt it would connect but not access the internet. so 9.04 you may still have to modify the /etc/ppp/options my carrier is mobipcs here in hawaii

---

### Post by dwouters on 2009-05-17
> **urbangeek said:**
> Hey folks I just wanted to add some feedback on this as well since I use the card as tell on my HP dv7-1273CL I only changed the ppp options as stated and the card works fine as well now. before I didnt it would connect but not access the internet. so 9.04 you may still have to modify the /etc/ppp/options my carrier is mobipcs here in hawaii

Great to hear urbangeek! However, after a clean install of 9.04, I had to make zero "0" modifications. I am able to put the card in and go. I have no connection issues and stay online as long as I like. Good advise though if anyone does have any issues with this card. Maybe, I have just been one of the lucky ones, huh?

---

### Post by BigIslandVegan on 2010-03-21
Are you folks using the ExpressCard / PCMCIA card or some kind of USB device?

I have a Kyocera KPC680 ExpressCard with a PCMCIA adapter. I'm trying to use this with Ubuntu 9.10 on a Toshiba laptop with PCMCIA port.

The lsusb command does not work with this device, it seems.

Does anybody know how to make this work for 9.10? I am another Hawaii / MobiPCS - Hele user. :-)

Aloha

---

