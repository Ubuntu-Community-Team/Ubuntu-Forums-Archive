---
title: "Can't get Alcatel Speedtouch 330 USB modem working"
date: 2006-09-01
forum: Networking &amp; Wireless
---

### Post by tommyjb on 2006-09-01
I've followed the HOWTO at [http://www.ubuntuforums.org/showthread.php?t=44763](http://www.ubuntuforums.org/showthread.php?t=44763), but when I plug in my modem, I get the following (and nothing more):

> usb 3-2: new full speed USB device using ohci_hcd and address 3
usb 3-2: reset full speed USB device using ohci_hcd and address 3
speedtch 3-2:1.0: no stage 1 firmware found!

I'm using Ubuntu 6.06.1 LTS.  Could anyone please help? :(

---

### Post by tommyjb on 2006-09-01
After following the instructions on [this page](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html), that error message is no longer showing, but I still can't connect.  Now, the following is printed instead:
> speedtch 4-1:1.0: found stage 1 firmware speedtch-1.bin
speedtch 4-1:1.0: found stage 2 firmware speedtch-2.bin
The ADSL light should flash initially, but it never does—even if I take the telephone cord out.

Does anyone have any ideas?  I badly want to get on the 'net with Ubuntu.  :(

---

### Post by tommyjb on 2006-09-01
Woo-hoo!  I have it working!  I'm posting from Ubuntu now.  :D

---

### Post by Edgar on 2006-09-03
Hey, I'm following this guide [https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch](https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch) and it was all going quite nicely till I got to the part where I had to copy the secrets.txt to /etc/ppp.

The tutorial says that to do so I should type in the following:

sudo install -m 600 secrets /etc/ppp/chap-secrets &&
sudo install -m 600 secrets /etc/ppp/pap-secrets

So I typed in:

edgar@P42GHZ:~$ cd speedtouch
edgar@P42GHZ:~/speedtouch$ sudo install -m 600 secrets /etc/ppp/chap-secrets &&
> sudo install -m 600 secrets /etc/ppp/pap-secrets
install: cannot stat `secrets': No such file or directory

I also tryed copying the file from my home folder but I got the same 'install: cannot stat `secrets': No such file or directory'
message.

What do I do?

---

### Post by MRND on 2006-09-08
Hi Edgar there's an easy way to get the speedtouch modem working just enter this [link]("http://steve-parker.org/speedtouchconf/") and follow the instructions you should be connected in minutes. I used it in Xandros and now i'm connected in Ubuntu 6.06

---

