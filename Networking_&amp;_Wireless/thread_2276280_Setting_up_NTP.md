---
title: "Setting up NTP"
date: 2015-05-01
forum: Networking &amp; Wireless
---

### Post by chriso0258 on 2015-05-01
Hello,

I may be asked to set up an NTP server for our private networks which will consist of over 700 cameras, NVRs, etc. My initial research shows that Ubuntu could be set up as an NTP server. I'm sure there is a ton of sites explaining how to set this up, but I thought I'd drop a couple of questions here to save me some time.

1. Would you point me to a couple of resources you feel do a great job of explaining how to set this up, which might include pitfalls to avoid etc.
2. Would a desktop pc, say a Dell GX 745 with 2 GB RAM be sufficient for the task? I don't suppose (in my ignorance of course) than an NTP server would require a lot of horse power. If not, what hardware requirements would you suggest? I also have a Dell Poweredge 2850 server I could possibly use but I also don't want to over-kill.
3. Any other advice I should know in setting this up?

Thanks for you help.

---

### Post by SeijiSensei on 2015-05-01
You can run an NTP server on an i386.  It requires very few resources.

Install [Ubuntu Server]("http://cdimage.ubuntu.com/ubuntu-server/trusty/daily/20150218.1/") on the machine.  It only comes with text-based interface.  If you need a GUI, install the regular [Ubuntu desktop]("http://cdimage.ubuntu.com/releases/14.04.2/release/").

Now you can install the NTP server on either version with the commands:
```

sudo apt-get update
sudo apt-get install ntp

```
It will be configured to start automatically when the server is booted.  

That's pretty much all you need to do.  Set this up on the Ubuntu machine, then try it out with a Windows client.  Use the date/time setting application to select the Ubuntu box as your NTP server.  If it doesn't work as advertised, post back here, and we'll try to figure out why.

---

