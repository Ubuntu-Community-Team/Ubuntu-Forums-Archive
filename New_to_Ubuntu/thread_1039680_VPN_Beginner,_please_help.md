---
title: "VPN Beginner, please help"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by DavidPcs on 2009-01-14
I am no expert in VPN's in general, as will become painfully obvious, but I have a project with a client trying to migrate to Ubuntu from windows. The cliente is also no expert in VPN's but has one that he uses regularly,  it is very simple to connect to with windows, in Vista, yeah, Vista, oh well, through the help wizard it can be setup in minutes with the address user and password and basically is automatic other than that.  Then he has a program, custom make it seems, that he runs in a dos prompt that, using the vpn connection, configures his session on the vpn server to access other servers from that point....
In Linux,  after many hours of investigation, experimentation and finally acheiving through KVpnc a successful connection, according to the screen of KVpnc, that user xxxxx is connected successfully to xxx.xxx.xxx.xxx  etc..   but now what?????
His dos program does not work with wine, a window opens, completely black and never does anything,  although other dos programs load and execute successfully with wine and wine doors..  It seems that with a virtual machine of Winxp running inside of linux, it can work, but the point was to be independent of windows.   
But other than that specific example, in general,  after making the vpn connection, I have no idea how to take advantage of it, how to use it.   It does not appear on the desktop, in the list of devices in my file manager, network places,  nothing,  I'm connected, cool,  now what?  The internet and local red continues to funcion as normal, it&#347; not causing any problems, I just don't know what do to do access the resources availble through this vpn connection.
This is the absolute beginner talk forum.  Please don't laugh too hard......

Thanks in advance...

David

---

### Post by cmnorton on 2009-01-16
Here are some links. Once you get the basics of the initial VPN setup, you may find that getting the connection to work is trial and error after that.

[https://help.ubuntu.com/community/VPNClient](https://help.ubuntu.com/community/VPNClient)
[https://wiki.ubuntu.com/VPN](https://wiki.ubuntu.com/VPN)
[http://tipotheday.com/2007/11/28/connect-to-windows-vpn-server-pptp-with-ubuntu-gutsy/](http://tipotheday.com/2007/11/28/connect-to-windows-vpn-server-pptp-with-ubuntu-gutsy/)
[http://ubuntuforums.org/showthread.php?t=201349](http://ubuntuforums.org/showthread.php?t=201349)

---

### Post by yknivag on 2009-01-16
I'm no expert, but I've done some research recently into this for my own needs.

You say he establishes the VPN in Vista and then "runs a DOS batch file to configure it". Do you have access to the DOS batch file? Can you tell us what it is doing?

My understanding is that all that is needed is a VPN client application on the user end and a VPN server (or some companies call them concentrators ?Cisco) on the other end.  The two must know about each other, have users configured and, in some setups, exchanged a certificate/key. So long as they both are talking the same protocol then all should work seamlessly, the remote PC should be granted a local IP on the inside of the network it's connecting to.

One thing to be very careful of is that the local IP of the client in it's local network must be in a different subnet to the pseudo-local IP it will be given by the VPN server, otherwise complex routing rules are required.

Hope this helps but if not, could you determine what the DOS program is doing (or post it here, suitably anonymised) and also give the result of trying to ping a known working host IP inside the remote network?

---

