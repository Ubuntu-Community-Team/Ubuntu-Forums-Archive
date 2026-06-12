---
title: "Printer server ?"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by WitchCraft on 2010-05-21
Question:

I've got a HP CM 1312 MFP (Color Laser Printer + Scanner)
From what I've read, at least the printer seems to work under Linux.

Now, unfortunately, that printer only has an USB connection, and no ethernet/wifi.
Now I have a router + wireless, and I would like to be able to print on this printer from more than one computer. 

My computer would be Linux, the other three are Windows (XP, Vista, Windows 7).

Now, I have a little Linux ubuntu server, which I use to host websites.
So it just occured to me, if I attach the printer to the Linux server, it should be possible to make the printer available over the network.

Which program is best as printer server in this situation ?
CUPS ?

And will it support Windows (I know it is possible, just not how) ?
Anybody has any great tips/tutorials ?
To make matters worse, my server doesn't use Xorg (or rather I didn't want to install it), and I'd prefer if it stayed that way...

Oh, and btw, is it possible to make the scanner available over the network, too ?
(of course, assuming the scanner is supported by Linux)

---

### Post by lykwydchykyn on 2010-05-21
If it will work with Linux, you can use the Linux box to share it out with other machines.

The simplest way to do this is with CUPS by itself, then your Windows machines can just use it like an IPP (internet printing protocol) printer.

See this page:
[https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)

---

### Post by lykwydchykyn on 2010-05-21
> **WitchCraft said:**
> 
Oh, and btw, is it possible to make the scanner available over the network, too ?
(of course, assuming the scanner is supported by Linux)

Yes, but as far as I know only to Linux clients.  You'd use saned for this.

---

### Post by WitchCraft on 2010-05-24
It's simple after all.


In the cups config file (/etc/cups/cupsd.conf) after:
Listen localhost:631

add:
Listen 192.168.1.4:631
in order to access the configuration from non-localhost computers.

Then you can access CUPS at
[http://192.168.1.4:631/](http://192.168.1.4:631/)


HP's printer driver can be installed on console, with /usr/bin/hp-setup -i (apt-get install hplip), if you omit the -i, it will require the GUI, and on the console, it won't tell you that you need  -i...

Then it will download the firmware and install the printer.
You then still have to set it to default printer.

then you can test: echo "Hello World" > lpr
You can also check the queue: lpq



For setting up a network scanner with sane, there is a very nice tutorial, here:
[https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)
What it omits, you need to do:    sudo apt-get install xinetd
but that's all.

For older ubuntu versions:
[http://hardc0l2e.wordpress.com/2009/07/10/sane-sharing-in-ubuntu/](http://hardc0l2e.wordpress.com/2009/07/10/sane-sharing-in-ubuntu/)


You can then use the sane scanner from Linux and from Windows.
Linux requires xsane client, and for windows, there is also a xsane port:
[http://www.xsane.org/xsane-win32.html](http://www.xsane.org/xsane-win32.html)


As you can see here, I've still some problems with removing the authentication...
[http://ubuntuforums.org/showthread.php?t=1491949](http://ubuntuforums.org/showthread.php?t=1491949)

---

