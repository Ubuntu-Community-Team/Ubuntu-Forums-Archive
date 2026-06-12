---
title: "Bluetooth pairing denied!"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by nishoe on 2007-08-08
I have been trying to pair my nokia 7370 with my laptop having a toshiba bluetooth device and running Ubuntu 7.04. 

I have followed all the steps of [https://help.ubuntu.com/community/BluetoothDialup](https://help.ubuntu.com/community/BluetoothDialup) documentation. I get to the point where I type pon BluetoothDialup and then my phone prompts me to enter the passkey following which the phone says pairing denied.

I had the same problem a few days back and I somehow managed to get it working (though I don't remember how).  Then I paired the phone with my windows xp following which I can't get paired to Ubuntu. I use my mobile to get online so cannot download the applications mentioned in many threads.
Here is what the var/log/syslog says

Aug  8 15:15:49 nazma-laptop pppd[17163]: pppd 2.4.4 started by nazma, uid 1000
Aug  8 15:15:59 nazma-laptop hcid[15257]: pin_code_request (sba=00:02:C7:65:C2:07, dba=00:15:DE:FA:5B:E9)
Aug  8 15:16:01 nazma-laptop pppd[17163]: Failed to open /dev/rfcomm0: Connection refused
Aug  8 15:16:01 nazma-laptop pppd[17163]: Exit.

Any help would be appreciated.
Thanks

---

### Post by ruibernardo on 2007-08-08
Hi Nishoe,

I think you have to add a pinhelper in your session.

Click on the Gnome menu in "System", "Preferences", "Sessions". Then click "New" and paste the following:

passkey-agent --default /usr/bin/bluez-pin

When asked, put an identical PIN on the phone and on Gnome. You might have to install the "bluez-pin" package (I don't remenber if it's allready installed or not).

---

### Post by nishoe on 2007-08-08
I don't think Ubuntu feisty requires bluez-pin as restarting the bluetooth device does not work with:
sudo /etc/init.d/bluez-utils restart

but works with:
sudo /etc/init.d/bluetooth restart

Am I right here?

---

### Post by wieman01 on 2007-08-08
You might have the same problem as I used to... Solution is posted here:

[http://ubuntuforums.org/showthread.php?t=486087]("http://ubuntuforums.org/showthread.php?t=486087")

---

### Post by ruibernardo on 2007-08-08
It's not bluez-utils, it is bluez-pin.

Anyway I think Feisty has it allready installed. You might have to restart the session and/or the computer to make it work.

---

