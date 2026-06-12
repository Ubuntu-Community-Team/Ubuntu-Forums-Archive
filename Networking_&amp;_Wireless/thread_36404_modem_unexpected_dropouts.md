---
title: "modem unexpected dropouts"
date: 2005-05-23
forum: Networking &amp; Wireless
---

### Post by Gunther_oz on 2005-05-23
After using Linux for a total of 3 hours I was quite happy to have been able to install software, mount my windows partitions on boot, etc...but I still have one issue left to sort out in regards to my dialup connection.

I use a D-Link external 56k modem (DFM-562E) which I bought after I gave up on my cheapo internal modem. I could connect through Admin...--> Networking but I got reduced speeds. After reading some forum threads I set up a connection through a terminal using PPP and reduced my modem speed from 115200 to 56700, causing the 1k/s to 5k/s jump. I was happy temporarily.

Now, I can connect fine with sudo pon and download quickly, but my connection unexpectedly tends to die every 20 minutes or so. I have checked through some of the config files in /etc/ppp but I'm not really sure what I'm looking for.

Has anyone else had similar problems or would be able to point me in the right direction?

---

### Post by xxfrankxx on 2005-05-28
I have a similar problem with a smartlink internal modem, here is what i posted:

> I installed the modules as described here:
[http://ubuntuforums.org/showpost.ph...56&postcount=34](http://ubuntuforums.org/showpost.ph...56&postcount=34)
It works but it hangs up very often, sometimes just in the first minute of connection.
I don't think it is a phone line problem since in windows it does not happen.

Does someone experience the same problem?
Any suggestion?
frank

---

