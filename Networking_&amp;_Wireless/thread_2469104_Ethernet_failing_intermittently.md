---
title: "Ethernet failing intermittently"
date: 2021-11-19
forum: Networking &amp; Wireless
---

### Post by phoenix-anna on 2021-11-19
The Ethernet connection on my Linux Ubuntu desktop machine fails intermittently. The manufacturer says that it is a software problem. Is there anything that could cause the OS to fail to function with Ethernet intermittently?

---

### Post by TheFu on 2021-11-20
> **phoenix-anna said:**
> The Ethernet connection on my Linux Ubuntu desktop machine fails intermittently. The manufacturer says that it is a software problem. Is there anything that could cause the OS to fail to function with Ethernet intermittently?

Is that really the best question?

The most likely problem is hardware or the driver.

Hardware could be the NIC, cable, switch, switch port. Have you checked all of those?  I had a NIC that dropped packets, so I disabled it in the bios and put in a cheapo $10 NIC which didn't perform great, but it didn't drop any packets.  Eventually, I replaced that cheap NIC with a quality NIC that tests at 940Mbps for each port.

Drivers for some NICs are pretty bad.  One extremely popular brand likes to ship the same driver to be used across 40+ different chips. At least we can see the revision levels in the hardware output to know.  For example, I had one of those rev: 0C  ... which seemed to have more issues. Some revisions didn't work with the expected drivers and people had to manually downgrade to an older, specific, driver.

Sometimes, especially on laptops, the driver may try to save power by turning off the connection after a few minutes without use. End-users often don't realize this. There is usually a driver setting to prevent that and sometimes it is possible to prevent it based on wall power or battery power.  Whether that is possible depends on the driver and the hardware.

The best way to get help would be to provide exact, correct, facts, about the OS, release, driver, and hardware details.  Many other threads here have the commands requested to capture that information.  Which should be run depends on information that hasn't been provided yet.

---

### Post by phoenix-anna on 2021-12-04
It would be helpful to know that names of the utilities that I should use to obtain the needed information.

It appears that the cable may have been at fault.

---

### Post by TheFu on 2021-12-04
> **phoenix-anna said:**
> It would be helpful to know that names of the utilities that I should use to obtain the needed information.

It appears that the cable may have been at fault.

We never know the linux experience level of the poster. I typically drop notifications about thread updates after a week of no response. Lots of people find the answer, but never provide any feedback here.

In THIS subforum, there is a sticky thread at the top: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) with some steps to gather information.

[https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) is an article about basic Linux network troubleshooting. It has a few commands.  There are many others on the internet. There are 50 different ways to get helpful information.

If you do SOLVE this, please update this thread with the root cause, the solution and use the Thread Tools button at the top of the page to specifically mark it as "SOLVED". That helps other members in the community seeking answers.

---

