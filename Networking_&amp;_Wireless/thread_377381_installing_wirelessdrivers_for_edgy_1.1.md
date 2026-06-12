---
title: "installing wirelessdrivers for edgy 1.1"
date: 2007-03-06
forum: Networking &amp; Wireless
---

### Post by the.eagle on 2007-03-06
Hello all
650
       I am still having a lot of trouble installing the drivers for a D-Link G650 wireless card. I keep getting errors, and all the help files seem to differ slightly, so it is not easy for a novice.Can someone give me the complete strings to un-install the native drivers and install the windows drivers, INCLUDING the location of the saved files instead of saying ' save to a folder'. Does anyone understand a novice? Thanx in advance....:)

---

### Post by zanglang on 2007-03-06
(Why would you want to remove the original driver? :p)

Edit: Just realized i've answered your first question in the other thread.

Try extracting the files to your Home folder, and then open your console, directly type in the command 'sudo ndiswrapper -i <name of .inf file>'.

Look here for detailed instructions:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

