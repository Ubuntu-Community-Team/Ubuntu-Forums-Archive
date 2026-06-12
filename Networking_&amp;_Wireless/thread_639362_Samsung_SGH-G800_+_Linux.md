---
title: "Samsung SGH-G800 + Linux"
date: 2007-12-13
forum: Networking &amp; Wireless
---

### Post by scorp123 on 2007-12-13
In the hope that someone may find this info useful:

I just wanted to report that Samsung's new **SGH-G800** mobile phone could be considered to be quite "Linux friendly". A lot of things work "out of the box", for some other functions such as bluetooth connectivity a few packages need to be downloaded from the repos (if they're not installed already). More infos about this phone can be found here:
[http://www.engadgetmobile.com/2007/10/22/samsungs-5-megapixel-g800-gets-launched-available-next-month/](http://www.engadgetmobile.com/2007/10/22/samsungs-5-megapixel-g800-gets-launched-available-next-month/)
[http://www.engadgetmobile.com/2007/12/10/hands-on-with-the-samsung-g800/](http://www.engadgetmobile.com/2007/12/10/hands-on-with-the-samsung-g800/)


_**What works:**_

The **Samsung SGH-G800** can be configured to act as USB mass storage device when it is connected to a computer. This works tip top, and with this you get access to the MicroSD card that is in the phone (if you have one, that is). Up- and downloading videos, photos and mp3 files works tip top via drag & drop (e.g. in GNOME's filemanager "Nautilus"), the phone's data transfer speeds via USB are tip top.

There are other USB modes available:
- "Media Player"
- "Samsung PC Studio"
- "Ask the user"

The "Media Player" mode is similar to the "USB mass storage" mode, the phone appears as media player device and I assume that applications such as Amarok and Exaile are able to talk to the phone and up- and download music, manage playlists, and so on. I haven't tested this yet, so far I have only used the "USB mass storage" mode for this and I am absolutely happy.

What I am currently experimenting with is the "Samsung PC Studio" mode. When connecting in this mode the kernel reports having found a new "ACM device" (e.g. I get a **/dev/ttyACM0** ) ... With other phones this is a good sign, because it means you could use it as modem (just use **/dev/ttyACM0** as modem device, e.g. instead of **/dev/ttyS0** or **/dev/ttyUSB0** ) ... Except the G800 doesn't seem to do anything when in this mode, I can't get it to react to any of the "AT..." commands I issue e.g. via "minicom". So I am still working on this and I will post more as soon as I find out more.

The "ask the user" mode is self-explanatory: When in this mode the phone will ask you what you want. I set my phone to this mode because it offers lots of flexibility.

**_Using the SGH-G800 as modem via Bluetooth_**

Basically you can follow this guide 1:1 ... it's what I did and it "just works":
[https://help.ubuntu.com/community/BluetoothDialup](https://help.ubuntu.com/community/BluetoothDialup)

To repeat some of the steps from above guide here again:

1.) **/etc/bluetooth/rfcomm.conf**
Enter your phone's hexadecimal MAC address and the channel for the "RFCOMM" service into this file (in my case it was channel 3). The file should already be "almost ready", you just need to fill the gaps and comment out the relevant lines. You can check those settings with this command: **sdptool browse 00:11: ...your-phone's-MAC-here... :33:44**

2.) **/etc/ppp/peers/BluetoothDialup**
Copy & paste this file from the guide.

3.) **/etc/chatscripts/BluetoothDialup**
Same here. Just copy & paste this file. Except for the last few lines which need to be corrected to reflect your provider's settings. In my case for the Swiss carrier [Swisscom](http://www.swisscom-mobile.ch) the settings would look like this:
```
TIMEOUT 35
ECHO    ON
ABORT   '\nBUSY\r'
ABORT   '\nERROR\r'
ABORT   '\nNO ANSWER\r'
ABORT   '\nNO CARRIER\r'
ABORT   '\nNO DIALTONE\r'
ABORT   '\nRINGING\r\n\r\nRINGING\r'
''      \rAT
OK      'AT+CGDCONT=1,"IP","gprs.swisscom.ch","",0,0'
OK      ATD*99***1#
CONNECT ""
```

And that's it.

To establish a connection you'd execute this command:
```
pon BluetoothDialup
```

And to hang up you'd execute this:
```
poff BluetoothDialup
```

BTW, when the phone is paired with your Ubuntu system and if the package **gnome-vfs-obexftp** is installed, you can access the phone's internal memory via your Nautilus file manager (connecting via USB in "USB mass storage" mode only gives access to the MicroSD card). Up- and downloading files to and from the internal memory is then just a matter of dragging & dropping the files from/to the right locations.

**_What I haven't tested yet or didn't yet get to work:_**

I don't know if things such as calendar synchronisation work or not, I haven't tested that yet. My company's "groupware" is web-based anyway, so for me it's more interesting to get to the web. I assume it could work with e.g. Evolution and e.g. the right "sync"-something plugins. If anyone gets this to work it would be nice to hear about it.

I tried a software I found in the repos: **bitpim** .... It looks promising, but so far I wasn't able to download my phone book or my stored SMS messages (which bitpim can do if you can get it to talk to your phone correctly).

So that's it ... To summarise:

- the SGH-G800 works tip top when in "USB mass storage mode", up- and downloading files to its MicroSD memory card is just a matter of drag & drop.
- up- and downloading files to the internal memory works tip top via Bluetooth
- using the phone as "3G modem" on Linux works tip top via Bluetooth (I haven't yet figured out how to get it working when connected via USB in "Samsung PC Studio" mode)

I hope someone will find the info provided here useful :)

---

### Post by FokkerCharlie on 2008-04-17
Thanks for the info!

I'm looking at getting this phone- can it be sync'd with Evolution via Multisync?

Or, failing that, some other method?

Cheers
Charlie

---

### Post by scorp123 on 2008-04-17
> **FokkerCharlie said:**
>  can it be sync'd with Evolution via Multisync? Or, failing that, some other method? I honestly haven't tried yet. I don't use Evolution -- I use Thunderbird for e-mail. And I don't use the phone's calendar app that much. I installed "Opera Mini" on my phone and now using the web is really easy. So now I connect to my Google Calendar directly if I really need to.

So if you want me to test my phone with Evolution you'd have to tell me how to do it, because I really never used Evolution before.

---

### Post by FokkerCharlie on 2008-04-17
Hi Scorp

Well, currently I have Evolution syncing with my Sony Ericsson K800i via MultiSync- the relevant plugins for Multisync are called 'Ximian Evolution 2' and 'IrMC Mobile Device'.  It works fine with a bit of tweaking.  I imagine that something equivalent is possible with Thunderbird, too- have you synced (how do you spell that?  I have no idea) your G800 phone/address book with the Thunderbird one?

For what it's worth, I couldn't get my K800i working with BitPIM, Gammu or Gnokii, to varying degrees of surprise.

Most interested in your input.

Charlie

---

### Post by scorp123 on 2008-04-17
Thanks for that input ... I will take a look and post again tomorrow.

---

### Post by scorp123 on 2008-04-22
Nope, doesn't seem to work. At least not via Bluetooth. Could not try USB yet because I can't find my #@!!!$ cable at the moment.

---

### Post by Gorkk on 2008-06-20
Hello there,

I just got my G800, and I can say one thing: at least through USB (no reason why it wouldn't work through Bluetooth), you can access your Phonebook and SMS with KMobileTools and export them to KMail (and import your contacts from KMail as well).
Note: this was with the "PC Studio" mode, haven't tried other modes yet.

I'll take a look to Multisync and try to make it work (that would be cool, 'cause then I could sync with Sunbird and Thunderbird, and remove KMobileTools from my system, as it has too much "kde" dependencies on Archlinux - well actually, it's kdepim which has too much, as it requires kde-base ;)). I'll update here if I can get the syncing to work then.

Note: regarding the G800, I've something strange though; I previously had an Ericson Razr V3, and had 44 SMS stored on the SIM. When inserted into the G800, only 6 (seem to be the oldest) are found (though when putting back the SIM in the Razr, it finds the 44...).

---

### Post by scorp123 on 2008-06-20
> **Gorkk said:**
> I've something strange though; I previously had an Ericson Razr V3, and had 44 SMS stored on the SIM. When inserted into the G800, only 6 (seem to be the oldest) are found (though when putting back the SIM in the Razr, it finds the 44...). Yes, same problem here. Seems the phones use different sub-dirs to store the messages in. And are you really really sure all those SMS are on the SIM? My SIM can store like 10 or so SMS, any subsequent SMS is then stored on the phone's memory. Could be that the first six SMS really are on the SIM card, but the rest is in your other phone's RAM?

---

