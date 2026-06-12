---
title: "Need help with Kyocera KPC650"
date: 2005-07-27
forum: Networking &amp; Wireless
---

### Post by absolutefog on 2005-07-27
I am trying to use my Kyocera KPC650 Cellular Wireless Modem under Ubuntu however have ran into some real issues. 

If anyone has any suggestions to get this card to work under Ubuntu (or any other Linux distro for that matter) then by all means let me know as I could sure use the help.

---

### Post by ricardom on 2006-11-24
Hi,

I have the same hardware (KPC650), i use to connect here in Brazil to Vivo Telecom (Vivo Zap), after hours of reading, testing and coffees, here is what i did to make my kyocera works in Ubuntu (6.06).

#  rmmod usbserial ; modprobe usbserial vendor=0xc88 product=0x17da

(you should change vendor and product infos for your card, use lsusb to get those infos)

#  mknod /dev/ttyUSB0 c 188 0 ; mknod /dev/ttyUSB1 c 188 1

# pico /etc/ppp/peers/vivozap

(copy and past the text below, remember to change the line user to your user of your ISP.)

```

ttyUSB0 115200 crtscts
noauth
defaultroute
usepeerdns
local
ipcp-accept-local
ipcp-accept-remote
lcp-echo-failure 0
lcp-echo-interval 0
login
user 99999999@vivozap.com.br # mude para seu numero da vivo
password vivo
multilink
novj
novjccomp
noccp
persist
passive
connect '/usr/sbin/chat -v -f /etc/ppp/chat-vivozap'

```

#  pico /etc/ppp/chat-vivozap

(copy and paste the text below)

```


ABORT "NO CARRIER"
ABORT "NO DIALTONE"
ABORT "ERROR"
ABORT "NO ANSWER"
ABORT "BUSY"
ABORT "Username/Password Incorrect"
SAY "VIVO Zap inicializando...\n"
"" "ATZ"
OK "AT&C0+CRM=1"
OK "ATDT#777"


```

# echo "/usr/sbin/pppd call vivozap" > /usr/bin/vivozap

# chmod +x /usr/bin/vivozap


To make the connection just type in normal shell: vivozap.

Hope that helps you, and all others owners of this card.

---

### Post by Paulo Wageck on 2006-11-24
thanks mr. macari.

are you enjoying your new card???

---

### Post by ricardom on 2006-11-25
Yes Mr Wageck, im here using this card now. :)

Did you get your card to work in Linux?

---

### Post by Jim March on 2006-11-25
In case anybody else is wrestling with this, see my post here:

[http://ubuntuforums.org/showthread.php?t=157113](http://ubuntuforums.org/showthread.php?t=157113)

It's a weird but good solution involving hardware and zero drivers.

---

### Post by Paulo Wageck on 2006-11-27
Yes indeed. 
But I think the conection is quite instable because of the maxsize issue... maybe i should recompile my kernel!
Yours 2.5G is ok.. but here.. at 3G the connection gets dropped after a while....
Cheers!

---

