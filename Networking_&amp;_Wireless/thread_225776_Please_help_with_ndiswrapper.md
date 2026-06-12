---
title: "Please help with ndiswrapper"
date: 2006-07-30
forum: Networking &amp; Wireless
---

### Post by .Maleficus. on 2006-07-30
I really need some help installing drivers with ndiswrapper.  I have ndiswrapper installed, and I went to their installation guide page, ([http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Install_Windows_driver](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Install_Windows_driver)) and I don't understand their directions.  I typed lspci like they said to see what drivers or whatever I need, and I didn't see anything that looked like my USB adapter (Linksys WUSB54G ver.4).  It has driver downloads on the List page, but I can't find one to use.  I tried the last one given for my card, and Wine tryed to open it.  All of the text describing each download only confused me more.  Could somebody please tell me how they set up their card?

---

### Post by .Maleficus. on 2006-07-30
Um, I had some odd wording in that last post.  Let me try to rephrase that.

I had some trouble with a guide for a different wireless adapter, so I decided to try to use my other one.  I installed ndiswrapper, but that's all I could really do (I'm a Linux n00b.)

I went to the driver installation website, and read their instructions.  They didn't make much sence to me, so I went ahead and just looked for a driver.  I found the drivers for my card, (Linksys WUSB54G ver. 4), and clicked the last link, because that was the only one that went directly to a download, and not to a site were I had to find the download myself.  It was a .exe file, so Wine tried to open it.  I tried to run in the terminal (the name of the download).inf.  That didn't work.  So basically I am stuck.  How did you guys install your drivers?

Also, does it matter that Networking calls it rausb0, unlike the other card which was named wlan0?

Thanks for any help!

---

### Post by .Maleficus. on 2006-08-02
Anybody?


Edit:  I just tried installing the driver again, and this is what happend.
```
Installing wusb54gv4_20050503
couldn't copy wusb54gv4_20050503 at /usr/sbin/ndiswrapper line 135.
```
I downloaded the driver from the Linksys website.
I tried installing it like this.
```
ndiswrapper -i wusb54gv4_20050503
```

Any help is greatly appreciated!

---

### Post by gary201147 on 2006-08-02
hi there, 

i just finished installing a driver for my usb wireless device so i'll help you out :)

your argument for -i command needs to be in this form:

ndiswrapper -i ~/driver.inf (assuming your driver is called driver and you put the driver in your /home/username directory)

it seems that you need to extract/unpack your driver using unzip, cabextract, unshield. within your driver you should find an *.inf file and *.sys file. make sure you put them in the same directory. now run the ndiswrapper command line again. then run:

ndiswrapper -l 

you should see the following if you did it correctly 

 {name of driver}  driver present, hardware present

check out this link if you have more questions [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by .Maleficus. on 2006-08-02
Ugh...  I couldn't get cabextract to extract my driver...  I got a message saying it was an invalid cabinet or something...
```
/home/andy/WUSB54Gv4_20050503.exe: no valid cabinets found

All done, errors in processing 1 file(s)
```
Any ideas?

---

### Post by .Maleficus. on 2006-08-03
I tried using Unshield as well, and that couldn't extract the file either.

Also, I tried extracting "Setup.exe" for something that I downloaded, and that couldn't be extracted either.

This is what I tried.
```
cabextract /home/andy/gtk-gnutella-downloads/complete/Setup.exe
```
Did I do it wrong?

---

### Post by .Maleficus. on 2006-08-05
Anybody?  I really need some help with this.

Has anybody else used this adapter and got it to work?  If so, what driver did you use and how did you do it?

---

### Post by .Maleficus. on 2006-08-06
Ok, I found my driver cd, and I copied the .inf and .sys files into my home directory because on the Installation Wiki for ndiswrapper, it said they needed to be in the same directory.

Every time I try to install a driver, I get the error message,
```
Installing rt2500usb
couldn't copy /root/rt2500usb.inf at /usr/sbin/ndiswrapper line 135.
```
Did I do it wrong?

---

### Post by Manveru913 on 2006-08-07
I am having the exact same problem with my wireless card--it is a pci card though, not a usb adapter. I cant find any other help on this anywhere...

---

### Post by Manveru913 on 2006-08-07
Ok, i think i figured out the "couldnt copy..." problem. The problem for me was that when entering the ndiswrapper -i command, you have to specify the entire path to the .inf file. 

example: 
ndiswrapper -i /home/name/driver.inf 
instead of 

ndiswrapper -i driver.inf

hope that helps.

---

### Post by .Maleficus. on 2006-08-08
Thanks for the reply, but sadly, that didn't work.:sad: 

Is there any way I can copy it manually, instead of having ndiswrapper do it?

---

### Post by .Maleficus. on 2006-08-11
Anybody?

---

### Post by mpvano on 2006-08-11
You must be doing something wrong.

I just downloaded that driver from linksys.com by following through all the menus and clicking on the final link with firefox and here's what I got in my specified download folder:

A file called WUSB54Gv4_20050503.exe

This is a "self-extracting" windows program containing an embedded .zip file. Running wine to extract it will work, but it's serious overkill. Most ubuntu linux zip file extractors have no trouble handling it.

In any case, I don't know what utiltity used to extract it, but it looks like it worked. Here's what I found: when I run the command "unzip WUSB54Gv4_20050503.exe" from a terminal program window logged into the directory containing the file, unzip runs, shows a list of the files it's extracting and exits.

This left a folder in that directory called "WUSB54Gv4_20050503" which seems to be what you experienced as well.

I'm guessing this result is what's confusing you. The files you need for ndiswrapper are in additional folders INSIDE this folder.

Specifically they are in a folder called WUSB54Gv4_20050503/Drivers/WUSB54Gv4.

rt2500usb.cat 
rt2500usb.inf
rt2500usb.sys

You need to pass the COMPLETE access path for the .inf file to ndiswrapper in order to configure it.

It sounds like everything is functioning just as it is supposed to do, but you're not understanding the instructions and ending up in the weeds on your attempts to set up ndiswrapper.

Perhaps you need to find someone locally to help you with unix commands. I'm afraid this just isn't a "one button install" operating system yet (and may never be).

For what it's worth I have successfully configured and used several different wireless adapters, including one USB one with Dapper using the default ndiswrapper installation and they have all worked perfectly, but it's clear that the process may not be suitable for beginners.

hoping that this gets you pointed in the right direction,

Mario

---

### Post by .Maleficus. on 2006-08-12
YES, IT INSTALLED!  But, now I have another problem.  When I try to activate it, my computer freezes.  Any ideas?

---

### Post by mpvano on 2006-08-13
I can't tell much remotely, but it's been my experience that if the computer freezes using an ndiswrapper driver, it's usually because of a problem with the windows driver. 

Before you assume that, however, you need to explain how you are loading ndiswrappre. By default, it's NOT loaded. Loading it twice or loading it and another driver can cause this problem.

What commands did you give to the ndiswrapper utility exactly to configure the driver?
After you got ndiswrapper configured what did you do next?

Mario

---

### Post by .Maleficus. on 2006-08-14
Well, I'm guessing I didn't load it at all, since I don't know how to do that lol.  All I did was get the driver installed, check to see that it installed, and the "modprobe" thing (another thing I don't know why I did, but I guess I was supposed to).

How do I go about loading ndiswrapper?

---

### Post by mpvano on 2006-08-14
I'm sorry, but it's impossible to tell what happened from your vague descriptions. Please tell me exactly what you did and what you saw.

1. What ndiswrapper commands did you give and what were the results?
2. What modprobe command did you give? What was the result?
3. Is THAT when your machine froze? If not, what did you do next?

When you say the machine froze, do you mean that you had to reset it or that something else happened?

If the machine did not "freeze" or report any errors on the terminal or do anything else surprising after the modprobe command, then the driver loading didn't crash things.

Try the following:

restart your machine (I assume you can do that without crashing?)

type the following commands into a terminal window and report back exactly what the results are - if you freeze at some point, tell me exactly what you mean by freeze and exactly at which point it happened.

lsmod | grep ndis

if that command does not display at least one line containing the word ndiswrapper, then try the following

sudo modprobe -a ndiswrapper

if that does not report any surprising errors or freeze then report back what the first command says...

lsmod | grep ndiswrapper

if that now shows a line with the word ndiswrapper, then try the following and report the results:

sudo iwconfig

sudo ifconfig

at this point you could also switch over to any of the standard threads covering getting your wireless card working, but let's make sure you really have a driver loaded.

By the way, the ndiswrapper commands you give just add the drivers to the ndiswrapper driver system so it will be able to use them when it's started. The ndiswrapper commands are not using ndiswrapper itself. Those commands are those of the utility that configures it.

It would be very useful to know exactly what installation commands you gave.

You can see if the installation succeeded, by inspecting the result with the command

ndiswrapper -l

If you can, try to report back the result of that command as well.

The actual ndiswrapper driver is a kernel module. kernel modules are loaded and removed by the "modprobe" command. If you typed "sudo modprobe ndiswrapper" you tried to load the driver. However, normally this command is run all by itself much earlier in the startup process, using information that is installed in other files to trigger the loading. Did you alter any other files when you did whatever you did to "install" the driver?

The modprobe command needed to load ndiswrapper can also be triggered by configuration file changes made by certain "ndiswrapper" commands - that's why I need to know whether you gave any other commands when you "installed" ndiswrapper.

What we are trying to find out here is whether the ndiswrapper kernel module is loaded or not, if it loaded successfully, or not, and whether there's any chance it somehow got loaded twice, or got loaded with the wrong windows driver attached to it.

Once we get figured out what you've GOT happening, then we'll get you set up to automatically load the driver correctly (if it's not working already). After that, you still need to get your computer to actually USE the driver to "associate" with an access point, get "authenticated" permission to use it, and succeed in joining its IP network.

There are a lot of steps in this process that have to work properly. So far we're just at the first one - one thing at a time.....

By the way, setting up ndiswrapper is usually very easy and straightforward once you locate the windows driver for your card. Most people get confused because something goes wrong at some point in the process and they end up blaming ndiswrapper. It actually works very well and is quite reliable for nearly all windows drivers. Most people seem to be having trouble setting up Dapper wireless at a much later stage - that of actually associating with an access point and authenticating and get into a horrible tailspin as a result. Please don't just blindly try things!

Mario

---

### Post by .Maleficus. on 2006-08-15
This should be everything:
```
andy@andy-desktop:~$ lsmod | grep ndis
andy@andy-desktop:~$ sudo modprobe -a ndiswrapper
andy@andy-desktop:~$ lsmod | grep ndiswrapper
ndiswrapper           177364  0
usbcore               130692  5 ndiswrapper,rt2570,ehci_hcd,ohci_hcd
andy@andy-desktop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

rausb0    RT2500USB WLAN  ESSID:""
          Mode:Managed  Frequency=2.412 GHz
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/70  Signal level:-120 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

andy@andy-desktop:~$ sudo ifconfig
eth1      Link encap:Ethernet  HWaddr 00:10:B5:8A:F9:4A
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::210:b5ff:fe8a:f94a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7418 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6943 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7578498 (7.2 MiB)  TX bytes:928466 (906.7 KiB)
          Interrupt:201 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

andy@andy-desktop:~$
```
When I do the ndiswrapper -l command, I get drivers present, hardware present.

I believe I did the sudo modprobe ndiswrapper command too.

If I changed any files, I did not realize it, so I don't think anything should be changed.  But, I may have done the wrong command at one point, so it might not be loaded or may have loaded wrong.

If you need any more information, please tell me.

And thank you for the help!

---

### Post by mpvano on 2006-08-15
Now we're getting somewhere!

This stuff

rausb0    RT2500USB WLAN  ESSID:""
          Mode:Managed  Frequency=2.412 GHz
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/70  Signal level:-120 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



appears to indicate that you have a properly working wireless card, but that it's not associated with an access point.

There's one thing here that may be confusing you, however, and that's the fact that it has a funny name. Various drivers usually decide to name the running device whatever they choose. This one is named rausb0. That makes no difference at all, except that you might have been looking for a device with a different name!

Ubuntu has a mechanism in place to ensure that cards always get standard names, but it is enforced by a text file called "iftab" in /etc. I suggest for now that we don't worry about this problem, but later on you may wish to look at the man page for iftab and see how to edit /etc/iftab to always cause your card to be named eth1 (or wlan0) to minimize confusion. That's done by associating the MAC address of the card with the desired name.

You also seem to be using a wired ethernet adapter right now (I presume that's how you typed your note). Don't forget that you'll have to decide which card is in use to connect to the internet later. You can't run both as your internet connection because you'll have to have an unambiguous default route set.

Tell me one more thing. Do you get the iwconfig results shown if you DON'T manually issue the sudo modprobe command? If so, the driver's being loaded automatically at startup. If not, one way to get it to load automatically at boot is by adding the line "ndiswrapper" to the file /etc/modules. Note that this won't enable the interface, but it will only make sure that the driver is loaded into memory and the card is available.

Tell me more about the network you want to connect with. There are many subtle problems in ubuntu (and even in windows XP) with connecting to wireless networks - especially if more than one is available. We're going to try to connect manually first using specific commands once we figure out the details of the access point you wish to connect to.

Tell me what kind of access point you are trying to connect to (brand and model), if possible, what channel it is on, what its Essid is (that's the name of the wireless network), how it authenticates (or guarantees privacy), and whether it uses any other security features.

One more thing that would help, would be to send the result of the following command:

sudo iwlist rausb0 scan

when you are within range of the desired access point...

Mario

(P.S. It's possible that if your network is very simple, you can actually get a connection using the ubuntu builtin gnome network administrator - you'll find it in the System:Administration menu as "Networking". But it's easy to get confused using it, especially because you can really mess it up by doing a lot of fast trial and error operations without waiting for the earlier ones to complete (sometimes you need to wait  as long as 5 minutes!). If you'd like to try that, go ahead, but if it doesn't seem to connect, restart your computer before doing any other troubleshooting.


mv

---

### Post by .Maleficus. on 2006-08-17
Thanks for all the help man, but it looks like I won't be needing it anymore.  My computer just died :(.  Thanks for all the time you put into it though!

---

### Post by mpvano on 2006-08-17
Sorry to hear that.

Mario

---

