---
title: "problems connecting to network (previously working)"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by wrathkeg on 2007-06-06
Dear all.

I got a wireless network running on 6.10.  Things were fine for a couple of weeks even connecting to the network on booting up.  Now it doesn't seem to want to connect on booting up, and getting it to connect later is not easy: endless restarts of the router and machine, running commands I don't really understand etc.  There seems to be no consistent pattern to what needs to be done to get it to work.  For instance, yesterday after doing these it worked, though it could be coincidence (I was frustrated and trying pretty much anything).
```
  sudo modprobe rt73
  iwconfig
  netstat -rn
  sudo /etc/init.d/networking restart
```
but today it doesn't: the last part of restarting the network says 
```
Listening on LPF/rausb0/00:19:5b:35:14:c5
Sending on   LPF/rausb0/00:19:5b:35:14:c5
Sending on   Socket/fallback
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.                            [ ok ]
```
Any ideas what might be causing the problems?  Running iwconfig even when not connected gives this as output, suggesting to me that it knows that the network is there:
```
lo        no wireless extensions.

eth0      no wireless extensions.

rausb0    RT73 WLAN  ESSID:"NETWORK_NAME"  
          Mode:Managed  Channel=6  Access Point: 00:19:5B:1D:97:14   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=59/100  Signal level:-62 dBm  Noise level:-99 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```
Thanks in advance for any suggestions.

WK

---

### Post by handaxe on 2007-06-06
I wonder if this is a similar issue?

[http://ubuntuforums.org/showpost.php?p=2731908&postcount=2]("http://http//ubuntuforums.org/showpost.php?p=2731908&postcount=2")

HA

---

### Post by wrathkeg on 2007-06-06
>  I wonder if this is a similar issue?

[http://ubuntuforums.org/showpost.php?p=2731908&postcount=2](http://ubuntuforums.org/showpost.php?p=2731908&postcount=2)


The links from that page seem to talk about installing drivers: I have already done this, which is how sometimes I can connect.  Or am I missing something?

To give some more background: I installed updates about a week or so ago, one of which installed the 2.6.17-11 kernel, which didn't let me connect at all.  So, I told grub to load 2.6.17-10 instead, which allowed me to connect to the network with no problems (I'll do without the updated kernel for now).  More recently I have had the problems I described in the first message.

So my issue seems to be: "sometimes it connects, sometimes it doesn't" (but always seems to find the network via iwconfig, see message and output above). Anyone know of a possible cause of that? Or preferably how to solve it...

To make things even more frustrating, I have just now booted up Ubuntu and it connected to the network with no problems.  But there is no guarantee that it will work next time, so I'd really like to get as close as I can to the bottom of this.

WK

---

### Post by handaxe on 2007-06-06
I posted those links because I was struck by the similarity of your problem to a known bug (AP visible, no connection made) - except that sometimes it works for you, which is decidedly weird.

What do you use to manage your connections? Network-Manager or  System ->  Administration ->  Network? I assume the last and that the AP passphrase etc are in /etc/network/interfaces.
[FONT=monospace]
"sudo modprobe rt73" - this loads the driver. If you are having to do this every time then something is wrong.

[/FONT]```
sudo lsmod | grep rt73
``` after bootup should show the driver loaded. If not already done, check this.

Long shot - Is your router acting up? Does it work flawlessly under Windoze?

---

### Post by wrathkeg on 2007-06-06
> I posted those links because I was struck by the similarity of your problem to a known bug (AP visible, no connection made) - except that sometimes it works for you, which is decidedly weird.

Yeah, it seems weird to me too.  I 'll have a closer look at the links though.  After the trouble I had installing the drivers in the first place, I panicked when I saw I might have to go through it all again ;)

> What do you use to manage your connections? Network-Manager or System -> Administration -> Network? I assume the last and that the AP passphrase etc are in /etc/network/interfaces.

I'll be honest, I've been trying to do all this through the command line, and had forgotten about the GUIs (which might be an error? though I seem to recall that the GUI network manager has caused problems for others) But yes, I have the passphrases in /etc/network/interfaces.  This is the end of that file

```
auto wlan0
iface wlan0 inet dhcp

# rt73 wireless network device using DHCP
iface rausb0 inet dhcp
pre-up ifconfig rausb0 up
wireless-essid NETWORD_ID
wireless-key  NETWORK_KEY # This line for hexidecimal keys
# wireless-key s:XXXXXXXXXXXXX  # This line for ASCII (string) keys
auto rausb0
```

> "sudo modprobe rt73" - this loads the driver. If you are having to do this every time then something is wrong.

I don't always have to do this (sometimes it connects on simply booting the machine), and sometimes it doesn't seem to help.  Because I have tried many different things, for all I know, it may not make a difference at all...

The output of
```
sudo lsmod | grep rt73
```
is
```
rt73                  223872  0 
usbcore               134912  7 usblp,usb_storage,rt73,libusual,ehci_hcd,uhci_hcd
```

I don't think it's a problem with the router.  On the few occasions that I have booted Windows, it has always found the network, so far as I remember.

Thanks for your help here: I'm stumped.

WK

---

### Post by handaxe on 2007-06-06
As far as I know, there were issues with the rt73 and N-M ....

Tried this to make sure you have the latest driver?  Likely you have:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver)]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29")

If not, why not try it? Compiling is not that hard and quite fun when mastered.

I also read of some folk who had connection issues with rt73 when they were some distance away from the router/AP but connected when close. Go figure...

HA

---

### Post by handaxe on 2007-06-06
You could try using the Windows drivers under ndiswrapper to see if they are more stable.

[http://ubuntuforums.org/showthread.php?t=324115](http://ubuntuforums.org/showthread.php?t=324115)

HA

---

### Post by wrathkeg on 2007-06-06
> **handaxe said:**
> As far as I know, there were issues with the rt73 and N-M ....

Tried this to make sure you have the latest driver?  Likely you have:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver)]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29")

If not, why not try it? Compiling is not that hard and quite fun when mastered.



That was indeed the how-to I had used the first time which worked, but has recently become unstable for some reason.  So, I just followed the instructions for different drivers from here, as you suggested:

[http://ubuntuforums.org/showthread.php?t=400236]("http://ubuntuforums.org/showthread.php?t=400236")

And, so far so good: at least, it has let me connect with no problems, and I have also rebooted and connected with no problems.  With a bit of luck, these drivers will give me the consistency I was lacking.  Thanks, Handaxe.

WK.

---

