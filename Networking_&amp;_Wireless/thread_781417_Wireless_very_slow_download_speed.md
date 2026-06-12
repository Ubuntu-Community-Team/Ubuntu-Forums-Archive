---
title: "Wireless very slow download speed"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by eperrone on 2008-05-04
Hello All,

I have been successful in getting my Dell 1505 Draft 802.11 n card working in Hardy Heron using the ndiswrapper (with the Windows Wireless Driver tool).  But what I am now experiencing is very slow download speeds.  

So I tried to run a few speed tests on the internet connection.  Just to see what is up.

This first test is using wireless from my laptop when booted into Windows XP.  

As you can see my download speed is close to 6000
[IMG]http://www.dslreports.com/im/50240407/8423.png[/IMG]

This second test is from the same laptop booted into Ubuntu 8.04 using a wireless connection a few minutes later.

[IMG]http://www.dslreports.com/im/50241544/9422.png[/IMG]

Here are the results in Ubuntu with a Wired Connection

[IMG]http://www.dslreports.com/im/50244023/1333.png[/IMG]

What is pretty amazing is that the download speed is slower than upload!  and the upload speed seems to be comparable it is only the download speed that is bad. I figure that must be some type of configuration problem.  Maybe?

Weird.

Any suggestions or ideas folks?  Do I need to post some more information?
Thanks!

---

### Post by Paris Heng on 2008-05-04
> **eperrone said:**
> Hello All,

I have been successful in getting my Dell 1505 Draft 802.11 n card working in Hardy Heron using the ndiswrapper (with the Windows Wireless Driver tool).  But what I am now experiencing is very slow download speeds.  

So I tried to run a few speed tests on the internet connection.  Just to see what is up.

This first test is using wireless from my laptop when booted into Windows XP.  

As you can see my download speed is close to 6000
[IMG]http://www.dslreports.com/im/50240407/8423.png[/IMG]

This second test is from the same laptop booted into Ubuntu 8.04 using a wireless connection a few minutes later.

[IMG]http://www.dslreports.com/im/50241544/9422.png[/IMG]

Here are the results in Ubuntu with a Wired Connection

[IMG]http://www.dslreports.com/im/50244023/1333.png[/IMG]

What is pretty amazing is that the download speed is slower than upload!  and the upload speed seems to be comparable it is only the download speed that is bad. I figure that must be some type of configuration problem.  Maybe?

Weird.

Any suggestions or ideas folks?  Do I need to post some more information?
Thanks!

this mayb is the hardware issue between ur AP and the 802.11n. Your AP is in which standard?

---

### Post by eperrone on 2008-05-04
The AP is 802.11b/g.  

It works fine in Windows and I am using the windows driver for ubuntu through ndiswrapper.  So I guess it should work, but I do notice that the signal strength is much lower in Ubuntu than in windows.

But even with that if I put the laptop next to the AP itself and the signal is 100% the speed does not get any better in Ubuntu.

Thanks

---

### Post by Paris Heng on 2008-05-04
> **eperrone said:**
> The AP is 802.11b/g.  

It works fine in Windows and I am using the windows driver for ubuntu through ndiswrapper.  So I guess it should work, but I do notice that the signal strength is much lower in Ubuntu than in windows.

But even with that if I put the laptop next to the AP itself and the signal is 100% the speed does not get any better in Ubuntu.

Thanks

It is OK not to using the ndiswrapper, this sometimes may due to the driver problem also. Just i can tell you is , there are no concrete solution for this. You have to trial and error on this.

-----------------------------
[Paris Heng @ Wifi-Linux]("http://parisheng.110mb.com/")

---

### Post by zdude on 2008-05-04
Dude, your speed tests looked like mine! I tried the rt73usb driver in 8.04 and it was 50 times slower on downloads (wireless) and 4 times slower than uploads! I then downloaded the serialmonkeys driver - compiled it (same one I used on 7.10) and still slow. I then tried ndiswrapper and no go. I finally gave up due to my slow downloads would kill the whole network, all the wireless users would experience this same slow down - including the windows users. I am running 7.10 again and all is well. Sorry, no good news but I been searching for one.

---

### Post by eperrone on 2008-05-04
Really!

Man that sucks, so it is related to 8.04?  I guess I'll need to to wait for patch?

Maybe a future version would be ok.  Oh well I was just trying linux anyway but If I cannot get wireless to work it will be hard to use it at all.

Iguess I'll see what happens...

---

### Post by Ayuthia on 2008-05-04
You might try to disable ipv6.  I am not for sure if this will solve it or not, but I have read something about people having internet problems and disabling this.
```
sudo modprobe -r ipv6
```
If it does not work, you can bring it back by doing:
```
sudo modprobe ipv6
``` or you can reboot and it will come back.

---

### Post by eperrone on 2008-05-05
Hey folks,

I tried the ipv6 thing but it said module in use and did not do anything?

Thanks

---

### Post by Ayuthia on 2008-05-05
I guess you can't just disable the module.  Here is a link that describes how to disable it.  However, it says that the chances of it helping is very small.

[http://ubuntu-tutorials.com/2007/11/18/how-to-disable-ipv6-on-ubuntu-710-gutsy-gibbon/](http://ubuntu-tutorials.com/2007/11/18/how-to-disable-ipv6-on-ubuntu-710-gutsy-gibbon/)

---

### Post by jorluiseptor on 2008-05-05
That happened to me when I was using Ubuntu 7.10 and now on 8.04. Try changing the drivers for your wireless device and/or using restricted drivers.

---

### Post by eperrone on 2008-05-06
Well I might have found something.  When I downloaded the dellk driver it had a whole set of driver folders after I unzipped the package.  Originally I installed the the driver from the folder "drivers" and that gave the results on download earlier in this thread.

AnywY I went back and removed thosae drivers and installed the driver from the folder  driver_us
and these are the results now:

[IMG]http://www.dslreports.com/im/50433538/2632.png[/IMG]

Seem to be a little better (almost bearable) but not perfect.  I guess that is something!

Thanks any more ideas welcome!

---

### Post by aitortilla on 2008-05-18
I have just installed Ubuntu 8.04 on my desktop PC. Firstable my wifi card was working slow. I run "iwconfig" to view main characteristics. It was working at 1Mb/s so I couldn't get more than 38 or 40 Kb/s.

So I run "iwconfig wlan0 rate 11M" and I could obtain till my 200Kb/s which was my ordinary speed on Windows.

---

### Post by ukch on 2008-06-12
I just ran that same command and everything now seems to work as normal. The question is: why is the bitrate being throttled to 1Mb in the first place?

---

### Post by jonnan on 2008-06-13
This seems to have just fixed it for me - My wireless dropped to 'painful' a few weeks ago when I reset my DSL modem/wireless router, and frankly I've been getting more and more steamed at my ISP ever since.

Obviously something actually changed between my original network, and when the network was recreated, but whatever it was can go back to the way it was before - this has been driving me nuts for weeks.

Many, MANY, thanks - Jonnan

---

### Post by jonnan on 2008-06-15
Well, the wireless keeps resetting to ridiculously slow after reboots, I'm not sure what to do about that, but creating a launcher "gksudo iwconfig ra0 rate 11M" seems to fix it it one click.

Just FYI.

Does anyone know what is causing this?

Jonnan

---

### Post by ukch on 2008-06-16
I managed to fix this problem at reboot by adding the line:

```

pre-up iwconfig wlan0 rate 11M

```

to my /etc/network/interfaces file, just under the line that says:
```

iface wlan0 inet dhcp

```

Hope that helps.

---

### Post by Arcadian on 2008-07-02
Thank you Ukch! You just nailed my 1Mb/s wifi connection speed at startup! :)

---

### Post by Altin on 2008-08-14
Hi

Im having similar problems to this one with my 1Mb/s wireless connection in Ubuntu 8.04.
I tried 'sudo iwconfig wlan rate auto' but got the reply, 'Error for wireless request "Set Bit Rate" (8B20): SET failed on device wlan0; No such device.'
When I tried 'sudo iwconfig wlan 11M' Im told, 'iwconfig: unknown command 11M'.
I trie disabling IPv6 with 'sudo modprobe -r ipv6', but it replies, 'FATAL: Module ipv6 is in use'. This occurs even if I disable my wireless internet.

Id really appreciate any suggestions as my wireless has slowed down from 847Kb/s in Win XP to 191Kb/s, download speeds.

---

### Post by ukch on 2008-08-15
Your device may be called something other than wlan0. Running 'iwconfig' on its own will show you the relevant device name, then replance 'wlan0' in the first command with whatever your device is called.

---

### Post by G0dzzilla on 2009-02-02
Try 

sudo iwconfig wlan0 rate 11M

---

### Post by ukch on 2009-02-02
Hi G0ddzilla, welcome to the forums!

You might want to know that this is an old thread that has actually been solved already. But thanks for the input anyway! ;)

---

### Post by AggravatedGestalt on 2010-12-20
Solved already? Hmmm. Since I am having the same problem and using Lucid Lynx here at Christmas time 2010, I beg to differ. It aint been solved. When I boot in windows, everything works fine. When I boot into shuttleworth (Lucid Lynx), things don't. I hate to admit this, but it it's just plain true; unless "solved" means swept under the carpet,... or if it's too big to sweep under the carpet, just call it solved? This RTL8187 chip has a substantial history of bugs in Linux. Anyone able to explain why? I thought realtek was nice about their source. It's a bit ironic that I have been having a lot of trouble in Ubuntu, and doing all sorts of physical acrobatics with my wireless device to make it work, only to find inadvertently that when I use windows, it works just fine. Super strong signal strength, but can't even load the home-page (google.com)? Odd, after so many years of bugs. I almost want to admit that I am inclined to expect the fix would be included in modern updates.

---

