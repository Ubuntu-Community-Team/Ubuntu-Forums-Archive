---
title: "[SOLVED] Wireless card sleeps after approximately an hour"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by ccbristo on 2008-08-26
Hi all,

I have recently installed ubuntu server (8.04 LTS) on an old compaq desktop.  It is mainly used as an ssh server to transfer documents between home and work.  Since it is in another room from the router/modem, it is connected via wireless.  It looks like the wireless card is being put to sleep after approximately an hour of inactivity (the time period is kind of a guess).  I can see from dmesg that it appears that the wireless is being deauthenticated:

me@machine:~$ dmesg | grep wlan0
[74767.794902] wlan0: RX deauthentication from {AP} (reason=7)
[74767.794929] wlan0: deauthenticated
[74767.797381] wlan0: RX deauthentication from {AP} (reason=7)
[74768.792605] wlan0: authenticate with AP {AP}
[74768.794308] wlan0: RX authentication from {AP} (alg=0 transaction=2 status=0)
[74768.794332] wlan0: authenticated
[74768.794341] wlan0: associate with AP  {AP}
[74768.796473] wlan0: authentication frame received from 00:12:17:b0:3f:15, but not in authenticate state - ignored
[74768.800621] wlan0: RX ReassocResp from  {AP} (capab=0x411 status=0 aid=3)
[74768.800646] wlan0: associated

The last 7 lines (I suspect) are me coming in an physically accessing the machine, thus awakening the wireless.  I am unable to ssh to the machine until I physically access it.  Once that is done, I can ssh to it again.

This is what happens when I try to set the power parameters via iwconfig:

me@machine:~$ sudo iwconfig wlan0 power off
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.

The card is a linksys WMP54G, using the wext driver.

Here is the relevant line from lspci:

01:09.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

Any information on how I can tell ubuntu to never put the wireless to sleep (or get iwconfig to do it) would be greatly appreciated.

My other option is to train the cat to type on the keyboard at least once per hour.

---

### Post by ccbristo on 2008-08-27
My newest idea is to create a cron job to ping the router every half hour or so.  I'll post in the morning about whether this helps or not in case someone else is having this problem.

---

### Post by ccbristo on 2008-08-28
In case anyone is wondering, the cron job did the trick.  Obviously, it is non-ideal, but it'll work.

---

