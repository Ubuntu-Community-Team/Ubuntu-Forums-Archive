---
title: "Starting Wireless Networking on ACER Aspire 5044WLMi"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by norules on 2008-12-13
I have recently installed Ubuntu 8.10 on my ACER Aspire 5044WLMi and am having problems starting wireless networking. Acer-wmi and the appropriate atheros drivers are installed.  However, starting wireless networking requires first that the card be turned on with the command:

echo 1 > /sys/devices/platform/acer-wmi/wireless

and the rebooting the computer.  

Is there a way to turn on the card during the init process?

Thank you for your consideration.

---

### Post by JKBurton on 2008-12-13
I recommend adding the line to /etc/rc.local using the command "gksu gedit /etc/rc.local".
Add the new command right before the "exit 0" line.

Reboot, and cross your fingers :)

rc.local's intended as a place for us to stick commands that need to be run at start-up. However, Linux startup is complex, and if rc.local gets run too early or too late for the command you want, there are lots of other options. It's worked fine for the setup commands I need to do for my own network though, so I'm optimistic.

Keep smiling!

---

### Post by albinootje on 2008-12-13
If it doesn't work through /etc/rc.local then in this specific situation you might want to take a look at : /etc/sysctl.conf
Make sure you use the right syntax.
See also : man sysctl

---

### Post by norules on 2008-12-13
Adding the line to rc.local does turn the wireless card but to late to establish networking.

It does simplify the process but a reboot is still necessary.

Only a minor inconvenience considering the windoze alternative.

---

### Post by JKBurton on 2008-12-13
You know the little network notification applet on the panel that tells when you're connected? You can probably uncheck "Enable Networking", then check it again, instead of having to reboot.

If you'd like to make it perfect, though, we can find another place to stick the command during startup.  Let me know if you'd like to continue.

---

