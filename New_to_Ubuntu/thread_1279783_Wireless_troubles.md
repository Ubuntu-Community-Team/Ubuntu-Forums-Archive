---
title: "Wireless troubles"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by donescamillo on 2009-10-01
Hi,

The wireless hardware is OK, works with Windows very well, the strength of the signal is either excellent or very good. It used to work with Ubuntu LiveCD very well every time, I was impressed that it worked just out of the box. Now that I installed Ubuntu permanently I have problems.
First I create a nwireless network:
1. In the Edit networks box I click Add
2. I leave the name as default
3. I give it SSID
4. I change the security options to WPA/WPA2 Personal
5. I enter the password
6. Click Apply
7. When asked about access to the keyring I select Allow always
and after a while I get connected to the Internet

The problem starts when I reboot. I manually try to connect , the network icon starts rotating. After a while a dialog appears asking me for the password even if I entered it when I created the network. Never mind, I enter it again, and it tries, and ask and I enter it and on and on. Sometimes I reboot again and delete the wireless and re-create the network and it works, but not every time. 
I dont know if it is important but there is a check box saying Show password.
If I enter a password and check the box, the password will appear. Now if I click Apply dismissing the box and after that click Edit to bring the box again there will be no password, just the black dots (as it should be). The Show password check box is unchecked. If I check it the password shown will not be the one I entered before but something else.
It seems to me that there is some problem with this keyring that stores the passwords, but when I tried to uninstall it, Synaptic informed that it will uninstall half the operating system with it, so I did not touch it.
Has anyone experienced similar problems?

Regards,
donescamillo

---

### Post by realzippy on 2009-10-01
...the chance that anybody could help you would grow if you would post:

1. your Ubuntu version
2. your WLAN Hardware and Driver you use

---

### Post by 3rdalbum on 2009-10-01
> **donescamillo said:**
> 
If I enter a password and check the box, the password will appear. Now if I click Apply dismissing the box and after that click Edit to bring the box again there will be no password, just the black dots (as it should be). The Show password check box is unchecked. If I check it the password shown will not be the one I entered before but something else.

Correct. You will be shown the encryption key, not the passphrase.

Wireless passwords get hashed so they become more random and of a certain length, which makes them more suitable for using as an encryption key for the wireless traffic.

I have seen the symptoms you are describing before. Sometimes the wireless card is in an inconsistent state and the computer must be shut down completely and started up again in order to recover (NOT just rebooted, as this doesn't remove power to the wireless card).

It usually happens as the result of a buggy wireless driver - try installing the "linux-backports-modules-jaunty" package and see if this brings in a better driver for you.

---

### Post by donescamillo on 2009-10-01
I am using Ubuntu 9.04
The wireless is Intel, I am not sure about the driver and I dont know how to find out what it is.
I am writing this from LiveCD. Just for the hell of it and created and deleted a wireless network from LiveCD and got connected every time. I have no problems with Windows and no problems with UbuntuLiveCD.

regards,
donescamillo

---

### Post by donescamillo on 2009-10-01
**The previous post re-edited, I misspelt words**
 		I am using Ubuntu 9.04
The wireless is Intel, I am not sure about the driver and I dont know how to find out what it is.
I am writing this from LiveCD. Just for the hell of it I created and deleted a wireless network three times in a row from LiveCD and got connected every time. I have no problems with Windows and no problems with UbuntuLiveCD.

regards,
donescamillo

---

### Post by pbateman on 2009-10-01
Is your router broadcasting an SSID or is it hidden? 
I had a similar issue in my Thinkpad which i tried to resolve unsuccessfully for about a month. Eventually the only thing that fixed it was to set  the router to broadcast the SSID. Somehow in my case (and some other people's) Ubuntu does not play well with hidden networks.
Since broadcasting the SSID, it now connects automatically after every reboot without  an issue....

---

### Post by donescamillo on 2009-10-01
It was hidden, I just unhid it and will give it a go

regards,
donescamillo

---

### Post by donescamillo on 2009-10-01
I think the problem was in the network being hidden. I unhid it and it works. I rebooted three times and it works every time. It takes about 30 sec after showing the desktop at boot to get connected, but that is acceptable

Thanks,
donescamillo

---

### Post by LewRockwell on 2009-10-01
> **donescamillo said:**
> I think the problem was in the network being hidden. I unhid it and it works. I rebooted three times and it works every time. It takes about 30 sec after showing the desktop at boot to get connected, but that is acceptable

Thanks,
donescamillo

yes, this has been a constant problem for new users and prospective users

sadly, some toss the disk and distro aside from just this one issue

.

---

### Post by kbm on 2009-10-01
Good call.  I was running into the same problem a few weeks ago.  Set my router to broadcast just to make debugging/reconfig easier and it started working consistantly.  Didn't peg the cause and effect, but now that it is spelled out for me...

---

### Post by pbateman on 2009-10-01
Cool, glad it worked for you!
Yeah it takes about 30 seconds to connect after bootup for me as well...but it beats the 15-20 minutes of trial and error after every boot up that it used to take when the SSID was hidden.

---

### Post by donescamillo on 2009-10-01
> yes, this has been a constant problem for new users and prospective users
sadly, some toss the disk and distro aside from just this one issue

Many people evaluate Linux by first look, feel and experience. They dont have the time or desire to search for help even if the problem is sometimes easily fixable. After all, most of them use computers only for Internet, email and some office documents, which can be catered for by Linux. But that is off the topic.

How do I flag a post as SOLVED?
I did edit the first post's topic but it did not appear, in this replay I am putting it again in the topic to see if it will happen, I have been wanting to do it since the first problem I resolved in this forum...

regards,
donescamillo

---

