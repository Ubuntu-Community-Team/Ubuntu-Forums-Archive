---
title: "thunderbird's about:config and security"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by minsf on 2009-04-10
hi, need some help with Thuderbird's about:config (that is Edit>Preferences>Advanced>General>ConfigEditor)

first if you have a good reference for beginners regarding about:config, please dont be shy to share... LOL

next, i know that I need mailnews.mesage_display.disable_remote_image to have a value of true, and javascript.allow.mailnews to have a false value. but i can see other java/javascript values which are true, such as javascript.enabled. is this going to pose any security problem?

finally, i'm trying to configure it for my gmail account. what is the difference between TLS and SSL (configuring the outgoing server smtp.gmail.com)? i want to use Tor, so i guess i need it to be very well encrypted, so that the Tor exit node cannot read my mail and password.
what does the "use secure authentication" option for the incoming mail server mean? i cannot get gmail to work with secure authentication yet... does this mean that my password can be seen at the exit node?

any other security advice for a thunderbird-newbie wil be greatly appreciated.

PS i installed it via "sudo apt-get install thunderbird thunderbird-gnome-support". version is 2.0.0.21.

---

### Post by cariboo on 2009-04-10
I've been using Thunderbird since it was in beta and have never needed to change any of the defaults. I have 3 email addreses, plus I forward email from Gmail to one of my accounts.

Between my ISP and Thunderbird's junk filter, I've never felt the need to do any more.

Jim

---

### Post by raymondh on 2009-04-10
I use thunderbird and gmail (IMAP).  Cariboo has a point.  The filters are good.  Nevertheless, to configure gmail in thunderbird .... open gmail>settings>forwarding pop/imap.  You'll see recommended instructions/configuration instructions to set up thunderbird.

Enjoy

---

