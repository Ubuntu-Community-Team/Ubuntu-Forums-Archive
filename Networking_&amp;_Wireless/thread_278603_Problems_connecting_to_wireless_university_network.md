---
title: "Problems connecting to wireless university network (PEAP,WEP)"
date: 2006-10-16
forum: Networking &amp; Wireless
---

### Post by ubuntu_demon on 2006-10-16
Hi,

I just bought a new laptop (my first) :
[http://ubuntudemon.wordpress.com/2006/10/15/i-bought-my-new-laptop/](http://ubuntudemon.wordpress.com/2006/10/15/i-bought-my-new-laptop/)
[http://ubuntuforums.org/showthread.php?p=1620371](http://ubuntuforums.org/showthread.php?p=1620371)

Wireless works perfectly (ipw3945) except for the wireless network of my university.
[B]
I'm using Edgy.[/B] But I don't think this is a bug so I'm posting here.

The network uses a 128 bit ascii WEP key :
"12345678901234567890123456"

and also PEAP authentication using my university account.

Some other things I know :
-MSCHAPV2
-802.11x authentication

I haven't gotten network-manager-gnome to work with it. Maybe network-manager-gnome only supports PEAP/WPA and not PEAP/WEP ? I tried just clicking on the network and also connecting to it as WPA-enterprise.

I also tried playing with interfaces. But I don't know yet how to combine PEAP and WEP. (That's why the WEP stuff is missing)

```

auto eth1
iface eth1 inet dhcp
  wpa-driver wext
  wpa-ssid MAASnet
  wpa-key-mgmt IEEE8021X
  wpa-eap PEAP
  wpa-phase2 auth=MSCHAPV2
  wpa-identity *******
  wpa-password *******

```

I'm still trying stuff ofcourse :). But maybe someone has an idea ?

---

### Post by randomnumber on 2006-10-17
I think that this setup file you have shown is not needed. 
I think that if you use the program network-manager instead of the default application installed in Ubuntu you can follow my instructions from the post in [http://ubuntuforums.org/showthread.php?t=249654](http://ubuntuforums.org/showthread.php?t=249654) . network-manager uses the wpa_supplicant application. 


network-manager can be installed by# sudo apt-get install network-manager
 [http://ubuntuguide.org/wiki/Dapper#How_to_Configure_Ubuntu.2FKubuntu_with_WPA_using_Network-Manager](http://ubuntuguide.org/wiki/Dapper#How_to_Configure_Ubuntu.2FKubuntu_with_WPA_using_Network-Manager) 

Be sure to change  ###6.change “Key Type:” to “Dynamic WEP”###
This is what I think I was originally having problems with and I now know that it will not work with orig. setting.

This makes it so you do not have to keep your id/password in a file which is a security risk. 

Please note that you have to disable the connection of the network manager that is installed by default. The hardware is not able to be used by network-manager If you do not do this.

I hope this helps. If your network is different you will have to adjust the settings. I plan to do more testing and I will remove any file settings to see if it has an effect. 

Please inform me of your progress. When I am confident with a way to get my  school's wireless network setup with linux I plan to submit a how to document for the school and I imagine that your network is the same.

My linux install can now connect everytime I have tried.

---

### Post by randomnumber on 2006-10-17
To disable network connections with orig manager:

System -> Adminstration -> Networking

select the network adaptor to use in the wireless connection

click properties button

DEselect "enable this connection"

select "OK"

================================================

network-manager should now be able to see the hardware.

try a reboot if it does not.

================================================

---

### Post by ubuntu_demon on 2006-10-18
> **randomnumber said:**
> I think that this setup file you have shown is not needed. 
I think that if you use the program network-manager instead of the default application installed in Ubuntu you can follow my instructions from the post in [http://ubuntuforums.org/showthread.php?t=249654](http://ubuntuforums.org/showthread.php?t=249654) . network-manager uses the wpa_supplicant application. 


network-manager can be installed by# sudo apt-get install network-manager


I already triead a couple of things with network-manager. I'm quite sure I tried it already.

IMHO my university's wireless network currently isn't supported by network-manager :(

I will play around more with network-manager to be sure.

> **randomnumber said:**
>  [http://ubuntuguide.org/wiki/Dapper#How_to_Configure_Ubuntu.2FKubuntu_with_WPA_using_Network-Manager](http://ubuntuguide.org/wiki/Dapper#How_to_Configure_Ubuntu.2FKubuntu_with_WPA_using_Network-Manager) 

Be sure to change  ###6.change &#8220;Key Type:&#8221; to &#8220;Dynamic WEP&#8221;###
This is what I think I was originally having problems with and I now know that it will not work with orig. setting.

This makes it so you do not have to keep your id/password in a file which is a security risk. 


There are two levels of authentication on my university's network :
- 128 bit ascii WEP key that has to be 26 numbers (it doesn't matter which numbers).
- PEAP MSCHAPV2 with username and password

(I use this password only on for my university account.)

> **randomnumber said:**
> 
Please note that you have to disable the connection of the network manager that is installed by default. The hardware is not able to be used by network-manager If you do not do this.


network-manager itself works fine. IMHO it's a great application. I have tried it on open networks.

> **randomnumber said:**
> 
I hope this helps. If your network is different you will have to adjust the settings. I plan to do more testing and I will remove any file settings to see if it has an effect. 

Please inform me of your progress. When I am confident with a way to get my  school's wireless network setup with linux I plan to submit a how to document for the school and I imagine that your network is the same.

My linux install can now connect everytime I have tried.

Thanks for your help. I will keep everyone updated on my progress.

I will write also HOWTO when I have figured this out. I'm not going to stop complaining to the university until they link to my HOWTO or provide the information themselves.

There are only MAC and Windows XP wireless guides available. And they don't provide very much information for I do not know what happens behind the GUI.

I want my university to at least provide me with some detailed information about the network  without having to "reverse engineer" a  windows guide.

So in practice they currently force all students to work on their windows machines with shared administrator accounts :(. This is very unsecure.

---

### Post by ubuntu_demon on 2006-10-18
Here's the windows guide to the wireless network :
[http://www.unimaas.nl/default.asp?template=portal.htm&id=46DB2THM760NB31KI30W&taal=en](http://www.unimaas.nl/default.asp?template=portal.htm&id=46DB2THM760NB31KI30W&taal=en)

---

### Post by Kitty on 2006-10-18
Without NetworkManager, I managed to connect with this sort of security.

See [http://www.ubuntuforums.org/showthread.php?t=36761](http://www.ubuntuforums.org/showthread.php?t=36761)

My HowTo, only in French: [http://wifi.utt.fr/connectlinux.htm](http://wifi.utt.fr/connectlinux.htm)

---

### Post by ubuntu_demon on 2006-10-18
Thanks. Maybe I can find some clues in your xsupplicant.conf and your script.

Does anyone know whether it's better to use wpasupplicant or xsupplicant for this particular network ?

wpasupplicant seems to be easier to use.

**(I'm using Edgy)**

---

### Post by ubuntu_demon on 2006-10-18
I now know for sure that wpasupplicant is the best way to tackle this. See my blog : [http://ubuntudemon.wordpress.com/2006/10/18/problems-connecting-to-wireless-university-network-peapwep](http://ubuntudemon.wordpress.com/2006/10/18/problems-connecting-to-wireless-university-network-peapwep)

---

### Post by ubuntu_demon on 2006-10-18
This is the suggestion by Dennis. Thanks Dennis!

I'm going to try it out today and I will keep you updated.

interfaces :
```

iface eth1 inet dhcp
wpa-driver wext #you might need to replace this
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

```

wpa_supplicant.conf :
```

network={
ssid="MAASnet"
key_mgmt=NONE
auth_alg=OPEN
wep_key0=12345678901234567890123456
eap=PEAP
phase2="auth=MSCHAPV2"
identity="username"
password="password"
}

```

---

### Post by no_mayl on 2006-10-18
i'm using xubuntu, and had to split the key (1234-5678-9012-3456-7890-1234-56) in the network manager. Looking into /etc/network/interface this is what the manager generated:
...
```
auto wlan0
iface wlan0 inet dhcp
wireless-essid blabla
wireless-key restricted 3c23-5423-d133-34af-5871-adf1-27

```

this might not help as u r using wpa supplicant.

---

### Post by randomnumber on 2006-10-18
I am sorry to hear that you are still having problems getting conneteced to your network. You say that your network is different. I included a link to a how to for xp and mac so you can compare. You can make note the differences. 

[http://portal.knowledgebase.net/display/2n/articleDirect/index.asp?aid=133405&r=0.9166834](http://portal.knowledgebase.net/display/2n/articleDirect/index.asp?aid=133405&r=0.9166834)

Good Luck

You may make fun of me but it took me a few months to figure out my connection.

---

### Post by Fritti on 2006-10-19
Someone at the faculty where I work (university of Eindhoven) has written a guide to make it work with Ubuntu. I guess the only difference is the WEP-key bit, we do use 802.11x + PEAP + MSCHAPv2.

[http://www.win.tue.nl/~cgray/tue-wireless.html](http://www.win.tue.nl/~cgray/tue-wireless.html)

HTH

---

### Post by ubuntu_demon on 2006-10-19
Thanks for all your help guys.

I didn't succeed yet but I'm making progress.

$iwconfig eth1
> 
eth1      unassociated  ESSID:"MAASnet"  
          Mode:Managed  Frequency=nan kHz  Access Point: 00:14:A8:25:63:C0   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:48   Missed beacon:0


Some things I'm going to try :
- Maybe this gives a little bit more information :
$iwlist scanning 
$cat /proc/net/wireless
-*wep_key0="1234.."* vs *wep_key0=12345*
-*EAP=PEAP* vs no line
-*auth_alg=SHARED* vs *auth_alg=OPEN*
-wpa_supplicant in debugging mode with wext and ipw drivers :

$sudo wpa_supplicant -c/etc/wpa_supplicant/wpa_supplicant.conf -ieth1 -Dwext -d
$sudo wpa_supplicant -c/etc/wpa_supplicant/wpa_supplicant.conf -ieth1 -Dipw -d


I attached a screenshot of kismet's "i". It has some information about the network/AP.

---

### Post by ubuntu_demon on 2006-10-19
succes!!!!!!! :D :D

network ={
ssid=&#8221;MAASnet&#8221;
key_mgmt=IEEE8021X
wep_key0=12345&#8230;
phase2=&#8221;auth=MSCHAPV2&#8243;
identity=&#8221;***&#8221;
password=&#8221;***&#8221;
}

I started with Dennis' configuration. I adapted it with help of /usr/share/doc/wpasupplicant and the debugging mode of wpa_supplicant :
$sudo wpa_supplicant -c/etc/wpa_supplicant/wpa_supplicant.conf -ieth1 -D*drivername* -d

Thanks for all your help everyone!

---

### Post by randomnumber on 2006-10-21
Congrads

Are you going to spreed your knowledge to you fellow students in addition to this forum? 

You can brag about it if you do.

I am still hoping to build a method that works for our school but I was recently contacted by someone that said they could not get connected with my directions. I hope to contact them and solve the problem.

again, congratulations

---

### Post by ubuntu_demon on 2006-10-21
> **randomnumber said:**
> Congrads

Are you going to spreed your knowledge to you fellow students in addition to this forum? 

You can brag about it if you do.

I am still hoping to build a method that works for our school but I was recently contacted by someone that said they could not get connected with my directions. I hope to contact them and solve the problem.

again, congratulations
I'm going to create a page on the wiki. And I'm going to give the information to the system administrators.

---

### Post by daller on 2006-11-28
I study at Aarhus School of Business.

I received at guide for Windows, but that didn't help! :D

Well, it basically tells me what to do:

SSID: asbstudent
Network authentication: Open
Data encryption: WEP
"The key is provided for me automatically"
EAP type: PEAP
Authentication method: Secured password
Validate server certificate: OFF
Enable fast reconnect: ON
Username: username
Password: password
Logon domain: ASB

Any ideas?

---

### Post by cognitive on 2007-06-22
Hey I am also at UM could you provide further details on how to get it to work?

Regards

---

### Post by Joshua Swink on 2007-08-03
I managed to connect to the UC Merced wireless network with the following setup. It uses PEAP and MSCHAPv2.

In /etc/network/interfaces:

[INDENT]```
iface eth1 inet dhcp
wpa-conf /etc/wpa_supplicant/ucmerced.conf
wireless-essid UCMerced
```[/INDENT]

I created /etc/wpa_supplicant/ucmerced.conf:

[INDENT]```
ctrl_interface=/var/run/wpa_supplicant
ap_scan=2
fast_reauth=1

network={
   ssid="UCMerced"
   key_mgmt=IEEE8021X
   eap=PEAP
   phase2="auth=MSCHAPV2"
   identity="XXXXXXXX"
   password="XXXXXXXX"
}
```[/INDENT]

Previous posts in this thread came very close to this, but I found that "ap_scan=2" is also necessary.

wpa_supplicant is VERY PICKY about quotes in its configuration files! Leaving them off certain settings will result in failure.

You always have to do "sudo ifup eth1" to connect.

---

### Post by band-aid on 2007-08-27
I'm trying to get this working as well.  This is what I get from the windows instructions that are given to the students. 
WEP
Uses IEEE 802.1x authentication 
EAP(PEAP)
"Authenticate as a computer when computer information is available"
uncheck "validate server"
uncheck "Allow other networks users to control..."
uncheck "Allow other network users to connect..."
Enter your login information when the window pops up

Problem I have is that I never see the WEP key. I is set up in such a way (windows calls it "key is provided for me") that it is provided to me somehow. This seems rather insecure, but I don't have any say in it. Would I just leave out the key line in a wpa supplicant configuration file or would I do something like WEP: 0000000000000. Thanks for the help.

---

### Post by nunomiguelmota on 2007-08-27
I think that my university has the same kind of network  and I use network-manager to connect to that. Just try selecting WPA Enterprise and choosing the right options to connect

---

### Post by band-aid on 2007-08-27
but my school uses wep encryption, not wpa... or does that even matter. And it would appear that I have screwed up my knetworkmanager (kubuntu) because It won't start on boot nor when I click it in my menu. DCOPServer is asking for my password rather than knetwork manager now. AND my CD drive doesn't work. My entire install has gone to crap in the past two days lol. Right now I'd just like my knetworkmanager to work OR wpa_supplicant to work for my school network.

---

### Post by wirelessmonkey on 2007-08-28
802.1X w/ dynamic wep is no longer enterprise security, it's not even really usable for home connections.  You may want to mention that.    5000 packets makes me the Man In The Middle.

---

### Post by band-aid on 2007-08-28
802.1X w/ dynamic wep is no longer enterprise security, it's not even really usable for home connections. You may want to mention that. 5000 packets makes me the Man In The Middle.

I realize that WEP is horribly insecure, I've cracked my own key in as little as 6 minutes. But I do not have any say in what my college uses and need some help getting this abomination of a security plan to allow my laptop to connect.

---

### Post by cracker on 2008-01-07
> **band-aid said:**
> 802.1X w/ dynamic wep is no longer enterprise security, it's not even really usable for home connections. You may want to mention that. 5000 packets makes me the Man In The Middle.

I realize that WEP is horribly insecure, I've cracked my own key in as little as 6 minutes. But I do not have any say in what my college uses and need some help getting this abomination of a security plan to allow my laptop to connect.

I hate to resurrect an old thread, but I have this exact same problem. I have no control over it, or help from IT. Has anyone gotten this to work?

---

