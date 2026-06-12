---
title: "remote desktop only on local network"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by akkad on 2009-04-29
since 9.04 installed am unable to access my machine remotely where in settings>>preferences>>remote desktop it gives a messages telling "Your desktop is only reachable over the local network. Others can access your computer using the address ...", how can i solve this also there is a new checkbox in the remote desktop settings "configure network automatically to accept connections" shall i select it or not?

---

### Post by akkad on 2009-04-30
any one ??

---

### Post by nhasian on 2009-04-30
Hello akkad,

do you have some firewall software installed?  or are you using a different port number? I believe the standard port 5900.

---

### Post by bolucpap on 2009-04-30
It probably means that your router/modem/etc does not forward messages for port 5900 to your computer. For this, you have to set up port forwarding on your router/modem/etc.

---

### Post by akkad on 2009-04-30
it is working now where i dont know why & how !!! i didnt change anything.
so far my setup is like:

- i configured an no-ip.com account by using DNS(A).

- my gateway dhcp supports setting an static ip to specific mac address, so i set my own static ip.

- i added a port forwarding entry in my gateway pointing to port number 5900 with my static ip.

- i enabled the remote desktop from ubuntu with unchecking the option box "configure network automatically to accept connections".

these settings are working on my ubuntu 9.04.

---

### Post by garferi on 2009-04-30
I also have this problem.
"Your desktop is only reachable over the local network. Others can access your computer using the address localhost."
In Ubuntu 8.10 (Gnome 2.24.1), there was an "Advanced" tab where I was able to allow connections from internet. I don't understand why Gnome developers remove everything what worked fine in previous releases...
I also opened port 5900, but no success.
Any idea? Thx!

---

### Post by halitech on 2009-04-30
the setting for local network is referring to the local computer. Because of the way *nix is set up, everything pretty much runs as a network so if you only allow local connections, its saying to only accept connections from the local computer. That option needs to be unchecked. I would hazzard a guess that the devs set it that way as default is to keep the system safe in case it gets enabled and has a connection to the net which could put it in danger of being taken over.

---

### Post by dublea on 2009-05-04
I'm having the same issue.  I've opened port 5900 on my router and still can not connect from outside my network.  Any help would be great.

---

### Post by halitech on 2009-05-04
did you uncheck the option where it says 'Only allow local connections'?

---

### Post by weekdaysailor on 2009-05-06
The "Advanced" tab, where that option used to be, has been "disappeared" - it's no longer in the UI. 

Bad bad NannyState developers!!

---

### Post by halitech on 2009-05-07
well isn't that nice of them :( I don't have it installed at the moment so not sure where to look now.

---

### Post by DBrocks on 2009-05-07
Hey,

Take a look at VNC: Its basically remote desktop software. You run the server-side client on your ubuntu box, and then you use a client program to tunnel into it. I know its a bulky solution, but it may work for you.

---

### Post by darkmatterhari on 2009-05-07
> **DBrocks said:**
> Hey,

Take a look at VNC: Its basically remote desktop software. You run the server-side client on your ubuntu box, and then you use a client program to tunnel into it. I know its a bulky solution, but it may work for you.

VNC is a protocol, and Vino is the pre-installed VNC server for Ubuntu.  It is the back-end being controlled by the Remote Desktop Preferences utility in question.

I've been having the same problem.  Installing a *different* VNC server did do the trick though, this appears to be a Vino bug.  I installed tightvncserver ```
sudo apt-get install tightvncserver
``` then ran ```
tightvncserver
```   It walks through a couple options (passwords for remote access, view-only settings) then when the CLI program exits you can successfully VNC to the box from the outside world on 5900.

---

### Post by pricetech on 2009-05-07
I get my best results using NX from nomachine.com.  VNC was problematic in Hearty and NX worked so well I stuck with it in Jaunty.
It works as long as I stick with the default port across the board.

---

### Post by happbd on 2009-05-11
I had the same issue with the default vnc on 9.04 (vino).  Local connections were permitted but outside connections were not.  I installed vnc4server and everything is working fine with no changes to my router/firewall.

Installation instructions:
[http://ubuntuforums.org/showthread.php?t=197964](http://ubuntuforums.org/showthread.php?t=197964)

---

### Post by obryantr on 2009-05-11
Same problem. In 9.04 there is no box to uncheck, for allowing only local connections, the advance tab is gone

---

### Post by macabro22 on 2009-06-04
> **obryantr said:**
> Same problem. In 9.04 there is no box to uncheck, for allowing only local connections, the advance tab is gone

What the heck is up with that?

---

### Post by Bussy14 on 2009-06-15
I had the same problem with 9.04, no advanced tab, server was not listening to the port (even default one), but I just found out how to set all this.

To use an alternative port:
run gconf-editor from terminal
in the open window go to:
/desktop/gnome/remote_access
Change the alternative_port value (mine was 5900) to the one you want
Select (check) use_alternative_port

And now, run:
/usr/lib/vino/vino-server
(you can make it run at login by addin the previous line in the: System->Preferences->Startup Applications)

Good Luck!

---

### Post by zensys on 2009-06-17
I had the same problem but was able to solve it by unchecking the option "configure network automatically to accept connections" This option requires the UPnP feature in your router to be enabled.

Surprisingly (I find computers have a strong resemblance to women) now I also have outside connectivity with the automatically accept connections option checked and UPnP disabled.

Hope this helps more than it confuses!

---

### Post by lmpmbernardo on 2009-07-02
I got the same problem after a yum upgrade (I guess). The checkbox for allow remote connections disappeared. But upon reboot the message that only local connections were allowed was replaced by a message indicating the ip addresses I could use to connect, one of them being the external (router) address.

---

### Post by Trigger on 2009-07-02
I think this symptom began after an upgrade for me as well.  I went on my router and UPnP is enabled so this in conjunction with the "configure network automatically to accept connections" may not be the case.  Unfortunately I am at work and cannot connect to my Ubox at home so I can not turn this option off to see if this alone is the issue.  

When I get home I will un-check this and bounce the box and see if I can even RD into itself let alone from another computer.

---

### Post by Trigger on 2009-07-02
Well I'm home, w00t half day!

I got it all working again and this is what I did...
First thing was to unchecked the "configure network automatically to accept connections".  I also applied some updates that popped up and then bounced the box. 

I left the machine for a few came back and noticed the PC did not reboot and it was telling me that the Remote Desktop was still open.  Knowing it is vino I went into the SysMan and stopped it.  the process was taking up about 50% CPU.

After the reboot I still could not get in via VNC.  I then did the following:

sudo ufw disable

That did the trick.  So I guess with the "configure network automatically to accept connections" unchecked and the ufw disabled all was back to normal.


Now my question is...what have I opened up by disabling ufw?

---

### Post by tito_drum on 2010-01-15
> **akkad said:**
> since 9.04 installed am unable to access my machine remotely where in settings>>preferences>>remote desktop it gives a messages telling "Your desktop is only reachable over the local network. Others can access your computer using the address ...", how can i solve this also there is a new checkbox in the remote desktop settings "configure network automatically to accept connections" shall i select it or not?

I just found this. It may help you
[https://help.ubuntu.com/community/VNC/Servers](https://help.ubuntu.com/community/VNC/Servers)

There is a part that says 

To allow connections from anywhere,
In versions up to Ubuntu 8.10 ("Jaunty Jackalope"): click on the tab marked Advanced, then untick Only allow local connections
In Ubuntu 9.04 ("Karmic Koala"): press alt-f2 to open the "run application" window, then type in gconftool -u /desktop/gnome/remote_access/network_interface and click Run

---

### Post by karmikdingo on 2010-01-18
Well I've tried that (on jaunty and karmik) and it's not opening the access beyod the "local network"... I'll have a closer look tomorrow and see if I can open the  access without touching the router or firewall setings!

cheers!

K

---

### Post by RubenK on 2010-02-17
Any luck or changes on this issue yet?

---

### Post by kbasarab on 2010-02-19
I had luck with Disabling the "Automatically configure network connection" link and also enabling port 5900 on my router.  Working like a champ now on 9.10.

---

### Post by DonMGard on 2010-03-27
+1 for disabling UPnP.

What does disabling UPnP do exactly?

---

### Post by autonomy on 2010-05-05
> **Bussy14 said:**
> run gconf-editor
go to: desktop/gnome/remote_access
Select (check) use_alternative_portThis worked for me, so thanks! Remote Desktop was already in my startup applications.

---

### Post by andyhelloween on 2010-06-18
As somebody said here, in "Remote Desktop Preferences", it says: "Your desktop is only reachable over the local network....", i.e: localhost.

I unchecked "allow other users to view your desktop", reboot, activated again and worked. "Configure network automatically..." is unchecked.

It's strange though... yesterday it was working... and today it wasn't.. don't ask me why.

Cheers!

---

