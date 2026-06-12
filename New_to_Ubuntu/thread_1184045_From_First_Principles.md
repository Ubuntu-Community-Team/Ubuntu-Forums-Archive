---
title: "From First Principles"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by chome4 on 2009-06-10
Using Jaunty and just got a Huawei modem for web access. From what I've read, I need wvdial but I then discover it's not a file you create and then run but it's a program!

Anyone got a step-by-step guide that covers getting online? In wvdial.conf there's reference to password and username. The mystery is that I don't have those details as the three.co.uk store who signed me up for the modem didn't offer me one!

I know how to use terminal to edit a file in the \etc\ folder and the 'lsusb' command but that's about it.

I do have web access from my local library so I can download files to a CD and take them home....

I'm determined not to reach for the Windows XP disk!

Hope someone can help.

---

### Post by Sealbhach on 2009-06-10
Most Huawei modems, like the E220 should just work - just plug it in and Ubuntu knows what to do. What have you tried so far?

.

---

### Post by Person_1873 on 2009-06-10
dial-up technology is so antiquated, might i ask why you wanted to go down this route?

---

### Post by Sealbhach on 2009-06-10
> **Person_1873 said:**
> dial-up technology is so antiquated, might i ask why you wanted to go down this route?

3G modems like the Huawei dongles aren't antiquated, they've been revived for the mobile generation.

.

---

### Post by chome4 on 2009-06-10
> **Sealbhach said:**
> Most Huawei modems, like the E220 should just work - just plug it in and Ubuntu knows what to do. What have you tried so far?

.

Thanks for the quick response...

I waited a few hours as they told me it would take this long for me to be 'added'. Plugged it in and typed lsusb and it appeared. The green light on the unit flashes two times at regular intervals.

Opened FireFox and nothing. Unchecked 'work offline' and still nothing.

I've created/edited no files so far.

Thanks

---

### Post by chome4 on 2009-06-10
> **Person_1873 said:**
> dial-up technology is so antiquated, might i ask why you wanted to go down this route?

There's no existing telephone landline in my flat and I will only there for a few months. Plus I will be travelling within the UK soon and a USB dongle fits the bill for when I get a laptop. My current pc is an old Dell Dimension mini tower.

If you're a home-based surfer/worker then a traditional wired/wireless setup would suffice.

---

### Post by Sealbhach on 2009-06-10
OK, what make of dongle is it? If you type lsusb and copy and paste the info here, that will help. It also helps if you have the dongle plugged in before you boot up the machine. Give that a try.

.

---

### Post by chome4 on 2009-06-10
> **Sealbhach said:**
> OK, what make of dongle is it? If you type lsusb and copy and paste the info here, that will help. It also helps if you have the dongle plugged in before you boot up the machine. Give that a try.

.

It's a *Huawei E165G*[I]. I'm away from my flat until the morning so I'll get the details then.

[/I]

---

### Post by Sealbhach on 2009-06-10
> **chome4 said:**
> It's a *Huawei E165G*[I]. I'm away from my flat until the morning so I'll get the details then.

[/I]

OK. If you look at the Ubuntu 3G page [here]("https://wiki.ubuntu.com/NetworkManager/Hardware/3G") you'll see that 3G wireless support is extensive, though I can't find your E165G there but we should be able to get you connected fairly soon.

.

---

### Post by t0p on 2009-06-10
I've got a Huawei 3G dongle - a E160X, but the pronciple will be the same for your modem.  You say that Three haven't told you the username and password - I think you'd better call their helpline and ask for this info, as it may well be needed.  There are often 3 pieces of info needed to maker a connection over mobile networks - username, password and APN (Access Point Name).  Call Three and ask them for this info.

Ubuntu's Network Manager should help you set up a connection.  When I plug my dongle (or mobile phone) into my computer, a window comes up saying it will help you set up a mobile broadband connection.  You answer a few questions - what country you're in, who your mobile service provider is - and the wizard sets up all the info for you.  This includes the username, password and APN, but the info the wizard comes up with is not always correct.  So you then need to right-click on the Network Manager icon (looks like 2 monitors, up in the top right of your display usually) and select Edit Connection.  Then you can enter the correct info for your provider.

Another solution -which I think is the best - is the [**Vodafone Mobile Connect Card Driver for Linux**]("https://forge.betavine.net/frs/?group_id=12").  I realise Vodafone isn't your provider, but that's okay - the VMC Driver works for all providers, you just need to ensure you put in the correct settings (that username, password and APN again).  You can download the VMC Driver for Linux from [this link]("https://forge.betavine.net/frs/?group_id=12").  Scroll down the page, about halfway down you'll find the versions for "Debian, Ubuntu, Ubuntu Netbook Remix, Linux Mint".  I personally found this the right .deb to install - [vodafone-mobile-connect_svn20090502_all.deb]("https://forge.betavine.net/frs/download.php/503/vodafone-mobile-connect_svn20090502_all.deb") - I tried earlier versions but they didn't work.  However, please bear in mind that this software is in Beta.  Make sure you also download the appropriate INSTALL.txt - [this one]("https://forge.betavine.net/frs/download.php/429/INSTALL.txt") - and follow the instructions carefully.

You may also find my tutorial on using a mobile phone as a modem helpful - see the link in my sig.  The principle is the same for using a 3G dongle, especially if you go down the route of using wvdial.

If you need any more help, post here and I'll help if I can. (Don't send me a PM, keep it in the forum so others can read it, and maybe help too.)

---

### Post by Sealbhach on 2009-06-10
It gives that info down the page [here]("https://wiki.ubuntu.com/NetworkManager/Hardware/3G") which is handy. For 3 in the UK it's:

APN = 3internet 

username = three

password = three

unless you're on Pay As You Go, in this case the APN is three.co.uk

.

---

### Post by chome4 on 2009-06-11
[SIZE=3][FONT=Times New Roman]lsusb output:[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]p@p:~$ lsusb[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Bus 001 Device 003: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Bus 003 Device 002: ID 04b3:310b IBM Corp. Red Wheel Mouse[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][EMAIL="p@p:~$"]p@p:~$[/EMAIL][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]Went to the store a minute ago and they assure me the dongle's live. As usual, they insist Linux isn't recommended for this type of kit![/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]I made a mistake in saying I had a 165. It's a Huawei E156G but it's not on the list. I can always exchange it for a ZTE MF627, which is the one previewed on their website but I was 'sold' on the benefits of the Huawei by the guy in the shop. Or 'Hawaii', as they call it![/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]I've got thirteen days to get this going before I can get a refund.
[/SIZE][/FONT]

---

### Post by chome4 on 2009-06-11
***"I think you'd better call their helpline and ask for this info, as it may well be needed. There are often 3 pieces of info needed to maker a connection over mobile networks - username, password and APN (Access Point Name). Call Three and ask them for this info."***
 
Just got off the telephone to Three and they say they're only trained on Microsoft and Mac Op systems.

---

### Post by chome4 on 2009-06-11
> **Sealbhach said:**
> It gives that info down the page [here]("https://wiki.ubuntu.com/NetworkManager/Hardware/3G") which is handy. For 3 in the UK it's:
 
APN = 3internet 
 
username = three
 
password = three
 
unless you're on Pay As You Go, in this case the APN is three.co.uk
 
.
 
Tried it. No go!
 
It seems the process isn't even attempting to talk to the modem to validate the username etc. The thing just sits there.
 
I bet the solution is no more than a couple of mouse clicks!

---

### Post by Idefix82 on 2009-06-11
> **chome4 said:**
> 
Just got off the telephone to Three and they say they're only trained on Microsoft and Mac Op systems.

In our language that translates as "they are not trained in customer support". What are they sitting there for, then? :o

---

### Post by chome4 on 2009-06-11
> **Idefix82 said:**
> In our language that translates as "they are not trained in customer support". What are they sitting there for, then? :o
 
It was an Indian help desk guy reading from a script. Did very well at asking me to confirm my email, though!
 
What do you expect from someone who wants only to talk about Microsoft.

---

### Post by Sealbhach on 2009-06-11
> 
[SIZE=3][FONT=Times New Roman]Bus 001 Device 003: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem[/FONT][/SIZE]

It's got the same device ID as the E220 and the E270 so it should work right out of the box. 



> 
Tried it. No go!What steps did you take here? Did you create a new Mobile Broadband connection in Network Manager? Like in my screenshot? Make sure to tick the connect automatically box.

.

---

### Post by t0p on 2009-06-11
I take it you haven't tried the Vodafone Mobile Connect Card Driver for Linux  then?  Shame, as it works with my Huawei USB dongle just fine.  One thing I forgot to mention though, before you can install VMC, you need to install usb-modeswitch.  That's no biggie though, it's available [on the same page]("https://forge.betavine.net/frs/?group_id=12") as the VMC downloads.

To tell the truth, from what you've posted I can't figure out what you've tried at all.  Have you tried *anything*?  If so, what?  And how?

Sealbhach has provided the username, password and APN you need.  So at the very least wvdial should work!  In my experience, if you use wvdial with a dongle, it will connect at a much lower speed than what's possible with VMC or Network Manager.  But it should be a very easy process:

1. Switch off the computer.

2. Plug in the dongle.

3.  Start the computer. (This allows the dongle to register correctly with the kernel - it shouldn't really be necessary to restart the machine like this, but it does make sure the dongle is correctly recognized).

4.  Open a terminal, and type the command

```
sudo wvdialconf
```

wvdialconf will detect the modem, and will write configuration data to /etc/wvdial.conf.

5.  Edit /etc/wvdial.conf (remember to use sudo) - fill in the username and password; the telephone number you should put in as *99#.  Make sure you remove the semi-colons from the beginning of those lines.  Also, add a line that says 

```
Stupid Mode = yes
```

6.  Now when you give the command 

```
sudo wvdial
```

it should connect.

I don't think I've missed anything out.  But check the tutorial linked to in my sig, just in case!  That ought to connect.  But like I said, VMC is much faster and better (as is using the Network Manager wizard to set up a mobile broadband connection).  Please, do try one of our suggestions.

---

### Post by Sealbhach on 2009-06-11
> **t0p said:**
> 

4.  Open a terminal, and type the command

```
sudo wvdialconf
```wvdialconf will detect the modem, and will write configuration data to /etc/wvdial.conf.


I checked this out a little while ago, wvdial is not installed in Jaunty.:o

There's a thread on how to install it here:

[http://swiss.ubuntuforums.org/showpost.php?p=7437892&postcount=20](http://swiss.ubuntuforums.org/showpost.php?p=7437892&postcount=20)

But it should not be needed, Network Manager should be able to handle the connection. Does Network Manager have a connection log?

.

---

### Post by chome4 on 2009-06-11
> **t0p said:**
> I take it you haven't tried the Vodafone Mobile Connect Card Driver for Linux  then?  Shame, as it works with my Huawei USB dongle just fine.  One thing I forgot to mention though, before you can install VMC, you need to install usb-modeswitch.  That's no biggie though, it's available [on the same page]("https://forge.betavine.net/frs/?group_id=12") as the VMC downloads.

To tell the truth, from what you've posted I can't figure out what you've tried at all.  Have you tried *anything*?  If so, what?  And how?

Sealbhach has provided the username, password and APN you need.  So at the very least wvdial should work!  In my experience, if you use wvdial with a dongle, it will connect at a much lower speed than what's possible with VMC or Network Manager.  But it should be a very easy process:

1. Switch off the computer.

2. Plug in the dongle.

3.  Start the computer. (This allows the dongle to register correctly with the kernel - it shouldn't really be necessary to restart the machine like this, but it does make sure the dongle is correctly recognized).

4.  Open a terminal, and type the command

```
sudo wvdialconf
```wvdialconf will detect the modem, and will write configuration data to /etc/wvdial.conf.

5.  Edit /etc/wvdial.conf (remember to use sudo) - fill in the username and password; the telephone number you should put in as *99#.  Make sure you remove the semi-colons from the beginning of those lines.  Also, add a line that says 

```
Stupid Mode = yes
```6.  Now when you give the command 

```
sudo wvdial
```it should connect.

I don't think I've missed anything out.  But check the tutorial linked to in my sig, just in case!  That ought to connect.  But like I said, VMC is much faster and better (as is using the Network Manager wizard to set up a mobile broadband connection).  Please, do try one of our suggestions.

As mentioned in my first post, I'm working from a fresh install with no Linux experience whatsoever and all the stuff I've read doesn't take a newbie from first principles without assuming certain things. I now know that wvdial isn't just a config file that runs to invoke the modem. I now have to learn how to install in a way that is very different from the Windows way. The VMC page in the link is a vast array of clickable lines. That's my project for the next couple of days!Ps

PS. I'll be going down the VMC route as I want the speed.

Following the instructions in your install.txt file and copying the files to my pen drive.

I'll post an update tomorrow.

Thanks very much for the info.

---

### Post by chome4 on 2009-06-12
*_**[SIZE=3]UPDATE - Vodafone Mobile Connect[/SIZE]**_*
[SIZE=2](Stuff I installed in bold. Errors in bold red)[/SIZE]
 
p@p:~$ **sudo dpkg -i usb-modeswitch_0.9.4-1_i386.deb**
[sudo] password for p: 
(Reading database ... 102000 files and directories currently installed.)
Preparing to replace usb-modeswitch 0.9.4-1 (using usb-modeswitch_0.9.4-1_i386.deb) ...
Unpacking replacement usb-modeswitch ...
Setting up usb-modeswitch (0.9.4-1) ...
[COLOR=black]p@p:~$[/COLOR] 
 
 
p@p:~$ **sudo dpkg -i vodafone-mobile-connect_1.99.17-8_all.deb**
Selecting previously deselected package vodafone-mobile-connect.
(Reading database ... 102000 files and directories currently installed.)
Unpacking vodafone-mobile-connect (from vodafone-mobile-connect_1.99.17-8_all.deb) ...
dpkg: dependency problems prevent configuration of vodafone-mobile-connect:
vodafone-mobile-connect depends on python-crypto; however:
Package python-crypto is not installed.
vodafone-mobile-connect depends on python-gnome2-extras; however:
Package python-gnome2-extras is not installed.
vodafone-mobile-connect depends on python-serial; however:
Package python-serial is not installed.
vodafone-mobile-connect depends on python-sqlite; however:
Package python-sqlite is not installed.
vodafone-mobile-connect depends on python-twisted; however:
Package python-twisted is not installed.
vodafone-mobile-connect depends on python-tz; however:
Package python-tz is not installed.
vodafone-mobile-connect depends on wvdial; however:
Package wvdial is not installed.
**[COLOR=red]dpkg: error processing vodafone-mobile-connect (--install):[/COLOR]**
**[COLOR=red]dependency problems - leaving unconfigured[/COLOR]**
Processing triggers for hal ...
Regenerating hal fdi cache ...
* Restarting Hardware abstraction layer hald [ OK ] 
Errors were encountered while processing:
vodafone-mobile-connect
p@p:~$ 
 
 
p@p:~$ **sudo apt-get -f install**
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Correcting dependencies...Done
The following packages will be REMOVED
vodafone-mobile-connect
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 5800kB disk space will be freed.
Do you want to continue [Y/n]? 
 
I answer yes....
 
(Reading database ... 102645 files and directories currently installed.)
Removing vodafone-mobile-connect ...
Processing triggers for hal ...
Regenerating hal fdi cache ...
* Restarting Hardware abstraction layer hald [ OK ] 
 
 
p@p:~$ 
p@p:~$ **vodafone-mobile-connect-card-driver-for-linux**
[COLOR=red]**bash: vodafone-mobile-connect-card-driver-for-linux: command not found**[/COLOR]
p@p:~$ 
 
[SIZE=2][COLOR=black]=========================================[/COLOR][/SIZE]
 
[SIZE=2]All went well until that last message. Seems like the path to where the driver is wrong.[/SIZE]
 
[SIZE=2]What do I need to check? My money's on that mention of python during the vodafone part of the install.[/SIZE]
 
[SIZE=2]Thanks.[/SIZE]

---

### Post by Sealbhach on 2009-06-12
Oh, I see what happened.  When you answered Yes it removed vodafone-mobile-connect...

Try this command instead:

```
sudo dpkg -i --force all vodafone-mobile-connect_1.99.17-8_all.deb
```

You'll notice in the Install.txt it says to ignore the message about the dependencies, which is the python stuff it's complaining about.

.

---

### Post by chome4 on 2009-06-12
> **Sealbhach said:**
> Oh, I see what happened. When you answered Yes it removed vodafone-mobile-connect...
 
Try this command instead:
 
```
sudo dpkg -i --force all vodafone-mobile-connect_1.99.17-8_all.deb
```
 
You'll notice in the Install.txt it says to ignore the message about the dependencies, which is the python stuff it's complaining about.
 
.
 
OK. I'll try it later.
 
Does the expression 'vodafone-mobile-connect-card-driver-for-linux' work in the same way as DOS/Windows in that it runs some sort of file of the same name?

---

### Post by Sealbhach on 2009-06-12
> **chome4 said:**
> OK. I'll try it later.
 
Does the expression 'vodafone-mobile-connect-card-driver-for-linux' work in the same way as DOS/Windows in that it runs some sort of file of the same name?

It launches the application. You can try this by opening a terminal and typing "firefox". This launches the browser.

I suspect from looking at your output that the command might be just:

vodafone-mobile-connect

That's what dpkg seems to be calling it:
> 
Unpacking vodafone-mobile-connect (from vodafone-mobile-connect_1.99.17-8_all.deb) ...
dpkg: dependency problems prevent configuration of vodafone-mobile-connect:

So try that if the first command doesn't work.

.

---

### Post by chome4 on 2009-06-12
[U]**UPDATE - ENTRIES IN BOLD / ERRORS IN BOLD-RED**
[/U]
p@p:~$ [B]sudo dpkg -i --force all vodafone-mobile-connect_1.99.17-8_all.deb
[/B]

(Reading database ... 102649 files and directories currently installed.)
Preparing to replace vodafone-mobile-connect 1.99.17-8 (using vodafone-mobile-connect_1.99.17-8_all.deb) ...
Unpacking replacement vodafone-mobile-connect ...
dpkg: vodafone-mobile-connect: dependency problems, but configuring anyway as you request:
 vodafone-mobile-connect depends on python-crypto; however:
  Package python-crypto is not installed.
 vodafone-mobile-connect depends on python-gnome2-extras; however:
  Package python-gnome2-extras is not installed.
 vodafone-mobile-connect depends on python-serial; however:
  Package python-serial is not installed.
 vodafone-mobile-connect depends on python-sqlite; however:
  Package python-sqlite is not installed.
 vodafone-mobile-connect depends on python-twisted; however:
  Package python-twisted is not installed.
 vodafone-mobile-connect depends on python-tz; however:
  Package python-tz is not installed.
 vodafone-mobile-connect depends on wvdial; however:
  Package wvdial is not installed.
Setting up vodafone-mobile-connect (1.99.17-8) ...
udevadm control expects commands without underscore, this will stop working in a future release

Processing triggers for hal ...
Regenerating hal fdi cache ...
 * Restarting Hardware abstraction layer hald                            [ OK ] 
p@p:~$ 


p@p:~$ [B]vodafone-mobile-connect-card-driver-for-linux
[/B]
Traceback (most recent call last):
  File "/usr/bin/upgrade-vmc-plugins", line 23, in <module>
    from vmc.common import plugin
[B][COLOR=Red]ImportError: No module named vmc.common
/usr/bin/vodafone-mobile-connect-card-driver-for-linux: line 3: twistd: command not found[/COLOR][/B]
p@p:~$ 


[COLOR=Black]p@p:~$ [B]vodafone-mobile-connect
[/B]
bash: [COLOR=Red]**vodafone-mobile-connect: command not found**[/COLOR]
p@p:~$
=======================

It mentions wvdial must be installed. I'll get onto that when I'm next in front of the PC. I've also downloaded all the Python related stuff to my pen drive.
[/COLOR]

---

### Post by Sealbhach on 2009-06-12
OK. Before you do that it's best to remove what you've just installed:

```
sudo dpkg -P vodafone-mobile-connect
```

.

---

### Post by scottuss on 2009-06-22
Wow I feel blessed that my USB just plugs in and gives an entry in NetworkManager. I click it and it connects. Easier than on Windows or a Mac.

---

### Post by chome4 on 2009-06-22
I'm up and running now! Faulty kit!

Yes, it's just plug and play.

In one hit I can now bypass two companies and save money - British Telecom and Microsoft. No need to by a full-spec expensive PC either!

---

