---
title: "dialup"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by Eric-A on 2010-06-11
hi all, I know this is a strange request, but I need to get dialup working on my ubuntu machine to get online, can anyone help? I've tried the pppconfig and no luck.

---

### Post by Autodave on 2010-06-11
> **Eric-A said:**
> hi all, I know this is a strange request, but I need to get dialup working on my ubuntu machine to get online, can anyone help? I've tried the pppconfig and no luck.

Since no one else has tried, let me see what I can offer.  First, is your modem internal or external.  If it is internal, is it what is considered a WINmodem?  If it is, that is probably your biggest obstacle to overcome.  WINmodems are designed for Windows and rarely work with Linux.

---

### Post by Eric-A on 2010-06-11
it is a USRobotics external USB modem... I can't seem to get it do dial out using pppconfig's pon provider... I use peoplepc dialup...

---

### Post by lkraemer on 2010-06-11
Start with:
[http://ubuntuforums.org/showthread.php?t=1472005](http://ubuntuforums.org/showthread.php?t=1472005)
Posting #6, then follow the link to more info.

[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)

You should install and configure wvdial so you know the
modem is identified and configured correctly.  Then edit
the wvdial.conf file to add the phone number, loginname, password
and specific information.  You will also need to setup pppconfig
and specify PAP or CHAP in that configuration.

Once you get going through the process, post back with questions.

You should be up and running in ~30 minutes.

You will need to download wvdial and the dependencies. 10.04 requires:

wvdial & dependencies:
libuniconf4.6
libwvstreams4.6-extras
libwvstreams4.6-base

Located at:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Select 10.04 -> Communications Programs -> wvdial 1.60.3
Download, copy to Ubuntu and install.

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
will be passed to ppp. [B]You will see several strings of HEX (funny
characters) and then you should stay connected. (you will use CNTL C to
terminate the session when you are done, but for this session you MUST
leave the Terminal window OPEN.....just minimize it) You may have to uncheck
the box marked OFFLINE when you open your browser to make it online.[/B]
Surf, then terminate the open session with CNTL C in the open terminal window
where you initiated wvdial.

If your configuration is wrong, it will disconnect in a few seconds because
it won't be able to authenticate properly......

PeoplePC is likely to be a problem with Linux (Ubuntu).
Search this forum for information on Linux Dialup ISP's, and see
if anyone has PeoplePC working with Linux.  (I use Copper.net)

lk

---

### Post by Eric-A on 2010-06-11
all those files say "not satisfiable" during install,,,,,,,,,, I'm ubuntu 9.10

---

### Post by ubunterooster on 2010-06-11
For 9.10

[wvdial]("http://packages.ubuntu.com/karmic/comm/wvdial")  (1.60.1+nmu2ubuntu1) PPP dialer with built-in intelligence

---

### Post by lkraemer on 2010-06-11
Did you copy the dependencies (folders) to:
/use/share/doc

When you download the deb for wvdial:
wvdial_1.60.1+nmu2ubuntu1_i386.deb
copy it to /var/cache/apt/archives

then try installing with Synaptics Package Manager.

lk

---

### Post by Eric-A on 2010-06-11
same error "not satisfiable"

---

### Post by ubunterooster on 2010-06-11
> **lkraemer said:**
> Did you copy the dependencies (folders) to:
/use/share/doc

When you download the deb for wvdial:
wvdial_1.60.1+nmu2ubuntu1_i386.deb
copy it to /var/cache/apt/archives

then try installing with Synaptics Package Manager.

lk
He was trying the 10.04 version when he needed the 9.10: > **ubunterooster said:**
> For 9.10

[wvdial]("http://packages.ubuntu.com/karmic/comm/wvdial")   (1.60.1+nmu2ubuntu1) PPP dialer with built-in intelligence

---

### Post by ubunterooster on 2010-06-11
> **Eric-A said:**
> same error "not satisfiable"
do you have all of these pakages > 
     **Other Packages Related to wvdial**
 

[LIST]
[*]            dep:     [debconf]("http://packages.ubuntu.com/karmic/debconf")      (>= 0.5.00)         Debian configuration management  system         or      [cdebconf]("http://packages.ubuntu.com/karmic/cdebconf")              Debian Configuration Management  System (C-implementation)
[*]            dep:     [libc6]("http://packages.ubuntu.com/karmic/libc6")      (>= 2.4)         GNU C Library: Shared libraries      
also  a virtual package provided by                 [libc6-udeb]("http://packages.ubuntu.com/karmic/libc6-udeb")
[*]            dep:     [libuniconf4.6]("http://packages.ubuntu.com/karmic/libuniconf4.6")              C++ network libraries for rapid  application development
[*]            dep:     [libwvstreams4.6-base]("http://packages.ubuntu.com/karmic/libwvstreams4.6-base")              C++ network libraries for rapid  application development
[*]            dep:     [libwvstreams4.6-extras]("http://packages.ubuntu.com/karmic/libwvstreams4.6-extras")              C++ network libraries for rapid  application development
[*]            dep:     [ppp]("http://packages.ubuntu.com/karmic/ppp")      (>= 2.3.0)         Point-to-Point Protocol (PPP) -  daemon
[/LIST]
        
                **Download wvdial**

               Download for all available architectures     Architecture          Package Size     Installed Size     Files         [amd64]("http://packages.ubuntu.com/karmic/amd64/wvdial/download")   185.8 kB512 kB     [[list  of files]("http://packages.ubuntu.com/karmic/amd64/wvdial/filelist")]               [i386]("http://packages.ubuntu.com/karmic/i386/wvdial/download")   184.0 kB496 kB     [[list  of files]("http://packages.ubuntu.com/karmic/i386/wvdial/filelist")]

---

### Post by lkraemer on 2010-06-11
OK, try this:
Stick in the Ubuntu 9.10 LiveCD.
Go to SYSTEM -> ADMINISTRATION -> SOFTWARE SOURCES
Check the box INSTALLABLE FROM CDROM

Then go to Synaptics and install wvdial.

lk

---

### Post by Eric-A on 2010-06-11
if i did everything correctly then wvdial is installed,,, now how do I deploy it

---

### Post by ubunterooster on 2010-06-11
press cntrl+alt+T and type wvdial (press enter)

---

### Post by lkraemer on 2010-06-11
wvdial must be configured before you can use it.  The best thing for you
to do is go back to Posting #4 and go step by step, starting with pppconfig.
You should be able to work your way through it in about 30 minutes or less.

Make sure you read it slow and do what it says.

When wvdial is working you can download Gnome-PPP and set it up and
connect from the GUI.

lk

---

### Post by Eric-A on 2010-06-11
did that and got cannot open /dev/modem no such file or directory.... okay back to the other wait one..
.
.
.
.
ttyS0 is locked by pid 2725
.
.
did synaptic and modem blinks but phonline is normal dialtone during it.

---

### Post by Eric-A on 2010-06-12
okay, the USRobotics is a wash, I switched to the *zoom* external USB modem which came with a deb file to install. That being installed, I can't dial out still.

---

### Post by Eric-A on 2010-06-12
I found a .deb package for gnome-kppp and now I can dial out. thanks.

---

