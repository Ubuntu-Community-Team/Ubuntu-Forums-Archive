---
title: "WiFi loses connection after a day or so"
date: 2016-09-09
forum: Networking &amp; Wireless
---

### Post by DGINSD on 2016-09-09
I did a clean install of Ubuntu 16.04 and all wnt well but my wifi connection randomly goes down after a day or so of being fine, only a reboot brings it back.  Odd thing when it does go down, the tray icon still shows it as connected, till I toggle the wifi button or networking menu, trying to get the connection back up. The only way I even know its down is by my browser or samba  connection not working.

I've tried both the closed source driver and the OS one it seems to happen with both bcmwl-kernel-source.

Heres some info on my network connectors:
```
Network: 
           Card-1: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
           driver: r8169 v: 2.3LK-NAPI port: 3000 bus-ID: 01:00.0
           
           Card-2: Broadcom BCM4313 802.11bgn Wireless Network Adapter
           driver: bcma-pci-bridge bus-ID: 07:00.0
           

```

I'll happily provide any more info or run some test commands for anyone that can help, rebooting every day is getting rather old, especially when you've given your computer work to do during the day, only to come home and find its all failed because you lost network connection as soon as you turned your back.

---

### Post by howefield on 2016-09-09
Thread moved to the "*Networking & Wireless*" forum for a better fit.

---

### Post by praseodym on 2016-09-09
Try this proprietary driver (newest version):
```
sudo apt-get install linux-headers-$(uname -r) build-essential dkms
wget http://de.archive.ubuntu.com/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-3_all.deb
sudo dpkg -i broadcom-sta-dkms_6.30.223.271-3_all.deb
```
[https://forum.ubuntuusers.de/topic/wlan-probleme-seit-neuer-o2-box-nur-unter-linu/2/#post-8031898](https://forum.ubuntuusers.de/topic/wlan-probleme-seit-neuer-o2-box-nur-unter-linu/2/#post-8031898)

---

### Post by QIII on 2016-09-09
Hello!

While a link to a German language forum would be quite useful to me, it probably is not to many of the users here.

Could you please distill the important parts and present that in English for our users?

Thanks.

---

### Post by praseodym on 2016-09-09
Thanks, will do so in the future

---

### Post by DGINSD on 2016-09-10
I actually dug back in some of my older posts and found a solution I  employed on an older version of Ubuntu, heres the link for others [https://ubuntuforums.org/showthread.php?t=1931680&p=11719606#post11719606](https://ubuntuforums.org/showthread.php?t=1931680&p=11719606#post11719606)
It basically blacklist some other broadcom modules that supposedly  interfere with the proprietary STA module. Executing these commands will  employ the fix.
```
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
I  paired it with a removal and reinstall and reinstall of  bcmwl-kernel-source for good measure, but your probably just as well  with blacklisting the other two modules and rebooting. Here's the total  of what I did.
```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get autoremove --yes
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo apt-get install --yes bcmwl-kernel-source
```
I'm  trying this fix first, and so far so good, but as I said the wifi  disconnects after a day or so and its pretty random when it does, so  I'll likely need to wait a week or so, but if it doesn't work I'll give [[COLOR=#000000]praseodyms  post a run through I do very much appreciate the help, the Ubuntu  community is awesome  and the only way I've been able to completely  switch to Linux.[/COLOR]]("https://ubuntuforums.org/member.php?u=1411497")

---

### Post by DGINSD on 2016-09-18
So this morning I did some maintenance on my media server, after which I rebooted it, after doing this my wifi onmy laptop no longer has an internet connection. This after working fine for over a week without rebooting. The wifi icon still shows connection but every app i launch that needs connection says there's no connection (browsers, smb, ssh).

So while my computer is in this state how can i trouble shoot to find out where my problem lies?

Some info that may be related, there was an active samba connection when I rebooted the server, i think this may be the cause of the wifi hang.

My samba connections have already been weird i can't go through network places I have to go through "connect to server" and manual enter the ip.

---

### Post by wildmanne39 on 2016-09-18
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by DGINSD on 2016-09-18
What does the script do?

I got a connection back by issuing this command to kill network manager
```
sudo kill `ps -C NetworkManager -o pid=`
```

Then I launched Boot Up Manager right clicked on Network Manager (which didnt have a check box selected) and selected to start Network manager and my connection came back. 

I think I can duplicate the issue now.  Should I still download your script, duplicate the issue, and run it?  Just run it as is?  Or does the restart of network manager offer any clues to the problem?

---

### Post by wildmanne39 on 2016-09-18
In 16.04 there is a bug where network manager has to be restarted but you are not running 16.04 right? and with all updates applied that bug should be resolved.

Do you think the issue is resolved or does it come back? Run the script when it will connect then when it will not.
Thanks

---

### Post by DGINSD on 2016-09-18
I am Running 16.04 all updates have been applied. I don't think its fixed, I just think stopping and restarting NM made it work again, but I'm sure it'll happen again. It seems to have something to do with connecting with a remote computer and that connection not terminating properly, this always seems to cause the connection to be lost on my HP's wifi.

---

### Post by wildmanne39 on 2016-09-18
Here is the network manager bug.
[https://bugs.launchpad.net/ubuntu/+source/network-manager](https://bugs.launchpad.net/ubuntu/+source/network-manager)
The work around is to restart network manager manually, I believe some people made a small script to do it but I do not remember where it is at this time.

I use ubuntu mate and it was fixed with an update for me so something else might be going on, we might tell by the posting of the wireless script when working and not working.

---

### Post by DGINSD on 2017-01-01
Ok I finally have some time to work on this issue wireless has been randomly shutting down and I've just been restarting network manager with the command I listed put into a script

```
#!/bin/bashsudo service network-manager restart
exit 0
```

I ran wildmanne39 script while the wifi is up and will attach it to this post, and will run it again the next time it goes out.

---

### Post by wildmanne39 on 2017-01-02
We will try to help when you post the non-working script.
Thanks

---

### Post by DGINSD on 2017-01-03
Alright got home tonight and had the wireless disconnected here's the new run of the wireless script.
On a side note I got rid of the Broadcom STA proprietary driver, I get the wifi disconnects no matter which I use. Restarting Network Manager fixed the drop.

---

### Post by wildmanne39 on 2017-01-03
Please do:
```
sudo -i
echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit
```
Reboot

---

### Post by DGINSD on 2017-01-05
Ok I executed those commands, do you want me to re-run the wifi script and re-post the output?

The last time wifi dropped out, when I restarted network manager the wifi icon never came back on the top bar, the network reconnected and the wired connection icon popped up (though the cable wasn't connected), I restarted NM again to see if it was a fluke but got the same result. Also the wireless section of the drop down menu was not there either not sure if this is relevant to my issue or not just thought I'd mention it.

---

### Post by wildmanne39 on 2017-01-05
It has disconnected since you ran those commands? The issue with the icon is a bug in network manager but it was fixed with an upgrade a long time ago, is your computer up to date? do you have any updates that are locked so they do not update? Even when the wifi icon disappeared everyone was still connected to the internet, I to had that bug for a very short period of time then I upgraded and it was fixed.

Yes please run the wireless script again and let's make sure the changes stuck.
Thanks

---

### Post by DGINSD on 2017-01-06
I was just posting back and as I was posting I got a drop out, so I have 2 runs of your script one before the drop and one after, I named the one before the drop "wireless-info before drop.tar.gz" and the other will be named normally.

My system is up to date but I'm only running 16.04 LTS do I need to be running 16.10 for the bug fix to apply?

---

### Post by wildmanne39 on 2017-01-06
Here it looks like your connection is being blocked, but that is IPV6 which should be set to ignore, it looks like you have two connections with the same name, one has IPV6 set to ignore and the other one does not, I recommend removing the one that does not from network manager and reboot.

Also your device is only partially supported with this driver but it is the only one for your device, so just have to hope it keeps getting developed.

I would remove the all capitalized letters and special characters from your network name, that use to be an issue with ubuntu staying connected.

If this does not fix it I am out of ideas.

Comparing the scripts this is the only difference:
```
[85882.637109] [UFW BLOCK] IN=wlp7s0b1 OUT= MAC= SRC=fe80:0000:0000:0000:<IP6 'wlp7s0b1' [IF2]> DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=220438 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[85882.637151] [UFW BLOCK] IN=wlp7s0b1 OUT= MAC= SRC=fe80:0000:0000:0000:<IP6 'wlp7s0b1' [IF2]> DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=765787 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
[85882.647435] [UFW BLOCK] IN=wlp7s0b1 OUT= MAC= SRC=fe80:0000:0000:0000:<IP6 'wlp7s0b1' [IF2]> DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=220438 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[85882.647475] [UFW BLOCK] IN=wlp7s0b1 OUT= MAC= SRC=fe80:0000:0000:0000:<IP6 'wlp7s0b1' [IF2]> DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=765787 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
```

---

### Post by DGINSD on 2017-01-07
K I changed the network name to all lower case. As far as a wireless connection that had IPv6 enabled, I only had one wifi (regular 802.11?) listed in the Network Manager. There was however a Bluetooth/3G connection listed that I'm not even sure how it got there, because I never connect that way (Bluetooth is extremely buggy with Ubuntu on this machine).  So I got rid of that connection.

Also when you said "your device is only partially supported with this driver" Im currently using no proprietary module, but I can install one and wifi does work the same with it (or so it seems) as long as I also change the modules blacklist to represent the opposite of the module I'm using. My question is which one should I be using? Both experienced the same problem, so I would think my problem lay elsewhere.

What about the password having CAPS in it would that be a possible problem as well? I would guess not as my understanding of passwords is that they're kept and transmitted as hashcode and not plain text (my understanding of this is quite limited).

---

### Post by wildmanne39 on 2017-01-07
No the Caps in your password is not an issue.
> Also when you said "your device is only partially supported with this driver" Im currently using no proprietary module, but I can install one and wifi does work the same with it (or so it seems) as long as I also change the modules blacklist to represent the opposite of the module I'm using. My question is which one should I be using? Both experienced the same problem, so I would think my problem lay elsewhere.

I would keep using the same driver, I think the issue is the firewall is blocking the connection at times. I really do not have much experience with firewall settings.

Did you check the firewall setting? have you been getting disconnected since you made the last changes, if you post one more wireless script file I will look and make sure all the changes have stuck, but I do not have anymore idea at this time.

I believe working with the firewall is the answer.

---

### Post by DGINSD on 2017-01-09
I switched to the proprietary driver, did it before you posted back, but like I said I don't think that's where the problem lay and it sounds like you don't either. I get the same results regardless. Got home tonight and the network was disconnected. 

Here's another wireless script.

Is there a way to completely reset the firewall and then I'll just reset the rules I need?

---

