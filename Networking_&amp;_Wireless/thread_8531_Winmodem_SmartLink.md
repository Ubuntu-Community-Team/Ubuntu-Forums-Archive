---
title: "Winmodem SmartLink"
date: 2004-12-18
forum: Networking &amp; Wireless
---

### Post by Smash on 2004-12-18
Hello, i have a problem.
I can't connect!  ](*,) 

Drivers are OK, but Wvdial returns an error: "NO DIALTONE".

I have to put a string in wvdial.conf, but does not work!
I don't know where i've to put this string.

Thanks

---

### Post by sylvinho on 2005-01-15
hello smash

i'd like to know if it's possible to make winmodems run, and especially smart link winmodem  under ubuntu, and how it's possible ? which drivers .... ? explain me please

d'you still have problems to connect ?

thks

---

### Post by az on 2005-01-15
Download this:
[http://linmodems.technion.ac.il/packages/scanModem.gz](http://linmodems.technion.ac.il/packages/scanModem.gz)
Here is the info page.
[http://linmodems.technion.ac.il/#scanmodem](http://linmodems.technion.ac.il/#scanmodem)

scanModem will scan you winmodem and tell you what driver to use.

The quick and dirty:

If you have an ac97codec modem from any company (intel, smartlink, conexant, whatever,..)  the sl-modem packages are what you need.

If you have a pctel modem, you only have drivers for 2.4 kernels.  No 2.6 yet.

If you have an Intel modem you can get drivers from them or probaly use the alsa driver.

If you have a smartlink mode, you use the sl-modem packages.

If you have a Conexant modem, you will have to pay for linux drivers.



To compile drivers, install build-essential and linux-headers-2.6-(whatever your kernel is say 386)

Read the documentation provided with the drivers.



"Drivers are OK, but Wvdial returns an error: "NO DIALTONE"

Use pppconfig

sudo pppconfig
add all the information.
Go into the advanced setting and add you user to the dip group.
save and exit.
logout and back in to adjust the new group permissions.
to dial type
pon

to hang up 
poff

Add the modem-lights applet to your ppanel (right-click and add applet)

Adjust the properties so that the lockfile is correct.
pon and poff are already set.


Good luck!

---

### Post by haddock on 2005-07-25
You need the Smartlink Winmodem driver.

[http://www.smlink.com/content.aspx?id=53](http://http://www.smlink.com/content.aspx?id=53) 

slmodem-2.9.10.tar.gz

You'll need to compile it and configure it manually.

This is what I did to get mine working:

lspci lists modem as:
Modem: Intel Corp. 82801CA/CAM AC'97 Modem Controller (rev 01) (prog-if 00 [Generic])
Subsystem: Toshiba America Info Systems Toshiba Satellite 1110 Z15 internal Modem

I unpacked it and compiled the driver, then followed the directions given in the package to set it up.

The main points are as follows:
1) Build slmodemd
make
make install

2) add slamr module to /etc/modules

vi /etc/modules
add slamr to bottom of list of modules to be loaded

4) copy slmodemd init script as supplied in slmodem-2.9.10.tar.gz for Debian into /etc/init.d

5) modify slmodemd in /etc/modules to use Australia: SLMODEMD_COUNTRY=AUSTRALIA 
(set this to your country so as not to incur fines for using an illegally configured communications device for your country)

6) create links for runlevels to start and stop slmodem on startup and shutdown

I created these links, you may want to create them differently but the principle is the same:
ln -s /etc/init.d/slmodemd /etc/rc0.d/K10slmodemd
ln -s /etc/init.d/slmodemd /etc/rc1.d/S100slmodemd
ln -s /etc/init.d/slmodemd /etc/rc2.d/S100slmodemd
ln -s /etc/init.d/slmodemd /etc/rc3.d/S100slmodemd
ln -s /etc/init.d/slmodemd /etc/rc4.d/S100slmodemd
ln -s /etc/init.d/slmodemd /etc/rc5.d/S100slmodemd
ln -s /etc/init.d/slmodemd /etc/rc6.d/K10slmodemd

7) configure your ppp connection
I use wvdial so simply did:
wvdialconf /etc/wvdial.conf
this found my modem on /dev/ttySL0 and set up my empty configuration file.
As per advice in README supplied in slmodem-2.9.10.tar.gz, I added:
Carrier Check = no 
to the wvdial.conf file as well as my phone number, username and password.

I also added my country code to the modem init command string:
ATZM0L0 +GCI=09 so as to ensure my modem is configured for Australia.

For a list of T.25 Country codes see:
[http://www.katpatuka.org/pub/doc/t.35.html](http://www.katpatuka.org/pub/doc/t.35.html)

After this, I tried wvdial and I connected to the net without problems.

---

### Post by shrik on 2005-07-28
This may be slightly off-topic, but did it bother anybody else that the instructions in the Ubuntu Guide asked you to wget and apt-get the Smartlink driver module and daemon?

I know I can download it through my other O$, or maybe even some other comp, but still, it's the principle here...

Just in case my point was lost, here's an analogy that occurred to me immediately:

"Error! Keyboard not detected! Press any key to continue."

---

### Post by az on 2005-07-28
[QUOTE=shrik]This may be slightly off-topic, but did it bother anybody else that the instructions in the Ubuntu Guide asked you to wget and apt-get the Smartlink driver module and daemon?

I know I can download it through my other O$, or maybe even some other comp, but still, it's the principle here...

Just in case my point was lost, here's an analogy that occurred to me immediately:

"Error! Keyboard not detected! Press any key to continue."[/QUOTE]

I mentioned that to the author, but he never answered.

---

### Post by around on 2005-08-20
Hello everyone, I am having a problem with my modem too. I have a usb modem, slmodem 2.9.10 drivers and 2.6.8.1-3-386 kernel. I installed the drivers, did "modprobe lsusb" , and then "sudo /usr/sbin/slmodemd --country=ITALY /dev/slusb0" and everything is ok to this point. 
 Then I tried to connect wvdail with no success. I tried with the network-admin with no success. I tried with ppp, I set it up with pppconfig and tried pon, the modem turns on  :)  but after 20 seconds turns off  ](*,) . the message plog gives me is:

Aug 20 13:29:37 localhost chat[4721]:  -- got it
Aug 20 13:29:37 localhost chat[4721]: send (ATDT7010187187^M)
Aug 20 13:29:37 localhost chat[4721]: expect (CONNECT)
Aug 20 13:29:37 localhost chat[4721]: ^M
Aug 20 13:29:37 localhost chat[4721]: ATDT7010187187^M^M
Aug 20 13:29:42 localhost chat[4721]: NO DIALTONE
Aug 20 13:29:42 localhost chat[4721]:  -- failed
Aug 20 13:29:42 localhost chat[4721]: Failed (NO DIALTONE)
Aug 20 13:29:42 localhost pppd[4718]: Connect script failed
Aug 20 13:29:43 localhost pppd[4718]: Exit.

I also tried modifiying /etc/chatscripts/provider  with ATX3DT, I read that this way the modem won't wait for the dailtone but the result is the same. It doesn't work.
Can someone help me.

---

### Post by hasannoori on 2007-06-21
Hi All.
I have a SmartLink Modem.
I Get The ModemDriver From[http://linmodems.technion.ac.il/packages/smartlink/]("http://linmodems.technion.ac.il/packages/smartlink/"),
and installed thr driver from source.
but i can,t connect to the net.
 plase help me.:(

---

### Post by hasala on 2008-02-06
(if you use this method you can forget about the rpms no rpm will be needed to be installed for you to get the modem running.)
RATHER THAN EXTERNAL MODEMS internal modems offloads a lot of funtionality to the software driver.it has always been a big problem to configure those internal modems or(WINMODEMS/LINMODEMS) to work with linux because of manufacturers not supporting linux (and also the driver being pretty much more complex than ) But due to a great person Linux maintainer Sasha Khapyorsky writing the neccassary drivers needed to work the winmodem , now using a internal modem in linux has become as easy as ABC.


Linux maintainer: Sasha Khapyorsky. Get his updated software from:
[http://linmodems.technion.il/packages/smartlink/](http://linmodems.technion.il/packages/smartlink/)


what to do.

1. download a software called scanmodem from the foresaid site.

2. Browse [http://linmodems.technion.ac.il](http://linmodems.technion.ac.il) and  download scanModem.gz .
 Within a Linux partition open up a console and type in the following commands
    gunzip scanModem.gz
 To make it executable:
    chmod +x scanModem
 Run diagnositics with:
    ./scanModem 
3.scanmodem will check your hardware and software and then write its diagnostics to a subdir called modem.

4.open the ModemData.txt file.and go to   -----------end Softmodem section----------- part .

5.it will give the softwares you need to download and install.

6.if u have not installed the source at the installation of the distro. please install it.(source of the kernel) from the installation cd/dvd.

7.then install the downloaded software.

8.go to scanmodem/modem and open the diagnostic file chipsetname.txt eg:Smartlink.txt/conexant.txt .

9.In the start of the doc it gives the commands you have to run at the console to load the drivers that u downloaded and installed.

10.make sure that the smpppd, pppd services are installed and running.else install both and remember to enable them.

11.dial up using kinternet(i prefer it) or kppp. put to stupid mode option..now configure kinternet and the modem properly.to do that 
 goto yast->network devices ->modem.
           1.choose your modem device and press edit.
              enter modem device as /dev/ttySL0 and enter the details of the isp. if you are not sure call customer support for internet of your isp (internet provider) and get the required details such as number to dial and prefix.username
and password.

           2.remember to definitely check the box for stupid mode.

now every thing is set up

enjoy the internet with a great browser like firefox/opera.!!!!!!!
(with this you do not need any rpm for you to download,what you compile is enough)
if u have any comments or questions please mail to:dharmawardena_06@elect.mrt.ac.lk

						or [email]hasaladharmawardena@yahoo.com[/email]
or //(hasalaid@gmail.com).

hasala dharmawardena
faculty of engineering
department of electrical engineering([www.elect.mrt.ac.lk](www.elect.mrt.ac.lk))
University Of Moratuwa
SRILANKA

regards from srilanka , hasala.         ([www.hasala.bravehost.com](www.hasala.bravehost.com))

---

