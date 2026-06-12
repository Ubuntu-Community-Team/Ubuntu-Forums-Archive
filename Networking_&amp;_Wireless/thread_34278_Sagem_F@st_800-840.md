---
title: "Sagem F@st 800-840"
date: 2005-05-14
forum: Networking &amp; Wireless
---

### Post by r3sp4wn on 2005-05-14
I have the ADSL connector plugged in and everything, the USB is on... but I can't get it to just connect to my Tiscali UK account and it just won't install the ADSL connector. Please help me as I need it to use Ubuntu, Internet is vital :(.

Edit: Okay, so maybe I'm impatient, but this is a big problem and if it was fixed I would happily use Ubuntu. Please?

---

### Post by r3sp4wn on 2005-05-14
[QUOTE=r3sp4wn]I have the ADSL connector plugged in and everything, the USB is on... but I can't get it to just connect to my Tiscali UK account and it just won't install the ADSL connector. Please help me as I need it to use Ubuntu, Internet is vital :(.[/QUOTE]
 Okay, so maybe I'm impatient, but this is a big problem and if it was fixed I would happily use Ubuntu. Please?

---

### Post by zxc on 2005-05-14
You need to eagleusb drivers from a debian repository.

Edit: It's possible to get it to work. I've done it but I can't really remember how as I was basically stepped through it. Basically you'll need to find it on the online debian repository on your Windows box? or whatever you're using at the moment. It's all the "Eagleusb" stuff you need as this supports the modem. Someone should know a link to these online repositories. Then just transfer them to your ubuntu partition and ask someone to help you set it up.

---

### Post by r3sp4wn on 2005-05-14
[QUOTE=zxc]You need to eagleusb drivers from a debian repository.

Edit: It's possible to get it to work. I've done it but I can't really remember how as I was basically stepped through it. Basically you'll need to find it on the online debian repository on your Windows box? or whatever you're using at the moment. It's all the "Eagleusb" stuff you need as this supports the modem. Someone should know a link to these online repositories. Then just transfer them to your ubuntu partition and ask someone to help you set it up.[/QUOTE]
 Meh, the USB part works fine, as shown by the light indicator, but the connectivity light is not on.

---

### Post by zxc on 2005-05-14
Oh try in terminal:

eaglectrl -d

(then wait, it will send driver information to your modem) your modem light should flash for about 20-30 seconds then stay on.

then type: sudo startadsl


and it should connect considering all your options have been entered correctly. If this doesn't work type in terminal:

eaglestat

and copy what it says about the modem.


and Good luck, I know how frustrating it can be  :neutral:

---

### Post by r3sp4wn on 2005-05-14
[QUOTE=zxc]Oh try in terminal:

eaglectrl -d

(then wait, it will send driver information to your modem) your modem light should flash for about 20-30 seconds then stay on.

then type: sudo startadsl


and it should connect considering all your options have been entered correctly. If this doesn't work type in terminal:

eaglestat

and copy what it says about the modem.


and Good luck, I know how frustrating it can be  :neutral:[/QUOTE]
Huh. Too late, I uninstalled ubuntu before installing windows... i cant do that then uninstall ubuntu and reinstall windows just to tell you that. =/

---

### Post by zxc on 2005-05-14
Erm. Ok. Thought it was still a problem.  :neutral:

---

### Post by r3sp4wn on 2005-05-14
It is, I want Ubuntu to work.

---

### Post by r3sp4wn on 2005-05-15
I would have thought someone would have replied in the night...

I need this info so...


...
bump

---

### Post by r3sp4wn on 2005-05-17
[QUOTE=r3sp4wn]I would have thought someone would have replied in the night...

I need this info so...


...
bump[/QUOTE]
 Help please?

---

### Post by r3sp4wn on 2005-05-19
[QUOTE=r3sp4wn]Help please?[/QUOTE]
 bump.

---

### Post by r3sp4wn on 2005-05-27
[QUOTE=r3sp4wn]bump.[/QUOTE]
 People hate me

BUMP

---

### Post by N'Jal on 2005-05-27
I'm sorry but i have this modem and never got it working properly, even under windows it was rather bad, i simply bought a alcatel speedtouch modem and use that, it's simple enough, i can help you with that modem.

Personnaly Tiscali modems are rather crap, est advice get a new one

---

### Post by sheepdog on 2005-05-27
[QUOTE=N'Jal]I'm sorry but i have this modem and never got it working properly, even under windows it was rather bad, i simply bought a alcatel speedtouch modem and use that, it's simple enough, i can help you with that modem.

Personnaly Tiscali modems are rather crap, est advice get a new one[/QUOTE]

Sorry I have to disagree there. I've never had any problems getting Sagem modem to work with any distro. Here's how I got it to work with Ubuntu.

Copy this code to a file called eagle-usb

 ```

#!/bin/bash
# eagle-usb
# Start/Stop ADSL connection for Sagem F@st 800 USB modem.

. /lib/lsb/init-functions
. /etc/eagle-usb/scripts/setvars

check_end_msg() {[indent]if [ "$?" == "0" ]; then[indent]log_end_msg 0
  [/indent]else[indent]log_end_msg 1
  [/indent]fi
[/indent]}

load_dsp_code() {[indent]     log_begin_msg "Loading DSP code for USB modem..."
     eaglectrl -d > /dev/null 2>&1
     check_end_msg
  
     log_begin_msg "Waiting for modem to synchronize..."
     eaglectrl -s
     check_end_msg
[/indent]}

case "$1" in[indent]     start)
[/indent][indent][indent]         load_dsp_code
         log_begin_msg "Starting ADSL connection..."
         touch $SYSCONF_FILE
         fctStartAdsl
         check_end_msg
    
         log_begin_msg "Checking connection, pinging www.ubuntulinux.org..."
         ping -c 5 [www.ubuntulinux.org]("http://www.ubuntulinux.org") > /dev/null 2>&1
         check_end_msg
         ;;
  [/indent]stop)
[/indent][indent][indent]         log_begin_msg "Stopping ADSL connection..."
         rm -f $SYSCONF_FILE
         fctStopAdsl
         check_end_msg
         ;;
  [/indent][/indent][indent]     status)
[/indent][indent][indent]         eaglestat
         ;;
  [/indent][/indent][indent]     restart|force-reload)
[/indent][indent][indent]         $0 stop
         $0 start
          ;;
  [/indent][/indent][indent]     reload)
[/indent][indent][indent]          $0 start
          ;;
  [/indent][/indent][indent]     *)
[/indent][indent][indent]          echo "Usage: eagle-usb {start|stop|status|restart|force-reload|reload}"
          exit 1
  [/indent][/indent]esac

exit 0

```

Now, how to get this to work:

After installing and configuring the eagle-usb deb packages backup the original eagle-usb script installed by them in /etc/init.d

As root do the following:
1. Copy the eagle-usb file you just made from the above script to /etc/init.d

2. Give it the following permissions:
    Owner & Group are root
    Read      = Owner, Group, Others.
    Write      = Owner.
    Execute = Owner, Group, Others.

3. Create a symlink in /etc/rcS.d with a name like S41eagle-usb
    ln -s /etc/init.d/eagle-usb /etc/rcS.d/S41eagle-usb

4. You may need to edit /etc/ppp/peers/adsl to add your ISP login name to the user "" line so it reads:
    user "my.name@tiscali.co.uk"

5. You may need to edit /etc/ppp/chap-secrets and/or /etc/ppp/pap-secrets and add your ISP login name and password so yo have a line that reads:
    "my.name@tiscali.co.uk" * "mypassword" *

6. You may need to edit /etc/ppp/resolv.conf to add your ISPs DNS settings. For Tiscali add:
    nameserver 212.74.112.77
    nameserver 212.74.112.78

7. Test that the script starts/stops the connection run from Applications->System Tools->Root terminal try: (sudoing these won't work)
/etc/init.d/eagle-usb start
    and
    /etc/init.d/eagle-usb stop

If all goes well this script will start the connection when booting/rebooting and stop the connection when shutting down . If you wan't to stop/start the connection manually:
sudo stopadsl
sudo startadsl

*Note* The name SXXeagle-usb may need to be changed depending on what files are in /etc/rcS.d (I named it so it would run after the SXXnetworking script).

This setup works for me, hopefully it will for you. Once you have it working you can forget about starting and stopping the connection, it's all done for you.

Good luck.

---

### Post by KindredHyperion on 2007-05-24
I have also got this working. After faffing around with ueagle stuff, I found it was actually fairly simple just to use the eagle-usb driver. Just as long as the kernel headers are present it works fine. I wrote about it here [http://www.bandstand.org.uk/~adamgray/fast800.html](http://www.bandstand.org.uk/~adamgray/fast800.html)

HTH

---

### Post by BobSchwarz on 2007-05-29
I read up on the site in the last post. When doing a ./configure, there is an error (can't make executable). I run as superuser. There are source headers present in my system. Because ./configure doesnt work, nothing else will.

What else do I need to do to get it to work?

ALso, when starting up, i get a LOT of i/o buffer errors on hdc1, what might this be?

---

### Post by SamiDelovely on 2007-10-15
i have no idea on what to do and it's weird cause the modem says it senses the PC AND that it's online it's just not GETTING online. ugh. help.

---

### Post by aleksa71 on 2008-06-10
> **r3sp4wn said:**
> bump.
help please ?

---

