---
title: "Trying to connect with freeNX on 7.10"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by qwert231 on 2008-11-04
Server is Ubuntu 7.10 and I did:
apt-get install freenx (after updating the sources as per this site:
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX))

Set up NoMachine free client on my windows box. I set up the parameters (very basic) and get this:
Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: mark
NX> 105 startsession  --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --media="0" --session="HomeServer" --type="unix-gnome" --geometry="1024x768" --kbtype="pc102/en_US" --screeninfo="1024x768x32+render" 

Permission denied (publickey,password).
NX> 280 Exiting on signal: 15



So, I'm guessing that since I did apt-get but didn't do the '--setup-nomachine-key' parameter is why it's not working.

I tried this:
nxsetup --install --setup-nomachine-key


but get this:
root@linux800:~# nxsetup --install --setup-nomachine-key
Setting up /etc/nxserver ...done
Setting up /var/lib/nxserver/db ...done
Setting up /var/log/nxserver.log ...done
Setting up known_hosts and authorized_keys2 ...done
Setting up permissions ...done

----> Testing your nxserver configuration ...
Warning: Could not find nxdesktop in /usr/lib/nx. RDP sessions won't work.
Warning: Could not find nxviewer in /usr/lib/nx. VNC sessions won't work.
Error: Invalid value "APPLICATION_LIBRARY_PRELOAD=/usr/lib/libX11-nx.so.6.2:/usr/lib/libXext-nx.so.6.4:/usr/lib/libXcomp.so:/usr/lib/libXcompext.so.1:/usr/lib/libXrender-nx.so.1.2"
Warning: Invalid value "DEFAULT_X_SESSION=/etc/X11/xdm/Xsession"
         Users might not be able to request a default X session.
Warning: Invalid value "COMMAND_START_KDE=/usr/bin/dbus-launch --sh-syntax --exit-with-session startkde"
         Users will not be able to request a KDE session.
Warning: Invalid value "COMMAND_START_GNOME=/usr/bin/dbus-launch --sh-syntax --exit-with-session gnome-session"
         Users will not be able to request a Gnome session.
Warning: Invalid value "COMMAND_START_CDE=cdwm"
         Users will not be able to request a CDE session.

  Errors occured during config check.
  Please correct the configuration file.



If I have to use SSH keys, that is fine, if it's more secure. Not sure how though.

I would like to do a Gnome session, so that error is also an issue.

Where should I go from here?

---

