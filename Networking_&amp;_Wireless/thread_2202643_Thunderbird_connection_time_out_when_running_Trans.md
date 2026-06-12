---
title: "Thunderbird connection time out when running Transmission"
date: 2014-01-30
forum: Networking &amp; Wireless
---

### Post by broadcd on 2014-01-30
I believe this is the right sub-forum for this question:

When I have Transmission bittorrent client running Thunderbird cannot connect to imap servers for either Gmail or Outlook (those are the 2 emails I use, so I haven't tested any more)  It tries to connect for a while then times out.  If Transmission is not running then Thunderbird connects to both within seconds.  I have alternative download times set on transmission to download overnight when my ISP has free bandwidth, so when I am checking my email it often has no uploads or downloads going.  I am relatively new to linux having switched from xp a few months ago, so I am not familiar enough with command line commands to troubleshoot it on my own.

I am running Lubuntu 13.10.  I have forwarded port 52125 on my router for bittorrent.  Let me know if you need any more relevant information.

Any help would be appreciated.

---

### Post by broadcd on 2014-01-31
Anyone have any ideas where to start?  Is this in the right sub-forum?

---

### Post by frankmorris2 on 2014-01-31
Hello,

I am not a Bit-torrent specialist, but I can tell you that sometimes Bit-torrent clients can generate a heavy traffic on your workstation. You should probably make some tests with the download speed. On a typical Bit-torrent client, it is possible to restrict the download speed. This should help diagnose your time out problem.

Have a nice day.

---

### Post by chili555 on 2014-01-31
> **frankmorris2 said:**
> Hello,

I am not a Bit-torrent specialist, but I can tell you that sometimes Bit-torrent clients can generate a heavy traffic on your workstation. You should probably make some tests with the download speed. On a typical Bit-torrent client, it is possible to restrict the download speed. This should help diagnose your time out problem.

Have a nice day.Exactly. Unless you tell it not to, Transmission will use almost *all* of your bandwidth. It has two settings that help. Under Edit > Preferences > Speed you can set restrictions on bandwidth generally and at specific times. For example, you might restrict download and upload speeds to 100 kB/s during the daytime and allow 500 kB/s when you are sleeping.

---

### Post by broadcd on 2014-01-31
Thanks for the replies.  I may not have been clear in my original post, but the problem presents itself even when I have my uploads and download speeds set to 0kb/s.  My ISP has free bandwidth between 2-9am so I have it set to only download then, but i'll leave the program running in the background when it's not downloading

Anyways, the power at my house blinked and reset my computer now the problem has gone away for now.  The inability to connect to imap servers seems to just pop up every now and then and seems to be connected to Transmission being open or not, but sometimes it works... I just got frustrated and finally posted about it because I couldn't find a solution.  I think I may have to switch email programs, thunderbird seems to be kinda finicky on Linux.

---

### Post by SeijiSensei on 2014-01-31
Trust me, as someone who has used Thunderbird since its beta days, it works just fine on Linux.  Whatever problems you're having are very unlikely to be the result of Thunderbird acting up.

---

