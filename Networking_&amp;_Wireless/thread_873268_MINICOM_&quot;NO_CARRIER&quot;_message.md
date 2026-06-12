---
title: "MINICOM &quot;NO CARRIER&quot; message"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by zanemccaig on 2008-07-28
I have a Toshiba Satellite A210 with Vista and Ubuntu 8.04 dual booted ith wubi. I bought a US robotics USB modem USR5637 that says Linux supported right on it. But it only connected once right at the start and i didnt do anyhting but it never worked again after that. It says to use minicom to connect it. So  I managed to make it dial it and i put in my username and password then i get a bunch of symbols then about 45 seconds later it disconnects and says "NO CARRIER". I tryed to change the Bps to 576000 and the init string to AT&F1 which i heard is what you are supossed to use for USR but i still get the same message. Also I can only dial using the dial directory I can't use ATDT or ATDP. Any help would be veryhelpful thanks in advance.

Zane McCaig

---

### Post by ModelM on 2008-07-28
I have one of these modems & mine works very well. Minicom is a great way to test it, also.

This modem is capable of a DTE rate of up to 230400, but your 57600 selected speed is fine for testing.

Your Init string should be: ATZ4 - this is the USR standard reset string which will enable hardware handshaking.

If your intent is to connect to the Internet, minicom won't do that for you. minicom will let you communicate with the modem, dial a number, and generally test the modem.

For the Internet you'll need a "dialer program". wvdial is already installed and works quite well. In order to use it, you'll need to edit the file:

/etc/wvdial.conf

Here's mine:

```
[Dialer Defaults]
    New PPPD = yes
    Stupid Mode = yes
    Modem Type = Analog Modem
    ISDN = 0
    Auto DNS = 1
    Auto Reconnect = 0
    Modem = /dev/ttyACM0
    Baud = 230400
    Init1 = ATZ4

Phone = 503 742 9199
Username = WhoIsThis
Password = Guessit


```

You can (as root) edit your /etc/wvdial.conf file to look like this, then, in a terminal, type:

sudo wvdial

after entering the root password, your modem should dial & connect.

After we get this working, we can work on fancier or easier ways to connect. But we'll stick to the basics for now in order to get things running.

---

### Post by ModelM on 2008-07-28
I forgot to mention, after your modem dials & connects, do not close the terminal window. Bring up your web browser, email program, whatever, & do your thing, but don't close the terminal window until you're finished. That will disconnect your modem.

As I said, we can get fancier with other dialers later. Right now we want to get the framework in place & correct.

---

### Post by zanemccaig on 2008-07-29
ok thank you very much i will try that and then get back to you.

---

### Post by zanemccaig on 2008-07-29
Wow thank you very much I used wvdial and it worked perfectly. The modem cuts out every onece in a while for a few seconds and isnt the fastest but it is way better than nothing. Also I did not put in all the extra stuff you had for the info in wvdial.conf i jsut put the password and what not then I did (sudo ln-s /dev/ttyACM0 /dev/modem). It works fine that way should i put in all of the other information too and it would be great if you could help find an easier way to connect. 

many thanks Zane!

---

### Post by ModelM on 2008-07-29
As to changing the "other stuff" in the config file, I would change the "Baud" line & the "Init1" line to what I have above. And comment out any other Init lines by putting a # as the first character of the line.

When the modem pauses, it's probably doing error correction or speed shifts - in other words it seems to be working properly.

You'll probably want to use a dialer program called GnomePPP and I'm sure there will be folks who will jump in here to help you set it up.

I use wvdial because it works so well & is easy to configure. Here's how I use it:

I bring up a terminal & type:

screen

When the hello message from screen appears, I just press return. I am now at a regular terminal, where I type:

sudo wvdial

You've seen what happens next. But then, when the modem connects, I click the button & close the terminal. I can do this because the "screen" program keeps everything running.

When I want to disconnect I open a terminal & type:

screen -r

which puts me right back where I was when the modem connected. I can now just press control-c to hang up & type "exit" to leave screen, then "exit" again to close the terminal.

I'm sure you'll want to use GnomePPP or something similar but you might want to try this once. It's not nearly as convoluted as it sounds. I like using wvdial "straight up" because it lets me see *everything* sent to the modem & *everything* the modem has to say about the connection. All of the "easy" dialer programs hide this info & I don't want anything hidden from me. I want to know exactly what's going on.

---

### Post by zanemccaig on 2008-07-30
Thank you I will try the screen command, and I think it was becasue I was running the package manager that it was slow. Also in my wvdial.conf I do not have an "init" line or "BAUD" shoudl I add them into it?

---

### Post by ModelM on 2008-07-30
How about this:

sudo mv /etc/wvdial.conf /etc/wvdial.conf.saved

and then copy my example above to

/etc/wvdial.conf.

Edit the phone number, username, & password, & try it out. If it gives you problems, just

sudo rm /etc/wvdial.conf && mv /etc/wvdial.conf.saved /etc/wvdial.conf

to go back to where you were.

---

### Post by zanemccaig on 2008-07-31
Thank you very much ModelM that worked perfectly and you helped me do what I have been trying to do for months.

---

### Post by ModelM on 2008-07-31
Thanks for saying that. As my "goodbye" message for this thread, I'd like to point out something unique about your modem.

If you read the instruction pamphlet you'll find the instructions for installing the driver in Windows & Mac OSX. Then, for Linux, they say in essence, "You linux folks don't need a driver, just plug it in & go".

A piece of hardware for which a driver is required under Windows, a driver required for Mac OSX, but no driver or other software required for use under Linux.

Now *that's* a rare occurrence! :)

---

### Post by MacDuff on 2008-09-26
I have a USB Robotics modem that I have been trying to get working using the GNOME Dialup Tool because this will be on a system whose owner is completely computer illiterate, even worse than I am.

I realize that this posting is not exactly on topic but close, and I am desperate, so here is hoping ...

The modem powers up and the data light comes on but the connection attempt fails part way through the login because the log reports: 
    Unable to run /usr/sbin/pppd
    Check permissions, or spedify a "PPPD Path" option in wvdial.conf.

I tried the connection method you outline above and when I enter "wvdial" the terminal reports:
    WvDial: Internet dialer version 1.60
    Cannot open /dev/ttyACMO: No such file or directory 

Can you shed some light on this and can you tell me how to get GNOME Dialup tool to work because as I say, the ultimate user needs something really simple to use.

Thanx

---

### Post by ModelM on 2008-09-26
What is the model number of the modem?

---

### Post by MacDuff on 2008-09-26
It is a USR Model 5637, and is supposed to support Linux.

---

### Post by ModelM on 2008-09-26
> **MacDuff said:**
> 
I tried the connection method you outline above and when I enter "wvdial" the terminal reports:
    WvDial: Internet dialer version 1.60
    Cannot open **/dev/ttyACM[color=#0000ff]O**[/color]: No such file or directory 


The last character of the device name should be the digit zero, not the letter O.

---

### Post by MacDuff on 2008-09-27
What a good eye you have!  Great catch, my bad.

I think I got a connection after editing the conf file.  Here is the output:

mac@T-61:~$ sudo wvdial
[sudo] password for mac: 
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Sending: ATDT250 388 5747
--> Waiting for carrier.
ATDT250 388 5747
CONNECT 48000/ARQ/V90/LAPM/V42BIS
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Fri Sep 26 20:53:23 2008
--> Pid of pppd: 16576
--> Using interface ppp0
--> local  IP address 207.102.100.151
--> remote IP address 207.102.100.3
--> primary   DNS address 204.174.64.1
--> secondary DNS address 204.174.65.1

Does the above look right to you or should there be more data?

Now the (silly) question is,  how do I work with that.  I tried to run Firefox but pages were not found. 

I assume that the connection must be converted into a network connection so that Kmail and Firefox can use the connection.  With Windows dialers the procedure was to create a dial-up network connection that, once it connected to the ISP, started the network automatically and away we went.  With linux there is obviously more involved.

Could you explain the rest of the procedure to me please so I can set up GNOME ppp so my friend can use email and web browsing?

Mac

---

### Post by ModelM on 2008-09-27
The dialog from wvdial you have posted looks ideal. You have received an IP address & the DNS server addresses. You have connected to your ISP.

Make sure that no other type of networking (ethernet, wireless) is enabled, that might be why Firefox failed to connect. The other types of networking, being faster, will take priority.

---

### Post by MacDuff on 2008-09-27
ModelM, I thank you.

Yes, I have a lan on all my computers and wireless lan on the laptop that I was using to test the modem for my friend.  I turned off the wireless but did not think to disable the network settings.

When I have time later today, I will try that and it sounds like this problem is solved. 

I may, however still have a problem with permissions using GNOME ppp.  I seem to recall that you do not use that so I may have to create another thread to deal with that.  

Anyway, you have been a BIG help to get me this far.

Mac

---

### Post by ModelM on 2008-09-27
I'd also recommend changing the init string to "ATZ4" in order to ensure hardware handshaking.

In this modem the init string "ATZ" might result in hardware handshaking being enabled or it might not. The result is dependent on other settings in the modem (check out "ATY" & "ATZ" in the reference section of the [_[color=blue]user guide[/color]_](http://www.usr.com/support/5637/5637-ug/index.html) at the USR website) .

An init string of "ATZ4", however, will always set the modem for hardware handshaking.

---

### Post by MacDuff on 2008-09-27
Yes I noticed that the log says it is sending ATZ but the wvdial.conf has ATZ4 as the command.

Can you explain why this would be?  It looks as though there may be another conf file somewhere.

When I do get a connection, I cannot use Firefox because it does not find a network connection,  I have played around with network connections [System] [Administration] [Network] and tried to create new settings for point to point connections but the settings do not stick. 

There are several confusing things about this:
On the General Tab, 
Connection type offers only  "Serial Modem" or PPPoE or GPRS/UMTS
I would not have thought that a USB modem would fit any of these categories.  Am I wrong?
If I select Serial modem the system does not seem to find it
If I select PPPoE the modem tab shows eth0 as the only choice.

I am really getting confused.  Should things be this difficult?  I am not the most brilliant man on earth but I do quite well with DOS and Windows OS.

I only have a couple of days to solve this and if I cannot I will have to re-install a Windows OS on my friend's computer and eat a heck of a lot of crow.

---

### Post by ModelM on 2008-09-28
The setting "serial modem" would be correct. You may need to:

```
sudo ln -s /dev/modem /dev/ttyACM0
```

to put a link to the modem in a place where the dialer will look for it.

---

### Post by MacDuff on 2008-09-28
Ok ModelM I did that, and I can still log into the Dial-up IP but my web browser still cannot find websites.

I have looked at network settings and "Point to point connection" shows "type ppoe Ethernet Interface: eth0" but there is no mark in the box to the left of the telephone icon.  If I check the box, the load icon spins for a few seconds and then the checkmark disappears. 
If it means anything the "Wired Connection" box above "Point to Point has a "-" in it all the time but there is no wired connection.

Any more suggestions or is there anything more I can tell you that might help?

---

### Post by MacDuff on 2008-09-28
I found some information that said there may be two locations for wvdial.conf.   Apparently it can exist in "/etc/wvdial.conf"  AND in "HOME/.wvdial.conf"

I have had a look at them and they are quite different.  Could this be part of the problem?

The contents of /etc/wvdial.conf:
[Dialer Defaults]
New PPPD = yes
Stupid Mode = yes
Modem Thpe = Analog Modem
ISDN = 0
Auto DNS = 1
Auto Reconnect = 0
Modem = /dev/ttyACM0
Baud = 230400
Initl = ATZ4
Phone = 2503885747
Username = {name}
Password = {password}


The contents of /home/max/wvdial.conf - much more and some differences.
[Dialer Defaults]
Modem = /dev/ttyACM0
ISDN = off
Modem Type = Analog Modem
Baud = 460800
Init = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = 
Init4 = 
Init5 = 
Init6 = 
Init7 = 
Init8 = 
Init9 = 
Phone = 2503885747
Phone1 = 2503885747
Phone2 = 
Phone3 = 
Phone4 = 
Dial Prefix = 
Dial Attempts = 1
Dial Command = ATM1L3DT
Ask Password = off
Password = {password}
Username = {user name}
Auto Reconnect = on
Abort on Busy = off
Carrier Check = on
Check Def Route = on
Abort on No Dialtone = on
Stupid Mode = on
Idle Seconds = 0
Auto DNS = on
;Minimize = off
;Dock = on
;Do NOT edit this file by hand!

Note the WARNING above!
Does this shed any light or just inject fog?

Mac

---

### Post by ModelM on 2008-09-28
If the modem is properly connecting to the ISP there is nothing more to be done with the wvdial.conf files, no matter where they are or how many. That's all wvdial does.

Let's try a couple of things:

Dial & connect, then type```
ifconfig
```
into a terminal. This will let us see all the network connections and their metric (priority).

Also type```
tail -25 /var/log/messages

```
into a terminal. This will let us see what the computer has to say at the moment of connection. Specifically we're looking for a "connect" line something like the third line here:```

Sep 28 09:50:47 asimov pppd[4364]: pppd 2.4.4 started by fred, uid 1500
Sep 28 09:50:47 asimov pppd[4364]: Using interface ppp0
Sep 28 09:50:47 asimov pppd[4364]: Connect: ppp0 <--> /dev/ttyACM0
Sep 28 09:50:48 asimov pppd[4364]: PAP authentication succeeded
Sep 28 09:50:48 asimov pppd[4364]: local  IP address xx.xx.xx.xx
Sep 28 09:50:48 asimov pppd[4364]: remote IP address xx.xx.xx.xx

```

And, just as a double check, ensure that Firefox is not set up to use a proxy.

firefox > edit > preferences > advanced > connection settings

---

### Post by MacDuff on 2008-09-28
Ok ModelM here is the output from the two commands you suggested.

mac@T-61:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:37:90:3b:f4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0x1840 Memory:fe000000-fe020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4050 (3.9 KB)  TX bytes:4050 (3.9 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.152.1  Bcast:172.16.152.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.186.1  Bcast:172.16.186.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

mac@T-61:~$ 




mac@T-61:~$ tail -25 /var/log/messages
Sep 28 16:13:51 T-61 pppd[15137]: pppd 2.4.4 started by root, uid 0
Sep 28 16:14:26 T-61 pppd[15137]: Timeout waiting for PADO packets
Sep 28 16:15:31 T-61 pppd[15137]: Timeout waiting for PADO packets
Sep 28 16:16:36 T-61 pppd[15137]: Timeout waiting for PADO packets
Sep 28 16:17:41 T-61 pppd[15137]: Timeout waiting for PADO packets
Sep 28 16:18:46 T-61 pppd[15137]: Timeout waiting for PADO packets
Sep 28 16:19:51 T-61 pppd[15137]: Timeout waiting for PADO packets
Sep 28 16:20:56 T-61 pppd[15137]: Timeout waiting for PADO packets
Sep 28 16:21:16 T-61 pppd[15137]: Terminating on signal 15
Sep 28 16:21:16 T-61 pppd[15137]: Exit.
Sep 28 16:21:16 T-61 pppd[15912]: Plugin rp-pppoe.so loaded.
Sep 28 16:21:16 T-61 pppd[15914]: pppd 2.4.4 started by root, uid 0
Sep 28 16:21:16 T-61 pppd[15914]: Exit.
Sep 28 16:21:16 T-61 kernel: [32717.030593] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 28 16:21:17 T-61 kernel: [32717.183384] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 28 16:21:19 T-61 kernel: [32719.356284] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 28 16:24:02 T-61 kernel: [32882.329770] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 28 16:24:02 T-61 kernel: [32882.473456] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 28 16:24:04 T-61 kernel: [32884.360920] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 28 16:24:09 T-61 pppd[20806]: Plugin rp-pppoe.so loaded.
Sep 28 16:24:09 T-61 pppd[20808]: pppd 2.4.4 started by root, uid 0
Sep 28 16:24:09 T-61 pppd[20808]: Exit.
Sep 28 16:24:09 T-61 kernel: [32889.063768] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 28 16:24:09 T-61 kernel: [32889.226243] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 28 16:24:11 T-61 kernel: [32891.390804] ADDRCONF(NETDEV_UP): eth0: link is not ready


Firefox >edit > preferences > network > connection > Configure Proxies to Access the Internet is set to "Use system proxy settings".

Should this be set to use "No Proxy" and if that is correct should some setting in Kontact or Kmail also be set similarly?

Mac

---

### Post by ModelM on 2008-09-28
Set Firefox to use no proxy. If the others have proxy settings, also, set them to use no proxy as well.

---

### Post by MacDuff on 2008-09-28
Ok set Firefox to no proxy and again tried sudo wvdial.  
Terminal showed primary and secondary DNS addresses but when trying to use Firefox it displays: 
"Offline Mode"  
"Firefox is operating in its offline mode and cannot connect to the requested item"

Any more suggestions?

---

### Post by ModelM on 2008-09-28
At that point in the Firefox menu

File > uncheck "work offline"

Here's a [_thread](http://ph.ubuntuforums.com/showthread.php?t=892271)_ where folks discuss that problem with Firefox.

---

### Post by MacDuff on 2008-09-29
ModelM you are a life saver, and that is not much of an over-statement.
You solved the problem!  And you should know the story behind it. 

I have a friend living alone on a farm in Alberta who is 70+ years old, has never used a computer and who has been pressured into getting one by his family.

We thought that satellite IP service would be available and I set up a computer this past summer predicated on being able to get a high speed Internet connection.  Then it turned out that a 100 ft. tower would have to be built to get satellite from his location, so he said the only option was telephone dial-up.

I am in the middle of a project and don't have much time to spare at the moment but I agreed to fly out there this weekend to install a modem and get some easy way for him to connect to the Internet so he can communicate with his family by e-mail.

I purchased a modem for him but could not make it work with my system, as you know.  I did not have much time to play with it to solve the problem(s) but you were kind enough to spend time on it and ultimately provided the solution.

I will tell him how the Ubuntu community came to his aid and hopefully he will tell his friends and family how kind and helpful Ubuntu users are.
 
If you are ever on Vancouver Island, send me a pm and I will buy you a meal.

Thank you! 

Mac

---

### Post by ModelM on 2008-09-29
You just swelled my hat size a bit. Thank you.

You might have a talk with the local amateur radio club about that tower. Those folks can be as helpful as the Linux community. They have experience assembling towers and could probably find a used one at a reasonable price. If you offer to allow them to install an antenna on the tower, they might be willing to help out with procuring the tower sections and construction, also.

---

### Post by MacDuff on 2008-09-29
That is one heck of great idea ModelM!  I guess that's why they pay you the big bucks eh? ("Eh" is an Canadianism. Most US residents expect to see it when they correspond with us Canucks, so just not disappoint, we throw one in from time to time....)

I will pass that information on to my friend.  He has been living in the area all his life and will no doubt know someone who is a ham operator.

Thank you again.

Mac

---

### Post by Westmeath on 2008-12-23
I have the same modem usr5637 & am trying to set it up for a non-literate friend on an Eeepc 900 running Intrepid. I want it to use Gnome-PPP as the GUI for simplicity. 

Have managed to get it to connect by running sudo wvdial in a terminal. Have had Firefox working by turning off networking & choosing Online mode in Firefox.

Won't dial unless I run as root. Get this message:

> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf

I have done:

> sudo chown root:dip /usr/sbin/pppd
sudo chmod 4754 /usr/sbin/pppd
sudo chmod 777 /etc/ppp/pap-secrets
sudo chmod 777 /etc/ppp/peers

& also:

> sudo ln -s /dev/modem /dev/ttyACM0

Any help greatly appreciated!

---

### Post by ModelM on 2008-12-23
You might have a look at this [ _bug report](https://bugs.launchpad.net/ubuntu/+source/gnome-ppp/+bug/289575)_.

---

### Post by Westmeath on 2008-12-23
> **ModelM said:**
> You might have a look at this [ _bug report](https://bugs.launchpad.net/ubuntu/+source/gnome-ppp/+bug/289575)_.

Thanks for that (not the reply I was hoping for).:(

Any suggestions for a more dial modem friendly distro? preferably a buntu derivative but will look at others.

I was hoping for a very simple solution. The end user might have enough trouble turning off networking & getting Firefox to go Online!

---

