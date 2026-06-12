---
title: "Struggling to install Realtek RTL8723B USB adapter"
date: 2017-01-17
forum: Networking &amp; Wireless
---

### Post by heatopher2 on 2017-01-17
Hi, I've just installed Ubuntu, after a bit of sweating, dual-booting  alongside Windows. I've been meaning to get round to this for years, and  finally I've managed it. So I'm reasonably proud of myself. But now I  have to connect to the internet, using a nifty little 2-in-1 wifi/bluetooth USB dongle, which cost next to nothing. It installed very easily on Windows, but of course on Linux it's a different story....

I'm not completely unused to Linux, but not confident enough to be able to do this kind of thing by myself. So I've tried looking at this documentation that came on the CD, along with the drivers and whatever else:

[ATTACH=CONFIG]273234[/ATTACH]

In the documents folder, there are indeed a lot of documents, but none of them constitute simple installation instructions for dummies like me :~(

[ATTACH=CONFIG]273235[/ATTACH]

I tried running that install.sh script (remembering my basic linux knowledge), but I'm afraid that didn't work.

The strange thing is that the bluetooth half of the dongle works already, without my having had to do anything at all, but unfortunately that doesn't seem to be true of the wifi half. Please help! This PC is a lo-o-o-ong way from the router, and I really don't want to have to be trailing a load of wires around the house!

Please point me elsewhere, if this has already been discussed.

Thanks in advance,

Chris

---

### Post by chili555 on 2017-01-17
It would help us soooo much more if you inserted the device, opened a terminal and ran:```
lsusb
```Post what the terminal says about your device. The usb.id, something like aabb:1235, is the key to everything.

---

### Post by heatopher2 on 2017-01-17
Hi, thanks for replying so fast, as ever with you guys!

So here's a screenshot of the terminal screen:

[ATTACH=CONFIG]273236[/ATTACH]

I assume it's 0bda:b720 ???

---

### Post by chili555 on 2017-01-17
You will need a temporary internet connection by tether, ethernet or whatever means possible. 

You may safely copy and paste these commands in the terminal. First, we install git:```
sudo apt-get update
sudo apt-get install git
```Now we download the driver:```
git clone https://github.com/lwfinger/rtl8723bu.git
```Now we compile and install it:```
cd rtl8723bu
make
sudo make install
sudo modprobe -v 8723bu

```Post back any errors or other snags.> I assume it's 0bda:b720 ???Exactly!

I will be away for about an hour. I will have one additional step.

---

### Post by heatopher2 on 2017-01-17
OK, great, thanks again. Don't worry, it'll take me a while to trail that wire downstairs. Take your time :p

---

### Post by chili555 on 2017-01-17
I'm baaaaack! And I'm ready for your good report.

---

### Post by heatopher2 on 2017-01-17
Hi, if you're back... Yes, that all seemed to work fine. I've copied the command line, just in case, but I had a prompt to connect to the wifi, in the normal way. I would have gone ahead and done that, but thought maybe I should wait for you to tell me whatever is left to do.

Is there anything that I need to do on the bluetooth side, by the way? Like I said, it seemed to be working already, but maybe there's some extra functionality that I didn't have yet.

Well, I couldn't wait any more. I'm writing this from inside Ubuntu (hoorah!), albeit with a slightly dodgy on-off connection; but not sure if that's just the crappy router, or if it's the last thing that you had to tell me :-|

---

### Post by chili555 on 2017-01-18
> albeit with a slightly dodgy on-off connection; but not sure if that's just the crappy router, or if it's the last thing that you had to tell me The last thing I had to tell you was that you've compiled the driver for your current kernel version only. When Update Manager installs a later linux-image, after the required reboot, you must re-compile:

```
cd rtl8723bu
make clean
make
sudo make install
sudo modprobe -v 8723bu
```Please retain the files and these instructions for that time. Glad it's working!

As for the router, you might check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Back in your computer, set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

I have no bluetooth suggestions. May I assume that it works as expected?

---

### Post by heatopher2 on 2017-01-18
Hi, firstly, yes, bluetooth seems to be fine fine fine. I've managed to connect two devices, without any apparent hitch.

Secondly, as for the update manager stuff, duly noted, but one question - do you mean whenever I upgrade to the next version of Ubuntu, or also more trivial updates? Stupid question, maybe?

I'm not sure about the router. It is a very basic one supplied by the ISP, and so probably not all that sophisticated. But I'll have a look at it later. 

Here's my output from that code.

kizza@HEATOPHER:~$ sudo iw reg get
[sudo] password for kizza: 
country GB: DFS-ETSI

(I haven't added the rest of the stuff from that output, in case it's sensitive somehow - is that important?)

So is that how it should be - isn't it? - showing 'GB' (which is correct, albeit I don't know for how much longer "Great Britain" will continue to exist with the political trajectory that we're currently on). Do I need to change anything? I assume not, but there are no stupid questions, right?

And finally, I've changed the iPv6 setting, as you said, so let's see :D

---

### Post by chili555 on 2017-01-18
>  there are no stupid questionsCorrect!> So is that how it should be - isn't it? - showing 'GB' (which is correctCorrect!> continue to exist with the political trajectory that we're currently onWe both live in very interesting times!!> do you mean whenever I upgrade to the next version of Ubuntu, or also more trivial updates?Trivial updates sometimes include a newer linux-image, more correctly known as kernel. For instance this command:```
uname -r
```...shows that I am currently on 4.8.0-34-generic. At some point in the future, Update Manager will offer to install a later version; 4.8.0-**35**-generic perhaps and, after doing so, request a reboot in order to complete the update. Your clue will be that your wireless no longer works after the reboot. Recompile as above and you'll be all set.

Questions? Concerns??

---

