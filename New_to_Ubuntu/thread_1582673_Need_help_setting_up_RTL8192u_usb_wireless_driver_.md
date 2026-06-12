---
title: "Need help setting up RTL8192u usb wireless driver (Realtek device)"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by Turtleman on 2010-09-26
Hey guys! I have a rtl8192u device from Realtek that is a wireless usb adapter. I plug it in and it doesn't work. So I tried looking around the net for drivers for that device for Ubuntu, but I didn't seem to find any. So I looked for a solution on Debian and I found a page on the Debian Wiki that contains the instructions and the driver:

[http://wiki.debian.org/rtl819x](http://wiki.debian.org/rtl819x)

Unfortunately, I'm not experienced enough with Ubuntu or Debian to follow the instructions correctly (I tried these instructions on a Debian install and a Ubuntu install). My questions are:

Is it possible to make the Debian packages/drivers for my device work in Ubuntu? And if yes, how can I do it? (If you know the answer, please explain in detail the procedure, I am a noob :P) If no, does anyone that has that device or similar knows an alternative method to get it working? :confused:

Funny how things are: I stayed away from Ubuntu because my intel video kept crashing ever since 9.04 and I could not fix it and it still crashed on 10.04! On 10.10 it stopped crashing, I was so happy to be able to use Ubuntu again, then I realized I couldn't make internet work in it haha. I hope I find a solution, I really don't wanna go back to Windows :).

Thanks a lot for your time!

---

### Post by spcwingo on 2010-09-26
I would try to install the firmware from the Debian repos.  To do that just plug your computer into your router via ethernet cable and issue these commands from a termial:

```
wget http://ftp.at.debian.org/debian-backports//pool/non-free/f/firmware-nonfree/firmware-realtek_0.24~bpo50+1_all.deb
```

followed by:

```
sudo dpkg -i ./firmware-realtek_0.24~bpo50+1_all.deb
```

finally:

```
sudo reboot
```

If for some reason installing the firmware doesn't work, you can uninstall it by issuing this command:

```
sudo apt-get remove --purge firmware-realtek_0.24~bpo50+1_all.deb
```

Let me know how it goes.  :)

---

### Post by lucaspr on 2011-02-28
I now this is an older thread, but I just wanted to thank you and confirm this as working (for me at least!)

So:  Thank you!  :)

Actually writing this with a wireless connection thanks to this thread! 

The firmware package is updated to 0.27 so the link isn't correct anymore, but it works great!
Here is a new link to the newer firmware package:

```

wget http://ftp.at.debian.org/debian-backports//pool/non-free/f/firmware-nonfree/firmware-realtek_0.27~bpo50+1_all.deb

```

---

### Post by spcwingo on 2011-02-28
> **lucaspr said:**
> I now this is an older thread, but I just wanted to thank you and confirm this as working (for me at least!)

So:  Thank you!  :)

Actually writing this with a wireless connection thanks to this thread! 

The firmware package is updated to 0.27 so the link isn't correct anymore, but it works great!
Here is a new link to the newer firmware package:

```

wget http://ftp.at.debian.org/debian-backports//pool/non-free/f/firmware-nonfree/firmware-realtek_0.27~bpo50+1_all.deb

```

No problem, bro.  I'm just glad to have helped someone.  :)

---

### Post by VpNKBQLjz0 on 2011-12-14
I registered just to say THANK YOU SO MUCH!!

After looking around stupidly for 2 days I finally found the answer to this question. I didn't even know what my little Realtek USBs factory number was... but this worked perfectly!

Thanks so much!

I had to use my brain though and replace the commands with the proper version numbers and then mess around with 1 or 2 other things but this worked flawlessly! I almost had a heart attack when I installed Ubuntu because my windows OS broke and I plugged this USB in and it didn't work...

Thanks so much. Power to Linux!

---

### Post by Turtleman on 2012-08-18
Hey again - nice to see that spcwingo's solution worked for you guys. I had actually switched computers back then so I didn't need my RTL8192u anymore, sorry if I didn't follow up in the thread. Thanks for posting a solution spcwingo! 

I have actually unboxed my old computer and now I'm running into a new problem installing the package - this is what my Terminal outputs to me:

```
Selecting previously unselected package firmware-realtek.
(Reading database ... 169183 files and directories currently installed.)
Unpacking firmware-realtek (from .../firmware-realtek_0.35~bpo60+1_all.deb) ...
dpkg: error processing /home/ricardo/Desktop/firmware-realtek_0.35~bpo60+1_all.deb (--install):
 trying to overwrite '/lib/firmware/RTL8192E/main.img', which is also in package linux-firmware 1.79
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/ricardo/Desktop/firmware-realtek_0.35~bpo60+1_all.deb

```

Can you anyone suggest a solution?

Thanks for your time!

Update: I removed firmware-linux and installed firmware-realtek to see if my device would work, but no go. I read the changelog of the .deb and apparently it does not support my device, so now I'm looking around for the correct driver. Will update if I find it. Any help is greatly appreciated!

---

