---
title: "Realtek RTL8188EE, Toshiba Satellite C55-A5300, Ubuntu 12.04: No Wifi Connection"
date: 2014-01-01
forum: Networking &amp; Wireless
---

### Post by swarup on 2014-01-01
I've just purchased a Toshiba Satellite C55-A5300 Laptop which came with Win8 preinstalled. I've set up a dual boot with Ubuntu 12.04 and everything is working wonderfully. With the single exception that there is no wireless internet connectivity, no wifi. In the options for connecting in the drop-down menu at the upper right corner of the screen, wireless is not even listed there. The laptop has Wi-Fi Wireless networking (802.11b/g/n), so it should work just fine. I have searched on the internet and found that there are quite a number of reports of others having the same problem with this Toshiba laptop and Ubuntu. But I could not locate the solution! I am really hoping someone either knows the solution and can let me know, or is better than me at finding the solution on the web.

---

### Post by sudodus on 2014-01-01
Please try to find out what ***wifi chip*** there is in you computer. You might find it with

```
 sudo lshw
```
 
or ***hardinfo***. It is fairly easy to find lists at the internet, that describe how well wifi chips cooperate with linux.

It might work better with the newest version 13.10. Try running a live session.

---

### Post by swarup on 2014-01-01
I am giving this computer to a friend who is a complete newbie to computers what to speak of linux. I want him to have a LTS OS so he doesn't have to make changes any time soon. Here is the hardware:

```
           *-network
                description: Ethernet interface
                product: AR8162 Fast Ethernet
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 10
                serial: 00:8c:fa:6c:38:21
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=alx driverversion=1.2.3 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:16 memory:c8500000-c853ffff ioport:3000(size=128)
```

And

```
           *-network UNCLAIMED
                description: Network controller
                product: RTL8188EE Wireless Network Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: ioport:2000(size=256) memory:c8400000-c8403fff
```

So I think what I've got for wireless is this:

                product: RTL8188EE Wireless Network Adapter
                vendor: Realtek Semiconductor Co., Ltd.

And I had seen that listed around the internet. But seeing that there were issues, and finding the solution are two different things. There must be a solution for this product with Ubuntu 12.04, don't you think?

---

### Post by swarup on 2014-01-01
Would the solution offered on [this link]("http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281") help me?

And what about [this link]("https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/236497"). Here it looks like a solution worked-- but I couldn't tell whether ultimately they got it working with 12.04, or whether they never did and had to go with 13.10 instead.

---

### Post by sudodus on 2014-01-01
It seems you need to compile the driver. This guy did it with some help [http://ubuntuforums.org/showthread.php?t=2196520](http://ubuntuforums.org/showthread.php?t=2196520)

So it should be possible for you too, but far from easy.

---

### Post by sudodus on 2014-01-01
I can't tell which of the links is the best one. But there seems to be solutions anyway.

---

### Post by swarup on 2014-01-01
I was hoping to give my newbie friend a long-term OS rather one for just nine months. But I need a solution for this wireless that is going to be fairly quick and straightforward for me to do. If it is going to be difficult, then I'd sooner do a fresh install of 13.10, which people report works perfectly. What do you think? Is it going to be a real struggle to get 12.04 working with wireless? If so, then I'll just have to give him the 9 month product to work with. [Here is a post]("https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/238309") where someone was recommended to switch from 12.04 to 13.10, and it work out perfectly.

---

### Post by sudodus on 2014-01-01
Well, you can read the dialogue of the link I gave you. If you think you can do it, go ahead, otherwise go for 13.10 and hope it will be easy to upgrade to 14.04, which will be an LTS release.

---

### Post by swarup on 2014-01-01
That link was very interesting. And they did get it working. But at the very end the one giving guidance wrote the following:

> You will have compiled the driver for your currently running kernel only. When Update Manager installs a later linux-image, after reboot, re-compile:

I could never leave my newbie friend having to recompile every time the kernel gets updated. If that is the only option, then I'll have to go with 13.10.

---

### Post by sudodus on 2014-01-01
I think you are right, good luck with 13.10 :-)

---

### Post by varunendra on 2014-01-01
If ease of use is prime concern and 'easy' means fully automatic here, I'd second sudodus's last advice -
> otherwise go for 13.10 and hope it will be easy to upgrade to 14.04, which will be an LTS release.

The solution in the thread he linked to is basically offers the same thing that 13.10 will offer you - the driver from kernel 3.12.. You can install the latest kernel in 12.04 too, which will be offered the upgrade to 14.04 (or just its kernel and Xorg packages only, as and if required) anyway. So you can choose whichever seems to be the best working solution for you -

1) Install the latest supported kernel on 12.04.3, which will install the same driver which you would have otherwise compiled from the backports package. This will be a permanent fix with no need to compile anything or do anything manually later. But whether the overall system would perform better after this upgrade can be questionable.

2) Install 13.10 and upgrade it to 14.04 when it comes out. I'd personally recommend to do the upgrade about a month later to give 14.04 enough time to iron out its bugs. Be aware that an 'upgrade' is not always smooth and sometimes breaks features/functionality/entire installation, especially if you are using any proprietary drivers and software from ppa's.

3) The above concerns bring up a third option that can be considered - Install 13.10 now, keep data in separate partitions (creating a separate /home partition makes that smooth and safe), and do a fresh install of 14.04 when it comes out.

Of course there are also some other options in-between, but none as easy and smooth as above ones.

Oh, and don't forget to test 13.10 in live mode first to make sure it works well with the hardware.

---

### Post by swarup on 2014-01-01
Thank you for your input Varun!

I've thought more about it though, and there are some other factors for me to consider here. This laptop is going to be for a friend of mine in India. He lives in an area where most people get on-line via USB dongles. And when I get to India, I'll be getting him a dongle. So given that, the likelihood he'll need the wireless feature is low. And the benefit of LTS till 2017 is great. Because he is not someone who is going to start downloading new versions and things like that. If I give him 13.10, it will likely remain on the computer for quite some time, perhaps years. Wiith 13.10 he'll lose support in July, won't be able to download any software or anything. So overall, even without wireless I think he will be better off with LTS. So I think I shall keep 12.04 on the laptop for him.

In the meantime if anyone does come up with a straightforward way of getting the wireless to work on this machine, that would be wonderful. Then he'll have both LTS benefits, as well as the wireless for any times he may need it.

---

### Post by varunendra on 2014-01-01
Makes sense.

I believe the next best option, better than banging head with a dodgy card/driver, is to simply replace the card with a one that is properly supported. Now 'which one' is properly supported, can take a little research unless some of our friends can confirm a particular name. For the research, this may be a good starting point : [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by sudodus on 2014-01-01
> **varunendra said:**
> Makes sense.

I believe the next best option, better than banging head with a dodgy card/driver, is to simply replace the card with a one that is properly supported. Now 'which one' is properly supported, can take a little research unless some of our friends can confirm a particular name. For the research, this may be a good starting point : [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

+1

---

### Post by swarup on 2014-01-01
That all makes sense, yes. Thanks so much to you both. Now I've got a clear pathway to move on! :p

Even though there was no straight road available for getting the native wireless card working with 12.04, I'm going to go ahead and mark this thread as solved. If anyone does come up with a simple solution for that, I'd love to hear about it!

---

