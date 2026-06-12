---
title: "staring netbook offline after upgrades"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by missLiz on 2010-02-21
Hello 

I have a starling netbook which I love and has worked great.  Until my husband decided to click on the upgrades.  Now I cant get on the internet.  Not only does it not see wireless, but when I plug the modem into the netbook directly, It says I am offline.  Do you think it is something about the upgrades ?  I'm  sure he didn't  look through to see what all he was upgrading.  Where should I start?  (my husband tried to fix it--he is a Linux user and a programer but now he had to go on a trip). Thanks.

---

### Post by J V on 2010-02-21
how exactly are you typing on these forums then?

---

### Post by missLiz on 2010-02-21
I am on my son's mac

---

### Post by mikewhatever on 2010-02-21
Assuming you are talking about [system76's starling netbook]("http://www.system76.com/product_info.php?cPath=28&products_id=92&osCsid=8292e3kl11srv0orjkb1lbeot4"). I wonder if the updates installed without error. You can probably get back online by booting an older kernel. What OS is it running?



> **J V said:**
> how exactly are you typing on these forums then?

That wasn't clever.

---

### Post by missLiz on 2010-02-21
Yes, it is System 76, I didn't know there were any other starling netbooks.  The os is Ubuntu 9.04 'jaunty jackalope.

---

### Post by mikewhatever on 2010-02-21
> **missLiz said:**
> Yes, it is System 76, I didn't know there were any other starling netbooks.  The os is Ubuntu 9.04 'jaunty jackalope.

There probably isn't, but not everyone is from North America and familiar with the brand.:)

Have you tried checking the older kernels? I don't know how the bootloader is configured, usually, there is a countdown of three seconds before booting, and you have to press Esq while it's counting to get to the boot menu. Once there, select an older kernel, if available, and hit Enter. When booted, and if wifi works, post the output of the following command from Terminal:

sudo lshw -C network

You might also want to run the following to make sure all updates were installed:

sudo apt-get update && sudo apt-get upgrade

---

### Post by missLiz on 2010-02-21
Thank you for your help and for the link to the article Linux is not windows. Even though I have never used windows (mac and linux administered by my husband)it was helpful to read about the culture difference of commercial vs open source.  I am just learning the culture and want to learn how to do things myself. I really appreciate your kindness and patience with someone new to the culture.  I will try your ideas and post later with my results.  Thank you

---

### Post by HunkirDowne on 2010-02-21
> **missLiz said:**
> Thank you for your help and for the link to the article Linux is not windows. Even though I have never used windows (mac and linux administered by my husband)it was helpful to read about the culture difference of commercial vs open source.  I am just learning the culture and want to learn how to do things myself. I really appreciate your kindness and patience with someone new to the culture.  I will try your ideas and post later with my results.  Thank you

We are mostly Mac and Linux here as well but we do speak Windows occasionally.  ;-)

Linux is certainly not Windows and that's a good thing.  I think some of the differences between Linux and Mac are important as well but have not seen much in the way of a similar topic posted.

But to get back to your original problem, I have had difficulty getting a proprietary wireless PCMCIA card to function and have scourged the forums (fora?) for information.  Regarding your situation a good place to start might by kevdog's post at the following link.

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

This is a good starting point and may not answer all your questions about configuring wireless, but it should point you in the right direction but you might have to do a Google search on the topic to find the information you are looking for.

One note about finding information, I have alluded to other forums and found the following to be helpful in addition to the Ubuntu forum.

[http://forums.debian.net/](http://forums.debian.net/)  Ubuntu is based on Debian and I use both so this is a natural for me.

[http://wiki.debian.org/WiFi/HowToUse](http://wiki.debian.org/WiFi/HowToUse)   This is similar in effect to kevdog's post and I believe there is may Ubuntu wiki as well but I never use it.  A quick look tells me it is not meant for help and may just be something for the development team.

Finally there is [http://www.linuxquestions.org/](http://www.linuxquestions.org/) -- I will let you make your own decision but I've found little here that hasn't been posted in the Debian and Ubuntu (and Mint) forums.

On a personal note, I am in the market for a new laptop (probably not a netbook) and would like more information about System76 from users that have them.  I have yet to peruse the forum but invite PM's on the subject since it is obviously off-topic here.


Cheers!

---

### Post by patchwork on 2010-02-21
You may need to install/reinstall the latest system76 driver (System > Administration >System76 Driver)  (v2.4.5, I believe...)

Either way, you're almost certainly better off posting in the system76 support forum [here.]("http://ubuntuforums.org/forumdisplay.php?f=341")

---

### Post by missLiz on 2010-02-21
Thanks,  I am on line again after booting an older kernal.  I dont know if that solves the root problem, but I will work off-forum on it. I think there is a way to say SOLVED, but cant see it now.  

Thanks to all who responded, and I will check out the other forums including the system76 help forum.

---

### Post by s.fox on 2010-02-21
Hello,

I am glad you are now back online :)

[Here]("http://ubuntuforums.org/showpost.php?p=4527051&postcount=6") is a howto on how to mark this thread as SOLVED

-Silver Fox

---

### Post by missLiz on 2010-02-21
I forgot to post what you asked for.  This is the output from the command sudo lshw -C network:
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:26:9e:01:44:ed
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:17:c4:91:ba:64
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.101 multicast=yes wireless=802.11b/g linked
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ea:62:7b:57:35:7e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
liz@system76-netbook:~$

---

### Post by mikewhatever on 2010-02-21
I'd try the following with the new kernel booted:

1. Check if the r8169 module is loaded.

lsmod | grep r8169*

2. If it's not loaded, try loading.

sudo modprobe r8169

3. If the module is loaded, try bringing up wlan0.

sudo ifconfig wlan0 up

---

### Post by missLiz on 2010-02-21
> **mikewhatever said:**
> I'd try the following with the new kernel booted:

1. Check if the r8169 module is loaded.

lsmod | grep r8169*

2. If it's not loaded, try loading.

sudo modprobe r8169

3. If the module is loaded, try bringing up wlan0.

sudo ifconfig wlan0 up
how can I tell if it's loaded?

---

### Post by mikewhatever on 2010-02-21
> **missLiz said:**
> how can I tell if it's loaded?

Well, you get the output saying r8169, and if there is no output, then it isn't loaded.

```
lsmod | grep r8169*
r8169                  32064  0 

```

---

### Post by missLiz on 2010-02-21
Thanks,   yes then it's loaded, but I cant bring up wlan0.

---

### Post by mikewhatever on 2010-02-21
Why not, what's the output you get? How about bringing up Ethernet?

sudo ifconfig eth0 up

---

### Post by missLiz on 2010-02-22
> **mikewhatever said:**
> Why not, what's the output you get? How about bringing up Ethernet?

sudo ifconfig eth0 up
ok.  Output for trying to bring up wlan0 is:
wlan0: ERROR while getting interface flags: No such device

when I try eth0, no output, just the prompt line again.

---

### Post by HotShotDJ on 2010-02-22
missLiz:  You are really posting in the wrong forum.  While the folks here in the "Absolute Beginner Talk" forums are quite helpful and kind (as you no doubt have already noticed), you'll get much better advice directly from System76 in the "[System76 Support]("http://ubuntuforums.org/forumdisplay.php?f=341")" forum right here at ubuntuforums.org.

---

### Post by missLiz on 2010-02-22
OK,  Thank you for being so helpful and kind.:D I am having a lot of fun learning this, but I dont want to waste anyone's time.   I will go over to the system 76 forum):P

---

### Post by mikewhatever on 2010-02-22
You can report one of the posts and ask the mods to move the thread to the system76 subforum.

---

