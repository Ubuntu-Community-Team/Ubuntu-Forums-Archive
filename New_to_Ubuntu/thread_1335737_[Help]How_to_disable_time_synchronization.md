---
title: "[Help]How to disable time synchronization?"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by Madel on 2009-11-23
How can I disable the automated time synchronization?

I usually set my time manually. Setting it to 15 minutes advanced. But after rebooting Ubuntu, time automatically deducts 15 minutes. Probably, due to time synchronization from some NTP servers.

I usually disable this feature in windows. Don't know where to disable this feature in Ubuntu.

---

### Post by bodhi.zazen on 2009-11-23
Left click the date -> properties -> unselect sync with network servers.

[https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

---

### Post by Madel on 2009-11-23
I think the version in the guide is not 9.10 as I can't find adjust date and time.
Only preference. Clicking on Time settings displays the date and time. There, i can edit the time.

But there's no such settings on changing time zones and disabling it. Not on 9.10.

---

### Post by wojox on 2009-11-23
Go into System > Admin > Time and Date 
Click the keys to unlock and adjust accordingly.

---

### Post by Madel on 2009-11-24
> **wojox said:**
> Go into System > Admin > Time and Date 
Click the keys to unlock and adjust accordingly.

still, it auto synchronize time during reboot.

btw, there's no Time and Date under System > Administraion

---

### Post by Madel on 2009-11-24
Any other suggestion? Probably your guides are not for Ubuntu 9.10.

@udpate

Problem solved.
I removed "ntpdate" package and it gets me what i want. Disabled auto time synchronization.

---

### Post by leorolla on 2009-12-02
Does it happen even when you turn off all internet connections?

Can you show the output of
```
ls -R /etc/cron*
```
?

---

### Post by cannibal_bill on 2010-04-29
Hi, just my two cents, for 9.10, since I'm waiting for the 10.04 release... It's at 6AM UTC.

So, as said before, click in the menu on System -> Admin -> Time & Date Settings.
Then, click the keyring to enter your password and be able to make some changes.
The form fields become accessible, click the 2nd one (Configuration). It says "manual", select the other one (there's only two, it should be labeled "Keep synchronized with internet servers".
The whole window will change : the minute/hour/day/month etc. are replaced with another drop-down menu that says "select servers". Here you go.

I selected the Swiss ones.

Then I went back to change the time back to manual and set it to a wrong time, just to see if it works (you can search "time utc" in google to get it instantly).
I don't know how to make it apply the new settings and get an updated time. I don't know how to tweak the update schedule etc. But I dont care, it's past 6AM now and I'll look for that in the new Ubuntu.

Before I post this, google says it's 06:07UTC and the ubuntu homepage still talks about "release candidate" and "change is coming"... can't wait!

---

