---
title: "Wireless network disappeared"
date: 2008-03-12
forum: Networking &amp; Wireless
---

### Post by enwr0003@hotmail.com on 2008-03-12
So here's the scoop.  I have an IBM Thinkpad T42p, with an Intel Pro Wireless 2100 802.11b  card.  I did a clean install of Ubuntu 7.10 Gutsy Gibbon on it removing Windows.  For the first two days things went great with my home wireless network.  However, late last night the wireless icon disappeared and I cannot get any wireless networks to even show up.  Manual network configuration also does not help.  I am very new to Ubuntu and could use some serious help if anyone has any solutions.  I do not want to go back to Windows!  Thank you, enwr0003

---

### Post by Bubba64 on 2008-03-12
This is a standard question have you tried rebooting a couple of times occasionally, and have you looked at the network stuff from administrative via system, and are you letting it roam or are set up on your own personal router.

---

### Post by enwr0003@hotmail.com on 2008-03-12
Thanks for the quick reply to my thread.  I have been rebooting my T42p many times since reading your reply and still nothing.  I haven't tried anywhere else because my home network works on my other laptop so well, MacBook Pro.  There seem to be a lot of posts about this problem, but none of them seem to be helpful to my situation. I even tried using an externl LinkSys wifi card and still nothing.  This is driving me crazy.

---

### Post by enwr0003@hotmail.com on 2008-03-12
Here's a little more info... I opened a terminal and entered 'sudo iwconfig' and got this as a result:

lo                   no wireless extensions.

eth2               no wireless extensions.

eth1               unassociated   ESSID:off/any  Nickname:"ipw2100"
                      Mode:Managed    Channel=0   Access Point:  Not-Associated
                      Bit Rate:0 kb/s     Tx-Power:16 dBm
                      Retry short limit:7    RTS  thr:off     Fragment  thr:off
                      Encryption  key:off
                      Power Management:off
                      Link Quality:0  Signal level:0  Noise level:0
                      Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
                      Tx excessive retries:0  Invalid misc:3   Missed beacon:0

irda0              no wireless extensions.


Don't know if this helps, but I have been trying tips from other forums and this was one tip.  Thanks!

---

