---
title: "How do I set up my modem?"
date: 2004-11-04
forum: Networking &amp; Wireless
---

### Post by lhtown on 2004-11-04
I have an external serial/usb port USRobotics businesss modem model number 3CP453294.

All I want is a basic connection that is easy to connect and disconnect to my isp to surf the internet and download files.

I have investigated wvdial and pppconfig, but I can't seem to get them working. I am using a serial cable to connect to my computer. My modem seems to be connected on /deb/ttyS0.

Could someone please walk me through the basic steps? I must be missing something painfully obvious.

---

### Post by az on 2004-11-04
If this is your modem, then it shoudl work with linux...
[http://www.overstock.com/cgi-bin/d2.cgi?PAGE=PROFRAME&PROD_ID=683151](http://www.overstock.com/cgi-bin/d2.cgi?PAGE=PROFRAME&PROD_ID=683151)
[http://www.usr.com/support/product-template.asp?prod=3294](http://www.usr.com/support/product-template.asp?prod=3294)


What happens when you try wvdial or pppconfig.

What happens when you go into the network configuration panel and try to add a dial-up device?

---

### Post by mr_ed on 2004-11-08
At my parents' house I tried the same thing and couldn't get it going.

I tried the Network Settings widget.
In the Network Settings panel, when I clicked on "Activate" it did nothing.  There was no feedback at all (and the modem made no noises), so I can't tell you any more than that.

I'm seriously thinking of porting over kppp to gtk+.  Is it worth it to do so when there is this (nice-looking) Network Settings tool?

---

### Post by az on 2004-11-09
Try the command line first.

sudo pppconfig
make sure that you enter all the information and save your setup.

sudo pon provider
(I keep the default connection name)

sudo tail -f /var/log/messages
(To see what is going on)  Post it if you still have trouble.  If it works - add the Modem Lights applet to your panel.  Pon and Poff are already the defaults...  Sudo pppconfig to add your user to the appropriate groud (advanced options)

---

### Post by lhtown on 2004-11-09
Ok,

Thanks for your help. It's working now. First of all, I was using wvdial. When I edited the configuration file manually, I didn't remove the comment ";" before the edited lines which of course makes the program ignore the file just as the comment "#" which is more widely used.

Secondly, my purpose in all of this was that I was trying to set it up on a friends computer, but was trying it at my house first. Here in the Dominican Republic, we have two choices for an ISP. I use Tricom and my friend uses Verizon. After I fixed the configuration file described above, wvdial worked great at my house using my isp (Tricom). I couldn't get pppconfig to do the trick- it did nothing on the command "pon."  Then, I took the modem over to my friends house to set it up with her isp (verizon). Wvdial refused to work. It dialed fine but the isp rejected my password. After some time on the phone with technical support (and they really did try), we were unable to get it going. I played with it some more but without successl. Finally, as a last resort, I tried pppconfig. It works like a charm. 

Go figure.

I do hope that the upcoming ubuntu release includes a (much) better dialer. Everything else that I use is great, but it is a bit cheesy to ask my friends to enter pon and poff and so forth. I don't mean to knock pppconfig, but it isn't what most desktop users are looking for as a means to connect to their isp.

---

### Post by lhtown on 2004-11-09
BTW, thanks for the tip about the modem lights.

---

### Post by Tommy on 2004-11-10
I'd like a "best practices" step-by-step for setting up ppp -- I've tried several things and once I got it working but the permissions were wrong, then Modem Lights quit showing when the modem was dialing or online, and I had other problems.

I gather the Networking application in Gnome can't make a working ppp connection, or maybe it can but not in all circumstances. pppconfig seems to be much more reliable in creating or modifying a ppp setup.

For awhile everything looked like it was working but pppconfig and Networking obviously don't look at the same files. Modem Lights won't show the status on anything now, even when the system actually does connect.

---

### Post by Tommy on 2004-11-10
I'm away from the errant computer but a Google search may have turned up a hint on making Modem Lights work:

[http://www.kryogenix.org/days/2004/03/16/modemlights](http://www.kryogenix.org/days/2004/03/16/modemlights)

> 
To make it work, you need to set the preferences as follows:
Device: ppp0
Lock file: /var/run/ppp0.pid
Disconnection command: poff -a
and make sure that /dev/modem exists and is a link to your modem device.
 
I'll have to drive over later and try that....

---

### Post by mr_ed on 2004-11-11
[QUOTE=azz]If it works - add the Modem Lights applet to your panel.  Pon and Poff are already the defaults...  Sudo pppconfig to add your user to the appropriate groud (advanced options)[/QUOTE]

Thanks.  After futzing around a bit, I finally got it.

I added the modem lights applet, but it still wouldn't work.

Things I needed to do:
Add my provider to the applet's pon command (duh!)
sudo vi /etc/group
added my user to the "dip" group.  (Your "groud" didn't register on me... it wasn't until I ran pon as user that I clued in)
Logged out and logged back in.
Voila.  Modem Lights works.

---

