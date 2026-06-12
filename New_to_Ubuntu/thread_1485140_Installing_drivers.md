---
title: "Installing drivers"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by Stoker580 on 2010-05-16
I need some advice about how to install a driver.

I've discovered a link in another thread (dealing with the installation of a X060S modem) to this driver :-

[http://www.ziddu.com/downloadlink/8287872/x060-karmic-driver.tar.gz](http://www.ziddu.com/downloadlink/8287872/x060-karmic-driver.tar.gz)

I've downloaded it but not sure what to do next.

Can anyone point me in the direction of an idiot's guide to installing drivers?

---

### Post by v1ad on 2010-05-16
what you do with that is open console.
if its on your desktop type cd Desktop      or whatever folder u put it in.

then type tar -xvzf drivernamehere

then type cd folderThatWasCreated

then type
sudo ./configure
sudo make
sudo make install

---

### Post by Stoker580 on 2010-05-16
Many thanks for the quick response. I'll let you know how I get on.

---

### Post by Stoker580 on 2010-05-16
Hi v1ad
Here's what happened:-
david@david-laptop:~/Downloads$ tar -xvzf x060-karmic-driver.tar.gz
x060-karmic-driver/
x060-karmic-driver/wvdialkarmic/
x060-karmic-driver/etc/
x060-karmic-driver/usr/
x060-karmic-driver/sbin/
x060-karmic-driver/etc/udev/
x060-karmic-driver/usr/share/
x060-karmic-driver/etc/udev/rules.d/
x060-karmic-driver/usr/share/man/
x060-karmic-driver/usr/share/doc/
x060-karmic-driver/usr/share/man/man1/
x060-karmic-driver/usr/share/doc/usb-modeswitch/
x060-karmic-driver/readme
x060-karmic-driver/wvdialkarmic/wvdial_1.60.1+nmu2ubuntu1_i386.deb
x060-karmic-driver/wvdialkarmic/libwvstreams4.6-extras_4.6-2_i386.deb
x060-karmic-driver/wvdialkarmic/libwvstreams4.6-base_4.6-2_i386.deb
x060-karmic-driver/wvdialkarmic/libuniconf4.6_4.6-2_i386.deb
x060-karmic-driver/wvdialkarmic/usb-modeswitch_1.0.5-1_i386.deb
x060-karmic-driver/wvdialkarmic/modemmanager_0.2ubuntu2~javi1_i386.deb
x060-karmic-driver/etc/usb_modeswitch.conf
x060-karmic-driver/etc/wvdial.conf
x060-karmic-driver/etc/mod.sh
x060-karmic-driver/sbin/usb_modeswitch
x060-karmic-driver/etc/udev/rules.d/99-alcatel.rules
x060-karmic-driver/etc/udev/rules.d/usb_modeswitch.rules
x060-karmic-driver/etc/udev/rules.d/45-alcatel.rules
x060-karmic-driver/etc/udev/rules.d/10-alcatel.rules
x060-karmic-driver/usr/share/man/man1/usb_modeswitch.1.gz
x060-karmic-driver/usr/share/doc/usb-modeswitch/NEWS.Debian.gz
x060-karmic-driver/usr/share/doc/usb-modeswitch/readme.gz
x060-karmic-driver/usr/share/doc/usb-modeswitch/changelog.Debian.gz
david@david-laptop:~/Downloads$ ls
debianx060s.html  x060-karmic-driver  x060-karmic-driver.tar.gz
david@david-laptop:~/Downloads$ cd x060-karmic-driver
david@david-laptop:~/Downloads/x060-karmic-driver$ sudo ./configure
[sudo] password for david: 
sudo: ./configure: command not found

Any ideas what might be wrong?

---

### Post by HotShotDJ on 2010-05-16
Although V1ad was clearly trying to be helpful, he made the assumption that the file you downloaded was source-code (often the case with tarballs).  It is not.

Open the directory that you extracted the files too, and read the file that has been quite conveniently named "readme."  It contains step by step instructions.

---

### Post by Stoker580 on 2010-05-16
Thanks for your reply Hot ShotDJ

Here's the first step of the instructions:-

1. Install to ubuntu karmic architecture i386.

su -i
cd x060-karmic-driver
cp -R etc/udev/rules.d/*.rules /etc/udev/rules.d
cp -R etc/*.conf /etc
cp -R etc/*.conf /etc
cp -R sbin/*.sh /sbin
cp -R sbin/* /bin
cp -R sbin/* /usr/bin
mkdir -p /usr/share/doc/usb-modeswitch
cp -R usr/share/doc/usb-modeswitch/*.gz /usr/share/doc/usb-modeswitch
cp -R usr/share/man/man1/*gz /usr/share/man/man1
sh /etc/mod.sh

However when I try to execute the first line this is what I got:-

david@david-laptop:~/Downloads/x060-karmic-driver$ su -i
su: invalid option -- 'i'
Usage: su [options] [LOGIN]

Options:
  -c, --command COMMAND         pass COMMAND to the invoked shell
  -h, --help                    display this help message and exit
  -, -l, --login                make the shell a login shell
  -m, -p,
  --preserve-environment        do not reset environment variables, and
                                keep the same shell
  -s, --shell SHELL             use SHELL instead of the default in passwd

any help would be much appreciated.

---

### Post by HotShotDJ on 2010-05-16
> **Stoker580 said:**
> david@david-laptop:~/Downloads/x060-karmic-driver$ su -i
su: invalid option -- 'i'Oh, right.  I forgot about that.  Use ```
sudo su -
```instead of su -i.  Just don't forget to type in "exit" when you're done.  Alternatively, you can simply add "sudo" in front of each line.

---

### Post by Stoker580 on 2010-05-16
I've done all that using sudo in front of all the commands.

When I run wvdial I get the following

--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ+CPIN=1234
ATZ+CPIN=1234
ERROR
--> Bad init string.

---

### Post by HotShotDJ on 2010-05-16
I'm not sure how to make the thing work.. just how to find and follow the "readme."  But I suspect you are close to having it working.  Check out this thread that I found: [http://ubuntuforums.org/showthread.php?t=1199646](http://ubuntuforums.org/showthread.php?t=1199646)

I'm not sure how helpful it will be, but it seems like there has been success in getting this particular modem to work.  Best of luck to you!

---

### Post by Stoker580 on 2010-05-16
Many Thanks HotShotDJ.

It looks like I have gone full circle on this one as it was from the thread that you mention that I got the tar file that I was trying to install.

I have learnt a lot from this and will post an update if/when I get it working.

---

### Post by cuberts on 2010-05-16
> **Stoker580 said:**
> I need some advice about how to install a driver.

I've discovered a link in another thread (dealing with the installation of a X060S modem) to this driver :-

[http://www.ziddu.com/downloadlink/8287872/x060-karmic-driver.tar.gz](http://www.ziddu.com/downloadlink/8287872/x060-karmic-driver.tar.gz)

I've downloaded it but not sure what to do next.

Can anyone point me in the direction of an idiot's guide to installing drivers?Install drivers?
You can just do that by installing all of the Updates from the Update manager (system>administration>Updatemanager)

---

### Post by Stoker580 on 2010-05-16
Hi Cuberts.

How can I check that this driver is included?

My version (9.10) is completely up to date BTW.

---

### Post by lkraemer on 2010-05-16
Before you run wvdial you really need to set up pppconfig and you also
need to configure wvdial.

**SET UP PAP/CHAP:**

Locate your userlogin, password, Dialup Provider Info, Phone Number,
and what your ISP uses (PAP or CHAP)

Open a Terminal Window and run the following:
```

sudo pppconfig

```
You will need your userlogin, password, ISP provider information, and
pap or chap information for the connection. (You can set up pap and
then chap, if pap doesn't work.) Basically, you just answer the questions
that are presented. You can delete a configuration and start over if
you need to from the menu selections.

For more information try:
```

man pppd
man pppconfig

```
pap-secrets file contains:
```

# OUTBOUND connections

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.

#       *       password
"yourusername" provider "yourpassword"

```
And the file is located at:
```

/etc/ppp/pap-secrets

```
Use pppconfig to create a modified file or edit the file with:
```

sudo nano /etc/ppp/pap-secrets

```


**SETUP WVDIAL:**

Now ppp is setup and the Drivers are loaded, you will need to set up wvdial.

In a Terminal window do:
```

sudo wvdialconf /etc/wvdial.conf

```
You should get a configuration file that is something like this,
but your modem and some of your parameters may be slightly different
depending on what wvdial detects.
Your PhoneNumber, LoginName, and PassWord will be what you use.
The Modem type ....as in Modem = /dev/ttyACM0 should be determined
by wvdial......hopefully.....
```

sudo nano /etc/wvdial.conf (you may need to edit/add/modify a few things...)

```
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
If wvdial gives you an error try:
```

sudo wvdial /etc/wvdial.conf

```
You should hear the modem go OFFHOOK with dialtone, Dial, and connect.
If your config file is correct you should authenticate and then control
will be passed to ppp. You will see several strings of HEX (funny
characters) and then you should stay connected. (you will use CNTL C to
terminate the session when you are done, but for this session you MUST
leave the Terminal window OPEN.....just minimize it) You may have to
uncheck the box marked OFFLINE when you open your browser to make it
online. Surf, then terminate the open session with CNTL C in the open
terminal window where you initiated wvdial.

If your configuration is wrong, it will disconnect in a few seconds
because it won't be able to authenticate properly......

Finally, when wvdial is working you can Download & Install
Gnome-PPP and then configure/set up Gnome-PPP.

When you get everything working, I'd suggest backing up the pap-secrets,
chap-secrets, and wvdial.conf files....just in case.
You can use:
```

cd /
cd /etc/ppp
sudo cp pap-secrets pap-secrets.sav
sudo cp chap-secrets chap-secrets.sav
cd ..
cp wvdial.conf wvdial.sav

```
to save the backup files.

Once wvdial is working Install Gnome-PPP and configure it so you can
Connect from the GUI.

lk

---

### Post by Stoker580 on 2010-05-17
Many thanks for your reply lkreamer.

I've already had a look at pppconfig and wvdial and previous research brought me to the driver that I mentioned in my original post.  I just didn't know how to go about installing it. I think I've gone as far as I can for the moment. The X060S is a mobile internet modem provided by Simyo that I use in Spain and I will have to wait until the next time I'm there to try it out.

---

