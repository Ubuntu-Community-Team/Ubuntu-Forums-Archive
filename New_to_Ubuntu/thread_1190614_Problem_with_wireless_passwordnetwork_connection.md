---
title: "Problem with wireless password/network connection"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by bubbhasdance on 2009-06-18
Hello everyone, I just started using Ubuntu 9.04 earlier yesterday, and I love it so far. The only problem is that I'm not able to connect to my wireless internet. I have a built-in wireless adapter and Ubuntu does recognize it and gives a list of connections to connect to. The problem is, whenever I choose to connect to my home router and the dialog box asking for the password opens, apparently it is the wrong password!

I checked my router settings and I am putting in the correct password and security key type. Can anyone solve this problem? I really don't enjoy having to stay connected to Ethernet all day. Thanks in advance.

---

### Post by measekite on 2009-06-18
> **bubbhasdance said:**
> Hello everyone, I just started using Ubuntu 9.04 earlier yesterday, and I love it so far. The only problem is that I'm not able to connect to my wireless internet. I have a built-in wireless adapter and Ubuntu does recognize it and gives a list of connections to connect to. The problem is, whenever I choose to connect to my home router and the dialog box asking for the password opens, apparently it is the wrong password!

I checked my router settings and I am putting in the correct password and security key type. Can anyone solve this problem? I really don't enjoy having to stay connected to Ethernet all day. Thanks in advance.

I do not know what kind of wireless card you have but I do think there are some issues with network manager.  I have an old Linksys wmp11 card that I got working on my #2 computer but even after checking on connect automatically it does not and I have to do it manually.

**[COLOR=Red]I think this may be close to your solution.[/COLOR]**

Let us know if it works.  Network Manager that Jaunty uses places passwords into the keyring so the password it is looking for may be there.  

I would make a new connection using the network manager icon.  Your router may be using either WEP or WPA authentication.  What network manager is looking for is either the WEP or WPA authentication 128 bit code that your router is using and they are calling it a password.

So in your configuration box make sure you give the connection a name of your choice and then in the next box provide the SSID.  Then where it asks for the password use the WEP or WPA depending on your router and choose connect automatically which means on reboot.  It may work for you.  I would uncheck the box (at least for now) that says available to all users.

Then when you left click on the connection icon if you do not see your network name or have trouble connecting then choose "Connect to hidden wireless network".  In the next dialog hit the drop down instead of the new and choose your name that you gave to the network.  The connect button should light up and when you press it the red x will disappear and you should see some bars.  If you then hover your mouse over the icon you will see your connection strength.

[B]I would like to know if this works for you.

I would also like to know if you can connect automatically on reboot.

I would also like to know the make and model of your wireless card and router.[/B]

Hope this helps/

---

### Post by Scunnered on 2009-06-18
You dont give us too much to work with.  It would assist is you could detail what wireless adapter you are using as this can effect the response to your question.

In my case when I have problems with wireless calling for the password I enter the password provided by my cable supplier, not the system password.  If it does not immediately open having entered the correct password I do not re-enter the password but **SHUT DOWN**.  I stress shut down as restart does not work in this regard. After rebooting normally you will find that a connection will be made.  The worst I have had was to reboot twice.

You can give this a try and see what works.  If not please provide detailed information and see if others can assist

PS Just like the thing while I an writing this measekite posts in similar vein

---

### Post by measekite on 2009-06-18
> **Scunnered said:**
> You dont give us too much to work with.  It would assist is you could detail what wireless adapter you are using as this can effect the response to your question.

In my case when I have problems with wireless calling for the password I enter the password provided by my cable supplier, not the system password.  If it does not immediately open having entered the correct password I do not re-enter the password but **SHUT DOWN**.  I stress shut down as restart does not work in this regard. After rebooting normally you will find that a connection will be made.  The worst I have had was to reboot twice.

You can give this a try and see what works.  If not please provide detailed information and see if others can assist

PS Just like the thing while I an writing this measekite posts in similar vein

If he is using a correctly configured router then most of the time the router is logging on to either DSL or the Cable and providing that password.  The router should be using either WEP or WPA depending on the router model and the card.

Network manager is really looking for the 128 bit hex encryption code that allow the card to communicate with the router.

So I think in his case what you have is the router is connected to the internet but the card is not connected to the router; therefore not network connection.  

Now if the original poster foolishly did not configure the router with either a WEP or WPA authentication then that password field should be left totally blank but that would be a real dangerous way of doing things since anybody nearby could log in to his router and use his internet connection.  As nothing would like credit card passwords etc would be encrypted.

That is just my opinion.

I have another issue. Actually more then one.  I have an old Linksys wmp11 card and can connect very well manually.  Read my other post.  But when I reboot the system does not connect automatically even thought network manager is configured to work that way with the box checked.

I do not know if that is a bug in network manager or the way it works with my card in Janunty for it did connect automatically in Feisty.

---

### Post by bubbhasdance on 2009-06-18
I did set up WPA2 authentication for my network settings, and I am using a PCI Atheros Wireless Adapter. If any more details need to be known about the adapter, I will gladly give it.

The only problem is, when I go to my home computer to access the router status page, there is an error within the page. Nothing shows up, and the status page is completely blank. This is unrelated to my connection problem, but in order to get the 128-bit hexadecimal code, I would have to be able to access that page. Is there any other way to acquire this code? I have heard of hexadecimal converters and the like but I am not sure if it will work in this case.

Thanks in advance, and if I am able to get this code, then I will let you know.

EDIT: Did not see the request for wireless card/router make. 

00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller [11ab:4353] (rev 14)
06:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
08:03.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
08:03.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
08:03.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]

---

### Post by 3rdalbum on 2009-06-18
Are you typing in the password, or the key?

Most operating systems will not be able to convert a WEP passphrase into a WEP key, even if they provide the option - crazy huh? But it's true! Linux can usually do it, but in this case maybe it isn't. Try finding out your key and typing it in, rather than the passphrase.

The other thing is, there might be some sort of problem preventing connection. If you run the "dmesg" command in the terminal, do you get any error messages towards the end regarding the wireless network?

---

### Post by bubbhasdance on 2009-06-18
[B]I am just typing in the passphrase, not the 128bit key. I have my security settings set to WPA2, but have no way of obtaining the 128bit code, as my router's status page is down for some unknown reason.

This is what I received after running the dsmeg command in Terminal. I have no clue what any of it means, so hopefully someone can decipher this. [/B]

[18351.787428] phy0: failed to set freq to 2432 MHz for scan
[18351.825920] phy0: failed to set freq to 2437 MHz for scan
[18351.864417] phy0: failed to set freq to 2442 MHz for scan
[18351.902870] phy0: failed to set freq to 2447 MHz for scan
[18351.941370] phy0: failed to set freq to 2452 MHz for scan
[18351.979853] phy0: failed to set freq to 2457 MHz for scan
[18352.018336] phy0: failed to set freq to 2462 MHz for scan
[18352.056793] phy0: failed to set freq to 2467 MHz for scan
[18352.095280] phy0: failed to set freq to 2472 MHz for scan
[18352.133775] phy0: failed to set freq to 2484 MHz for scan
[18352.172288] phy0: failed to restore operational channel after scan
[18364.323349] __ratelimit: 21 callbacks suppressed
[18364.323354] ath5k phy0: noise floor calibration timeout (2462MHz)
[18375.322494] ath5k phy0: noise floor calibration timeout (2462MHz)
[18386.324514] ath5k phy0: noise floor calibration timeout (2462MHz)
[18392.179550] ath5k phy0: failed to wakeup the MAC Chip
[18392.179561] ath5k phy0: can't reset hardware (-5)
[18392.179567] phy0: failed to set freq to 2412 MHz for scan
[18392.218080] ath5k phy0: failed to wakeup the MAC Chip
[18392.218087] ath5k phy0: can't reset hardware (-5)
[18392.218092] phy0: failed to set freq to 2417 MHz for scan
[18392.256555] ath5k phy0: failed to wakeup the MAC Chip
[18392.256562] ath5k phy0: can't reset hardware (-5)
[18392.256567] phy0: failed to set freq to 2422 MHz for scan
[18392.295063] ath5k phy0: failed to wakeup the MAC Chip
[18392.295070] ath5k phy0: can't reset hardware (-5)
[18392.295075] phy0: failed to set freq to 2427 MHz for scan
[18392.333543] ath5k phy0: failed to wakeup the MAC Chip
[18392.333550] phy0: failed to set freq to 2432 MHz for scan
[18392.372040] phy0: failed to set freq to 2437 MHz for scan
[18392.410553] phy0: failed to set freq to 2442 MHz for scan
[18392.449034] phy0: failed to set freq to 2447 MHz for scan
[18392.487500] phy0: failed to set freq to 2452 MHz for scan
[18392.525967] phy0: failed to set freq to 2457 MHz for scan
[18392.564450] phy0: failed to set freq to 2462 MHz for scan
[18392.602943] phy0: failed to set freq to 2467 MHz for scan
[18392.641437] phy0: failed to set freq to 2472 MHz for scan
[18392.679899] phy0: failed to set freq to 2484 MHz for scan
[18392.718393] phy0: failed to restore operational channel after scan
[18397.324926] __ratelimit: 21 callbacks suppressed
[18397.324931] ath5k phy0: noise floor calibration timeout (2462MHz)
[18397.754570] ath5k phy0: failed to wakeup the MAC Chip
[18397.754582] ath5k phy0: can't reset hardware (-5)
[18397.754588] phy0: failed to set freq to 2412 MHz for scan
[18397.793129] ath5k phy0: failed to wakeup the MAC Chip
[18397.793137] ath5k phy0: can't reset hardware (-5)
[18397.793143] phy0: failed to set freq to 2417 MHz for scan
[18397.831662] ath5k phy0: failed to wakeup the MAC Chip
[18397.831669] ath5k phy0: can't reset hardware (-5)
[18397.831674] phy0: failed to set freq to 2422 MHz for scan
[18397.870114] ath5k phy0: failed to wakeup the MAC Chip
[18397.870119] ath5k phy0: can't reset hardware (-5)
[18397.870122] phy0: failed to set freq to 2427 MHz for scan
[18397.908559] ath5k phy0: failed to wakeup the MAC Chip
[18397.908564] phy0: failed to set freq to 2432 MHz for scan
[18397.947023] phy0: failed to set freq to 2437 MHz for scan
[18397.985475] phy0: failed to set freq to 2442 MHz for scan
[18398.023932] phy0: failed to set freq to 2447 MHz for scan
[18398.062395] phy0: failed to set freq to 2452 MHz for scan
[18398.100863] phy0: failed to set freq to 2457 MHz for scan
[18398.139351] phy0: failed to set freq to 2462 MHz for scan
[18398.177822] phy0: failed to set freq to 2467 MHz for scan
[18398.216251] phy0: failed to set freq to 2472 MHz for scan
[18398.254673] phy0: failed to set freq to 2484 MHz for scan
[18398.293147] phy0: failed to restore operational channel after scan
[18403.358627] __ratelimit: 21 callbacks suppressed
[18403.358635] ath5k phy0: failed to wakeup the MAC Chip
[18403.358642] ath5k phy0: can't reset hardware (-5)
[18403.358648] phy0: failed to set freq to 2412 MHz for scan
[18403.397198] ath5k phy0: failed to wakeup the MAC Chip
[18403.397206] ath5k phy0: can't reset hardware (-5)
[18403.397211] phy0: failed to set freq to 2417 MHz for scan
[18403.435772] ath5k phy0: failed to wakeup the MAC Chip
[18403.435779] ath5k phy0: can't reset hardware (-5)
[18403.435784] phy0: failed to set freq to 2422 MHz for scan
[18403.474259] ath5k phy0: failed to wakeup the MAC Chip
[18403.474264] ath5k phy0: can't reset hardware (-5)
[18403.474267] phy0: failed to set freq to 2427 MHz for scan
[18403.512726] ath5k phy0: failed to wakeup the MAC Chip
[18403.512731] ath5k phy0: can't reset hardware (-5)
[18403.512734] phy0: failed to set freq to 2432 MHz for scan
[18403.551172] phy0: failed to set freq to 2437 MHz for scan
[18403.589743] phy0: failed to set freq to 2442 MHz for scan
[18403.628184] phy0: failed to set freq to 2447 MHz for scan
[18403.666630] phy0: failed to set freq to 2452 MHz for scan
[18403.705123] phy0: failed to set freq to 2457 MHz for scan
[18403.743614] phy0: failed to set freq to 2462 MHz for scan
[18403.782065] phy0: failed to set freq to 2467 MHz for scan
[18403.820527] phy0: failed to set freq to 2472 MHz for scan
[18403.859019] phy0: failed to set freq to 2484 MHz for scan
[18403.897513] phy0: failed to restore operational channel after scan
[18408.962598] __ratelimit: 21 callbacks suppressed
[18408.962605] ath5k phy0: failed to wakeup the MAC Chip
[18408.962613] ath5k phy0: can't reset hardware (-5)
[18408.962619] phy0: failed to set freq to 2412 MHz for scan
[18409.001169] ath5k phy0: failed to wakeup the MAC Chip
[18409.001178] ath5k phy0: can't reset hardware (-5)
[18409.001183] phy0: failed to set freq to 2417 MHz for scan
[18409.039686] ath5k phy0: failed to wakeup the MAC Chip
[18409.039694] ath5k phy0: can't reset hardware (-5)
[18409.039699] phy0: failed to set freq to 2422 MHz for scan
[18409.078194] ath5k phy0: failed to wakeup the MAC Chip
[18409.078199] ath5k phy0: can't reset hardware (-5)
[18409.078203] phy0: failed to set freq to 2427 MHz for scan
[18409.116676] ath5k phy0: failed to wakeup the MAC Chip
[18409.116681] ath5k phy0: can't reset hardware (-5)
[18409.116684] phy0: failed to set freq to 2432 MHz for scan
[18409.155167] phy0: failed to set freq to 2437 MHz for scan
[18409.193619] phy0: failed to set freq to 2442 MHz for scan
[18409.232075] phy0: failed to set freq to 2447 MHz for scan
[18409.270542] phy0: failed to set freq to 2452 MHz for scan
[18409.309016] phy0: failed to set freq to 2457 MHz for scan
[18409.347472] phy0: failed to set freq to 2462 MHz for scan
[18409.385875] phy0: failed to set freq to 2467 MHz for scan
[18409.424362] phy0: failed to set freq to 2472 MHz for scan
[18409.462836] phy0: failed to set freq to 2484 MHz for scan
[18409.501297] phy0: failed to restore operational channel after scan
[18414.550544] __ratelimit: 20 callbacks suppressed
[18414.550551] ath5k phy0: failed to wakeup the MAC Chip
[18414.550559] ath5k phy0: can't reset hardware (-5)
[18414.550564] phy0: failed to set freq to 2412 MHz for scan
[18414.589156] ath5k phy0: failed to wakeup the MAC Chip
[18414.589165] ath5k phy0: can't reset hardware (-5)
[18414.589171] phy0: failed to set freq to 2417 MHz for scan
[18414.627685] ath5k phy0: failed to wakeup the MAC Chip
[18414.627692] ath5k phy0: can't reset hardware (-5)
[18414.627697] phy0: failed to set freq to 2422 MHz for scan
[18414.666145] ath5k phy0: failed to wakeup the MAC Chip
[18414.666150] ath5k phy0: can't reset hardware (-5)
[18414.666153] phy0: failed to set freq to 2427 MHz for scan
[18414.704564] ath5k phy0: failed to wakeup the MAC Chip
[18414.704569] ath5k phy0: can't reset hardware (-5)
[18414.704572] phy0: failed to set freq to 2432 MHz for scan
[18414.743019] phy0: failed to set freq to 2437 MHz for scan
[18414.781463] phy0: failed to set freq to 2442 MHz for scan
[18414.819909] phy0: failed to set freq to 2447 MHz for scan
[18414.858346] phy0: failed to set freq to 2452 MHz for scan
[18414.896798] phy0: failed to set freq to 2457 MHz for scan
[18414.935228] phy0: failed to set freq to 2462 MHz for scan
[18414.973686] phy0: failed to set freq to 2467 MHz for scan
[18415.012121] phy0: failed to set freq to 2472 MHz for scan
[18415.050584] phy0: failed to set freq to 2484 MHz for scan
[18415.089036] phy0: failed to restore operational channel after scan
[18420.114769] __ratelimit: 21 callbacks suppressed
[18420.114776] ath5k phy0: failed to wakeup the MAC Chip
[18420.114783] ath5k phy0: can't reset hardware (-5)
[18420.114789] phy0: failed to set freq to 2412 MHz for scan
[18420.153340] ath5k phy0: failed to wakeup the MAC Chip
[18420.153349] ath5k phy0: can't reset hardware (-5)
[18420.153354] phy0: failed to set freq to 2417 MHz for scan
[18420.191864] ath5k phy0: failed to wakeup the MAC Chip
[18420.191869] ath5k phy0: can't reset hardware (-5)
[18420.191872] phy0: failed to set freq to 2422 MHz for scan
[18420.230298] ath5k phy0: failed to wakeup the MAC Chip
[18420.230302] ath5k phy0: can't reset hardware (-5)
[18420.230305] phy0: failed to set freq to 2427 MHz for scan
[18420.268730] ath5k phy0: failed to wakeup the MAC Chip
[18420.268735] ath5k phy0: can't reset hardware (-5)
[18420.268738] phy0: failed to set freq to 2432 MHz for scan
[18420.307213] phy0: failed to set freq to 2437 MHz for scan
[18420.345705] phy0: failed to set freq to 2442 MHz for scan
[18420.384126] phy0: failed to set freq to 2447 MHz for scan
[18420.422569] phy0: failed to set freq to 2452 MHz for scan
[18420.460978] phy0: failed to set freq to 2457 MHz for scan
[18420.499445] phy0: failed to set freq to 2462 MHz for scan
[18420.537884] phy0: failed to set freq to 2467 MHz for scan
[18420.576308] phy0: failed to set freq to 2472 MHz for scan
[18420.614742] phy0: failed to set freq to 2484 MHz for scan
[18420.653220] phy0: failed to restore operational channel after scan
[18425.682664] __ratelimit: 20 callbacks suppressed
[18425.682672] ath5k phy0: failed to wakeup the MAC Chip
[18425.682679] ath5k phy0: can't reset hardware (-5)
[18425.682685] phy0: failed to set freq to 2412 MHz for scan
[18425.721259] ath5k phy0: failed to wakeup the MAC Chip
[18425.721267] ath5k phy0: can't reset hardware (-5)
[18425.721273] phy0: failed to set freq to 2417 MHz for scan
[18425.759855] ath5k phy0: failed to wakeup the MAC Chip
[18425.759863] ath5k phy0: can't reset hardware (-5)
[18425.759869] phy0: failed to set freq to 2422 MHz for scan
[18425.798244] ath5k phy0: failed to wakeup the MAC Chip
[18425.798248] ath5k phy0: can't reset hardware (-5)
[18425.798251] phy0: failed to set freq to 2427 MHz for scan
[18425.836641] ath5k phy0: failed to wakeup the MAC Chip
[18425.836646] ath5k phy0: can't reset hardware (-5)
[18425.836649] phy0: failed to set freq to 2432 MHz for scan
[18425.875129] phy0: failed to set freq to 2437 MHz for scan
[18425.913630] phy0: failed to set freq to 2442 MHz for scan
[18425.952125] phy0: failed to set freq to 2447 MHz for scan
[18425.990626] phy0: failed to set freq to 2452 MHz for scan
[18426.029162] phy0: failed to set freq to 2457 MHz for scan
[18426.067737] phy0: failed to set freq to 2462 MHz for scan
[18426.106299] phy0: failed to set freq to 2467 MHz for scan
[18426.144827] phy0: failed to set freq to 2472 MHz for scan
[18426.183370] phy0: failed to set freq to 2484 MHz for scan
[18426.221966] phy0: failed to restore operational channel after scan
[18431.250556] __ratelimit: 21 callbacks suppressed
[18431.250564] ath5k phy0: failed to wakeup the MAC Chip
[18431.250572] ath5k phy0: can't reset hardware (-5)
[18431.250578] phy0: failed to set freq to 2412 MHz for scan
[18431.289084] ath5k phy0: failed to wakeup the MAC Chip
[18431.289092] ath5k phy0: can't reset hardware (-5)
[18431.289098] phy0: failed to set freq to 2417 MHz for scan
[18431.327684] ath5k phy0: failed to wakeup the MAC Chip
[18431.327693] ath5k phy0: can't reset hardware (-5)
[18431.327698] phy0: failed to set freq to 2422 MHz for scan
[18431.366199] ath5k phy0: failed to wakeup the MAC Chip
[18431.366206] ath5k phy0: can't reset hardware (-5)
[18431.366211] phy0: failed to set freq to 2427 MHz for scan
[18431.404822] ath5k phy0: failed to wakeup the MAC Chip
[18431.404831] ath5k phy0: can't reset hardware (-5)
[18431.404837] phy0: failed to set freq to 2432 MHz for scan
[18431.443352] phy0: failed to set freq to 2437 MHz for scan
[18431.481876] phy0: failed to set freq to 2442 MHz for scan
[18431.520402] phy0: failed to set freq to 2447 MHz for scan
[18431.558843] phy0: failed to set freq to 2452 MHz for scan
[18431.597154] phy0: failed to set freq to 2457 MHz for scan
[18431.635678] phy0: failed to set freq to 2462 MHz for scan
[18431.674113] phy0: failed to set freq to 2467 MHz for scan
[18431.712603] phy0: failed to set freq to 2472 MHz for scan
[18431.751118] phy0: failed to set freq to 2484 MHz for scan
[18431.789672] phy0: failed to restore operational channel after scan
[18436.818620] __ratelimit: 20 callbacks suppressed
[18436.818628] ath5k phy0: failed to wakeup the MAC Chip
[18436.818636] ath5k phy0: can't reset hardware (-5)
[18436.818641] phy0: failed to set freq to 2412 MHz for scan
[18436.857130] ath5k phy0: failed to wakeup the MAC Chip
[18436.857138] ath5k phy0: can't reset hardware (-5)
[18436.857143] phy0: failed to set freq to 2417 MHz for scan
[18436.895684] ath5k phy0: failed to wakeup the MAC Chip
[18436.895692] ath5k phy0: can't reset hardware (-5)
[18436.895698] phy0: failed to set freq to 2422 MHz for scan
[18436.934314] ath5k phy0: failed to wakeup the MAC Chip
[18436.934321] ath5k phy0: can't reset hardware (-5)
[18436.934327] phy0: failed to set freq to 2427 MHz for scan
[18436.972846] ath5k phy0: failed to wakeup the MAC Chip
[18436.972851] ath5k phy0: can't reset hardware (-5)
[18436.972854] phy0: failed to set freq to 2432 MHz for scan
[18437.011282] phy0: failed to set freq to 2437 MHz for scan
[18437.049662] phy0: failed to set freq to 2442 MHz for scan
[18437.088149] phy0: failed to set freq to 2447 MHz for scan
[18437.126649] phy0: failed to set freq to 2452 MHz for scan
[18437.165118] phy0: failed to set freq to 2457 MHz for scan
[18437.203645] phy0: failed to set freq to 2462 MHz for scan
[18437.242179] phy0: failed to set freq to 2467 MHz for scan
[18437.280700] phy0: failed to set freq to 2472 MHz for scan
[18437.319265] phy0: failed to set freq to 2484 MHz for scan
[18437.357851] phy0: failed to restore operational channel after scan
[18442.386517] __ratelimit: 21 callbacks suppressed
[18442.386525] ath5k phy0: failed to wakeup the MAC Chip
[18442.386532] ath5k phy0: can't reset hardware (-5)
[18442.386538] phy0: failed to set freq to 2412 MHz for scan
[18442.425060] ath5k phy0: failed to wakeup the MAC Chip
[18442.425067] ath5k phy0: can't reset hardware (-5)
[18442.425073] phy0: failed to set freq to 2417 MHz for scan
[18442.463537] ath5k phy0: failed to wakeup the MAC Chip
[18442.463544] ath5k phy0: can't reset hardware (-5)
[18442.463549] phy0: failed to set freq to 2422 MHz for scan
[18442.502027] ath5k phy0: failed to wakeup the MAC Chip
[18442.502034] ath5k phy0: can't reset hardware (-5)
[18442.502039] phy0: failed to set freq to 2427 MHz for scan
[18442.540510] ath5k phy0: failed to wakeup the MAC Chip
[18442.540517] ath5k phy0: can't reset hardware (-5)
[18442.540523] phy0: failed to set freq to 2432 MHz for scan
[18442.578983] phy0: failed to set freq to 2437 MHz for scan
[18442.617485] phy0: failed to set freq to 2442 MHz for scan
[18442.655936] phy0: failed to set freq to 2447 MHz for scan
[18442.694440] phy0: failed to set freq to 2452 MHz for scan
[18442.732923] phy0: failed to set freq to 2457 MHz for scan
[18442.771385] phy0: failed to set freq to 2462 MHz for scan
[18442.809864] phy0: failed to set freq to 2467 MHz for scan
[18442.848340] phy0: failed to set freq to 2472 MHz for scan
[18442.886825] phy0: failed to set freq to 2484 MHz for scan
[18442.925359] phy0: failed to restore operational channel after scan
[18447.954560] __ratelimit: 20 callbacks suppressed
[18447.954567] ath5k phy0: failed to wakeup the MAC Chip
[18447.954574] ath5k phy0: can't reset hardware (-5)
[18447.954580] phy0: failed to set freq to 2412 MHz for scan
[18447.993050] ath5k phy0: failed to wakeup the MAC Chip
[18447.993056] ath5k phy0: can't reset hardware (-5)
[18447.993061] phy0: failed to set freq to 2417 MHz for scan
[18448.031565] ath5k phy0: failed to wakeup the MAC Chip
[18448.031573] ath5k phy0: can't reset hardware (-5)
[18448.031578] phy0: failed to set freq to 2422 MHz for scan
[18448.070089] ath5k phy0: failed to wakeup the MAC Chip
[18448.070096] ath5k phy0: can't reset hardware (-5)
[18448.070100] phy0: failed to set freq to 2427 MHz for scan
[18448.108573] ath5k phy0: failed to wakeup the MAC Chip
[18448.108581] ath5k phy0: can't reset hardware (-5)
[18448.108586] phy0: failed to set freq to 2432 MHz for scan
[18448.147060] phy0: failed to set freq to 2437 MHz for scan
[18448.185522] phy0: failed to set freq to 2442 MHz for scan
[18448.224030] phy0: failed to set freq to 2447 MHz for scan
[18448.262488] phy0: failed to set freq to 2452 MHz for scan
[18448.300954] phy0: failed to set freq to 2457 MHz for scan
[18448.339432] phy0: failed to set freq to 2462 MHz for scan
[18448.377952] phy0: failed to set freq to 2467 MHz for scan
[18448.416429] phy0: failed to set freq to 2472 MHz for scan
[18448.454909] phy0: failed to set freq to 2484 MHz for scan
[18448.493399] phy0: failed to restore operational channel after scan
[18463.324142] __ratelimit: 21 callbacks suppressed
[18463.324151] ath5k phy0: noise floor calibration timeout (2462MHz)
[18471.630562] ath5k phy0: failed to wakeup the MAC Chip
[18471.630573] ath5k phy0: can't reset hardware (-5)
[18471.630579] phy0: failed to set freq to 2412 MHz for scan
[18471.669055] ath5k phy0: failed to wakeup the MAC Chip
[18471.669062] ath5k phy0: can't reset hardware (-5)
[18471.669067] phy0: failed to set freq to 2417 MHz for scan
[18471.707594] ath5k phy0: failed to wakeup the MAC Chip
[18471.707601] ath5k phy0: can't reset hardware (-5)
[18471.707606] phy0: failed to set freq to 2422 MHz for scan
[18471.746068] ath5k phy0: failed to wakeup the MAC Chip
[18471.746076] ath5k phy0: can't reset hardware (-5)
[18471.746081] phy0: failed to set freq to 2427 MHz for scan
[18471.784554] ath5k phy0: failed to wakeup the MAC Chip
[18471.784560] phy0: failed to set freq to 2432 MHz for scan
[18471.823022] phy0: failed to set freq to 2437 MHz for scan
[18471.861483] phy0: failed to set freq to 2442 MHz for scan
[18471.899969] phy0: failed to set freq to 2447 MHz for scan
[18471.938431] phy0: failed to set freq to 2452 MHz for scan
[18471.976933] phy0: failed to set freq to 2457 MHz for scan
[18472.015454] phy0: failed to set freq to 2462 MHz for scan
[18472.053947] phy0: failed to set freq to 2467 MHz for scan
[18472.092400] phy0: failed to set freq to 2472 MHz for scan
[18472.130891] phy0: failed to set freq to 2484 MHz for scan
[18472.169383] phy0: failed to restore operational channel after scan
[18485.325286] __ratelimit: 22 callbacks suppressed
[18485.325293] ath5k phy0: noise floor calibration timeout (2462MHz)
[18496.324517] ath5k phy0: noise floor calibration timeout (2462MHz)
[18507.324670] ath5k phy0: noise floor calibration timeout (2462MHz)
[18518.324090] ath5k phy0: noise floor calibration timeout (2462MHz)
[18529.324210] ath5k phy0: noise floor calibration timeout (2462MHz)
[18540.325660] ath5k phy0: noise floor calibration timeout (2462MHz)
[18551.325057] ath5k phy0: noise floor calibration timeout (2462MHz)
[18562.325253] ath5k phy0: noise floor calibration timeout (2462MHz)
[18573.324918] ath5k phy0: noise floor calibration timeout (2462MHz)
[18584.325325] ath5k phy0: noise floor calibration timeout (2462MHz)
[18591.630670] ath5k phy0: failed to wakeup the MAC Chip
[18591.630680] ath5k phy0: can't reset hardware (-5)
[18591.630686] phy0: failed to set freq to 2412 MHz for scan
[18591.669178] ath5k phy0: failed to wakeup the MAC Chip
[18591.669186] ath5k phy0: can't reset hardware (-5)
[18591.669191] phy0: failed to set freq to 2417 MHz for scan
[18591.707673] ath5k phy0: failed to wakeup the MAC Chip
[18591.707680] ath5k phy0: can't reset hardware (-5)
[18591.707685] phy0: failed to set freq to 2422 MHz for scan
[18591.746200] ath5k phy0: failed to wakeup the MAC Chip
[18591.746207] ath5k phy0: can't reset hardware (-5)
[18591.746212] phy0: failed to set freq to 2427 MHz for scan
[18591.784675] ath5k phy0: failed to wakeup the MAC Chip
[18591.784681] ath5k phy0: can't reset hardware (-5)
[18591.784686] phy0: failed to set freq to 2432 MHz for scan
[18591.823143] phy0: failed to set freq to 2437 MHz for scan
[18591.861599] phy0: failed to set freq to 2442 MHz for scan
[18591.900063] phy0: failed to set freq to 2447 MHz for scan
[18591.938531] phy0: failed to set freq to 2452 MHz for scan
[18591.977028] phy0: failed to set freq to 2457 MHz for scan
[18592.015515] phy0: failed to set freq to 2462 MHz for scan
[18592.053988] phy0: failed to set freq to 2467 MHz for scan
[18592.092448] phy0: failed to set freq to 2472 MHz for scan
[18592.130913] phy0: failed to set freq to 2484 MHz for scan
[18592.169428] phy0: failed to restore operational channel after scan
[18606.324135] __ratelimit: 21 callbacks suppressed
[18606.324143] ath5k phy0: noise floor calibration timeout (2462MHz)
[18617.324175] ath5k phy0: noise floor calibration timeout (2462MHz)
[18628.324573] ath5k phy0: noise floor calibration timeout (2462MHz)
[18639.324126] ath5k phy0: noise floor calibration timeout (2462MHz)
[18650.325391] ath5k phy0: noise floor calibration timeout (2462MHz)
[18661.325534] ath5k phy0: noise floor calibration timeout (2462MHz)
[18672.325385] ath5k phy0: noise floor calibration timeout (2462MHz)
[18683.325308] ath5k phy0: noise floor calibration timeout (2462MHz)
[18694.325068] ath5k phy0: noise floor calibration timeout (2462MHz)
[18705.324124] ath5k phy0: noise floor calibration timeout (2462MHz)
[18711.630624] ath5k phy0: failed to wakeup the MAC Chip
[18711.630635] ath5k phy0: can't reset hardware (-5)
[18711.630642] phy0: failed to set freq to 2412 MHz for scan
[18711.669186] ath5k phy0: failed to wakeup the MAC Chip
[18711.669194] ath5k phy0: can't reset hardware (-5)
[18711.669200] phy0: failed to set freq to 2417 MHz for scan
[18711.707722] ath5k phy0: failed to wakeup the MAC Chip
[18711.707729] ath5k phy0: can't reset hardware (-5)
[18711.707735] phy0: failed to set freq to 2422 MHz for scan
[18711.746281] ath5k phy0: failed to wakeup the MAC Chip
[18711.746291] ath5k phy0: can't reset hardware (-5)
[18711.746297] phy0: failed to set freq to 2427 MHz for scan
[18711.784861] ath5k phy0: failed to wakeup the MAC Chip
[18711.784869] ath5k phy0: can't reset hardware (-5)
[18711.784874] phy0: failed to set freq to 2432 MHz for scan
[18711.823371] phy0: failed to set freq to 2437 MHz for scan
[18711.861832] phy0: failed to set freq to 2442 MHz for scan
[18711.900299] phy0: failed to set freq to 2447 MHz for scan
[18711.938783] phy0: failed to set freq to 2452 MHz for scan
[18711.977244] phy0: failed to set freq to 2457 MHz for scan
[18712.015724] phy0: failed to set freq to 2462 MHz for scan
[18712.054185] phy0: failed to set freq to 2467 MHz for scan
[18712.092694] phy0: failed to set freq to 2472 MHz for scan
[18712.131227] phy0: failed to set freq to 2484 MHz for scan
[18712.169750] phy0: failed to restore operational channel after scan
[18727.324262] __ratelimit: 21 callbacks suppressed
[18727.324270] ath5k phy0: noise floor calibration timeout (2462MHz)
[18738.325709] ath5k phy0: noise floor calibration timeout (2462MHz)
[18749.323606] ath5k phy0: noise floor calibration timeout (2462MHz)
[18760.324512] ath5k phy0: noise floor calibration timeout (2462MHz)
[18771.326128] ath5k phy0: noise floor calibration timeout (2462MHz)
[18782.325285] ath5k phy0: noise floor calibration timeout (2462MHz)
[18793.324169] ath5k phy0: noise floor calibration timeout (2462MHz)
[18804.324792] ath5k phy0: noise floor calibration timeout (2462MHz)
[18815.324459] ath5k phy0: noise floor calibration timeout (2462MHz)
[18826.325577] ath5k phy0: noise floor calibration timeout (2462MHz)
[18831.630665] ath5k phy0: failed to wakeup the MAC Chip
[18831.630676] ath5k phy0: can't reset hardware (-5)
[18831.630682] phy0: failed to set freq to 2412 MHz for scan
[18831.669201] ath5k phy0: failed to wakeup the MAC Chip
[18831.669208] ath5k phy0: can't reset hardware (-5)
[18831.669214] phy0: failed to set freq to 2417 MHz for scan
[18831.707706] ath5k phy0: failed to wakeup the MAC Chip
[18831.707713] ath5k phy0: can't reset hardware (-5)
[18831.707718] phy0: failed to set freq to 2422 MHz for scan
[18831.746235] ath5k phy0: failed to wakeup the MAC Chip
[18831.746242] ath5k phy0: can't reset hardware (-5)
[18831.746247] phy0: failed to set freq to 2427 MHz for scan
[18831.784636] ath5k phy0: failed to wakeup the MAC Chip
[18831.784640] ath5k phy0: can't reset hardware (-5)
[18831.784643] phy0: failed to set freq to 2432 MHz for scan
[18831.823065] phy0: failed to set freq to 2437 MHz for scan
[18831.861443] phy0: failed to set freq to 2442 MHz for scan
[18831.899863] phy0: failed to set freq to 2447 MHz for scan
[18831.938278] phy0: failed to set freq to 2452 MHz for scan
[18831.976730] phy0: failed to set freq to 2457 MHz for scan
[18832.015142] phy0: failed to set freq to 2462 MHz for scan
[18832.053544] phy0: failed to set freq to 2467 MHz for scan
[18832.091971] phy0: failed to set freq to 2472 MHz for scan
[18832.130394] phy0: failed to set freq to 2484 MHz for scan
[18832.168851] phy0: failed to restore operational channel after scan
[18837.325811] __ratelimit: 20 callbacks suppressed
[18837.325819] ath5k phy0: noise floor calibration timeout (2462MHz)
[18848.325613] ath5k phy0: noise floor calibration timeout (2462MHz)
[18859.324116] ath5k phy0: noise floor calibration timeout (2462MHz)
[18870.323865] ath5k phy0: noise floor calibration timeout (2462MHz)
[18881.324236] ath5k phy0: noise floor calibration timeout (2462MHz)
[18892.324191] ath5k phy0: noise floor calibration timeout (2462MHz)
[18903.325198] ath5k phy0: noise floor calibration timeout (2462MHz)
[18914.325054] ath5k phy0: noise floor calibration timeout (2462MHz)
[18925.325324] ath5k phy0: noise floor calibration timeout (2462MHz)
[18936.325342] ath5k phy0: noise floor calibration timeout (2462MHz)
[18947.324734] ath5k phy0: noise floor calibration timeout (2462MHz)
[18951.630637] ath5k phy0: failed to wakeup the MAC Chip
[18951.630648] ath5k phy0: can't reset hardware (-5)
[18951.630654] phy0: failed to set freq to 2412 MHz for scan
[18951.669127] ath5k phy0: failed to wakeup the MAC Chip
[18951.669133] ath5k phy0: can't reset hardware (-5)
[18951.669139] phy0: failed to set freq to 2417 MHz for scan
[18951.707599] ath5k phy0: failed to wakeup the MAC Chip
[18951.707605] ath5k phy0: can't reset hardware (-5)
[18951.707611] phy0: failed to set freq to 2422 MHz for scan
[18951.746077] ath5k phy0: failed to wakeup the MAC Chip
[18951.746084] ath5k phy0: can't reset hardware (-5)
[18951.746089] phy0: failed to set freq to 2427 MHz for scan
[18951.784550] ath5k phy0: failed to wakeup the MAC Chip
[18951.784557] phy0: failed to set freq to 2432 MHz for scan
[18951.823032] phy0: failed to set freq to 2437 MHz for scan
[18951.861515] phy0: failed to set freq to 2442 MHz for scan
[18951.900048] phy0: failed to set freq to 2447 MHz for scan
[18951.938599] phy0: failed to set freq to 2452 MHz for scan
[18951.977115] phy0: failed to set freq to 2457 MHz for scan
[18952.015627] phy0: failed to set freq to 2462 MHz for scan
[18952.054090] phy0: failed to set freq to 2467 MHz for scan
[18952.092572] phy0: failed to set freq to 2472 MHz for scan
[18952.131036] phy0: failed to set freq to 2484 MHz for scan
[18952.169519] phy0: failed to restore operational channel after scan
[18958.325333] __ratelimit: 21 callbacks suppressed
[18958.325341] ath5k phy0: noise floor calibration timeout (2462MHz)
[18969.324202] ath5k phy0: noise floor calibration timeout (2462MHz)
[18980.324151] ath5k phy0: noise floor calibration timeout (2462MHz)
[18991.324139] ath5k phy0: noise floor calibration timeout (2462MHz)
[19002.324834] ath5k phy0: noise floor calibration timeout (2462MHz)
[19013.323395] ath5k phy0: noise floor calibration timeout (2462MHz)
[19024.325083] ath5k phy0: noise floor calibration timeout (2462MHz)
[19035.324376] ath5k phy0: noise floor calibration timeout (2462MHz)
[19046.324083] ath5k phy0: noise floor calibration timeout (2462MHz)
[19057.324083] ath5k phy0: noise floor calibration timeout (2462MHz)
[19068.321498] ath5k phy0: noise floor calibration timeout (2462MHz)
[19071.630633] ath5k phy0: failed to wakeup the MAC Chip
[19071.630644] ath5k phy0: can't reset hardware (-5)
[19071.630651] phy0: failed to set freq to 2412 MHz for scan
[19071.669116] ath5k phy0: failed to wakeup the MAC Chip
[19071.669123] ath5k phy0: can't reset hardware (-5)
[19071.669128] phy0: failed to set freq to 2417 MHz for scan
[19071.707627] ath5k phy0: failed to wakeup the MAC Chip
[19071.707634] ath5k phy0: can't reset hardware (-5)
[19071.707639] phy0: failed to set freq to 2422 MHz for scan
[19071.746226] ath5k phy0: failed to wakeup the MAC Chip
[19071.746234] ath5k phy0: can't reset hardware (-5)
[19071.746239] phy0: failed to set freq to 2427 MHz for scan
[19071.784748] ath5k phy0: failed to wakeup the MAC Chip
[19071.784755] phy0: failed to set freq to 2432 MHz for scan
[19071.823275] phy0: failed to set freq to 2437 MHz for scan
[19071.861807] phy0: failed to set freq to 2442 MHz for scan
[19071.900216] phy0: failed to set freq to 2447 MHz for scan
[19071.938667] phy0: failed to set freq to 2452 MHz for scan
[19071.977084] phy0: failed to set freq to 2457 MHz for scan
[19072.015547] phy0: failed to set freq to 2462 MHz for scan
[19072.054127] phy0: failed to set freq to 2467 MHz for scan
[19072.092628] phy0: failed to set freq to 2472 MHz for scan
[19072.131151] phy0: failed to set freq to 2484 MHz for scan
[19072.169680] phy0: failed to restore operational channel after scan
[19079.324217] __ratelimit: 21 callbacks suppressed
[19079.324225] ath5k phy0: noise floor calibration timeout (2462MHz)
[19090.323851] ath5k phy0: noise floor calibration timeout (2462MHz)
[19101.323024] ath5k phy0: noise floor calibration timeout (2462MHz)
[19112.324269] ath5k phy0: noise floor calibration timeout (2462MHz)

---

### Post by bubbhasdance on 2009-06-18
I was able to access the router page on my laptop, I am going to try out the 128-bit key as soon as I remember the password for the settings (I have it written down in my file cabinet). If this works I will let you all know.

I did try rebooting but nothing occurred. I am pretty convinced that the culprit is the 128bit code that I am missing.

---

### Post by sandy8925 on 2009-06-18
Well looking at the dmesg output it looks like your wireless card is unable to scan for networks on any of the channels. Looks like it could be a driver problem or hardware problem.Or there's too much noise or something. I don't really have any idea. If you have any other OS installed check and see if it is working there. Or try reinstalling the driver (if possible).

---

### Post by bubbhasdance on 2009-06-18
I finally got the wireless network to connect, I had to reset the router, install the software again, and reboot the computer. All seems to work now, thanks so much for everyone's help!

---

### Post by ashwyn on 2009-06-30
Hi All,

I have noticed what I believe to be the same bug.

I have an MSI VR321 laptop (full of horrible via chips :( ) with Atheros AR242x wifi.  I am running Ubuntu 9.04. Every time I start up the computer the wifi works, however if the connection drops out, sometimes it will refuse to connect to any other networks.  NM shows them, but iwlist scan from the terminal always yeilds no scan results.

At the beginning of the disconnected period, dmesg shows:
ath5k phy0: unsupported jumbo
ath5k phy0: unsupported jumbo

then repeatedly:
ath5k phy0: failed to wakeup MAC Chip
ath5k phy0: cant' reset the hardware (-5)
ath5k phy0: failed to wakeup MAC Chip
ath5k phy0: cant' reset the hardware (-5)
ath5k phy0: failed to wakeup MAC Chip
ath5k phy0: cant' reset the hardware (-5)
...

then occasionally:
ath5k phy0: noise floor calibration timeout (2437MHz)

I have tried restarting the network services with /etc/init.d/networking restart, but this does not fix it.

When I then restart the computer, everything is back to normal.  I did not notice this bug before upgrading to jaunty, however it is the sort of thing that you don't always notice.

I have seen people reporting similar bugs on the kernel discussion list, leading me to think that it is a kernel bug? 

The bug exists in a more severe form (the wifi stops working more frequently) on Fedora 11 using the 2.6.29 kernel, and not in puppy linux, using the 2.6.25.16 kernel.

Please let me know if I should provide more info.  I am very keen to get this fixed!
Any help would be appreciated

---

