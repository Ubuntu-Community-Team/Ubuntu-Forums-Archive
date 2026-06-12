---
title: "VZAccess Manager/Ubuntu"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by XulluX on 2007-06-28
I have just made the switch from the windows platform and i use my blackberry (8703e) as a modem.  The application that allows me to do this VZAccess Manager. 

I see that there are only rpm and dep builds is there way his there any why to use these build to build a package for ubuntu 

If not is there any way to use my blackberry as a modem.

i am using 7.04 the 32bit version

---

### Post by bynyry on 2007-06-29
You are able to install both rpm and deb files.
You can install an rpm file by using the 'rpm' command in the terminal. (ex: rpm -ivf myInstallFile.rpm)

---

### Post by jcankrom on 2007-06-29
Where did you get an RPM of VZ Access manager? I didnt' think they made a linux version.
i spent so long editing ppp config files to get my phone to dial without vzaccess

---

### Post by t4thfavor on 2007-06-29
much easier way...

In the terminal type 

sudo wvdialconfig

it will test for a modem, if there are no modems in your box besides your blackberry it should tell you that it found a modem and is using it.

if there are multiple modems you can edit the /etc/wvdial.conf to point to the correct modem(which was identified in the wvdialconf step). I believe it should be /dev/ttyACM0 (that is what my razr shows up as)
Then use whatever dial program you want like gnome-ppp or kppp or whatever. in the settings page you should have a place to put the modem device.

I may be a bit confusing to you, if you have any questions I will be here later.

---

### Post by XulluX on 2007-07-05
i found an article on the web addressing the VZAccess manager in linux packages.
I think the URL for that PDF is: wagoneers.com/CS/LINUX/v620-SUSE/VZAccessManagerLinuxInstallationGuide.pdf
I could find the actual rpm though

I don't have the command for 
sudo wvdialconfig
so where do i go form there, i get the error that it is a bad command 

And i also want to know if i do it this way will it dial out like a phone call and use my minutes or will it be treated as if i were using VZAccess and use my data plan?

---

### Post by hwertz on 2007-07-05
Does anyone have information on this?  I'm highly interested.  I saw 1 mention of VZAM for Linux 1.2, supporting the PC5740.  It's sucks nuts to have to swap in a spare 6GB with Win2K on it, just to update my PRL.  (EVERYONE I know either has Linux on a notebook, or Windows but it's expresscard, so I can't slot my PC5740 into it.)

---

### Post by t4thfavor on 2007-07-06
as far as i know wvdial and wvdialconf come with ubuntu. it will dial out and use your data plan as far as I know (it uses my minutes because I have no data plan) It is called teathering

The creds for wvdial are as follows 

user YourTenDigitPhone#@vzw3g.com
pass vzw

---

### Post by machineelf368 on 2007-07-06
After some trial and error I got everything working for my Verizon USB720 modem. I followed the directions at [http://www.linux.com/articles/52729](http://www.linux.com/articles/52729) to connect using pppd. The thing that got me was when the author gives the device name as ttyACM0, but that was just for his system not mine (or presumably anyone else's). Follow his directions to the t, but after modprobe go to /dev and look at the most recently created files, the proper device name is one of those. For me ttyUSB0 worked. 

Also, I found the rpm for VZAccess Manager 1.1 at [http://wagoneers.com/CS/LINUX/v620-SUSE/](http://wagoneers.com/CS/LINUX/v620-SUSE/) along with several documents and another rpm. They seem to have been useless to me, but I did install both before trying the above pppd method. 

machineelf

---

### Post by XulluX on 2007-08-05
i had ran across this site when looking for a solution to my problem, and i have taken it a step further by converting the rpm with alien 'sudo alien (file name)' this seems to worked up until the i connected my blackberry.  Still getting the charging error but at  least this seems to be a step forward because i know the program is somewhat available under Ubuntu.   

I have tried both my 8703 and my 8830 and both get the charging error and both are unseen by the vzaccess manager.

I also have tried the barry and it has not work for me to this point either.

---

### Post by JohnnyVW on 2007-08-21
I am also very interested in this!  I just picked up an 8830 this weekend and love it!  I have the broadband plan with Verizon and would LOVE to use the Ubuntu Laptop with the 8830 while traveling or just 'out there.'

---

### Post by wilberfan on 2007-09-26
Wanted to say thanks to t4thfavor for his post regarding wvdialconf.    (Post #4, above)

I was a little slowed down by the fact that there was a typo in his post:   he wrote "sudo wvdialconfig"  when it should have been "sudo **wvdialconf**".   

The latter worked like a charm!   It detected the USB720 modem, and wrote a .conf file that I didn't even have to edit!   I just rebooted--and voila!!

:guitar:

---

### Post by coyotech on 2008-02-01
it's sudo wvdialconf. don't forget the sudo.

---

### Post by coyotech on 2008-02-01
Yes, I also thank the sender of the wvdialconf information! How sweet to find it's actually easy :-)

---

### Post by sunbird on 2008-07-19
Every time I run wvdialconf, I get this:

```

$ sudo wvdialconf /etc/wvdial.conf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: USB1 


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

```

*And* it crashes my Palm. Anyone had any luck getting it running with any Palm devices? What am I missing here?

---

