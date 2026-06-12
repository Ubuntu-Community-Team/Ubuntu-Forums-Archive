---
title: "Wireless Issues - WEP keys"
date: 2006-08-10
forum: Networking &amp; Wireless
---

### Post by johns996 on 2006-08-10
I just put Ubuntu on my new IBM/Lenovo ThinkPad R60 and everything is working great.  The only problem I'm having is when I try to connect to my home network.  If I remove all of the security, I can connect without a problem but when I turn it back on I can't connect.

I'm using a Linksys WRT54G (v. 5 with standard firmware) that does not broadcast the SSID, has MAC filtering turned on, and uses a 128 bit WEP key.  The WEP key in my router is identified as Key 3.  (I'm not sure if the broadcast channel means anything, but if it does I'm using channel 9 (2.452 GHz).)

I've downloaded various GUI tools to try and set up the networking but nothing seemed to work.  None of the tools I've used had any options for specifying what WEP key was used (*example key 3*) and I'm assuming this is where I'm encountering the problem.   Ideas?

**Note**: I have added the MAC address of the wireless card in my laptop to the router so this isn't the problem.  I'm sure of this because I am dual booting into Windows and can connect without problems.

---

### Post by meng on 2006-08-10
Are you using GNOME? The Networking config enables specification of WEP keys.

---

### Post by jplinux on 2006-08-11
Under SuSE 10.1, I use iwconfig and iwpriv to connect using WPA inside a small script, because knetworkmanager seems to be buggy.

---

### Post by johns996 on 2006-08-11
I am using GNOME, basicly a standard install of of Ubuntu LTS.  Where do I find the config GUI?  Under the system> administration> networking menu?

---

### Post by meng on 2006-08-11
Yes, exactly, configure the wireless interface from there.

---

### Post by johns996 on 2006-08-12
Well I got something to work.  According to this post [http://ubuntuforums.org/showthread.php?t=195694](http://ubuntuforums.org/showthread.php?t=195694), which links to another post, the network manager only allows you to set WEP key #1.  So after reconfiguring my router to use key 1, I connected without a problem.

Hopefully this post helps someone else get through this problem quicker than I did.  Regardless, I now have another reason to completly remove Win from my laptop.  Thanks Ubuntu!:p

---

### Post by mlavikai on 2007-01-08
Hi.

I found one solution for using WEP key with KNetworkmanager. In my AccessPoint WEP key is in HEX rather than PASSPHRASE. However, KNetworkmanager seems to constantly try to use only PASSPHRASE when connecting.

Solution. First to connect to your WLAN. When it fails, close KNetworkmanager. Open file:
~/.kde/share/config/knetworkmanagerrc

Content of your entry looks something like: 

```

[Network_LKrkKhMhEtYJXq07]
ESSID=xxxxx
Encryption=WEP
HardwareAddresses=,??:??:??...
Timestamp=2007,1,8,14,49,44
Trusted=true
WEPMethod=SharedKey
WEPType=PASSPHRASE
```

In that file replace option 'WEPType' value to 'HEX' or 'ASCII', depending on you configuration. Also 'WEPMethod' can be something else than 'SharedKey'. Try to change that also.

Save, and then restart KNetworkmanager and possibly ndiswrapper and try to connect.

Hopefully that helps.

---

### Post by chili555 on 2007-01-08
Shared Key, which I recommend, is tricky and keeps quite a few of us stumped until we figure out its significance.

For the best security under WEP, make sure your router is set to Shared Key. You can then set up  /etc/network/interface similar to this:

auto wlan0
iface wlan0 inet static
wireless-essid GBR1
wireless-key xxxc7f280e2xxx8ba1154e4xxx restricted
address 192.168.1.106
netmask 255.255.255.0
gateway 192.168.1.1

The word restricted corresponds to Shared Key in your router. Unless both are set, you will bang your head on the brick wall all day long. ](*,)

---

