---
title: "testing serial port"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by dotborg on 2010-01-24
I have an internal com header on my motherboard that's connected to the back of my machine with a fly lead. It's been activated in the bios but as it's connected to a non-functioning serial modem I just wanted to make sure that the port itself was ok.

I've tried a few commands I've found on the forums, the most useful looking is:

$ stty -F /dev/ttyS0 -a
 
which returns:

speed 9600 baud; rows 0; columns 0; line = 0;
intr = ^C; quit = ^\; erase = ^?; kill = ^U; eof = ^D; eol = <undef>; eol2 = <undef>; swtch = <undef>; start = ^Q;
stop = ^S; susp = ^Z; rprnt = ^R; werase = ^W; lnext = ^V; flush = ^O; min = 1; time = 0;
-parenb -parodd cs8 hupcl -cstopb cread clocal -crtscts
-ignbrk -brkint -ignpar -parmrk -inpck -istrip -inlcr -igncr icrnl ixon -ixoff -iuclc -ixany -imaxbel -iutf8
opost -olcuc -ocrnl onlcr -onocr -onlret -ofill -ofdel nl0 cr0 tab0 bs0 vt0 ff0
isig icanon iexten echo echoe echok -echonl -noflsh -xcase -tostop -echoprt echoctl echoke


If I try the same command with a different numbered port it returns an error - so whilst this looks promising I have no idea what the output means, I was just hoping someone might confirm all was well with my com port, or could recommend another test.

many thanks

---

### Post by lkraemer on 2010-01-24
The easiest thing to try is to use a terminal program (minicom) to
transmit characters out the port.  Here is is some good information
on the RS-232C port.

The pin numbers are often engraved in the plastic of the connector, but
you may need a magnifying glass to read them.  Note DCD is sometimes
labeled CD.  The numbering of the pins on a female connector is read
from right to left, starting with 1 in the upper right corner (instead
of 1 in the upper left corner for the male connector as shown below)


So, if you jumper Pin 2 to Pin 3 of the 9 Pin connector, you should see
the characters echo back to the display.  If that works your port most
likely is 100% functional.  You can also toggle the RTS & DTR lines
to verify that they also function.  RTS & DTR "ASSERTED" mean they are
a "HIGH" voltage, and the states are changed in SOFTWARE.

Or, just connect the External Modem and use wvdial to try dialing out.

lk

---

### Post by dotborg on 2010-01-25
Hi, Thankyou so much for replying to my post!
Would you happen to know the commands to try in minicom? (I'm still very new at this)

I tried booting up with the pins already jumpered and minicom wouldn't run saying "/dev/ttyS0 is locked".
 When I restarted again with the socket bare then shorted the pins, minicom runs but I don't know how to get it to echo any commands.

I also tried opening two xterm windows and using "cat /dev/ttyS0" in one whilst typing "echo "AT" >/dev/ttyS0" in another - unfortunately nothing happened so I'm still a bit stuck.

---

### Post by lkraemer on 2010-01-25
While I haven't used minicom, I did find some documentation on how
to set it up.

[http://openmaniak.com/minicom.php](http://openmaniak.com/minicom.php)
[http://www.linux-tutorial.info/modules.php?name=Howto&pagename=Remote-Serial-Console-HOWTO/modem-minicom.html](http://www.linux-tutorial.info/modules.php?name=Howto&pagename=Remote-Serial-Console-HOWTO/modem-minicom.html)

To configure minicom for modem use, the following command is used (Even though you have no modem attached):
```

minicom -o console

```
to start Minicom without sending an initialization string to the modem. Now issue the
```

AT

```
commands to configure the modem.

ie, ATZ  will RESET the MODEM (but of course you won't have one attached.)

Anything you type on the keyboard should now be echoed back to the
screen, if you have the TX to RX Jumper on the RS-232C Port.

If you toggle to Hardware Control RTS & DTR should go ASSERTED (HIGH),
so when you type, the characters will go to the Data Communication Equipment (typical Modem)

When finished use the Quit option to leave Minicom without sending a reset string to the modem; this option is:
```

Alt-Q

```

(I have used Procomm in Windows to do this sort of thing, and it works
the same way.  Just different terminal software.)

Probably the easiest way to start is to connect the Voltmeter RED Lead from TX
(Pin 3 on the DB9 Connector, or Pin 2 on the DB25 Connector) to SIGNAL GROUND
BLACK Voltmeter Lead to (Pin 5 for DB9 or Pin 7 for DB25 Connector).  Now set
the BAUD to the lowest possible rate in minicom.  Now type some characters on
the keyboard and watch the voltmeter needle swing.  If it doesn't work, you most
likely have used the wrong pins or have problems.  Most DTE (Data Terminal Equipment)
cables are MALE Pin Connectors in the DB9 or DB25 Connectors that plug into
Modems etc. (Data Communication Equipment) 

I just found this site:
[http://www.arcelect.com/rs232.htm](http://www.arcelect.com/rs232.htm)
Go read, study, and find out how to test for DTE vs. DCE.

Cable Info:
[http://www.camiresearch.com/Data_Com_Basics/RS232_standard.html](http://www.camiresearch.com/Data_Com_Basics/RS232_standard.html)

lk

---

