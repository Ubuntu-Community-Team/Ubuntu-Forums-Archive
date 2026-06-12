---
title: "Serial Port--Terminal command?"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by jitsu on 2007-04-30
What is the terminal command to use to check whether my modem, which is on the serial port, is recognized?

thanksi

---

### Post by hartz on 2007-05-01
Hi Jitsu.

Ubuntu (Linux actually) does not use a driver for serial-port connected modems, it uses only the driver for the serial port itself.  So there will not be a driver loaded for your modem.

I've had a look through the packages in Synaptic and found some that may be of interest.
A package called "statserial" include a command (statserial) which can display the status of the serial port - it is intended to be used to troubleshoot connectivity problems (connectivity between the computer and the modem, that is)

You can also look at cutecom or minicom, either of which will allow you to enter AT-commands to control your modem directly.

Post back with your results so that we can help you further if necessary.

P.S. If your modem did have a driver loaded, you would be able to see it with the command "lsmod", and the commands lspci and lsusb tells you what is plugged in into the PCI-bus and USB-bus respectively.

---

### Post by jitsu on 2007-05-02
Hi Hartz:

Thanks for your reply.

I'm running Ubuntu 6.06 right now and my ext. serial modem Trendnet TFM-560x is operating perfectly.

I tried to upgrade to Ubuntu 6.10 and my modem (probably) is not being detected. I had to go back to Ubuntu 6.06 to access the internet.

I'm new to Ubuntu and inexperienced. I don't know why my modem would work in one distro and not in the other.


thanks,
Jitsu

---

### Post by hartz on 2007-05-02
Jitsu, I don't have an answer for you right away, I am sure some more experienced with Dial-up here would be able to point you in the right direction.

However here is a hint:
You can download Debian packages (*.deb files) using your working 6.06 Ubuntu installation, then later install them into the 6.10 Ubuntu instalation.

To do this, you can download the deb directly from the web, or use Synaptic and select the "Download packages only" option in the window you get when you click the "Apply" button.

Then copy the deb files from /var/spool/apt/cache to any directory, (use a memory stick or blank CD if necessary) to somewhere where you can access them from within Ubuntu 6.10.  

Then just install them from the command line using this command:

```
 dpkg -i packagefilename.deb
```

In the mean time can you maybe describe the modem problem in more detail (what do you see differently to what you expect from Ubuntu 6.06)?  How do you normally establish a connection to the internet (I'm assuming you use the modem to dial up to the internet).  And did you "upgrade" to 6.10 or did you do a new/fresh install?

Thanx.

---

### Post by jitsu on 2007-05-02
Hi Hartz:
I'm back on Ubuntu 6.06 now after another unsuccessful attempt to install 6.10.

I wrote down the modem setup that works in 6.06 and entered it in the 6.10 modem setup box. It didn't work. I have not touched the modem so I figure it may be somewhere in the operating system.

On the "General" tab: I checked enable this connection, entered the phone No. of my ISP, and my username and password.

Under the "Modem" tab: I entered my modem port as /dev/ttyS0, dial type Tones, volume low and under options I accepted the default settings 

After hitting okay, I never got the activate connection as I was supposed to get and it never worked. This same setup works in 6.06

It's working perfectly on U6.06.

I tried to download some of the items you mentioned in Synaptic and I was denied access.

I have another computer with windows xp and have a 6.10 Kubuntu dvd but it's for a 64-bit system. I don't know if I would have the same problem with a Kubuntu DVD for this computer.

From everything I've read a serial modem works with Ubuntu.


Thank you very much,
Charles
.

---

### Post by Bartender on 2007-05-03
The dialer was broken in Edgy and from what i've been told continues to be broken in Feisty.  Bummer, huh?  Take a look at this thread
[http://ubuntuforums.org/showthread.php?t=330467](http://ubuntuforums.org/showthread.php?t=330467)

The links given at the end of the thread might help you.  Or try another distro that isn't so unfriendly to the dial-up set, like PCLOS.

---

### Post by jitsu on 2007-05-03
Thank you for your reply--


I'm at the point that I don't think I can get my serial modem working. I have a Winmodem that I might have a better chance with, if I can figure out how to run the "Scan Modem" tool.

Dialup is probably here to stay. I live out in the country and broadband is not available now or in the forseeable future in my area. 

I don't know what PCLOS is. I may try another distro if all else fails.

I have another computer that I built and has a generic type winmodem and it worked with no problem  when I had Xandros installed. But Xandros is a commercial application along the lines of Microsoft products.

thanks,
Jitsu

---

### Post by Bartender on 2007-05-03
Oh, sorry -
PCLOS is PCLinuxOS

They've been in a state of disarray the last few weeks, trying to get the latest version finalized at the same time as their internet host went gunnysack on them.

[http://www.pclinuxos.com/](http://www.pclinuxos.com/)

It was offline when I checked a minute ago, but should be back.  PCLOS 2007 final is expected in a week or so.

If your Trendnet was working in 6.06, hang in there.  Serial hardware modems are still the most reliable way for us newbs.  It's unlikely that abandoning it for an internal modem is going to be an easier path.

---

### Post by _duncan_ on 2007-05-04
> The dialer was broken in Edgy and from what i've been told continues to be broken in Feisty. Bummer, huh?

Just to clarify: one of the dialer programs, specifically the one that comes with System > Administration > Network, doesn't work with edgy and feisty.

There are at least four (4) other dialer programs I know of: pppconfig, wvdial, gnome-ppp and kppp.

the first 2, pppconfig and wvdial, comes with the default install of ubuntu, regardless of version. So there are no additional packages to download. This makes them ideal for a fresh install without internet connection yet. They are both terminal-based. I'm sure pppconfig works, coz it's always the first dialer I configure every time I installed a new version of Ubuntu.

I'm also sure that gnome-ppp works, because it's my GUI frontend of choice. Since this app uses wvdial, we can also assume that wvdial also works.

I tried KPPP on edgy, and it also works, even if the desktop is gnome instead of KDE. It's a nice application, but it looks alien in the default gnome desktop, so I don't use it much.

To summarize: 4 out of 5 dialers I know of works in edgy. I'm sure 2 of them works in feisty. It's just a matter of looking up the pertinent section in the DialUpModemHowTo wiki and trying them out.


Other info:

A hardware modem doesn't have to be recognized to work with Ubuntu, as long as you know which port it is connected to. For example, when using pppconfig, there is a section there to auto-detect the modem. This always fail in my case. No problem. I know that my smartlink winmodem is on /dev/ttySL0, while my US Robotics hardware modem is on /dev/ttyS0 (COM1 in windows), so I just specify the port manually, and it works.

---

