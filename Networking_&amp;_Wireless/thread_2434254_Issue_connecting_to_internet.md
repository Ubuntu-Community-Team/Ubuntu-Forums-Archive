---
title: "Issue connecting to internet"
date: 2020-01-02
forum: Networking &amp; Wireless
---

### Post by darylbe on 2020-01-02
Hi everyone,

I'm having issues connecting to the internet. I am using a Dell inspiron 15r-5521 work station, running Ubuntu 19.04. Everything has worked perfectly for months. 

I am not certain what I was doing that caused this system issue, but noticed it a week later. 

The wifi networks appear, but when I try signing on, wifi icon has a question mark. Linux sees the wireless adapter, and it shows that it's connected, but I cannot access internet via Chrome or Firefox. 

I then connected via ether net cable, and again, it does not work. 

Other devices can use the wifi without problems. I tried to use another wifi and was unable to log on as well. So the next step--I loaded Ubuntu from a flash disk, and this connected and worked fine. (I was wondering if Mac address was blocked, etc, but this ruled it out). 

I have tried flushing DNS, I pinged Google which I believe worked, but when I 
Ping 8.8.8.8, "operation is not permitted" is response. Not sure what this means or what to do with it lol

I logged into router info, and it seems everything is working correctly, and thru ISP it seems the device is connected. 

I notice i used to be able to select VPN, networking, etc from top right corner of desktop, whereas now it only shows internet/wifi and Bluetooth, so I'm going to try and uninstall and reinstall network manager tonight. And need to figure out how to install network tools w/out access 

Sorry, I'm at work and don't have access to the computer right now. I know I can backup harddrive and do a fresh install, but this is part of using Ubuntu and I'd prefer to fix whatever issue I caused.

---

### Post by TheFu on 2020-01-02
Support for 19.04 ends in just a few weeks.  It isn't worth any effort trying to solve any issues on that release. Either move to 19.10 or back to 18.04.

19.10 support ends in July, but there should be an upgrade path to 20.04 which will have no-hassle support until 2025.
18.04 no-hassle support ends in 2023.  And this support can be extended 5 more years with some hassles.

LTS releases with no-hassle 5 yrs of support happen every even year in April.

If the same thing happens with any other release, please run with wifi-info script and post the output.  It is also useful to say the exact flavor of Ubuntu and the DE used since some of them use different networking methods.

---

### Post by DanPerecky on 2020-01-20
I had the same problem.. and had to do an unusual step to fix it...  Hope that this helps. Worth a shot.

I had a weird problem last week... the Wired connection.. for Virtual Box / Ubuntu worked one day... The next day Virtual Box / Ubuntu's internet would not connect. WiFi on Windows 7 - the host OS, was fine.

The solution was to go into Virt Box | Settings | Network | Advanced and change the MAC Address for the Ubuntu guest system.

..

---

### Post by jamesjaze on 2020-04-03
Hi, I have read your problem fully. I think you need to use [vpn chrome]("https://chrome.google.com/webstore/detail/ookhnhpkphagefgdiemllfajmkdkcaim") as a solution. Hope this will be helpful to solve your problem.
Thanks!

---

