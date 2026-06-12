---
title: "Now Kismet does not work anymore"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by telovoyagarcar on 2007-02-22
What do they mean when they say ¨Linux is a stable system¨ ?

I was using kismet without problems the last couple of days and today is not working anymore.

I noticed that for some reason, the ¨source¨ line in the kismet.conf file changes by itself to the a wrong setting so i just edit the line and it works..

But now the **** does not start... i get this:

```
 Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (madwifi-ng): Enabling monitor mode for madwifi_ag source interface wifi0 channel 6...
NOTICE:  Created Madwifi-NG VAP kis
WARNING: wifi0 appears to be using Madwifi-NG.  Some versions of the Madwifi-NG drivers have problems in monitor mode, especially if non-monitor VAPs are active.  If you experience problems, be sure to try the latest versions of Madwifi-NG and remove other VAPs
Source 0 (madwifi-ng): Opening madwifi_ag source interface kis...
Source 1 (Atheros): Enabling monitor mode for madwifing_g source interface wifi0 channel 6...
WARNING: wifi0 appears to not accept the Madwifi-NG controls. Will attempt to configure it as a standard Madwifi-old interface. If you are using madwifi-ng, be sure to set the source interface to the wifiX control interface, NOT athX
FATAL: channel get ioctl failed 22:Invalid argument
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}

```

Where it says: ¨be sure to set the source interface to the wifiX control interface, NOT athX¨ is the place where i change ath0 to wifi0 so then it works.

but now i dont know what this means or why is happening, because i did not change anything in ubuntu since the last time i used kismet:

FATAL: channel get ioctl failed 22:Invalid argument
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}


Any ideas????:confused:

---

### Post by a_stanley on 2007-10-18
hello!

 I thought i was going nuts, i have the EXACT SAME PROBLEM. The only thing i've noticed that might bear some fruit is that kismet appears to first set up madwifi_b source (as mine is supposed to from the .conf) but then it tries to activate madwifing_g source after... I don't understand why.

I've been reading posts and some point to updating madwifi-ng to the newest cutting edge version (i'm not so familiar with linux that i'm sure i can do this without completely hosing my networking  so have thus far avoided the attempt)

I just don't see how kismet would work, perfectly, then not.. there should be a way to get it back into however it was setup before, right? I've tried restarting (some habits die hard) but that just got my normal wireless working again, disabled it in the network aplet, tried kismet, same error.

any thoughts on this problem would be greatly appreciated.

---

### Post by Oraclegol on 2007-10-18
um no expert but it seem's that you have kismet running to sources

Source 0 (madwifi-ng): Opening madwifi_ag source interface kis...
Source 1 (Atheros):

What's your config file say ?
my has
source=madwifi_ag,wifi0,AtherosAG

with the enable sources option below it commented out with a #
nope that helps

---

### Post by a_stanley on 2007-10-18
my source line: source=madwifing_b,wifi0,madwif

i got that from /etc/kismet/kismet.conf

i believe that is correct, it previously worked... but now i get:

acer@acer-laptop:~$ sudo kismet
Password:
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (madwifi): Enabling monitor mode for madwifing_b source interface wifi0 channel 6...
NOTICE:  Created Madwifi-NG VAP kis
WARNING: wifi0 appears to be using Madwifi-NG.  Some versions of the Madwifi-NG drivers have problems in monitor mode, especially if non-monitor VAPs are active.  If you experience problems, be sure to try the latest versions of Madwifi-NG and remove other VAPs
Source 0 (madwifi): Opening madwifing_b source interface kis...
Source 1 (Atheros): Enabling monitor mode for madwifing_g source interface wifi0 channel 6...
NOTICE:  Created Madwifi-NG VAP kis
WARNING: wifi0 appears to be using Madwifi-NG.  Some versions of the Madwifi-NG drivers have problems in monitor mode, especially if non-monitor VAPs are active.  If you experience problems, be sure to try the latest versions of Madwifi-NG and remove other VAPs
Source 1 (Atheros): Opening madwifing_g source interface kis...
Source 2 (Atheros): Enabling monitor mode for madwifing_g source interface wifi0 channel 6...
NOTICE:  Created Madwifi-NG VAP kis
WARNING: wifi0 appears to be using Madwifi-NG.  Some versions of the Madwifi-NG drivers have problems in monitor mode, especially if non-monitor VAPs are active.  If you experience problems, be sure to try the latest versions of Madwifi-NG and remove other VAPs
Source 2 (Atheros): Opening madwifing_g source interface kis...
Source 3 (Atheros): Enabling monitor mode for madwifing_g source interface wifi0 channel 6...
WARNING: wifi0 appears to not accept the Madwifi-NG controls. Will attempt to configure it as a standard Madwifi-old interface. If you are using madwifi-ng, be sure to set the source interface to the wifiX control interface, NOT athX
FATAL: channel get ioctl failed 22:Invalid argument
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}
acer@acer-laptop:~$

---

### Post by little dave on 2007-10-19
> 
FATAL: channel get ioctl failed 22:Invalid argument


 Right click your Network manager and turn off enable wireless.

---

### Post by a_stanley on 2007-10-19
hey,

yeah, i already had wireless unchecked didn't help - disabled networking, no luck

I ended up deciding to upgrade to 7.10, got kismet working, airoplay, all that (kinda disturbing to see MY wep key unclothed so easily hahaha, better me than someone else doing it though.

I've still got a problem with kismet though...

it runs fine for awhile, then stops getting packets.. (how many times have you heard this?)

I've tried disabling anything i can think of, checked the logs to see what's happening and i don't see anything coming up at the time the card kicks off.

the new version of kismet destroys all the VAPs and creates the kis interface by itself, so i don't have a rouge VAP taking it over.

I read that wma_supplicant could be a source of problems but am unsure if it can be removed, or how to go about doing that. I tried running the "ifupdown.sh" script which as i understand it would shutdown the process if it was running?

I was able to do everything i needed but i don't think i'm going to be satisfied until i can just leave kismet running... maybe get a gps and cruise the block with it

when i had kismet working previously airodump had the same problem (would work, then stop recieving packets) now airodump runs fine, just fine but kismet still craps out on me

lemme know if anyone got any ideas

thanks!

---

### Post by Oraclegol on 2007-10-19
yeah it is a know pug with the mad wifi drivers so make shure you enter
```

sudo modprobe -r ath_pci wlan_scan_sta ath_rate_sample wlan
sudo modprobe ath_pci autocreate=none 
```
before you run kismet

---

### Post by a_stanley on 2007-10-19
ill give it a shot, how would i go about reversing those commands to get my wifi internet connection back?

my guess:

sudo modprobe -r ath_pci wlan_scan_sta ath_rate_sample wlan
sudo modprobe ath_pci autocreate=true

?

would i then be able to 'sudo wlanconfig ath0 create wlandev wifi0 wlanmode managed'
then enable wireless by right clicking on the applet?

---

### Post by tturrisi on 2007-10-19
These are sources to use in kismet:
[http://www.kismetwireless.net/documentation.shtml](http://www.kismetwireless.net/documentation.shtml)
(section 12)
[http://www.kismetwireless.net/Forum/General/Search/?SearchString=source%3Dmadwifi&SearchType=Body](http://www.kismetwireless.net/Forum/General/Search/?SearchString=source%3Dmadwifi&SearchType=Body)

When kismet errors as mentioned above, it writes lines to the bottom of kismet.conf.  Look at the very bottom of your /etc/kismet.conf file and delete the madwifi lines if get the errors as posted above.

These are the ones I use:
```

source=madwifi_b,wifi0,madwifi

# OTHER SOURCES

#source=bcm43xx,eth2,bcm43xx
#source=acx100,wlan0,acx
#source=orinoco,eth0,hermes1
#source=rt8180,wlan0,Realtek
#source=prism54g,eth1,PrismGT
#source=hostap,wlan0,Prism2
#source=wlanng,wlan0,Prism2
#source=ipw2100,eth1,Centrino_b
#source=ipw2200,eth1,Centrino_g
#source=rt2500,ra0,Ralink_g
#source=rt2500,rausb0,Ralink_g
#source=kismet_drone,192.168.2.252:3501,kismet_drone 
```

---

### Post by a_stanley on 2007-10-20
hey, thanks for the links

I think i've got the source configured correctly, currently my source line is:

source=madwifi_b,wifi0,atheros

i tried the commands you suggested, it returns that wlan is in use, i've disable wireless networking in the network managed app though

---

### Post by tturrisi on 2007-10-20
Sometimes kismet does not cleanly handle atheros devices when exiting, thus you must manually reset the device to managed mode.  See the wireless setup section at my page here:
[http://members.cox.net/tonyt/d830/#wireless-setup](http://members.cox.net/tonyt/d830/#wireless-setup)

---

### Post by VncentVega on 2008-04-07
has anyone found a solution to this problem ? This has been bugging me for quite some time now. I used it last night to test how quick it would be to crack my home WEP and it worked. I didn't change a thing, now whenver I run kismet I get the same errors as most of you as well, I've tried everything listed in this thread except installing new madwifi drivers. I'm thinking it might have something to do with airmon-ng ?

---

