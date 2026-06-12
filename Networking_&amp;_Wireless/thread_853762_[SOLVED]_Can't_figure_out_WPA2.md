---
title: "[SOLVED] Can't figure out WPA2"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by itsjareds on 2008-07-08
I really am having a lot of trouble trying to get my Netgear WPN111 adapter to work. It's turned into a 3 day project (so far). 

I have no idea why it STILL won't work; I have everything installed correctly. I installed ndiswrapper, added my connection via System > Admin. > Network, entered in my WPA2 password, and my adapter is now blinking meaning it works.

Yet the internet connection is still out, and when I right click the two monitors icon at the top, and click Wireless Connections (or something like that), it doesn't show my connection.

My router allowed the MAC address for my adapter, and that isn't the problem because I am on the same computer using the same adapter on Windows XP. 

I think the problem might be with the WPA2 password, but I really don't have a clue since I'm a complete noob at Linux and connecting to the internet.

---

### Post by itsjareds on 2008-07-08
No help? :(

---

### Post by jimrz on 2008-07-08
check out [[COLOR="Sienna"]**_this "How-To"_**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=414023&highlight=WPN111") for instructions on how to get your adapter working.

---

### Post by itsjareds on 2008-07-08
I've done all of that, and it still doesnt work. I'll try it again because when i first started, i was using Run Applications instead of Terminal. :lolflag:

---

### Post by st33med on 2008-07-08
Try this if you don't have v2 of your USB wireless: [http://ubuntuforums.org/showthread.php?t=844856](http://ubuntuforums.org/showthread.php?t=844856)

---

### Post by pytheas22 on 2008-07-08
I tried helping someone else with the same kind of adapter a couple weeks ago who was experiencing exactly what you describe: all indicators point to the adapter being working under ndiswrapper, but it won't connect to WPA networks.  That thread is still ongoing (the guy said he was going on vacation), so unfortunately I don't have an easy answer for you.

But I will try to help if you can do a few things and tell me the results.

First, if possible, please disable encryption on your wireless router and try to connect, and report your results.

Second, try to connect to your network a few times while it is using WPA.  Then please post the output of these commands

```
dmesg
ndiswrapper -l
iwconfig
```

---

### Post by pytheas22 on 2008-07-08
> check out this "How-To" for instructions on how to get your adapter working.

> I've done all of that, and it still doesnt work. I'll try it again because when i first started, i was using Run Applications instead of Terminal.


Yeah, the other guy that I was helping followed the same tutorial and ended up in exactly the same position as the original poster here, so I suspect that the problem comes down to WPA (probably a wpa supplicant issue), which that tutorial doesn't mention.  That's why I want to know if it's possible to connect to an unsecured network with no problems.

---

### Post by itsjareds on 2008-07-08
> **pytheas22 said:**
> First, if possible, please disable encryption on your wireless router and try to connect, and report your results.

I wish i could do that, but the router is connected to my dad's computer, and his computer is password-protected.

> Second, try to connect to your network a few times while it is using WPA.  Then please post the output of these commands

```
dmesg
ndiswrapper -l
iwconfig
```

I'll try that.

---

### Post by itsjareds on 2008-07-08
Ok. This is what I got:

> 
dmesg : incredibly long list, not sure what i was looking for

ndiswrapper -l : netwpn11 - driver installed, device present

iwconfig : wlan0 - IEEE 802.11g, mode: managed, freq: 2.412 GHz, Access Point: Not associated, bit rate: 108 mb/s. The rest of the values were 0.


It takes a while to transfer from Ubuntu to WinXP, so I try to keep switching back and forth to a minimum. The adapter works fine in WinXP.

---

### Post by pytheas22 on 2008-07-09
It would be really good to see all of dmesg.  If your computer is dual-boot, you could save the dmesg output into a text file and move it to the Windows partition (you can open the Windows partition under the Places menu).  Otherwise, just save the file to a USB stick and bring it to a computer with Internet access so that you can post here.  iwconfig and ndiswrapper -l don't say anything interesting, but dmesg will hopefully contain a clue about why the association is failing.

---

### Post by itsjareds on 2008-07-09
Oh, didn't know that I could save a file on Linux and read it on windows!

Is it possible to save something like a .tar.gz extension in windows, then open it in Linux?

And I'll do what you said about the dmesg thing.

---

### Post by itsjareds on 2008-07-09
Uploaded to mediafire.

[dmesg.txt]("http://www.mediafire.com/?9mn932hijpm")

---

### Post by itsjareds on 2008-07-09
Could this help ?

[HOWTO: Wireless Security]("http://ubuntuforums.org/showthread.php?t=202834")

---

### Post by Bentai on 2008-07-09
Something odd I came across.. I wasn't able to get my laptop running 8.04 to connect using WPA2 until I had my router start rebroadcasting it's SSID. Shot in the dark but if your router isn't broadcasting, try making it broadcast the SSID and then connect to it.

---

### Post by pytheas22 on 2008-07-09
> Is it possible to save something like a .tar.gz extension in windows, then open it in Linux?

Yes, sure.  Linux can read files from NTFS partitions with no problem now.  (You can also open up your Linux partition in Windows if you install drivers for the ext3 filesystem (provided you use ext3)).

Anyway thanks for the dmesg; I'll take a look and get back.  I think what it's going to come down to is trying to connect manually from the command line.

---

### Post by itsjareds on 2008-07-09
> **Bentai said:**
> Something odd I came across.. I wasn't able to get my laptop running 8.04 to connect using WPA2 until I had my router start rebroadcasting it's SSID. Shot in the dark but if your router isn't broadcasting, try making it broadcast the SSID and then connect to it.

The router I use already broadcasts it, but it's not my router, it's my dad's. Would it rebroadcast when his computer restarts?


> **pytheas22 said:**
> Yes, sure.  Linux can read files from NTFS partitions with no problem now.  (You can also open up your Linux partition in Windows if you install drivers for the ext3 filesystem (provided you use ext3)).

I tried to open my windows partition from linux; it's at Places > System Networks , right? When I opened it, I found Windows Network, but when I clicked it, it didn't bring up anything. Wouldn't allow me to write anything in there either. Do I need to install something?

---

### Post by pytheas22 on 2008-07-09
Alright, dmesg doesn't say anything about the association attempt--did you try connecting a couple of times before running dmesg?  dmesg does say that your card should be capable of connecting to WPA2 networks, and it doesn't mention any problems with ndiswrapper.

Either way, I think the best thing to do now is try to connect manually from the command-line.  That will at least rule out problems with Network Manager.  This [guide]("http://ubuntuforums.org/showthread.php?t=202834") that you already linked to is probably best; [this one]("http://ubuntuforums.org/showthread.php?t=571188") is also useful for reference (but note that the approaches that they take are a little different, do don't be confused if you find something in one guide that's not mentioned in the other).  I was going to copy out steps for you to follow here, but mostly I'd just be copying from that first tutorial, so I think you should just try following it and see if it gets you connected.  I think the steps are straight-forward enough, but if you need clarifications at any point, please ask.  Make sure that you understand everything before applying it, so that you do it all correctly.
> 
I tried to open my windows partition from linux; it's at Places > System Networks , right? When I opened it, I found Windows Network, but when I clicked it, it didn't bring up anything. Wouldn't allow me to write anything in there either. Do I need to install something?

The Windows Network thing is for connecting to other Windows computers over the local network (and you would need to install samba first to do that), not on your own computer.  To open the Windows partition on your computer's hard drive, click on Places and you should see an entry that says something like "20 GB Media" (replace 20 GB with the size of your Windows partition).  Click on that and it will open a folder containing your Windows file system at the level of C:/  Sometimes you need to click again for it to open.  If you're using Ubuntu 8.04, access to Windows partitions should "just work" out-of-the-box.

---

### Post by itsjareds on 2008-07-09
Ok, I did what was on the first tutorial, but no connection happened. I even restarted my computer..

When I opened System > Admin > Networks, clicked my connection, then properties, it said I was using WPA(1) encryption, and my password was the hex-key, not the ascii one.

Also, my SSID has a space in it, so how should I put it into the command line? I just did Charlotte_Martin instead of Charlotte Martin.

About browsing the windows partition, I finally found it under /host. Didn't see anything about 20GB.

---

### Post by itsjareds on 2008-07-09
Also, I noticed that System > Admin. > Networks changes /etc/network/interfaces

So if I change any of it, then Networks changes it back to what it was (if I save the changes in properties)

---

### Post by pytheas22 on 2008-07-09
> I noticed that System > Admin. > Networks changes /etc/network/interfaces

Yes, it does this; Networks is basically just a GUI for configuring the /etc/network/interfaces file.
> 
Also, my SSID has a space in it, so how should I put it into the command line? I just did Charlotte_Martin instead of Charlotte Martin.

Put the essid in quotes when you enter it into a file.  Don't use an underscore because the computer will interpret that as a completely different essid.  If you used an underscore when you followed that tutorial, please try doing it again with the essid inside " ".

If it still doesn't work, please post your /etc/network/interfaces file here.

Also, it would still be good if you could test the connection on a network using a different kind of encryption.  If there's anyway for you to bring the computer somewhere else (e.g. a coffee shop) to test there, or to get your father to temporarily disable encryption or switch it to something else (he could try WPA1, which is just as secure as WPA2 as long as you use a long, non-dictionary-word password), it would be good.  I want to make sure that WPA2 is really the issue here, and not a broader problem with your connection.

---

### Post by itsjareds on 2008-07-09
Should a connection have started once I saved interfaces?

This is /etc/network/interfaces:
> 
auto lo
iface lo inet loopback
auto wlan0
iface wlan0 inet dhcp
address 65.5.199.134
gateway 65.5.199.134
dns-nameservers 208.67.222.222
netmask 65.5.199.134
wpa-driver wext
wpa-ssid Charlotte Martin
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk 92a1020c340339e5303bc6a63782b9fab1423fe6c33d018626ec97e35dc6a619


---

### Post by itsjareds on 2008-07-09
I installed a driver to let me access the linux partition in windows, but I don't see any familiar folders. Where in it is the normal part?

---

### Post by pytheas22 on 2008-07-10
> I installed a driver to let me access the linux partition in windows, but I don't see any familiar folders. Where in it is the normal part?

It should mount your Linux partition as a drive in Windows, like E: for example.  Open up that drive and navigate to /home/YOUR-USER-NAME.  It's inside that folder that all of the familiar stuff would be.  Everything outside of /home is system directories, which you should be careful not to modify from within Windows so as to avoid breaking something on Linux--and likewise, it's probably not a good idea to go playing in the system32 directory of Windows mounted on Linux, either.

---

### Post by itsjareds on 2008-07-10
I don't see a /home folder. I only see:

/DOS
/MFGSTAT
/minint
/preboot
/RECOVERY
/swwork
/TPTOOLS


Also searched within each directory and didn't see ../home

---

### Post by pytheas22 on 2008-07-11
> I don't see a /home folder. I only see:

That's strange; that's definitely not a Linux partition that you mounted.  It looks like maybe a special recovery partition installed by your computer's manufacturer, or maybe a boot partition.  Are you sure that it's formatted in ext3?  The Linux partition at the highest level would contain directories like /home, /usr, /bin, /opt, /media and so on...in other words, all the directories you see when you type:
```

ls /
```

in Linux.

---

### Post by itsjareds on 2008-07-11
That's not a problem anymore.. figured it out. Some program I used just mounted /media for some reason. Used a different program and it's fine. 

Do you see anything wrong with interfaces?

---

### Post by itsjareds on 2008-07-11
typed this command:
> sudo /etc/init.d/networking restart

which produced:
> 
jared@jared-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.wlan0.pid with pid 5916
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:14:6c:59:31:ed
Sending on   LPF/wlan0/00:14:6c:59:31:ed
Sending on   Socket/fallback
ioctl[SIOCSIWPMKSA]: Invalid argument
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:14:6c:59:31:ed
Sending on   LPF/wlan0/00:14:6c:59:31:ed
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


---

### Post by itsjareds on 2008-07-11
Here is my terminal:
[Click here]("http://pastebin.ca/1069500")

---

### Post by youthforlinux on 2008-07-11
If you are on you dad's network, when you go into Windows, you can access the router from there since your network connection is working, go to Run type in cmd press enter then type in ipconfig then look for your wireless card, then look for the gateway address, type that into a web browser with http:// before it.  That will take you to the router.  Then disable the wireless security, the router's default username and password is either admin password or just admin as the password without a username.

---

### Post by itsjareds on 2008-07-11
Newest terminal:
[Click here]("http://pastebin.ca/1069573")

---

### Post by itsjareds on 2008-07-11
Terminal with Wicd:
[wicdterminal]("http://pastebin.ca/1069703")

---

### Post by itsjareds on 2008-07-12
Terminal after fixing the typo in /etc/wpa_supplicant.conf:
[http://pastebin.ca/1070166](http://pastebin.ca/1070166)

---

### Post by pytheas22 on 2008-07-12
Try running with just these commands:
```

sudo rm -rf /var/run/wpa_supplicant/wlan0
sudo ifconfig wlan0 down
sudo wpa_supplicant -w -D wext -i wlan0 -c/etc/wpa_supplicant.conf -dd 
sudo ifconfig wlan0 up
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0
```

---

### Post by itsjareds on 2008-07-12
Terminal with new commands:
[http://pastebin.ca/1070158](http://pastebin.ca/1070158)

---

### Post by pytheas22 on 2008-07-12
Try changing /etc/wpa_supplicant.conf to this:
```

network={
        ssid="Charlotte Martin"
        psk="ASCII PSK Password in Quotes"
        key_mgmt=WPA-PSK
        proto=WPA2
        pairwise=CCMP
}
```

Then please run these commands:

```
sudo rm -rf /var/run/wpa_supplicant/wlan0
sudo ifconfig wlan0 down
sudo wpa_supplicant -w -c /etc/wpa_supplicant.conf -i wlan0 -D wext -d -t -K 
sudo ifconfig wlan0 up
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

```
If that doesn't work, please save the output from the terminal, and then try changing /etc/wpa_supplicant.conf to this:
```

network={
       ssid="Charlotte Martin"
       scan_ssid=1
       proto=WPA RSN WPA2
       key_mgmt=WPA-PSK
       auth_alg=OPEN
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk="YOUR PASSWORD HERE, IN QUOTES"
}
```

Then try running the commands a second time.  Please post the output from both tries.

---

### Post by itsjareds on 2008-07-12
Terminal from using the first wpa_settings.conf edit:
[http://pastebin.ca/1070190](http://pastebin.ca/1070190)

Terminal from the second:
[http://pastebin.ca/1070192](http://pastebin.ca/1070192)

---

### Post by itsjareds on 2008-07-12
Take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=263136"). It shows that in wpa_supplicant.conf, psk is the hex key, not the ASCII key. Was it supposed to be like that all along?

Also, I think my driver had to be installed using ndiswrapper. Would wext work as well?

---

### Post by WinterMadness on 2008-07-12
> **itsjareds said:**
> I really am having a lot of trouble trying to get my Netgear WPN111 adapter to work. It's turned into a 3 day project (so far). 

I have no idea why it STILL won't work; I have everything installed correctly. I installed ndiswrapper, added my connection via System > Admin. > Network, entered in my WPA2 password, and my adapter is now blinking meaning it works.

Yet the internet connection is still out, and when I right click the two monitors icon at the top, and click Wireless Connections (or something like that), it doesn't show my connection.

My router allowed the MAC address for my adapter, and that isn't the problem because I am on the same computer using the same adapter on Windows XP. 

I think the problem might be with the WPA2 password, but I really don't have a clue since I'm a complete noob at Linux and connecting to the internet.

did you make sure you went to system>admin>windows wireless drivers and actually install the .inf file for your wireless driver?

---

### Post by itsjareds on 2008-07-12
> **WinterMadness said:**
> did you make sure you went to system>admin>windows wireless drivers and actually install the .inf file for your wireless driver?

yes

---

### Post by pytheas22 on 2008-07-12
> Also, I think my driver had to be installed using ndiswrapper. Would wext work as well?

wext is the name of the driver that ndiswrapper uses to negotiate WPA keys--you're still using ndiswrapper; wext just does the WPA part.

> Take a look at this thread. It shows that in wpa_supplicant.conf, psk is the hex key, not the ASCII key. Was it supposed to be like that all along?


I think it's alright to just put your plaintext password in /etc/wpa_supplicant.conf (you can do either).  But it couldn't hurt to try getting the password as described in that thread, too.  As they say, type:
```

wpa_passphrase "Charlotte Martin" your_plaintext_password
```

and put that into /etc/wpa_supplicant on the "psk=" line (you shouldn't need to put the passphrase in quotes if you generate it using the command above) to see if it makes a difference.

That aside, I'm very encouraged by the output from the last try.  You got really close--this is the money line:
```

1215884096.835627: State: ASSOCIATING -> ASSOCIATED
```

This means that you were three-quarters there...but for some reason the router wouldn't authenticate to complete the connection.

The problem may indeed be that you need to enter the key in non-plaintext form, so give that a try as described above, and please post your logs (it also wouldn't hurt to see your /etc/wpa_supplicant.conf file at this point just to be sure we're all on the same page with that).  In the meantime, I will do some research and see if I can figure out if something else is wrong.  I don't have time now but will hopefully get a chance to come back on by tomorrow afternoon.

I know this must be frustrating to you to keep trying and still not solve the problem yet--especially since you're having to reboot to try each new step--but that "ASSOCIATING -> ASSOCIATED" message is really, really good, so I think we're very close to finally solving it.  Hopefully tomorrow will be the day.

By the way, I researched the wpn111 + WPA2 extensively on Google and not a single person seems to have ever figured this out (but there are several with the same issue as you), but no one tried as hard as you are.  So when we do solve it, we will be making a major step forward for lots of other people too, which is nice :)

---

### Post by itsjareds on 2008-07-13
> **pytheas22 said:**
> wext is the name of the driver that ndiswrapper uses to negotiate WPA keys--you're still using ndiswrapper; wext just does the WPA part.



I think it's alright to just put your plaintext password in /etc/wpa_supplicant.conf (you can do either).  But it couldn't hurt to try getting the password as described in that thread, too.  As they say, type:
```

wpa_passphrase "Charlotte Martin" your_plaintext_password
```

and put that into /etc/wpa_supplicant on the "psk=" line (you shouldn't need to put the passphrase in quotes if you generate it using the command above) to see if it makes a difference.

That aside, I'm very encouraged by the output from the last try.  You got really close--this is the money line:
```

1215884096.835627: State: ASSOCIATING -> ASSOCIATED
```

This means that you were three-quarters there...but for some reason the router wouldn't authenticate to complete the connection.

The problem may indeed be that you need to enter the key in non-plaintext form, so give that a try as described above, and please post your logs (it also wouldn't hurt to see your /etc/wpa_supplicant.conf file at this point just to be sure we're all on the same page with that).  In the meantime, I will do some research and see if I can figure out if something else is wrong.  I don't have time now but will hopefully get a chance to come back on by tomorrow afternoon.

I know this must be frustrating to you to keep trying and still not solve the problem yet--especially since you're having to reboot to try each new step--but that "ASSOCIATING -> ASSOCIATED" message is really, really good, so I think we're very close to finally solving it.  Hopefully tomorrow will be the day.

By the way, I researched the wpn111 + WPA2 extensively on Google and not a single person seems to have ever figured this out (but there are several with the same issue as you), but no one tried as hard as you are.  So when we do solve it, we will be making a major step forward for lots of other people too, which is nice :)

Awesome. That's really encouraging. You'll be known forever as that guy who figured it out. :) Hehe

I hope I will get it with this next attempt.

---

### Post by itsjareds on 2008-07-13
No!!

Ubuntu's not loading!

It loads the boot screen then after, it just gets dark then its black :mad:

The second time I restarted, it went to this weird prompt thing about 5 seconds after the boot, but I don't know what it said.

:mad::mad: This is annoying! Just as I was going to get the internet up!

Well.. worst case scenario.. I'll have to re-install Ubuntu. I don't have anything important or really anything set up on it yet. I'll just have to install ndiswrapper and wicd again :(

Very disappointing..

---

### Post by itsjareds on 2008-07-13
Ok, now I'm worried.

Got ubuntu to load after I came here and vented, then I restarted because I accidentally unplugged my adapter, and no more connections would be found after I reconnected. Well the same thing happened to me when I restarted. Nothing would come up. 

I switched to windows just to the login screen, then Shut Down. Right before windows shut down, it gave me a blue screen. Scared the **** out of me.. 

It said that Newly installed hardware may not be installed properly. If this is your first time seeing this message, restart your system. If it isn't.. (blah blah..)

Should I re-install Ubuntu? I don't want to destroy my PC.

---

### Post by pytheas22 on 2008-07-13
I don't know what's going on with Ubuntu.  Booting into a different kernel may help--at the boot menu you should have options for at least two different kernels, as well as the memory test and recovery modes.  If a different kernel doesn't help, then I guess you should reinstall Ubuntu.

Does Windows work alright when the wireless adapter is not plugged in?  I suspect that that's the problem, although I don't know why exactly the device would send Windows to the blue screen.  The only thing that makes sense is hardware failure on the part of the wireless card.  Does it still work fine in Windows?

Let me know how things go and hopefully we can get back to the wpa_supplicant stuff.

---

### Post by itsjareds on 2008-07-13
> **pytheas22 said:**
> I don't know what's going on with Ubuntu.  Booting into a different kernel may help--at the boot menu you should have options for at least two different kernels, as well as the memory test and recovery modes.  If a different kernel doesn't help, then I guess you should reinstall Ubuntu.

Does Windows work alright when the wireless adapter is not plugged in?  I suspect that that's the problem, although I don't know why exactly the device would send Windows to the blue screen.  The only thing that makes sense is hardware failure on the part of the wireless card.  Does it still work fine in Windows?

Let me know how things go and hopefully we can get back to the wpa_supplicant stuff.

The wireless card still works fine on windows.. I'll try that thing with the kernel.

---

### Post by itsjareds on 2008-07-13
The recovery kernel didn't fix anything, so I'm re-installing :-|

---

### Post by itsjareds on 2008-07-13
Reinstalled, but when I restarted to complete the installation, I got the blue screen again. 

This is what was written (same screen):

> If this is your first time seeing this screen, reboot your system. If there is something in the STOP section, please disable that driver.

STOP 0x0000008E (0xC000001D, 0X00000063, 0xA91F7C64, 0x00000000)

Beginning dump of physical memory
Physical memory dump complete

What is that?


Also, when I tried to load Ubuntu, I got a weird screen (installer screen?) right when the boot screen started up. It didn't finish the loading or anything, it just went straight to a screen with this:
> Busybox v1.1.3 (debian smoethingsomething) 
Type 'help' for commands. 
It was some kind of command prompt, but I don't know what to do. Waited to see if it was an autorun or something, but it wasn't.

Do you think I could system restore to about two days ago and fix everything?

---

### Post by pytheas22 on 2008-07-13
> If this is your first time seeing this screen, reboot your system. If there is something in the STOP section, please disable that driver.

STOP 0x0000008E (0xC000001D, 0X00000063, 0xA91F7C64, 0x00000000)

Beginning dump of physical memory
Physical memory dump complete 

I'm not sure what this means exactly, but because it mentions disabling a driver, it sounds like either driver problems with Windows, or hardware malfunctioning.  Was your wireless card plugged in when that message appeared?  Or did you add any other hardware or install/upgrade drivers in the last couple of days?  Disabling your wireless card in the Windows hardware-setup utility (you can reenable it once Windows boots) may also help, although I'm not sure.

As for Ubuntu, something really strange is going on there.  Were you able to boot the live CD without a problem?  Or did you use wubi?
> 
Do you think I could system restore to about two days ago and fix everything? 

That might help to fix Windows.  I don't think it would fix Ubuntu, but I'm not sure.  If you installed using wubi, it might.  I don't have much experience with system restore in Windows, unfortunately.

---

### Post by itsjareds on 2008-07-13
> **pytheas22 said:**
> I'm not sure what this means exactly, but because it mentions disabling a driver, it sounds like either driver problems with Windows, or hardware malfunctioning.  Was your wireless card plugged in when that message appeared?  Or did you add any other hardware or install/upgrade drivers in the last couple of days?  Disabling your wireless card in the Windows hardware-setup utility (you can reenable it once Windows boots) may also help, although I'm not sure.

As for Ubuntu, something really strange is going on there.  Were you able to boot the live CD without a problem?  Or did you use wubi?


That might help to fix Windows.  I don't think it would fix Ubuntu, but I'm not sure.  If you installed using wubi, it might.  I don't have much experience with system restore in Windows, unfortunately.

No, I didn't add any hardware at all. The only thing is when I switch from Ubuntu to windows after trying to make a connection through Ubuntu, Windows tells me that I have new hardware. I just have to replug in my adapter and it's fine. 

How would I re-enable my wireless driver? I don't think I've ever installed new hardware..

As far as installing Ubuntu, I'm using wubi. I used wubi last time and it worked fine.

---

### Post by itsjareds on 2008-07-13
Sorry I took so long, the restore took like 2 hours.

Re-installing AIM since restore deleted it.

---

### Post by itsjareds on 2008-07-15
Ah.. reinstalled wubi again and it is all fixed :)

Very relieving. 

Now I have to reinstall everything on Ubuntu :-|

---

### Post by itsjareds on 2008-07-15
:confused:

When I installed ndiswrapper and ndisgtk, it says my hardware and device are both present. A guide on setting up wpn111 says to use the commands 
> sudo ndiswrapper -i netwpn111.inf
(which I already did)

and 
> sudo ndiswrapper load_fw_ar5523 /etc/ndiswrapper/netwpn111/ar5523.bin
which worked perfectly the first time I setup ndiswrapper, but now it just brings me the list of commands instead of doing load_fw_ar5523

---

### Post by pytheas22 on 2008-07-15
I'm glad to hear that the wubi issue is cleared up.  I guess it was disk corruption in Windows then?
```

When I installed ndiswrapper and ndisgtk, it says my hardware and device are both present. A guide on setting up wpn111 says to use the commands
Quote:
sudo ndiswrapper -i netwpn111.inf
(which I already did)

and
Quote:
sudo ndiswrapper load_fw_ar5523 /etc/ndiswrapper/netwpn111/ar5523.bin
which worked perfectly the first time I setup ndiswrapper, but now it just brings me the list of commands instead of doing load_fw_ar5523
```

Which guide did you use?  I'm not familiar with any load_fw.... commands and have never known them to be necessary, but maybe they are.  If ndiswrapper -l says device present, though, then you should be all set and a reboot should make the wireless work (or in your case, at least make it see networks).  Is that not the case?

I'm going to be travelling for the next couple of weeks but will respond as I'm able.  I would still really like to get back to the wpa_supplicant stuff and figure this out for good.

---

### Post by itsjareds on 2008-07-15
> **pytheas22 said:**
> I'm glad to hear that the wubi issue is cleared up.  I guess it was disk corruption in Windows then?

I'm not sure, but as long as it's working fine and no blue screens :). Also, sometimes Ubuntu would freeze during bootup and randomly while I'm using it. Seems like that worked itself out, too. Maybe I just did something stupid when I first installed it.

> **pytheas22 said:**
> Which guide did you use?  I'm not familiar with any load_fw.... commands and have never known them to be necessary, but maybe they are.  If ndiswrapper -l says device present, though, then you should be all set and a reboot should make the wireless work (or in your case, at least make it see networks).  Is that not the case?

I used [(WORKS!) Complete How-To for WPN111]("http://ubuntuforums.org/showthread.php?t=414023&highlight=WPN111"). The second step is > sudo ndiswrapper load_fw_ar5523 and it says after I do that, my device should be blinking.

---

### Post by pytheas22 on 2008-07-15
After the command:
```

sudo ndiswrapper -i /home/<username>/Desktop/netwpn111.inf
```

you should be able to reboot and have the stick blinking.  Does it?

---

### Post by itsjareds on 2008-07-15
> **pytheas22 said:**
> After the command:
```

sudo ndiswrapper -i /home/<username>/Desktop/netwpn111.inf
```

you should be able to reboot and have the stick blinking.  Does it?

No. I installed using that command and using ndisgtk, and still didn't seem to work.

---

### Post by itsjareds on 2008-07-16
I think [this]("http://ubuntuforums.org/showthread.php?t=9454") may be what we need to figure out the WPA part of connecting.

---

### Post by bodhi.zazen on 2008-07-16
This is a long thread ...

I suggest you start with the basics, access your router and turn off security (wpa2) for a minute.

Lets see if we can connect without security.

On my system I have not been too happy with the current state of affairs with wireless, it seems network manager likes to overwrite config files without asking permission ~ bad, bad gui tool :lolflag:

At any rate ...

Open network manager -> Left click on the icon in the upper left panel, select manual configuration.

Do you see your wireless card listed ?

OK, assuming so, unlock the interface (click unlock and enter password).

Select your wireless card and click properties -> select your network -> click "OK"

Now the tricky part ... reboot

Repeat steps

You should now have access.

Now to add wpa2, re-enable your router (and confirm password).

In Network manager select WPA2 -> enter password -> click OK

Open a terminal

sudo dhclient ....

should work.

---

### Post by itsjareds on 2008-07-16
I also know why my driver isn't working.

For some reason, my first installation of Ubuntu thought my system was 32bit, but now it's 64 bit. Had to download all the amd64 versions of things instead of i386. 

When I run > dmesg | grep ndis it gives me "Windows wireless driver is not 64bit."

But since my first installation ran my driver perfectly fine, doesn't that prove that my computer is capable of running it? How would I set it up?

Edit: I'm sure that I downloaded the normal version of Ubuntu, not the 64bit. It's still in my downloads folder as i386.

---

### Post by bodhi.zazen on 2008-07-16
It looks like there are a number of posts re: your card. The posts are of variable quality some say it works out of the box, others to use ndiswrapper.

I would try ndiswrapper from the repositories, then from source if needed.

[]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/getting-netgear-wireless-usb-dongle-wpn111-atheros-chipset-to-work-on-ubuntu-6.06-515914/?")[http://www.linuxquestions.org/questions/linux-wireless-networking-41/getting-netgear-wireless-usb-dongle-wpn111-atheros-chipset-to-work-on-ubuntu-6.06-515914/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/getting-netgear-wireless-usb-dongle-wpn111-atheros-chipset-to-work-on-ubuntu-6.06-515914/)

[http://ubuntuforums.org/showthread.php?p=5363332#post5363332](http://ubuntuforums.org/showthread.php?p=5363332#post5363332)

[http://ph.ubuntuforums.com/showthread.php?&t=652910](http://ph.ubuntuforums.com/showthread.php?&t=652910)

---

### Post by itsjareds on 2008-07-16
We're trying to figure how to get it to work with WPA2 encryption. I'm sure it would work without encryption, nobody has figured it out with WPA2 encryption using my adapter. I've seen my wireless connection (through wicd) and tried to connect, then my computer started having problems and I had to reinstall Ubuntu. 

Entering in my password just like it says doesn't work, that's what we're trying to figure out.

But now my computer thinks its a 64 bit system..:-k

---

### Post by bodhi.zazen on 2008-07-16
Your card is reported to work with encryption (WPA2).

First thing though is to get a working driver.

You can check your version of Ubuntu with :

```
uname -a
```

Then if your driver is working with 

```
ndiswrapper -l
```

Then test connection without encryption.

Unless you go through this problem with a systematic approach, you will spin your wheels.

---

### Post by itsjareds on 2008-07-16
Yesss i know 

I've had to reinstall ubuntu because my computer started giving random problems.. and now, using the same installation file that I installed my first version of Ubuntu, it thinks my computer is a 64bit system (which it is, but my driver is a 32bit program). 

Ubuntu used to think my computer was 32bit (for whatever reason) and it installed all 32 bit programs, which worked fine. My driver worked fine under that installation. 

There is no download for a 64bit driver. My computer should be able to run 64bit and 32bit programs, but Ubuntu isn't letting me.

---

### Post by pytheas22 on 2008-07-17
> But since my first installation ran my driver perfectly fine, doesn't that prove that my computer is capable of running it? How would I set it up?

Although you can run most 32-bit programs on a 64-bit kernel without a problem, ndiswrapper needs 64-bit Windows drivers to work on a 64-bit kernel.  It won't work if a 32-bit Windows driver is installed.  So that's the problem.  Can you find a 64-bit Windows driver anywhere?  If not, the only option is to install 32-bit Ubuntu.

I'll take a look at that [other thread]("http://ubuntuforums.org/showthread.php?t=9454").

---

### Post by itsjareds on 2008-07-17
> **pytheas22 said:**
> Can you find a 64-bit Windows driver anywhere?

Nope :/. Netgear deleted it. 

The problem is, I installed Ubuntu using the same installer.. I don't understand how some setting changed.

*sigh* Not looking forward to resetting all of my options on Ubuntu again, but looks like it's the only choice.

---

### Post by pytheas22 on 2008-07-18
I'm not sure where, but wubi must give you the option to choose a 32-bit or 64-bit installation.  I would just make sure to look around all the options before clicking install.

Unfortunately, it seems like Netgear is totally neglecting support for 64-bit operating systems, which is bad not only for you both for Windows users as well.

---

### Post by itsjareds on 2008-07-20
It is strange, the file in my downloads folder that I use to extract wubi is called ubuntu-8.04.1-desktop-i386.iso

It should be i386, right?

I checked around on the wubi installer dialog, and there are only these things:

Installation drive
Installation size
Ubuntu distro
Language
Username
Password

---

### Post by pytheas22 on 2008-07-20
Should have checked here earlier; this is from the wubi [site]("http://wubi-installer.org/faq.php"):

> 
Why is the AMD64 version of Ubuntu getting downloaded and installed?

You probably have a 64 bit machine, the 64AMD installation is appropriate for all 64 bit architectures whether AMD or Intel.

Can I force Wubi to download and install a 32 bit version of Ubuntu?

Yes, either pre-download the appropriate 32 bit ISO manually and place it in the same folder as Wubi.exe or start Wubi with the "--32bit" argument.

So if your processor architecture is 64-bit, apparently wubi tries to install the 64-bit version without asking you first.  Why it installed 32-bit for you the first time and later 64-bit, I have no idea.  But your options now I guess are to download the 32-bit ISO from ubuntu.com and tell wubi to install using that, or run it with the --32bit option...I guess you need to run from the command line in Windows for that.

When you get the 32-bit version installed and the wireless back up, please let us know.  I'm still travelling but am eager to figure out what's up with the wpn111 and Linux.

---

### Post by itsjareds on 2008-07-22
I downloaded it from ubuntu.com, and I am sure I downloaded i386. 

Oh well, no point in doing nothing. I'll re-download it and see if it makes a difference.

---

### Post by itsjareds on 2008-07-22
Ok, I downloaded it a second time fresh start from [www.ubuntu.com](www.ubuntu.com), under i386 desktop edition.

It still installed amd64 :mad:

> **pytheas22 said:**
> But your options now I guess are to download the 32-bit ISO from ubuntu.com and tell wubi to install using that, or run it with the --32bit option...I guess you need to run from the command line in Windows for that.

What would I type in the prompt?

---

### Post by pytheas22 on 2008-07-23
> What would I type in the prompt?

You'd have to cd to the location of the wubi installer.  If it's at C:\, then you'd type:
```

cd c:\
Wubi-8.04.1-rev506.exe --32bit
```

The name of the Wubi installer may be a little different depending on which version you download, so you may need to change it to reflect that (keep in mind that tab autocompletion works in Windows too, so you can just type "wubi" and press tab and it should autocomplete the rest of the name).  Above is the file on the wubi site available right now.

---

### Post by itsjareds on 2008-07-24
Ok, I'm installing now.

---

### Post by itsjareds on 2008-07-24
Ahhh.. much better :)

Was able to install i386 packages now, that means it worked.

Now I have everything re-installed, I tried connecting again.

The first time I did it, I got to
> sudo wpa_supplicant -w -c /etc/wpa_supplicant.conf -i wlan0 -D wext -d -t -K 

It looked like it was connecting, but got stuck at 
> ASSOCIATED -> 4-WAY HANDSHAKE

Tried it again a few minutes later, and it got stuck at 
> Scanning for addresses..
Failed

---

### Post by itsjareds on 2008-07-24
By the way, the > ASSOCIATED -> 4-WAY HANDSHAKE was after the > ASSOCIATING -> ASSOCIATED (I think, didn't get a chance to copy it down. Terminal got cleared or something..)

---

### Post by pytheas22 on 2008-07-25
I'm glad you've finally got i386 working again, and thanks for going through all that and sticking with this thread. 

When you get a chance, could you try connecting again please and post all of the output?  It would be helpful to see the "Scanning for addresses..Failed" bit in context.

Also, please post your /etc/wpa_supplicant.conf file.

---

### Post by itsjareds on 2008-07-25
I was more worried about you giving up.. but you seem to be motivated

---

### Post by pytheas22 on 2008-07-26
Don't worry; I won't give up until I'm really 100% out of suggestions, in which case I'd try to find people who could help you more than me.  As I said earlier, I think it's really important to figure this wpn111+WPA stuff out, because it seems to affect a lot of people.

Also I'm back from vacation now so I should be able to respond more quickly.  When you get a chance to try the connecting again and can post the output here (along with the contents of /etc/wpa_supplicant.conf), please do so.

---

### Post by itsjareds on 2008-07-26
/etc/wpa_supplicant.conf:> network={
       ssid="Charlotte Martin"
       scan_ssid=1
       proto=WPA RSN WPA2
       key_mgmt=WPA-PSK
       auth_alg=OPEN
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=(my password in quotes)
}


[Here is my terminal]("http://pastebin.ca/1083711")

---

### Post by pytheas22 on 2008-07-27
Thanks for all that information.  I'm not sure exactly what's going on, but it almost looks like it's connecting for a split second, but then it thinks that the MAC address of your access point (aka router) changes to 00:00:00:00:00:00.  Try changing wpa_supplicant.conf to this:

```
network={
ssid="Charlotte Martin"
**bssid="00:1c:f0:eb:1e:4d"**
scan_ssid=1
proto=WPA RSN WPA2
key_mgmt=WPA-PSK
auth_alg=OPEN
pairwise=CCMP TKIP
group=CCMP TKIP
psk=(my password in quotes)
} 
```

and see if it makes a difference.

Also, please try running with these different commands to see if any of them gives you more luck (please save the output from each attempt):

```
sudo wpa_supplicant -w -c /etc/wpa_supplicant.conf -i wlan0 -D wext -dd -t -K
sudo wpa_supplicant -w -c /etc/wpa_supplicant.conf -i wlan0 -D ndiswrapper -dd -t -K
sudo wpa_supplicant -w -c /etc/wpa_supplicant.conf -i wlan0 -D ndis -dd -t -K
sudo wpa_supplicant -w -c /etc/wpa_supplicant.conf -i wlan0 -D hostap -dd -t -K
```

(run also "sudo rm -rf /var/run/wpa_supplicant/wlan0" before each attempt...I don't think the "ifconfig wlan0 down" is necessary and may be causing problems)



Finally, could you please post the output of:
```

lshw -C Network
```

because it would be useful to know exactly which release of the Windows driver you're using with this.

---

### Post by kevdog on 2008-07-27
Is this parameter valid for wpa2 networks?

key_mgmt=WPA-PSK

---

### Post by imdano on 2008-07-27
> **kevdog said:**
> Is this parameter valid for wpa2 networks?

key_mgmt=WPA-PSKYes it is, kevdog.  The other options are WPA-NONE (used for static WEP) or WPA-EAP (used for WPA Enterprise)

> **pytheas22 said:**
> Thanks for all that information.  I'm not sure exactly what's going on, but it almost looks like it's connecting for a split second, but then it thinks that the MAC address of your access point (aka router) changes to 00:00:00:00:00:00.
Sometimes wpa_supplicant will '0' out your MAC Address after it fails to authenticate with a given AP.

itsjareds, Are there any non-alphanumeric characters in your passphrase?  Certain ones ('$', '\', a few others I can't remember) can cause issues.

Most likely though, is that you're just not going to be able to connect.  Especially if no one before you has been able to get WPA2 working.  This > Associating->Associated
Associated->4-Way Handshake
4WAY_HANDSHAKE -> DISCONNECTEDis what is typically seen when wpa_supplicant is able to find (and therefore associate with) your network, but can't authenticate because either a) the psk is incorrect, or b) the encryption type being used isn't supported.

---

### Post by itsjareds on 2008-07-28
My psk has all letters, no other characters.


> **pytheas22 said:**
> Thanks for all that information.  I'm not sure exactly what's going on, but it almost looks like it's connecting for a split second, but then it thinks that the MAC address of your access point (aka router) changes to 00:00:00:00:00:00.  Try changing wpa_supplicant.conf to this:

```
network={
ssid="Charlotte Martin"
**bssid="00:1c:f0:eb:1e:4d"**
scan_ssid=1
proto=WPA RSN WPA2
key_mgmt=WPA-PSK
auth_alg=OPEN
pairwise=CCMP TKIP
group=CCMP TKIP
psk=(my password in quotes)
} 
```

and see if it makes a difference.

Also, please try running with these different commands to see if any of them gives you more luck (please save the output from each attempt):

```
sudo wpa_supplicant -w -c /etc/wpa_supplicant.conf -i wlan0 -D wext -dd -t -K
sudo wpa_supplicant -w -c /etc/wpa_supplicant.conf -i wlan0 -D ndiswrapper -dd -t -K
sudo wpa_supplicant -w -c /etc/wpa_supplicant.conf -i wlan0 -D ndis -dd -t -K
sudo wpa_supplicant -w -c /etc/wpa_supplicant.conf -i wlan0 -D hostap -dd -t -K
```

(run also "sudo rm -rf /var/run/wpa_supplicant/wlan0" before each attempt...I don't think the "ifconfig wlan0 down" is necessary and may be causing problems)



Finally, could you please post the output of:
```

lshw -C Network
```

because it would be useful to know exactly which release of the Windows driver you're using with this.

Will do.

---

### Post by itsjareds on 2008-07-28
YES!!

I have internet running on Ubuntu \\:D/\\:D/

I don't know what happened, except that I copied down your updated version of /etc/wpa_supplicant.conf and updated my file, then tried to connect. It said that the BSSID was invalid, so I removed that line. After that, I tried to connect using wicd gui, just to test. Entered everything in, clicked connect, and it connected :D

yay.

---

### Post by itsjareds on 2008-07-28
Thanks a million Pytheas (and other contributors)

Have some popcorn :popcorn:

---

### Post by itsjareds on 2008-07-28
The most stunning thing about the internet on Ubuntu: I'm getting speeds about 2.75x my speed on Windows XP.

I usually download at 160kb/s, but I downloaded at a high 509kb/s

---

### Post by imdano on 2008-07-28
Good to hear you go it working.  Just so you know, the wpa_supplicant.conf that wicd uses to connect is different from the one you've been editing.  The one used by wicd is in /opt/wicd/encryption/configurations/<your AP's MAC address>.

---

### Post by pytheas22 on 2008-07-28
Wow...so you finally got this to work?  If so, I'm pretty sure you're the first one ever to get the wpn111 working with WPA1/2.  For the benefit of others, could you please paste the wpa_supplicant.conf that wicd uses (should be at /opt/wicd/encryption/configurations/00:1c:f0:eb:1e:4d) here?  It would also be good to know which ndiswrapper version you're using and which Windows driver you have, so please also post:
```

ndiswrapper -v
lshw -C Network
```

and if possible, provide a link to the Windows driver that you used.  A screenshot of what exactly you entered into wicd to get it to work would also not hurt.

It would be nice if we could write up a WPA how-to for this card.

---

### Post by itsjareds on 2008-07-28
> **pytheas22 said:**
> A screenshot of what exactly you entered into wicd to get it to work would also not hurt.

It would be nice if we could write up a WPA how-to for this card.

It is really strange; once I removed the BSSID line from /etc/wpa_supplicant.conf, I've been able to connect even using the terminal.

Here is my /opt/wicd/encryption/configurations/00:1c:f0:eb:1e:4d file:
> ap_scan=1

network={
       ssid="Charlotte Martin"
       scan_ssid=0
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=92a1020c340339e5303bc6a63782b9fab1423fe6c33d018626ec97e35dc6a619
}

Ndiswrapper version: 1.52

Windows driver: netwpn11 (version 2.0) There is an older version (1.1) of the driver for the WPN111, but it uses two drivers (netwpn111.inf and athsys.inf)

[Here is a download page for all the versions of NETWPN111 drivers.]("http://kbserver.netgear.com/products/wpn111.asp")

[IMG]http://i38.tinypic.com/1564yyw.png[/IMG]

---

### Post by itsjareds on 2008-07-28
I would also note that I have only gotten it to work after I did 
> sudo rm -rf /var/run/wpa_supplicant/wlan0.

I'm not sure if it would work before, but I do that just to be safe.

---

### Post by pytheas22 on 2008-07-28
Thanks for all that information.  Also I should have asked before, but just to be sure--you installed ndiswrapper from the repositories (Synaptic), right...you didn't have to compile from source?

There's [another thread]("http://ubuntuforums.org/showthread.php?t=837751&page=5") with someone else with a wpn111 and a WPA2 network, so I'm going to see if he can get connected doing the same thing you did.

---

### Post by itsjareds on 2008-07-28
I installed ndiswrapper by downloading the .deb package file on WinXP, then opened it up.

Another important thing to note is each time you restart after getting connected, you have to unplug the adapter. I don't know why, but when I do that, the networks show up again after I reboot. Otherwise there are no connections.

---

### Post by itsjareds on 2008-07-29
It is somewhat buggy though -- connection randomly stops and I have to restart to get it to work again. Also doesn't work if my computer puts on a screensaver or hibernates.

I think I have to stop some process every time it stops working, because when I restart, my device is still blinking.

---

### Post by pytheas22 on 2008-07-29
> It is somewhat buggy though -- connection randomly stops and I have to restart to get it to work again. Also doesn't work if my computer puts on a screensaver or hibernates.

I think I have to stop some process every time it stops working, because when I restart, my device is still blinking.

The next time it crashes, run:
```

dmesg | tail
```

and post the output here.  That should give information about why it's crashing and hopefully a way to fix it.

---

### Post by itsjareds on 2008-07-30
Happened a few times -- same result:

> jared@jared-desktop:~$ dmesg | tail
[   66.850197] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   70.217947] [drm] Initialized drm 1.1.0 20060810
[   70.233852] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   70.233869] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   70.233999] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   74.502811] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   74.537675] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   74.667009] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   76.960594] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   87.612623] wlan0: no IPv6 routers present

Also noticed that when I restart/shut down, some type of terminal comes up saying> closing other daemon processes
starting wicd daemon

could this be because I have it set on "reconnect on disconnection"?

---

### Post by pytheas22 on 2008-07-30
hmmm, it's not saying too much about what caused the disconnection.  Maybe it would help to see all of dmesg; in other words, post the output of:
```

dmesg
```

(without the | tail) the next time the connection drops.  It will be really long but hopefully somewhere in there will be an indication as to what's going on.

If seeing all of dmesg doesn't help, I guess you could recompile ndiswrapper with debugging enabled, but that would be a lot of work, would possibly break your wireless again and might not end up solving anything.  I'm thinking that it would be easier to write a script to work around the problem--maybe bringing the device down and up again periodically, or reinserting the ndiswrapper module every so often, would help.

How often do the crashes occur?  Do they seem completely arbitrary or always at about the same time or time interval?  Does it only crash when you're at the computer browsing the Internet, or also when the machine is idle?

> 
Also noticed that when I restart/shut down, some type of terminal comes up saying
Quote:
closing other daemon processes
starting wicd daemon
could this be because I have it set on "reconnect on disconnection"? 

I'm not sure what that means.  You could try changing the "reconnect on disconnection" option (after all, it's not really reconnecting on its own, is it?) to see if it makes any difference.

---

### Post by imdano on 2008-07-30
That message is nothing to worry about.  I don't think the first one is wicd related, that looks like a generic Linux message saying its shutting down stuff in etc/init.d/  I'm not sure why the wicd daemon is starting instead of stopping though...it shouldn't affect anything, so don't worry about it.

---

### Post by itsjareds on 2008-07-30
Alright.

And when I went to wicd to turn off the reconnect on connection loss, I noticed I can turn on "debug mode". Could we use this?

---

### Post by kwtm2 on 2008-07-30
Just finished reading through all 10 pages of this thread.  I don't have any new info to contribute, but I wanted to commend everyone on their perseverance in getting this to work.  This includes itsjared, who is willing to jump through all sorts of hoops, especially on a system that is not all under your control (sounds like the router and the main computer are under the parent's jurisdiction).  I remember trying to get things done on my own computer without having the cooperation of my dad to get that the important passwords, etc.  Also to pytheas22 and all the others on the forum who helped.  This is what sets this Ubuntu forum apart from other "RTFM"-type forums.

I especially want to emphasize the importance of (and express my appreciation for) posting all the results of your program outputs and explaining what didn't work and (most importantly) what worked.  I like to tinker on older hardware that most other people worked on 2-3 years ago, and I'll often find answers in Google search results in forums that people posted long ago.  It was a relief to know that other people had encountered the same problems as me, and figured things out.  On the other hand, it was really really frustrating to see something like "Can anyone help me with [insert description of problem, which was EXACTLY the same problem I was having]", and then later on, "It's okay, I figured it out, everything's working so I don't need any more help," and then they DIDN'T EXPLAIN WHAT THEY DID TO GET THINGS WORKING!!! :P  aaauugghh!

So, thanks!

---

### Post by imdano on 2008-07-31
> **itsjareds said:**
> Alright.

And when I went to wicd to turn off the reconnect on connection loss, I noticed I can turn on "debug mode". Could we use this?It just increases the verbosity of the logging wicd does.  In 1.4.2 it's very spammy and usually isn't all that useful in solving problems.  It's a little bit better in 1.5.0, but I don't think it would help much in this case.

---

### Post by pytheas22 on 2008-07-31
> And when I went to wicd to turn off the reconnect on connection loss, I noticed I can turn on "debug mode". Could we use this?

I think that the best thing to do is to see all of dmesg after it crashes next time.

But I admit that I don't know too much about how wicd works; imdano may be of more help if this is a wicd problem.  I didn't even know wicd kept logs; where are they?

You could also try uninstalling wicd and installing Network Manager again; this one command should do both:
```

sudo apt-get install network-manager-gnome
```

If it's wicd's fault that the connection drops, then maybe NM would be better.  On the other hand, maybe you won't be able to connect with NM at all (although it would be useful to know if wicd actually mattered to your success at eventually connecting, or whether NM can do it as well).  Either way, you could try...but keep in mind that you do run the risk of breaking things again, so I can understand if you just want to stick with what you know works, more or less, right now.

And either way, please post the total output of "dmesg" after the next crash; hopefully that will provide a clue.

> 
Just finished reading through all 10 pages of this thread. I don't have any new info to contribute, but I wanted to commend everyone on their perseverance in getting this to work.

Thanks; I think these forums are a lot better than most other ones as well.  The vast majority of posts are more coherent, well-intentioned and useful than what you find in a lot of forums, even in other Linux ones.  And users here are, as you say, usually more attuned to the concept that their threads are not just about their individual problems, but can be helpful to lots of other people, too, who may not read them till years later.  I don't know why it is this way--I rarely see moderators censoring anything to enforce these standards--but it's nice.

---

### Post by imdano on 2008-07-31
The wicd log is kept in /opt/wicd/data/wicd.log in 1.4.2 and /var/log/wicd/wicd.log in 1.5.0.

Typically random disconnection is not the fault of network management app but rather just driver/hardware issues.  If you have problems like constantly disconnecting/reconnecting, that's probably a symptom of a NM/wicd problem (usually caused by a weird driver quirk).

Also, you might try using modprobe to unload and reload your wireless driver next time you get disconnected and can't connect again.  For many people who run into that kind of issue that gets them connected again without having to restart.

---

### Post by unutbu on 2008-07-31
itsjareds, what version of ndiswrapper are you using? You can find out with```

ndiswrapper -v
```

The changelog for ndiswrapper says Version 1.51 fixed a bug which maybe your problem(??):

```
Version 1.51 has been released. Short summary of changes since 1.50:

    * Fixed an smp issue that may cause ndiswrapper to stop transmitting packets after a while (noticed with Marvell Pre-N USB driver)
```

I don't know if this will solve your problem, but if you are interested, kevdog wrote a guide on how to compile the latest version of ndiswrapper here: [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

---

### Post by kevdog on 2008-07-31
You can either install the latest version with that guide or just use the svn version (which is the cutting edge).  I always recommend going with either the most recent release or svn version since things are fixed with ndiswrapper over time and as new kernels are released.

---

### Post by itsjareds on 2008-08-01
My ndiswrapper version is 1.52.

And what do you mean by svn?


Also noticed that when I try to run ndisgtk, it doesn't respond and I have to close it.

---

### Post by pytheas22 on 2008-08-01
svn means the latest, unstable version of ndiswrapper.  To get the svn source code, you would have to first install subversion, a program to connect to svn repositories and check out code:
```

sudo apt-get install subversion
```

then check out the ndiswrapper svn code with:
```

svn co https://ndiswrapper.svn.sourceforge.net/svnroot/ndiswrapper/trunk/ndiswrapper 
```

and then compile it.

svn code is never guaranteed to be stable, however.  You may want to first try compiling ndiswrapper version 1.53, the latest stable release, using these commands:
```

sudo apt-get install build-essential
wget http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz?modtime=1211931005&big_mirror=0
tar -xzvf ndiswrapper*
cd ndiswrapper*
make
sudo make install
```

*maybe* the bug is fixed in 1.53.

> 
Also noticed that when I try to run ndisgtk, it doesn't respond and I have to close it. 

When did this start happening?  If you open ndisgtk from the command-line, does any information get dumped there about what's wrong?

---

### Post by itsjareds on 2008-08-01
> When did this start happening? If you open ndisgtk from the command-line, does any information get dumped there about what's wrong?

It happens after the internet crashes. I tried opening from the terminal, and nothing came back.


I got this in the terminal after installing ndiswrapper 1.53:
> NOTE: Windows driver configuration file format has changed since 1.5. You must re-install Windows drivers if they were installed before.


Maybe that is the fix?

---

### Post by pytheas22 on 2008-08-01
> I got this in the terminal after installing ndiswrapper 1.53:
Quote:
NOTE: Windows driver configuration file format has changed since 1.5. You must re-install Windows drivers if they were installed before.
Maybe that is the fix?

Interesting; I hadn't heard of that before.  It could have something to do with it.  Did you try removing your Windows drivers:
```

sudo ndiswrapper -r DRIVER-NAME
```

and reinstalling with:
```

sudo ndiswrapper -i /path/to/.inf/file
```

(I don't know what the name of your Windows driver file is, but "ndiswrapper -l" should tell you)

You could also try this:
```

sudo apt-get remove --purge ndisgtk
sudo apt-get install ndisgtk
```

to see if it makes a difference--it will reinstall ndisgtk.  But I don't know how well it will work, because ndisgtk depends on the version of ndiswrapper that's in the repositories (1.52), and apt-get installing ndisgtk might cause the system to reinstall the older version of ndiswrapper (you can check with "ndiswrapper -v").  I don't know how to install ndisgtk on its own; I recall trying once and not having success.  I think it's just a Python script but I could never figure out where to download it by itself.

Also, just to confirm (as another poster mentioned): does running these commands make the Internet work again after it crashes (without unplugging the wireless card):

```
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
```

---

### Post by itsjareds on 2008-08-02
I already re-installed my driver, seems to work. I'll try those commands when the internet crashes. If they don't work, I'll try re-installing ndisgtk.

---

### Post by kevdog on 2008-08-02
Is there a reason you need ndisgtk?  I really find this program pointless for many reasons, since personally I find it easier to use the command line since it gives you a lot more options and is far easier in debugging problems.  ndiswrapper is one of those things that once you get things working, you tend to forget about it.

---

### Post by itsjareds on 2008-08-02
no real reason to use it, but i just installed it anyway. I checked to see if ndiswrapper was working first, then ndisgtk.

And my connection didn't restart when I tried your commands, pytheas. The first two didn't respond with anything for a few minutes, so I closed them. Third one gave me "wlan0 is not a device" or something.

---

### Post by pytheas22 on 2008-08-03
> And my connection didn't restart when I tried your commands, pytheas. The first two didn't respond with anything for a few minutes, so I closed them. Third one gave me "wlan0 is not a device" or something.

When you typed the "rmmod ndiswrapper" command, do you mean that it was hanging for a while with no response and didn't return you to a command-line?  If so then it sounds like there are some instability issues going on with the driver.  Do you get any output from:
```

sudo rmmod --verbose ndiswrapper
sudo modprobe --verbose ndiswrapper
```

And by the way, how often do the crashes occur (once a day, once an hour, every ten minutes...)?

---

### Post by itsjareds on 2008-08-03
It varies. Sometimes I only have the network running for 10 minutes then it crashes, sometimes I can have it up for a few hours.

---

### Post by pytheas22 on 2008-08-03
> It varies. Sometimes I only have the network running for 10 minutes then it crashes, sometimes I can have it up for a few hours.

Does it happen only when you're browsing web pages or also when the machine is idle?

---

### Post by itsjareds on 2008-08-05
Uhh usually while browsing, but I think it happened one time when nothing was happening.

---

### Post by pytheas22 on 2008-08-06
Do you notice certain web pages causing it to break?  I ask because I have a Netgear WG111v2 device (I think it's the next model up from the WPN111, although it has a different chipset, prism) that used to give me trouble in Mandriva that sounds very similar to what the WPN111 is doing to you.  I was using ndiswrapper to drive the card, as at that time there was no native driver (there is now and it works well).

It would usually be fine if I left the machine idle, but when I was in the middle of browsing, the card would crash, and the only way to make the Internet work again was to either restart the computer or unplug and replug the USB wireless card.  I eventually noticed that the crashes always occurred when I tried to visit certain websites, like en.wikipedia.org.

That was a couple of years ago and I never found a solution (I also never tried it under distributions other than Mandriva); that was when I was very new to Linux and just ended up buying a new wireless card instead of trying to troubleshoot the issue.

But I'm thinking that if we can pinpoint some of the sites that reliably trigger your card to crash (if in fact it does always happen with certain sites), we might be able to figure out what they have in common and link it to whichever bug is at the root of the issue.

---

### Post by itsjareds on 2008-08-07
I don't think so, it seems pretty random. One time I was just watching the download to wait for it to finish when it disconnected. Hadn't done anything.

---

### Post by itsjareds on 2008-08-10
Hmm, not sure what happened, but I think it is fixed. Might have been one of the system updates I installed. Now I can unplug and replug my adapter and it starts blinking again, all I have to do is reconnect via wicd.

Now just to get it to connect automatically :P

Edit: Nevermind.. seems that it reconnects fine if I unplug/replug it when it didn't disconnect for no reason. Looks more like it isn't scanning or something..

---

### Post by itsjareds on 2008-08-12
I was tweaking a lot of things, and none of them worked. All it did was mess up Ubuntu.. things like sound, usplash, and firefox all weren't working. I couldn't figure it out, so I re-installed it (relucantly).

Now I can't get past the associating -> disconnected. :oops:

---

### Post by pytheas22 on 2008-08-14
Sorry to hear it's broken again.  But at least now we have an opportunity to figure out exactly what it takes to make it work.

First, have you tried using this for your wpa_supplicant.conf file:
```

ap_scan=1

network={
ssid="Charlotte Martin"
scan_ssid=0
proto=WPA RSN
key_mgmt=WPA-PSK
pairwise=CCMP TKIP
group=CCMP TKIP
psk=92a1020c340339e5303bc6a63782b9fab1423fe6c33d01 8626ec97e35dc6a619
} 
```

Because that seemed to be the one that had it working with wicd before.

---

### Post by unutbu on 2008-08-14
pytheas22, you are really outstanding. Thank you for being here and contributing to the Ubuntu community.

---

### Post by itsjareds on 2008-08-14
I agree 8-)

@Pytheas: I'll do that soon, though I think I already changed it to that. Lemme look.

---

### Post by pytheas22 on 2008-08-14
> pytheas22, you are really outstanding. Thank you for being here and contributing to the Ubuntu community.

Thanks.  You obviously are a major asset to all of us as well--I've seen you solving problems in a lot of other threads.
> 
@Pytheas: I'll do that soon, though I think I already changed it to that. Lemme look.

I figured you had already tried that, but check again I guess and let us know.  If it still doesn't work, could you post the output when you try to connect manually?

---

### Post by itsjareds on 2008-08-19
Sorry for the late response.

I set /etc/wpa_supplicant.conf to exactly what you had, but took out the space from the passphrase.

There's no connections showing up still. This happened the first time, I just can't remember how I fixed it.

---

### Post by pytheas22 on 2008-08-20
> There's no connections showing up still. This happened the first time, I just can't remember how I fixed it.

You mean you can't see any networks when you scan, even with:
```

iwlist scan
```

or just that you can't connect to them?  If you're having trouble connecting, could you post the output you get when you try running wpa_supplicant manually, please?  If you can't see networks at all, what is:
```

iwlist scan
dmesg | grep -e ndis -e wlan
```

---

### Post by itsjareds on 2008-08-23
Oh good, I can see all the networks, including mine. Here's what is said about mine:

```

Cell 01 - Address: 00:1C:F0:EB:1E:40
          ESSID:"Charlotte Martin"
          Protocol:IEEE 002.11g
          Mode:Managed
          Frequency:2.442 GHz (Channel 7)
          Quality:50/100 Signal level:-64 dBm  Noise Level:-96 dBm
          Encryption key:on
          Bit Rates:1 Mb/s; 2 MB/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s;
          9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
          Extra:bcn_int=100
          Estra:atim=0
          IE: WPA Version 1
              Group Cipher : TKIP
              Pairwise Ciphers (2) : TKIP CCMP
              Authentication Suites (1) : PSK
          IE: IEEE 802.11i/WPA2 Version 1
              Group Cipher : TKIP
              Pairwise Ciphers (2) : TKIP CCMP
              Authentication Suites (1) : PSK

```

Again, sorry for late replies but I'll be around more often now.

---

### Post by itsjareds on 2008-08-23
This is pretty ironic. I can view and connect to my network on the network manager, but I can't see it at all using wicd.

In the terminal when I run sudo wpa_supplicant, it tells me that it associated, authenticated, and is connected. Yet when I try to visit a site, it gives me the "Looking up ____.com.." in the status.

It might be worth noting that I didn't use any verbose options on that try, but the first time I did, and it told me that it was connected also.

---

### Post by itsjareds on 2008-08-23
Ugh. Wrote the whole tutorial then somehow Firefox navigated back before I submitted. So this is the second time I am writing this. I'm sorry if I seem to rush a little bit, please feel free to ask questions if I am unclear.

I got the internet to work on my computer and my other one. Here is how I did it, step-by-step from a fresh installation:


**1.** Install ndiswrapper-common, ndiswrapper-utils, ndisgtk, and wicd. I provided attachments to the versions that I used -- these have worked. Other versions may work but haven't been tested.

See the bottom of my post for attachments.

I provided only i386 versions of everything because NETGEAR hasn't released a x64 bit version of their driver. Only 32 bit Ubuntu will work.

Before installing wicd, you must uninstall networkmanager. Go to System -> Administration -> Synaptic Package Manager. Search for "networkmanager".

Mark for complete removal. This will uninstall another package (I can't remember the name). Click OK. After this, you can install Wicd fine.


**2.** Install your driver in ndisgtk. Go to System -> Administration -> Windows Wireless Drivers. Click "Install Driver" and locate your .inf file in your Windows partition, if you are dual-booting. For me, it was located in /host/Program Files/NETGEAR/WPN111/Driver. If there are two .inf files, install both of them. Otherwise, just install the single one.

If you are not dual-booting, find another computer with internet to download the software from [the NETGEAR site]("http://kbserver.netgear.com/products/wpn111.asp"), if you do not have the software already. 

Select the 2.0 version of the driver if possible, this will allow you to re-plug your adapter if it ever gets unplugged on accident. The 1.1 version will not allow you to do this. The 2.0 version is also better because NETGEAR condensed their driver to one .inf file, rather than two. This just speeds up the process.


**3.** With any luck, you should see your adapter light blinking once you installed the driver. We're almost connected. Open Wicd (Applications -> Internet -> Wicd) and click "Preferences". Change "Wireless interface" to "wlan0". You can also optionally set your DNS servers -- mine are for OpenDNS. The server numbers are 208.67.222.222 and 208.67.220.220.

Click OK, then click "Refresh". Your adapter should scan and display the list of networks nearby. Open your network tree, then open the "Advanced settings" tree. Look down to "Use Encryption". Check it, change the password type to WPA 1/2, and type in your ASCII password in the field. Once you have this done, you can click connect!

Here is what it says in my status when connecting (my ESSID is Charlotte Martin):
> 
Charlotte Martin: Obtaining IP Address


If you see this, then you will connect. When you are officially connected, it will say "Connected to Charlotte Martin". Open up Firefox and go to Google, it will come up!

---

### Post by imdano on 2008-08-23
If you're using wicd, changes you make to /etc/wpa_supplicant.conf won't make any difference, since wicd makes its own wpa_supplicant config file when it tries to connect.

---

### Post by itsjareds on 2008-08-24
Ok, I wasn't sure so I just did that anyway.

---

### Post by itsjareds on 2008-08-24
> **pytheas22 said:**
> I'm thinking that it would be easier to write a script to work around the problem--maybe bringing the device down and up again periodically, or reinserting the ndiswrapper module every so often, would help.

My connection does work again if I re-install the driver in ndiswrapper. Wrote a little script to do this but I don't know how to reconnect with wicd via the terminal.

---

### Post by pytheas22 on 2008-08-24
> My connection does work again if I re-install the driver in ndiswrapper. Wrote a little script to do this but I don't know how to reconnect with wicd via the terminal.

I searched and couldn't seem to find any way to pass command-line options to wicd.  But if you start wicd (write in your script 'python /opt/wicd/tray.py' I think) won't it just automatically connect, as long as you've checked the box in wicd that says "automatically connect to this network" for Charlotte Martin?

Your other option is to add these lines to your script:
```

wpa_supplicant [arguments...]
dhclient wlan0
```

I know you said that you can't view web pages even after running wpa_supplicant successfully, but that's probably because you still need to get an IP address, which 'dhclient' will do for you.  So the script should work if you add those lines.

Also thanks for writing up that tutorial; I hope it will help someone (it would also be nice to have someone else with a WPN111 verify independently that those are the steps it takes to connect)!

---

### Post by itsjareds on 2008-08-26
It looks like my connection never terminated when it stops, but for some reason it doesn't work anymore. Still says connected in Wicd even after I refresh. But I didn't know that dhclient refreshes my IP, that might help.

My IP is static, I think, though.


> **pytheas22 said:**
> Also thanks for writing up that tutorial; I hope it will help someone (it would also be nice to have someone else with a WPN111 verify independently that those are the steps it takes to connect)!

It was really my pleasure, it feels good letting people know how to do it rather than wasting time like I did. I'll make a new thread about it so people can find it.

---

### Post by itsjareds on 2008-08-27
Here's the tutorial:

[HOWTO: WPA2 with NETGEAR WPN111]("http://ubuntuforums.org/showthread.php?p=5670733")

---

### Post by pytheas22 on 2008-08-30
> It looks like my connection never terminated when it stops, but for some reason it doesn't work anymore. Still says connected in Wicd even after I refresh. But I didn't know that dhclient refreshes my IP, that might help.

My IP is static, I think, though.


I thought you used dyanmic IPs.  If you use static, then you would have had to enter your IP manually using the System>Administration>Network utility, or by editing /etc/network/interfaces directly.  Did you do that?

If you do use dynamic IPs served by dhcp, then running dhclient again should get you a new IP.

If you want to find out whether you actually have an IP on your wireless interface, run:

```
ifconfig wlan0
```

---

### Post by itsjareds on 2008-08-30
I'm pretty sure I have a static IP, this is when your IP address does not change for a long time? I'm not really sure though and had no idea what that meant when I was editing the conf file.

I don't think I added it at all, this is the output of ifconfig wlan0:
```
jared@jared-desktop:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:14:6c:59:31:ed  
          inet addr:192.168.0.127  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:6cff:fe59:31ed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16087 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12106 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12089407 (11.5 MB)  TX bytes:1758969 (1.6 MB)

```

All the addresses look like public ones.

---

### Post by pytheas22 on 2008-09-01
Even if your IP address doesn't change for a long time, it can still be dynamic, which I think yours is.  The only way it could not be is if you manually configured all of your computers (in Linux and Windows) to use a certain IP address.

Anyway though, how well is your wireless card working now?  Are you still having to unplug and replug frequently?

---

### Post by itsjareds on 2008-09-01
> **pytheas22 said:**
> Even if your IP address doesn't change for a long time, it can still be dynamic, which I think yours is.  The only way it could not be is if you manually configured all of your computers (in Linux and Windows) to use a certain IP address.

My IP address has stayed the same for over a year. Is that static?


> Anyway though, how well is your wireless card working now?  Are you still having to unplug and replug frequently?

It's having the same trouble that it's always been, sometimes I can have it plugged in and working for hours, and today it stopped working about five minutes after I booted up Ubuntu.

---

### Post by pytheas22 on 2008-09-01
> My IP address has stayed the same for over a year. Is that static?

It could be, but again, if you have a static IP address, you must have configured your computer at some point to use static IP.

It's also possible to tell your router to always give the same IP to a certain computer--in that case, the addresses are still dynamic insofar as they're served via dhcp; it's just that the router always assigns the same address.  With static IP, the router doesn't assign any address; the user of each computer has to specify manually what the address is.  That's the big difference between static and dynamic.

So it's possible that you're using a fixed address through your router, which explains why it's always the same, but it's still dynamic.  If you never told wicd or Ubuntu which IP address it should use, then you have to be using dynamic IP served by dhcp.

---

### Post by itsjareds on 2008-09-01
> **pytheas22 said:**
> It's also possible to tell your router to always give the same IP to a certain computer--in that case, the addresses are still dynamic insofar as they're served via dhcp; it's just that the router always assigns the same address.

That must be it, I changed my settings in wicd for Static IP to this:

IP - 192.168.0.127
Netmask - 255.255.255.0
Gateway - 192.168.0.1

192.168.0.127 is my local network address, so it is probably dhcp, right? This works out much better as when I connect it doesn't say "Obtaining Network Address" for about 5 seconds. Now, I can connect to the internet in about a second.


Also, not sure if I have said this yet, but when my connection gives up, I can still scan for connections and they all show like normal. It just doesn't let me connect to them.

---

### Post by pytheas22 on 2008-09-01
Alright, if you're telling wicd to use static IPs and the connection is working that way, then I guess you must be using static IPs.  Maybe your router supports both and was serving you via dhcp before?

> Also, not sure if I have said this yet, but when my connection gives up, I can still scan for connections and they all show like normal. It just doesn't let me connect to them.

No, you didn't say that and that's strange.  Was this always the case?  I was under the impression before that when you got disconnected the whole interface crashed.  See if it still crashes with static IP set.

---

### Post by itsjareds on 2008-09-02
Yeah it still crashes with static.

I thought the whole thing was crashing, but then someone told me (was it you?) to try iwlist scan when my connection gave up, and I could still scan. It's only when I try to load ndiswrapper that is when it freezes.

Should I try something other than ndiswrapper?

---

### Post by pytheas22 on 2008-09-02
Unfortunately there is nothing other than ndiswrapper, since your card is not supported by any native Linux driver, and Netgear won't provide specifications so writing one would be very difficult (it can be done, but it would take a really long time and is probably not worth it when you could just buy a new card with better Linux support for $20).

If you really wanted to be hardcore (and have some time), you could recompile ndiswrapper with debugging enabled and try to troubleshoot the crashes that way.  I don't really know how to do that, but I'm sure there are instructions somewhere.

---

### Post by itsjareds on 2008-09-03
I'll probably end up doing the last thing if I ever do it at all. I'll have to learn some programming probably, though. Never have in Linux.

---

### Post by pytheas22 on 2008-09-04
As I say, I don't know very much about debugging ndiswrapper, but if you do end up trying that, let me know and I'll try to help as much as I can.  I don't think you need to know sophisticated programming; you just need to be able to interpret the debugging output and know enough about the source to get an idea of what's wrong.

---

### Post by itsjareds on 2008-09-16
Actually, now it looks like it's crashing only when it's under a lot of load (or maybe it is a contributor). I tried downloading 4 files at once and my connection gave out, then it happened again after a reboot.

---

### Post by pytheas22 on 2008-09-16
That's interesting.  Have you changed anything lately with regards to ndiswrapper?

Also have you made any progress on the debugging stuff?

---

### Post by itsjareds on 2008-09-17
Haven't had a chance to start debugging yet. Hopefully this weekend, or today/tomorrow if I have time.

And no, I haven't changed ndiswrapper at all since I installed it. All I've ever done on it was install my card. It also happens on my other computer with the same device.

---

