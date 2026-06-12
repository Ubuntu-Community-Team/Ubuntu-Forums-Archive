---
title: "how do i start prey?"
date: 2011-08-12
forum: New to Ubuntu
---

### Post by cosmoshell on 2011-08-12
i installed prey and cant seem to figure out how to start it.

---

### Post by jtarin on 2011-08-12
[http://preyproject.com/faq](http://preyproject.com/faq)

---

### Post by MickSulley on 2011-08-16
I have a similar problem.  I have installed prey but the tutorials I have found say to run the configurator from Applications > System Tools, but it is not there.  I have tried installing from Synaptic and from terminal.

I have run /etc/prey/config and it doesn't seem to do anything.

I have run /usr/lib/prey/prey.sh and it says that I need to enter the device key in the control panel, but I have no control panel to use.

I'm on Ubuntu 11.04 64 bit.

Any ideas?

Thanks
Mick

---

### Post by jtarin on 2011-08-16
The reason you’re not seeing anything is because Prey is made that way, so that the thief won’t be able to detect it. The best way to check if everything is fine is to log into your Control Panel (through the link sent to your email) and make sure your device’s status is OK. You can also mark it as missing and enable some of the report modules to see how it will work in real action. Once you get a report, you can safely delete it and set back the status from missing to OK.

[http://preyproject.com/faq](http://preyproject.com/faq)

---

### Post by jtarin on 2011-08-16
Please mark this thread as solved if the OP solved their problem.

---

### Post by MickSulley on 2011-08-17
The control panel says 'Device still unverified!'.  I think I need to enter the key into the laptop somewhere, but I don't know where to enter it.

The tutorials I have found show an entry in System Tools, but I do not have one.

Troubleshooting says to run in check mode, but I get 

mick@mick-laptop:~$ sudo /usr/share/prey/prey.sh --check
[sudo] password for mick: 
sudo: /usr/share/prey/prey.sh: command not found
mick@mick-laptop:~$ 

so it seems that something is not installed or not set up correctly.

Any ideas?

Thanks
Mick

---

### Post by MickSulley on 2011-08-19
Fixed it!!!

I uninstalled and then downloaded from their website.  There is a link just under the download button that takes you to specific downloads for various OS's.  Downloaded from the Ubuntu link and it works fine, I now have Prey Configurator under Applications > System Tools

---

### Post by jtarin on 2011-08-19
> **MickSulley said:**
> Fixed it!!!

I uninstalled and then downloaded from their website.  There is a link just under the download button that takes you to specific downloads for various OS's.  Downloaded from the Ubuntu link and it works fine, I now have Prey Configurator under Applications > System ToolsYou might edit the name in the menu to make it less obvious to someone stealing your computer.
Mark this thread solved if you will.

---

