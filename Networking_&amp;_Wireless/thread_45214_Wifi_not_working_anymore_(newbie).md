---
title: "Wifi not working anymore (newbie)"
date: 2005-06-29
forum: Networking &amp; Wireless
---

### Post by jbeaudet on 2005-06-29
Hi everyone,

When I installed Hoary on my thinkpad t41, I got the wifi working almost right away.  I used 128 bit encryption with a shared key.

For the last two weeks, it had not been working at all. However, when I boot to winxp, wifi does work.  I did an update not long before that but I am not sure this is relevant.

Thus, I tried every option on the router (Netgear MR814 v2) but the eth1 interface (wireless) is always _disconnected_  or unavailable.

Have any idea?  I it possible to reset everything and start all over again like if I had no connection configured?

Regards,

Jean  :)

---

### Post by ianpeters on 2005-06-29
[QUOTE=jbeaudet]Hi everyone,

When I installed Hoary on my thinkpad t41, I got the wifi working almost right away.  I used 128 bit encryption with a shared key.

For the last two weeks, it had not been working at all. However, when I boot to winxp, wifi does work.  I did an update not long before that but I am not sure this is relevant.

Thus, I tried every option on the router (Netgear MR814 v2) but the eth1 interface (wireless) is always _disconnected_  or unavailable.

Have any idea?  I it possible to reset everything and start all over again like if I had no connection configured?

Regard,

Jean  :)[/QUOTE]

I found this thread to be very helpful: [http://ubuntuforums.org/showthread.php?t=25683&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=25683&highlight=ndiswrapper)
Just follow the instructions.

---

### Post by jbeaudet on 2005-06-29
Thanks,

I just don't understand why you should use this ndiswrapper (which is a wrapper for the windows driver) when a linux driver exists and is actually used by ubuntu. 

ipw2100.sourceforge.net/

Hoary actually use version 1.0.2, even though 1.1 is out and tagged as stable. Maybe this is what I should get. 

Please not that my wifi card can detect available networks. However, it always remains unassociated. 

[FONT=Courier New]eth1 unassociated ESSID:"NETGEAR" Nickname:"ipw2100"
Mode:Managed Channel=0 Access Point: 00:00:00:00:00:00
Bit Rate=0kb/s Tx-Power:off
Retry:on RTS thr:off Fragment thr:off
Encryption key:off
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0[/FONT]

Regards,

--
Jean

---

### Post by spd106 on 2005-07-01
Hi, perhaps it has lost the encryption key. Sometimes the config files are overwritten and you lose the settings. Not sure what does this though.

Check the /etc/network/interfaces files for settings. It should display the information such as essid and encryption key. If not or if they are wrong you can set them with "sudo ifconfig" or the easier option is to use the network gui.

Once you set the encryption key from the command line it should associate with the AP automatically.
"sudo ifconfig eth1 key XXXXXXXXXXXXXXXXXXXXXXXXXX"

Hope this helps

---

