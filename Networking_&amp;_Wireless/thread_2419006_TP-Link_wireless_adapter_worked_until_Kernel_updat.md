---
title: "TP-Link wireless adapter worked until Kernel update to 4:15:0-48"
date: 2019-05-15
forum: Networking &amp; Wireless
---

### Post by DroversDuck on 2019-05-15
Folks,
A few weeks back I installed a TP-Link wireless adapter (the Archer 4TU device based on the rtl8812au chip) in a desktop machine running Ubuntu 18.04 kernel 4:15:0-47.  Ubuntu's Software and Updates app found the r8812au network driver and everything went very smoothly with good network connection, until two weeks later when I did a software update.  As soon as the kernel was updated to 4:15:0-48 I had no wifi - although the machine saw the USB device (lsusb) the Settings tab told me there was no wireless device connected.  It was as dead as a dodo.

I restarted the machine and selected the previous kernel from GRUB's boot options tab - I immediately had wireless connectivity again.  Clearly, the problem is with the kernel.

My question is what to do from here?  If I maintain the previous kernel (taking care to avoid future software updates) will that take me off the update trail?  Every time Software Updater tells me there are updates available I will have to ensure that the kernel does not update and then there's a possibility that my system could fail the software pre-requisites for other updates.

I would appreciate any advice on what to do in this situation.

Thanks in anticipation

---

### Post by jeremy31 on 2019-05-15
That is an issue with the Makefile and/or dkms.conf file of the package, see [https://askubuntu.com/a/832741/300665](https://askubuntu.com/a/832741/300665) for instructions on how to fix

---

### Post by DroversDuck on 2019-05-31
Thank you Jeremy for your assistance - I've been away for two weeks and only just got back home yesterday, so this is a belated response to your reply.

I have followed your scripts as closely as I could but without success.  The sequence I followed is this:

1.  I successfully edited the dkms.conf file in /usr/src.
2.  When I attempted to edit the dkms.conf file in /var/lib/..../build/dkms.conf the edit screen showed that the file did not exist.
3.  When I tried again, having removed the /build/ folder, the file does exist but is completely empty.
4.  When I used your subsequent /build/ and /install/ scripts the response was that both functions have been already installed for my 4.15.0-48 kernel but my adapter is still not recognised.

Then, I noted the comment from Heynnema, below your referenced scripts and can see that there is something else I need to be aware of but I am not sufficiently au faix with Linux code to understand what he is saying.

I am now successfully connected to the Internet using the 4.15.0-47 kernel but would like to resolve this problem in the longer term.

If I am appearing to be a bit dense here I apologise but I can make no excuse; my limited knowledge of the system structure/commands is a serious problem for me.

Neil

---

### Post by jeremy31 on 2019-05-31
Try
```
dkms uninstall rtl8812au/4.3.8.12175.20140902+dfsg -k 4.15.0-48-generic
dkms install rtl8812au/4.3.8.12175.20140902+dfsg -k 4.15.0-48-generic
```
Reboot

---

### Post by DroversDuck on 2019-06-03
Jeremy,
I have done as you suggested but there's a problem somewhere.  I have attached a screen shot of my terminal window because I am not able to interpret the results.  Does this make sense to you?
Thank you for your assistance.

---

### Post by jeremy31 on 2019-06-03
I would install updates and reboot, see if it works correctly with a new kernel

---

### Post by DroversDuck on 2019-06-04
Hi Jeremy,
Well, I have installed all updates and rebooted without success; Kernel 4.15.0-47 (which did see the adapter) was uninstalled and replaced by 4.15.0-50, which does not see the wifi adapter.  The only options for me now are to use version 48 or 50, neither of which see the adapter.  I'm thinking I should reinstall version 47 and live with it - no more updates.

What do you think?

---

### Post by jeremy31 on 2019-06-04
It may be worth using a different source
```
sudo apt install git
git clone https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git
cd rtl8812AU_8821AU_linux
sudo make -f Makefile.dkms install
sudo dkms remove rtl8812au/4.3.8.12175.20140902+dfsg --all
```

---

### Post by DroversDuck on 2019-06-05
Hi Jeremy,
These five lines of code have had some effect - now Ubuntu is seeing the adapter in the Settings app but cannot see any wireless networks in the "Visible Networks" box.  I know there's a very strong signal present because I have a Ubiquiti Access Point six feet away and the signal strength is high.  I did a search using the "hidden network" option but no connection was made.

If I could get an ISO of the very latest version of 18.04 I could do a complete re-installation but that's an option I really don't want to take because it's a blunt and inelegant solution and I would feel as though I'm not learning anything in the process.  The other thing is that there might be a bug in the kernels after 47 and that needs to be fixed for everyone's benefit (I have seen quite a few instances of difficulty on the forum with some kernels and this adapter).

What do you think?

---

### Post by jeremy31 on 2019-06-05
See the wireless script link in my signature and post results

---

### Post by DroversDuck on 2019-06-06
OK - herewith the link to pastebin      

[http://paste.ubuntu.com/p/F9S2ZJvV8r/](http://paste.ubuntu.com/p/F9S2ZJvV8r/)

---

### Post by DroversDuck on 2019-06-23
Hello Jeremy - Are we still in communication?

I have perused the pastebin file but my unpractised eye sees nothing untoward.

Do you have any observations?

Thanks

Neil

---

### Post by jeremy31 on 2019-06-23
Do a ```
iwconfig
```
Post results

---

