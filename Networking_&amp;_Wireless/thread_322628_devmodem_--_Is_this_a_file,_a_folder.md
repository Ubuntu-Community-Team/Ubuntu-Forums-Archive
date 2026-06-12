---
title: "/dev/modem -- Is this a file, a folder?"
date: 2006-12-20
forum: Networking &amp; Wireless
---

### Post by Mark_in_Hollywood on 2006-12-20
For months and months my Dapper, using WvDial only, not GnomePPP, dials into my isp, sometmes I am up and running OK, othertimes, not. I get an intermittent connection.

I can listen to the modem while it is hooked up without disturbing the connection (there is no microphone), and I hear what seems to be an attempt at handshaking over and over, when the pppd or wvdial has died. Othertimes, I just get the dialtone. It's nuts. It's been like this since Hoary, then Breezy and now Dapper.

What is the relationship between all the files? Does sudo somehow get lost after 10 minutes, but PPPD forgets to see if it's running under sudo sometimes, or does WvDial look at PPPD and think it's 10 minutes are up and is waiting for a kernel call or some nutty thing like that?

Cogent experts as Linmodems.org have seen the scanModem output and said the modem isn't the problem. The windows side of the disk, never has a problem (nuts!), so I know it isn't the phone line.

Please don't suggest DSL, etc., I'm not paying that much. I only use the 'net 1 or 2 hours a day, I just get tired of having to reboot to get the modem/software/OS back to normal 3, 4, 5 times a day to see the email.

---

