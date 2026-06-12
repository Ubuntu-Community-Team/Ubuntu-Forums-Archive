---
title: "Speedtouch 330 Problems"
date: 2004-11-22
forum: Networking &amp; Wireless
---

### Post by deiniol on 2004-11-22
Hi,

I've got a Speedtouch 330 modem, which I've installed following the instructions on the Howto exactly. But, umm, I don't know what to do now.

After I'd completed the install nothing happened, and likewise nothing has happened since- no error messages, no dialog boxes, no reports that everything was successful, nothing. I'm not sure if it's connected or not and I'm even less sure on how to tell. I tried to go to a few websites using Mozilla but got "server not available". Is there any sort of diagnostic thing I can run in order to find out what's gone wrong? I'd really appreciate some help.

---

### Post by deiniol on 2004-11-23
No-one can help?

---

### Post by jdong on 2004-11-23
Start by issuing an *ifconfig*.

---

### Post by deiniol on 2004-11-24
[QUOTE=jdong]Start by issuing an *ifconfig*.[/QUOTE]

Sorry, I'm a complete newbie when it comes to Linux- what's an *ifconfig*?

---

### Post by deiniol on 2004-11-25
Well, I ran *ifconfig* and got this:

lo	Link encap:Local Loopback
	inet addr:127.0.0.1 Mask:225.0.0.0
	inet6 addr:  ::1/128  Scope:Host
	UP LOOPBACK RUNNING   MTU:16436  Metric:1
	RX packets:2449  errors:0 dropped:0 overruns:0 frame:0
	TX packets:2499  errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:0
	RX bytes:177710 (173.5 KiB) TX bytes:177710 (173.5 KiB)


What on earth does that mean?

---

### Post by darrell on 2004-11-25
[QUOTE=deiniol]Well, I ran *ifconfig* and got this:

lo	Link encap:Local Loopback
	inet addr:127.0.0.1 Mask:225.0.0.0
	inet6 addr:  ::1/128  Scope:Host
	UP LOOPBACK RUNNING   MTU:16436  Metric:1
	RX packets:2449  errors:0 dropped:0 overruns:0 frame:0
	TX packets:2499  errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:0
	RX bytes:177710 (173.5 KiB) TX bytes:177710 (173.5 KiB)


What on earth does that mean?[/QUOTE]
 which howto were you following?

---

### Post by deiniol on 2004-11-26
[QUOTE=darrell]which howto were you following?[/QUOTE]

[This one]("http://www.ubuntulinux.org/wiki/UKSpeedtouchDSLHowTo/view?searchterm=speedtouch%20330")- the one on the ubuntu wiki.

---

### Post by darrell on 2004-11-26
[QUOTE=deiniol][This one]("http://www.ubuntulinux.org/wiki/UKSpeedtouchDSLHowTo/view?searchterm=speedtouch%20330")- the one on the ubuntu wiki.[/QUOTE]
 thanks, thought it might be, but there are a few speedtouch howtos floating about the web...

Unplug your modem, then type *tail -f /var/log/messages* in a terminal. this will show an updating display of the last few messges in the log file. (ctrl-c gets you back out to a prompt)

Plug in your modem. The first thing which should happen is the firmware load sequence which is shown by lights flashing on the modem. When the lights become steady (should take a minute or so) check the log screen. you should see messages about the adsl line coming up, the authentication process, and the assignment of ip/dns addresses. 

post the log messages back here, so we can see how far it goes. Note that if the modem just comes on with steady lights, and no flashing sequence, the firmware is not loading. Mention this as well when you post. (I assume that the speedtouch 330 is the same in this respect as my old speedtouch usb)

darrell

---

### Post by deiniol on 2004-11-27
The log gives this:

---
Nov 27 16:32:29 localhost kernel: usb 1-1: new full speed USB device using address 2
Nov 27 16:32:30 localhost kernel: usb 1-1: new full speed USB device using address 3
Nov 27 16:32:32 localhost usb.agent[4510]:      speedtch: loaded successfully
Nov 27 16:32:32 localhost usb.agent[4509]:      speedtch: already loaded
Nov 27 16:32:32 localhost usb.agent[4533]:      speedtch: loaded successfully
Nov 27 16:32:32 localhost kernel: usbcore: registered new driver speedtch
Nov 27 16:32:33 localhost usb.agent[4510]:      speedtouch: loaded successfully
Nov 27 16:32:33 localhost usb.agent[4533]:      speedtouch: loaded successfully
Nov 27 16:32:33 localhost usb.agent[4509]:      speedtouch: loaded successfully
Nov 27 16:32:33 localhost kernel: CSLIP: code copyright 1989 Regents of the University of California
Nov 27 16:32:33 localhost kernel: ppp_generic: Unknown symbol slhc_toss
Nov 27 16:32:33 localhost kernel: ppp_generic: Unknown symbol slhc_compress
Nov 27 16:32:33 localhost kernel: ppp_generic: Unknown symbol slhc_free
Nov 27 16:32:33 localhost kernel: ppp_generic: Unknown symbol slhc_uncompress
Nov 27 16:32:33 localhost kernel: ppp_generic: Unknown symbol slhc_remember
Nov 27 16:32:33 localhost kernel: ppp_generic: Unknown symbol slhc_init
Nov 27 16:32:33 localhost kernel: PPP generic driver version 2.4.2
Nov 27 16:32:33 localhost modem_run[4674]: modem_run version 1.3.1 started by root uid 0
Nov 27 16:32:33 localhost modem_run[4675]: modem_run version 1.3.1 started by root uid 0
Nov 27 16:32:33 localhost modem_run[4680]: modem_run version 1.3.1 started by root uid 0
Nov 27 16:32:35 localhost kernel: usb 1-1: bulk timeout on ep5in
Nov 27 16:32:35 localhost kernel: usb 1-1: usbfs: USBDEVFS_BULK failed ep 0x85 len 512 ret -110
Nov 27 16:33:09 localhost modem_run[4674]: ADSL synchronization has been obtained
Nov 27 16:33:09 localhost modem_run[4674]: ADSL line is up (576 kbit/s down | 288 kbit/s up)
---

Which rather implies to my untrained eyes that it is actually connected to the internet, but Mozilla and everything else which uses the internet seems to disagree. Do I have to use some sort of login sequence or similar in order to connect?

I think the firmware's loaded as the modem goes through its whole flashy lights thing as it used to under Windows.

---

### Post by darrell on 2004-11-27
[QUOTE=deiniol]The log gives this:

---
Nov 27 16:32:29 localhost kernel: usb 1-1: new full speed USB device using address 2
Nov 27 16:32:30 localhost kernel: usb 1-1: new full speed USB device using address 3
Nov 27 16:32:32 localhost usb.agent[4510]:      speedtch: loaded successfully
Nov 27 16:32:32 localhost usb.agent[4509]:      speedtch: already loaded
Nov 27 16:32:32 localhost usb.agent[4533]:      speedtch: loaded successfully
Nov 27 16:32:32 localhost kernel: usbcore: registered new driver speedtch
Nov 27 16:32:33 localhost usb.agent[4510]:      speedtouch: loaded successfully
Nov 27 16:32:33 localhost usb.agent[4533]:      speedtouch: loaded successfully
Nov 27 16:32:33 localhost usb.agent[4509]:      speedtouch: loaded successfully
Nov 27 16:32:33 localhost kernel: CSLIP: code copyright 1989 Regents of the University of California
Nov 27 16:32:33 localhost kernel: ppp_generic: Unknown symbol slhc_toss
Nov 27 16:32:33 localhost kernel: ppp_generic: Unknown symbol slhc_compress
Nov 27 16:32:33 localhost kernel: ppp_generic: Unknown symbol slhc_free
Nov 27 16:32:33 localhost kernel: ppp_generic: Unknown symbol slhc_uncompress
Nov 27 16:32:33 localhost kernel: ppp_generic: Unknown symbol slhc_remember
Nov 27 16:32:33 localhost kernel: ppp_generic: Unknown symbol slhc_init
Nov 27 16:32:33 localhost kernel: PPP generic driver version 2.4.2
Nov 27 16:32:33 localhost modem_run[4674]: modem_run version 1.3.1 started by root uid 0
Nov 27 16:32:33 localhost modem_run[4675]: modem_run version 1.3.1 started by root uid 0
Nov 27 16:32:33 localhost modem_run[4680]: modem_run version 1.3.1 started by root uid 0
Nov 27 16:32:35 localhost kernel: usb 1-1: bulk timeout on ep5in
Nov 27 16:32:35 localhost kernel: usb 1-1: usbfs: USBDEVFS_BULK failed ep 0x85 len 512 ret -110
Nov 27 16:33:09 localhost modem_run[4674]: ADSL synchronization has been obtained
Nov 27 16:33:09 localhost modem_run[4674]: ADSL line is up (576 kbit/s down | 288 kbit/s up)
---

Which rather implies to my untrained eyes that it is actually connected to the internet, but Mozilla and everything else which uses the internet seems to disagree. Do I have to use some sort of login sequence or similar in order to connect?

I think the firmware's loaded as the modem goes through its whole flashy lights thing as it used to under Windows.[/QUOTE]
 as you say, it looks like the firmware is loading and the line is going up. What does not seem to be happening is any authentication with your isp.

if you were following the ubuntu howto, you should have a file called */etc/ppp/peers/dsl-provider* - please confirm this, and that it contains your valid isp username.

ensure that the files */etc/ppp/pap-secrets* and */etc/ppp/chap-secrets* both contain the line:

yourispusername * yourisppassword *

including the *'s

ensure that in the file */etc/hotplug/usb/speedtouch*:

there is a line which says *PPPD_PEER="dsl-provider"* - this needs to match the name of the file you created in /etc/ppp/peers - I have named mine after my isp, but dsl-provider is fine if that's what you called it.

once you have all the above in place, unplug the modem,  issue the command *sudo killall pppd* (just to make sure any old pppd process is removed), do the *tail -f /var/log/messages* and plug the modem in again. If all goes well, you should see the messages you posted above, plus something like the following:

Nov 27 19:26:45 localhost pppd[10536]: Plugin pppoatm.so loaded.
Nov 27 19:26:45 localhost pppd[10536]: PPPoATM plugin_init
Nov 27 19:26:45 localhost pppd[10536]: PPPoATM setdevname - remove unwanted options
Nov 27 19:26:45 localhost pppd[10536]: PPPoATM setdevname_pppoatm - SUCCESS:0.38Nov 27 19:26:45 localhost pppd[10537]: pppd 2.4.2 started by root, uid 0
Nov 27 19:26:45 localhost pppd[10537]: Using interface ppp0
Nov 27 19:26:45 localhost pppd[10537]: Connect: ppp0 <--> 0.38
Nov 27 19:26:52 localhost pppd[10537]: CHAP authentication succeeded: CHAP authentication success, unit 3066
Nov 27 19:26:52 localhost pppd[10537]: local  IP address xxx.xxx.xxx.xxx
Nov 27 19:26:52 localhost pppd[10537]: remote IP address xxx.xxx.xxx.xxx
Nov 27 19:26:52 localhost pppd[10537]: primary   DNS address xxx.xxx.xxx.xxx
Nov 27 19:26:52 localhost pppd[10537]: secondary DNS address xxx.xxx.xxx.xxx

If it doesn't get this far, post what you have, and we'll take it from there. I'm a little worried about the error messages you are getting from the ppp_generic module, but let's leave that for now, just in case it's not important!

darrell

---

### Post by deiniol on 2004-11-27
[QUOTE=darrell]If it doesn't get this far, post what you have, and we'll take it from there. I'm a little worried about the error messages you are getting from the ppp_generic module, but let's leave that for now, just in case it's not important!
[/QUOTE]

I checked what you told me to- it turned out that the *speedtouch* file didn't have *PPPD_PEER="dsl-provider"* in it.  Everything else was fine. I plugged in the modem and got exactly the same log, save that the bit which goes:

[i]Nov 27 16:32:33 localhost kernel: ppp_generic: Unknown symbol slhc_toss
Nov 27 16:32:33 localhost kernel: ppp_generic: Unknown symbol slhc_compress
Nov 27 16:32:33 localhost kernel: ppp_generic: Unknown symbol slhc_free
Nov 27 16:32:33 localhost kernel: ppp_generic: Unknown symbol slhc_uncompress
Nov 27 16:32:33 localhost kernel: ppp_generic: Unknown symbol slhc_remember
Nov 27 16:32:33 localhost kernel: ppp_generic: Unknown symbol slhc_init[/i] 

wasn't there. However, nothing happened after the *localhost modem_run[4674]: ADSL line is up (576 kbit/s down | 288 kbit/s up)* bit.

---

### Post by darrell on 2004-11-29
[QUOTE=deiniol]I checked what you told me to- it turned out that the *speedtouch* file didn't have *PPPD_PEER="dsl-provider"* in it.  Everything else was fine. I plugged in the modem and got exactly the same log, save that the bit which goes:

[i]Nov 27 16:32:33 localhost kernel: ppp_generic: Unknown symbol slhc_toss
Nov 27 16:32:33 localhost kernel: ppp_generic: Unknown symbol slhc_compress
Nov 27 16:32:33 localhost kernel: ppp_generic: Unknown symbol slhc_free
Nov 27 16:32:33 localhost kernel: ppp_generic: Unknown symbol slhc_uncompress
Nov 27 16:32:33 localhost kernel: ppp_generic: Unknown symbol slhc_remember
Nov 27 16:32:33 localhost kernel: ppp_generic: Unknown symbol slhc_init[/i] 

wasn't there. However, nothing happened after the *localhost modem_run[4674]: ADSL line is up (576 kbit/s down | 288 kbit/s up)* bit.[/QUOTE]
 I would check that the pppoatm module is loaded:

the command lsmod |grep pppoatm

should show it if it is. if it is not, do

modprobe pppoatm, then try again, unplugging and plugging in the modem. If this still doesn't work, you could try some slightly different speedtouch packages: see my post in another thread regarding the original speedtouch usb modem: [http://www.ubuntuforums.org/showthread.php?p=22918#post22918](http://www.ubuntuforums.org/showthread.php?p=22918#post22918)

if the pppoatm module was not loaded, and loading it works, then add the line pppoatm at the bottom of the file /etc/modules. This will make sure it is loaded on boot.

---

### Post by deiniol on 2004-11-29
Well, I tried what you said and nothing happened. Then I followed the instructions in the *alcatel usb speedtouch* thread and it got a _lot_ further than it has before. Quoting the log:

---
Nov 29 21:54:33 localhost kernel: usb 1-1: new full speed USB device using address 2
Nov 29 21:54:34 localhost kernel: usb 1-1: new full speed USB device using address 3
Nov 29 21:54:36 localhost usb.agent[4529]:      speedtch: loaded successfully
Nov 29 21:54:36 localhost usb.agent[4548]:      speedtch: already loaded
Nov 29 21:54:36 localhost usb.agent[4567]:      speedtch: already loaded
Nov 29 21:54:36 localhost kernel: usbcore: registered new driver speedtch
Nov 29 21:54:37 localhost usb.agent[4529]:      speedtouch: loaded successfully
Nov 29 21:54:37 localhost usb.agent[4548]:      speedtouch: loaded successfully
Nov 29 21:54:37 localhost usb.agent[4567]:      speedtouch: loaded successfully
Nov 29 21:54:37 localhost modem_run[4685]: modem_run version 1.3.1 started by root uid 0
Nov 29 21:54:37 localhost modem_run[4686]: modem_run version 1.3.1 started by root uid 0
Nov 29 21:54:37 localhost modem_run[4691]: modem_run version 1.3.1 started by root uid 0
Nov 29 21:54:39 localhost kernel: usb 1-1: bulk timeout on ep5in
Nov 29 21:54:39 localhost kernel: usb 1-1: usbfs: USBDEVFS_BULK failed ep 0x85 len 512 ret -110
Nov 29 21:55:13 localhost modem_run[4685]: ADSL synchronization has been obtained
Nov 29 21:55:13 localhost modem_run[4685]: ADSL line is up (576 kbit/s down | 288 kbit/s up)
Nov 29 21:55:22 localhost pppd[4706]: Plugin pppoatm.so loaded.
Nov 29 21:55:22 localhost pppd[4706]: PPPoATM plugin_init
Nov 29 21:55:22 localhost pppd[4706]: PPPoATM setdevname - remove unwanted options
Nov 29 21:55:22 localhost pppd[4706]: PPPoATM setdevname_pppoatm - SUCCESS:0.35
Nov 29 21:55:22 localhost pppd[4709]: pppd 2.4.2 started by root, uid 0
Nov 29 21:55:22 localhost pppd[4709]: Using interface ppp0
Nov 29 21:55:22 localhost pppd[4709]: Connect: ppp0 <--> 0.35
Nov 29 21:55:52 localhost pppd[4709]: LCP: timeout sending Config-Requests
Nov 29 21:55:52 localhost pppd[4709]: Connection terminated.
Nov 29 21:56:22 localhost pppd[4709]: Using interface ppp0
Nov 29 21:56:22 localhost pppd[4709]: Connect: ppp0 <--> 0.35
Nov 29 21:56:52 localhost pppd[4709]: LCP: timeout sending Config-Requests
Nov 29 21:56:52 localhost pppd[4709]: Connection terminated.
---

Unfortunately this is where it just stops. It tries about ten times but each time it says "LCP: timeout sending Config-Requests". What does that mean?

---

### Post by deiniol on 2004-12-04
I've just spent the last hour googling for information on "LCP: timeout sending Config-Requests", which is what my modem's still throwing at me when I try to connect. The FAQ [here](http://cvs.sourceforge.net/viewcvs.py/*checkout*/speedtouch/speedtouch/doc-linux/FAQ?rev=HEAD)  gives three possible options as to why this keeps coming up:

[quote="The FAQ"]
- Your ISP does not respond to your config requests. This cannot be solved
    by the driver :-)
  - You may have done a mistake in user/password between the adsl peer file
    and the chap/pap-secrets file.
  - Sometimes pppoa3 fails to remove its pid/lock file in /var/run/
    Then check  your daemon.log, and if you see lines where pppoa3 is waiting
    like this :

    >Mar 24 13:56:12 leloo pppoa3[25981]: Sending the kill signal to 1381 and
    >waiting
      but this line is missing :
    >Mar 24 13:56:12 leloo pppoa3[25981]: Ok, the previous instance seems to
    >quit

     To solve the problem, remove the pppoa3 pid file in /var/run and try
     again[/quote]

I rang my ISP and checked the spelling of my username and password and they're correct, so it's not option 2. The ISP responds to my config requests when I use windows on my partner's computer, so I don't think it's option 1. As far as I can tell there isn't a pid/lock file in /var/run/ and I'm not sure on how to check my daemon.log, so I *think* it's not option 3. Which still leaves me totally at sea as to why "LCP: timeout sending Config-Requests" comes up.

Please, does anyone have any idea on this. I hate it when technology gets the better of me and this modem problem is slowly eating away at my sanity. It's got so bad I've even contemplated going back to XP (which I really don't want to do).

Cheers.

---

### Post by jimbor on 2004-12-04
[QUOTE=deiniol]I've just spent the last hour googling for information on "LCP: timeout sending Config-Requests", which is what my modem's still throwing at me when I try to connect. The FAQ [here](http://cvs.sourceforge.net/viewcvs.py/*checkout*/speedtouch/speedtouch/doc-linux/FAQ?rev=HEAD)  gives three possible options as to why this keeps coming up:



I rang my ISP and checked the spelling of my username and password and they're correct, so it's not option 2. The ISP responds to my config requests when I use windows on my partner's computer, so I don't think it's option 1. As far as I can tell there isn't a pid/lock file in /var/run/ and I'm not sure on how to check my daemon.log, so I *think* it's not option 3. Which still leaves me totally at sea as to why "LCP: timeout sending Config-Requests" comes up.

Please, does anyone have any idea on this. I hate it when technology gets the better of me and this modem problem is slowly eating away at my sanity. It's got so bad I've even contemplated going back to XP (which I really don't want to do).

Cheers.[/QUOTE]
 Just getting mine to work so hitting the same problems I notice the vpi vci are for polish/dutch isp's and if yours is dutch there is another common pair shown when speedtouchconf is run 
8 48

---

### Post by deiniol on 2004-12-05
[QUOTE=jimbor]Just getting mine to work so hitting the same problems I notice the vpi vci are for polish/dutch isp's and if yours is dutch there is another common pair shown when speedtouchconf is run 
8 48[/QUOTE]

That could be the problem- I'm in the UK.

---

