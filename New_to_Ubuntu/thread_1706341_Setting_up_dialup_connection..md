---
title: "Setting up dialup connection."
date: 2011-03-13
forum: New to Ubuntu
---

### Post by Olivares on 2011-03-13
I have recently installed Ubuntu on my computer which already has Windows XP. The next step for me is to activate a dialup internet connection for Ubuntu. I have tried to follow instructions in such places as [www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu](www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu) and [https://help.ubuntu.com/community/DialUpModemHowto/SetUpDialler](https://help.ubuntu.com/community/DialUpModemHowto/SetUpDialler). As far as I can tell I have successfully completed the Network configuration part (see screenshots in attachment 'Network Settings'). Instructions are then to 'use the Gnome Modem Monitor panel' to start the connection. This is apparently part of the Gnome-PPP package. When I went to install I got the message "couldn't find package gnome-ppp" - even though the package is evidently there in the directory /usr/share/app-install/desktop/. I have also tried launching wvdial.config but I am getting the message "sorry no modem was detected." 

What am I doing wrong?

---

### Post by lkraemer on 2011-03-15
OK, I think you need to take a step back, and tell us what kind of Modem
you are trying to use.  If it is a WinModem, you are going to need to 
contact Marvin and the folks at [www.linmodems.org](www.linmodems.org) to run the script
and determine what Drivers may possibly be used.  Their site ONLY accepts
Emails in "PLAIN TEXT".

You're best bet is to use an External Hardware Modem, and be up & running 
in 15 minutes or less, assuming you use Windows to Download the wvdial &
Dependencies for your Version of Ubuntu.

But, you will need to use Windows or another system (Ethernet Connection)
because you don't have wvdial installed yet.

You need to download wvdial and the following dependencies for 10.04,
or whatever version you have installed......

wvdial & dependencies:
```

libuniconf4.6
libwvstreams4.6-extras
libwvstreams4.6-base

```
Located at:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Select 10.04 -> Communications Programs -> wvdial 1.60.3
Download these with XP or Ubuntu, then copy the *.deb files to USB Flash Drive,& then to Ubuntu
subdirectory /var/cache/apt/archives & then install using Synaptic Package Manager.....ie.

```

sudo cp ~/Downloads/mydebs/*.deb /var/cache/apt/archives

```
OR you can go to SYSTEM -> ADMINISTRATION -> SOFTWARE SOURCES
and check the box for installable from CDROM/DVD.........then
insert your LiveCD and install from the CDR.

Power up the modem, and connect it to your serial port.
In a Terminal window do:

```

sudo wvdialconf /etc/wvdial.conf

```
You should get a configuration file something similar to this at
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

Once wvdial is working download Gnome-PPP and set it up.

lk

---

### Post by Olivares on 2011-03-21
Thanks Ikraemer

I followed your instructions up to the point of copying wvdial files to /var/cache/apt/archives. But when I open Synaptic Package Manager these files don't show up. What would they be labelled as in the package browser panel on the left? I have also tried Ubuntu Software Center but they are not findable there either. Can you advise what I do now?

---

### Post by lkraemer on 2011-03-21
Well, the easiest thing to do is to boot from your Hard Drive.
Then insert the LiveCD in the CDRW Drive.  Then go to
SYSTEM -> ADMINISTRATION -> SOFTWARE SOURCES
and check the box for installable from CDROM/DVD.........then
install wvdial from the CDR.  That will get you going.

You should have only copied the *.deb files to the /var/cache/apt/archives
I've forgotten where the libs go....and I'm on 8.04 now.

You should be able to Open a Terminal Window and type:
```

sudo apt-get install /path/to/lib/libuniconf4.6
sudo apt-get install /path/to/lib/libwvstreams4.6-extras
sudo apt-get install /path/to/lib/libwvstreams4.6-base
exit

```

Then run Synaptic Package Manager, RELOAD, and SEARCH for wvdial, Select it, then apply.


lk

---

### Post by Olivares on 2011-03-22
OK I do not have a feature called ‘Software Sources’ under System > Administration. Under ‘Places’ I did identify the file wvdial_1.60.4_i386.deb in CDROM/DVD directory /media/”Ubuntu 10.10 i386"/main/w/wvdial/. I opened the terminal and tried the following:

cd /media/”Ubuntu 10.10 i386"/main/w/wvdial/
sudo dpkg -i wvdial_1.60.4_i386.deb  

This installation failed as it said packages libunicof4.6, libwvstreams4.6_base and libwvstreams4.6_extras were not installed. These packages are in directory /var/cache/apt/archives/.

I tried moving wvdial_1.60.4_i386.deb to /var/cache/apt/archives/ but I get ‘permission denied.’ Ubuntu let me copy wvdial_1.60.4_i386.deb to the desktop ... I then tried moving the above three lib files to the desktop but again I get ‘permission denied.’
:o

---

### Post by lkraemer on 2011-03-22
OK, Open a Terminal Window and Copy & Paste these commands making sure
you include the period as the last character:
```

cd ~
cd Desktop
sudo mv /var/cache/apt/archives/libuniconf4.6 .
sudo mv /var/cache/apt/archives/libwvstreams4.6-extras .
sudo mv /var/cache/apt/archives/libwvstreams4.6-base .
sudo apt-get install libuniconf4.6
sudo apt-get install libwvstreams4.6-extras
sudo apt-get install libwvstreams4.6-base
cd /
cd /media/&#8221;Ubuntu 10.10 i386"/main/w/wvdial/
sudo dpkg -i wvdial_1.60.4_i386.deb 
exit

```
If what you have posted is correct this should get wvdial installed.

Then Connect and download Gnome-PPP and set it up.

lk

---

### Post by Olivares on 2011-03-23
Yes great ... the sudo mv command worked fine, it shifted the three files to the desktop.

The next line did not work:
sudo apt-get libuniconf4.6_4.6.1-1ubuntu1_i386.deb

I got the following message:
Reading package lists ... Done
Building dependency tree
Reading state information ... Done
E: Unable to locate package libuniconf4.6_4.6.1-1ubuntu1_i386.deb
E: Couldn't find any package by regex 'libuniconf4.6_4.6.1-1ubuntu1_i386.deb'

I note these three *.deb files have a padlock symbol attached to them. Is this significant?

---

### Post by lkraemer on 2011-03-23
Maybe it would help if you re-read the previous Posting SLOWLY!
```

cd ~
cd Desktop
sudo mv /var/cache/apt/archives/libuniconf4.6 .
sudo mv /var/cache/apt/archives/libwvstreams4.6-extras .
sudo mv /var/cache/apt/archives/libwvstreams4.6-base .
sudo apt-get install libuniconf4.6
sudo apt-get install libwvstreams4.6-extras
sudo apt-get install libwvstreams4.6-base
cd /
cd /media/”Ubuntu 10.10 i386"/main/w/wvdial/
sudo dpkg -i wvdial_1.60.4_i386.deb 
exit

```

Compare the first instruction to the second:
sudo apt-get install libuniconf4.6
TO
sudo apt-get libuniconf4.6_4.6.1-1ubuntu1_i386.deb

You might find the answer.  That is why I posted "Copy & Paste these commands".

lk

---

### Post by Olivares on 2011-03-23
Sorry I thought you were omitting the full file name just as a way of being concise. I attempted to pick up from where we left off, i.e. the three 'lib' files are on the desktop and I entered the line:
sudo apt-get install libuniconf4.6

I get this message:
"Package libuniconf4.6 is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source.

E: Package 'libuniconf4.6' has no installation candidate"

---

### Post by lkraemer on 2011-03-23
Try this, assuming the libs are still on your Desktop...Copy & Paste:
```

cd ~
cd Desktop
sudo apt-get install libuniconf4.6
sudo apt-get install libwvstreams4.6-extras
sudo apt-get install libwvstreams4.6-base
cd /
cd /media/&#8221;Ubuntu 10.10 i386"/main/w/wvdial/
sudo dpkg -i wvdial_1.60.4_i386.deb 
exit

```

If this doesn't work them I'm at the end of my rope.....

lk

---

### Post by Olivares on 2011-03-23
Phew ... I pasted in your code, it seemed to process the code without error, and the Terminal window then closed itself!

Looking in Synaptic Package Manager, wvdial now shows up - as uninstalled. When I click on 'mark for installation' I get the following message:

"Could not mark all packages for installation or upgrade.

"The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.

"wvdial:

"Package wvdial has no available version, but exists in the database. 
"This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list."

Hope you are not too exasperated.

---

### Post by lkraemer on 2011-03-23
If all the commands completed from the Terminal Window, wvdial should be
installed, no matter what Synaptic is telling you.

Try typing this in a Terminal Window:
```

sudo wvdialconf /etc/wvdial.conf

```
to see if wvdial will execute and configure.

lk

---

### Post by Olivares on 2011-03-23
Well what I get now is:

sudo: wvdialconf: command not found

Ol.

---

### Post by lkraemer on 2011-03-24
Try SYSTEM -> ADMINISTRATION -> SYNAPTICS PACKAGE MANAGER
then click on
EDIT -> FIX BROKEN PACKAGES
then click on 
RELOAD on the Main Synaptic Menu.  Now maybe wvdial can be installed
via Synaptics.

Does it install?

lk

---

### Post by Olivares on 2011-03-24
No, I'm sorry, I did click on 'fix broken packages' then on 'reload.' I then get the message 'downloading package information' ... followed by 'an error occurred' followed by 30-odd items like this:
"W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/maverick/Release](http://nz.archive.ubuntu.com/ubuntu/dists/maverick/Release). Could not resolve 'nz.archive.ubuntu.com.' 
It's trying to connect to the internet, but connection to the internet is what I haven't achieved yet!

Ol.

---

