---
title: "[SOLVED] How to disable VPN autostarting?"
date: 2008-09-14
forum: Networking &amp; Wireless
---

### Post by Piraja on 2008-09-14
Dear all!

I recently installed Intrepid Ibex on my laptop. One of the few minor problems I've encountered so far is that the quiet splash is interrupted by a VPN username and password prompt: "Autostarting VPN 'openvpn'." I do not want to autostart my VPN connection at startup time &#8212; I'd rather connect during the GUI session, at will (by the command "sudo /etc/init.d/openvpn start"). Of course, I can always ignore the prompt and just press "enter" and the startup progress continues. What is more, if I do give my VPN username and password, it does not seem to start the connection &#8212; and I wonder how could it even do that, before I have even logged in... I'm not the only user of the laptop and I would like to have the quiet splash back without having to uninstall OpenVPN.

So my question is: How can I disable VPN autostarting at bootup time, or prevent the system from prompting me for VPN user information at bootup?

---

### Post by Piraja on 2008-09-17
I tried to clarify the question a little bit. Would you think this might be a bug to be reported? Hardy did not prompt for VPN user information at startup time, anyway.

---

### Post by Piraja on 2008-09-22
I spotted the file to be modified: **/etc/default/openvpn**. I uncommented the line saying **AUTOSTART="none"** and now the bootup is not interrupted by **Autostarting VPN 'openvpn'** and username prompt. Instead of that: **Autostart disabled. No VPN will be started.**

---

### Post by Piraja on 2008-10-08
Now I tried to launch an OpenVPN connection with "sudo /etc/init.d/openvpn start," but it won't work (as it used to with Hardy) since autostart is disabled!

So I will have to enable autostart &#8212; but then it will prompt for my VPN username and password at boot-up time (before the graphical login screen!), and that's definitely something I do not want to happen... 

Rather confusing. Perhaps I should file a bug report, since this did not happen with Hardy.

**P.S. (edit)** I posted a [new thread]("http://ubuntuforums.org/showthread.php?p=5931147") to the Intrepid Ibex Testing and Discussion forum and filed a [bug report]("https://bugs.launchpad.net/ubuntu/+source/openvpn/+bug/280428"), too.

---

### Post by Piraja on 2008-10-10
The solution can be found at [Launchpad]("https://answers.launchpad.net/ubuntu/+source/openvpn/+question/47501"), thanks to Thierry Carrez.

---

