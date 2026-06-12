---
title: "Lenovo S206 - Xubuntu 14.04 - Can't find my WLan"
date: 2015-05-22
forum: Networking &amp; Wireless
---

### Post by COschmann on 2015-05-22
Hello everybody,

my problem is the following:
I can't find the wireless connection to my very own router. I find other routers (those of my neighbours) and I can find and connect to the WLan at my university without any problem. Just the home wireless does not appear. Since I dont have a ethernet plug I can not connect to the router directly (which is one of the presented solutions around here and other forums). 
The solution from [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110) did not work for me.
 
Since I am not very good with Ubuntu, and I really don't understand all the values in the .txt file I would appreaciate any help I can get.

Kind regards and thanks in advance.

[ATTACH]262124[/ATTACH]

---

### Post by chili555 on 2015-05-23
I wonder if your wireless device doesn't see your home router because the router is set to a channel that the wireless device thinks it is not allowed to receive. Do you know what channel it's on, perhaps from other devices on the network? Is it, by chance, on 12 or 13?

Please see this from your diagnostics:> wlan0     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency=2.462 GHz (Channel 11)And also:> ##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

[COLOR="#FF0000"]country 00[/COLOR]:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSSI recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

It may take a reboot.

If this doesn't help, we will need to address settings in the router itself.

---

