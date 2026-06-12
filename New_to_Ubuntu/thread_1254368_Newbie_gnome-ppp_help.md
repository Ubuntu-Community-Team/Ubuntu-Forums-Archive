---
title: "Newbie gnome-ppp help"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by pj_kare on 2009-08-31
Having problems installing gnome-ppp into Jaunty. When we try to install we get
"ERROR Dependency is "not satisfiable".wvdial. We try wvdial and get more errors, dependency not satisfiable ....

Have searched forum and googled for 3 days and are still no further advanced. Any help would be gratefully accepted ...:confused:

---

### Post by CatKiller on 2009-08-31
When I needed to install dial-up stuff previously, I did so by first connecting that computer to a wired network to get it all set up. I have no idea if it was necessary to do that, but it's possible that it will make things straightforward for you.

Don't forget that you can install more than one thing at one time to satisfy dependencies. You haven't said how you're trying to install them, but either (for example)

```
sudo apt-get install gnome-ppp wvdial
``` (if you're installing from repositories) or ```
sudo dpkg -i gnome-ppp_0.3.23-1_i386.deb wvdial_1.60.1+nmu2_i386.deb
``` (if you're installing .deb files) will install both of them.

Don't forget that you can check dependencies for a particular package at packages.ubuntu.com, but if you're using a package manager because you've got the machine temporarily connected to the Internet through other means, all the dependencies will be sorted out for you (that's pretty much the point of a package manager).

---

### Post by Bartender on 2009-08-31
In case the Linux PC is offline -

Use any connected Windows PC and a thumb drive.  Google "ubuntu packages".  Go to the first hit.  Partway down the page find the window to type in a package search.  The package search will search for various versions of Ubuntu, so make sure it's set to Jaunty.  I believe it is Jaunty by default.  Type in gnome-ppp.  Download the resulting package to the thumb drive, plug the thumb drive into the Linux PC, open the thumb drive, double-click on the gnome-ppp package to begin installation.

I'm pretty sure this package will install and does not need any further dependencies.  wvdial should work after you install gnome-ppp.  On my Jaunty install, wvdial was broken, or missing parts, out of the box but installing the gnome-ppp package made wvdial functional.

And of course it also made gnome-ppp work...

---

### Post by GeorgeVita on 2009-08-31
Hi **pj_kare**,
searching this forum for 'wvdial dependencies' shows your thread and the next one with the answers:
[http://ubuntuforums.org/showthread.php?t=846522&highlight=wvdial+dependencies](http://ubuntuforums.org/showthread.php?t=846522&highlight=wvdial+dependencies)
> **GeorgeVita said:**
> Hi ****,
assuming that you do not have an internet connection to the Ubuntu 9.04 PC, which is i386 32 bit, you need all files below:

1. [http://packages.ubuntu.com/jaunty/i386/libxplc0.3.13/download](http://packages.ubuntu.com/jaunty/i386/libxplc0.3.13/download)
2. [http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-base/download](http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-base/download)
3. [http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-extras/download](http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-extras/download)
4. [http://packages.ubuntu.com/jaunty/i386/libuniconf4.4/download](http://packages.ubuntu.com/jaunty/i386/libuniconf4.4/download)
5. [http://packages.ubuntu.com/jaunty/i386/wvdial/download](http://packages.ubuntu.com/jaunty/i386/wvdial/download)

and install them in above sequence 1-2-3-4-5

take a look my note at:
[http://acomelectronics.com/GeorgeVita/restore_wvdial.html](http://acomelectronics.com/GeorgeVita/restore_wvdial.html)
where you can find a .zip file also.
Regards,
George

---

### Post by pj_kare on 2009-08-31
Thanks everyone :)
 
Bartender -  already d/l'd gnome-ppp package. Tried to install, that's when we got wvdial error. Then we tried wvdial, got more dependency errors, that's why I posted, just kept getting these errors and got lost and confused.
 
Cat - jaunty PC can only use dialup, can't get online with jaunty, so can't use apt get for anything yet.
 
George - thanks, off to try your fix. Looked for gnome-ppp dependencies, never thought to try wvdial ... sigh ...

---

### Post by zvacet on 2009-08-31
Download it from [here.]("http://packages.ubuntu.com/jaunty/gnome-ppp")You see packages marked with red ball,they are dependencies.Yoz have to download them all and install them first.Then install gnome-ppp.

---

### Post by pj_kare on 2009-08-31
George .... thank you ... that got gnome-ppp installed ... yea !  Now to wrestle a winmodem into submission ... 
 
zvacet - nice to know that now ...  very hard for almost total ubuntu newbs to make head or tail of "how to do" things ...

---

### Post by rob86 on 2009-08-31
Hey, I'm a complete newbie to Ubuntu as well, only installed it two days ago, but managed to get my old ESS Dial up modem connected to the internet using WvDial, GnomePPP but NOT the Network Admin Tool which still won't work (but I don't care, Gnome PPP is fine). 

If you need any help...feel free to PM me (I don't regularly check the forums..) I'm no Linux Guru by any means, just a newbie who spent a heck of a lot of time the last couple days figuring out how to install Wvdial, gnomeppp, editing confs, downloading drivers, etc..... I know how frustrating it can be.

---

### Post by Bartender on 2009-09-01
Frustrating indeed.  The oldest, most low-tech way to get online is also the hardest to configure.

---

### Post by hallenr on 2009-09-17
Rob, that is indeed very encouraging:) I have a Reliance zte880, usb datacard for my laptop, and am still struggling to get connected. Can you help me?

---

### Post by mustaq2001 on 2009-09-18
> **rob86 said:**
> Hey, I'm a complete newbie to Ubuntu as well, only installed it two days ago, but managed to get my old ESS Dial up modem connected to the internet using WvDial, GnomePPP but NOT the Network Admin Tool which still won't work (but I don't care, Gnome PPP is fine). 
 
If you need any help...feel free to PM me (I don't regularly check the forums..) I'm no Linux Guru by any means, just a newbie who spent a heck of a lot of time the last couple days figuring out how to install Wvdial, gnomeppp, editing confs, downloading drivers, etc..... I know how frustrating it can be.
 
 
Hi,
 
I am also stuck with a similar problem. I some how managed to install WvDial and configure pppconfig; but could not find the right driver for my modem. My machine has dual boot. Currently i am accessing the net through Vista. While in Vista i see that my modem is "Agere systems hda modem". I could not find a linux driver for this modem. 
 
Could you please point me to a location where I can find a linux driver for this modem.
 
Thanks,
Mustaq

---

### Post by toloykhan on 2010-04-16
Hello every one....,
am totally new in linux and community and am facing problems with my network connection and application installation ...
my modem is sudani mdsl usb AC8700 800M 
want to connect to the internet plz help me

---

### Post by lotharmat on 2010-04-16
> **toloykhan said:**
> Hello every one....,
am totally new in linux and community and am facing problems with my network connection and application installation ...
my modem is sudani mdsl usb AC8700 800M 
want to connect to the internet plz help me


I'd post this as a new thread - You will get more help that way rather than posting in a thread marked solved. :wink:

---

### Post by pradeepthundiyil on 2010-05-20
Hi,

Do this..........

1.Install wvdial & gnome-ppp

2. sudo chmod 777 /etc/wvdial.conf

3. sudo gedit /etc/wvdial.conf 

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 9600
New PPPD = yes
PPPD Path = /usr/sbin/pppd
Modem = /dev/ttyUSB0
ISDN = 0
; Phone = <number>
; Password = <passwrd>
; Username = <usrnam>

4. sudo pppconfig

in the new (below) window select Create and give ok... 
 
Type provider name (say reliance) and give ok 
 
Select Dynamic and give ok 
 
Select PAP and give ok 
 
Enter your Reliance Number and give ok 
 
Password is same as your Reliance Number, enter it and give ok 
 
Select Tone and give ok 
 
Enter #777 and give ok 
 
Enter yes 
 
Now all set. Ensure Everything is fine. Select Finished then ok 
 
Finally in the last wind select Quit and give ok


5. sudo chmod a+x /usr/sbin/pppd
6.$ sudo chmod a+rw /etc/ppp/pap-secrets
7. $ sudo chmod a+rw /etc/ppp/chap-secrets

sudo gedit /etc/ppp/options

# Set the maximum number of IPCP configure-NAKs returned before starting
# to send configure-Rejects instead to <n> (default 10).
ipcp-max-failure 30

Code:
gksudo gedit /etc/ppp/options
Add this line and save:

replacedefaultroute

if this is done then replace the # in front of the

replace the # in front of the " ipcp-max-failure 30 " do not use both lines


configure gnome-ppp, with ur username & password.. 

Reboot and click connect in gnome-ppp:guitar:

---

