---
title: "Need Archer T1U wireless USB connection help"
date: 2016-06-16
forum: Networking &amp; Wireless
---

### Post by bulazeem on 2016-06-16
Good evening,

I recently purchased an Archer T1U wireless usb adapter and after following the installation manual, got it to work with my computer.  Keep in mind that I'm a complete linux novice and so the installation process was just me copying and pasting lines from the manual with no understanding as to why or what was being accomplished :(
I'm currently running Lubuntu 14.04.4 LTS and here's the problem.  The device is installed but every time I reboot the computer, I have to type a bunch of commands into the terminal because the computer seems to forget everything.  So I have to put:

cd /home/george/Documents/Archer_T1U_V1_150909/Driver
sudo bash load.sh
sudo ifconfig ra0 up
sudo iwpriv ra0 set NetworkType=Infra
sudo iwpriv ra0 set AuthMode=WPA2PSK
sudo iwpriv ra0 set EncrypType=AES
sudo iwpriv ra0 set SSID="XXXXX"      Obviously replacing X's with pertinent info
sudo iwpriv ra0 set WPAPSK="XXXXX"
sudo iwpriv ra0 set SSID="XXXXX"
sudo iwpriv ra0 set WirelessMode=14
sudo iwpriv ra0 set SSID="XXXXX"
sudo iwconfig ra0
sudo dhclient ra0

Also, the device doesn't show up in the network manager at the bottom right taskbar so now when I click the icon, the option to enable my VPN is grayed out.
I'd appreciate it if anyone could explain how to resolve these issues (in the most basic of ways, sorry).

Thank you all for your time

---

### Post by bulazeem on 2016-06-19
In an attempt to try to make my experience better, I "upgraded" from lubuntu 14.04 to 16.04 and now I can't get internet working at all.  Not all of the driver files are being created during sudo make so then there's nothing to insert into the kernel (I think I said that right, sorry). I'm guessing that the problem is that the driver for the device found at [http://www.tp-link.com/en/download/Archer-T1U.html#Driver](http://www.tp-link.com/en/download/Archer-T1U.html#Driver) says that it's for Linux Kernel version 2.6~3.16.  What can I do to fix this issue (aside from waiting for a new release or replacing hardware)?  Are there alternative drivers that are known to work?  I've been using various version of ubuntu and lubuntu for a few years now (despite this I'm still quite ignorant of how to do things) and after all this struggle, I'm very tempted to purchase a copy of windows for my home PC.  I feel like I'm not just smart enough to keep using this OS. :(

Edit:  I now got it to behave in 16.04 the same way that it did in 14.04.  I have to load everything up each time I reboot but at least this works.  Is there no way I can make a script to do all of this automatically?  Or how about copy files to appropriate directories so that they're there each time I boot up the machine?  Please keep it basic and thank you.

---

### Post by cheetodust on 2016-08-23
Hey Im also very new to Linux. And also have the same usb dongle.
Quick question,  when you changed dir to the driver file.  Was it still zipped or did you use the archive manager to unzip it?

Thanks,
Cheetodust

---

### Post by cheetodust on 2016-08-23
Also did you get error messages when you used the "sudo bash load.sh" command?

---

### Post by bulazeem on 2016-09-15
Cheetodust, sorry for my super delayed response but I gave up on the problem since I could never make heads or tails of it.  I decided to take a look again, out of boredom and noticed that you wrote.  I had unzipped the files and no I did not get an error when I ran the command.  I ended up using the slower 2.4ghz built in chip instead of running the commands each time.  It's a computer that's mainly used by someone that's less tech savvy than I am (and I thought I knew nothing...) so I can't have something so difficult.  Just wanted to write back because I know it's frustrating when you see a dead thread and start wondering if the OP ever found a solution and didn't update the community or what.

---

### Post by Bucky Ball on 2016-09-16
As you are both new, one question, and you may think it's a silly one: did you actually plug the device in and test to see if it was recognised and up prior to going through all this??? Many wireless drivers are already in the kernel, not like Win where you need a 25 digit authentication key for every bit of hardware you want to use.

Generally, any Linux driver that comes packaged with a wireless device is all but useless. Have never wasted my time with one, if that's what you're doing.

Open a terminal, just one of you, the OP thanks, and post the output of this if you still want to find a fix. If not, I'll close the thread, as you've said yourself it is 'dead'. We can breath life into it for one more shot, though, if you like. :) Post the output of these two commands.

```
sudo lshw -C network
lsusb
```

Use code tags for the output (see green link in my signature).

@cheetodust: suggest you start a new thread of your own and include the output of the command above for a start (don't post it here, please). While your wireless dongle *might* be the same model, it would be guaranteed you are not using the same machine or hardware configuration. Just gets confusing trying to help two people on one thread.

Good luck.

---

### Post by bulazeem on 2016-09-16
Bucky Ball, thank you for your response and interest in my problem, but between responding to cheetodust and checking back here I found a solution at [http://askubuntu.com/a/819231](http://askubuntu.com/a/819231) .  It's a new post that was made just a couple of weeks ago and it's working perfectly for myself.  I hope this helps anyone else that has had problems with this particular usb dongle.  Strangely I need to have my wifi switch enabled for the usb dongle to work but speed tests indicate that it is indeed connected to the 5ghz network instead of the 2.4ghz band.  So if you follow that link and still have problems, make sure any hard switch is enabled and also make sure that you don't auto connect to the 2.4ghz band with any on board chip (just go ahead and forget it in your settings).  Thank you!

---

### Post by Bucky Ball on 2016-09-16
Good news, well done and please mark the thread as 'solved' to help others (Thread Tools, top right or see the link in my signature). Thanks for sharing the fix. We like that. :)

---

