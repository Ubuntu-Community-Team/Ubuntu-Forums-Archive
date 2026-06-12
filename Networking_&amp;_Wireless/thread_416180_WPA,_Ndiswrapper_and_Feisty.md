---
title: "WPA, Ndiswrapper and Feisty"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by sefs on 2007-04-20
Can some kind so give me concise instrutions to get  WPA-Personal using AES back up and running now i have upgraded to feisty.

I am using ndiswrapper which i believes supports wpa.

I have followed some guides/how-tos but no cigar.

---

### Post by anarchron on 2007-04-20
I'm afraid you're out of luck for the time being. I can't seem to get mine to work using settings from Edgy.

---

### Post by anarchron on 2007-04-20
I'm afraid you're out of luck buddy. I can't get mine to work using settings from Edgy in Feisty.

---

### Post by sefs on 2007-04-20
Something seems to have changed between edgy and feisty.

I actually had to use to newest version of ndiswrapper 1.42 to even get ndiswrapper installed.  

So it something betweent the supplicant and the wrapper ... i really dunno.  frustrating.

---

### Post by mmatt on 2007-04-27
No luck with WPA for me either. Has worked with this card in other distros with ndiswrapper. Can connect unencrypted but not with WPA. These lines from daemon.log seem to hold a clue, but no idea how to solve the problem...

NetworkManager: <information>^Iwlan0: Device is fully-supported using driver 'ndiswrapper'.

NetworkManager: <information>^IActivation (wlan0/wireless): association took too long (>60s), failing activation.

along with some others about hexdumps, keys etc.

Hope someone figures this out soon.

---

### Post by mmatt on 2007-04-27
Success! Downloading the latest (1.42) ndiswrapper driver from source fixed my problem. I think this should be updated in the repositories, it appears to be a very common problem.

mmatt

---

### Post by belekas on 2007-04-27
broadcom airforceone 54g rev2 doesnt work on feistywith or without ndiswrapper, im using fujitsu-amilo notebook, the wifi led wont even come red as on windows, im in need of this working but i see that linux has very poor support for this card and it doesnt work at all, i tried like nnnz of howtoz and **** but still nothing. linux sees the device as eth1 but i cant scan and do anything, dont know what to do. i have it blacklisted and windows drivers installed, all setup like some advises and still nothing. anyone have a clue??? or any other linux edition that will support this card for real???

---

### Post by freak101 on 2007-05-02
> **belekas said:**
> broadcom airforceone 54g rev2 doesnt work on feistywith or without ndiswrapper, im using fujitsu-amilo notebook, the wifi led wont even come red as on windows, im in need of this working but i see that linux has very poor support for this card and it doesnt work at all, i tried like nnnz of howtoz and **** but still nothing. linux sees the device as eth1 but i cant scan and do anything, dont know what to do. i have it blacklisted and windows drivers installed, all setup like some advises and still nothing. anyone have a clue??? or any other linux edition that will support this card for real???
Some amilo uses software to turn on WLAN. You can try with acer_acpi, it worked for my amilo, take a look at this howto:
[http://ubuntuforums.org/showthread.php?t=224350&highlight=broadcom+wireless+acer_acpi](http://ubuntuforums.org/showthread.php?t=224350&highlight=broadcom+wireless+acer_acpi)

---

