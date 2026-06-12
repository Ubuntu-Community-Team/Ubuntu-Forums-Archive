---
title: "Problems With Att Dialup Configuration"
date: 2008-04-16
forum: Networking &amp; Wireless
---

### Post by scottslinux on 2008-04-16
I am setting up moms computer for dial up using her att formerly worldnet account. Kubuntu 7.10 and kppp. entering the user name and password in kppp and dialing in the deamon dies and this is the output.

Apr 15 21:27:39 scottslinux pppd[6218]: pppd 2.4.4 started by scott, uid 1000
Apr 15 21:27:39 scottslinux pppd[6218]: Using interface ppp0
Apr 15 21:27:39 scottslinux pppd[6218]: Connect: ppp0 <--> /dev/ttySHSF0
Apr 15 21:27:40 scottslinux pppd[6218]: CHAP authentication failed
Apr 15 21:27:40 scottslinux pppd[6218]: CHAP authentication failed
Apr 15 21:27:42 scottslinux pppd[6218]: Hangup (SIGHUP)
Apr 15 21:27:42 scottslinux pppd[6218]: Modem hangup
Apr 15 21:27:42 scottslinux pppd[6218]: Connection terminated.
Apr 15 21:27:42 scottslinux pppd[6218]: Exit.

I have entered the username and password in the chap-secrets file....no luck. any thoughts?
It seems from my surfing that this is a problem for many people. I payed to get them a dsl line but until that gets her I need to make this work.  THanks for any help you may be able to provide.

Scott

---

