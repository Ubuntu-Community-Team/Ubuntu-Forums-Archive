---
title: "External DSL ALCATEL modem (Speed Touch)"
date: 2006-09-06
forum: Networking &amp; Wireless
---

### Post by sshahir on 2006-09-06
I have used ADSLPPPOE thread ([https://wiki.ubuntu.com/ADSLPPPoE)](https://wiki.ubuntu.com/ADSLPPPoE)). 
After configuring PPPoE, the message says the connection is established, 
but when I try Firefox browser or ping, it is clear that the connection has not established yet.
Then I tried "dpkg -s pppoeconf", and received the following message.


---------------------------------------------------------------------------------
[COLOR="Silver"]Package: pppoeconf
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 308
Maintainer: Debian QA Group <packages@qa.debian.org>
Architecture: all
Version: 1.8ubuntu2
Depends: whiptail-provider | whiptail, ppp (>= 2.4.2+20040428-2) | pppoe (>= 3.0), ppp (>= 2.4.1.uus2-4), gettext-base (>= 0.13), sed (>= 3.95)
Recommends: locales
Suggests: xdialog
Description: configures PPPoE/ADSL connections
 Userfriendly tool for initial configuration of a DSL (PPPoE) connection.
[/COLOR]---------------------------------------------------------------------------------------

I don&#8217;t know what is wrong with the Internet connection. 

Even though external DSL ALCATEL modem is connected to my computer through RJ-45 but not USB, I have tried USBADSLMODEM/SPEEDTOUCH thread. When I try &#8220;grep &#8221; command to determine the REV=X.00, no result is obtained. So I couldn't continue with the instruction.

Can you please let me know how I can establish my Internet connection through External DSL ALCATEL modem. Thank you.

sshahir

---

### Post by sshahir on 2006-09-06
How can I establish Internet connection through External DSL ALCATEL modem (Speed Touch):confused: ?

I appreciate for any comment. Thanks.

sshahir

---

### Post by Original Brownster on 2006-09-06
Hi,
Which exact model do you have? I know there must be a few kicking around, I have one that is usb only hence the need to install speedtouch drivers and fiddle around a bit.

---

### Post by sshahir on 2006-09-06
The modem I have is an external DSL ALCATEL that is connected to my computer through RJ-45 but not USB.

I have tried to detect the modem automatically through System>Administration>Networking, but the system couldn&#8217;t detect the modem.

Then, I have tried USB based SpeedTough DSL modem installation process, USBADSLMODEM/SPEEDTOUCH thread even though the modem is not USB based.

As mentioned in the struction, I can find out about the modem type by trying &#8220;grep&#8221; command, so I tried

>**[COLOR="Blue"]grep &#8211;B l &#8220;THOMSON ALCATEL&#8221; /proc/bus/usb/devices [/COLOR]**

 to determine the REV=X.00, but NO RESAULT is provided by the command , and I have no further information about the modem unfortunately. if you have any solution in your mind, please let me know.

Thanks,
sshahir

---

### Post by Eversmann on 2006-09-06
You said you have the modem connected using rj-45, is this a modem-router adsl?

If it is, you have to configure the "router" internally to make the connection and just enable dhcp on it, ubuntu will work alone.

You won't have any other success that way if the modem isn't attached on usb. 

If you're spanish contact me and i'll give you some info to configure your modem-router, if it really is a modem-router (thru some links).

---

### Post by sshahir on 2006-09-06
> **Eversmann said:**
> You said you have the modem connected using rj-45, is this a modem-router adsl?

If it is, you have to configure the "router" internally to make the connection and just enable dhcp on it, ubuntu will work alone.

You won't have any other success that way if the modem isn't attached on usb. 

If you're spanish contact me and i'll give you some info to configure your modem-router, if it really is a modem-router (thru some links).


I am sure it is DSL modem and the connection is RJ-45, and I am also positive that it is not router. But I don't know if the modem is called modem-router or not.

Can you please let me know if you have any solution in your mind.

Thanks,
sshahir

---

### Post by Original Brownster on 2006-09-07
Eversman is right, if your connected via an ethernet cable to the DSL box you should not be following the speedtouch howtos. These are usb devices and require completely different steps to configure, yours potentially should be simple if it is just an ethernet connection as you say but you have not said the model so it's hard to help you.

The modem will have an in-built web interface which by default will have a username and password assigned along with a static ip address.
Check the manual for you modem, if you don't have one you can normally get one via the internet. If you tell us the model of the modem this will greatly help. normally there is at least a model number ie mine is an alcatel speedtouch 330, which is usb only.

---

### Post by sshahir on 2006-09-10
I got it. Thanks.

sshahir

---

