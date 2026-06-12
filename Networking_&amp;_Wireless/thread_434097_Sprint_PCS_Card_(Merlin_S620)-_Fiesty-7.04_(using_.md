---
title: "Sprint PCS Card (Merlin S620)- Fiesty-7.04 (using ppp dialer)"
date: 2007-05-05
forum: Networking &amp; Wireless
---

### Post by JoaoMachado on 2007-05-05
This is my first tutorial so bear with me... I am using Ubuntu 7.04 

I was able to use the graphical Gnome-PPP dialer to dial my Sprint PCS Card and want to share how I did it, just in case anyone does not want to have to keep a terminal window open while using their card.

A few things to note:

1. My Merlin S620 card was recognized automatically by the airprime drivers, if you install your card, open a terminal window and type "dmesg", you should see an output similar to this:

> [ 5766.974976] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[ 5766.975386] usbcore: registered new interface driver usbserial_generic
[ 5766.975393] drivers/usb/serial/usb-serial.c: USB Serial Driver core
[ 5766.986979] drivers/usb/serial/usb-serial.c: USB Serial support registered for airprime
[ 5766.987470] airprime 6-1:1.0: airprime converter detected
[ 5766.988070] usb 6-1: airprime converter now attached to ttyUSB0
[ 5766.988598] usb 6-1: airprime converter now attached to ttyUSB1
[ 5766.989109] usb 6-1: airprime converter now attached to ttyUSB2
[ 5766.989419] airprime 6-1:1.1: airprime converter detected
[ 5766.990888] usb 6-1: airprime converter now attached to ttyUSB3
[ 5766.992893] usb 6-1: airprime converter now attached to ttyUSB4
[ 5766.993522] usb 6-1: airprime converter now attached to ttyUSB5
[ 5766.993799] usbcore: registered new interface driver airprime


Next, install gnome-ppp; either using synaptic or apt-get.
For apt-get, open a terminal window and type the following:
> sudo apt-get install gnome-ppp


Next, we need to add or change the ppp0 file in /etc/ppp/peers/, 
you may already have a file named ppp0 and it may be empty, 
at any rate, just back it up and create a new file called ppp0.
You must have root priviledges to do so, just use Nautilus in SU mode:

> sudo nautilus

Once you have the file created, copy the following into to the file,
you will have to change the XXXXXXXXXX to your 10 digit phone number.
> #the USB serial device of the EVDO PCMCIA card.
/dev/ttyUSB0
#your login information
user [email]xxxxxxxxxx@sprintpcs.com[/email]
921600 # speed
#debug
defaultroute # use the cellular network for the default route
usepeerdns # use the DNS servers from the remote network
-detach # keep pppd in the foreground
crtscts # hardware flow control
lock # lock the serial port
noauth # don't expect the modem to authenticate itself
connect "/usr/sbin/chat -v -f /etc/ppp/peers/sprint-connect"
disconnect "/usr/sbin/chat -v -f /etc/ppp/peers/sprint-disconnect" 
lcp-echo-failure 0

Now create another file in the same directory called "sprint-connect"
and add the following:
> SAY 'Starting Sprint\n'
TIMEOUT 120
ABORT 'BUSY'
ABORT 'NO ANSWER'
ABORT 'NO CARRIER'
'' 'ATZ'
'OK' 'AT&F0'
'OK' 'ATE0v1'
'' 'AT+CSQ'
'OK' 'ATDT#777'
'CONNECT' 

Then create one more file in the same directory called "sprint-disconnect"
and add the following:
> "" "\K"
"" "+++ATH0"
SAY "Disconnected from Sprint." 

Now, start Gnome-pppp from Applications>Internet>GNOME PPP;
Now, click on "Setup", under Device, change that to your USB device name, 
for instance, on my dmesg above, the first airprime device found was USB0, 
so I added the following 

_Under the Modem Tab_
Device: /dev/ttyUSB0
Type: USB MOdem
Speed: 460800
Phone Line: Pulse
Volume: Off

_Under the Networking Tab_ 
set the IP to Dynamic IP Address,
for DNS, use Automatic DNS

Under the Options tab
Check off;
Minimize  and Dock in Notification Area

**Close the set up window.**

Now, for Username, your user name should be already populated, if not 
add it, it is your 10 digit phone number followed by @sprintpcs.com
Your password is your four digit unlock code.

the phone number to dial is "#777" without the quotes.

Click Connect, and should be connected.

I used this post for the ppp0 connection files: [http://www.cs.drexel.edu/~kfu22/evdo/]("http://www.cs.drexel.edu/~kfu22/evdo/")

---

### Post by ebozzz on 2007-05-13
There's a great guide on the Sprint site that is actually based on Ubuntu. 

[http://www4.sprint.com/pcsbusiness/support/downloads/index.jsp?internalId=downloads](http://www4.sprint.com/pcsbusiness/support/downloads/index.jsp?internalId=downloads)

Select Linux and get the PDF file.

---

### Post by Yeormom on 2007-06-20
The Sprint guide works great. Nice find ebozzz.

---

### Post by ebozzz on 2007-06-20
> **Yeormom said:**
> The Sprint guide works great. Nice find ebozzz.

Glad to hear that it did and you're very welcome.

---

### Post by Bartender on 2007-07-25
Have any of you tried making the connection with an actual phone, not the card?  A friend has a Sanyo 7600 (I think) phone that he's using successfully in Windows.  I tried it with Ub 7.04, and it saw the phone but I couldn't get gnome-ppp to do the deed for me unless I set it to "stupid mode", then it cut me off after 2.5 minutes.  TYried seeral times, same results each time.
I used #777, and "web" for both username and password.  Read something on the internet about that being the correct entries (?)  Maybe the wrong username/password is why I kept getting cut off.

Here's the log from gnome-ppp with stupid mode on:

 Ignoring malformed input line: ";Do NOT edit this file by hand!"

--> WvDial: Internet dialer version 1.56

--> Cannot get information for serial port.

--> Initializing modem.

--> Sending: ATZ

ATZ

OK

--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

OK

--> Modem initialized.

--> Sending: ATM0L0DT#777

--> Waiting for carrier.

ATM0L0DT#777

CONNECT

--> Carrier detected.  Starting PPP immediately.

--> Starting pppd at Tue Jul 24 20:35:55 2007

--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied

--> --> PAP (Password Authentication Protocol) may be flaky.

--> Pid of pppd: 6613

--> Using interface ppp0

--> local  IP address 70.6.45.182

--> remote IP address 68.28.57.69

--> primary   DNS address 68.28.58.11

--> secondary DNS address 68.28.50.11

--> Connect time 2.6 minutes.

--> Disconnecting at Tue Jul 24 20:38:28 2007

--> The PPP daemon has died: Lack of LCP echo responses (exit code = 15)

--> man pppd explains pppd error codes in more detail.

--> I guess that's it for now, exiting

--> Provider is overloaded(often the case) or line problem.

--> The PPP daemon has died. (exit code = 15)

With stupid mode off it would get  to CONNECT, then wait for prompt which it never gets.   I'll look at that guide and see how much the cards cost.  That might be the better way for him to go anyway...

---

### Post by fredsmith11 on 2007-10-27
Thanks for the great guide from sprint.   I am about to use it to set up my card.  

BTW - here's a link to the inux version from the sprint site - 
[http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf](http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf)

---

### Post by wooby on 2007-10-31
Using 7.10 and posting using my Sprint EVDO card!  YEAH!  Mine was even easier than the guide.  I just plugged it in and did the KPPP config and it worked like a champ.  I have tried every other "guide" out there and despite the fact I am a CLI freak in Cisco I just don't have the time to learn another CLI, The picture is worth a thousand words and that sprint doc is full of screenshots so you know exactly what to expect.  Very happy to use my company provided evdo card on my Linux system!!  \\:D/

---

### Post by parthamage on 2007-11-26
I am using 7.10 with a Sprint Sierra 580.  Configured according to their nice help guide, but after being connected for approximately 30 seconds, I get the "The pppd daemon died unexpectedly!  Exit status 15" message.  The FAQ link in the error message is useless, and I can't get anything from the helps.  I actually get all the way to the Internet, and can start surfing, but it always dies after less than a minute.

I am still a noob on Ubuntu (or Linux of any kind), so need specific, detailed (read:  idiot proof) help.

Thanks for all the help!

Charles

---

### Post by kd5ful on 2008-01-14
I went the "wvdial" route.
I had found this option on here, or someplace similar to here.
Do some poking around on here, and you'll find it.
I'm planning to try getting my PX-500 working in Kppp as well now, just so I can use the GUI method, and call myself a lazy person :D (Just Kidding).
Linux had taught me a long time ago, there are several paths to the internet, pick one.
...Gutsy, and this is Linux 3.0 for me.
I LOVE this version!!

---

### Post by himikeb on 2008-02-20
I used the Sprint guide to get a (previously activated in Windoze) Merlin S620 card working in Gutsy.
The Sprint site has directions for Ubuntu that worked great with KPPP.
To solve the 2.5 minute disconnect, I used: sudo vi /etc/ppp/options
locate the line:
 lcp-echo-failure 4
comment it out so that there is no lcp check
#lcp-echo-failure 4
and reconnect - that fixed it for me!
Another site uses lcp-echo-failure 0 to disable it, but the man doc says the number must be greater than 0 and I didn't bother because this was working.

---

