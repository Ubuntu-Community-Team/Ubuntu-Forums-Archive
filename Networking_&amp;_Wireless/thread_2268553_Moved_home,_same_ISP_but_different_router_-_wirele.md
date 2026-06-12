---
title: "Moved home, same ISP but different router - wireless Broadcom BCM4352 issues"
date: 2015-03-09
forum: Networking &amp; Wireless
---

### Post by pages on 2015-03-09
Hi all ,

recently moved home but my hardware isn't handling the move as good as me!

Setup is identical except the router being used. But it is the same ISP
It seems as though the connection is being throttled and at times outright disconnecting.

Here's a link for the out put from this [question]("http://askubuntu.com/questions/425155/my-wireless-wifi-connection-does-not-work-what-information-is-needed-to-diagnos")
[http://paste.ubuntu.com/10570539/](http://paste.ubuntu.com/10570539/)


I've no idea what could be the issue but it's something to do with Ubuntu+ the router since my windows machine connection doesn't drop or throttle at all

---

### Post by Vladlenin5000 on 2015-03-10
> *UPC940852:      Infra, E8:40:F2:6B:83:B7, Freq 2462 MHz, Rate 54 Mb/s, Strength 58 [COLOR=#ff0000]WPA[/COLOR]

Change it to WPA2.

---

### Post by pages on 2015-03-15
Hi ,
First off thanks for the reply , never saw the email notification so apologies for the late reply.
Went into the administration and changed it to WPA2 . At first didn't seem to help  but did a hard restart of the router  and it's certainly much better.

I'm still cautious it's still not fully fixed although given my download:upload speed ratio on files is 1:4 when download used to be at least 2-3 times faster before.
But thank you so much for taking the time to help me out.

---

### Post by coffeecat on 2015-03-15
I know you've marked this thread as solved but a couple of thoughts.

> **pages said:**
> download used to be at least 2-3 times faster before.

Have you done a speedtest with the computer connected to the router via ethernet cable? It may be that although you have the same ISP, the line speed in your new home may not be as good as your old home. If you have adsl via copper wire phone line, speed is dependent on distance from exchange, or the line itself may be noisy and need attention from whoever maintains the infrastructure where you are.

I suggest speed tests via ethernet and wireless. The ethernet result will give you best available on your connection, and the wireless result will tell you how much (if any) speed you are losing using the wireless connection. It may be that walls in your new home are degrading signal more than in your old, or perhaps you have more wireless traffic from neighbouring homes interfering with your wireless signal.

---

### Post by pages on 2015-03-17
> **coffeecat said:**
> I know you've marked this thread as solved but a couple of thoughts.



Think you may be right about marking this thread as resolved too early.

Was having issues streaming so  decided to run speedtest.
Was only getting between 1-3 MB/s down and 6-7 MB/s Up   :/
Quickly booted up to windows and ran the test asap and got 30 MB/s down and 10 MB/s Up .

So with same hardware and presumably same interference there's nearly a 10 fold difference in download .
Just to see if the wireless receiver is causing issues ran the speed test on my laptop right beside the receiver and was getting  60 MB/s down and 25 MB/s Up.
So the wireless receiver isn't the strongest but it should be at least getting up to 30/10 as it does on windows.


Is there any programs I can run to see what's causing the contention or throttling ?

---

### Post by coffeecat on 2015-03-17
I've edited your thread title to include the wireless device you are using. Hopefully, that will attract those with experience of Broadcom devices.

The difference in speeds between Windows - 30/20 - in your normal location - and unspecified OS - 60/25 - near the router is interesting. It would be useful to do a speed test with the computer connected to the router via ethernet cable to get a best possible estimate against which you can compare all your wireless speedtests in both Windows and Ubuntu.

---

### Post by wildmanne39 on 2015-03-17
The file you posted is missing most of the information needed to see what the settings are in your new router so we can see what needs to be changed.
Thanks

---

### Post by pages on 2015-03-18
> **coffeecat said:**
> 
The difference in speeds between Windows - 30/20 - in your normal location - and unspecified OS - 60/25 - near the router is interesting. It would be useful to do a speed test with the computer connected to the router via ethernet cable to get a best possible estimate against which you can compare all your wireless speedtests in both Windows and Ubuntu.

Amazingly I've lost both my ethernet cables so I can't do this test :/   ( the other OS on the laptop was windows 7 )

> **Wild Man said:**
> The file you posted is missing most of the information needed to see what the settings are in your new router so we can see what needs to be changed.
Thanks

Hmm not sure how it was missing anything . I re-ran the script while streaming in a hope it might pick up something that was otherwise missed.
[http://paste.ubuntu.com/10621566/](http://paste.ubuntu.com/10621566/)

If that's missing anything let me know and I'll see what i can do different , was only running 
wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && \
chmod +x wireless_script && \
./wireless_script

---

### Post by wildmanne39 on 2015-03-18
Your driver needs upgraded let's do:

```
wget http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb
```
```
sudo apt-get install build-essential dkms linux-headers-generic
sudo apt-get remove --purge bcmwl-kernel source
sudo dpkg -i *.deb
```
If wget is not installed you will need to install it.
If you still have issues after the new driver is installed post fresh information from the script so we can take a close look at your router settings.

---

### Post by pages on 2015-03-19
Hey , 
Thanks for the help ,


Ran those with no issues but still didn't seem to fix the throttling 
[http://paste.ubuntu.com/10626251/](http://paste.ubuntu.com/10626251/)

---

### Post by wildmanne39 on 2015-03-19
You still have the same driver errors in the dmesg information, You have four network on channel four all with the same link quality, I recommend changing your channel two 6 or 11 and see if that helps.

Set your settings in network manager to match the screenshots:
In the router change this > CCMP TKIPto wpa2 AES CCMP and take out the TKIP it slows connections in most cases.
Thanks

---

### Post by pages on 2015-03-19
Hey 
Back again :/ !
so changed the network connections and also went around searching the router to change it to AES . Only other option was AES+TKIP 

[ATTACH=CONFIG]260740[/ATTACH]


Here's the updated wireless txt info
[http://paste.ubuntu.com/10629424/](http://paste.ubuntu.com/10629424/)

---

### Post by wildmanne39 on 2015-03-19
Did you set IPV6 to ignore in network manager like in the screenshots?
Change the channel to 11 in your router other people are on the same channel and that can cause issues.

The error messages are still there, I will continue to look for a driver or kernel that will fix that.
Thanks

---

### Post by pages on 2015-03-20
Yep changed  both settings to match yours.


Also changed the channel to 11.
It's still all a bit mental though , here's some runs i did on speed test so you can see the differences.
[ATTACH=CONFIG]260769[/ATTACH]


Also something to note , when i changed the channel to 11 , it didn't get picked up as channel 11 ( in the wireless script)  until I did a computer reboot , although on my windows laptop it immediately saw that it was channel 11 
Anyway heres the latest wireless script.
[http://paste.ubuntu.com/10634621/](http://paste.ubuntu.com/10634621/)

once again thanks for trying to work through this , it's so far out of my depth

---

### Post by wildmanne39 on 2015-03-20
That is all I know to do, it may be the best it will do until the bug is fixed in that driver.

---

### Post by pages on 2015-03-20
Ok no worries , 

Have you a link where i can check the latest updates on the driver ?

---

### Post by wildmanne39 on 2015-03-20
Here is a link maybe one of the drivers here will help. 
[https://launchpad.net/ubuntu/+source/bcmwl](https://launchpad.net/ubuntu/+source/bcmwl)

---

