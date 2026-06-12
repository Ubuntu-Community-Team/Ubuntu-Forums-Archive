---
title: "HowTo: Get your Verizon Wireless PC5740 working."
date: 2006-07-27
forum: Networking &amp; Wireless
---

### Post by jdseek on 2006-07-27
First, a word of caution. I am a noob, I found this info by trial and error (more error).  Credit must be given where credit is due, and it it wasn't for [this website]("http://kenkinder.com/evdo-pc5740/"), I would still be banging my head against the wall.

Here is how I got my PC5740 to work, your milage may vary.

This howto assumes you are running ubuntu 6.06

A word of caution.  If you are using the liveCD you will lose your changes on reboot unless you copy them elsewhere.  (a USB thumbdrive makes a handy dandy file holder)
Also, liveCD users take heed.  You should not be connected to the internet via your PC5740 while installing to your hard drive.  If you do, your install will get to 84% and hang while trying to locate the update mirrors.  Not sure what the issue is with it, but I am told it is a known bug.
And yes, this method worked for me in both the liveCD and the HDD install.


Step One BEFORE YOU INSERT THE CARD!
This verifies your vendor and product codes

```
cat /proc/bus/usb/devices > devices
```

Insert the card now.

Then

```
diff /proc/bus/usb/devices devices | grep Vendor

< P: Vendor=0000 ProdID=0000 Rev= 2.06 
< P: Vendor=0000 ProdID=0000 Rev= 2.06 
< P: Vendor=106c ProdID=3701 Rev=0.00
```


In my case the vendor code is 106c and the product ID is 3701
If your numbers are different, replace these with yours in the next step.

The next step may not be nessicary, but we will do it anyway to make sure.
Hey, it worked for me.

```
sudo modprobe usbserial vendor=0x106c product=0x3701
```


Now check for your new device by typing:

```
ls /dev/ttyACM0

 /dev/ttyACM0
```



If your device is presnt then lets go configure that thing to get online!

Next we must write (or modify) the wvdial configuration, first make a backup of your old one

```
sudo cp /etc/wvdial.conf /etc/wvdial.conf.backup
```

then we start the editor by

```
sudo nano -w /etc/wvdial.conf
```

Copy and paste this into the file
IMPORTANT!
MAKE SURE YOU REPLACE <your-phone-number-here>with your access card's phone number!

```
[Dialer Defaults] 
Stupid Mode = on 
Modem = /dev/ttyACM0 
Baud = 921600 
Init = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
Phone = #777 
Username = <your-phone-number-here>@vzw3g.com 
Password = vzw 
Init1 = ATZ 
ISDN = 0 
Modem Type = Analog Modem 
Auto Reconnect = on 
Carrier Check = no 

[Dialer shh] 
Init3 = ATM0 

[Dialer pulse] 
Dial Command = ATDP
```


then save your work and exit by

```
<ctrl+x> 
y 
<enter>
```



Now we're ready to try our new connection out.

```
sudo wvdial
```


[note:install only, it may ask for a password, enter it to continue]

If that gets you going, but you drop the connection alot, try this, if not, I say, if it ain't broke, don't fix it.

Warning, the next step still needs some tweaking. I used this to avoid dropping the connection while updating.

```
sudo cp /etc/ppp/peers/wvdial /etc/ppp/peers/wvdial.backup 
```
```
sudo nano -w /etc/ppp/peers/wvdial
```

copy and paste these 2 lines onto the end of the file

```
lcp-echo-failure 65535 
lcp-echo-interval 65535
```

The whole file should look like this

```
noauth
name wvdial
usepeerdns
lcp-echo-failure 65535
lcp-echo-interval 65535
```

Again, save your work and exit by:

```
<ctrl-x>
y
<enter>
```

Attempt to start the connection again.

```
sudo wvdial
```


Please note, to terminate the connection, make sure the terminal window is active, then hit:

```
<ctrl+c>
```

Feel free to improve on this, I am still a noob and could probably use the insight.  Specificly, if there is a way to automate connecting for non-sudo users, I would be interested to know.  I would like to let my wife and kids on the internet, but don't want to give them sudo powers.

Good luck and happy interneting. I really enjoy my access card now that it works in ubuntu.

JD

---

### Post by rockingmtranch on 2007-04-10
Thanks for posting your results. I have to assume you are on a laptop. I have been using this same card in a desktop for a while now and Kenkinder.com helped me also. Here is what is working for me at present:

I do the modprobes and get a file called /dev/ttyACM0.

My ppp script: /etc/ppp/peers/1xevdo

ttyACM0
9600
debug
noauth
defaultroute
usepeerdns
connect-delay 10000
user [email]xxxxxxxxxx@vzw3g.com[/email]
show-password
crtscts
lock
lcp-echo-failure 4
lcp-echo-failure 65535
connect '/usr/sbin/chat -v -t3 -f /etc/ppp/peers/1xevdo_chat'

My chat script: /etc/ppp/peers/1xevdo_chat

# AT$QCMIPGETP  "login" name used for MobilIP, which usually matches your MIN.
# AT+GSN        ESN in hex
# AT+GMR        firmware revision and build date.
# AT+CSQ        first number indicates the signal strength above -109 dBm (in
#               2 dBm increments). A value of 7 or higher (-95 dBm) can be
#               considered adequate. 31 is the max. (Possible values in
#               Audiovox PC5740 are 0, 7, 15, 23, 31.)
# AT+CDV=*22899 Update PRL.  at+cdv=*22899 | OK | Lost carrier.
ABORT 'NO CARRIER' ABORT ERROR ABORT 'NO DIALTONE' ABORT BUSY ABORT 'NO ANSWER'
TIMEOUT 30
'' AT OK AT+CSQ OK ATDT#777 CONNECT

In terminal, I type pppd call 1xevdo then hit enter.
Then, tail -f /var/log/messages to see the output.

This gives me download speeds around 200 kbps most of the time and no disconnects. Not real consistent (30 to 230) but I'm happy with it.

---

### Post by loxety on 2007-06-20
this link explains how I got the card working on my laptop [http://ubuntuforums.org/showthread.php?t=336695&highlight=5740](http://ubuntuforums.org/showthread.php?t=336695&highlight=5740)

---

### Post by andreikin on 2008-04-23
Hi.
followed your instruction to the dot. thank you. 
About the speed, it depends on your location only.
i am getting 762 down and 99 up, according to speedtest.net
Thanks again.

---

### Post by Jaxl on 2008-06-24
[http://ubuntuforums.org/showthread.php?t=838891&highlight=1xevdo](http://ubuntuforums.org/showthread.php?t=838891&highlight=1xevdo)

---

