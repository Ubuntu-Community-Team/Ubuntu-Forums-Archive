---
title: "Bluetooth In Edgy (Kubuntu) Still Not Pairing"
date: 2006-12-09
forum: Networking &amp; Wireless
---

### Post by WirelessMike on 2006-12-09
I noticed this was an issue while Edgy was still in development.  How is it still a problem?

I've looked at multiple threads regarding this issue and nothing has helped.  My bluetooth phone is detected by kbluetoothd, but will not connect or pair.  I've checked and rechecked settings in /etc/bluetooth/hcid.conf and no adding of PIN helper config (which wasn't there at all originally), nor changing/updating default PIN passkey helps.

Apt-get says I have bluez-utils installed, but guess what?  There is no bluez-utils restart utitilies in /etc/init.d

There is a bluetooth command there, though.  I have to assume that has taken its place, but restarting doesn't help, anyway, so what difference does it make?

I have finally got the kbluetoothd icon to show up in the taskbar, but it appears to be fairly useless except to show me alot of settings for options I don't appear to have.

Is this an issue for anyone else on Edgy?  Has it been addressed?  I know there's no equipment issue, as I can get everything to work in Windows (thankfully, I had the forethought to dual-boot).

Any clues are appreciated!

---

### Post by ronniet on 2006-12-09
I know that when I was banging my head against a brick wall with Bluetooth it was actually my own fault...

I went to my mobile phone and turned on Bluetooth. Thing is; I didn't know the phone had an option to turn on/off incoming connections. This was turned off. Turned it on and all was good...

Maybe thats whats screwing up your bluetooth transfers??

---

### Post by WirelessMike on 2006-12-09
I wish that's all it was.

Thanx, though, for the suggestion. :)

---

### Post by WirelessMike on 2006-12-09
*bump*

---

### Post by n00buntu NJ on 2006-12-10
this might be too easy to be the fix to your problem, but I also had some trouble with bluetooth (in Gnome though), and I eventually found that I needed to install bluez-passkey-gnome which handles the actual passkey prompt for Bluetooth pairing.

Like I said, this is probably way too simple to be the answer to your question, but I thought I'd throw it out there...

Good luck...

---

### Post by WirelessMike on 2006-12-11
Even though I believe your suggestion may help, I really didn't want to add a bunch of gnome support to my kubuntu install.

Instead, I believe I'm going to upgrade to Dapper Drake.  I know that doesn't sound right, but it's accurate.  On Dapper Drake, my usb card reader worked (flash memory), bluetooth worked, and kde actually looked better.  In retrospect, I'm truly sorry I installed Edgy over it and wish I had made an image of my install before going to Edgy.

Regardless, everything simply worked in Dapper.  The same cannot be said of Edgy.  Things that worked in Dapper don't work now in Edgy, and those that do still work were better and more reliable in Dapper.  Edgy is no upgrade.

Thanx for the suggestions, though, all!

---

### Post by kirenpillay on 2007-04-12
Hi

I agree totally, stuff worked in the previous version but not in this version (Edgy). This was a poor release, and there seems to be inadequate support. I've tried almost everything mentioned in the forum to fix this problem, and nothing came right.

I there was something wrong with bluetooth, I still believe a howto should have been written by the developers to detail how to sort the problem out. Just poor cricket.

---

