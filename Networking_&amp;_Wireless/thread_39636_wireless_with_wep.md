---
title: "wireless with wep"
date: 2005-06-05
forum: Networking &amp; Wireless
---

### Post by ssck on 2005-06-05
hi all,

need some help.i don't seem to be able to ping my wireless device gateway ip.it is using wep.can someone check whether my settings are correct in the interfaces file ?

iface wlan0 inet dhcp
wireless_mode managed
wireless_keymode restricted
wireless-essid H2
wireless-key 7E2C-5A33-88

is the above setting correct for connecting to a wep cionfigured wireless device ?

any help appreciated.

thanks

---

### Post by joshmachine on 2005-06-06
[QUOTE=ssck]hi all,

need some help.i don't seem to be able to ping my wireless device gateway ip.it is using wep.can someone check whether my settings are correct in the interfaces file ?

iface wlan0 inet dhcp
wireless_mode managed
wireless_keymode restricted
wireless-essid H2
wireless-key 7E2C-5A33-88

is the above setting correct for connecting to a wep cionfigured wireless device ?

any help appreciated.

thanks[/QUOTE]
 1.  I think in Ubuntu (and debian based distros) the options all use a "-" character not a "_" character like your first two do.
2.  the wireless_mode and wireless_keymode aren't necessary, and I would drop them.
3. You have to have the "wireless-tools" package installed to use these scripts.  You can test if this is case by typing "iwconfig" at the prompt and see what you get.  If it is a command not found, you must install that package (using aptitude/synaptic/whatever).
4. iwconfig will also show you that the settings are as you expected.
5. If you want this to be done automatically at boot time you must add the following line into your "/etc/network/interfaces" file  

auto wlan0

otherwise you must run 

sudo ifup wlan0

to bring the interface up

and 

sudo ifdown wlan0 

to bring it down.

NOTE: Having it set to auto will make your boot sequence stall if you are booting up your computer and it does not pick up your AP

6. What driver are you using for your wireless card?  

Cheers

---

### Post by ssck on 2005-06-06
[QUOTE=joshmachine]1.  I think in Ubuntu (and debian based distros) the options all use a "-" character not a "_" character like your first two do.
2.  the wireless_mode and wireless_keymode aren't necessary, and I would drop them.
3. You have to have the "wireless-tools" package installed to use these scripts.  You can test if this is case by typing "iwconfig" at the prompt and see what you get.  If it is a command not found, you must install that package (using aptitude/synaptic/whatever).
4. iwconfig will also show you that the settings are as you expected.
5. If you want this to be done automatically at boot time you must add the following line into your "/etc/network/interfaces" file  

auto wlan0

otherwise you must run 

sudo ifup wlan0

to bring the interface up

and 

sudo ifdown wlan0 

to bring it down.

NOTE: Having it set to auto will make your boot sequence stall if you are booting up your computer and it does not pick up your AP

6. What driver are you using for your wireless card?  

Cheers[/QUOTE]

i have changed the settings in the interfaces file accordingly.these are my settings for iwconfig.however, when i ping the wireless gateway, i am still getting request time out.what else could be the problem ? the wep is obviously correct because otherwise, i will not be able to get connected.

in windows xp, i have no problems getting connected.in my home wireless device which i tested without wep, it works fine.

wlan0     IEEE 802.11g  ESSID:"H2"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:04:E2:66:C7:70
          Bit Rate:11 Mb/s
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-51 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0]

---

### Post by joshmachine on 2005-06-06
Hmmm I am a little confused by your posting.   

There are two independant pieces which we must verify are working. The wireless connection. And the network configuration. let us keep them seperate.

Also we know that xp is working fine. 

My understanding of your current situation is that 

* Everything works and you are able to ping your router if you comment out the wireless-key entry in your "interfaces" file.
* once you try to use an encrypted connection, it doesn't work

Is this the case?


NOTE: it is much easier when you are testing encryption if you use a key that is easily typed.
"abcdefg0000000000000000000"


Please post the following info:
Your network card information (pcmcia?, brand, etc.)
Your brand of router
The encryption settings on your router.
(i.e) key length, open or shared or both etc.

At this point I think it is best just to focus on getting the connection working and ignore the "interfaces file" we can do that be issuing our configuration on the commandline.

sudo iwconfig wlan0 essid H2 key abcdefg0000000000000000000

Post the rest of your info and we'll see what we can do.  I gotta go, work is bustin' my balls.


Cheers

---

### Post by joshchernoff on 2005-06-07
[QUOTE=joshmachine]Hmmm I am a little confused by your posting.   

There are two independant pieces which we must verify are working. The wireless connection. And the network configuration. let us keep them seperate.

Also we know that xp is working fine. 

My understanding of your current situation is that 

* Everything works and you are able to ping your router if you comment out the wireless-key entry in your "interfaces" file.
* once you try to use an encrypted connection, it doesn't work

Is this the case?


NOTE: it is much easier when you are testing encryption if you use a key that is easily typed.
"abcdefg0000000000000000000"


Please post the following info:
Your network card information (pcmcia?, brand, etc.)
Your brand of router
The encryption settings on your router.
(i.e) key length, open or shared or both etc.

At this point I think it is best just to focus on getting the connection working and ignore the "interfaces file" we can do that be issuing our configuration on the commandline.

sudo iwconfig wlan0 essid H2 key abcdefg0000000000000000000

Post the rest of your info and we'll see what we can do.  I gotta go, work is bustin' my balls.


Cheers[/QUOTE]
first I'd like to say what I have 
wifi dwl-g510 dinks Vb with new windows2k .inf from dlink
ndiswrapper1.2
wireless-tools 27-1ubuntu1

if I set the rout to use wep 64bit hex 
i lose the the conection to the ap 
in the way of the mac shows 00-00-00-00-00-00 but if i turn off the wep 
I'm on with no problems

so in the atemp to fined out whats up  i try the gui way of setting the wep and 
the iwconfig way of 0000-0000-00 or just strate 0000000000
but nuthen and when I look at sudo iwconfig wlan0 i get this 

josh@joshome:~$ sudo iwconfig wlan0
Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wlan0     IEEE 802.11g  ESSID:"wescott apts."
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:11:95:73:71:C2
          Bit Rate:54 Mb/s
          Encryption key:off
          Link Quality:40/100  Signal level:-66 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed be

can some on tell me about the 18th driver and what the driver is
is it to ndiswrapper or the dlink card or something els I dont know about, and is thare a way of maken the wep a 64bit over 128bit, And is it a hex and how to make shure it's set to that
thanks to all that well help me with this.

---

### Post by joshmachine on 2005-06-07
[QUOTE=joshchernoff]first I'd like to say what I have 
wifi dwl-g510 dinks Vb with new windows2k .inf from dlink
ndiswrapper1.2
wireless-tools 27-1ubuntu1

if I set the rout to use wep 64bit hex 
i lose the the conection to the ap 
in the way of the mac shows 00-00-00-00-00-00 but if i turn off the wep 
I'm on with no problems

so in the atemp to fined out whats up  i try the gui way of setting the wep and 
the iwconfig way of 0000-0000-00 or just strate 0000000000
but nuthen and when I look at sudo iwconfig wlan0 i get this 

josh@joshome:~$ sudo iwconfig wlan0
Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wlan0     IEEE 802.11g  ESSID:"wescott apts."
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:11:95:73:71:C2
          Bit Rate:54 Mb/s
          Encryption key:off
          Link Quality:40/100  Signal level:-66 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed be

can some on tell me about the 18th driver and what the driver is
is it to ndiswrapper or the dlink card or something els I dont know about, and is thare a way of maken the wep a 64bit over 128bit, And is it a hex and how to make shure it's set to that
thanks to all that well help me with this.[/QUOTE]
I have had lots of problems with the Gnome Network configuration utility and don't use it myself. Unfortunately this requires a good deal of funky low level linux knowledge (I don't think that's a bad thing, but it does take some time.)

I recommend using the command line only. I have never used 64 bit WEP, so I can't rule that out, but for testing/ debugging I would use the following steps.

Confiugration assumptions:

* your wireless router provides dhcp
* you have your wireless driver installed installed properly (for ndiswrapper see [http://ndiswrapper.sourceforge.net/phpwiki/index.php/Installation]("http://ndiswrapper.sourceforge.net/phpwiki/index.php/Installation")  Section 2 for ensuring that you get the CORRECT windows drivers for your device, and install them properly)
* You have the following configuration in your /etc/network/interfaces file 

 ```
 iface wlan0 inet dhcp
``` 

That's it for configuration assumptions. When you debuggin networking stuff it is best to take it in small steps and verify that things are working along the way.

NOTE: Sometimes when testing out ndiswrapper enabled devices, things get a little funky and stop working.  An 

 ```
sudo rmmod ndiswrapper
```  

followed by 

 ```
sudo modprobe ndiswrapper
```

will usually clear things out and get you back to a good state.


Testing Steps.
Preamble:
Assume access point ssid is "foobar" and 128 bit WEP key (when is use)
is "abcdef00000000000000000000"   (abcdef followed by 20 zeros)


1. Verify that you are able to connect with your AP unencrypted (seems as though you both have done this)  
 ```
sudo iwconfig wlan0 essid foobar
``` 

now type

 ```
sudo iwconfig wlan0
```

you should see "ESSID:foobar"
and a non zero mac-id in the Access Point: section

1.1 Verify that you are able to get an ip address from your access point
type 
```
sudo ifup wlan0
```

2. Repeat with encryption turned on in your access point. I have only ever used 128 bit encryption so my example will use the same.

(reinsert the ndiswrapper module if things don't work for you before giving up)

2.1.

 ```
sudo iwconfig wlan0 essid foobar key abcdef00000000000000000000
``` 

now type
 
  ```
sudo iwconfig wlan0
```
 
 you should see "ESSID:foobar"
 and a non zero mac-id in the "Access Point:" section and a nonzero key in the "Encryption key:" section

If you get an error about WEP not being supported, you will have to check the ndiswrapper page listed above and verify that your card works with encryption.

Repeat 1.1 

And it should all just work.

Good luck.

When you are ready for some more configuration ass-kicking you can try WPA with wpasupplicant, but save that for later.

Cheers

---

### Post by joshchernoff on 2005-06-07
[QUOTE=joshmachine]I have had lots of problems with the Gnome Network configuration utility and don't use it myself. Unfortunately this requires a good deal of funky low level linux knowledge (I don't think that's a bad thing, but it does take some time.)

I recommend using the command line only. I have never used 64 bit WEP, so I can't rule that out, but for testing/ debugging I would use the following steps.

Confiugration assumptions:

* your wireless router provides dhcp
* you have your wireless driver installed installed properly (for ndiswrapper see [http://ndiswrapper.sourceforge.net/phpwiki/index.php/Installation]("http://ndiswrapper.sourceforge.net/phpwiki/index.php/Installation")  Section 2 for ensuring that you get the CORRECT windows drivers for your device, and install them properly)
* You have the following configuration in your /etc/network/interfaces file 

 ```
 iface wlan0 inet dhcp
``` 

That's it for configuration assumptions. When you debuggin networking stuff it is best to take it in small steps and verify that things are working along the way.

NOTE: Sometimes when testing out ndiswrapper enabled devices, things get a little funky and stop working.  An 

 ```
sudo rmmod ndiswrapper
```  

followed by 

 ```
sudo modprobe ndiswrapper
```

will usually clear things out and get you back to a good state.


Testing Steps.
Preamble:
Assume access point ssid is "foobar" and 128 bit WEP key (when is use)
is "abcdef00000000000000000000"   (abcdef followed by 20 zeros)


1. Verify that you are able to connect with your AP unencrypted (seems as though you both have done this)  
 ```
sudo iwconfig wlan0 essid foobar
``` 

now type

 ```
sudo iwconfig wlan0
```

you should see "ESSID:foobar"
and a non zero mac-id in the Access Point: section

1.1 Verify that you are able to get an ip address from your access point
type 
```
sudo ifup wlan0
```

2. Repeat with encryption turned on in your access point. I have only ever used 128 bit encryption so my example will use the same.

(reinsert the ndiswrapper module if things don't work for you before giving up)

2.1.

 ```
sudo iwconfig wlan0 essid foobar key abcdef00000000000000000000
``` 

now type
 
  ```
sudo iwconfig wlan0
```
 
 you should see "ESSID:foobar"
 and a non zero mac-id in the "Access Point:" section and a nonzero key in the "Encryption key:" section

If you get an error about WEP not being supported, you will have to check the ndiswrapper page listed above and verify that your card works with encryption.

Repeat 1.1 

And it should all just work.

Good luck.

When you are ready for some more configuration ass-kicking you can try WPA with wpasupplicant, but save that for later.

Cheers[/QUOTE]
 something wird work! I found gtkwifi installed and try the 64bit key that I'v used under windows xp befor coming to ubuntu. and the next thing i knew I'm talking to my ap I could see it's mac and I got a ip from it's dhcp. It's a nice lettel app but I dont know how to realy work it to the bone.(witch is nice to know how to) any ways I found that this did fix the problem so I woud try it if you fined your self where I was, but thanks for the info on ndiswrapper I'v 
been looken for the way to upgrade my  Wireless Extension 17 to 18 and I'v not found much but that I need to patch my kernal witch I thought I did. but if you got any info on that I would be happy. I think this my be playing  a problem with the wep under ndiswrapper( not shur though)

---

### Post by ssck on 2005-06-08
[QUOTE=joshmachine]Hmmm I am a little confused by your posting.   

There are two independant pieces which we must verify are working. The wireless connection. And the network configuration. let us keep them seperate.

Also we know that xp is working fine. 

My understanding of your current situation is that 

* Everything works and you are able to ping your router if you comment out the wireless-key entry in your "interfaces" file.
* once you try to use an encrypted connection, it doesn't work

Is this the case?


NOTE: it is much easier when you are testing encryption if you use a key that is easily typed.
"abcdefg0000000000000000000"


Please post the following info:
Your network card information (pcmcia?, brand, etc.)
Your brand of router
The encryption settings on your router.
(i.e) key length, open or shared or both etc.

At this point I think it is best just to focus on getting the connection working and ignore the "interfaces file" we can do that be issuing our configuration on the commandline.

sudo iwconfig wlan0 essid H2 key abcdefg0000000000000000000

Post the rest of your info and we'll see what we can do.  I gotta go, work is bustin' my balls.


Cheers[/QUOTE]


hi,

sorry for the delay.

my network card is an internal linksys inprocomm ipn2220 card.

router is SMC.

and the key length for wep is 64 bit.

the setting is shared.

when i ping the gateway, there will be a request time out.

the above settings are for my office.

at home, it is a linksys router with no wep.there are no problems getting connected onto the internet.

so i believe that the issue is with the wep key.

thanks for helping.

---

### Post by ssck on 2005-06-12
i finally found the problem

iface wlan0 inet dhcp
wireless-essid H2
wireless-mode managed
wireless-keymode restricted
wireless-key aaaa-bbbb-cc

the wireless-essid setting must come immediately after the first setting (iface ....)

then wireless with wep will work ....

---

### Post by AdamLeyshon on 2005-06-23
what do you mean?
it must be the first setting in the config?

---

