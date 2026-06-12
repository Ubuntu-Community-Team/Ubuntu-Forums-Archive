---
title: "Upgraded wicd, now can't connect to any network"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by oldsmobile_mike on 2008-01-26
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=674759](http://ubuntuforums.org/showthread.php?t=674759) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Well, the latest version of wicd (1.4.1) just broke on me.  Hopefully some of the same helpful fellows who showed me how to get it set up in the first place can chime in again?  (hint hint!  ;-)

Here's what happened:

I installed wicd 1.3.1 about a week ago, and was using it to connect to the wireless network at my girlfriend's house.  I got it set up to use WEP-64 and MAC address filtering (for extra security) on the router, and everything worked fine.  Then I took the laptop home, where I connect via wired Ethernet, and got annoyed that I had to manually restart wicd each time I rebooted my computer.  Fortunately I got advice on this forum that told me how to download wicd version 1.4.1, which fixed the bug, and after that wicd would start automatically every time I turned on the laptop, and connect via the wired Ethernet.

Now here it is the weekend again, and I'm back at my girlfriend's place.  However, when I start wicd it gives me the message "Generating WPA configuration file", and doesn't connect to the wireless network - even though it worked fine last weekend with version 1.3.1.  I tried plugging the laptop directly into the router, and it still gave me that same error message.  I was able to access the Preferences button, and even though both networks (wired and wireless) were showing up on the wicd screen, I could not select the "Connect" button for either one - it's like they were grayed out, and all I got was the "Generating WPA configuration file", with an option to cancel.  Selecting Cancel did not actually cancel the application, but a minute or two later wicd would close it's window.  I tried rebooting, and nothing changed.  Attempted numerous changes in the Preferences screen, but still all I got was the "Generating WPA configuration file" message, and remember - I wasn't even using WPA at her place.

So I uninstalled wicd and reinstalled network-manager, and it connects fine.  Thinking that it might just be a settings glitch, I removed network-manager again, reinstalled wicd 1.4.1, and still got the same error - both networks showed up on the list, but I could not select Connect, and it just said "Generating WPA configuration file" down at the bottom.

So I removed wicd again, and reinstalled network-manager again, and it works fine - I am able to connect via both the wireless, and when plugged directly into her router, but I'd really like to use wicd, which seems a lot more powerful than the standard network-manager.  What is going on??  :confused:

Should I post my wicd.log file?  (it's very long)

---

### Post by imdano on 2008-01-26
Sounds like something is crashing during the connection process, which is making it freeze at the "Generating WPA configuration file" step.  Close the tray/gui, and kill the daemon with "sudo /etc/init.d/wicd stop".  Open up /opt/wicd/daemon.py, and find this section of code (it will be near the very end of the file
[php]if True: #for easy disabling
    try:
        pid = os.fork()
        if pid > 0:
            # exit first parent
            sys.exit(0)[/php]
Change it to read [php]if False: #for easy disabling
    try:
        pid = os.fork()
        if pid > 0:
            # exit first parent
            sys.exit(0)[/php]

Then move down a few lines and look for these lines [php]output = FlushWriter()
sys.stdout = output #open("data/wicd.log","w")
sys.stderr = output[/php]And comment them out: [php]#output = FlushWriter()
#sys.stdout = output #open("data/wicd.log","w")
#sys.stderr = output[/php]

Then open up a console and run sudo "/opt/wicd/daemon.py", it should start up and start displaying a lot of output.  Then run the tray (/opt/wicd/tray.py) from another console.  Try connecting and post any error messages that appear.

---

### Post by oldsmobile_mike on 2008-01-26
> **imdano said:**
> Then open up a console and run sudo "/opt/wicd/daemon.py", it should start up and start displaying a lot of output.  Then run the tray (/opt/wicd/tray.py) from another console.  Try connecting and post any error messages that appear.

Hi imdano, you are correct.  It displayed a lot of error messages.  Specifically I noticed a few, such as one that said "IOError: [Errno 2] No such file or directory: 'encryption/templates/wep'", and I tried duplicating one of the other files in that same directory (wep-hex, renamed it as wep to see if that would make a difference, but it didn't), I also saw the error "** (gui.py:6504): CRITICAL **: draw_box: assertion `height >= -1' failed", don't know what to do about that one...

Anyhow, here's a few log files:



**From wicd.log:**

2008/01/26 21:08:09 :: ---------------------------
2008/01/26 21:08:09 :: wicd initalizing...
2008/01/26 21:08:09 :: ---------------------------
2008/01/26 21:08:09 :: found wireless interface in configuration... setting wireless interface eth2
2008/01/26 21:08:10 :: found wired interface in configuration... setting wired interface eth0
2008/01/26 21:08:10 :: found wpa driver in configuration... setting wpa driver wext
2008/01/26 21:08:10 :: 0
2008/01/26 21:08:10 :: setting use global dns to 0
2008/01/26 21:08:10 :: setting use global dns to boolean False
2008/01/26 21:08:10 :: setting global dns
2008/01/26 21:08:10 :: global dns servers are False False False
2008/01/26 21:08:10 :: wired autoconnection method is 2
2008/01/26 21:08:10 :: wireless configuration file found...
2008/01/26 21:08:10 :: wired configuration file found...
2008/01/26 21:08:10 :: chmoding configuration files 0600...
2008/01/26 21:08:10 :: chowning configuration files root:root...
2008/01/26 21:08:10 :: autodetected wireless interface... automatically detected wireless interface eth2
2008/01/26 21:08:10 :: eth2
2008/01/26 21:08:10 :: using wireless interface... returning wireless interface to client
2008/01/26 21:08:10 :: eth2
2008/01/26 21:08:10 :: autoconnecting... returning wireless interface to client
2008/01/26 21:08:10 :: eth2
2008/01/26 21:08:10 :: scanning start
2008/01/26 21:08:10 ::  ##### 00:12:0E:5D:77:3D
2008/01/26 21:08:10 :: scanning done
2008/01/26 21:08:10 :: found 1 networks: 00:12:0E:5D:77:3D
2008/01/26 21:08:10 :: 
2008/01/26 21:08:10 :: no wired connection present, wired autoconnect failed
2008/01/26 21:08:11 :: attempting to autoconnect to wireless network
2008/01/26 21:08:11 :: returning wireless interface to client
2008/01/26 21:08:11 :: LR555 has profile
2008/01/26 21:08:11 :: trying to automatically connect to... LR555
2008/01/26 21:08:11 :: returned wireless network 0 property beforescript of type <type 'NoneType'>
2008/01/26 21:08:11 :: returned wireless network 0 property afterscript of type <type 'NoneType'>
2008/01/26 21:08:11 :: returned wireless network 0 property disconnectscript of type <type 'NoneType'>
2008/01/26 21:08:11 :: connecting to wireless network LR555
2008/01/26 21:08:11 :: interface down...
2008/01/26 21:08:11 :: Setting false ip...
2008/01/26 21:08:11 :: killing wpa_supplicant, dhclient, dhclient3
2008/01/26 21:08:11 :: generating psk...
2008/01/26 21:08:11 :: generating wpa_supplicant configuration file...
2008/01/26 21:08:11 :: Exception in thread Thread-1:
2008/01/26 21:08:11 :: Traceback (most recent call last):
2008/01/26 21:08:11 ::   File "threading.py", line 460, in __bootstrap
2008/01/26 21:08:11 ::     self.run()
2008/01/26 21:08:11 ::   File "/opt/wicd/networking.py", line 401, in run
2008/01/26 21:08:11 ::     misc.ParseEncryption(network)
2008/01/26 21:08:11 ::   File "/opt/wicd/misc.py", line 77, in ParseEncryption
2008/01/26 21:08:11 ::     enctemplate = open("encryption/templates/" + network["enctype"])
2008/01/26 21:08:11 :: IOError: [Errno 2] No such file or directory: 'encryption/templates/wep'
2008/01/26 21:08:11 :: 
2008/01/26 21:08:11 :: None
2008/01/26 21:08:16 :: returning always show wired interface False
2008/01/26 21:08:30 :: returned number of networks... 1
2008/01/26 21:08:30 :: returned number of networks... 1
2008/01/26 21:08:30 :: returned number of networks... 1
2008/01/26 21:08:30 :: returned wireless network 0 property essid of type <type 'str'>
2008/01/26 21:08:30 :: returned wireless network 0 property essid of type <type 'str'>
2008/01/26 21:08:30 :: returned wireless network 0 property essid of type <type 'str'>
2008/01/26 21:08:30 :: returned wireless network 0 property ip of type <type 'NoneType'>
2008/01/26 21:08:30 :: returned wireless network 0 property netmask of type <type 'NoneType'>
2008/01/26 21:08:30 :: returned wireless network 0 property gateway of type <type 'NoneType'>
2008/01/26 21:08:30 :: returned wireless network 0 property use_global_dns of type <type 'NoneType'>
2008/01/26 21:08:30 :: returned wireless network 0 property dns1 of type <type 'NoneType'>
2008/01/26 21:08:30 :: returned wireless network 0 property dns2 of type <type 'NoneType'>
2008/01/26 21:08:30 :: returned wireless network 0 property dns3 of type <type 'NoneType'>
2008/01/26 21:08:30 :: returned wireless network 0 property beforescript of type <type 'NoneType'>
2008/01/26 21:08:30 :: returned wireless network 0 property afterscript of type <type 'NoneType'>
2008/01/26 21:08:30 :: returned wireless network 0 property disconnectscript of type <type 'NoneType'>
2008/01/26 21:08:30 :: returned wireless network 0 property automatic of type <type 'bool'>
2008/01/26 21:08:30 :: setting wireless network 0 property automatic to value 1
2008/01/26 21:08:30 :: setting network option automatic to True
2008/01/26 21:08:30 :: returned wireless network 0 property enctype of type <type 'str'>
2008/01/26 21:08:30 :: returned wireless network 0 property enctype of type <type 'str'>
2008/01/26 21:08:30 :: returned wireless network 0 property enctype of type <type 'str'>
2008/01/26 21:08:30 :: returned wireless network 0 property enctype of type <type 'str'>
2008/01/26 21:08:30 :: returned wireless network 0 property enctype of type <type 'str'>
2008/01/26 21:08:30 :: returned wireless network 0 property enctype of type <type 'str'>
2008/01/26 21:08:30 :: returned wireless network 0 property enctype of type <type 'str'>
2008/01/26 21:08:30 :: returned wireless network 0 property enctype of type <type 'str'>
2008/01/26 21:08:30 :: returned wireless network 0 property key of type <type 'str'>
2008/01/26 21:08:30 :: returned wireless network 0 property quality of type <type 'int'>
2008/01/26 21:08:30 :: returned wireless network 0 property strength of type <type 'str'>
2008/01/26 21:08:30 :: returned wpa driver
2008/01/26 21:08:30 :: returned wpa driver
2008/01/26 21:08:30 :: returned wireless network 0 property bssid of type <type 'str'>
2008/01/26 21:08:30 :: returned wireless network 0 property mode of type <type 'str'>
2008/01/26 21:08:30 :: returned wireless network 0 property channel of type <type 'str'>
2008/01/26 21:08:30 :: returned wireless network 0 property encryption of type <type 'bool'>
2008/01/26 21:08:30 :: returned wireless network 0 property encryption_method of type <type 'str'>
2008/01/26 21:08:30 :: 


**From when I tried to start /opt/wicd/tray.py:**


attempting to connect daemon...
success
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
attempting to connect daemon...
success
starting gui.py...
refreshing...
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
attempting to connect daemon...
success
starting gui.py...
refreshing...
Number of wireless networks detected: 1
using global dns: 0
ESSID : LR555
making a new network entry...
disabling ip
disabling dns
dns checkbox toggled False
global dns checkbox toggled False
0
found language key key

** (gui.py:6504): CRITICAL **: draw_box: assertion `height >= -1' failed
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
  eth2:   13178     292    0    0    0     0          0         0    14803      84    4    0    0     0       0          0
not trans
0
m| 10000
not rec
mike@Sager-5600P:~$


**And from when I started /opt/wicd/daemon.py (some of this got cut off at the top, I believe...)**

wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
returning wireless interface to client
wired connecting False
returning wireless interface to client
wireless connecting True
returning wireless interface to client

returning wireless interface to client
status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless interface to client
returning wireless interface to client
returning wired ip None
returning wireless ip None
returning automatically reconnect when connection drops False
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wired ip None
returning wireless ip None
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wired ip None
returning wireless ip None
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wired ip None
returning wireless ip None
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wired ip None
returning wireless ip None
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wired ip None
returning wireless ip None
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wired ip None
returning wireless ip None
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wired ip None
returning wireless ip None
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wired ip None
returning wireless ip None
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wired ip None
returning wireless ip None
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wired ip None
returning wireless ip None
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wired ip None
returning wireless ip None
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wired ip None
returning wireless ip None
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wired ip None
returning wireless ip None
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wireless interface to client
returning wired ip None
returning wireless ip None


returning always show wired interface False
returned number of networks... 1
returned number of networks... 1
returned number of networks... 1
returned wireless network 0 property essid of type <type 'str'>
returned wireless network 0 property essid of type <type 'str'>
returned wireless network 0 property essid of type <type 'str'>
returned wireless network 0 property ip of type <type 'NoneType'>
returned wireless network 0 property netmask of type <type 'NoneType'>
returned wireless network 0 property gateway of type <type 'NoneType'>
returned wireless network 0 property use_global_dns of type <type 'NoneType'>
returned wireless network 0 property dns1 of type <type 'NoneType'>
returned wireless network 0 property dns2 of type <type 'NoneType'>
returned wireless network 0 property dns3 of type <type 'NoneType'>
returned wireless network 0 property beforescript of type <type 'NoneType'>
returned wireless network 0 property afterscript of type <type 'NoneType'>
returned wireless network 0 property disconnectscript of type <type 'NoneType'>
returned wireless network 0 property automatic of type <type 'bool'>
setting wireless network 0 property automatic to value 1
setting network option automatic to True
returned wireless network 0 property enctype of type <type 'str'>
returned wireless network 0 property enctype of type <type 'str'>
returned wireless network 0 property enctype of type <type 'str'>
returned wireless network 0 property enctype of type <type 'str'>
returned wireless network 0 property enctype of type <type 'str'>
returned wireless network 0 property enctype of type <type 'str'>
returned wireless network 0 property enctype of type <type 'str'>
returned wireless network 0 property enctype of type <type 'str'>
returned wireless network 0 property key of type <type 'str'>
returned wireless network 0 property quality of type <type 'int'>
returned wireless network 0 property strength of type <type 'str'>
returned wpa driver
returned wpa driver
returned wireless network 0 property bssid of type <type 'str'>
returned wireless network 0 property mode of type <type 'str'>
returned wireless network 0 property channel of type <type 'str'>
returned wireless network 0 property encryption of type <type 'bool'>
returned wireless network 0 property encryption_method of type <type 'str'>
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
canceling connection attempt
dhclient: no process killed
dhclient3: no process killed
wpa_supplicant: no process killed
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config
returning wireless ip None
wired connecting False
wireless connecting True

status request
acqlock True
 ...lock acquired...
 ...lock released...
wireless connect status generating_wpa_config


Traceback (most recent call last):
  File "/opt/wicd/daemon.py", line 1236, in <module>
    mainloop.run()
KeyboardInterrupt
mike@Sager-5600P:~$

---

### Post by imdano on 2008-01-26
Ok, well the reason the connection process is freezing up is almost certainly because of the absense of the wep template.  What does the /opt/wicd/encryptions/templates/active file look like?  Make sure it matches this:
> wpa
wep-hex
wep-passphrase
leap
ttls
eap
peap
peap-tkipThen restart the daemon and tray/gui and see if that error goes away.  If everything works normally, revert the changes you made to the daemon, and restart it using ```
sudo /etc/init.d/wicd start
```And restart the tray/gui again as well (you don't have to run it from the console this time, since hopefully everything will be working normally).

---

### Post by oldsmobile_mike on 2008-01-27
> **imdano said:**
> Ok, well the reason the connection process is freezing up is almost certainly because of the absense of the wep template.  What does the /opt/wicd/encryptions/templates/active file look like?  Make sure it matches this:
Then restart the daemon and tray/gui and see if that error goes away.  If everything works normally, revert the changes you made to the daemon, and restart it using ```
sudo /etc/init.d/wicd start
```And restart the tray/gui again as well (you don't have to run it from the console this time, since hopefully everything will be working normally).

Hi,

Not sure what you want me to do here.  The /opt/wicd/encryptions/templates/active file does look as you describe (with the eight names in it), however each time I restart the application it gives me the same error.  I have removed and reinstalled the application numerous times, to no avail.  I'm thinking it may have something to do with the files that are left behind when I uninstall (I'm doing a "sudo apt-get remove wicd" each time), but there several directories and files that are not removed each time.  Do you know how I could remove those, and possibly start with a completely fresh install?

Thanks!
Mike

---

### Post by oldsmobile_mike on 2008-01-27
Okay, I was able to get it working again.  I uninstalled the app, and this time was also able to remove all the files left behind after the uninstall by dragging the contents of /opt/wicd into the trashcan (just pressing the delete key didn't work, and I wasn't able to delete the files via command line, either - it said I didn't have permission, even though I tried chmod'ing them to give myself permission).  But by removing all of the files left behind and performing the install again, the application is now working.  It must've been one of these files left behind that was somehow mucking up the app.  I dunno.  In any case, thanks again!   :-D

---

### Post by imdano on 2008-01-27
Does the network you were trying to connect to use WEP?  Try opening up /opt/wicd/data/wireless-settings.conf, find the wireless network you were trying to connect to and manually change the enctype line from
enctype=wep
to
enctype=wep-hex
Restart the daemon/tray and see if it works then.

---

