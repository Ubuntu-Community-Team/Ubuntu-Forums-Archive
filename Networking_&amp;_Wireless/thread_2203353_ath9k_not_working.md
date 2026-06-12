---
title: "ath9k not working"
date: 2014-02-03
forum: Networking &amp; Wireless
---

### Post by shankara2 on 2014-02-03
I have read through alot of postings to get my ath9k wireless card working. Research has shown the ath9k card is a bastard.  A search of ath9k + ubuntu (red hat, fedora, knoppix, puppy or gentoo) show complaints of this card not working.  Even The Dark Lord of Redmond has issues with this card working.

Rather than trying to get the ath9k card working, would not a usb wireless unit be a better option?

Has anyone had luck with a usb wireless unit?

Using Acer Aspire-V3-771 laptop with Xubuntu 12.04 LTS.

Thanks,
Shankara

---

### Post by chili555 on 2014-02-03
Although the title of this thread is 'ath9k not working' the real question is 'which USB wireless should I get.' There is about a thread a week on that question on this forum and I'd suggest a search. Here is an example: [http://ubuntuforums.org/showthread.php?t=2166676](http://ubuntuforums.org/showthread.php?t=2166676) 

As for your ath9k, have you tried the nohwcrypt=1 option? Have you tried compiling the backports version from kernel 3.13? Have you tried any settings in your router? For example, my Intel wireless does better with a fixed channel, 11 in my case, rather than auto channel. I'd probably also try disabling N.

---

### Post by shankara2 on 2014-02-04
have you tried the nohwcrypt=1 option? Have you tried compiling the backports version from kernel 3.13?

I tried all that and it made my problem worse.  Now my wireless card doesn't work.  Rather than continue to pull my hair out, I spent 20$ on a Belkin 150N usb wireless adaptor.  I now have internet.

thanks for the suggestions though

---

### Post by chili555 on 2014-02-04
And did you blacklist ath9k? If so,I believe you're all set.

---

