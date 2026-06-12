---
title: "Intel 7260 starting to falter. Ubuntu 15.10."
date: 2016-02-02
forum: Networking &amp; Wireless
---

### Post by warren3 on 2016-02-02
Hi.

I have a Intel 7260 and I am running Ubuntu 15.10.  At first when I installed Ubuntu 15.10 I had a RTL8723AE card but that wasn't working too well so I was told to try the Intel 7260 which I had lying around.  This worked fine but now Its starting to take a long time to connect to my network on a fresh boot.  I am also experiencing horrendous pings on Quake 3 at random times.  At first I thought it might be my ISP but I have a hunch its the card.

I have attached the tar.gz file.

[ATTACH]267079[/ATTACH]

---

### Post by Hadaka on 2016-02-02
Hi, your wireless report shows..
```
iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7260-15.ucode failed with error -2
iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7260-14.ucode failed with error -2
```

Try this...Post #2
[http://ubuntuforums.org/showthread.php?t=2300362](http://ubuntuforums.org/showthread.php?t=2300362)

you also need to ..please copy and paste..
```
sudo iw reg set GB
sudo sed -i 's/^REG.*=$/&GB/' /etc/default/crda
```

---

### Post by chili555 on 2016-02-02
For the information of both of you, I have a 7260 in one of my laptops and, in order to both boost its performance and achieve N speeds, I installed backports-4.4-rc2-1 and also the 7260 firmware files from here:  [https://github.com/OpenELEC/iwlwifi-firmware.git](https://github.com/OpenELEC/iwlwifi-firmware.git)

Now, my system loads the -17 firmware:> loaded firmware version [COLOR="#FF0000"]17[/COLOR].265642.0 op_mode iwlmvmI expect that Hadaka will skilfully guide you through the steps.

---

### Post by Hadaka on 2016-02-03
Hi, please try this gift from chili555.

Download this file to your desktop: [https://www.kernel.org/pub/linux/ker...4-rc2-1.tar.gz]("https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.4-rc2/backports-4.4-rc2-1.tar.gz") Right click it and select 'Extract Here.' Now, in the terminal:

```
cd ~/Desktop/backports-4.4-rc2-1
make defconfig-iwlwifi
make
sudo make install
```

Now, let's get the firmware:

```
sudo apt-get update
sudo apt-get install git
git clone [https://github.com/OpenELEC/iwlwifi-firmware.git](https://github.com/OpenELEC/iwlwifi-firmware.git)
cd iwlwifi-firmware/firmware
sudo cp iwlwifi-7260*  /lib/firmware
```

Reboot and check:

```
dmesg | grep iwl
```

You should see the 17.xx firmware loaded as well as a better, more stable connection.

After a newer kernel version is installed, after the requested restart, you must recompile:

```
cd ~/Desktop/backports-4.4-rc2-1
make clean
make defconfig-iwlwifi
make
sudo make install
```

---

### Post by warren3 on 2016-02-03
Hi.

I get upto command:

[I]cd linux-firmware/firmware
[/I]
...and i get this back 

*bash: cd: linux-firmware/firmware: No such file or directory*

Am I doing something wrong?

---

### Post by chili555 on 2016-02-03
Ooops! Sorry. Please substitute:```
cd iwlwifi-firmware/firmware
```And then proceed as before.

---

### Post by warren3 on 2016-02-03
Hi.

Thanks for the quick reply.  

I now see this after dsmeg command

[I][    3.163266] iwlwifi 0000:02:00.0: enabling device (0000 -> 0002)
[    3.183307] iwlwifi 0000:02:00.0: loaded firmware version 17.265642.0 op_mode iwlmvm

[/I]plus loads of other stuff.

When I rebooted wifi connected quicker to my network.

Thank you both of you!

Fingers crossed everything will be a lot better now!

---

### Post by Hadaka on 2016-02-03
Glad to hear the good news, and i have corrected the mistype.
did set your country code?, it is important that you do.
```
sudo iw reg set GB
sudo sed -i 's/^REG.*=$/&GB/' /etc/default/crda
```

*special thanks to chili555 !

---

### Post by warren3 on 2016-02-03
Hi.

I tried the country code but on the second command I get this 

[I]sed: -e expression #1, char 14: unknown option to `s'

[/I]Cheers

---

### Post by warren3 on 2016-02-03
Hi.

I put in 

sudo sed -i 's/^REG.*=$/&GB/' /etc/default/crda

...that I saw from another one of your threads about wireless problems and I did not get any error message this time.  Hopefully that worked?

---

### Post by Hadaka on 2016-02-03
Another typo, please acccept my apology. Please copy and paste.

```
sudo sed -i 's/^REG.*=$/&GB/' /etc/default/crda
```
thanks.

---

### Post by warren3 on 2016-02-03
Hi.

All done.

Early signs are not too good.  It connects to my network a bit faster but web browsing is slow to loads pages and my Quake 3 ping is the worst I have seen.  It should be 50ms (like it was a few weeks ago) but now it is anywhere between 200ms and 800ms and the Quake 3 network icon show a lot of problems with the connection.

Speedtest.net shows a solid 5.7mbs for my tablet and phone but Ubuntu is struggling to get 3.5 and its up and down.

What do you think?  

Could you recommend another half height PCI card or another card because I think I am at the end of the line with the 7260.

---

### Post by Hadaka on 2016-02-03
Hi, i would suggest running the wireless script again and see
what may have changed.
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
thanks

---

### Post by warren3 on 2016-02-03
Hi Hadaka.

I tried Q3 again and the ping improved to about 80ms-100ms.  A bit better.  It weird though on the server screen when you ping for servers 1st time the pings are horrendous and then you ping again about 10 seconds later and they are ok-ish.  It keeps on alternating between bad and good.

Here is the new wireless script :)

[ATTACH]267104[/ATTACH]

---

### Post by Hadaka on 2016-02-03
Give this a go and see if it impoves..
    ```
sudo modprobe -r iwldvm
sudo modprobe -r iwlwifi
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf 
```
then disable IPV6..
#In Firefox
     Code:
     [http://ccm.net/faq/758-myth-disabling-ipv6-will-speed-up-internet-connections](http://ccm.net/faq/758-myth-disabling-ipv6-will-speed-up-internet-connections) 
# In ubuntu
     Code:
     [http://askubuntu.com/questions/440649/how-to-disable-ipv6-in-ubuntu-14-04](http://askubuntu.com/questions/440649/how-to-disable-ipv6-in-ubuntu-14-04) 
# In Network Manager -> IPv6 #See attached
[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=267105&d=1454542339&thumb=1[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=267105&d=1454542339")

---

### Post by warren3 on 2016-02-07
I just thought I would give a quick update.

Just for anyone else in the same boat I followed everything apart from post #15 and now it is working.  

What I did was I just turned off bluetooth and voila it is back to how it was when I first installed Ubuntu.  Q3 ping is 40ms and connecting to a network is super fast.

So thanks Hadaka and Chili555 for your help.

I will mark as solved.

---

### Post by Hadaka on 2016-02-07
Glad you were able to get an acceptable rate. If you notice in your
wireless-info.txt file toward the bottom of the report is your dmesg
info. When starting your wireless,by default IPv6 tests to see if there
is a connection, so if you are not using IPv6,shutting it down will save
you some process time. As is not causing any harm.

---

