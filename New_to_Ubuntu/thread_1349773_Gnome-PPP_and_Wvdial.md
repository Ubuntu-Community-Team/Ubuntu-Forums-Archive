---
title: "Gnome-PPP and Wvdial"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by dwaynedauzat on 2009-12-08
I have successfully installed a Lucent/Agere modem in Ubuntu 9.1 and was able to dialup and connect to the internet using Martian_Modem, Wvdial, and Gnome-PPP.  My problem is that it only works by using the sudo command and password to launch Wvdial and Gnome-PPP.  If I try to launch these as just a normal user they fail to detect the modem.  Does anyone know how to get Wvdial and Gnome-PPP to detect my modem without having to use sudo and the password?

---

### Post by t0p on 2009-12-08
I also have this problem, as explained toward the end of [this thread]("http://ubuntuforums.org/showthread.php?t=1296460").  If you follow the advice I got at the end of the thread, you can make a launcher to run 'gksudo gnome-ppp', and edit the sudoers file so you won't have to type in your password when you launch the command.  That's the best solution I could find.

---

### Post by llamabr on 2009-12-08
Right.  This is not a bug, it's a feature.  PPP is a system level process, and so regular users shouldn't necessarily have access to it.  In ubuntu, this philosophy is often ignored, but I guess ppp has gone un-noticed.  

You could change the permissions of the relevant devices, but that may have unwanted consequenses.  You could always have sudo control the device, which is preferable, but annoying.  And you could set sudo not to ask for your password, which can sometimes be dangerous, but will sidestep the annoying.

---

### Post by dwaynedauzat on 2009-12-08
When I get a chance, I will try t0p's solution.

> **llamabr said:**
> Right.  This is not a bug, it's a feature.  PPP is a system level process, and so regular users shouldn't necessarily have access to it.  In ubuntu, this philosophy is often ignored, but I guess ppp has gone un-noticed.

:confused:

Linux/Ubuntu is absolutely new to me.  If regular users shouldn't necessarily have access to PPP, how then are they supposed to dialup to the internet?  I don't understand this philosophy in Ubuntu.

Thanks

---

### Post by _duncan_ on 2009-12-09
The simplest solution is to add the user ID to the 'dip' group by entering the following command in a terminal:```
sudo adduser [COLOR="Blue"]userID[/COLOR] dip
```

replace [COLOR="Blue"]userID[/COLOR] with the actual user ID you want to grant access to dial-up.

logout and login again for the changes to take effect.

now try running gnome-ppp without sudo. In fact, if gnome-ppp is installed properly and you executed the above command correctly, you can launch gnome-ppp via Applications > Internet > GNOME-PPP.

---

### Post by Cubby on 2010-09-03
Frustrating.  I can use KPPP as user, no problem, only needing to make sure to add user properties
"connect to internet using modem" 
and editing file as sudo:
/etc/ppp/peers/kppp-options
and removing the pound sign from:
#noauthor
the modem is detected, and I can dial out.  

But, whenever I use wvdial or gnome-ppp I have to run either as sudo, which isn't a good thing in my book.  If only I could figure out which files kppp uses and handles as user, that wvdial and wvdial's GUI front end Gnome-PPP uses that has the difference in permissions.  I've also been looking at an older version of Linux Mint 6 that is based on Ubuntu.  You run wvdialconf as sudo the first time, but after that, you only need to enter in terminal 'wvdail' to connect, not 'sudo wvdial - enter password'.  So, have been waisting time trying to find the differences in what I believe are the key files, including /usr/sbin/pppd, but still haven't found anything that works.

I have heard modem-manager can be a problem, but it isn't installed on my OS.  I'm also already a part of the correct groups:
~$ id
uid=1000(me) gid=1001(me) groups=20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),105(netdev),110(scanner),112(powerdev),1001(me)

I've seen so many ways to get around this, by changing file permissions with the ever-too easy "chmod-777".  No thanks.  

Looks like the next step is try the sudoers suggestions.  Sheesh. "Raise your hands as I'd like to know how many of you are using dial up?"  Intersting.  "Hmmm, okay, for those of you that have switched back to dial up due to the current economy and job outlook, raise your hands?"  Very interesting.
Cubby

---

### Post by lkraemer on 2010-09-03
To enable dialout without Root permission do:
```

sudo chmod a+x /usr/sbin/pppd

```
Configure wvdial with:
```

sudo wvdialconf

```
the config file will be at /etc/wvdial.conf
to configure your ISP's telephone number, login & password etc.
```

SAMPLE wvdial.conf file
[Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = yes
Modem Type = Analog Modem
Baud = 115200
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = 1234321
Password = yourpassword
Username = yourlogin@ISP.net

```

You can later edit your personal information with:
```

sudo gedit /etc/wvdial.conf

```
Open a Terminal window (you will leave it open the total time
you will be connected via dialup)

dial out with:
```

wvdial

```
SURF!!!
You can go back to the open terminal window and do a CNTRL C
to terminate the connection/session, then close the terminal window.


When that is all working set up Gnome-PPP.

lk

---

### Post by jim777 on 2010-09-05
Our forum members are lucky that experts such as lkraemer give their time and knowledge to sort out our problems.

But why is dial-up set-up such a mission in Linux and Ubuntu in particular?
I've gone back to using dial-up to save some $$, and set-up under Win XP using a Dynalink external hardware modem is just so incredibly easy.
It's things like this that cause PC magazines to hammer Linux for poor user experience...    Frankly, I can't be bothered to hassle with all this
stuff just to get a modem working.

---

### Post by jim777 on 2010-09-05
Sorry, my post appeared twice for some reason.

---

### Post by Cubby on 2010-09-05
Thank you, lkraemer!  Yes, I appreciate the time to help me, too, as I've read so many ways to use wvdial as user, and wanted the least change to my Gnome system.  I balked from the suggestion to edit the /etc/sudoers file.  

I've understood to first set up wvdial, to run in terminal, 'wvdialconf' as sudo, then to edit the created wvdial.conf file as gksu gedit /etc/wvdial.conf.  So, that is easy.  I was just baffled by the change in the past year or two for the need to then run wvdial as 'sudo'.  I'm also surprised that kppp on a KDE desktop will run as user without altering the permissions for /usr/sbin/pppd.  There must be something that kppp does differently, permission-wise, obviusly.  

@jim777, yes, it can be a pain, but once you learn how to do it, you'll never forget, unless something changes upstream in configurations again, or our ISP's do some changes, again, such as my ISP changed to require CHAP authentication in the past year, when previously they just needed PAP.  
We use dial up, for one, it's the only thing available here besides Hughes satalitte service, which I've heard is not all that great, and too expensive, plus, my engineer husband has been unemployed for over a year, so we save money this way,
Thanks again,
Cubby

---

### Post by Cubby on 2010-09-11
I finally got around to doing the file permission change, and it appears it was already set up as such.  When I do a ls -l /usr/sbin/pppd it shows:
-r-xr-xr-x 1 root dip 293812 2010-05-31 13:50 /usr/sbin/pppd
I still couldn't surf without doing sudo wvdial.

I finally got it working by installing pppconfig and now use "pon/poff provider" to dial out.

---

### Post by lkraemer on 2010-09-11
I guess I should have double checked my file.  Mine is set as follows:
-rwsr-xr--  1 root    dip      273312 2010-03-06 21:59 pppd


lk

---

### Post by niharthekadi on 2010-09-12
wvdial & gnome-ppp are good s/w for dial-up connection in ubuntu
but now ubuntu's n/w manager applet detects many devices.

but still i,m not able to connect to internet using my cell-phone.

the problem is my n/w provider does not give any username or password !
we just have to use APN to connect.

but wvdial or gnome-ppp does not accept blank password
i don't know what to write in the username & password fields.

n/w manager & also the gnome-ppp detects my device but no one connects.
device is : lg gd 510 (cokkie pep)

---

