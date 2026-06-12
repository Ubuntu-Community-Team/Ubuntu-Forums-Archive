---
title: "Intel Pro 3945 &amp; Kismet"
date: 2006-08-21
forum: Networking &amp; Wireless
---

### Post by Midgard on 2006-08-21
Greetings all,

today i came upon a strange problem in Ubuntu.
I have this great wifi card from Intel and Ubuntu 6.06, the wifi card works great and driver support came out of the box. I can connect to internet using the network manager from gnome.

As happy as i was this worked and I proceded installing Kismet

$ apt-get install kismetc

next i configure kismet ( /etc/kismet/kismet.conf ) and changed the source to: source=ipw3945,eth1,Centrino_ag

output from iwconfig:

> midgard@midgard-laptop:/$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      **unassociated**  ESSID:off/any
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:16 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:749   Missed beacon:0

hence my wifi card is NOT connected to the internet at this time!

so i start kismet

> midgard@midgard-laptop:/$ sudo kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
FATAL: Unknown capture source type 'ipw3945' in source 'ipw3945,eth1,Centrino_ag'

so i dont know how to get kismet working here. What am i doing wrong?
I booted up Mpentoo live cd were Kismet is working OK with this source, i copied it exactly from the mpentoo config.

Can anyone help me out here?

BTW: lsmod | grep ipw also shows ipw3945 & ieee in use so that should be ok i guess.

Thanks in advance,
Midgard

---

### Post by Midgard on 2006-08-21
Hello all, I fixed the problem after searching deeper in the forums.

I will try to explain the problem for everybody with this problem.

Kismet needs to be compiled manually! The pre-build packages will not work with ipw3945.
So go to the kismet website and download the source.

You will need extra libraries to compile so I'm reffering to this thread:

[http://www.ubuntuforums.org/showthread.php?t=195235&highlight=kismet+ipw3945]("http://www.ubuntuforums.org/showthread.php?t=195235&highlight=kismet+ipw3945")

after compiling Kismet edit the config file:

source=ipw3945,eth1,Intel

Good luck!

---

### Post by morphet on 2007-01-17
Man. Thank you Midgard :)

---

### Post by Metallinut on 2007-03-28
> **Midgard said:**
> Hello all, I fixed the problem after searching deeper in the forums.

I will try to explain the problem for everybody with this problem.

Kismet needs to be compiled manually! The pre-build packages will not work with ipw3945.
So go to the kismet website and download the source.

You will need extra libraries to compile so I'm reffering to this thread:

[http://www.ubuntuforums.org/showthread.php?t=195235&highlight=kismet+ipw3945]("http://www.ubuntuforums.org/showthread.php?t=195235&highlight=kismet+ipw3945")

after compiling Kismet edit the config file:

source=ipw3945,eth1,Intel

Good luck!

I managed to build kismet from source...but it still is giving me the
```
FATAL: Support for capture source type 'ipw3945' was not built.  Check the output from 'configure' for more information about why it might not have been compiled in.

```

My kismet.conf has
source=ipw3945,eth1,Intel

What did I do wrong?

---

### Post by OuTcRy on 2007-05-13
my problem is the same too

---

### Post by chili555 on 2007-05-13
> The pre-build packages will not work with ipw3945I don't agree. I got it to work perfectly with the following steps:```
sudo apt-get install kismet
sudo vim /etc/kismet/kismet.conf
```Amend the suid user to chili, amend the source to ipw3945,eth1,Intel. Save and close.```
sudo iwconfig eth1 mode monitor
sudo kismet
```Remember to return the card's mode to managed when you finish kismet.

Works fine.

---

### Post by Adnarim on 2007-08-19
I also tried to install kismet and failed :(

I did sudo apt-get install kismet and modified suid user and source as said here. But then I tried to switch my card to monitor mode and nothing happens?

```

laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID: removed 
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:15:0C:72:4D:FD   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=63/100  Signal level=-69 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:134404   Missed beacon:0

laptop:~$ **sudo iwconfig eth1 mode monitor**
laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID: removed
          Mode:**Managed**  Frequency:2.437 GHz  Access Point: 00:15:0C:72:4D:FD   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=63/100  Signal level=-68 dBm  Noise level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:134404   Missed beacon:0

laptop:~$ 

```

What did I wrong? There was no error-message but I didn't succed with switching the cards-mode? If I try no to start kismet I get:
```

laptop:~$ sudo kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Will drop privs to myusername (1000) gid 1000
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
FATAL: Support for capture source type 'ipw3945' was not built.  Check the output from 'configure' for more information about why it might not have been compiled in.
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}

```

Can someone provide help with this problem?

greets

---

### Post by obitori on 2007-08-30
1.Identify your wireless card.  I used &#8220;lspci&#8221; and got the following (snipped) results for my Dell D820:
[FONT="Courier New"]
> lspci[/FONT]

0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)


2.  I googled this controller (&#8220;3945ABG&#8221;) and found this Ubuntu forum thread.  

3.  I went to the below website and downloaded the latest stable version of Kismet:
[FONT="Courier New"]
[http://www.kismetwireless.net/download.shtml](http://www.kismetwireless.net/download.shtml)
[/FONT]
4.  I de-archived the tar.gz file:
[FONT="Courier New"]
> tar -xzvf kismet*.tar.gz
[/FONT]
5. I went into the working directory for the source file and configured the make file.  I could have just used './configure'.  But that puts all the kismet files in the /usr/local/etc/ directory.  I am good with the location because non-Ubuntu official repository files should be segregated from the normal packages, but there are quite a few config files now for kismet and I wanted them in their own subdirectory to etc, so I used:
[FONT="Courier New"]
> cd kismet*01b
> ./configure --sysconfdir=/usr/local/etc/kismet
[/FONT]

6. I bumped into two missing libraries.  Per earlier threads, I downloaded the '*-dev' version of the .deb packages for the missing libraries.  (In fact the two missing libraries were installed as non &#8220;dev&#8221; packages.)  The missing libraries for my new install (with a number of automatix2 packages added) were &#8220;libncurses&#8221; and &#8220;libpcap&#8221;.  Warning&#8212;The missing libncurses will stop './configure' with an error but libpcap only gives a warning&#8212;but it's absence will cause you to lose extremely important packet collection capabilities.  I used synaptic to check the latest available versions of the libraries and then added them on the command line as follows:
[FONT="Courier New"]
> sudo apt-get install libncurses-dev

> sudo apt-get install libpcap0.8-dev[/FONT]


7. The generic name (without the release number) installed the latest version of libncurses, but installed libpcap0.7, so I removed it and installed (according to synaptic) the latest version.  (I had no reason to do so other than the assumption that newer is better.)  Finally, './configure' completed correctly, but I did &#8220;make dep&#8221; just to be sure:
[FONT="Courier New"]
> make dep[/FONT]

8.a. Then, rather than install the source directly, I made a .deb package with it using checkinstall.  First, I installed that program (which replaces 'make' and 'make install') with a program that makes a .deb package and installs that.  I typed:
[FONT="Courier New"]
sudo apt-get install checkinstall[/FONT]

8.b.  Next, I used 'checkinstall' to compile the source.  There are two different ways to use 'checkinstall'.  I tried both and both worked.  The install portion of the command has produced some errors in the past so foolproof but more complicated way is to use 'checkinstall' only to build the .deb package and install it with dpkg.  (The second way is simpler.  I just typed &#8220;sudo checkinstall&#8221; and it compiled a .deb package and installed it in one step.  No hassles, no need to remember &#8220;-d &#8211;install=no&#8221; options...If you go this route, skip to step #11 below.)
[FONT="Courier New"]
> sudo checkinstall -D &#8211;install=no
[/FONT]
9. This produced the following message:
[FONT="Courier New"]
********************************************************


 Done. The new package has been saved to



 /home/bud/kismet-2007-01-R1b/kismet-2007-01_R1b-1_i386.deb

 You can install it in your system anytime using: 



      dpkg -i kismet-2007-01_R1b-1_i386.deb



*********************************************************[/FONT]

10.  I typed the above in exactly as told.  I also saved a copy of the .deb file to /usr/local/src for future use.  
[FONT="Courier New"]
> dpkg -i kismet-2007-01_R1b-1_i386.deb
[/FONT]

Note that the .deb you created and installed will be viewable if you search &#8220;kismet&#8221; from synaptic or any other apt-based package handler.  

11.  Now, you need to edit the .conf file.  remember the switch I added to the &#8220;./configure&#8221;, so I edited the config file located within '/usr/local/etc/kismet':
[FONT="Courier New"]
> sudo vi /usr/local/etc/kismet/kismet.conf
[/FONT]
The relevant portion (after the changes) looks like:
[FONT="Courier New"]
# Name of server (Purely for organizational purposes)

servername=Kismet_Potomac



# User to setid to (should be your normal user)

suiduser=bud



# Sources are defined as:

# source=sourcetype,interface,name[,initialchannel]

# Source types and required drivers are listed in the README under the

# CAPTURE SOURCES section.

# The initial channel is optional, if hopping is not enabled it can be used

# to set the channel the interface listens on.

# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE



source=ipw3945,eth1,intelpro

[/FONT]
Please note that the raw sources put your log files in a hidden '.kismet' directory in the home directory of the user specified in the kismet.conf file (i.e., '/home/user/.kismet').  The Ubuntu package, however, puts it in /var/log/kismet.  You can have the raw .deb that you built mimic the Ubuntu package by editing the kismet.conf file's configdir= variable to look like &#8220;configdir=/var/log/kismet/&#8221;.  You will also need to create the 'kismet' directory within '/var/log' and set its ownership and permissions to let the kismet program write to files as the user that you specified above within the '/var/log/kismet' directory.

12.  Now, I use sudo to execute the executable and I'm good to go:
[FONT="Courier New"]
sudo kismet[/FONT]

This worked for me.  Have fun.  Check out gpsdrive...BTW, does anyone have any idea if the current driver supports the A mode for this PRO/Wireless?  Just curious...

---

### Post by LAD29 on 2007-11-03
Did you guys find a solution to this?

"Support for capture source type 'ipw3945' was not built"

---

### Post by ankuryu on 2007-11-17
Hi Obitori 

I did just as you have show. Yet I get the same error

"Support for IPW3945 is not built in, check the configure file......"

Can someone help me locate the error from the configure.log file , I see no errors in it.
also the exit code = 0.  Yet I am not able to run kismet.

Also I 1st carried out  everything ( ./configure, make , make install) ,
 However I had missed out the libpcap*.dev file. 
  Rather than to uninstall the kismet, I carried out the procedures as mentioned by you and generated the kismet * .deb file after installing the libpcap*.dev file.  Later on  I Installed the deb file.

Yet it keeps giving me the same error

Ankuryu :confused:

My config : DELL Lattitude 520, with 1GB Ram 160 GB HD with KUbuntu Fiesty Fawn, contains Intel PRO 3945 Wireless Card.

---

### Post by mitpat on 2007-11-25
> **chili555 said:**
> I don't agree. I got it to work perfectly with the following steps:```
sudo apt-get install kismet
sudo vim /etc/kismet/kismet.conf
```Amend the suid user to chili, amend the source to ipw3945,eth1,Intel. Save and close.```
sudo iwconfig eth1 mode monitor
sudo kismet
```Remember to return the card's mode to managed when you finish kismet.

Works fine.

for some reason i can't do the bit after the first quote as it won't let me save it, i'm the only user (and admin) so why does it refuse to save?

---

### Post by ramon243 on 2007-11-25
Hi
I had many trouble compiling it myself, and I just installed it using apt. I did not edit the configuration file, so every time I run it I type:
```
sudo kismet -c ipw3945,eth1,ipw3945
```
It works fine for me

---

### Post by belleg on 2007-12-08
> **ankuryu said:**
> Hi Obitori 

I did just as you have show. Yet I get the same error

"Support for IPW3945 is not built in, check the configure file......"

Can someone help me locate the error from the configure.log file , I see no errors in it.
also the exit code = 0.  Yet I am not able to run kismet.

Also I 1st carried out  everything ( ./configure, make , make install) ,
 However I had missed out the libpcap*.dev file. 
  Rather than to uninstall the kismet, I carried out the procedures as mentioned by you and generated the kismet * .deb file after installing the libpcap*.dev file.  Later on  I Installed the deb file.

Yet it keeps giving me the same error

Ankuryu :confused:

My config : DELL Lattitude 520, with 1GB Ram 160 GB HD with KUbuntu Fiesty Fawn, contains Intel PRO 3945 Wireless Card.


Hi guys, if you install kismet with "sudo make suidinstall" it will fix your problem (atleast it did it for me).

---

### Post by busquelo on 2008-01-17
Hello, 
I just wanted to say thanks. I followed your instructions exactly how you specified and successfully installed and ran Kismet. I'm on an Acer Aspire 5670. Cheers!

---

### Post by PeeZz on 2008-01-21
I've tried so much bit still it doesn't work for me.
I have a HP Compaq nc6320 with Ubuntu 7.10 installed.

when I put my wireless card in monitor mode it works, but only for 5 seconds.
After that my card returns to managed mode.

Can you help me?

Henri

EDIT: My problem's solved now. I switched off  "use wireless network".

---

### Post by dhysk on 2008-01-22
Ok this is how i got it to work on mine.  I have a HP dv6????us ,forgot the actual model, with the IPW3945, running Linux 7.10.  I'm a brand new to Linux so this may not be the best way but it works and as a newb i can't guarantee you wont break something

#1 sudo apt-get install kismet
     this installed kismet -v 2007.01.R1

#2 go down to the little wireless manager icon left click and uncheck Enable Wireless
    Not necessary but makes it easier to reconnect after you turn off kismet

#3 sudo kismet -c ipw3945,eth1,ipw3945
     kismet should run at this point if it does go to step #4

#4 sudo gedit /etc/kismet/kismet.conf and change to : source=ipw3945,eth1,ipw3945
    this saves the -c blabla,eth1,blablabla part when you start kismet

#5 type sudo kismet
    should work fine now.  It does seam take a bit for kismet to quit.  I'm guessing it has an issue taking it out of monitor mode.  Either way if you followed step 2 you can just recheck the Enable Wirles box if not you will probably have to do one or both of the following

sudo iwconfig eth1 mode mon
sudo iwconfig eth1 mode man 

and/or sudo ifconfig eth1 down
          sudo ifconfig eth1 up

hope this helps... bye the way so far Linux ROCKS ;)

---

