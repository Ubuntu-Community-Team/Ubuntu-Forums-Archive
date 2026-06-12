---
title: "Fresh install: Wireless worked yesterday, but not today"
date: 2008-01-31
forum: Networking &amp; Wireless
---

### Post by PureW on 2008-01-31
Hello, I installed Ubuntu 7.10 yesterday on an Acer Aspire 5003WLMi
and I have enabled the "Firmware for Broadcom 43xx chipset family"
under proprietary drivers. It worked flawless and I could connect without 
a problem.
But today I can't even see any of the wireless networks that was visible 
yesterday. 
I have been googling around and it seems I'm not alone, but I can't find
any fixes for this?

"sudo iwlist scan" returns "No scan results"

/etc/network/interfaces:
auto lo
iface lo inet loopback

---

### Post by PureW on 2008-01-31
Could this be a bug in Ubuntu? I have read about other people having this problem with
the wireless working after a fresh install only to die after a day or two.

---

### Post by lungdart on 2008-01-31
I have had problems with my Broadcom card kicking out at what seemed to be a random basis, many hours apart as to make it inconveniently hard to test. However a system restart always brings my network connection back. Also my interfaces file still has all of my information and iwconfig still lists my card as a wireless device.

One of the things that helped me with Fiesty in the bast was to remove network-manager; the wireless manager that sits in your system tray. I found it flakey back then, and have removed it right off the bat of a fresh install since. I manually configure my network with ifconfig/iwconfig and /etc/network/interfaces.

If you dont want to try removing it, you can disable it in the gnome session startup section. Then configure normally.

---

### Post by PureW on 2008-02-01
> **lungdart said:**
> I have had problems with my Broadcom card kicking out at what seemed to be a random basis, many hours apart as to make it inconveniently hard to test. However a system restart always brings my network connection back. 

The problem is that restarting doesn't work. It worked for a day after the fresh install, but since then it's dead. No wireless networks are found.

---

### Post by Cadmus on 2008-02-01
I'm in the same boat, I can't seem to get anything to come up, which is infuriating as it has been working.

---

### Post by PureW on 2008-02-01
> **Cadmus said:**
> I'm in the same boat, I can't seem to get anything to come up, which is infuriating as it has been working.

I'll reinstall windows on the laptop for now. I've switched to Ubuntu on my stationary but the  laptop is needed too.

---

### Post by Cadmus on 2008-02-02
My post was a little short. I'll try and be a bit more complete here.

Installed Gutsy on my main computer, which uses wireless. Using ethernet briefly I was able to download the restricted driver for my card (Asus WL-138G V2) and thins seemed ok. Well once I'd moved it back to my desk it stopped behaving. Thinking it might be a range issue I moved the DSL router into my room and ti seemed to pick it up, moved the router back and I could still see it. Tried again the next morning and nothing's working, looked on here for the manual instructions but couldn't seem to find the right driver to use with the supllicant so re-installed network manager, not been able to get through to my router again.

---

### Post by Jay Jay on 2008-02-02
Only a couple of days ago I experienced this too, all of a sudden I couldn't connect to my preferred router, no matter which strategy I used. 

From Terminal the router appeared If I typed in: Iwlist scanning, but the OS was unable to connect.  Eventually I was able to get back online by re-editing my interfaces file, but this only lasted a few hours and then the problem returned. It wasn't the router because when I logged into Windows there was an automatic and perfect connection.

In the end I was forced to reinstall and the issue seems to have gone away, for now...

---

### Post by Cadmus on 2008-02-03
I've never had to (touch wood) reinstall an operating system due to a configuration mess-up, and I have no intention to start now :)

The question we need to answer is what was in your fresh install that made it work that we are missing (or vice versa).

---

### Post by ngreimel on 2008-02-03
I am having a similar problem... I have a dual-boot setup, and I hadn't been using Ubuntu for a while. Yesterday I booted Ubuntu and applied a bunch of updates (unfortunately, I don't know which). It did ask me to restart, but I had some work to do and did not restart til this morning. I had no problems the rest of the night, but this morning and I have had nonstop wireless issues. What usually happens is I can connect initially, but after a while I lose my connection and I have to restart networking to get it back. On a different computer (different network too), same problem!

How can I find out which updates I just applied and undo them?

---

### Post by Cadmus on 2008-02-04
I did manage to get wireless connectivity after doing a full update on my machine (last Tuesday (31st)  just after a new install), so whatever it is it's not consistent, otherwise I would have lost wireless immediately.

---

### Post by PureW on 2008-02-04
> **Cadmus said:**
> I've never had to (touch wood) reinstall an operating system due to a configuration mess-up, and I have no intention to start now :)

The question we need to answer is what was in your fresh install that made it work that we are missing (or vice versa).

Today I can see the wireless networks again in ubuntu, but I can't seem to connect. I get to the part where I can enter the password but it does not connect even though I know I'm using the correct password. (WPA-PSK/WPA2-PSK encryption it says in the router).

Is there any log to look at so I at least know what's wrong?

---

### Post by Cadmus on 2008-02-04
Just to add where I'm at, I know the hardware is working on some level, as I can see networks in the drop-down, but typing in the WPA key (and it is WPA, not WPA2) and leaving the Network Manager doesn't seem to give any sort of connection (tested by trying to ping the ip of the router).

---

### Post by ounas on 2008-02-04
Had lot's of problems with network-manager after upgrading.
So removed it, and installed madwifi and wicd.
All working now, try it it may work for you.

:)

---

### Post by PureW on 2008-02-05
**I have identified the problem!**

When the laptop's lid is closed, it enters hibernate mode or the other powersaving mode.
When it wakes up the network manager tries to reconnect to the network, **but** it tries to connect with WPA1 instead of WPA2 encryption!

I must manually pick WPA2-encryption in the passphrase-window.

Perhaps there is a bug in how the network-manager reads the SSID?

---

### Post by punkybouy on 2008-02-05
I had some similar wireless issues in Dapper which I fixed by using a static IP address instead of trying to use DHCP.  Give that a try.

---

### Post by Jay Jay on 2008-02-06
> Perhaps there is a bug in how the network-manager reads the SSID?

it does seem that way, many users including myself have found that removing Network Manager and using the Terminal instead provides better wireless connectivity. This has been discussed at length elsewhere on the forum. 

If you haven't done so already, I suggest that you check out the following links, they've worked for me in the past...

**[How To: Manual Network Configuration without the need for Network Manager]("http://ubuntuforums.org/showthread.php?t=571188")**

[B][URL="https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide"]WifiDocs/WirelessTroubleshootingGuide
[/URL][/B]

---

