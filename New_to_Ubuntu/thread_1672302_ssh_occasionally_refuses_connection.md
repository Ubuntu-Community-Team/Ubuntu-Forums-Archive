---
title: "ssh occasionally refuses connection"
date: 2011-01-20
forum: New to Ubuntu
---

### Post by punjabdapunk on 2011-01-20
Hi, 
I'm a noob but with 2 months experience behind me now... I've installed a headless ubuntu sever 10.04 which is running well.

I've installed open-ssh and can connect via a ssh client from any of my machines Windoze, OS X and Android.

Occasionally, I get a connection refused on port 22. I can't work out why? I have to reboot the machine before I can connect:(

The only thing I can guess at is that I use wake on lan to start my server and sometimes I don't connect via ssh for at least 20 mins. I think the screen saver might be kicking in or the server falls into some suspend state.

Is there a log I can look at to work out what the cause of the connection refusal is?

Alternatively, is it possible to stop the screen saver kicking in or prevent suspend mode?

I have googled extensively on both the screen saver and suspend mode but am usually confused by what works for desktop ubuntu and server ubuntu. I'm concerned with server ubuntu only. I'll keep looking but any advice or pointers will be highly appreciated.

Later.

---

### Post by Brandon Williams on 2011-01-21
"Connection refused" indicates that you can get to the machine but that ssh is not listening. I don't use wake-on-lan, so I don't know about any potential oddities associated with system initialization, but it certainly could be the case that the machine is just coming up and hasn't started the ssh server yet.

This is a server, right? Why would it be running a screensaver? Is someone logged in locally? If the machine does have a graphical login setup, check the power manager configuration for gdm to verify that it isn't configured to monitor to suspend or shutdown due to inactivity. From the gdm login screen, you should be able to right-click on the power-manager icon to get to the configuration dialog.

---

### Post by punjabdapunk on 2011-01-21
Hi Brandon,
It is a server and there is no GUI installed and hence no gdm.

I remember when installing ubuntu server that the screen I attached at the time would go blank. I assumed that could have been a screen saver but your reply has got me thinking that is might just be a power saving mode the screen falls in to.

In that case I'm not sure why occasionally the ssh connection is refused.

It might be a red herring but the screen going blank shouldn't cause a problem. I'm a little stuck. Is there a log I can look at?

---

### Post by rezaervani on 2011-01-22
Can you ssh into localhost ?

> ssh localhostBy default, the OpenSSH server logs to the AUTH facility of syslog, at the INFO level. If you want to record more information - such as failed login attempts - you should increase the logging level to VERBOSE.

To increase the level, find the following line in your sshd_config: (/etc/ssh/sshd_config)

> LogLevel INFOand change it to this:

> LogLevel VERBOSE
Now all the details of ssh login attempts will be saved in your /var/log/auth.log file.

----
Yayasan Rumah Ilmu Indonesia
[http://www.rumahilmuindonesia.or.id](http://www.rumahilmuindonesia.or.id)
Official Archive Mirror Ubuntu
[http://cermin.rumahilmu.org](http://cermin.rumahilmu.org)

---

### Post by punjabdapunk on 2011-01-26
Thanks rezaervani,
I'll give that a go and see what the log has to say after I receive another failed to connect...

---

### Post by asmoore82 on 2011-01-26
I once had a similar sounding issue with older hardware -
even if I was working to the max over SSH the machine would still go to sleep.

There ended up being sleep Settings in the BIOS that "snooped" traffic from the PS/2
mouse and/or keyboard and would sleep if they became idle for a set timeout.
I was able to turn this off in the BIOS completely and never had the problem again.

Oh, but looking over the thread again, it could be a kernel lock up because
the kernel now does modesetting. Some combinations of kernels and graphics hardware
lock when trying to modeset on a disconnected or powered off monitor.

Get it to do it again and see if the machine responds to a ping.

If not, try adding "nomodeset" to your kernel line boot options.

---

