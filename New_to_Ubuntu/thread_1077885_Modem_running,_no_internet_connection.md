---
title: "Modem running, no internet connection"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by marcf3998 on 2009-02-22
Being new I am sure I just missed something. I bought a Zoom external modem to replace the internal USR (3Com) I had so I could connect to the internet.

It dials and connects to the ISP (peoplepc) the lights show its still connected, I can here crap on the phone line, but firefox will not connect to the internet. I unchecked the "work offline", I have looked all over the forum and tried several suggested fixes but they all point to the modem not working.

I would really like to ditch M$ and use Ubuntu but I have spent numerous hours and money on this problem of connecting. I have loaded 8.04, 8.10, Fedora. I bought a new modem. 

To top it off PuppyLinux connects with 3 clicks and some simple typing. 

Help. :(

System Specs:
P4 3.0
Biostar P4VMA-M
512 MB
IDE HDD
ATI 9200
Logitech wireless mouse
Zoom v.92 External Modem

---

### Post by llamabr on 2009-02-22
You're no longer an absolute beginner.  Take this to the networking forum.

I used to use a zoom modem.  They'll want to know that you've got the appropriate ppp module installed, and then want the output of ifconfig.

good luck.

---

### Post by marcf3998 on 2009-02-22
I posted this in the network section--As for your thought that I am not a beginner, I am not so sure...

Marc

---

### Post by lkraemer on 2009-02-23
Are you using wvdial to make the connection?  or pon or Gnome-PPP?

Why not try setting up wvdial and use that for your initial connection.
In a Terminal window:  (leaving the window open for the session)
```

sudo wvdialconf /etc/wvdial.conf

```

[http://en.wikipedia.org/wiki/Wvdial](http://en.wikipedia.org/wiki/Wvdial)
[http://support.real-time.com/linux/dialup/wvdial.html](http://support.real-time.com/linux/dialup/wvdial.html)
[http://tldp.org/HOWTO/PPP-HOWTO/x314.html](http://tldp.org/HOWTO/PPP-HOWTO/x314.html)
[http://www.squarebox.co.uk/cgi-squarebox/manServer/wvdial.conf.5](http://www.squarebox.co.uk/cgi-squarebox/manServer/wvdial.conf.5)

[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
osdir.com/ml/ubuntu.doc/2005-04/pdfuHGgEItwtF.pdf

For REF:
[https://wiki.edubuntu.org/DialupModemHowtoOld](https://wiki.edubuntu.org/DialupModemHowtoOld)

the config file will be at /etc/wvdial.conf
to configure your ISP's telephone number, login & password etc.

You can later edit your personal information with:
$ sudo gedit /etc/wvdial.conf


If you haven't set up pppd:
The easiest thing to do is to open a Terminal window.
Type:
```

sudo pppconfig

```

Then go through the menus. Try modifying the existing connection before creating a new one to see if any exist. Or, you can delete the one that
exists and create a new one. You will need to know if the ISP uses PAP or CHAP, User login, User Password....etc to answer the questions, or
once again just keep trying until you get a connect.

In a Terminal window:
```

man pppd
man pppdconfig

```

will give you added information.

Once you have pppconfig set up wvdial should: modem offhook, dialout,
make a connection, transfer to ppp.  You may have to open firefox and
uncheck the work offline box to get firefox connected.

When you are finished, close firefox, go to the open terminal window
and terminate wvdial with CNTL C.  Close that Terminal window.

Success, Now you can try setting up Gnome-PPP.

Good Luck!

lkraemer

---

