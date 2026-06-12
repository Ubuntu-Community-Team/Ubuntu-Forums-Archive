---
title: "RT2500 w/ WPA Grief, help me tidy up?"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by zoiks on 2007-10-21
OK well finally I got my ralink-based card working again after the upgrade to Gutsy put the kibosh on it. I searched the posts and found that most of the successful suggestions on here tell you to dump the rt2500 drivers and use ndis-wrapper.

Good grief, I don't want to use Windows drivers (and I don't have the Windows install CD anymore, anyway).

The wiki also says that rt2500 should work "out of the box" with gutsy, "even with WPA". But I've found that to be untrue in my case.

So, after a few hours, my current working setup is highly sub-optimal, mostly because I am not an expert at the inner workings of kernel drivers.  But this is what is working for me:

1) Download and install the rt2500 source from serialmonkey. Install build-essential and the kernel-headers for the current kernel. Go to the rt2500 source directory's Module directory and type "make" and "sudo make install".

2) Put the following lines in /etc/network/interfaces:

auto wlan0
iface wlan0 inet dhcp 
        pre-up ifconfig wlan0 up
        pre-up ifconfig wlan0 down
        pre-up ifconfig wlan0 up
        pre-up ifconfig wlan0 down
        pre-up iwconfig wlan0 essid "myssid"
        pre-up iwconfig wlan0 mode Managed
        pre-up iwpriv wlan0 set AuthMode=WPAPSK
        pre-up iwpriv wlan0 set EncrypType=TKIP
        pre-up iwpriv wlan0 set WPAPSK="mypskkeystring"
        pre-up ifconfig wlan0 up

3) Run the following commands (which I have now put in a script):

sudo ifdown wlan0
sudo rmmod rt2500
sudo rmmod rt2500pci
sudo insmod /home/username/sources/rt2500-cvs-2007102014/Module/rt2500.ko


Note that I have to point to the compiled kernel module in the script, which happens to be in my user's home directory where I downloaded it.

So here's my question: how do I remove ubuntu's native rt2500 and rt2500pci modules, so that they don't load on startup, and how do I install the compiled rt2500(.ko) module so that it loads automatically during startup? This way I wouldn't have to run the script every time I start up my laptop.

Thanks for any suggestions.

---

### Post by kevdog on 2007-10-21
After you compiled the drivers from serialmonkey and issued the sudo make install command, didnt this install the custom kernel module into the appropriate directory??

If you dont want kernel modules to automatically load, then put them in /etc/modprobe.d/blacklist

---

### Post by zoiks on 2007-10-21
> **kevdog said:**
> After you compiled the drivers from serialmonkey and issued the sudo make install command, didnt this install the custom kernel module into the appropriate directory??

If you dont want kernel modules to automatically load, then put them in /etc/modprobe.d/blacklist

Well a bunch of text came back that (to me) said the module was "installed", but even after sudo make install, I could not "insmod rt2500" without pointing to the compilied .ko file (it says no such file or directory).

OK, I can blacklist the modules I want to, but how do I get the correct rt2500 module to load on startup?

Thanks.

---

### Post by zoiks on 2007-10-21
FWIW, it seems to me that gutsy's implementation of rt2500 is broken when it comes to the "iwpriv" commands that are issued in /etc/network/interfaces. The usual way to set WPA mode, encryption type, and the pre-shared key is to use

iwpriv wlan0 set Variable='value'

but the wlan0 interface created from gutsy's version of rt2500 doesn't have the "set" command available in the internal interface. Thus, the "interfaces" file fails to bring up wlan0 successfully, and the WPA-related settings for the ralink card can't be set.

Therefore, the kludge I described in my initial post is a way to get rid of the ubuntu-supplied rt2500 modules, and replace them with one that allows the "set" command through iwpriv.

I dunno. It's just a gripe I have that with every upgrade I've done, barring feisty I think, rt2500 seems broken. A shame since Ralink has been possibly the best company at supporting open source drivers for its product.

---

### Post by kevdog on 2007-10-21
Just curious what you find:

modinfo rt2500

Does this return the default info or the one for your custom made kernel??

If you do
sudo updatedb

then
locate rt2500

How many rt2500.ko files are listed?  Is the module you compiled listed along with the default kernel module??

If so, how about manually renaming the default kernel module??

I thought modules could be forced to load by default by placing them in /etc/modules

Any specific reason for using insmod over modprobe??

---

### Post by zoiks on 2007-10-21
> **kevdog said:**
> Just curious what you find:

modinfo rt2500

Does this return the default info or the one for your custom made kernel??

If you do
sudo updatedb

then
locate rt2500

How many rt2500.ko files are listed?  Is the module you compiled listed along with the default kernel module??

If so, how about manually renaming the default kernel module??

I thought modules could be forced to load by default by placing them in /etc/modules

Any specific reason for using insmod over modprobe??


Thanks! From your helpful suggestion, modinfo rt2500 showed that I actually did have the custom-compiled rt2500.ko module installed and loading. Apparently, the loading of rt2500pci was preventing rt2500 (which turned out to be the correct rt2500) from working properly.

Thus, all I had to do actually was add the line

"blacklist rt2500pci"

to the file /etc/modprobe.d/blacklist, and now the wireless network interface comes up when the machine boots. Thank you!

(My problem is I don't understand all the ins and outs of kernel modules and such.)

So, in summary, I can re-state what my effective solution was to get my ralink-based card working properly in gutsy:

1) Download and unpack the rt2500 source from serialmonkey. Install build-essential and the kernel-headers for the current kernel. Go to the rt2500 source directory's Module directory and type "make" and "sudo make install".

2) Put the following lines in /etc/network/interfaces:

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up ifconfig wlan0 down
pre-up ifconfig wlan0 up
pre-up ifconfig wlan0 down
pre-up iwconfig wlan0 essid "myssid"
pre-up iwconfig wlan0 mode Managed
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set WPAPSK="mypskkeystring"
pre-up ifconfig wlan0 up

3) Add the line "blacklist rt2500pci" to the file /etc/modprobe.d/blacklist, and reboot.

Now the wireless network comes up at startup. The above steps describe my effective solution the way I can recall, after having futzed with this for a while.

Thanks for the responses. I hope this helps others having difficulties with the ralink-based wireless cards. Cheers.

---

### Post by zoiks on 2007-10-21
Just wanted to add also, I have the rt2500 stuff working without having to remove network-manager-gnome. It still runs, but just says that wlan0 is "roaming".

Also, I installed ubuntu's rutilt (via the rt2500 package) and it works as well. Cheers all.

---

### Post by kevdog on 2007-10-21
I would be great if you could write this up in another thread and make it a HOW-TO.  Would be one of the first Gutsy how to's.

How did you discover that the default rt2500.ko module was not properly responding to your set commands??

Good detective work.

If you are using rutilt it might be a good idea to uninstall network-manager (at least it was in Feisty where ra based cards really never worked correctly with network manager).  I know WICD would work with ra based chipsets.  Seems like the ra - network manager problem still exists in Gutsy

---

### Post by zoiks on 2007-10-21
> **kevdog said:**
> 
How did you discover that the default rt2500.ko module was not properly responding to your set commands??


I simply typed "ifup wlan0" and it complained that "set" was an invalid command. I learned that iwpriv (issued through /etc/network/interfaces) is used to issue commands to the interfaces through private ioctl's. When I typed "iwpriv" at the command line, a list of 2 "commands" shows up, and "set" isn't one of them. I believe now that this result was from having rt2500pci (not rt2500) creating the wlan0 interface, and the "set" command not being made available by rt2500pci.

When I got the correct module working, I typed "iwpriv" and several commands were listed for wlan0, and "set" was on the list. So that added a little clarity on what was going on.

---

### Post by bigboy_pdb on 2007-10-23
If you who don't want to use ndiswrapper (and you'd prefer to use the modules that came with Gutsy), you might want to try the solution that worked for me. It can be found here:
[http://ubuntuforums.org/showthread.php?t=587727](http://ubuntuforums.org/showthread.php?t=587727)

---

