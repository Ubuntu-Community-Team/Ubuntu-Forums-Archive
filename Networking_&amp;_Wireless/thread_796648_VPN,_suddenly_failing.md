---
title: "VPN, suddenly failing"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by Orestez on 2008-05-16
Right. Im connecting to an encrypted VPN (SwissVPN btw) and it worked well under hardy for some time. Occasionally I would get a 

VPN Connect Failure

Could not start the VPN connection 'swiss' due to a connection error.

VPN Connection failed

and in /var/log/messages it says

May 16 21:28:43 zerko pppd[9300]: Terminating on signal 15
May 16 21:28:43 zerko pppd[9300]: Child process /usr/sbin/pptp 83.253.80.28 --nolaunchpppd (pid 9301) terminated with signal 15
May 16 21:28:43 zerko pppd[9300]: Modem hangup
May 16 21:28:43 zerko pppd[9300]: Connection terminated.
May 16 21:28:43 zerko pppd[9300]: Exit.

After entering the password again it would work. Now its not working anymore at all. I know its not the configuration, because it worked before, and nothing has changed with my internet connection either. Anybody know what might be causing this?

---

