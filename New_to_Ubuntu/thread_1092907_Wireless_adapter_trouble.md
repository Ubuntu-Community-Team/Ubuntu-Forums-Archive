---
title: "Wireless adapter trouble"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by sbelz79 on 2009-03-10
I'm just getting started with Ubuntu, and I'm having some difficulty getting my wireless adapter to work at full capacity.  When I run WinXP Pro I usually get around 84% signal strength, but when I boot up in Ubuntu (on the same machine, different hard drive), my signal strength is anywhere from about 60% to as low as 10%.
My adapter is a Linksys WMP54G.  Does anyone have any suggestions as to how to solve this problem.  I'm considering installing NDSwrapper 1.54 and then installing the driver for the device within Linux, but am wondering if there are any other ways of fixing this problem.

Please keep in mind that I'm a total newbie when it comes to using Linux (I've used WIN most of my life), so feel free to phrase any suggestions as if you were giving them to a small child.

---

### Post by beno1990 on 2009-03-10
Try this:

```

sudo apt-get install wavemon

```

Then in the terminal, type wavemon.

If the signa-to-noise ratio is above about 45dB, your signal is fine.

Linux and Windows have different ways of calculating signal strength so it can report different percentages.

---

### Post by sbelz79 on 2009-03-11
> **beno1990 said:**
> Try this:

```

sudo apt-get install wavemon

```

Then in the terminal, type wavemon.

If the signa-to-noise ratio is above about 45dB, your signal is fine.

Linux and Windows have different ways of calculating signal strength so it can report different percentages.
Thanks!  That was easy enough.  But while the Signal to noise ratio is at about +195, the link quality is hovering between 10/100 and 30/100.  Plus the the speeds with which files download and web pages load are noticeably slower when I'm running Ubuntu than when I'm running Windows.

---

### Post by 3rdalbum on 2009-03-11
You might need to compile the latest wireless driver for the chipset. I believe those things use a RaLink chipset - try the terminal command "sudo lspci" or "sudo lsusb" to find out for sure. If you can find the project that creates the drivers for those wireless chipsets, then you can download and compile the latest version which should hopefully fix the problem.

---

