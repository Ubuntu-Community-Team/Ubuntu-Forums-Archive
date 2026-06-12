---
title: "Belkin F9L1108-TG USB dongle"
date: 2014-05-04
forum: Networking &amp; Wireless
---

### Post by yoshimitsuspeed on 2014-05-04
I just installed 14.04 on a desktop and am trying to get a USB wifi dongle working. 
I have spent hours trying to make something work and am getting pretty burnt out. 

It's a Belkin F9L1108-TG. 
I cannot find jack for info on it specifically. Some threads say I need to run ndiswrapper. Others say I need to install additional linux drivers  such as rt2870sta. I tried this and believe I finally got a successful install after having many issues with make install throwing errors. Unfortunately most of the info I found on this is very outdated. Many of the links to downloads are broken and so on making me wonder if it's still a pertinent option? 

For ndiswrapper I don't have the install CD. They say to download the EXE and unwrap it to get the needed files but I cannot figure out how to do that. 
[http://ubuntuforums.org/showthread.php?t=1784691](http://ubuntuforums.org/showthread.php?t=1784691)


I hate to spend a lot more time on this not knowing which one is most likely to work or if they will work at all. 
What should I do?

---

### Post by QIII on 2014-05-04
Hello!

The following (*Please copy and paste in the terminal.  Even a small typo will render this useless.*) will download a script and create a text file in your home folder with wireless information -- and all sensitive information will be redacted to protect your privacy.  When it is done, click on the "paper clip" in the toolbar above the text input box and attach the netinfo.txt file that was created.

A couple of the people I know who are very good with this sort of thing are most likely asleep right now, but getting the information they need will be helpful

```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```

Be patient.  Remember that the community is world-wide and people live in all time zones.

Cheers!

---

### Post by yoshimitsuspeed on 2014-05-04
Thanks for the quick reply. 

[ATTACH]252828[/ATTACH]

---

### Post by varunendra on 2014-05-04
The script report you posted is incomplete. But looking at the device ID of the usb adapter, I suggest you try the solution suggested in this post : [http://ubuntuforums.org/showthread.php?t=2153777&p=12688576#post12688576](http://ubuntuforums.org/showthread.php?t=2153777&p=12688576#post12688576)

The card in the above linked thread was a different one, but the same driver (hence the same installation method) will work for your card too.

Try it, and post back if you get any errors. If not, let us know how well (or not) the driver performs.

---

### Post by yoshimitsuspeed on 2014-05-04
Wow quick responsive help that actually worked. This is a whole side of the ubuntu forums I am unfamiliar with haha. 
Thanks a lot guys. Rebboted and wifi is up and running.

---

### Post by varunendra on 2014-05-04
Please consider marking the thread as [SOLVED] then, using the "Thread Tools" link above the top post. :)

---

