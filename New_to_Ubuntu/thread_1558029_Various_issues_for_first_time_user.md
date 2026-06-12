---
title: "Various issues for first time user"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by mr_simon13 on 2010-08-21
I have just taken a delivery of a second hand Dell Inspiron Mini 10 netbook, and it came with an unauthentic version of Windows 7 on it, so I thought, what better time to give Linux a go?

I used my USB drive to put Ubuntu Netbook on it (the latest version, I can't remember which specifically and can't find it detailed anywhere), and I'm having a few issues.

First, the whole interface is very jerky. This is a good netbook and handled Windows 7 fine, but Linux is being very unresponsive. 

Second: I can't figure out how to hook it up to my Wifi connection. The network tab in the System area doesn't seem to give me the option, and the wifi logo at the top is greyed out with a red ! over it. Clicking that gives me the option of VPN Connections, Connect to Hidden Wireless Network, or Create New Wireless Network, the other two options above these are greyed out.

And third, I can't figure out how to change the resolution. In Monitor Preferences, it does not recognise the monitor, and has put it into a 800x576(4:3) res with 0Hz Refresh Rate, but I know this netbook can go to [EDIT: (1366x760 16:9].

Sorry to post so many questions at once, hope someone can help. Thanks

---

### Post by theepdinker on 2010-08-21
For the wireless connection, a proprietary driver may be required.

See <http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html> for instructions

---

### Post by _0R10N on 2010-08-21
Your graphic and wireless issues are caused because the proper drivers are not installed yet. Take a look in your Hardware Drivers window. Ubuntu may have already found the drivers you need, and is waiting for you to activate them.

---

### Post by mörgæs on 2010-08-21
Have you installed all updates using wired internet access?

---

### Post by ironic.demise on 2010-08-21
Monitor resolution can be changed at system>preferences>monitors but may need the drivers mentioned.

Update the system and try to open a terminal and type sudo apt-get update

---

### Post by mr_simon13 on 2010-08-21
I have sorted the wifi, as suggested it needed a wired connection first to install the appropriate drivers.

Ironic demise: "Update the system and try to open a terminal and type sudo apt-get update" - I apologise but I have absolutely no idea how to do that! Any chance you could break it down for me please?

As for the rest of the drivers, it only automatically picked two wifi drivers, and then the Hardware Drivers utility closes - how would I go about installing one for the screen?

---

### Post by DougieFresh4U on 2010-08-21
Upper left corner
Applications>Accessories>Terminal

```
sudo apt-get update
sudo apt-get dist-upgrade
```
one at a time
it will prompt you for password and when you type it, you won't see it but it will recognized

---

### Post by mr_simon13 on 2010-08-21
> **DougieFresh4U said:**
> Upper left corner
Applications>Accessories>Terminal

```
sudo apt-get update
sudo apt-get dist-upgrade
```one at a time
it will prompt you for password and when you type it, you won't see it but it will recognized

This seemed to update ok, but I'm not sure its done anything. In the monitor utility it still won't recognise the monitor, and I haven't a clue how to find the driver for it.

---

### Post by c.c.rascal on 2010-08-21
> **_0R10N said:**
> Your graphic and wireless issues are caused because the proper drivers are not installed yet. Take a look in your Hardware Drivers window. Ubuntu may have already found the drivers you need, and is waiting for you to activate them.
im a newbie  to ubuntu well even windows but this looks like the same problem ive had also what else has happened when booting back into windows from hard  drive i get a blue screen crash could this also be down to drivers thanks and very much appreciated

---

### Post by tjktyler on 2010-08-21
Under System>Administration>Hardware Drivers OR go to Terminal and type ```
sudo jockey
``` jockey is the name of the Hardware Drivers program. It will search for drivers and attempt to install them for you.

---

### Post by farsight on 2010-08-21
Hey there, 

I thought you might find this a useful source of information on your system, the output of the program potentially leading you towards the correct driver for your monitor:

[http://www.ubuntugeek.com/system-hardware-information-and-run-reports.html]("http://www.ubuntugeek.com/system-hardware-information-and-run-reports.html")

I think you might also find this page useful, however I have not used it to offer any additional support at present:

[https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")

Farsight

---

