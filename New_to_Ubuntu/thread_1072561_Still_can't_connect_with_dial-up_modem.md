---
title: "Still can't connect with dial-up modem"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by Bearly Able on 2009-02-17
Hi,

I've been trying to get an elderly friend online with a dial-up connection without success.  I know internal winmodems are notoriously difficult to use with Linux, and that one was no different.  I eventually got hold of a second-hand serial modem, which I know is working, and seem to get slightly further with that, but it still won't connect.  I've followed the instructions in the  [wiki]("https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-277fdde88a3b04feee00e14834388d58d7add4f9") to configure the modem using wvdialconf and then connect with wvdial.  What I get is this:```
cath@WiseOwl:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot set information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT08456043070
--> Waiting for carrier.
ATDT08456043070
CONNECT 115200
--> Carrier detected.  Waiting for prompt.
~[7f]}#@!}!}!} &}"}&} }*} } }#}%B#}%}%}&3}:H}2}'}"}(}"}1}$}%t}3})}!BTMDIPE`~
--> PPP negotiation detected.
--> Starting pppd at Tue Feb 17 15:27:43 2009
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 5710
--> Using interface ppp0
--> pppd: &#65533;k[06][08]0&#65533;[06][08]
--> pppd: &#65533;k[06][08]0&#65533;[06][08]
--> pppd: &#65533;k[06][08]0&#65533;[06][08]
--> pppd: &#65533;k[06][08]0&#65533;[06][08]
--> pppd: &#65533;k[06][08]0&#65533;[06][08]
--> Disconnecting at Tue Feb 17 15:28:14 2009
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds

```Unfortunately, I don't have sufficient understanding of what I'm looking at to know where the problem lies.  I'd be grateful for any help.

If I ever get the thing working, is there an easier way for her to connect than by opening a terminal and using wvdial?  There's a modem applet in Ubuntu that can be added to the panel, but I've never used Xubuntu before and can't find anything similar.

Thanks for any assistance you can offer.

Lesley

---

### Post by yoyoned on 2009-02-17
try running wvdial as root
```
sudo wvdial
```

---

### Post by corncob on 2009-02-17
There's a program in Ubuntu called GNOME PPP.  If you don't see it in Applications > Internet, look in Applications > Add/Remove > Internet or, finally, in System > Administration > Synaptic Package Manager and install it.  It should then show up in Applications > Internet.  I've used it successfully in the past but I had a hardware modem from USRobotics ($60).  I'm assuming that Xubuntu is pretty much like Ubuntu but I never have used it.

---

### Post by Bearly Able on 2009-02-18
Thanks, yoyoned, but now I'm confused.  The wiki says use ```
sudo wvdial
``` but in reply to a question [elsewhere ]("http://ubuntuforums.org/showthread.php?p=6717309#post6717309")in the forums, I was told> sudo wvdial would try to open that program using root access, which is wrong, and why it failed.  Please can you explain what the problem is, and why using sudo would fix it?  Many thanks.

Corncob - thanks for the tip about Gnome PPP.  If I ever get connected, I'll give it a go.

---

### Post by lkraemer on 2009-02-18
The easiest thing to do is to open a Terminal window.
Type:
```

sudo pppconfig

```

Then go through the menus. Try modifying the existing connection before creating a new one to see if any exist.  Or, you can delete the one that
exists and create a new one.  You will need to know if the ISP uses PAP or CHAP, User login, User Password....etc to answer the questions, or
once again just keep trying until you get a connect.  Shouldn't be that hard.

In a Terminal window:
```

man pppd
man pppdconfig

```
will give you added information.

The Error 16 was because the Modem hung up, most likely because login
information was incorrect in (pppconfig) your configuration files as
noted in the message text.

lkraemer

---

### Post by corncob on 2009-02-18
In my version of Ubuntu (Ultimate 1.2) there is, in addition to GNOME PPP, an internet application called KPPP.  Is this a graphical interface for pppd?

---

### Post by Bearly Able on 2009-02-19
Thanks, guys, I'll go round later this morning and have another go.  
Corncob - I understand from the wiki that KPPP is a Kubuntu application and I'm pretty sure it won't run on Xubuntu, but thanks for the tip anyway.  (I'd have stuck with Ubuntu, which I'm a bit more familiar with, but the machine is very low on RAM and I was advised to use Xubuntu instead.)

---

### Post by TopEnder on 2009-02-19
G'Day,

I agree with lkraemer to use pppconfig after you got the info suggested by him you should not have any problems been using pppconfig since Ubuntu 6.06,  (I have tried wvdial but always seem to have sort of problems).  
A couple of points you need to be a member of 'dip' & 'dialout' you can do/check this by: 
sudo adduser username dip    &  
sudo adduser username dialout    
also my modem port is:   /dev/ttyS0.  To check it out in terminal to start the modem 'pon' & 'poff' to turn the modem off. if it works then you shound have no problems in setting-up GNOME PPP - Gnome Dialup Tool

---

### Post by Bearly Able on 2009-02-19
Ikraemer, TopEnder, you guys are stars! :)  pppconfig has solved the problem and I can connect with pon, no bother.  Thanks for your help.

I'm having less success with Gnome PPP, but I didn't have much time to play about with the settings.  I understand it uses wvdial, and I'm having the exact same problem with Gnome PPP that I had before.  I'll try again tomorrow, but at least now we can get online.  Thanks again.

---

### Post by lkraemer on 2009-02-20
Now that pon works you should be able to use wvdial, assuming that
the wvdial configuration file is correct.  Just remember that you must
leave the Terminal window open as long as you are connected, and a
CNTRL C will terminate the session in the open Terminal window.
When wvdial is working, next step is Gnome PPP.

lkraemer

---

### Post by cebobbitt on 2009-02-20
I have been using dialup since Breezy. The pppconfig is probably the best way to do this and if the isp disconnects on a timed basis, just set it to persist and it will redial the dropped number. I have used gnome-ppp too and it works well and gives a online window that lets you keep track of how long you are online. The thing I like about gnome-ppp is you can set it up with various phone numbers that you can pick at random, but with pppconfig you have to manually set the phone number. If you can get online and download gnome-ppp I would recommend it. Try to set it up first by itself and if you get any conflicts you may have to use a text editor and comment out anything in wvdial and let gnome-ppp set wvdial. Gnome-ppp is just a frontend for wvdial but it is a very good program. I hope this helps, best of luck.

---

### Post by Bearly Able on 2009-02-22
Hi guys,

Thanks for the further help.  I've temporarily abandoned my struggle with Gnome PPP until I get the updates done.  As it's a new install of Xubuntu, I have 188 updates listed, and it took over 3 hours to do the first 27 yesterday.  (Dial-up is *very* slow in this area - something to do with aluminium in the telephone cables, I seem to remember.  Our 56kbps modem used to run at about 22kbps, 28 on a good day, which is why we eventually went for broadband.)  Anyway, once I've got the updates done, I'll have another go at configuring Gnome PPP and report back.  Watch this space!

Thanks again for taking the trouble to help.

Lesley

---

### Post by Bearly Able on 2009-03-10
Sorry I've taken so long - I've had 'flu and my friend's had visitors.  I've spent an hour this morning trying to configure Gnome PPP but still no joy.  I get pretty much the same messages I got trying to configure wvdial (which makes sense), I can't view web pages or e-mail and it disconnects after 30 seconds.  I've commented-out lcp-echo-interval30 and lcp-echo-failure4, and added replacedefaultroute in the pppd options file, but it makes no difference.  Despite having very little idea what I was doing, I tried changing other options that looked as if they might help, but nothing did.  (I've since changed them all back.)  

Just as I write this, I'm wondering if I've been editing the wrong file.  I learned from the "How To" that Gnome PPP creates its own wvdial.conf file, and I edited that to show the same settings as pppconfig, which does work.  Now I'm wondering if Gnome PPP also has its own pppd options file?  I've been using ```
gksudo gedit /etc/ppp/options 
```

When I configured pppconfig, I set it to use PAP authentication, but there's no option for this that I can find in Gnome PPP (or wvdial).  The log still shows the message  ```
Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
``` which makes me think the problem may be here, although I don't understand how, or what to do about it!

I've also checked /var/log/messages, but it's blank.

Can someone please explain what I'm doing wrong and how to correct it?  Many thanks.

---

### Post by lkraemer on 2009-03-11
OK, Here is what your problem is.  If you open up a Terminal Window and
change to /etc/ppp then do a ls -alt you will see the following:

larry@Larry-laptop:/etc/ppp$ ls -alt
total 84
drwxr-xr-x 127 root root 12288 2009-03-11 08:04 ..
drwxr-s---   2 root dip   4096 2009-01-20 03:19 peers
drwxr-xr-x   8 root dip   4096 2009-01-20 03:15 .
-rw-------   1 root root    80 2009-01-20 03:15 chap-secrets
drwxr-xr-x   2 root root  4096 2009-01-20 03:15 ip-down.d
drwxr-xr-x   2 root root  4096 2009-01-20 03:15 ip-up.d
-rw-------   1 root root  1628 2009-01-20 03:15 pap-secrets
-rwxr-xr-x   1 root root  1754 2007-10-04 12:57 ip-down
-rwxr-xr-x   1 root root  1892 2007-10-04 12:57 ip-up
-rwxr-xr-x   1 root root   784 2007-10-04 12:57 ipv6-down
drwxr-xr-x   2 root root  4096 2007-10-04 12:57 ipv6-down.d
-rwxr-xr-x   1 root root   922 2007-10-04 12:57 ipv6-up
drwxr-xr-x   2 root root  4096 2007-10-04 12:57 ipv6-up.d
-rw-r--r--   1 root root 13486 2007-10-04 12:57 options
-rwxr-xr-x   1 root root   137 2007-10-04 12:57 pppoe_on_boot
drwxr-xr-x   2 root root  4096 2007-06-21 21:55 resolv

ALL files have owner of root......So, you need to become root to
modify them or preface each command with sudo.  Plus notice that the
file "options" has -rw-r--r--

So user has rw- access, group has r-- access, and other has r-- access.
where r is read, w is write, and x is execute. - is NO ACCESS.....
so, user has read & write but NO EXECUTE ACCESS.........etc.......

To become root you can use sudo su in a terminal window, and when finished
use exit to terminate. Or you can preface each command with sudo.....
larry@Larry-laptop:/etc/ppp$ 
larry@Larry-laptop:/etc/ppp$ sudo su
root@Larry-laptop:/etc/ppp# exit
exit
larry@Larry-laptop:/etc/ppp$
(Notice the change from $ to # when I used sudo root above?)

This should get you to where you can edit options, but if you ran
sudo pppconfig it should have set the proper options for you, and if needed
you can modify the file as needed by running it a second time using modify.

I thought you were able to connect by using pon and poff.  If so, then
your problem is most likely configuration setup in wvdial.  Once wvdial is
configured correctly and will connect and you can get online then try setting up GnomePPP.


lkraemer

---

### Post by Bearly Able on 2009-03-11
Hi Ikraemer and thanks for the reply.

Yes, my problem is with getting wvdial configured.  Thanks to your earlier post, I got connected with pppconfig and pon.  I wouldn't be bothering with Gnome PPP at all, but it's not my system, it belongs to an elderly friend, and I think an easier way of connecting would encourage her to use the internet more on her own.

I'm too much of a beginner at this to be able to work out where the differences lie, that let me connect with one app and not the other.  I *can* edit /etc/ppp/options, but I don't understand *what* I need to edit in the file.  As I say, I've already commented-out lcp-echo-interval30 and lcp-echo-failure4, and added replacedefaultroute, but that doesn't help and I don't know where to go next.

The Gnome PPP log is giving me the same messages I was getting before in wvdial, including the warnings about PAP and CHAP being flaky, which I don't understand.  Maybe they're nothing to do with the problem, but if something doesn't work and there's a message saying "Warning", I tend to assume there's a connection.

I'm at home at the moment, and won't be able to try anything on the system until tomorrow, but if you could point me in the right direction, I'd be grateful.

Thanks again.

---

### Post by lkraemer on 2009-03-11
If you will try to run the following in a terminal window:

```

sudo wvdialconf /etc/wvdial.conf

```

You should get a configuration file like this at
/etc/wvdial.conf  (you may need to add a few things...)

[Dialer Defaults]
Modem = /dev/ttyACM0
Baud = 115200
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = USB Modem
;AutoDNS = yes
;Carrier check = yes
Stupid Mode = yes
Phone = 7024460568
Username = [email]yourname@yourisp.net[/email]
Password = yourpassword

now assuming that your pap-secrets and or your chap-secrets file is
correct you should be able to use wvdial to dial the connection with:

```

wvdial /etc/wvdial.conf

```
(/etc/wvdial.conf is the default.... so you don't need to use it.....)

You should hear the modem go OFFHOOK with dialtone, Dial, and connect.
If your config file is correct you should authenticate and then control
will be passed to ppp.  You will see several strings of HEX (funny characters)
and then you should stay connected.  (you will use CNTL C to 
terminate the session when you are done.)  You may have to uncheck the
box marked OFFLINE when you open your browser to make it online.  Surf,
then terminate the open session with CNTL C in the open terminal window
where you initiated wvdial.

When this is all working you can work with Gnome PPP to get it functional.
I haven't used it yet.  (I don't have hardwired phone lines to access for
further testing.  Will be back on dialup in about 2 months......but you
won't want to wait that long.)

Check your pap-secrets and chap-secrets files in /etc/ppp/
They should have references to your ISP.  I don't have a copy of mine
in front of me, and it will be 2 months before I get back to them.
I'll assume that since you ran pppconfig they were set correctly
for your ISP since pon/poff works.

I wish I had a copy of my configuration file here with me. 

wvdial.conf info:
[http://linux.die.net/man/5/wvdial.conf](http://linux.die.net/man/5/wvdial.conf)

PPP HOWTO:
[http://tldp.org/HOWTO/PPP-HOWTO/index.html](http://tldp.org/HOWTO/PPP-HOWTO/index.html)

PAP-SECRETS info:
[http://tldp.org/HOWTO/PPP-HOWTO/x1034.html](http://tldp.org/HOWTO/PPP-HOWTO/x1034.html)

CHAP-SECRETS info:
[http://tldp.org/HOWTO/PPP-HOWTO/x1053.html](http://tldp.org/HOWTO/PPP-HOWTO/x1053.html)

Setting up PPP Manually
[http://tldp.org/HOWTO/PPP-HOWTO/manual.html](http://tldp.org/HOWTO/PPP-HOWTO/manual.html)

lkraemer

---

### Post by GeorgeVita on 2009-03-11
Hi, I thing you must use **sudo wvdial** to dial (enter your password when asked), otherwise you have the "...--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied..." error message.

In your 1st post you were connected but the provider "hung up" the line (exit code=16) probably because did not get your user/pass. You should always try sudo wvdial (when using wvdial to connect from terminal) and possibly add to your /etc/wvdial.conf the line **Stupid mode = 1** just to go directly to ppp negotiation (read **man wvdial** and **man pppd** from terminal). 

Regards,
George

---

### Post by Bearly Able on 2009-03-11
OK, this is the wvdial.conf file:

```
[Dialer Defaults]
Init = ATZ
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = 08456043070
Modem = /dev/ttyS0
Username = myusername
Carrier Check = no
Password = mypassword
Baud = 115200
```

(I'm still at home, but I took a copy of this in case I needed it, or screwed up so badly I wanted to restore the original!)  The username and password are exactly as they are in pppconfig, so they can't be the problem.

The modem dials OK, and if I'm using Gnome PPP it shows it's connected, but it disconnects every time after 30 seconds.  The log shows this kind of entry:

```
--> Starting pppd at Tue Feb 17 15:27:43 2009
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 5710
--> Using interface ppp0
--> pppd: &#65533;k[06][08]0&#65533;[06][08]
--> pppd: &#65533;k[06][08]0&#65533;[06][08]
--> pppd: &#65533;k[06][08]0&#65533;[06][08]
--> pppd: &#65533;k[06][08]0&#65533;[06][08]
--> pppd: &#65533;k[06][08]0&#65533;[06][08]
--> Disconnecting at Tue Feb 17 15:28:14 2009
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
```
During the 30-second "connection", neither Firefox nor Thunderbird can get online, even though they're in online mode.

Does any of this help?

I'm hoping to get over tomorrow to have another go and I'll be able to check the pap-secrets and chap-secrets files then.

Thanks for your help.

---

### Post by Bearly Able on 2009-03-11
Hi GeorgeVita, thanks for your reply.

I'm really confused about the use of sudo here.  When I followed the wvdial instructions in the wiki in the first place, it said use sudo, which I did.  Then I was told (in another thread) that using sudo is wrong, and that's why I'm having problems.  If wvdial needs to be run with sudo, shouldn't Gnome PPP (which is what I'm ultimately trying to configure?) ask for a password, because it doesn't.

---

### Post by GeorgeVita on 2009-03-11
I believe that is easier to connect directly with wvdial (sudo wvdial) and then find a better User Interface.

The wvdial program tells you very clear about what happening. The only you possibly miss is what parameters (initialize at commands) needs your modem or your provider, so helpful "search strings" for google or forums are: the modem type (manufacturer, etc), your provider and the version of Ubuntu.

---

### Post by lkraemer on 2009-03-11
OK, I just got my Laptop to connect with an external USR modem.
First time I have ever tried this Compaq V5201US laptop.

Checking settings of: /etc/ppp/options
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

Edit pap-secrets with:
```

sudo gedit /etc/ppp/pap-secrets

```

pap-secrets setting; (your ISP may use chap.......)

```

# OUTBOUND connections

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.

#	*	password
"yourusername@yourisp.net" provider "yourpassword"

```

wvdial.conf
```

[Dialer Defaults]
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

My wvdial.conf will be different because I used a USB to Serial Adapter.

dial from within a Terminal window with:

```

wvdial

```

Don't worry about the errors that are displayed for pap-secrets
and chap-secrets.  Mine has them also. As long as ppp doesn't
disconnect or error out you should be able to open firefox and surf.

Mine does not connect each and everytime because of a terrible connection.  Try it several times............You will hear the
modem varying speeds before the quiet connection.  :~)

WHEW!!! It is SLOW!

Now you should be ready for Gnome PPP.

lkraemer

---

### Post by Bearly Able on 2009-03-12
Thanks, Ikraemer, you're a real star.  I really appreciate the time you've taken over this.  I'd been back over everything and still couldn't find the problem, until I compared my wvdial.conf file with yours, and wondered what would happen if I added "Stupid mode = yes".  Answer - success! :D  I couldn't believe it - I sat anxiously waiting for it to disconnect on me but no, that's it finally fixed.  (Somehow the solution seems rather apt.)  After that, it was a snap to configure Gnome PPP and add a launcher to the panel.

Thanks again.

Lesley

---

### Post by lkraemer on 2009-03-13
Now, one last thing you need to do.....

Make yourself a document that will be your guide with all the steps
in order, so next time you won't have to try and remember what you did
two to four years ago.  Also I'd recommend that you open a Terminal window
and use the following commands:

```

cd /
cd /etc/ppp
sudo cp pap-secrets pap-secrets.sav
sudo cp chap-secrets chap-secrets.sav
cd ..
cp wvdial.conf wvdial.sav

``` 

That way you will have backup files.....just in case.
You might even want to save the files on a usb stick for reference.

lkraemer

---

### Post by Bearly Able on 2009-03-14
Hi Ikraemer, that's excellent advice and I'll go round and do it today, before I forget.  My friend is delighted with Gnome PPP - fewer steps for a beginner to remember.  Now I just have to hope she doesn't get so enthusiastic she decides to get broadband; I've discovered she doesn't have an ethernet card, and I don't fancy trying to configure a USB modem!

Thanks again for all your time and trouble.

Lesley

---

### Post by Bartender on 2009-03-16
I went thru most of your ordeal a coupla years ago.
[http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)
Might be helpful reading because it's pretty much step-by-step.  Also, I tried to write it so that the uninitiated might understand.  I hate it when someone skips over parts that they know by heart but you don't.
Although wvdial and ppp were both unable to find that serial-to-USB cable, it's definitely at /dev/tty/ACM0.  That's a zero at the end, not an "Oh".
I'd really like to try out that new US Robotics 5637 USB modem, but I have three of the old USR serial externals and can't justify the expense.

Regarding broadband, you should find it much much easier than dial-up!  Does your friend's PC have an available PCI slot?  Any NIC from a reputable co. should work.

On the other hand, you never know what'll work.  A friend is connected to DSL via Qwest.  His modem has a USB output and ethernet.  An old Ubuntu test PC connected to the internet just as easily via either port.  Ethernet will be faster, but the USB was still pretty good.  We didn't have to do anything to make it work.

---

### Post by Bearly Able on 2009-03-19
Hi Bartender,

Thanks for the tips - I may need them!  We spent *hours* on her dial-up, getting her a visa waiver to visit her cousin in Wisconsin, then trying to arrange travel insurance, and she started talking about broadband.  Two days later, her phone company sent her details of what looks like a really good deal...

From what I remember of the last time I peered inside the box, yes, there's a spare PCI (had to look that one up on Wikipedia).  So do I really just need to buy an adapter card and plug it in?  If I've understood you correctly, I have found one that says it's compatible with Linux and costs peanuts; I can't quite believe it could be this simple!

Thanks again.

---

