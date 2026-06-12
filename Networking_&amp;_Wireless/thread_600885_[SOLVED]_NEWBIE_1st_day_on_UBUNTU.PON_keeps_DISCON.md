---
title: "[SOLVED] NEWBIE 1st day on UBUNTU.PON keeps DISCONNECTING after connecting fine   USB"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by abishek22 on 2007-11-02
i'm trying to connect a usb phone momdem to via gprs to connect to the net



i have a Pocket pc ATOM after searching the net up and down found the following  on a site 

 
                                          Airtel GPRS on FC5 Linux with O2 Atom



Posted by akshay under: HowTo .
   1.Connect the O2 to your pc via any usb port and turn on the modem on the phone.

   2.Type: cat /proc/bus/usb/devices

   3.Look out for "Windows USB Modem"

   4. Check the values of vendor and productid for that listing, in my case, they are 0408 and 0079 respectively

   5. Then: /sbin/modprobe ipaq vendor=0x0408 product=0x0079

   6.   Then see the output of: dmesg

   7. It should show something like: ipaq 3-1:1.0: PocketPC PDA converter detected,usb 3-1: PocketPC PDA converter now attached to ttyUSB0

   8.  Now, open KPPP from the Internet menu of KDE

   9.  Setup a new modem at /dev/ttyUSB0, choose a high enough speed like 115200 or more

  10. Set *99# as the phone number, username & password dont matter, put your phone number for both.

  11.  Hit Connect

after following the steps and running the command in root and creating a connection using ppp.the internet got connected but disconnects in 2 mins


1)problem


why doesn't my modem show up in modems in network???



2)the guy said create a ppp connection 

i use a UBUNTU i think its a gnome i cant kind a KDE neither am i proficient enough to even attempt switching it


on creating a connection named provider and using the command called PON PROVIDER

the internet connects works well alas i stops working in about 2 mins help!!!!!!!!!!!!!1

i'm trying to break my head here to some how get the net connected to download divx,vlc player


can some one tell me what to do..with regards to this problem  i found this on another site but i dotn understand how to


"To fix this, I created script into /etc/ppp/ip-up.d/zzz-fix-route:
#!/bin/sh
/sbin/route del default gw 0.0.0.0      # Remove nonsense route
/sbin/route add default gw $PPP_REMOTE  # Add correct route

Remember to make the file executable. The “zzz-” prefix insures that it is the last script run, just to prevent a script after it from misconfiguring the route again"


HOW DO I MAKE AN EXECUTABLE FILE?


THE WHOLE THING IS FROM HERE
\


Setting up ppp

There are some great GUI tools for setting up PPP on Linux, but I don’t care to use them. I like editing text files and working on the CLI.

To get things working, we only need to create several different files (as superuser). The first, /etc/ppp/peers/sprint:
/dev/ttyUSB0    # modem
921600          # faster than this has no effect, and actually can be detrimental
defaultroute    # use cellular network for default route
usepeerdns      # use the DNS servers from the remote network
#nodetach        # keep pppd in the foreground
#debug
crtscts        # hardware flow control
lock            # lock the serial port
noauth          # don't expect the modem to authenticate itself
local          # don't use Carrier Detect or Data Terminal Ready
persist        # Redial if connection lost
user
ppp
holdoff 5      # Reconnect after 5s on connection loss

lcp-echo-failure 4      # prevent timeouts
lcp-echo-interval 65535 # prevent timeouts

connect        "/usr/sbin/chat -v -f /etc/chatscripts/sprint-connect"
disconnect      "/usr/sbin/chat -v -f /etc/chatscripts/sprint-disconnect"

Notice that you do not need your Sprint PCS username or password. The modem authenticates itself to Sprint in hardware via its ESN. Next is /etc/chatscripts/sprint-connect:
TIMEOUT 10
ABORT 'BUSY'
ABORT 'NO ANSWER'
ABORT 'ERROR'
SAY 'Starting Sprint...\n'

# Get the modem's attention and reset it.
""      'ATZ'
# E0=No echo, V1=English result codes
OK    'ATE0V1'

# List signal quality
'OK' 'AT+CSQ'

'OK' 'ATDT#777'
CONNECT
and your connection will work And then the optional /etc/chatscripts/sprint-disconnect:
"" "\K"
"" "+++ATH0"
SAY "Disconnected from Sprint."

You can also setup this connecton in /etc/network/interfaces, adding the stanza (assuming you want to use ppp0):
iface ppp0 inet ppp
        provider sprint

And that’s basically it! If you setup your interfaces file, you can simply run:
sudo ifup ppp0

to bring up the connection. Remember to ifdown the interface to disconnect. If not using interfaces, you can use the pon/poff pair of commands:
sudo pon sprint # Start connection
sudo poff sprint # Stop connection
Problem: default route does not get set

For some reason, my default route is not set properly. If not set properly, you look as if you’ve been connected to Sprint, but you will not actually be able to connect to any site on the Internet. To check if this is happening to you, look at the last line of “route -n” and see if it reads the nonsense:
0.0.0.0        0.0.0.0    0.0.0.0        UG    0      0        0 ppp0

To fix this, I created script into /etc/ppp/ip-up.d/zzz-fix-route:
#!/bin/sh
/sbin/route del default gw 0.0.0.0      # Remove nonsense route
/sbin/route add default gw $PPP_REMOTE  # Add correct route

Remember to make the file executable. The “zzz-” prefix insures that it is the last script run, just to prevent a script after it from misconfiguring the route again,










[B]CAN SOME ONE TELL ME HOW TO GET MY NET TO STAY ON PLS!! I THINK THE ANSWER IS SOME WHERE ABOVE BUT I CANT UNDERSTAND HOW TO DO IT................HELP!!

MY SETTINGS ARE ALMOST SAME ISP REQUIRES NO USERNAME AND PASSWWORD 
[/B]

---

### Post by abishek22 on 2007-11-02
this is what plog shows



abishek@Delllaptop:~$ plog
Nov  3 05:01:37 Delllaptop pppd[7831]: No response to 4 echo-requests
Nov  3 05:01:37 Delllaptop pppd[7831]: Serial link appears to be disconnected.
Nov  3 05:01:37 Delllaptop pppd[7831]: Connect time 2.0 minutes.
Nov  3 05:01:37 Delllaptop pppd[7831]: Sent 45072 bytes, received 107180 bytes.
Nov  3 05:01:37 Delllaptop pppd[7831]: Script /etc/ppp/ip-down started (pid 7886)
Nov  3 05:01:37 Delllaptop pppd[7831]: sent [LCP TermReq id=0x2 "Peer not responding"]
Nov  3 05:01:37 Delllaptop pppd[7831]: Script /etc/ppp/ip-down finished (pid 7886), status = 0x0
Nov  3 05:01:37 Delllaptop pppd[7831]: rcvd [LCP TermAck id=0x2]
Nov  3 05:01:37 Delllaptop pppd[7831]: Connection terminated.
Nov  3 05:01:38 Delllaptop pppd[7831]: Exit.

---

### Post by abishek22 on 2007-11-02
abishek@Delllaptop:~$ pon
abishek@Delllaptop:~$ plog
Nov  3 05:03:19 Delllaptop pppd[7934]: rcvd [IPCP ConfAck id=0x5 <addr 117.97.11.250> <ms-dns1 202.56.250.5> <ms-dns3 202.56.250.6>]
Nov  3 05:03:19 Delllaptop pppd[7934]: Cannot determine ethernet address for proxy ARP
Nov  3 05:03:19 Delllaptop pppd[7934]: local  IP address 117.97.11.250
Nov  3 05:03:19 Delllaptop pppd[7934]: remote IP address 10.0.0.1
Nov  3 05:03:19 Delllaptop pppd[7934]: primary   DNS address 202.56.250.5
Nov  3 05:03:19 Delllaptop pppd[7934]: secondary DNS address 202.56.250.6
Nov  3 05:03:19 Delllaptop pppd[7934]: Script /etc/ppp/ip-up started (pid 7938)
Nov  3 05:03:19 Delllaptop pppd[7934]: Script /etc/ppp/ip-up finished (pid 7938), status = 0x0
Nov  3 05:03:47 Delllaptop pppd[7934]: appear to have received our own echo-reply!
Nov  3 05:04:17 Delllaptop pppd[7934]: appear to have received our own echo-reply!
abishek@Delllaptop:~$ plog
Nov  3 05:04:47 Delllaptop pppd[7934]: appear to have received our own echo-reply!
Nov  3 05:05:17 Delllaptop pppd[7934]: No response to 4 echo-requests
Nov  3 05:05:17 Delllaptop pppd[7934]: Serial link appears to be disconnected.
Nov  3 05:05:17 Delllaptop pppd[7934]: Connect time 2.0 minutes.
Nov  3 05:05:17 Delllaptop pppd[7934]: Sent 19225 bytes, received 236030 bytes.
Nov  3 05:05:17 Delllaptop pppd[7934]: Script /etc/ppp/ip-down started (pid 7966)
Nov  3 05:05:17 Delllaptop pppd[7934]: sent [LCP TermReq id=0x2 "Peer not responding"]
Nov  3 05:05:17 Delllaptop pppd[7934]: Script /etc/ppp/ip-down finished (pid 7966), status = 0x0
Nov  3 05:05:17 Delllaptop pppd[7934]: rcvd [LCP TermAck id=0x2]
Nov  3 05:05:17 Delllaptop pppd[7934]: Connection terminated.

---

