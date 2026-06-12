---
title: "wifi broken since upgrade to 17.04"
date: 2017-05-22
forum: Networking &amp; Wireless
---

### Post by csdgbas on 2017-05-22
Randomly drops internet connection, even though it indicates that the link to the router is still up.

---

### Post by howefield on 2017-05-22
Thread moved to the "*Networking & Wireless*" forum.

---

### Post by wildmanne39 on 2017-05-22
I posted a recommendation in your other thread for your other issue, however if you want to continue with 16.10 please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

---

### Post by csdgbas on 2017-05-22
> **wildmanne39 said:**
> I posted a recommendation in your other thread for your other issue, however if you want to continue with 16.10 please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.  Sorry, 17.04 as per the other thread.  Output here: [http://paste.ubuntu.com/24626102/](http://paste.ubuntu.com/24626102/)

---

### Post by wildmanne39 on 2017-05-22
Let's try what is in post 8 at the following link:
[https://ubuntuforums.org/showthread.php?t=2358532](https://ubuntuforums.org/showthread.php?t=2358532)
Then if it does not connect we will proceed.
Thanks

---

### Post by csdgbas on 2017-05-22
I've made the config file edit but it's late, here, so I will try it out tomorrow.  If I don't say anything, then it worked, let's (hopefully) leave it at that.  Thanks for your help so far, regardless of whether I need to come back tomorrow and report that it didn't fix things.

Out of interest, what does the config file change do?

---

### Post by wildmanne39 on 2017-05-22
In 17.04 there was a change in how network manager deals with mac addresses and there are some drivers that are not setup to handle the change and in those cases there is no internet access and modifying the file allow network manager to work like it use to before 17.04 came out.

---

### Post by csdgbas on 2017-05-23
Unfortunately that hasn't fixed it :(  Not completely, anyway.  It does *appear* to last longer, but eventually the same problem occurs.  

At first glance it looks very much like a DNS problem that is peculiar and exclusive to that particular device on the network, but pinging known IPs - even the home router! - doesn't work, even though it does from other devices.  And then, later, it might all start working again, without me having done anything.  In case I have to repeat, this problem wasn't present in 16.04 (for me, at least).

---

### Post by csdgbas on 2017-05-23
I don't know if this is significant, or even repeatable, but it just happened again (unable to connect to anything etc.) and I logged out and logged into another account, and was surprised that I could immediately use the internet with that account.  Logged back into the other account and could also connect using that.  So either logging out and logging back in again resets something or it was just a fluke occurrence, I don't have enough data yet.

---

### Post by wildmanne39 on 2017-05-23
There are a few things we can do to help it connect better.

Go into your router settings and in your network name take out the special character.

Check the settings in your router. WPA2-AES is best; not WPA1 and WPA2 mixed mode and do not use TKIP. 

Next, if your router is capable of N speeds, you will probably have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. You also should set a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Let's set your Country code for your router, please do the following if you live in London:
```
sudo iw reg set GB
```
```
sudo sed -i 's/^REG.*=$/&GB/' /etc/default/crda
```
Set your settings in network manager to match the screenshots:
Then do:
```
sudo systemctl restart NetworkManager.service
```
Let us know how it is working please.

---

### Post by csdgbas on 2017-05-23
I'm not sure it's very much better, to be honest.  Difficult to tell.  There have been very definite... pauses... in connectivity, but for all I know they were just normal issues from outside.  On the other hand, the pauses have been comparatively short, unlike previously.  I'll keep an eye on it tomorrow, see how things go.  Thanks very much for your help, I had been tearing my hair out over this.

---

### Post by csdgbas on 2017-05-23
No, it just blew out again, just like before.  Internet still working on all other devices.

---

### Post by wildmanne39 on 2017-05-24
There are several things going on with your wifi, all the things we have changed help improve performance if the driver is working correctly with the kernel but this driver tends to have issues so let's install a different driver and see if it helps.
```
sudo apt-get install linux-headers-generic build-essential git 
git clone http://github.com/lwfinger/rtlwifi_new.git
cd rtlwifi_new
make
sudo make install

```
Reboot

---

### Post by csdgbas on 2017-05-24
Thank you, I will try that.  Before I do, however, how do I get back to the current state of play should that not work, or goes wrong and launches the nukes?  Thanks.

---

### Post by wildmanne39 on 2017-05-24
I do not think it will make it worse, if it will not connect please run the wireless script again so we can see what is going on, please do not remove it until we have a chance to try setting a parameter or two. It can be done like this:
```
cd rtlwifi_new
make clean
```
I hope you did not change any of the settings I have asked you to change they will make a difference if we can get this driver working and I think we can.

---

### Post by csdgbas on 2017-05-24
> **wildmanne39 said:**
> I hope you did not change any of the settings I have asked you to change they will make a difference if we can get this driver working and I think we can.I've tried it, and it seems better, but am obviously open to any improvements you can suggest.   I can't say it is "solved" yet because the drops are/were so random.

---

### Post by wildmanne39 on 2017-05-24
Please post a new script file and I will look at it then if it drops and you can not connect please post another one while you can not connect.
Thanks

---

### Post by csdgbas on 2017-05-28
I just wanted to report back that everything seems to be working well with the new driver.  The script file is at [http://paste.ubuntu.com/24690758/](http://paste.ubuntu.com/24690758/) if you can see any further room for improvement.  Thanks so much for fixing it, it was really frustrating.

---

### Post by wildmanne39 on 2017-05-29
Let's turn off power management:
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot, that is all I see, as long as it is working good we do not want to change anything else.

Your welcome and Enjoy!:)

---

### Post by csdgbas on 2017-08-06
It's not solved.  It has started happening again after an update.

---

### Post by wildmanne39 on 2017-08-06
After a kernel upgrade you have to rebuild the driver:
```
cd rtlwifi_new
make clean
make
sudo make install
```
Reboot

---

### Post by csdgbas on 2017-08-09
Yes, I did that before posting.  Somehow the first time it didn't "take", but I did a make clean and then followed the above steps and it worked fine, so OOTT I guess.

---

### Post by wildmanne39 on 2017-08-09
Glad it is working again!
Enjoy!:)

---

### Post by csdgbas on 2017-10-06
It is still not reliable.  Unless by "reliable" means "can be relied on to fail at least once a day".  This is rubbish.

---

