---
title: "Success with wireless Linksys wusb54g v4"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by enderal on 2008-08-28
[SIZE="3"]I'm writing this so that perhaps it will help others. I am new to linux as a personal OS and ubutu except for some experience on a shared server where I have some experience using the OS and command line.

It was a lot of work to get the wireless going but it was probably only a day or less total but seemed much more.

At first I was overwhelmed and after reading many posts I about gave up but I did accidently get the wireless working with the CD but it would not work on the hard drive. At least I knew there was hope.

I knew the network was there because I could ping it.

Kept plugging along feeling hopeless.

Succeeded in installing ndiswrapper and installing the driver with it. 

I was able to install ndiswrapper (after failed attempts using other means) from the CD using the command"sudo apt-get install ndiswrapper-common" I think I had to find the path and file and make changes accordingly.

At long last, finally saw a network.

Network was there but super slow and would not connect to the internet.

Then I read the sticky in this forum about ndiswrapper.
[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

There was indeed another driver taking up the network. Blacklisted it and everything works now.

Also, one of the posts said to uncheck roaming in the network dialog but things didn't work until checked it so maybe I beat my head for hours unnecessarily.

The signal is still weak but at least it works.

I'm posting this to help others with the same problem and it seems to be a common problem.

Don't know if I've been any help but at least you know it is possible to get it working.

Some of it has to do with getting the wireless network settings correct also. Using the System > Administration > Network Tools helps by using the Ping tool.

Anyway, hope this helps a little.

Onwards into more struggles!

(This is a long time dream of mine to start using linux!)[/SIZE]

---

### Post by caljohnsmith on 2008-08-29
> **enderal said:**
> 
Also, one of the posts said to uncheck roaming in the network dialog but things didn't work until checked it so maybe I beat my head for hours unnecessarily.

The signal is still weak but at least it works.

Just keep in mind that when you use the roaming mode, Ubuntu connects to whichever open wireless network it can find, which is not necessarily your own network (or the network you really want to use). That's probably why the signal is "weak"--you might be using someone else's network. I would recommend not using roaming mode, and then you can select which network you want to connect to. If you give more details about what problems you have when doing that, then maybe we can help you troubleshoot.

---

### Post by snowpine on 2008-08-29
Hi Enderal, I have the same model Linksys as you, and I also found it a bit frustrating when I switched over to Ubuntu. Like you, the solution that worked best for me was using ndiswrapper. 

Personally, I have had better luck using a network manager other than the default. The two that work best for me are called rutilt and wicd. I am pretty sure they are both in the standard repositories, so they are easy to install and test. Rutilt in particular is very beginner-friendly. Check it out!

---

