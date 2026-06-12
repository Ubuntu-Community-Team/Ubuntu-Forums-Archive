---
title: "Ubuntu 12.04 lts wireless/wifi problem"
date: 2013-10-05
forum: Networking &amp; Wireless
---

### Post by Filip_Lundberg on 2013-10-05
Hi :) I installed Ubuntu 12.04 for a week ago but my wifi/wireless don't work. I have read many threads about how to solve this problem but none work :( I hope someone here can help me!



Thank you :)

---

### Post by Bucky Ball on 2013-10-05
Welcome. Open a terminal and post these two commands in, one at a time hitting return after each:

```
sudo lshw -C network
iwconfig
```

You will need to put your password in after the first command. Post the output of each back here, please.

---

### Post by Filip_Lundberg on 2013-10-05
[http://tinypic.com/r/345jv4w/5](http://tinypic.com/r/345jv4w/5)

Here you have :) What to do next? :)

---

### Post by Bucky Ball on 2013-10-05
Can you get this machine online with a cable? That will make fixing it much easier. Your card is identified as Broadcom BCM4321. It will work without issue but, as I mention, if you can get online with a cable it should be simple enough.

---

### Post by Bucky Ball on 2013-10-05
If you can't get a cable to the machine (or if you can) this page will help:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access)

---

### Post by Bucky Ball on 2013-10-05
If you can't get a cable to the machine (or if you can) this page will help:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access)

---

### Post by Filip_Lundberg on 2013-10-05
I can't connect through an Ethernet cable. But which firmware should I download?

---

### Post by Filip_Lundberg on 2013-10-05
Sorry for asking so much :) 

Should I download b43 legacy , b43 (10.04 lucid lynx) or b43 (12.04 precise pangolin) firmware file?

---

### Post by Bucky Ball on 2013-10-06
b43-fwcutter
firmware-b43-installer

One you can get from the install disk, one you cannot. Follow the link I posted. ;)

---

### Post by Filip_Lundberg on 2013-10-06
I don't find the firmware-b43-installer on the link, but can I download it from here [http://packages.debian.org/sv/squeeze/firmware-b43-installer](http://packages.debian.org/sv/squeeze/firmware-b43-installer)? Or is it wrong?

---

### Post by Bucky Ball on 2013-10-06
Do you have b43-fwcutter installed from the Ubuntu install CD? If not, do that. Then you need to get the firmware-b43-installer for 12.04 (not legacy) from step 2 in the link below, the one named 'b43 (12.04 Precise Pangolin)'. Click on the link and save it to somewhere you will remember:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access)

Then, in a terminal, navigate to the folder you've saved that to. For, instance, if it is in /home/Downloads, then:

```
cd /home/Downloads
```

Then, one after the other and hitting return after each, issue these two commands:

```
tar xfvj broadcom-wl-5.10.56.27.3_mipsel.tar.bz2
sudo b43-fwcutter -w /lib/firmware broadcom-wl-5.10.56.27.3/driver/wl_apsta/wl_prebuilt.o
```

Restart. Report what happened. ;)

---

### Post by Filip_Lundberg on 2013-10-06
First I downloaded these 2 files from another computer and then I moved them to an USB and then to my Ubuntu computer with no wifi. I put the files into home/downloads [http://tinypic.com/r/ojnzr/5](http://tinypic.com/r/ojnzr/5). Then I wrote the code "cd /home/downloads" but then terminal answered "no such file or directory" . 

I don't know what to do, I really suck at these.

---

### Post by Filip_Lundberg on 2013-10-06
.have I done everything wrong? :(

---

### Post by Bucky Ball on 2013-10-06
Ok. We'll try and do this step by step. Just in case you haven't done it yet, install b43-fwcutter, thus:

1/ Boot into Ubuntu. Once you're at the desktop, insert the CD you installed Ubuntu with.
2/ Open a terminal and apply these two commands, one at a time, hitting return between each (wait for each to do their thing and you're back at a cursor before applying the next command):

```
cd /cdrom/pool/main/b/b43-fwcutter/
sudo dpkg -i b43-fwcutter*
```

Now, download this file:

b43 (12.04 Precise Pangolin) - [http://mirror2.openwrt.org/sources/broadcom-wl-5.10.56.27.3_mipsel.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-5.10.56.27.3_mipsel.tar.bz2) 

(From the link given in the other posts.) Once you have that copy it to your /home folder, then these two commands, one after the other with return between:

```
tar xfvj broadcom-wl-5.10.56.27.3_mipsel.tar.bz2
sudo b43-fwcutter -w /lib/firmware broadcom-wl-5.10.56.27.3/driver/wl_apsta/wl_prebuilt.o
```

Reboot the computer and see what happens. At the least, we should have b43-fwcutter and firmware-b43-installer installed. 

If you have any probs, post back. If you get that done and restart and you get nothing, run this command:

```
iwconfig
```

... and post the result. ;)

PS: Absolutely no way you can get an ethernet cable to the computer? Anyways, let's hope this works.

---

### Post by Filip_Lundberg on 2013-10-06
Thank you, I will test this tomorrow ;) 

I have an Ethernet cable, But  I don't get internet even if I connect it to the computer :( Is it easier if I use the Ethernet cable or what is it? :)

---

### Post by Bucky Ball on 2013-10-06
Plug the ethernet cable in and run this command:

```
ifconfig
```

Post back the result. Also with the cable in, does the network icon say it's connected?

---

### Post by Filip_Lundberg on 2013-10-07
Thank you mate :) I got internet through the ethernet cable now, but when I try to get it through wireless, it's not working. How do I get through wireless now? Should i make the command that you post before or is it anything easier now when I can get internet through the cable??

---

### Post by Bucky Ball on 2013-10-07
You have ethernet working? Great. MUCH easier. 

1/ Open 'Update Manager' and do an update. It could come up with a lot of stuff, but that's fine: hit 'Install';
2/ Open 'Additional Drivers'. Is there anything there mentioning 'b43'? If so, enable it.

You may need to restart or the wireless may start working straight away.

* If there is nothing in 'Additional Drivers':

1/ Open Software Centre (or Synaptics, whichever you're using), search for and install:

b43-fwcutter
firmware-b43-installer

2/ Unplug the cable, restart and you should be there. If not, report back, but shouldn't be far away. ;)

---

### Post by Filip_Lundberg on 2013-10-07
I found a driver called Broadcom STA wireless driver, then I enabled/installed the driver and now the wireless working perfect :) Thank you so much man, you are awesome :)I hope I can be as good as you in the future so I can help people like you helped me ;)

Thank you very much and I'm very thankful for the help you gaved me ;)

---

### Post by Bucky Ball on 2013-10-07
All good. Glad you got it working. The STA driver can be flaky for some Broadcom cards but seems to be working for you so enjoy! If you have any issues, swap to the b43 (just disable the STA and refer back to this thread). 

Good luck, and please mark as 'solved' to help others from 'Thread Tools' at top right. ;)

PS: Did you find the STA driver in 'Additional Drivers'?

---

### Post by Bucky Ball on 2013-10-07
All good. Glad you got it working. The STA driver can be flakey for some Broadcom cards but seems to be working for you so enjoy! If you have any issues, swap to the b43. 

Good luck, and please mark as 'solved' to help others from 'Thread Tools' at top right. ;)

---

### Post by Filip_Lundberg on 2013-10-08
How do I change to the b43 driver? It can be nice to know if I should get any problems in the future ;)

Yes, I found the STA driver in 'additional drivers' ;)

And thank you for all help :)

---

### Post by Bucky Ball on 2013-10-08
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Switching_between_drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Switching_between_drivers)

You'd follow the stuff for b43. Probably the easiest would be to disable the STA driver and install b43-fwcutter and firmware-b43-installer, restart and see what happens. You may need to blacklist a thing or two. Never tried it. Never used the STA (as it didn't like the card on a HP laptop which I no longer have).

If you want to start a new thread asking how to switch between the two, feel free. ;)

---

### Post by Bucky Ball on 2013-10-08
[https://help.ubuntu.com/community/Wi...etween_drivers](https://help.ubuntu.com/community/Wi...etween_drivers)

You'd follow the stuff for b43. Probably the easiest would be to disable the STA driver and install b43-fwcutter and firmware-b43-installer, restart and see what happens. You may need to blacklist a thing or two. Never tried it. Never used the STA (as it didn't like the card on a HP laptop which I no longer have).

If you want to start a new thread asking how to switch between the two, feel free (but try the above first).

---

