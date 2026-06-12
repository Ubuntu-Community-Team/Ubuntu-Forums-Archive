---
title: "Netplan, Networking, OpenVPN"
date: 2019-11-19
forum: Networking &amp; Wireless
---

### Post by databoy2k on 2019-11-19
Hey All:

I've got Ubuntu Server 18.04 running various services, particularly Pi-Hole and DNSMasq. I've been trying to clean up various issues with DNSMasq and have run into some sort of a problem with my networking. 

Prior to things breaking, and I'm not sure how I did so, I could not get OpenVPN Server to start on boot. I always had to use systemctl start openvpn@server. This is despite running systemctl enable openvpn@server. 

At some point I had networking issues that resulted in me re-doing the static IP binding using netplan apply. Since doing so, systemctl start openvpn@server results in "A dependency job for [email]openvpn@server.servic[/email]e failed." The status just says, "Dependency failed for OpenVPN connection to server."

If I go over to systemctl status networking, I get "Starting Raise network interfaces..." and then "Unknown interface enp4s0" from sh and ifup. I suspect that this is the failed dependency.

Ifconfig returns enp4s0 as the network adaptor, as well as my static IP settings. 

What do I need to do to get this up and running again?

Thanks for your help.

---

### Post by Skaperen on 2019-11-19
**systemd** is now at the steering wheel.  lots of new stuff to learn.  my personal _workaround_ was to have a user with _passwordless_ **sudo** permissions be autologged in at boot up.  then its [COLOR=#0000cd][FONT=courier new]**~/.config/autostart/autostart.desktop**[/FONT][/COLOR] (in xubuntu your universe may be different) _autostarted_ a terminal which started a bash shell.  then [COLOR=#0000cd][FONT=courier new]**~/.bashrc**[/FONT][/COLOR] started the various services i wanted to run and exited the shell.  this one user was dedicated to this purpose.  it made it easy to restart everything by coding that [COLOR=#0000cd][FONT=courier new]**~/.bashrc**[/FONT][/COLOR] to first stop all the services.  so all i need to do was login to that user instead of reboot.[COLOR=#0000cd][FONT=courier new][/FONT][/COLOR]

---

### Post by databoy2k on 2019-11-20
Thanks. That tip should help once i fix the dependency issue.

Any idea how to troubleshoot the networking dependency?

---

