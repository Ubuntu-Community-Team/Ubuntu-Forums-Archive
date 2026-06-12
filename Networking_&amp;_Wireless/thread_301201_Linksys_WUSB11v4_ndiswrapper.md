---
title: "Linksys WUSB11v4 ndiswrapper"
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by FrodoB on 2006-11-16
I just put up a user document for my ndiswrapper experience with the Linksys WUSB11v4 USB wireless device. A strange note is that this device requires that the wireless-key keyword in the interfaces file has to be changed to wireless-key1 for the device to work. Is this common with ndiswrapper?

Here is the procedure that I followed:

[https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

---

### Post by wieman01 on 2006-11-16
No, this entirely relates to your WEP security settings. "ndiswrapper" has nothing to do with it. Check your router for more details.

---

### Post by FrodoB on 2006-11-17
Normally I would agree with you on this one, in fact if I had read the same post from someone else before yesterday I would have said the same thing that you said. But the issue is solid and repeatable. 

The exact same record using "wireless-key" rather than "wireless-key1" works with the three non-ndiswrapper using devices that I also have here with me. In fact the exact same record just changing "wireless-key" to "wireless-key1" works on this device. 

I just pull out this device and remove ndiswrapper using rmmod and plug those devices into the computer and they come up using native drivers and use the same wlan0 record using "wireless-key" correctly and ifup/ifdown(using the same wlan0 record in interfaces) as many times as you please.

The only  two variables are using ndiswrapper or using this device(and its  ndis driver) vs not using ndiswrapper and this device. The router's security settings have not changed in over a month and work without fail using the following USB devices using native drivers and I should note that the key was cut and pasted from the records for these devices and the WG111v2 uses wlan0 as its device name and the same record:

F5D7050 ver 3000
F5D7050 ver 4000
WG111v2

The reason I found this issue was that after installing everything and seeing that device worked but would not attach, I wrote a startup script to bring up the device using iwconfig commands and the card worked perfectly. I know the key is not the issue because I used the cut/paste method between the working script and the interfaces file. And as I said I was cutting and pasting these KEY records from previously working devices as I do find that most people's issues at this point relate to key settings.

I started looking at other folk's ndiswrapper experience on the web and I was seeing that in their interfaces files that some of them were using "wireless-key1" rather than "wireless-key". Then I noticed that in some others they had both keywords with the same key in both records. I thought that it did not make any sense, but upon changing "wireless-key" to "wireless-key1" in the interfaces record one could use ifup/ifdown rather than having to use a bash script of iwconfig commands to bring the device up. I then read through the startup scripts that read the interfaces file, nothing revealing there.

I then changed the interfaces file back to "wireless-key" and verified that ifup/ifdown no longer worked. If I issue an ifup dhclient never gets a dhcp address. If you look in another terminal window and type iwconfig it shows you why, the device has not authenticated with the AP. If while dhclient is trying to connect you issue:

sudo iwconfig wlan0 key "XXXXXXXXXXXXXXXXXXXXXXXXXX"

dhclient immediately finds the device and obtains an address. 


So I agree that it should not be an issue, and logically it should not make a difference, I have used prior versions of ndiswrapper on other devices in the past and they did not have this issue, but for this device type and ndiswrapper it clearly does. I have further redone this same install on a new install of 6.06 on another machine to verify that the "wireless-key" vs. "wireless-key1" issue still exists. Perhaps another version of ndiswrapper?

Everything is repeatable, no exceptions, any suggestions for a series of test events to determine conclusively where the fault lies?

I should also note for those reading this post that the device works correctly per the published documentation in the first post, so it would work for you also, we are just trying to determine why the "wireless-key" vs. "wireless-key1" anomaly exists when it should not. 

Thanks,

FrodoB

---

### Post by wieman01 on 2006-11-17
I cannot speak for your version of ndiswrapper, only for mine (v1.17). I have tested "wireless-essid" before and it worked, however, this may have changed in the meantime. When using WEP, the system usually generate 4 keys that you may use for encryption and apparently your version of "ndiswrapper" caters to that. 

So my point is that you're right if this works for you. You have all the evidence you need. The facts speak for themselves.

---

### Post by Y4CcduyctJL3 on 2006-11-18
hi. i've got the same adapter as you, and i've been having the same problem too.  up until now i had done everything the same as you did except for the 'key1' thing, and when i found your post i thought i'd finally found the silver bullet.  but after trying it there was no change.  i still have to run a script after startup to get a connection, so there must be something else that's being overlooked.

---

### Post by FrodoB on 2006-11-18
What do you have to run in your script?

---

### Post by Y4CcduyctJL3 on 2006-11-18
sudo ifconfig wlan0 down
sudo iwconfig wlan0 essid ........
sudo iwconfig wlan0 key open ............
sudo ifconfig wlan0 up
sudo dhclient wlan0
sudo -k

---

### Post by FrodoB on 2006-11-18
What are you putting in the interfaces file that does not work?

---

### Post by Y4CcduyctJL3 on 2006-11-18
i'm not really sure.  how would i tell.  i just know it's not connected after startup.

```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid .......
wireless-key1 .......

```

---

### Post by FrodoB on 2006-11-19
> **coffeejoe said:**
> 
sudo ifconfig wlan0 down
sudo iwconfig wlan0 essid ........
sudo iwconfig wlan0 key open ............
sudo ifconfig wlan0 up
sudo dhclient wlan0
sudo -k

Well, this looks similar to my experience in trying to get the same device to work on my Presario notebook. Have you tried just this alone:

sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
sudo dhclient wlan0

On my notebook, for some reason, the ndiswrapper was finding the device on bootup, but it did not finish initialization, so it was part way up. Because what you are doing is bringing the settings in interfaces down, setting them again manually, and then reinstalling the settings in interfaces on the way back up. So could it be that the manual settings are not does the trick, but taking the network down and back up?

Also another thing to try, that does not make sense, but might show something. Put the same settings in interfaces twice:

iface wlan0 inet dhcp
wireless-essid H.M.S. Hood
wireless-key1 xxxxxxxxxxxxxxxxxxxxxxx
wireless-key xxxxxxxxxxxxxxxxxxxxxxx
auto wlan0

I would like to figureout what the trick is here so we can document it for others.

---

### Post by Y4CcduyctJL3 on 2006-11-19
the first thing doesn't work, and the second thing makes no change.

one other thing.  how's you system stability?  I'm getting random hard crashes, and i suspect it might be related to the linksys.

---

### Post by wieman01 on 2006-11-19
The hardcrash issue may relate to your version of "ndiswrapper". I remember that I used to have them as well until I upgraded...

---

### Post by FrodoB on 2006-11-20
Coffeejoe;

What version of ndiswrapper are you using? I am using 1.28 which I compiled from source and there are no stability issues, just the wireless-key vs. wireless-key1 thing, which is liveable. I should add that I have used the procedure on three computers and Dapper and Edgy with identical results so far.

---

### Post by Y4CcduyctJL3 on 2006-11-23
```
:~$ ndiswrapper -v
utils version: 1.9
driver version:        1.28
vermagic:       2.6.15-27-386 preempt 486 gcc-4.0
```compiled from source.

i upgraded it because i had the same thought about the hard crashes, but it didn't eliminate them.  they do however seem to be less frequent.

---

### Post by 720iD on 2007-02-24
dont know whether i am interfering in something that is way over my head here but i have this exact device and it is working great using ndiswrapper and xp driver. i dont have any encryption keys though.

---

### Post by wieman01 on 2007-02-24
> **720iD said:**
> dont know whether i am interfering in something that is way over my head here but i have this exact device and it is working great using ndiswrapper and xp driver. i dont have any encryption keys though.
Guess we can help you with encryption though.

---

### Post by 720iD on 2007-02-24
> **wieman01 said:**
> Guess we can help you with encryption though.

thanks its ok, my internet is provided by my landlord it is an open access point for all tennents, i dont need encryption, i realise this may compromise my own system but i dont have anything important here so i'm not too worried.

---

