---
title: "wireless connection drops after a while and I have to reboot"
date: 2015-11-19
forum: Networking &amp; Wireless
---

### Post by mbk2 on 2015-11-19
I have ubuntu 15.04 64 bit and a iwlwifi driver.
When I switch my laptop on (Lenovo T530) the Wifi Network is found and I am connected, no prob.
After about ten minutes the connection to my WiFi gets disconnected and I can't re-establish it again. I have to reboot or use 
a cable.

I read thousands of posts and googled around but I didn't find the answer to my problem.
In my home we have several Android devices, a Windows computer and a Fedora 22 laptop - and they work fine. 
The newer loose the WiFi connection.

So I don't know where to look because everything what I did so far was useless :(
I did:

> lspci -knn |grep Net -A2
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo Device [17aa:21f3]
    Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation Centrino Ultimate-N 6300 [8086:4238] (rev 3e)
    Subsystem: Intel Corporation Centrino Ultimate-N 6300 3x3 AGN [8086:1111]
    Kernel driver in use: iwlwifi

I added in iwlwifi.conf the line
options iwlwifi 11n_disbale=0 (and 1)
but no results.

Would be nice if there is an existing solution.

---

### Post by jeremy31 on 2015-11-19
> **mbk2 said:**
> 
I added in iwlwifi.conf the line
options iwlwifi 11n_disbale=0 (and 1)


I hope that is just a typo, the line in iwlwifi.conf should be
```
options iwlwifi 11n_disable=
```

It is 0 by default, and if you already tried 1, then try 8 as it might help by enabling aggressive tx

Also check power management for wifi
```
iwconfig | grep -i power
```

If it doesn't help see [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) and post your wireless script results

---

### Post by mbk2 on 2015-11-19
the typo was only in the post
I tried 11n_disable=0 ; 1 and 8 but always the same. My WiFi connection drops after 5 minutes.

> iwconfig | grep -i power
eth0      no wireless extensions.

lo        no wireless extensions.

          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Power Management=off

I will try to attach the output of this script wireless.info (don't know how this works).
(the output is too big: look here for the output: [Wireless Info]("https://gist.github.com/mbk2/7388707d4d6e048af184"))

---

