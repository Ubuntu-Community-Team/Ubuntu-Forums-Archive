---
title: "How to set up Wireless connection"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by Wiesje on 2008-11-02
Hi,

Just installed 8.10 on Acer Aspire One.
But I don't know how to get Wireless connection to work.
I did try ```
sudo aptitude install linux-backports-modules-intrepid
```
And also ```
sudo aptitude install linux-backports-modules-intrepid-generic
```
I did completely shut down and booted again.
But I don't see no wireless networks showing up in Network Connections.
So did add a connection manually, but how to connect to it? And where can I find what networks ar nearby?

- yeah, I'm a first-time Linux user -

---

### Post by nothingspecial on 2008-11-02
Check you have the atheros card that Acers use.
```

lspci -v
```

It should return 

```
Ethernet controller : Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter
```

somewhere near the end.

If it does copy and paste the following commands into your terminal with a wired connection.

Download the latest madwifi snapshot.

```
wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz

```
Unzip it
```

tar -xvf madwifi-hal-0.10.5.6-current.tar.gz
```


navigate to the extracted file

```

cd madwifi-hal-0.10.5.6-r3861-20080903
```

If you`ve not got the tools necessary for compiling get them

```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

Then compile it
```

sudo make
```

```
sudo make install
```

load the module

```
sudo modprobe ath_pci
```

make it load every time you boot

```
gksudo gedit /etc/modules
```

then copy and paste this to the bottom of that file
```

ath_pci
```

save
exit 
reboot

---

### Post by Wiesje on 2008-11-02
> **nothingspecial said:**
> Check you have the atheros card that Acers use.
```

lspci -v
```

It should return 

```
Ethernet controller : Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter
```

somewhere near the end.

If it does copy and paste the following commands into your terminal with a wired connection.

Download the latest madwifi snapshot.

```
wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz

```


First step: allright, it returned this ethernet controller.
But when trying to download madwifi snapshot it returns:
[I]Resolving snapshots.madwifi.org... failed: Name or service not known.
wget: unable to resolve host address `snapshots.madwifi.org'[/I]

---

### Post by nothingspecial on 2008-11-02
madwifi.org appears to be down at the moment. Try later.

---

### Post by pasencorelui on 2008-11-02
madwifi.org is unreachable. is there another wau to get madwifi-hal-0.10.5.6 ? Is someone can share or indicate a mirror to get it?

Thank's

---

### Post by pasencorelui on 2008-11-02
madwifi.org is unreachable. is there another wau to get madwifi-hal-0.10.5.6 ? Is someone can share or indicate a mirror to get it?

Thank's

---

### Post by Wiesje on 2008-11-02
> **pasencorelui said:**
> madwifi.org is unreachable. is there another wau to get madwifi-hal-0.10.5.6 ? Is someone can share or indicate a mirror to get it?

Thank's

Yeah, would be much appreciated. It's still offline :cry:

---

### Post by ngirala on 2008-11-02
I found this link to download, but haven't tried it yet. [www.4shared.com/file/58847723/81fbdf/madwifi-hal-01056-r3835-20080801tar.html](www.4shared.com/file/58847723/81fbdf/madwifi-hal-01056-r3835-20080801tar.html)
Good luck

---

### Post by ngirala on 2008-11-02
I confirm that this download works
[http://www.4shared.com/file/58847723/81fbdf/madwifi-hal-01056-r3835-20080801tar.html]("http://www.4shared.com/file/58847723/81fbdf/madwifi-hal-01056-r3835-20080801tar.html")
following this instructions 
[http://www.mclarenx.com/2008/06/17/atheros-ar242x-ar5007eg-en-ubuntu-linux-804/]("http://www.mclarenx.com/2008/06/17/atheros-ar242x-ar5007eg-en-ubuntu-linux-804/")
Tried it with ubuntu 8.10

---

### Post by nothingspecial on 2008-11-04
Madwifi is back up. Try again

---

### Post by eks on 2008-11-05
> **Wiesje said:**
> I did completely shut down and booted again.
But I don't see no wireless networks showing up in Network Connections.
So did add a connection manually, but how to connect to it? And where can I find what networks ar nearby?


If you have not yet installed the driver manually by downloading it from madwifi.org, try going to System/Administration/Hardware Drivers and make sure the Atheros one is activated. Then reboot.

If it doesn't do the trick, you can either try to install it manually with the suggestions above or try to make sure only ath5k module is being loaded. More information about this second option here: [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)


PS: a driver, as it's called in Windows, is called a module on Linux.

---

### Post by nothingspecial on 2008-11-05
One more piece of advice.

Every time you get a kernel update, as I did this morning you will have to recompile madwifi. This is very easy. 

Keep the extracted files you downloaded, madwifi-hal-0.10.5.6-r3861-20080903.

I keep them in my home directory in a folder called .madwif.
Putting a dot in front of a folder name hides it. To view hidden folders press Ctrl + H or from the command line ```
ls -a
```.

Now you put the madwifi folder wherever you like but assuming you do the same as me go to the madwifi folder ```
cd .madwifi/madwifi-hal-0.10.5.6-r3861-20080903
```

Then do these 3 commands one at a time

```
make clean
make
sudo make install
```

That`ll fix it.

Another useful snippet. The terminal will finish things off for you with the tab key. So instead of typing ```
cd .madwifi/madwifi-hal-0.10.5.6-r3861-20080903
```[/CODE]

I just typed ```
cd .madwifi/ma
``` then pressed tab and the rest of the folders name magically appears. This works for commands aswell. Try it.

---

### Post by audiobreather on 2008-11-05
This fix worked very well on my Acer Aspire 5220 with Atheros AR242x! It got faster connection than the compat-wireless fix. Thank you so much nothingspecial!

---

### Post by xobo on 2008-11-05
Hello, I am new to linux,I just install Ubuntu 8.10, After doing the following:-
--------------------------------------------
[COLOR="Blue"]cd madwifi-hal-0.10.5.6-r3861-20080903

If you`ve not got the tools necessary for compiling get them

sudo apt-get install build-essential linux-headers-$(uname -r)[/COLOR]
--------------------------------------------
I get at the bottom line:-
[COLOR="blue"]E: Couldn't find package build-essential[/COLOR]
Anyone could advise me what to do? how to get the "necessary tools to compile them?
Thank you.

---

### Post by nothingspecial on 2008-11-06
Click system > administration > software sources

Make sure all the boxes in the ubuntu software tab are checked.

Then ```
sudo apt-get update
```

And try again.

---

### Post by beresovskiy on 2008-11-06
Hello everyone. I'm new to linux. I've installed Ubuntu 8.10 recently and issued a problem with ati, flash and wi-fi. I've googled for a while and found solutions to both 1 and 2 problems, but I've got stuck with setting up wi-fi.

My laptop: samsung r60p
Wi-Fi controller:
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Askey Computer Corp. Device 7131
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at d8100000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [60] Express Legacy Endpoint, MSI 00
	Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Kernel modules: ath5k, ath_pci

I've tried to use restricted drivers, to compile the madwifi (i gave up at the stage of make/make install - see report in attach).


/home/main/madwifi-0.9.4/net80211/ieee80211_power.c: In function 'ieee80211_pwrsave':
/home/main/madwifi-0.9.4/net80211/ieee80211_power.c:240: error: implicit declaration of function '__skb_append'
make[3]: *** [/home/main/madwifi-0.9.4/net80211/ieee80211_power.o] Error 1
make[2]: *** [/home/main/madwifi-0.9.4/net80211] Error 2
make[1]: *** [_module_/home/main/madwifi-0.9.4] Error 2
make: *** [modules] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 2
main@main-laptop:~/madwifi-0.9.4$ sudo make install > error2.txt
install: cannot stat `ath_pci.ko': No such file or directory
make[1]: *** [install] Error 1
make: *** [install-modules] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1




Please, anyone who can help me, reply!

_____________
I've also tried ndiswrapper, but failed to learn its usage

---

### Post by xobo on 2008-11-06
> **nothingspecial said:**
> Click system > administration > software sources

Make sure all the boxes in the ubuntu software tab are checked.

Then ```
sudo apt-get update
```

And try again.
Yes it did work beautifully.At last after about a month of work I can connect to the Internet with wireless. I can confirm that the above process work with the Compact Presario laptop C793VU (that got athros AR2425 {AR5007} ). Thank you very much for your assistance. Yes, You are Special Thing.
Xobo

---

### Post by Cirvaazny on 2008-11-09
I will add that the method described by nothingspecial finally got the wifi on my Toshiba L355D-S7815 working under intrepid.  Thank you, I can finally remove the cord from my laptop.  I'll note that I had Wicd already installed (the newest version from the site) and that I had to manually add the adapter into the settings and reinstall Wicd before it would successfully connect using the WLan.

---

### Post by Open on 2008-12-16
Thanks fore the how to, now I can browse the web wireless on my Acer Aspire 5220.

---

### Post by NOOBUNTU54961 on 2008-12-20
got it !!! Thanks
              Randy

---

### Post by usafmom04 on 2010-11-16
I have a msi laptop with built in wireless card and web cam and I can get them to work?
Also If i decide that I want ubuntu as my only os how do i go about it?

---

### Post by nothingspecial on 2010-11-16
> **usafmom04 said:**
> I have a msi laptop with built in wireless card and web cam and I can get them to work?
Also If i decide that I want ubuntu as my only own os how do i go about it?
Hi, welcome :)

The first thing you do is create your own thread detailing your wireless info (rather than dragging one up from 2 years ago)

So, open a terminal (in your menu - accessories > terminal) and copy and paste this into it

```
sudo lshw -C network
```

Then copy and paste the gobbldygook that the terminal spits out into a new thread, either on the networking & wireless board or the absolute beginner one, depending on your experience.

Give as much information as you can.

I wouldn`t recommend ditching your other os until you have sorted out your wireless issues.

Cheers :)

---

