---
title: "Help With gnome-ppp (Dial-up Connection)"
date: 2010-11-05
forum: New to Ubuntu
---

### Post by tb75252 on 2010-11-05
Using Ubuntu 10.10 (32-bit), Gnome version.

I managed to download and install gnome-ppp so that I could set up a dial-up connection with my ISP.  The modem is detected and everything works fine up to the point when the modem tries to establish a connection with my ISP.

The window says "Waiting for prompt..." and after a couple of seconds I get disconnected.  I did some research online and somebody was suggesting to go into the Setup window, Options tab, and select "Ignore terminal strings (stupid mode)".  That did not help.

What else can I try?

PS:  My ISP is AT&T, in case you wonder.

---

### Post by ieee488 on 2010-11-05
I used to have AT&T dial-up.
I wrote up something about it [http://techplusnj.com/linux/linux_dialup.html]("http://techplusnj.com/linux/linux_dialup.html")
I found wvdialconf more useful when trying to debug.

---

### Post by lkraemer on 2010-11-05
You didn't specify, but I am assuming you have an EXTERNAL Modem,
either USB or RS-232C.  You also did not specify the Dialup ISP you
are using.  You might want to search the forum for ISP's that work
well with Linux.  (I use Copper.net) 

If you don't have a serial port, or want to use a USB port to Serial Adapter
check out the following:

The USB to Serial Converter is from [www.newegg.com](www.newegg.com) and is a
N82E16812156008 SABRENT 1 ft. USB to Serial db9 Male RS-232 (9-pin) Converter
Model SBT-USC1M - Retail @ $10.99.

These work wonderful with wvdial, etc.

I'd suggest installing wvdial and use it to troubleshoot your problem.
It can be found in the Synaptics Package Manager.  (You run it from a
Terminal Window or Console, leaving that window minimized.)

Once that is done, you will need to set up the pap-secrets and/or chap-secrets
file by running the following in a Terminal Window:
```

sudo pppconfig

```
You will need your userlogin, password, ISP provider information, and
pap or chap information for the connection. (You can set up pap and
then chap, if pap doesn't work.) Basically you just answer the questions
that are presented. You can delete a configurations and start over if
you need to from the menu selections.

For more information try:
```

man pppd
man pppconfig

```
/etc/ppp/pap-secrets file contains:
(NOTE: File Format for 10.04)
```

# Every regular user can use PPP and has to use passwords from /etc/passwd
*       hostname        ""      *

# UserIDs that cannot use PPP at all. Check your /etc/passwd and add any
# other accounts that should not be able to use pppd!
guest   hostname        "*"     -
master  hostname        "*"     -
root    hostname        "*"     -
support hostname        "*"     -
stats   hostname        "*"     -

# OUTBOUND connections

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.
#       *       password
"yourusername@yourisp.net" provider "yourpassword"

```
Now after ppp is setup, you will need to set up wvdial. Power up the modem,
and connect it to your serial port.  In a Terminal window do:
```

sudo wvdialconf /etc/wvdial.conf

```
You should get a configuration file like this at
/etc/wvdial.conf (you may need to add a few things...)

wvdial.conf contains:
```

[Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 48800
New PPPD = yes
Stupid mode = yes
;carrier check = no
Modem = /dev/ttyACM0
ISDN = 0
Phone = 4460568
Password = yourpassword
Username = yourusername@yourisp.net

```
You might want to double check the following settings:
Checking settings of: /etc/ppp/options
```

asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

```
You also need to do this after wvdial is installed and
after pppconfig is executed:

Now assuming that your pap-secrets and or your chap-secrets file is
correct you should be able to use wvdial to dial the connection with:
```

wvdial /etc/wvdial.conf

```
You should hear the modem go OFFHOOK with dialtone, Dial, and connect.
REMEMBER after wvdial dials, you can pick up a handset and monitor the
activity by listening to what is going on with the communications.
If your config file is correct you should authenticate and then control
will be passed to ppp. You will see several strings of HEX (funny characters)
and then you should stay connected. (you will use CNTL C to
terminate the session when you are done, but for this session you MUST
leave the Terminal window OPEN...) You may have to uncheck the box
marked OFFLINE when you open your browser to make it online. Surf,
then terminate the open session with CNTL C in the open terminal window
where you initiated wvdial.

Now that it works set up Gnome-PPP.


lk

---

### Post by tb75252 on 2010-11-06
Thank you for your help!  I really appreciate the degree of effort you put into answering my problem.

Before testing out your suggestions, I should specify that I have an  INTERNAL modem.  It is a US Robotics mod. USR5610C and I picked that  particular model because it is guaranteed to work with Linux.

The dial-up ISP used is AT&T.

Based on this information, would anything change in your instructions?

---

### Post by waynefoutz on 2010-11-06
Have you tried KPPP? I've found that is usually easier to set up and use than Gnome PPP.

---

### Post by dineshs on 2010-11-06
Run gnome-ppp as root
```
sudo gnome-ppp
```
while configuring untick [COLOR="SeaGreen"]check carrier line[/COLOR] and tick [COLOR="SeaGreen"]stupid mode[/COLOR]

---

### Post by jtarin on 2010-11-06
You have it is known as a Winmodem.....you'll need a driver for it if it is availabel. [Check here]("http://ubuntuforums.org/showthread.php?t=308098") and see if these instructions can help you get over this first hurdle. No amount of dial-up programs will help until your chipset is recognized and a driver loaded.

---

### Post by Old *ix Geek on 2010-11-06
> **jtarin said:**
> You have it is known as a Winmodem...It is *NOT* a winmodem; see its info page at US Robotics: [http://www.usr.com/support/product-template.asp?prod=5610c](http://www.usr.com/support/product-template.asp?prod=5610c) and note how Linux is included under OS compatibility.

---

### Post by jtarin on 2010-11-06
> **Old *ix Geek said:**
> It is *NOT* a winmodem; see its info page at US Robotics: [http://www.usr.com/support/product-template.asp?prod=5610c](http://www.usr.com/support/product-template.asp?prod=5610c) and note how Linux is included under OS compatibility.In Linux parlance a "WinModem" is known as an internal modem, compatibility not withstanding. All internal harware devices regardless of Linux Compatibility still need some enablement to perform. Commonly a module/driver is loaded for said device. This is either built in to the kernel or compiled from 3rd party sources.In the recent past internal modem modules were not built-in to the kernel.

I stand corrected on the need for a 3rd-party module/driver.
From Robotics manual
> Linux Users
All 2.3 and higher Linux kernels contain the USRobotics Linux modem drivers. Installation
of the modem under these kernels is fully automatic provided your kernel has the
Plug and Play module enabled (default).

---

### Post by jtarin on 2010-11-06
[Again from the manual]("http://www.usr.com/support/5610c/5610c-files/5610c-ig.pdf")
> Linux
1. Reboot the computer and verify that a serial port (/dev/ttySX) is listed along with
the name U.S. Robotics V92 Fax PCI, indicating the modem is present. Write down
the serial port information for the modem (ttySX).
2. Log in to the system.
3. Check that the modem is communicating properly:
o If working in a shell environment, start a Minicom terminal session from the terminal
prompt:
a) Launch a terminal (shell) session.
b) Create a symbolic link for the modem using the following commands:
cd /dev and press ENTER.
rm modem and press ENTER.
ln -s ttySX, where ttySX is the serial port for your modem, and press
ENTER.
c) Type Minicom and press ENTER.
d) If the modem initializes under Minicom, type AT and press ENTER.
11
If AT is displayed in the Minicom window as you type and OK is displayed
after you press ENTER, the installation was successful.
If AT is not displayed as you type and OK is not displayed after you press
ENTER, the installation was not successful; repeat the installation procedure.
o If using X Windows, use Minicom through a shell window or use the dial-up program
(Kppp or equivalent).
a) Execute the Kppp program (or other dial-up program) from the Internet submenu.
b) Within the Kppp program, click the Setup button, then the Device tab, and
then select U.S. Robotics V92 Fax PCI from the pull-down menu.
c) Click the Modem tab, then click the Query Modem button. About 15 seconds
later a window should appear with I-screen information from the
modem, indicating a successful installation.
If no information is displayed, the installation was not successful; repeat
the installation procedure.

---

### Post by QLee on 2010-11-06
[QUOTE=jtarin]In Linux parlance a "WinModem" is known as an internal modem, compatibility not withstanding. All internal harware devices regardless of Linux Compatibility still need some enablement to perform. Commonly a module/driver is loaded for said device. This is either built in to the kernel or compiled from 3rd party sources.In the recent past internal modem modules were not built-in to the kernel.

I stand corrected on the need for a 3rd-party module/driver.
From Robotics manual[/QUOTE]

May I offer a bit of correction on this too? A "winmodem" is one that uses some of the system's processing time for modem function, there are a couple of types. True "hardware" modems, whether internal or external have their own processing power and all that is needed from the system is the serial module, so the system can talk to the modem through the serial port where the modem resides.

I miss the tiger.

---

### Post by jtarin on 2010-11-06
> **QLee said:**
> May I offer a bit of correction on this too? No,but you may expound on it.:P

---

### Post by ieee488 on 2010-11-06
> **tb75252 said:**
> Thank you for your help!  I really appreciate the degree of effort you put into answering my problem.

Before testing out your suggestions, I should specify that I have an  INTERNAL modem.  It is a US Robotics mod. USR5610C and I picked that  particular model because it is guaranteed to work with Linux.

The dial-up ISP used is AT&T.

Based on this information, would anything change in your instructions?

You really should just *do* it instead of expecting everything to be handed to you on a plate.

Part of learning about Linux is in the trying. Unless you are fortunate to find someone with AT&T dial-up these days, you are the only one who can do anything to get your modem working.

I happen to have the USR modem with the same chipset as yours, and it **worked** with AT&T.

---

### Post by lkraemer on 2010-11-06
tb75252,
Proceed...  Your Modem should work, as wvdial should find it.
Shouldn't take you very long....less than 20 minutes.

It should work like a charm.

lk

---

### Post by Old *ix Geek on 2010-11-06
> **jtarin said:**
> In Linux parlance a "WinModem" is known as an internal modemWell, that's your opinion--and you know what they say [**_about opinions_**](http://www.cafepress.com/saproducts/1019475). :D In my opinion, especially regarding US Robotics modems--which I used for many, many years on Linux without issue--when the manufacturer itself lists Linux in its OS compatibility list, I don't consider it to be a win-anything. But then, that's my opinion. :)

---

### Post by tb75252 on 2010-11-06
> **lkraemer said:**
> You didn't specify, but I am assuming you have an EXTERNAL Modem,
either USB or RS-232C.  You also did not specify the Dialup ISP you
are using.  You might want to search the forum for ISP's that work
well with Linux.  (I use Copper.net) 

If you don't have a serial port, or want to use a USB port to Serial Adapter
check out the following:

The USB to Serial Converter is from [www.newegg.com]("http://www.newegg.com") and is a
N82E16812156008 SABRENT 1 ft. USB to Serial db9 Male RS-232 (9-pin) Converter
Model SBT-USC1M - Retail @ $10.99.

These work wonderful with wvdial, etc.

I'd suggest installing wvdial and use it to troubleshoot your problem.
It can be found in the Synaptics Package Manager.  (You run it from a
Terminal Window or Console, leaving that window minimized.)

Once that is done, you will need to set up the pap-secrets and/or chap-secrets
file by running the following in a Terminal Window:
```

sudo pppconfig

```You will need your userlogin, password, ISP provider information, and
pap or chap information for the connection. (You can set up pap and
then chap, if pap doesn't work.) Basically you just answer the questions
that are presented. You can delete a configurations and start over if
you need to from the menu selections.

For more information try:
```

man pppd
man pppconfig

```/etc/ppp/pap-secrets file contains:
(NOTE: File Format for 10.04)
```

# Every regular user can use PPP and has to use passwords from /etc/passwd
*       hostname        ""      *

# UserIDs that cannot use PPP at all. Check your /etc/passwd and add any
# other accounts that should not be able to use pppd!
guest   hostname        "*"     -
master  hostname        "*"     -
root    hostname        "*"     -
support hostname        "*"     -
stats   hostname        "*"     -

# OUTBOUND connections

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.
#       *       password
"yourusername@yourisp.net" provider "yourpassword"

```Now after ppp is setup, you will need to set up wvdial. Power up the modem,
and connect it to your serial port.  In a Terminal window do:
```

sudo wvdialconf /etc/wvdial.conf

```You should get a configuration file like this at
/etc/wvdial.conf (you may need to add a few things...)

wvdial.conf contains:
```

[Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 48800
New PPPD = yes
Stupid mode = yes
;carrier check = no
Modem = /dev/ttyACM0
ISDN = 0
Phone = 4460568
Password = yourpassword
Username = yourusername@yourisp.net

```You might want to double check the following settings:
Checking settings of: /etc/ppp/options
```

asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

```You also need to do this after wvdial is installed and
after pppconfig is executed:

Now assuming that your pap-secrets and or your chap-secrets file is
correct you should be able to use wvdial to dial the connection with:
```

wvdial /etc/wvdial.conf

```You should hear the modem go OFFHOOK with dialtone, Dial, and connect.
REMEMBER after wvdial dials, you can pick up a handset and monitor the
activity by listening to what is going on with the communications.
If your config file is correct you should authenticate and then control
will be passed to ppp. You will see several strings of HEX (funny characters)
and then you should stay connected. (you will use CNTL C to
terminate the session when you are done, but for this session you MUST
leave the Terminal window OPEN...) You may have to uncheck the box
marked OFFLINE when you open your browser to make it online. Surf,
then terminate the open session with CNTL C in the open terminal window
where you initiated wvdial.

Now that it works set up Gnome-PPP.


lk


I am running into problems with wvdial /etc/wvdial.conf.  Here is the output on the screen for this command:
   [B]--> WvDial: Internet dialer version 1.60
   --> Warning: section [Dialer /etc/wvdial.conf] does not exist in wvdial.conf.
   --> Initializing modem.
   --> Sending: ATZ
   ATZ
   OK
   --> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
   ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
   OK
   --> Modem initialized.
   --> [COLOR=Red]Configuration does not specify a valid phone number.
   --> Configuration does not specify a valid login name.
   --> Configuration does not specify a valid password.[/COLOR][/B]

When I did "sudo pppconfig" I first tried the pap-secrets setup.  Since that did not work, I then setup the chap-secrets.  But that way does not work either.

On both attempts, I issued the command "sudo wvdialconf /etc/wvdial.conf"._  I am absolutely sure that I input phone number, login name, and password for both attempts!_  So, I do not understand why wvdial is saying that all that information is missing...

This is the output of file wvdial.conf:
   [B][Dialer Defaults]
   Init1 = ATZ
   Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
   Modem Type = Analog Modem
   [COLOR=Red]; Phone = <Target Phone Number>[/COLOR]
   ISDN = 0
   [COLOR=Red]; Password = <Your Password>[/COLOR]
   New PPPD = yes
   [COLOR=Red]; Username = <Your Login Name>[/COLOR]
   Modem = /dev/ttyS2
   Baud = 115200[/B]

I am unable to change anything in file wvdial.conf.  (I was going to add _phone number_, _password_, and _username_ info since they are not there!)  The file appears to be read only and won't let me make changes!

I am unable to check what is inside chap-secrets and pap-secrets file!  When I click on either file, I get a window that says that I do not have the permissions necessary to open the files.

---

### Post by lkraemer on 2010-11-06
You just need to have root privileges to edit the file.

So open a Terminal and do:
```

cd /
pwd
cd /etc
pwd
ls -alt
sudo nano wvdial.conf

```
Then save and exit the file after you add loginname, password, and Phone number.

You should really try pap vs chap, so configure it for pap.  That should work.

You can skip the edit of /etc/ppp/options as it should be correct.

lk

---

### Post by tb75252 on 2010-11-06
> **lkraemer said:**
> You just need to have root privileges to edit the file.

So open a Terminal and do:
```

cd /
pwd
cd /etc
pwd
ls -alt
sudo nano wvdial.conf

```Then save and exit the file after you add loginname, password, and Phone number.

You should really try pap vs chap, so configure it for pap.  That should work.

You can skip the edit of /etc/ppp/options as it should be correct.

lk

Thanks for your help.  Everything went fine with the edit of file wvdial.conf.

Unfortunately, I still cannot connect to the ISP.  This is a portion of what I see on the Terminal when I launch "wvdial /etc/wvdial.conf" (it does not matter whether using pap or chap).  I've **[COLOR=DarkOrange]edited[/COLOR]** phone number, username and password for security reasons.

It appears to me that there is a problem with sending my password.  Inbetween the lines "**[COLOR=DarkOrange]Sending: [username edited][/COLOR]**" and "[COLOR=Red]**Nam**[/COLOR]**[COLOR=Red]e, password pair incorrect[/COLOR]**[COLOR=Red][COLOR=Black]"[/COLOR][/COLOR]the program is sending again my username ([COLOR=Lime]**[username edited]**[COLOR=Black])[/COLOR][/COLOR] whereas it should be sending my password, right?  Again, I am absolutely sure that wvdial.conf now has the correct username, password, and phone number.  I also have made sure that I am inputting all the right information when I run "sudo pppconfig" (pap or chap). 

[B]--> WvDial: Internet dialer version 1.60
--> Warning: section [Dialer /etc/wvdial.conf] does not exist in wvdial.conf.
--> Cannot set information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT[COLOR=DarkOrange][phone # edited][/COLOR]
--> Waiting for carrier.
ATDT[/B]**[COLOR=DarkOrange][phone # edited][/COLOR]**
[B]CONNECT 48000/ARQ/V92/LAPM/V42BIS
--> Carrier detected.  Waiting for prompt.
STATION ID - dlltx06rh11hp018,dlltx41ev
Welcome 
Please Sign-on: 
--> Looks like a login prompt.
--> Sending: [/B]**[COLOR=DarkOrange][username edited][/COLOR]**
[COLOR=Lime]**[username edited]**[/COLOR]
[COLOR=Red]**Nam**[/COLOR][B][COLOR=Red]e, password pair incorrect[/COLOR]
[/B]

---

### Post by lkraemer on 2010-11-06
OK, your wvdial.conf in /etc should look something like this with
your updates for loginname, password, and phonenumber.
loginname=joeY@swbell.net
password=mypassword
phonenumber=1234554
```

[Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 48800
New PPPD = yes
Stupid mode = yes
;carrier check = no
Modem = /dev/ttyS2
ISDN = 0
Phone = 1234554
Password = mypassword
Username = joeY@swbell.net

```
Check it line by line, but yours may be slightly different because of
hardware etc.

Then run pppconfig again and delete the configuration file for pap,
and create it again.

[B]If your config file is correct wvdial should authenticate and then control
will be passed to ppp. You will see several strings of HEX (funny characters)
and then you should stay connected. (you will use CNTL C to
terminate the session when you are done, but for now you MUST
leave the Terminal window OPEN...)[/B]

lk

---

### Post by jtarin on 2010-11-07
> **Old *ix Geek said:**
> Well, that's your opinion--and you know what they say [**_about opinions_**](http://www.cafepress.com/saproducts/1019475). :D 


In my opinion, especially regarding US Robotics modems--which I used for many, many years on Linux without issue--when the manufacturer itself lists Linux in its OS compatibility list, I don't consider it to be a win-anything. But then, that's my opinion. :)

Sure I have opinions, but I usually try to keep them to myself. I only try to quote a consensus on subjects and evidently you haven't used Robotics long enough> [Q: What modem should I buy to achieve best results on my Linux workstation?]("http://linuxmafia.com/faq/VALinux-kb/modems-for-linux.html")

A: Since people hold strong views on this matter, and prefer modems of different varieties, it is perhaps best to detail modem taxonomy before making a recommendation and explaining its rationale. Readers interested only in a recommendation can skip to the "Conclusion" section at the bottom.

Modems can be either regular modem devices or so-called "winmodems". (**"Winmodem" is a registered trademark of US Robotics, Inc.,** but the term is widely used to describe modems of non-traditional design that can be communicated with only using custom driver software.) Regular modems can be either internal on an add-in card that fits inside the PC system case or external, encased in a separate box with its own power supply, connected to either one of the PC's serial ports using a serial (RS-232C) cable, or to a USB bus. To date, all known "winmodems" have been either internal or USB-type, but there have also been some claims of external winmodems.

---

### Post by QLee on 2010-11-07
jtarin,
Since I can be, and usually am, as pedantic as anyone else, I have another OT comment, or I suppose I should call it an opinion.

Yes, I was aware of the copyright, however your statement was, "In Linux parlance". It would probably have been more correct to state, in USRobotics parlance. 

I'm sure you know as well as I do that most GNU/Linux users just use the term "winmodem" to refer to the host controlled processing types of modems and "hardware modem" as the other type that has it's own processor. We can take the space to discuss this because the OP is getting great help and this shouldn't be confusing the issue of dial-up configuration and I think we all can benefit from defining our terms correctly so that we avoid confusion.

I no longer miss the tiger, I now see the tiger in mickey's eyes. :-)

---

### Post by jtarin on 2010-11-07
> **QLee said:**
> jtarin,
Since I can be, and usually am, as pedantic as anyone else, I have another OT comment, or I suppose I should call it an opinion.

Yes, I was aware of the copyright, however your statement was, "In Linux parlance". It would probably have been more correct to state, in USRobotics parlance. 

I'm sure you know as well as I do that most GNU/Linux users just use the term "winmodem" to refer to the host controlled processing types of modems and "hardware modem" as the other type that has it's own processor. We can take the space to discuss this because the OP is getting great help and this shouldn't be confusing the issue of dial-up configuration and I think we all can benefit from defining our terms correctly so that we avoid confusion.

I no longer miss the tiger, I now see the tiger in mickey's eyes. :-)
The copyright blurb was posted for the benefit of the unenlightened.Avoiding confusion is my desire and not my opinion. :P

---

### Post by tb75252 on 2010-11-08
> **lkraemer said:**
> OK, your wvdial.conf in /etc/ppp should look something like this with
your updates for loginname, password, and phonenumber.
loginname=joeY@swbell.net
password=mypassword
phonenumber=1234554
```

[Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 48800
New PPPD = yes
Stupid mode = yes
;carrier check = no
Modem = /dev/ttyS2
ISDN = 0
Phone = 1234554
Password = mypassword
Username = joeY@swbell.net

```Check it line by line, but yours may be slightly different because of
hardware etc.

Then run pppconfig again and delete the configuration file for pap,
and create it again.

[B]If your config file is correct wvdial should authenticate and then control
will be passed to ppp. You will see several strings of HEX (funny characters)
and then you should stay connected. (you will use CNTL C to
terminate the session when you are done, but for now you MUST
leave the Terminal window OPEN...)[/B]

lk

In a previous post you stated that wvdial.conf should be located in subdirectory /etc.
I see that now you mention subdirectory /etc/ppp.  In which directory should the file be located?
Right now wvdial.conf is located in subdirectory /etc.  Should I move it from there?

---

### Post by QLee on 2010-11-08
[QUOTE=jtarin]The copyright blurb was posted for the benefit of the unenlightened.Avoiding confusion is my desire and not my opinion. :P[/QUOTE]
Cool. Avoiding confusion is my desire also. Whether or not either of us is successful in that goal is a matter of opinion and I imagine we could find differing opinions in the forum members about that issue. :-)

BTW, I'm not the poster who brought up the term opinion.

I'm done now, over and out.

---

### Post by QLee on 2010-11-08
[QUOTE=tb75252]In a previous post you stated that wvdial.conf should be located in subdirectory /etc.
I see that now you mention subdirectory /etc/ppp.  In which directory should the file be located?
Right now wvdial.conf is located in subdirectory /etc.  Should I move it from there?[/QUOTE]
I'm not the poster you directed this question to but, since I'm here I'll answer.

No, don't move it. Read what that says again, it was mentioned that wvdial passes control to ppp.

Edit: You are getting good help, I apologise for the noise I have been a part of in your thread. Please don't let it distract you.

---

### Post by lkraemer on 2010-11-08
QLee is correct.

It should be in /etc

Sorry.  I'll edit the previous post.

Thanks.

LK

---

### Post by tb75252 on 2010-11-08
Thanks LK for all your help.  Unfortunately, I am still unable to connect to the ISP.

I have compared the wvdial.conf copy you posted with mine and made some changes.  This is how file wvdial.conf looked like _before_ the changes.  (I [COLOR=Lime]removed[/COLOR] some information for security reasons)

   	 	 	 	p { margin-bottom: 0.08in; }  **[Dialer Defaults]  **
 **Init1 = ATZ  **
 **Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0  **
 **Modem Type = Analog Modem  **
 **Phone = [COLOR=Lime][removed phone number][/COLOR]  **
 **ISDN = 0  **
 **Password = [COLOR=Lime][removed password][/COLOR]  **
 **New PPPD = yes  **
 **Username = [COLOR=Lime][removed username][/COLOR]  **
 **Modem = /dev/ttyS2  **
 **Baud = 115200**
 

 And this is the same file _after_ I made some changes and shuffled things around:
 

  **[Dialer Defaults]**
[B]Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 115200
New PPPD = yes
Stupid mode = yes
Modem = /dev/ttyS2
ISDN = 0
Phone = [COLOR=Lime][removed phone number][/COLOR]
Password =[COLOR=Lime] [removed password][/COLOR]
Username =[COLOR=Lime] [removed username][/COLOR]
[/B]
After having changed wvdial.conf I ran "sudo pppconfig", deleted the old  file and created a new one (pap).  After that, I ran "wvdial  /etc/wvdial.conf".  This is the full output of what I am getting.  I am  outlining a few things in red font because they appear to signal  problems.

   	 	 	 	p { margin-bottom: 0.08in; }  **--> WvDial: Internet dialer version 1.60 **
 **--> [COLOR=Red]Warning: section [Dialer /etc/wvdial.conf] does not exist in wvdial.conf.   [/COLOR]**
 **--> [COLOR=Red]Cannot set information for serial port.[/COLOR] **
 **--> Initializing modem. **
 **--> Sending: ATZ **
 **ATZ **
 **OK **
 **--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 **
 **ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 **
 **OK **
 **--> Modem initialized. **
 **--> Sending: ATDT[COLOR=Lime][removed phone number][/COLOR]**
 **--> Waiting for carrier. **
 **ATDT[COLOR=Lime][removed phone number][/COLOR]**
 **CONNECT 48000/ARQ/V92/LAPM/V42BIS **
 **--> Carrier detected.  Starting PPP immediately. **
 **--> Starting pppd at Mon Nov  8 21:43:24 2010 **
 **-->[COLOR=Red] Warning: Could not modify /etc/ppp/pap-secrets: Permission denied   [/COLOR]**
 **--> --> [COLOR=Red]PAP (Password Authentication Protocol) may be flaky.[/COLOR] **
 **--> [COLOR=Red]Warning: Could not modify /etc/ppp/chap-secrets: Permission denied   [/COLOR]**
 **--> --> [COLOR=Red]CHAP (Challenge Handshake) may be flaky.[/COLOR] **
 **--> Pid of pppd: 1518 **
 **--> Using interface ppp0 **
 **--> pppd: &#65533;&#65533;? &#65533;&#65533;?  **
 **--> pppd: &#65533;&#65533;? &#65533;&#65533;?  **
 **--> pppd: &#65533;&#65533;? &#65533;&#65533;?  **
 **--> pppd: &#65533;&#65533;? &#65533;&#65533;?  **
 **--> pppd: &#65533;&#65533;? &#65533;&#65533;?  **
 **--> local  IP address 12.74.228.122 **
 **--> pppd: &#65533;&#65533;? &#65533;&#65533;?  **
 **--> remote IP address 199.69.137.104 **
 **--> pppd: &#65533;&#65533;? &#65533;&#65533;?  **
 **--> primary   DNS address 68.94.156.1 **
 **--> pppd: &#65533;&#65533;? &#65533;&#65533;?  **
 **--> secondary DNS address 68.94.157.1 **
 [B]--> pppd: &#65533;&#65533;? &#65533;&#65533;? 
[/B]
 

 Despite the error messages outlined above, I decided to set up Gnome-PPP and dial in to see what would happen.  This is the full output of the log.  I am again highlighting a few things in red font because they might signal problems.  It would appear that somehow my username is still being sent in place of my password!
 

 [B]--> WvDial: Internet dialer version 1.60
--> [COLOR=Red]Cannot set information for serial port.[/COLOR]
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM0L0DT[COLOR=Lime][removed phone number][/COLOR]
--> Waiting for carrier.
ATM0L0DT[COLOR=Lime][removed phone number][/COLOR]
CONNECT 48000/ARQ/V92/LAPM/V42BIS
--> Carrier detected.  Waiting for prompt.
STATION ID - dlltx26rh10hp023,dlltx43ev
Welcome 
Please Sign-on: 
--> Looks like a login prompt.
--> Sending: [COLOR=Lime][removed username][/COLOR]
  [COLOR=Red][removed username][/COLOR]
  [COLOR=Red]Name, password pair incorrect[/COLOR]
Please Sign-on: 
--> Looks like a login prompt.
--> Sending: [COLOR=Lime][removed username][/COLOR]
  [COLOR=Red][removed username][/COLOR]
  [COLOR=Red]Name, password pair incorrect[/COLOR]
Please Sign-on: 
--> Looks like a login prompt.
--> Sending: [/B][B] [COLOR=Lime][removed username][/COLOR]
  [COLOR=Red][removed username][/COLOR][/B][B]
  [COLOR=Red]Name, password pair incorrect[/COLOR]
Please Sign-on: 
--> Looks like a login prompt.
--> Sending: [/B][B] [COLOR=Lime][removed username][/COLOR]
  [COLOR=Red][removed username][/COLOR][/B][B]
Login failed, reason = (-190,dlltx43ev,1289275565-000,dlltx26rh10hp023)
Connection closed by foreign host.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATM0L0DT[COLOR=Lime][removed phone number][/COLOR]
--> Waiting for carrier.
NO CARRIER
ATM0L0DT[/B]**[COLOR=Lime][removed phone number][/COLOR]**[B]
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATM0L0DT[/B]**[COLOR=Lime][removed phone number][/COLOR]**[B]
--> Waiting for carrier.
NO CARRIER
TM0L0DT[/B]**[COLOR=Lime][removed phone number][/COLOR]**[B]
--> No Carrier!  Trying again.
--> Maximum Attempts Exceeded..Aborting!!
--> Disconnecting at Mon Nov  8 22:06:26 2010[/B]

---

### Post by zer010 on 2010-11-09
:shock:Man alive! I'm probably going to be setting up a PC with Ubuntu running a dial-up connection. While I don't have the specs on the PC in question yet, I sure hope I wont be running into this much trouble!  If I do, at least I know to come to this thread.  OP, I wish I had advice to give, but in the mean time I wish you all the luck and hope you get your issue resolved.

---

### Post by QLee on 2010-11-09
tb75252,
What output do you get from the command, groups, in a terminal window?

---

### Post by lkraemer on 2010-11-09
It looks to me like you are connected,
wvdial dialed out, established a connection, then transfered to pppd:
```

--> Pid of pppd: 1518
--> Using interface ppp0
--> pppd: &#65533;&#65533;? &#65533;&#65533;?
--> pppd: &#65533;&#65533;? &#65533;&#65533;?
--> pppd: &#65533;&#65533;? &#65533;&#65533;?
--> pppd: &#65533;&#65533;? &#65533;&#65533;?
--> pppd: &#65533;&#65533;? &#65533;&#65533;?
--> local IP address 12.74.228.122
--> pppd: &#65533;&#65533;? &#65533;&#65533;?
--> remote IP address 199.69.137.104
--> pppd: &#65533;&#65533;? &#65533;&#65533;?
--> primary DNS address 68.94.156.1
--> pppd: &#65533;&#65533;? &#65533;&#65533;?
--> secondary DNS address 68.94.157.1
--> pppd: &#65533;&#65533;? &#65533;&#65533;? 

```

Just leave this window open, then open Firefox, and see if your browser
works.  Then when you are finished surfing, close your browser, go back
to the Terminal Window where you ran wvdial, and do a:
CNTL C
That will terminate the connection.  You are finished so close the Terminal Window.

Next time repeat the process.

When this works set up Gnome-PPP.

LK

---

### Post by tb75252 on 2010-11-09
> **QLee said:**
> tb75252,
What output do you get from the command, groups, in a terminal window?

Here's the output:
tb adm dialout cdrom dip plugdev lpadmin admin sambashare

PS:  "tb" is my username.

---

### Post by tb75252 on 2010-11-09
> **lkraemer said:**
> It looks to me like you are connected,
wvdial dialed out, established a connection, then transfered to pppd:
```

--> Pid of pppd: 1518
--> Using interface ppp0
--> pppd: &#65533;&#65533;? &#65533;&#65533;?
--> pppd: &#65533;&#65533;? &#65533;&#65533;?
--> pppd: &#65533;&#65533;? &#65533;&#65533;?
--> pppd: &#65533;&#65533;? &#65533;&#65533;?
--> pppd: &#65533;&#65533;? &#65533;&#65533;?
--> local IP address 12.74.228.122
--> pppd: &#65533;&#65533;? &#65533;&#65533;?
--> remote IP address 199.69.137.104
--> pppd: &#65533;&#65533;? &#65533;&#65533;?
--> primary DNS address 68.94.156.1
--> pppd: &#65533;&#65533;? &#65533;&#65533;?
--> secondary DNS address 68.94.157.1
--> pppd: &#65533;&#65533;? &#65533;&#65533;? 

```Just leave this window open, then open Firefox, and see if your browser
works.  Then when you are finished surfing, close your browser, go back
to the Terminal Window where you ran wvdial, and do a:
CNTL C
That will terminate the connection.  You are finished so close the Terminal Window.

Next time repeat the process.

When this works set up Gnome-PPP.

LK

You are right.  The "wvdial /etc/wvdial.conf" does indeed establish a connection with the ISP and I am able to open a browser that way.  The problem now is that I am unable to set up Gnome-ppp...

I have been extra careful to input my password into the Gnome-ppp window and I clicked the box for remembering the password too!  Still, it appears that Gnome-ppp is passing my username instead of the password as shown in the following output of the connection log (see lines highlighted in red color and the comment made in blue color):

[B]--> WvDial: Internet dialer version 1.60
--> Cannot set information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM0L0DT[COLOR=Lime][removed phone number][/COLOR]
--> Waiting for carrier.
ATM0L0DT[COLOR=Lime][removed phone number][/COLOR]
CONNECT 48000/ARQ/V92/LAPM/V42BIS
--> Carrier detected.  Waiting for prompt.
STATION ID - dlltx27rh05hp011,dlltx43ev
Welcome 
Please Sign-on: 
--> Looks like a login prompt.
--> Sending: [COLOR=Lime][removed username][/COLOR]
[COLOR=Red][removed username]      [COLOR=DeepSkyBlue]<---There should be my password here, not my
                                           username again!![/COLOR][/COLOR]
[COLOR=Red]Name, password pair incorrect[/COLOR]
Please Sign-on: 
--> Looks like a login prompt.
--> Sending: [COLOR=Lime][removed username][/COLOR]
[COLOR=Red][removed username]
Name, password pair incorrect[/COLOR]
Please Sign-on: 
--> Looks like a login prompt.
--> Sending: [COLOR=Lime][removed username][/COLOR]
[COLOR=Red][removed username]
Name, password pair incorrect[/COLOR]
Please Sign-on: 
--> Looks like a login prompt.
--> Sending: [COLOR=Lime][removed username][/COLOR]
[COLOR=Red][removed username][/COLOR]
Login failed, reason = (-190,dlltx43ev,1289357946-000,dlltx27rh05hp011)
Connection closed by foreign host.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATM0L0DT[COLOR=Lime][removed phone number][/COLOR]
--> Waiting for carrier.
NO CARRIER
ATM0L0DT[COLOR=Lime][removed phone number][/COLOR]
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATM0L0DT[COLOR=Lime][removed phone number][/COLOR]
--> Waiting for carrier.
NO CARRIER
ATM0L0DT[COLOR=Lime][removed phone number][/COLOR]
--> No Carrier!  Trying again.
--> Maximum Attempts Exceeded..Aborting!!
--> Disconnecting at Tue Nov  9 20:59:27 2010[/B]

---

### Post by tb75252 on 2010-11-09
> **zer010 said:**
> :shock:Man alive! I'm probably going to be setting up a PC with Ubuntu running a dial-up connection. While I don't have the specs on the PC in question yet, I sure hope I wont be running into this much trouble!  If I do, at least I know to come to this thread.  OP, I wish I had advice to give, but in the mean time I wish you all the luck and hope you get your issue resolved.

A word of advice from a newbie:  Make sure that the sound chip installed on your motherboard (or the sound card, if you will be installing one) is compatible with ALSA!

I installed openSUSE 11.3 on a computer with a dedicated sound card made by Creative Labs (model is Sound Blaster X-Fi Xtreme Audio, PCI-E interface) and was never able to get any audio out to my speakers.  In desperation and after a week of back-and-forth with the openSUSE forum people, I removed the Sound Blaster card and installed an ASUS Xonar (PCI-E interface).  After a little bit more tinkering, I finally had sound!

Apparently, not all audio card manufacturers fully cooperate with the Linux developers and drivers for sound cards (or sound chips) are nonexistent or (sometimes) have serious bugs in them.  The end result is that some sound cards/chips just do now work with Linux -- or have their features curtailed!

To get an idea of what works and what does not, go to: [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main) and click on the manufacturer of your sound card/chip.

Hope you'll have better luck than I.

---

### Post by lkraemer on 2010-11-10
OK, go back and look at the Gnome-PPP Pictures on my posting #3.

You know the Device (/dev/ttyS2) and you know your loginname & password,
and the Phone number.

Your loginname is something like **JoeSmoot@copper.net** not just **JoeSmoot**, 
and your password is something like **MyPassWord**.  Add these to the Setup in Photo one.
Set the Device to /dev/ttyS2.  Then check your settings for Photo's two and three against
the other two Photo's.  (These settings worked for me with Copper.net)

It works when you have the proper information inserted.

It appears you are somehow trying to log in to something other than
your ISP.
```

STATION ID - dlltx27rh05hp011,dlltx43ev
Welcome
Please Sign-on: 

```
as this doesn't appear to be normal.

lk

---

### Post by _duncan_ on 2010-11-10
@lkraemer

I looked at posting #3. In the wvdial configuration (/etc/wvdial.conf), "Stupid mode = yes".

However in photo 3 (gnome-ppp), the "Ignore terminal strings (stupid mode)" checkbox is unchecked.

It's a long shot, but perhaps it can account for the error in gnome-ppp for the OP?

---

### Post by lkraemer on 2010-11-10
That could be possible, but the settings in the Photo's are exactly what 
I use to connect to my dialup ISP, so they should work for him.

Thanks.

LK

---

### Post by tb75252 on 2010-11-10
> **_duncan_ said:**
> @lkraemer

I looked at posting #3. In the wvdial configuration (/etc/wvdial.conf), "Stupid mode = yes".

However in photo 3 (gnome-ppp), the "Ignore terminal strings (stupid mode)" checkbox is unchecked.

It's a long shot, but perhaps it can account for the error in gnome-ppp for the OP?

Thanks for the tip!  After I checked the box "Ignore terminal strings (stupid mode)" in the Gnome-ppp setup file and rebooted I was finally able to connect with my analog modem.

---

### Post by tb75252 on 2010-11-10
> **lkraemer said:**
> That could be possible, but the settings in the Photo's are exactly what 
I use to connect to my dialup ISP, so they should work for him.

Thanks.

LK

Success at last!  _duncan_'s tip about the string "Stupid mode = yes" in my wvdial.conf file was right on target.  I checked the box "Ignore terminal strings (stupid mode)" in the Gnome-ppp setup window (Options tab), rebooted, and now I am able to connect to my ISP using the analog modem.
Thanks again for all your help and patience!

---

### Post by wkhasintha on 2010-11-11
That could be possible, but the settings in the Photo's are exactly what 
I use to connect to my dialup ISP, so they should work for him.

Thanks.

---

### Post by zer010 on 2010-11-16
> **tb75252 said:**
> A word of advice from a newbie:  Make sure that the sound chip installed on your motherboard (or the sound card, if you will be installing one) is compatible with ALSA!

I installed openSUSE 11.3 on a computer with a dedicated sound card made by Creative Labs (model is Sound Blaster X-Fi Xtreme Audio, PCI-E interface) and was never able to get any audio out to my speakers.  In desperation and after a week of back-and-forth with the openSUSE forum people, I removed the Sound Blaster card and installed an ASUS Xonar (PCI-E interface).  After a little bit more tinkering, I finally had sound!

Apparently, not all audio card manufacturers fully cooperate with the Linux developers and drivers for sound cards (or sound chips) are nonexistent or (sometimes) have serious bugs in them.  The end result is that some sound cards/chips just do now work with Linux -- or have their features curtailed!

To get an idea of what works and what does not, go to: [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main) and click on the manufacturer of your sound card/chip.

Hope you'll have better luck than I.
Thanks for the tip, but my Lucid install is running pretty sweet. My step-dad's machine might be another story.... Next time I take the trip over there, I might be installing Ubuntu on a machine with nothing but Dial-up access only.  I'm glad to see your problem has been solved.  I'll probably be referring to this thread if I get into any trouble. Good thing he's got a laptop running Win7 that CAN get online so I won't be stuck! Who knows, he might convert that one or at least dual-boot....:)

---

