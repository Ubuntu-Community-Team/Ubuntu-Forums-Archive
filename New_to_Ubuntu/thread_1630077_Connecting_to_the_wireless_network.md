---
title: "Connecting to the wireless network"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by Architor on 2010-11-24
Hello members of ubuntoforums.org,

I just installed Ubuntu 10.04 today with the Windows installer and I cannot connect to the internet. I tried using this command line:

sudo lshw -C network

And I got 'Unclaimed' as a result, which means that there's no driver loaded. I found all this on [this]("https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-ndiswrapper") website. This is what the website tells me that I have to do:

1. Obtain the Windows Driver for your system and locate the file that ends with .inf.

2. Install the ndisgtk package.

3. Open ndisgtk (System &#8594; Administration &#8594; Windows Wireless Drivers).

4. Select Install new driver.

5. Choose the location of your Windows .inf file and click Install.

6. Click OK.

But how do I do this without an internet connection? Which files do I have to download? How do I get them on my Ubuntu system? I have a Broadcom 43255, and I can go on the internet with my Windows 7 system on the same computer.

Please note that I have no experience with Ubuntu, I am an absolute beginner.

Thanks in advance,
Architor

---

### Post by wojox on 2010-11-25
Hook up an Ethernet cable and run

```
sudo apt-get update && sudo apt-get upgrade
```

Then look in Hardware Drivers for a driver to activate.

---

### Post by Architor on 2010-11-27
Thanks for replying. Running that command fixed it. Thank you very much!

---

