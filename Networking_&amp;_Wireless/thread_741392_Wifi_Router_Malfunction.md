---
title: "Wifi Router Malfunction?"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by BruisedQuasar07 on 2008-03-31
Can anyone point me to a link that has an explanation of how to determine if your
wifi router\AP is malfunctioning and thereby the cause of suddenly inability of your
PCs connecting with internet? 

My well functioning LAN (Win XP & Win 2000pro and Linux Ubuntu, Xubuntu & Puppy)
suddenly will not work, not even a single Ethernet line to a single PC. I can find no reason. Everything appears to be connecting and functioning. Net Stumble shows wifi connecting, 100% signal strength etc. Yet I cannot connect to any Internet Servers.

Would appreciate any suggestions

-Bruised

---

### Post by pytheas22 on 2008-03-31
You should try rebooting your router if you haven't already, obviously.

You should also make sure that your connection to the outside world actually works--your machines may be connected to your router alright, but if your Internet connection is down for some reason, you won't be able to connect to anything outside your local network.  If you are able to ping local machines inside your network but not anything on the outside, there's a very good chance that this is the problem.

---

### Post by BruisedQuasar07 on 2008-04-01
Thank you for your reply. Yes, that was the first thing I did was try direct connect to my 
Cable Modem. The PC I use as my LAN server connects to internet fine but a laptop that I have dual booted, Win 2000 (Wifi) and Xubuntu (and Puppy live cd) (Wired Connection) I cannot get Internet even when I connect directly to my cable modem (that one puzzles me).

I have had to get my cable modem and LAN back up several times in the past but I have never been stumped  like this. 

As for resetting the Netgear router, I have considered it but I was concerned about
getting it set up again, since my server PC is completely Linux and my understanding is your router must be connected to the PC your cable modem was originally connected to.

Given I cannot get my laptop on Internet even when I direct Eth cable connect to the
cable modem, I've been reluctant to reboot the router. 

-Bruised

---

### Post by rustybronco on 2008-04-01
> **BruisedQuasar07 said:**
> 
As for resetting the Netgear router, I have considered it but I was concerned about
getting it set up again, since my server PC is completely Linux and my understanding is your router must be connected to the PC your cable modem was originally connected to.

Given I cannot get my laptop on Internet even when I direct Eth cable connect to the
cable modem, I've been reluctant to reboot the router. 
-BruisedI don't think there is any reason to do that.
can you post the output of...
lshw -C network
iwlist scan

---

### Post by kevdog on 2008-04-01
So just in summary

The wireless works, but the wired connection does not?

---

