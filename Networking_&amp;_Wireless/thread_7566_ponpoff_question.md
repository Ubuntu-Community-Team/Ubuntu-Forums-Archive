---
title: "pon/poff question"
date: 2004-12-08
forum: Networking &amp; Wireless
---

### Post by elder68 on 2004-12-08
I am having troubles getting connected to the internet. I am using a Motorola 56K externat modem, which has worked fine with a variety of liniux distributions that I have tried. The unit itself is an AMD/Duron.

wvdial: I have been able to connect with the internet with wvdial.

However, I would like to be simply able to click on an icon on the desktop. So I installed the "Modem Lights" applet on the task bar at the top. I them went on to set up pppconfig. Under "advanced features" I added my user name, presuming that this adds me to the "dip" group.

Now what happens if I connect through the "Modem Lights" the modem comes alive and pciks up the phone line but does not dial out. Checking further, I went to a root terminal and tried "pon" again, and again the modem came alive and picked up the phone line, but once more it did not dial out.

Any help would be appreciated.

Thank you, Bill.

---

### Post by az on 2004-12-08
pon.wvdial
poff.wvdial

Those will work when you are setup with wvdial.

pppconfig will set you up to use pon and poff.

pon will dial the connection named "provider"
pon NET will dial the connection named NET.


Add your user to the dip group with the addvanced options in pppconfig.

---

### Post by elder68 on 2004-12-08
Thank you for the following:

[QUOTE=azz]pon.wvdial
poff.wvdial

Those will work when you are setup with wvdial.[/QUOTE]

Thanks I know about these but they don't work  under preferences with the "Modem Lights" applet on the task bar.

> pppconfig will set you up to use pon and poff.
pon will dial the connection named "provider"
pon NET will dial the connection named NET.
Add your user to the dip group with the addvanced options in pppconfig.

Did all of the above and as far as I have got is what I outlined in my first message.

I have been looking forward to using Ubuntu  and I find this dialup problem out of step with what seems to be a very nice package. I have been through two versions of Mandrake, three versions of Suse, Xandros and all of them I was able to be in contact with my ISP in moments after getting the distro installed. I have spent hours with trying to do the same with Ubuntu but to no avail. Wvdial does work but it is a klunky way of getting on to the net in the face of the way other distros accomplish it. 

The unit I am using mostly has Libranet installed on it. A Debian based distribution which installed easily and had me on the net in momnets. As did Xandros, another Debian based distribution. So why not Ubuntu?

---

### Post by az on 2004-12-09
Did you set up your dial-up information with pppconfig, too?

Do sudo tail -f /var/log/messages as you dial out with pon to see what is happening...

---

### Post by elder68 on 2004-12-09
[QUOTE=azz]Did you set up your dial-up information with pppconfig, too? Do sudo tail -f /var/log/messages as you dial out with pon to see what is happening...[/QUOTE]

Thank you for the above and it is yes to both questions. The screen of information I got from the second command, might just as well have been written in  Latin for I could get from it. :(

A bit back though, someone suggested I try Gnome-ppp. So I googled it and found the latest version on Debian unstable. It is only a small file and it installed without a problem with "dpkg -i gnome-ppp". Two minutes later it was connection me to the net without a problem. When it is installed it can be found on the "Internet" portion of the menu. Why Ubuntu left this our of their Gnome configurarion beats me. It certainly was not on my system beforehand as I searched everything under; "locate gnome*"

So now I am a happy camper... :)

Bill.

---

