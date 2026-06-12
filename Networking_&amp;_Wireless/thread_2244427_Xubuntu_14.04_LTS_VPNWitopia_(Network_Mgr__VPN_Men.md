---
title: "Xubuntu 14.04 LTS VPN/Witopia (Network Mgr / VPN Menu)"
date: 2014-09-16
forum: Networking &amp; Wireless
---

### Post by Nagi_Mani on 2014-09-16
Using **XU** 14.04 LTS on an Asus EeePC 1015PX (high-perf netbook)
Previously / successfuly used Witopia on the same 1015PX w/ **U** 12.04 LTS - worked very well.
**(U** = Ubuntu;  XU = Xubuntu)

Problem:  
VPN Menu not updated after network manager installed (prevents VPN setup completion)

After using the command line* **sudo apt-get install network-manager-vpnc -y **, the VPN menu should include the **IPSEC **option, but it doesn't.  That menu still shows only the default options of Confgiure VPN and Disconnect VPN.

**per Witopia instructions @:  [https://www.witopia.net/support/setting-up-and-using-your-vpn/ubuntu-linux-ipsec-setup/](https://www.witopia.net/support/setting-up-and-using-your-vpn/ubuntu-linux-ipsec-setup/)*

Without that added menu option of IPSEC, VPN setup can't be completed.  Full stop.

/

It's worth mentioning that *Witopia VPN worked perfectly in my original install of **U** 12.04 LTS* when it first came out.  But then, during the past ten days +/-, I accepted the most *recent updates to **U** 12.04 LTS*.  Doom on me:  that update process stalled, then hard-crashed my system.  So I then fresh reinstalled **U** 12.04.  That *install* succeeded, but it produced the same result when attempting to setup Witopia - no VPN menu change to reflect an IPSEC option.  So then I resorted to a fresh install of **U** 14.04 LTS.  No dice.  Same result in re: Witopia - no VPN menu change to reflect an IPSEC option.

After that... process, I opted for a fresh install of XU 14.04 LTS, because it was allegedly light-weight in resource usage, the only current U-version that I hadn't tried... and hadn't crashed my system.  So far, **XU** 14 is working perfectly overall, with the single exception of this network manager / VPN issue.

I have looked for a solution on my own  - no joy.  That includes what I've been able to see on forums here and elsewhere.  It also includes Witopia tech support.  On that count, after 15 hours of online tech-chat with Witopia over the past week, they've decided that the problem is:
1 - Ubuntu 12.04 LTS related, _*after*_ the most recent barrage of updates thereto (the past 10 days in particular)
2 - Ubuntu 14.04 LTS related
3 - Xubuntu 14.04 LTS related
4 - repository related
5 - er sumpin...

Current Status:
I have not attempted to reverse / un-install the network manager cited above.  In fact, I'm leaving the system alone so I don't add my own stupid pet tricks to the problem.  Everything else about the fresh XU 14.04 LTS install s-e-e-m-s as though it functions well on the Asus EeePc 1015PX.

Thanks in advance to anyone who wants to take a run at this network manager / VPN issue, cuz I'm just plain burned out trying to find a fix.

Nagi

---

### Post by Nagi_Mani on 2014-09-23
POSSIBLY SOLVED:

**After today's (14.09.23) kernel update, a new sub-menu has appeared in the VPN pull down menu** which allows completion of VPN setup.  Witopia has been advised accordingly.   **Image of the "new" Sub-Menu follows:**

/Message Ends/

---

