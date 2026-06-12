---
title: "Getting wireless with a Belkin"
date: 2005-11-11
forum: Networking &amp; Wireless
---

### Post by natman on 2005-11-11
I know there are a lot wireless things in here sorry to add one more,

anyway i have belkin wireless 54 mbps 802.11g (part no. F5D7010 ) on brezzy, and wireless network network that work fine in windows. I have run "sudo iwconfig" it said i had no wireless connection.

Can anyone help?

---

### Post by spd106 on 2005-11-11
Have you installed ndiswrapper yet?

Start with the ndis-utils packages. I've read that the ndisgtk package is easy to use.

You will need the windows drivers that came on the disc. Both .inf and .sys files.

This wiki page might help [https://wiki.ubuntu.com/SetupNdiswrapperHowto?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/SetupNdiswrapperHowto?highlight=%28ndiswrapper%29)

Good luck

---

