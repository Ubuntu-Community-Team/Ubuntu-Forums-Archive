---
title: "Wireless Network Startup - NetworkManager problem?"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by etonki on 2007-06-26
Hi

I am using ndiswrapper with a Linksys WUSB54GS, connected to a router using WPA (TKIP) and configuring with Networkmanager Applet 0.6.4.

The problem I have is that when the machine starts up I don't get a connection straight away. I have to enter: 

sudo /etc/init.d/dbus restart 

and then reenter the default keyring to get things started. After doing this my network connects. 

I wondered if it was because I had roaming enabled and Networkmanager was trying all the available wireless networks detected before plumping for mine as it was the only one with a key entered. I originally wanted to configure it manually (again through NetworkManager) but the only encryption option is WEP.

If anyone has any ideas about how I can get things started quicker and avoid the dbus restart and reentry of the key every time I start the machine, I'd really appreciate it.

Thanks.

---

### Post by kevdog on 2007-06-26
I have the same problem.  This is a known bug, I use sudo /etc/init.d/networking restart rather than dbus. It has something to do with the way services are started at boot.  There is a work-around

 > Talking  Re: WPA2 / RSN, NDiswrapper, Static IP, Hidden ESSID, WUSB54G V4
This thread resulted in my getting a Broadcom 4318 wireless installed and running with WPA(1) under Edgy. I am basically using your example '*Sample configuration WPA1 & DHCP, ESSID broadcast enabled*' from your message #1. Thanks very much.

A slight improvement on this is that actually, to get wireless up at bootup, all you need is to do this as root:
Quote:
echo 'ifdown wlan0' >/etc/init.d/WlanDown
chmod +x /etc/init.d/WlanDown
ln -s ../init.d/WlanDown /etc/rcS.d/S40WlanDown
This runs S40WlanDown just before S40networking, so tidies up something in the wlan setup. Then S40networking runs ../init.d/networking which runs 'ifup -a' which successfully starts wlan0 and all other interfaces.

The source problem is a bug whereby at shutdown 'ifdown -a' does not seem to run (successfully) :not effectively doing an 'ifdown wlan0'.

Now I just gotta find again (for the record) where is the other forum message that told me where to get a tarball, that had the driver, and a script to do a lot of the work for me.



This was found from here:
[http://ubuntuforums.org/showthread.php?t=202834&page=4](http://ubuntuforums.org/showthread.php?t=202834&page=4)

---

### Post by etonki on 2007-06-26
Thanks for the quick reply.

I've tried the suggestion but when I try the first line I get a 'permission denied' error. I've tried sudo as well with no luck. 

Any suggestions? Could this be a symptom of another problem?

---

### Post by kevdog on 2007-06-26
Could you be more specific in what you tried, ie give me the syntax.  You are right that you need to preface every command with sudo

---

### Post by etonki on 2007-06-26
I typed:

sudo echo 'ifdown wlan0' > /etc/init.d/WlanDown

Have I missed some vital character? I'm fairly new to Linux but do have some grasp of the basics. So I might have made a silly mistake somewhere.

---

### Post by walkerk on 2007-06-26
How about removing Network Manager and use [Wicd]("http://wicd.sourceforge.net/") instead.. I was having similar issues with network-manager so i removed it and install Wicd which works perfectly with ndiswrapper and WPA1/2... also with the wicd tray daemon you don't have to enter your default key ring password to connect..

---

### Post by kevdog on 2007-06-26
Im not at my linux box right now but how about you do the above command in two steps.

#1.
cd /etc/init.d
#2
gksu gedit WlanDown
#3
Insert the following: ifdown wlan0
#4
Save the file and exit

I dont know why the single command doesnt work for you. Intuitively to me it should have, but at least the above is not too painful.

---

### Post by etonki on 2007-06-26
That's really helpful. I'll try that thanks. As soon as I can get Network Manager installed again!

I installed wicd (after uninstalling NM) and that showed all the networks around but wouldn't connect to the one I needed at all. No error. Just no connection. Everything else was unchanged from using Network manager.

Now I can't reinstall Network Manager. Synaptic Package Manager is complaining about dependencies. I can't install from the network (no connection) and only have the installation CD. I have applied updates since I installed Ubuntu so don't know if this is the problem. Sorry if that's a bit vague but I'm writing this from Windows.

Any ideas about how I can get Network Manager installed again so I can try the above would be really helpful.

Thanks again.

---

### Post by wieman01 on 2007-06-27
> **etonki said:**
> Thanks for the quick reply.

I've tried the suggestion but when I try the first line I get a 'permission denied' error. I've tried sudo as well with no luck. 

Any suggestions? Could this be a symptom of another problem?
Do this first:
> su root
Then type in your root password and continue from there.

---

