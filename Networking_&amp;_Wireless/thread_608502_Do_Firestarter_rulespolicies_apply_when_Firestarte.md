---
title: "Do Firestarter rules/policies apply when Firestarter is not running?"
date: 2007-11-10
forum: Networking &amp; Wireless
---

### Post by jasontan6 on 2007-11-10
As the title says.

I added a few policies to open up ports for certain applications to work properly. My question is: do these ports remain open when Firestarter is not running?

Using Firestarter 1.0.3, on Gutsy.

---

### Post by jpkotta on 2007-11-10
Firestarter is a frontend for iptables, the firewall mechanism in the Linux kernel.  It basically just configures iptables, which is always present.  However, Firestarter undoes its configurations when it "shuts down", so it will act like there is no firewall unless you configure iptables manually.  Don't think of Firestarter as something that runs in the background.  Think of it as a configuration tool that can switch the firewall on and off.

If you're interested in just opening ports, the default is to allow everything.  On a fresh install, all ports are "open" in that iptables is not blocking them, but nothing is listening on them, so it doesn't matter.

---

### Post by ruibernardo on 2007-11-10
> **jpkotta said:**
> Firestarter undoes its configurations when it "shuts down", so it will act like there is no firewall unless you configure iptables manually.  Don't think of Firestarter as something that runs in the background.  Think of it as a configuration tool that can switch the firewall on and off.

Firestarter will set up iptables, even if its GUI isn't on the desktop.  When you setup Firestarter to open, lets say port 80, and you close the Firestarter GUI, port 80 will be opened, even after you reboot, until you open Firestarter GUI again and disable that port.

When you change something in the GUI, you are changing things in /etc/firestarter/ and it's subdirectories. When you reboot, /etc/init.d/firestarter is executed, looks at what settings are in /etc/firestarter/ and runs a script that sets up iptables according to the present configuration. You just need the GUI to change the setup, block all access in case of emergency and to watch the open connections and the events log. So there is no need to have it always opened.

To have Firestarter working the right way, you **must** run the "Wizzard" in the "Firewall" menu the first time you run Firestarter or when you change the network interface. Look here to setup Firestarter: [http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html](http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html)

To verify if Firestarter is working, even if there is no GUI in the desktop, try running:

```
sudo iptables -L

```

---

### Post by OrangeCrate on 2007-11-10
Running "Shields UP" occasionally will tell you not only the overall integrity of your firewall,** but which ports are open**, closed, or stealthed.

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

From the Firestarter Q/A page...

> Q: How can I test if the firewall is working for sure?

The only way to know for sure if your firewall coverage is complete is for an outside party to test it. You can not run nmap or some other network tool to test the firewall from the firewall host itself.

There are many free sites on the Internet that will provide a remote scan of your system. Here are a few that we have found useful, as well as the expected result with the Firestarter default policy loaded:

    * Sygate Security Scan
      The scan will report Unable to detect any running services!
    *** Shields Up!**
      The scan will report all ports as stealthed.


[http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)

Edit:

Here's the Firestarter manual:

[http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)

---

