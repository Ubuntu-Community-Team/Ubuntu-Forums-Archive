---
title: "How secured is my ubuntu wireless"
date: 2006-12-29
forum: Networking &amp; Wireless
---

### Post by sn0m on 2006-12-29
I just like to ask the experts here about my ubuntu wireless.
I had to downgrade me encryptin from wpa-psk to wep to connect my lap top, compaq pressario v5000 to my house wireless network.
the other think is that i've got mac filter on on my router settings.
As i do a lot of transactions online, such as ebay, or online shopping, how easy is to break my network and should i defer doing online business till ubuntu has sorted out this wap-psk support.
thnx
sn0m

---

### Post by jml on 2006-12-29
WEP plus MAC filtering is a pretty secure set-up, but not quite as good as WPA, since a MAC address can be spoofed.  But even WPA is not impenetrable if someone tries long enough.  I tend to be paranoid and use a wired connection for my business transactions, and a wireless connection for everything else.  Now someone can rightly say that even that has risks if the vendor you are shopping at gets their servers hacked.

You can set up WPA encryption in Ubuntu.  First I would recommend upgrading to 6.10 if you are not on that version yet.  It seems to handle wireless better than earlier versions.  Then download and install network-manager and network-manager-gnome.  Once that application is up and running, you can use WPA encryption.  It also makes switching between available wireless networks a bit easier.  If you search this subforum and the wiki for the terms network-manager, you should be able to find several posts to help you out.  

When you are ready to switch over, I would disable all encryption and filtering temporarily to ensure that you get the initial configuration right.  Then add back WPA encryption and If you want, then add the MAC filtering.  Good luck.

Joe

---

### Post by sn0m on 2006-12-30
Hi Joe
I downloade ntwork-manager and network- gnome-manager and installed them with synaptic package.
Trouble is that i cannot find them anywhere, either under applications, or systems.
Me being a beginer get stuck soon.
could you help me with it pls.
thnx
Koli

---

### Post by c.dric on 2006-12-30
i used this [How-to]("http://ubuntuforums.org/showthread.php?t=318539") and it worked fine on my computers. I didn't use any network manager.

[Here is another How-to]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo") that explains how-to use WPA with network-manager.

I hope this will help you.

---

### Post by sn0m on 2006-12-30
Hi
I have managed to get connection with WPA encryption by using some other guidance fished out by google ( this is the link: [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)).
The problem is that each time i turn the lap top on, when the NetworkManager applet 0.6.3 i think would like the password which is stored at the keyring manager to connect to the wireless network, 
once the password is stored in the keying manager it connects for the session but when a reboot is done it will not connect unless you delete the passphrase from the keying manager.
but the connecion will work manually if you deny keying manager to store the passphrase and do it manually all the time.

---

### Post by jml on 2006-12-30
sn0m, the problem you describe with the password/keyring is a known issue with the applet.  I think that someone is working on a fix, but until they do, I am doing the same thing you are doing.  Typing in the password whenever I reboot/restart my computer.  Glad you got it working.   Have a happy new year.  Boy, I need to learn to type better.  :-)

Joe

---

### Post by sn0m on 2006-12-31
happy new year to u mate. I love my ubuntu, is fast, has got fantastic graphics, i can change the settings the way i like it and i am having fun exploring it. Ubuntu is letting me into places that the hated windows guards with one million keys. If i have to type the password each time I log on into my network, so be it,i will do any thing for my ubuntu...
As far as typing english correctly is concerned, mate english is not my native language, yesterday me and my brother were having a bit of wine as we were plying with it, but we managed to understand each other, and that is the question, can we 'ubuntu' each other, yes and thats the phylosophy. But i promised to pay attention next time and write a queens english....joking
Anyway happy new year and have a good one tonight buddy.
Koli:p

---

