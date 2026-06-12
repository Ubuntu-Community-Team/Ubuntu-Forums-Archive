---
title: "So closet yet so far (Cisco VPN wireless problems)"
date: 2007-02-01
forum: Networking &amp; Wireless
---

### Post by TrueXtremeIcon on 2007-02-01
Well...over the course of the day I've managed to get Ubuntu installed on this laptop (first time user). After some work I was able to find drivers for my wireless card. After some more work I was able to get the cisco vpn client downloaded, extracted, and even installed (thanks to some of the other helpful posts on this forum). 

All that's left is actually connecting...

I copied the two .pcf files from the windows version of the vpn client that my university furnishes and placed them in the folder (one for split vpn and one for wireless). I give the following

```

sudo vpnclient connect sample user marshall\(username) pwd (password)

```

And the very first thing it asks for is the GroupPwd....even though in the pcf file it is left blank and right below it is enc_GroupPwd=(hash)

I've done everything from leaving it blank to trying to input my own user account's password, but regardless of what I enter I end up with:

```

Initializing the VPN connection.
Contacting the gateway at xxx.xxx.xxx.xxx
Secure VPN Connection terminated locally by the Client
Reason: Remote peer is no longer responding.
There are no new notification messages at this time

```

I'm pretty much out of all the ideas. I've tried making edits to the pcf file and just about anything else I could think of with no luck.

Any help would be greatly appreciated.

---

### Post by Coombabah on 2007-02-02
vpnc

Vpnc is so much easier to setup than going through the hassles of getting the cisco version to work.

Sometimes the version that Universities have for download is so out of date it won´t work
You can´t go to cisco and download the latest version either.

The alternative: Enable the universe repository and search for vpnc in synaptic.

try making a myconf.conf file with these values
IPSec gateway xxx.xxx.xxx.xxx
IPSec ID wireless_name_the Uni_uses
IPSec secret secret_the_Uni_uses
Xauth username  your_username
Xauth password ********* (this line is optional)

to start
sudo /usr/sbin/vpnc-connect /etc/vpnc/myconf.conf
to stop
sudo /usr/sbin/vpnc-disconnect

---

