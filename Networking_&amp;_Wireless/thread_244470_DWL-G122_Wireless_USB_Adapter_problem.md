---
title: "DWL-G122 Wireless USB Adapter problem"
date: 2006-08-26
forum: Networking &amp; Wireless
---

### Post by Straumoy on 2006-08-26
Hey everyone,

I'm totally new to Ubuntu, so bare with me on this one okay? I need to get my D-link USB adapter to work and I've looked around on the net and dug up **Ubuntu Dapper Drake DWL-G122 Wireless USB Adapter Setup Guide**, which is very good.

The problem is that I get an error when I try to install the driver as described in the guide. This is how far I get:
[I]sudo ndiswrapper -i ~/drivers/prisma02.inf
Installing prisma02
couldn't copy /home/ole/drivers/prisma02.inf at /usr/sbin/ndiswrapper line 135.[/I]

Now looking after line 135 was enough to know that I was way over my head and it was time to ask around for help. Obviously something's wrong, but what and how can this be fixed. I stress out that I'm totally new to Ubuntu, so any solution must be presented in a very step-by-step manner in order for me to keep up (sorry 'bout that). 

If this doesn't work, I'm heading straight back to Windows (although I rather not), so please help me out. Thank you for reading=D>

---

### Post by meng on 2006-08-26
Okay, basic things first.
Where is your driver file located? According to your command there, you placed it in your home folder within a sub-directory called drivers. Is this correct? Because if not, that's a showstopper right there.

---

### Post by jdc8890 on 2006-08-26
I also have the D-Link DWL-G122. For me, I didn't even have to use ndiswrapper to install the driver.  Ubuntu automatically recognized it.  However, I had to configure it with terminal because whenever I used the network manager, the system crashed.  Hope this helps.

---

### Post by secdroid on 2006-08-26
Step 1 is to determine **which version** you have.  Unfortunately, there are a number of different versions, with different driver requirements.

See [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53")

This issue doesn't affect Windows users, as the proper driver is supplied with the product.  Unfortunately, they don't provide a proper Linux driver.

So, it can probably be made to work, but you have to know exactly which version you have.  How to tell?  See [http://support.dlink.com/products/revision.asp?productid=DWL-G122]("http://support.dlink.com/products/revision.asp?productid=DWL-G122")

Once you have that info, a bit of search engine work and questions on the forum should help.

---

### Post by Straumoy on 2006-08-27
@ Meng - Yes, the driver files, one *.inf and one *.sys file, is in the same folder called Drivers, which is located in the Home folder.

@ jdc8890 - I get the feeling that using the DWL shouldn't be too problematic, just a little tweaking around since there's no Linux driver around. For me it is the tweaking itself that is the problem, since I'm totally new to Linux.

@ secdroid - Argh! I can't believe I've managed to forget to put up such important info](*,) My version is a B1, so I suppose downloading the driver randomly from the net doesn't really cut it? So is it safe to assume that I should fall back to the install CD that came with it, or is there a special place where the correct driver can be downloaded?


EDIT:

Found what I was looking for, a Linux driver for the USB and although what to do with it is described, it doesn't make much sense to me :confused: 

[B]Card: D-Link DWL-G122 rev. B1 (USB)

    * Chipset: Ralink 2500
    * usbid: 2001:3c00
    * Label: P/N: EDWLG122..B1 FCC ID:KA2DWLG122B1
    * Native linux driver: Download from Ralink. Tested with Fedora Core 4, kernel 2.6.13-1.1526_FC4.
    * Driver: Latest WinXP driver downloaded from [41].
    * Other: Working great!
    * Other: Got WPA-PSK encryption working on Debian Linux with kernel 2.6.15.3. I used ndiswrapper-1.10 with original driver version 2.03 (shipped on CD with the Wireless USB Adapter) and wpa_supplicant-0.4.8 (got it from wpa_supplicant ) and it is working great. You only have to install the original driver in ndiswrapper, load the ndiswrapper module, use wpa_supplicant compiled with Driver-interface for ndiswrapper, then make a wpa_supplicant config (like in the examples shipped with the sourcecode of the wpa_supplicant) Edit it with your own key or passphrase and SSID, and then start wpa_supplicant -w -i wlan0 -c /path/to/your-created-config-file -D ndiswrapper -B thats all, enjoy it :-D . [/B]

So far I've downloaded the darn thing and looked around on the various README files in hopes of making any sense out this, but so far no good. This makes it all the more frustraing, because I'm so darn close, I can practically taste it. Just that last inch to go. :mrgreen:

---

### Post by meng on 2006-08-27
The directory Drivers is different from the directory drivers! Linux is case-sensitive. So is your post wrong, or do you need to go back and alter your command?

---

### Post by jdc8890 on 2006-08-27
I have the same exact revision and mine was automatically detected because linux already had the Ralink driver installed.  If you type iwconfig in terminal, does something listed as rausb0 appear? If so, your card is installed and just needs to be configured.

---

### Post by Straumoy on 2006-08-28
```
ole@Nemesis:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

rausb0    RT2500USB WLAN  ESSID:"Default"
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=11 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=0/70  Signal level:-120 dBm  Noise level:-209 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```


Using Wireless Assistant 0.5.5 I get this small window asking: You might have insufficent permissions for Wireless Assistant to function properly. Did you run it using 'sudo'?
Then there's a OK button, so I click it. I don't understand this message, since I am the admin on the computer, thus should have full and complete rights to do whatever I want (as long as I can type the password when the machine asks for it that is). I start the program from Applications | Internett | Wireless Assistant

Once inside, I get up both signals coming from the router (getting a full set of stars on both of them), but I'm unable to connect to either of them. It just says "Connection failed" at the bottom of the window, no real reason as of why let alone how it can be fixed. 

The signal called "Default" has a WEP on it, and yes I know the password and yes I'm sure I've typed it in correctly. It has the following settings:
Automatic (DHCP) **checked**
WEP Mode Shared Key **checked**
WEP Key ********** ASCII **checked**

The other signal called "linksys" doesn't have a WEP, though it to has DHCP checked.

Under Network Settings, Wireless connection is active, though under default gateway device it says eth1. Switching it over to rausb0 doesn't do much as far as I can tell. The USB remains as inactive as always and the moment I pull the cable, I'm offline since the USB isn't working.

---

### Post by Straumoy on 2006-08-30
I've done some looking around on the forum in hopes of finding someone with a similar problem, thus also a solution. I'm not sure if I'm moving along the proper direction, but I did stumble over this:
```
ole@Nemesis:~$ dmesg | grep rausb
[4294699.079000] rausb0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
[4294713.291000] rausb0: no IPv6 routers present
```

Again, since I'm new to linux, this doesn't tell me much. Well, there's a problem with the driver that needs to be addressed, but just HOW to do that.... I have no idea.

---

### Post by libertyforever on 2006-08-30
***Straumoy,*** you may want to consider [THIS]("http://www.ubuntuforums.org/showthread.php?t=190703&highlight=D-Link+G120") post.  Though it was for another model of D-Link, it worked for me.  I have a DWL-G122 ver., B1.  Read all the way through the thread down to Sam Lui's and my posts.  I was having problems with continual lock ups and had to endlessly tweek the dern thing.  I was able to use the driver that was on the CD.  Anyway, check it out and see what you think.  My internet is now working fantastic!  ;)

---

### Post by jISh on 2006-08-30
[http://www.ubuntuforums.org/showthread.php?t=209315&highlight=dwl-g122](http://www.ubuntuforums.org/showthread.php?t=209315&highlight=dwl-g122)
My guide on setting up the DWL-G122!
Although your filename will be different, as the B revision uses a different chipset than the A. However, other than the filename, the steps should follow exactly the same.

---

### Post by itsstillraining on 2007-08-11
Hi There All,

I was reading through your posts.
I have like some of you swithched to using ubuntu. I have the same DLINK usb adapter. DWL-G122 H/WARE VER C1 F/WARE V:3

Ubuntu seems to have recognised it and I can see all the available networks around me but I cant connect. I input my pasky and nothing. No error, no message nothing!

I have tried manual configuration a number of times but no joy.
I have looked at dozens of posts and sites offering asistance but each one is different.

I have downloaded the ndiswrapper as a tar file. I am trying to install it on ubuntu via a cdrom. I can get as far as selecting the files to extract but what do I do next? I cant create a folder, cant seem to do anything.

This linux is not for the faint hearted. There is a reason Mr. Gates conquered the world its called plug and play.

Any assistance for a distressed newbie?:confused:

---

