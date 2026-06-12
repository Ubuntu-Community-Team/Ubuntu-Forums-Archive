---
title: "help installing new rtl8187 driver"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by Len666 on 2010-11-27
Hi,
I'm new here. I installed 10.10 on a HP G62 laptop. I use an Alfa USB wireless adapter based on the rtl8187L. I get a connection but no or almost no traffic possible.
I read some threads and suppose I need the newest rtl8187 driver.
I downloaded it and it is in my home folder.

Then I followed instructions from one of the threads.
In terminal:  
sudo apt-get install alien

Then I get: "Unable to locate package alien"

I tried switching directories but it's no show....

Please help.

Thanks, Len.

---

### Post by realzippy on 2010-11-27
Think you need to download & compile this driver:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187L](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187L)

Do not use "alien" which is a tool to convert rpm files (fedora/suse) for ubuntu/debian systems unless you have any other solution.
And welcome to UF !
Please run in terminal:

```
lspci | grep Wireless
```

and post the output to ensure type of wireless device...

---

### Post by Len666 on 2010-11-27
> **realzippy said:**
> 
Do not use "alien" which is a tool to convert rpm files (fedora/suse) for ubuntu/debian systems unless you have any other solution.
And welcome to UF !
Please run in terminal:

```
lspci | grep Wireless
```

and post the output to ensure type of wireless device...


Thanks for helping!
I got the right driver. I dl'd it with my Acer (windows) netbook and transferred it to my HP, it's in the home folder. 

I used lsusb | grep Wireless and it shows:
Bus 002 Device 005: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter

So, I'm all set to install.... (and pretty eager as well...)
What do I do now?

---

### Post by realzippy on 2010-11-27
...basically you have to unpack the file,copy it to e.g. your user's home folder and compile it,means open terminal,navigate to the unpacked file,run:

```
make
```

```
sudo make install
```

reboot & hope it works.
... maybe you have to install some tools for compiling;error messages will tell you.In this case,I suggest to get a LAN cable and plug the ubuntu computer to the internet,otherwise it might be a hassle to install those tools...

---

### Post by Len666 on 2010-11-27
> **realzippy said:**
> ...basically you have to unpack the file,copy it to e.g. your user's home folder and compile it,means open terminal,navigate to the unpacked file,run:

```
make
```

```
sudo make install
```

reboot & hope it works.
... maybe you have to install some tools for compiling;error messages will tell you.In this case,I suggest to get a LAN cable and plug the ubuntu computer to the internet,otherwise it might be a hassle to install those tools...

Geez, i feel like a little kid.](*,)
I started terminal.
I typed: dir [enter]
I see the document: rtl8187L_Linux_26.1040.0820.2010.release.tar.gz.
So I assume I navigated to the correct folder...

I do as you say: I type:  make [enter]
Then it says:
*** no targets specified and no makefile found. Stop.

I try the oder code you provided: sudo make install [enter]
then it says:
*** No rule to make target  'install' Stop.

What do I do wrong?

---

### Post by realzippy on 2010-11-27
..you have to unpack it first:


```
tar -xvzf rtl8187L_linux_26.1040.0820.2010.release.tar.gz
```

then navigate to unpacked folder:

```
cd rtl8187L_linux_26.1040.0820.2010.release
```


 Note that you can autocomplete filenames with "TAB",so just type e.g.:
**tar -xvzf rtl8**   then hit "TAB"

Then:
```
make
```      ....can take a while,be patient.
```
sudo make install
```

reboot & pray



*Geez, i feel like a little kid.*

...you posted in absolute beginner section,no need to feel guilty.

---

### Post by Len666 on 2010-11-27
Unpacking went ok, the make-command went ok, the sudo make went ok, I rebooted and.... no difference.

Well, it sure was a good try. Thanks for your time.
I will follow your advice and take the laptop to an internet cafe and use a cable. And see what difference it makes when the updating has been done.
Could you point me in the right direction here?

With wired internet in the RJ45 socket, what do I have to do to get the updating started? Everything you write will be studied and thoroughly followed !!!

Thanks again,
Len.

---

### Post by realzippy on 2010-11-27
...so the driver is installed.Thread solved.  ;-)

You suggested this particular driver;I do not know *if* it works with your USB adapter...thought you got this from some threads you read.
Suggest to read some Ubuntu Wlan basics 
or start a new thread:
"How to make Alpha WLAN USB XXX work in 10.10"

Will not have time for this until monday,but:
I have a ALPHA 36H (do not remember exactly the name) back from the days
testing own WLAN security;it worked with the penetrating-patched realtek drivers in those *special* linux distributions like Nubuntu,Backtrack perfectly,in normal ubuntu realtek drivers are known to be buggy/tricky..may someone correct me....maybe your USB device is not the best for daily/normal usage.If you want to test your network,run backtrack...
Anyway,which ALPHA USB is it?If it has the same chipset as mine (forgot),
I can test this here monday/tuesday.
Recommend some googling: realtek8187 maverick..

---

### Post by beew on 2010-11-27
Are you sure you need to go through all that? I use rtl8187 driver for my usb wireless card and it works out of the box.

However, since you are using a usb card as well, you should make sure that the driver for the internal card has been blacklisted or the rtl8187 wouldn't be used. In my case the internal card is damaged and it uses the ipw2200 driver, so I have to blacklist it first or Ubuntu would give pirority to the internal card. When it did that it showed connected but I couldn't get online, similar to what you described here.

To see which driver is being used, click the network manager icon and look at "connection information".

---

