---
title: "Xvnc inetd solution stopped working"
date: 2016-06-10
forum: Networking &amp; Wireless
---

### Post by bnilsson on 2016-06-10
We have been using a Xvnc server system in XDMCP mode to present a login dialog to the VNC viewer, so that the user can log in as from a local screen.
This has been working fine until recently, I suspect the recent tightening of security has changed the conditions.
We suddenly got a black screen instead of the greeter.
We tried to reinstall from scratch using the same methods as when we started, and now we cannot even get a black screen.


OS: Ubuntu 14.04 LTS xfce4
openbsd_inetd
Xvnc server:TurboVNC Xvnc -inetd mode

/etc/services
....
[FONT=Monaco]# Local services[/FONT]
[FONT=Monaco]vnc            5950/tcp

[/FONT]
/etc/inetd.conf
[FONT=Monaco]vnc     stream tcp nowait nobody /opt/TurboVNC/bin/Xvnc Xvnc -inetd -query localhost -once -geometry 2560x1024 -depth 24[/FONT]

/etc/lightdm/lightdm.conf
...
[FONT=Monaco][XDMCPServer][/FONT]
[FONT=Monaco]enabled=true[/FONT]



This combination used to work fine, but now TurboVNC viewer responds for connection "vnchost":50 with "Connection closed".
Testing with telnet:
[FONT=Monaco]telnet localhost 5950[/FONT]
[FONT=Monaco]Trying ::1...[/FONT]
[FONT=Monaco]Trying 127.0.0.1...[/FONT]
[FONT=Monaco]Connected to localhost.[/FONT]
[FONT=Monaco]Escape character is '^]'.[/FONT]
[FONT=Monaco]RFB 003.008[/FONT]
[FONT=Monaco]Connection closed by foreign host.[/FONT]

So it seems like some security issue.
Any constructive input is appreciated.

BN

Note: In this post, my system is NOT Ubuntu studio, as is shown in my profile.

EDIT:
I have googled around, but I found no threads on any relevance later than 2014, and I think this problem is new.
Many of them was actually the ones helping me to set this up in the first place, which is no longer working.

---

### Post by bnilsson on 2016-06-13
Does anybody have a still working xinetd / Xvnc combo?
I feel no urge to move to xinetd if this is broken also.

Edit:
I find no logfiles from inetd nor Xvnc.
Am I looking in the wrong place? (/var/log, /etc,...)

---

### Post by bnilsson on 2016-06-17
I removed TurboVNC and openbsd-inetd, replacing them with vnc4server and inetutils-inetd.
Then I changed the Xvnc path parameters in /etc/inetd.conf:
 
vnc 	stream tcp nowait nobody /usr/bin/Xvnc4 Xvnc4 -inetd -query localhost -once -geometry 1280x1024 -depth 24 -securitytypes=none


and rebooted.
It worked right away.

Note: The "-securitytypes=none" option had no effect in the previous configuration.

Please be aware that this config is without security or encryption, so it should be used with in a safe evironment only, or with ssh tunnelling.

---

