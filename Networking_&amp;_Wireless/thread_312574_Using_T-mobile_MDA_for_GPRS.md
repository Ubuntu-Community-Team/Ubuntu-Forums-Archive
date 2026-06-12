---
title: "Using T-mobile MDA for GPRS"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by dasoutham on 2006-12-04
Hello, this is my first post on this forum. I have installed Dapper Drake on an old Dell Inspiron 4000 laptop, which I am trying to get online with GPRS using a Bluetooth dongle and my T-mobile MDA.
From various pages on the Ubuntu community I have managed to find the T-mobile info, pair the devices and made the following files:

/etc/bluetooth/rfcomm.conf

	rfcomm0 {
	bind yes;
	device 00:**:**:**:**:**; (actual address goes in here!)
	channel 5;
	comment "MDA";
	}


/etc/ppp/peers/tmobile

	/dev/rfcomm0 115200
	connect '/usr/sbin/chat -v -f /etc/ppp/chat-gprs
	crtscts
	modem -detach
	noccp
	defaultroute
	usepeerdns
	noauth
	ipcp-accept-remote
	ipcp-accept-local
	noipdefault


/etc/ppp/chat-gprs

	" ATZ OK
	AT+CGDCONT=1,"IP","general.t-mobile.uk"
	OK "ATD*99***1#"
	CONNECT "

I am getting the following message:

	pppd: The remote system is required to authenticate itself
	pppd: but I couldn't find any suitable secret (password) for it to use to do so.

Questions !?!
Do I actually need to put in a password, and if so where and how? From one web page it appears that "pass" is a T-mobile password.
Or am I doing something completely wrong?

Any help would be gratefully received,
Dave

---

### Post by dasoutham on 2006-12-10
I have now got over this initial problem.

I had some problems with Gnome which I couldn't fix.
So I have installed Kubuntu as I understand KDE slightly better.
I have started again, using the procedure in:

[https://help.ubuntu.com/community/BluetoothDialup](https://help.ubuntu.com/community/BluetoothDialup)

This is _almost_ working!

I can dial and apparently get a connection as there are no error messages, and from ifcconfig it looks as though the connection is OK.

But what do I do next to get internet access from a terminal window?

---

### Post by dasoutham on 2006-12-10
Oops, I meant ifconfig not ifcconfig

---

### Post by christhemonkey on 2006-12-10
You could try:
```
pon tmobile 
```
And then look at the output of:
```
plog
```

---

### Post by dasoutham on 2006-12-10
Thanks christhemonkey,

Below I've listed the files I am now using (with the addresses etc. changed) and the log file


/etc/bluetooth/rfcomm.conf
rfcomm0 {
        bind yes;
        device your-phone-mac-address;
        channel 5;
        comment "Bluetooth PPP Connection";
}

/etc/ppp/peers/BluetoothDialup
debug
noauth
connect "/usr/sbin/chat -v -f /etc/chatscripts/BluetoothDialup"
usepeerdns
/dev/rfcomm0 115200
defaultroute
crtscts
lcp-echo-failure 0


/etc/chatscripts/BluetoothDialup
TIMEOUT 35
ECHO    ON
ABORT   '\nBUSY\r'
ABORT   '\nERROR\r'
ABORT   '\nNO ANSWER\r'
ABORT   '\nNO CARRIER\r'
ABORT   '\nNO DIALTONE\r'
ABORT   '\nRINGING\r\n\r\nRINGING\r'
''      \rAT
OK      'AT+CGDCONT=2,"IP","general.t-mobile.uk"'
OK      ATD*99***1#
CONNECT ""


dasoutham@dasoutham-laptop:~$ plog
Dec 10 21:42:52 dasoutham-laptop chat[4865]: abort on (\nNO ANSWER\r)
Dec 10 21:42:52 dasoutham-laptop chat[4865]: abort on (\nNO CARRIER\r)
Dec 10 21:42:52 dasoutham-laptop chat[4865]: abort on (\nNO DIALTONE\r)
Dec 10 21:42:52 dasoutham-laptop chat[4865]: abort on (\nRINGING\r\n\r\nRINGING\r)
Dec 10 21:42:52 dasoutham-laptop chat[4865]: send (^MAT^M)
Dec 10 21:42:52 dasoutham-laptop chat[4865]: expect (OK)
Dec 10 21:43:27 dasoutham-laptop chat[4865]: alarm
Dec 10 21:43:27 dasoutham-laptop chat[4865]: Failed
Dec 10 21:43:27 dasoutham-laptop pppd[4862]: Connect script failed
Dec 10 21:43:27 dasoutham-laptop pppd[4862]: Exit.


It looks as though it is not getting any response from the modem.
Any ideas anyone?

---

### Post by dasoutham on 2006-12-12
I've made some more progress.
Tried using kppp to connect. I can find the modem but I am getting "modem busy" response using both USB cable and Bluetooth.
So I've also tried using the MDA as a modem from my desktop computer with Windows XP, and also get "number busy".
Tried turning various bits of the MDA on and off but not sorted this bit yet!

---

### Post by dasoutham on 2006-12-12
And a bit more progress. Something sent me to look back into my MDA's documentation, I found I needed to install HTC USB Modem to get the MDA to connect from Windows. This worked! I have a cable connection.
I haven't quite worked out whether it is just a Windows driver or whether it has also installed something on the MDA.
So from IE via T-mobile on the MDA I did a search for "Linux HTC USB modem" and found this:

[http://andrewtv.org/fedora-ppc6700/](http://andrewtv.org/fedora-ppc6700/)

which I will explore tomorrow. Too knackered tonight and I have to get up for work tomorrow.

---

### Post by manny0 on 2006-12-16
any luck with this? i want to try this when i have some time. maybe later on today.

---

### Post by dasoutham on 2006-12-31
Not sorted it yet!

---

### Post by zir0n on 2008-02-24
Hi all,

I've been trying to get this MDA modem thing to work for a while now, gave up and just recently tried again. I followed the How To from ubuntuguide 

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Using_mobile_phone.2FGPRS.2FEDGE_as_Internet_modem](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Using_mobile_phone.2FGPRS.2FEDGE_as_Internet_modem)

I created those files and changed some of the lines so that the device is /dev/ttyUSB0 because its connected to the usb and changed the APN to wap.voicestream.com because thats what my phone has in that box in the modem link application. I also added a couple other options from other How To configurations. When I run the script it opens the chat window and I get this output:

> 
Feb 24 19:41:28 laptop chat[5650]: timeout set to 120 seconds
Feb 24 19:41:28 laptop chat[5650]: abort on (BUSY)
Feb 24 19:41:28 laptop chat[5650]: abort on (ERROR)
Feb 24 19:41:28 laptop chat[5650]: abort on (NO CARRIER)
Feb 24 19:41:28 laptop chat[5650]: send (ATE1^M)
Feb 24 19:41:28 laptop chat[5650]: expect (OK)
Feb 24 19:41:29 laptop chat[5650]: ATE1^M^M
Feb 24 19:41:29 laptop chat[5650]: OK
Feb 24 19:41:29 laptop chat[5650]:  -- got it 
Feb 24 19:41:29 laptop chat[5650]: send (AT+CGDCONT=1,"IP","wap.voicestream.com"^M)
Feb 24 19:41:29 laptop chat[5650]: expect (OK)
Feb 24 19:41:29 laptop chat[5650]: ^M
Feb 24 19:41:29 laptop chat[5650]: AT+CGDCONT=1,"IP","wap.voicestream.com"^M^M
Feb 24 19:41:29 laptop chat[5650]: OK
Feb 24 19:41:29 laptop chat[5650]:  -- got it 
Feb 24 19:41:29 laptop chat[5650]: send (ATD*99#^M)
Feb 24 19:41:29 laptop chat[5650]: expect (CONNECT)
Feb 24 19:41:29 laptop chat[5650]: ^M
Feb 24 19:41:30 laptop chat[5650]: ATD*99#^M^M
Feb 24 19:41:30 laptop chat[5650]: CONNECT
Feb 24 19:41:30 laptop chat[5650]:  -- got it 
Feb 24 19:41:30 laptop chat[5650]: send (\d)
Feb 24 19:41:31 laptop pppd[5645]: Serial connection established.
Feb 24 19:41:31 laptop pppd[5645]: Using interface ppp0
Feb 24 19:41:31 laptop pppd[5645]: Connect: ppp0 <--> /dev/ttyUSB0


it stops there and now I'm stuck. I'm soooo close that I can feel the internet streaming into my laptop from the cell towers.  From what I've seen other How To's do that are geared towards other phone models and providers, I'm suppose to get an IP at this point and then I should be able to get on the internet. Look at this Log from another How To guide:

[http://wiki.xda-developers.com/index.php?pagename=bluetoothnetworking](http://wiki.xda-developers.com/index.php?pagename=bluetoothnetworking)

I've also attached my files if that will help recreate the situation.
[LIST]
[*]gprs.sh should be renamed to gprs and moved to /usr/sbin/
[*]gprs_chat.txt should be renamed to gprs and moved to /etc/chatscripts/
[*]gprs_ppp.txt should be renamed to gprs and moved to /etc/ppp/peers/
[/LIST]
then just run /usr/sbin/gprs

---

### Post by bowsercake on 2008-03-01
I have been trying to get GPRS to work on my MDA for forever.

I am unsure what to do with the phone as well. Before I connect with the laptop, I open IE on the phone and let it connect to GPRS and then I run the program "modem link" and set connection: USB, Baud Rate:Unused, Access point name: wap.voicestream.com. and then I click activate.  After doing that I try connecting with the scripts given here and other ones before, but I cannot figure it out.

With the scripts on this page and once before I got it to connect, however, it cannot find an IP address and defaults to 10.*.*.* which designated a local address, so, obviously I am not connected to the internet and of course web pages on my laptop do not load.

I'll report back here if I get any updates.

---

### Post by bowsercake on 2008-03-24
I am posting this right now from my laptop using my Tmobile MDA as my internet connection. I am a US Tmobile customer. Previously I was using the $6.99 "Tmobile Web" addon plan using a proxy server for a connection. Now I signed up for the $20 "Tmobile Total Internet" add on to my plan.  THERE IS NO DIFFERENCE IN SPEED OR CONNECTION between these two plans. However, to get the cheaper plan you have to enter some well documented numbers into the proxy server connections settings, which is not a big deal.  However, I could not get to laptop to connect using that plan. If I knew how to set up the  proxy connection settings on my laptop ppp then it would probably work, but I don't know how to do that.  So, basically I am now paying $13 more just to get the internet to work on my laptop, oh well, I may cancel it and 'downgrade' again to the cheaper plan.

Here is how to do it.

On the MDA:
1. Make sure your MDA has the program "Model Link" installed on it. I think I needed to download it for my phone, but it may have been preinstalled on some.

2. Settings > Connections > Connections: make a new connections and name it anything. For "Select a Modem:" choose "Cellular Line (GPRS)".  For "Access point name:" choose "wap.voicestream.com".  For User name, password, and domain, just leave them blank. Then finish.

On the laptop:
3. open the terminal and do a "sudo nano /etc/ppp/peers/gprs
```
/dev/ttyUSB0 115200
connect '/usr/sbin/chat -v -f /etc/ppp/chat-gprs'
crtscts
modem -detach
noccp
defaultroute
usepeerdns
noauth
ipcp-accept-remote
ipcp-accept-local
noipdefault

```

4. then do "sudo nano /etc/ooo/chat-gprs"
```
'' ATZ OK
AT+CGDCONT=1,"IP","wap.voicestream.com"
OK "ATD*99#"
CONNECT ''

```
Note that this will be different for other users, this works for tmobile users in the United States.

On the MDA:
5. open Modem Link and set "Connection" to "USB" and "Access point name" to "wap.voicestream.com".  Then click activate.

6. Open the WM5 Internet Explorer and it will make a GPRS connection and open up your homepage on the MDA.

On the Laptop:
7. type the command "pon gprs" and check for errors. Mine looks like this when it was successful:
```
chris@chrisr50e:/etc/ppp$ pon gprs
Serial connection established.
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0
PAP authentication succeeded
Could not determine remote IP address: defaulting to 10.64.64.64
Cannot determine ethernet address for proxy ARP
local  IP address 10.173.38.131
remote IP address 10.64.64.64
primary   DNS address 66.94.9.120
secondary DNS address 66.94.25.120
LCP terminated by peer (M-O^A)
Connect time 9.9 minutes.
Sent 107885 bytes, received 917118 bytes.
Connection terminated.
Modem hangup

```

Not sure what it means by "Could not determine remote IP address: defaulting to 10.64.64.64" but it did work.

However, half way through writing this i lost connection and I had to do a "pon gprs" again as the connection was terminated. I know there is a option to put in the 'gprs' file to make it reconnect automatically. I will have to look into that.  Good luck. Hope this was helpful as I came into this project as a big noob and I have been lost for months, probably mostly due to my proxy settings.

---

### Post by zir0n on 2008-03-25
Thanks Bowsercake i'm glad you got it working. I followed your directions and I believe you meant
"4. then do "sudo nano /etc/ppp/chat-gprs""

instead of:
"4. then do "sudo nano /etc/ooo/chat-gprs""

Anyways, I ran into a problem after following the directions. After I typed "pon gprs" as a normal user I got the following...

```

user@laptop:/etc/ppp$ pon gprs
Serial connection established.
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0

```

It just stays there indefinitely. I'm not getting to the PAP Authentication part. Maybe other MDA people could try this out and see if they get the same results. As for the option in the gprs file to reconnect on disconnect I think it's "persist".

---

