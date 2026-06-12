---
title: "rtl8812au installed via dkms driver issues"
date: 2016-08-31
forum: Networking &amp; Wireless
---

### Post by issact2 on 2016-08-31
Hello all,

I have a bit of an annoying problem.  Every time I restart my PC, I have to unplug and plug in my wireless adapter in order for it to work.  Also, if the kernel ever updates, I get two entries for it in dkms status, and that completely breaks it.  When it happened I had to remove both dkms entries manually, uninstall the rtl8812au-dkms package, then reinstall it.

I don't really understand dkms much, I just want the dang thing to work reliably.  Before dkms I used some other driver from github, but that would be rather unreliable as well.  At least the dkms driver is reliable once connected, but dealing with all this is rather annoying.

Could anyone please take the time to help me troubleshoot?  I have other issues as well, but a reliable internet connection is #1 right now.


Ubuntu 16.04
dkms status: rtl8812au, 4.3.8.12175.20140902+dfsg, 4.4.0-36-generic, x86_64: installed

Thank you!

Edit:
Thanks for moving it to the appropriate forum, jeremy.

I will say that I have been fighting with this for a few weeks before coming here to ask for help.  I apologize for not going into detail with what I've done, I had originally posted this with minutes before I had to leave for work.  I'll give a detailed rundown of my specific system, what I have tried, and with any luck it will help someone help me.

First off, from a fresh installation of Ubuntu 16.04LTS, wifi is dead in the water.  There is no inclusive support for the rtl8812au chipset.  My specific wlan card it a TP-LINK Archer T4UH.  I got it off Amazon at a good price, but have only recently discovered it's a bit rare in the US because it was a short-lived UK marketed card.  Now this shouldn't matter, right?

As for other hardware, I recently treated myself to a major upgrade.  I was using bloomfield, now I'm on skylake with the ASUS Z170-a.  Very happy with it, too!  I'm not sure if this information helps.

Alright, let's go to two weeks ago when I decided to give linux another shot after 4 years-  Steam was starting to make me quite hopeful (And I am quite pleased, to this end, games ARE working quite well!)  I have no internet, cannot do a thing with packages.  Boot back up into windows, find a driver on github that I must compile.  It works!  Well, not completely.  See here:

[http://askubuntu.com/questions/814058/unreliable-wireless-driver-rtl8812au](http://askubuntu.com/questions/814058/unreliable-wireless-driver-rtl8812au)

Ah, but I found the answer to my own question.  It's true, giving the 5GHz band a different SSID did fix a lot of the unreliability.  However, wireless would still randomly disconnect for no rhyme or reason from time to time.  Sometimes I would even need to reboot!  And to further my frustrations, the kernel would completely forget my wireless card with every system update!  There had to be something better, and indeed, I found the dkms package.  That leads us here.

Compared to the github driver I have to compile every time I update, the connection was far more reliable and I never had to reboot or reconnect intermittently.  But as said above, it still needs to be reinstalled with every system update.  Unlike the github driver, I have to reconnect the hardware every time I reboot for the network list to show.


Here's some hopefully useful info.

iwconfig after reboot, before reconnecting the card:

```
enxc4e984090bf4  unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

iwconfig after reconnecting the card:

```
enxc4e984090bf4  IEEE 802.11bgn  ESSID:"Home-C398"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 9C:34:26:D4:C3:96   
          Bit Rate:144.4 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=93/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I am on the 2.4GHz band currently because I don't get intermittent high latency over it.  5GHz works fine when I want to download something quickly, but if I need perfect latency for games like CSGO, I have to switch over to 2.4.  I am not sure if this issue is related to my driver woes or if it's just a bad router.  The signal strength on both bands is nearly flawless.  5GHz just has random spasms of 300+ms response times to the router.  Another thing driving me crazy.  Whatever.  Help?

---

### Post by jeremy31 on 2016-09-01
*Thread moved to **Networking & Wireless**.*

---

### Post by issact2 on 2016-09-04
Giving this a bump.

---

### Post by praseodym on 2016-09-04
Please run the wireless script from the sticky thread and show the outputs.

---

### Post by issact2 on 2016-09-04
Here's a pastebin of the output:
[http://paste.ubuntu.com/23133743/](http://paste.ubuntu.com/23133743/)

---

### Post by praseodym on 2016-09-04
Wow, 55 networks around...Add the mtu-value of your ISP as number instead of "Automatic" and reconnect.

Check
```

ifconfig -a
```afterwards if there are still dropped packages. Also change the encryption mode in your router to pure WPA2-AES (CCMP), not mixed mode WPA/WPA2.

---

### Post by issact2 on 2016-09-04
Yeah, I live in a condominium complex.  And also comcast likes to make everyone's router a public wifi hotspot-  That essentially doubles it.

I don't seem to have the option to force set my MTU to 1500, likely because this router is a modem/router combo provided by comcast.

I changed the encryption to WPA2-AES only, here's to hoping there's no one with an older device in the house complaining in a few days :P  Will get back with ping test results on 5GHz later.  What about the issue on reboot and system updates I mentioned earlier?  Any ideas on that?

---

### Post by issact2 on 2016-09-06
So far my latency has been stable on the AC band in CSGO, after two days playing, now.  Thanks for that!

Still need help with the dkms drivers, though.

---

### Post by issact2 on 2016-09-09
> **issact2 said:**
> So far my latency has been stable on the AC band in CSGO, after two days playing, now.  Thanks for that!

Still need help with the dkms drivers, though.

Bumping again,

The intermittent high latency came back on the 5gHz connection.  Seems resetting the router fixes it for a day or two.  Still need help with other issues mentioned in OP.

Thanks!

---

### Post by issact2 on 2016-09-21
I'm sorry to keep bumping this.

Tonight the kernel for ubuntu updated again, and this time all my dkms entries doubled, so I removed all the older duplicates manually.
This did not fix the wifi, I had to remove all dkms entries for my adapter, uninstall the apt package, and reinstall it.

And of course, unplug and plug it in.  And I still must do this with every restart.

I have looked into this all along, of course.  The best idea I had is to put some line in init.rc to probe it at startup, but unfortunately I don't know my way around the terminal well enough to know what command will do that.  Or something like, cut the power to it and repower it.  I don't know, hah.  I'm willing to try anything for this to be handled automatically, it's starting to get a bit annoying to have to walk over to the dang thing every time I reboot.

There's also the issue of losing internet entirely and having to remember how to fix it every time the kernel updates.  I've no clue how to even start on that one.

As for the third issue, I'm pretty sure the fault lies in the ISP-provided router.  Unfortunately, I rent a room and have zero control over this.  She lets me log into it to change settings, but I don't think she'd go for replacing equipment.

---

### Post by jeremy31 on 2016-09-21
Can you post the dkms.conf file contents from rtl8812AU_rtl8821AU_linux directory

---

### Post by issact2 on 2016-09-22
Thanks for replying,

I found the following from the **rtl8812au-dkms_4.3.8.12175.20140902+dfsg-0ubuntu2_all.deb** package archive.  In the source folders, there was the dkms.conf file.

```

PACKAGE_NAME="rtl8812au"
PACKAGE_VERSION="4.3.8.12175.20140902+dfsg"
BUILT_MODULE_NAME[0]="8812au"
MAKE="'make' all"
CLEAN="'make' clean"
DEST_MODULE_LOCATION[0]="/updates/dkms"
AUTOINSTALL="YES"

```

---

### Post by jeremy31 on 2016-09-22
Do a ```
locate dkms.conf
```
This might be fixed with an edit of that file

---

### Post by issact2 on 2016-09-22
Thanks, Jeremy.

In **/var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/dkms.conf** the contents appear to be exactly the same as it was in the archive.
The same is true in **/usr/src/rtl8812au-4.3.8.12175.20140902+dfsg/dkms.conf**

---

### Post by jeremy31 on 2016-09-22
We will edit both dkms files just to be sure as my idea seems to have worked when testing on my laptop
```
sudo -H gedit /usr/src/rtl8812au-4.3.8.12175.20140902+dfsg/dkms.conf
```

Replace ```
MAKE="'make' all"
```
with
```
MAKE[0]="'make' all KVER=${kernelver}"
```
Save and exit gedit then do the same after
```
sudo -H gedit /var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/dkms.conf
```
Save, exit, and wait for the next kernel update to see if your results are the same as mine

---

### Post by issact2 on 2016-10-17
Hey Jeremy,

The kernel updated today and after restart, I was able to normally reconnect the wlan card as I usually do after a restart.  Thanks for the help. :)

You've given a lot of time, I guess I should let the last issue go, it's really just a QoL thing.  Maybe after a year or two Ubuntu core will just natively support it better.  Here's to hoping!

---

