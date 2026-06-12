---
title: "Dial-Up Internet: Have To Reboot System to Reconnect"
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by CyBeR_WoLf on 2008-04-22
[CENTER]**[COLOR="Red"]_[SIZE="3"][SIZE="2"][SOLVED - READ POST #3 ON THIS PAGE][/SIZE][/SIZE]_[/COLOR]**[/CENTER]

I think this is another sl-modem-deamon bug. I've been searching all forums, help files, and have done numerous searches on Yahoo and Google in regards to a problem I've been having with sl-modem and I couldn't find anything regarding my particular situation (in reference to this problem regarding dial-up Internet connection) so I guess it's time to post it here and hope someone can help me resolve it. I have discovered from my searches that sl-modem is loaded with bugs.

OS: Ubuntu 7.10 Gutsy
System: Toshiba Laptop Satellite 1400 series
Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (Toshiba Software Modem AMR)
Modem Driver: sl-modem-daemon (SmartLink software modem daemon)
Internet connection method: wvdial

When I first connect to the Internet there is no problem however, when I disconnect (Ctrl + c, or close the terminal), I cannot reconnect to the Internet unless I reboot the system.

If I try to reconnect without rebooting there are two different errors that will appear..

I get the following text after disconnection (Ctrl + c) if I try to reconnect using the same terminal that was used for the previous connection..

(The 1st line is from the previous Internet connection that was closed, the 2nd thru 7th lines is what appears when trying to reconnect, and no connection is made)
---------------------------------------------------------------
WvDial<*1>: Disconnecting at Tue Apr 22 22:00:45 2008
personal@personal-computername:~$ wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvDial<Err>: Cannot open /dev/ttySL0: No such file or directory
WvDial<Err>: Cannot open /dev/ttySL0: No such file or directory
WvDial<Err>: Cannot open /dev/ttySL0: No such file or directory
personal@personal-computername:~$ 
---------------------------------------------------------------

If I close the terminal from the previous Internet connection and open a new terminal to type in "wvdial", then the following text will appear, and no connection is made..
---------------------------------------------------------------
personal@personal-computername:~$ wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial<*1>: Sending: ATQ0TQ0
WvDial<*1>: Re-Sending: ATZZ
                           personal@personal-computername:~$
---------------------------------------------------------------

So, the only way I can reconnect to the Internet is to reboot my computer which is very irritating. I've found info about fixing this problem for DSL and other types of Internet connections which do not help me at all since I am still using Dial-Up. There must be a way to fix this for Dial-Up users too?

I have output information from scanModem files if requested for assistance in resolving this problem/bug.

P.S. - If the connection is dropped during a session, wvdial automatically redials and reconnects without any issues. The only time reconnection is not possible is after disconnection (Ctrl + c, or closing the terminal). So this appears to be possibly some sort of disconnection problem with the sl-modem-daemon.

Thank-you in advance for any assistance,
CyBeR_WoLf[COLOR="Red"][COLOR="Black"][/COLOR][/COLOR]

---

### Post by Goldpin on 2008-05-02
Try using sl-modem daemon 2.9.9d+e-pre2-7etch2 it works for me both in Feisty and after a Gutsy upgrade.  Can't get it to work with Hardy.

---

### Post by _duncan_ on 2008-05-02
I had the same error using wvdial under Hardy 8.04. In my case, it's a problem with wvdial, not with sl-modem-daemon. For the same reason, gnome-ppp, which is the GUI frontend for wvdial, also gives the same error.

My suggestion is to use pppconfig, pon and poff to set up, connect and disconnect. It works very well with Hardy. If you want a graphical interface, then consider using KPPP instead.

---

### Post by CyBeR_WoLf on 2008-05-02
Thanks for the idea Goldpin. I tried it, but I still ended up with the same problem. I did a complete removal of sl-modem daemon 2.9.10+2.9.9d+e-pre2-5ubuntu4, replaced it with sl-modem daemon 2.9.9d+e-pre2-7etch2 as you suggested, and I also just upgraded from gutsy 7.10 to 8.04 just prior to reading your reply and trying what you said worked for you but I guess I need to find a different solution in my case.

---

### Post by CyBeR_WoLf on 2008-05-02
Yep, same problem using GnomePPP regarding my situation too as well as wvdial _duncan_.
I'll test your two suggestions later tonight and post the results here afterward to let you know if it worked.

---

### Post by CyBeR_WoLf on 2008-05-02
KPPP, isn't that for the K-desktop rather than Gnome which is used in Gutsy?

Can K-applications be used (and function properly) with a Gnome desktop?

---

### Post by Reg Editor on 2008-05-02
See if unplugging the modem then plugging it back in works if you have used Ctrl + c and later want to connect to the internet again

---

### Post by _duncan_ on 2008-05-02
> **CyBeR_WoLf said:**
> KPPP, isn't that for the K-desktop rather than Gnome which is used in Gutsy?

Can K-applications be used (and function properly) with a Gnome desktop?

Yes, KDE apps can work with gnome desktop. It normally requires bigger downloads though since a lot of dependent KDE library packages will be added to the default gnome-desktop installation.

An efficient way to do this is to get pppconfig working first so that you at least have a working internet connection, then use a package manager to install KPPP so you won't have to bother hunting down all the dependent packages. If I remember correctly, installing KPPP on my fresh Ubuntu Hardy install required 10+ packages and about 30+ MB of download using synaptic package manager. Definitely not something pleasant to do on an Ubuntu box without internet connection.

P.S. Ignore the 2nd paragraph. I forgot you can connect using wvdial. It's just reconnection that is the problem.

---

### Post by CyBeR_WoLf on 2008-05-03
> **Reg Editor said:**
> See if unplugging the modem then plugging it back in works if you have used Ctrl + c and later want to connect to the internet again
Reg Editor...

once I disconnect using Ctrl + c, no matter what, even disconnecting the phone line either prior to, or after Ctrl + c I would have to reboot to reconnect.

However, occassionaly I cold reconnect if I unplugged the phone line to actually disconnect but left the terminal open from the previous connection, then plug the phone line back in and retype "wvdial".

Even doing that, most of the time the following text would appear in the terminal and no connection was made..

---------------------------------------------------------------
personal@personal-computername:~$ wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial<*1>: Sending: ATQ0TQ0
WvDial<*1>: Re-Sending: ATZZ
            personal@personal-computername:~$
---------------------------------------------------------------

---

### Post by CyBeR_WoLf on 2008-05-03
> **_duncan_ said:**
> I had the same error using wvdial under Hardy 8.04. In my case, it's a problem with wvdial, not with sl-modem-daemon. For the same reason, gnome-ppp, which is the GUI frontend for wvdial, also gives the same error.

My suggestion is to use pppconfig, pon and poff to set up, connect and disconnect. It works very well with Hardy. If you want a graphical interface, then consider using KPPP instead.
-duncan-..

Thanks very much for your suggestion, it worked!

I configured pppconfig, connected to the internet, used Synaptic to download and install kppp. Then I used poff to disconnect, configured kpp and used it to connect to the Internet, disonnect, reconnect and the having to reboot to reconnect problem is solved now!

Thank you,
CyBeR_WoLf

---

