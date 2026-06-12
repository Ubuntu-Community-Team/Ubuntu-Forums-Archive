---
title: "Draytek N61 Wireless USB Adaptor"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by Radiobeamer on 2008-03-18
Hi All, I'm quite a newbie to Linux and Ubuntu.  I've installed Gutsy on an old Dell Inspiron 1100 without too many problems.  I've got a Draytek N61 USB wireless dongle and set out to get it working.  Yes, I know that it isn't on the supported list (it's quite new) but I had it anyway and Linux is about saving money, right?

So I figured out that it is based on the Ralink 2870 chip and that Ralink have a linux driver on their web site.  So far so good.  After a lot of work I managed to get all the dependencies together to make it compile.  The documentation tells you how to configure it for wifi access to your ssid etc.

Then I found that I need to get it running with insmod, ifconfig, and so on.  After doing these things it worked quite well.  I made a batch file (is that the correct linux term?) to get it running at first.  This works fine but you need to have root user rights.

The next challenge was to get it to connect up on boot.  I discovered how to make it load on boot etc by copying the driver executable into the correct place and modify the interfaces file.  This is a big improvement because I have an account for my 6 year old on the laptop and he can make it work by re-booting now.

One of the big advantages for the USB dongle is that we can prevent my 6 year old from internet access just by removing the dongle.  The next challenge is to get the dongle running again when it is plugged (back) in to the USB port.  Right now it seems that the driver is loaded but the wifi connection (ifconfig) is not established.  Once again I have to run a batch file.  So the question is ... how can I make this work automatically?  Can anybody explain this to me, as I have looked for this information for quite some time now?

Cheers, Paul

By the way - thanks for such a fantastic technical resource.  If anybody would like the detail of how I got the Draytek N61 to run (so far) then I will be happy to make a step-by-step write-up.  So far this story has taken many weeks and I've forgotten most of the detail by now, so it will just take a little time to re-construct.

---

### Post by i_hate_command_line on 2008-06-19
> **Radiobeamer said:**
> ... If anybody would like the detail of how I got the Draytek N61 to run (so far) then I will be happy to make a step-by-step write-up. ...
**@Radiobeamer**: As I have a N61 too and as I am a newbie to Linux command lines, I would really appreciate such a write-up. It would be really great, if you could write it dummy-proof (i.e., from the very start and with tiny steps). I was able to [find]("http://www.ralinktech.com/ralink/Home/Support/Linux.html") Linux drivers for the  "Ralink 2870", though. ;-) I found them thanks to your post and via [this]("http://ubuntuforums.org/showthread.php?t=683085&highlight=Ralink+2870") and [this]("https://answers.launchpad.net/ubuntu/+question/25507") forum.

---

