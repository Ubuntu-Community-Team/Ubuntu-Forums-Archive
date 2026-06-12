---
title: "D-Link DWA-131 Adapter Low signal Strength.Same adapter gives full signal strength in"
date: 2018-02-09
forum: Networking &amp; Wireless
---

### Post by blaine12100 on 2018-02-09
Hello People

I have purchases a small D-link DWA 131(Hardware Version-E1)  Wifi-Adapter and i have installed the necessary drivers for the same.But  the Adapter gives me a low signal strength when the wifi router is in  the next room and when i use this adapter in windows,it gives me a good  full signal strength.Any ideas how can i fix this?
  I am using Ubuntu 17.10

Link for Pastebin-[https://paste.ubuntu.com/26546530/](https://paste.ubuntu.com/26546530/)

This link contains the output of the wireless script mentioned in the forums.And i also have a Broadcom Adapter in-Built which is not very good that is why i am using the D-Link DWA-131 Adapter(USB).

---

### Post by wildmanne39 on 2018-02-09
There is another driver we can try and it will probably work better, I am curious what exactly is wrong with your internal card? broadcom devices are usually pretty reliable.

Please Do:
```

sudo apt install git
git clone https://github.com/Mange/rtl8192eu-linux-driver.git
cd rtl8192eu-linux-driver
make
sudo make install 
sudo modprope -rv rtl8xxxu
sudo modprobe 8192eu
```
do not reboot, if this driver works better we will have to blacklist the rtl8xxxu driver.

You will have to recompile this driver every time the kernel is upgraded.

---

### Post by cruzer001 on 2018-02-09
> You will have to recompile this driver every time the kernel is upgraded.

Would dkms work in this case.

---

### Post by wildmanne39 on 2018-02-09
> **cruzer001 said:**
> Would dkms work in this case.

It can but the last I read there was issues with the dkms package in this driver and the driver was having to be installed without the dkms package in order for it to work,  have not read that it is fixed yet.

---

### Post by blaine12100 on 2018-02-10
i believe the Broadcom WiFi chip in my laptop has been physically damaged since my laptop has fallen/knocked over a couple of times.Specifically the antennae.

I will try the solution after some time and let you know.If it works,then can i shut the system down later?

Edit.Did the installation and Signal Strength Has Increased.

---

### Post by wildmanne39 on 2018-02-10
If you shut it down before we blacklist the driver it is using now when you start it up again it will load both drivers and they will conflict.

I am not sure if that driver will compile on your computer, I have a third party kernel on my computer so I can run amd graphics and it will not allow me to compile any drivers or packages so I could not test it on my computer.
 
You will need to also have kernel headers and build essential installed to compile the driver, you can install them with the following command.
```
sudo apt install --reinstall linux-headers-$(uname -r) build-essential
```
Run the above command first.

Thanks

---

### Post by blaine12100 on 2018-02-10
I installed the headers as requested.Immediately i can notice a increase in signal strength(Between 3-4 or Good/Excellent.)

But i still have a bit of an issue wherein if i go to the corner-most part of the room,the wifi is connected but no data is able to pass through(Although other devices can connect just fine)

And the Device's LED does not light up.Is it an issue?

And how can i blacklist the driver.?

Extremely sorry as i have only used Ubuntu for about a month.

Sometimes i also have an issue like the one shown in the screen shot.

---

### Post by wildmanne39 on 2018-02-10
Before I give instructions to blacklist the driver please run and post the wireless script again so we can see if there is more we can do to make your connection more stable and we will double check that you are using the driver that you compiled. 

Thanks

---

### Post by blaine12100 on 2018-02-10
Link for Pastebin Output after Running Script.
[http://paste.ubuntu.com/=vqRghTQ325/](http://paste.ubuntu.com/=vqRghTQ325/)

---

### Post by wildmanne39 on 2018-02-10
Both drivers are loaded so we will blacklist the original driver then we will see how your connection is with just the new driver loaded.

Please do:
> echo "blacklist rtl8xxxu" | sudo tee -a /etc/modprobe.d/blacklist.conf
Then:
```
sudo modprobe -rv rtl8xxxu
sudo modprobe -v 8192eu
```
Let us know how it is working after blacklisting the original driver please.

Thanks

---

### Post by blaine12100 on 2018-02-10
Did as you had instructed.So if i shut down the system now,will the driver conflict arise now?

Wifi is Working Right now with signal strength going from 60% to 100% and Link quality goes in the same range.

And i have also noticed that sometimes even if the signal quality is good(monitoring via watch -n1 iwconfig),the WifI signals gets replaced by a Question Mark.

Any idea why does that happen?

---

### Post by wildmanne39 on 2018-02-10
Yes you can reboot now without the original driver loading again. 
> And i have also noticed that sometimes even if the signal quality is good(monitoring via watch -n1 iwconfig),the WifI signals gets replaced by a Question Mark.

Any idea why does that happen? 
No I do not know, it could be that the signal is going up and down and can not be seen, just test it out and see if it is better if so please mark the thread solved using thread tools at the top of the page.

It does sound like the signal strength is a lot better, if you have a kernel upgrade you will have to do:
```
cd rtl8192eu-linux-driver
make clean
make
sudo make install 
sudo modprobe 8192eu
```
It is possible that this driver is now working with dkms and if so you can install it using another method and you will not have to compile it every time you have a new kernel upgrade but as I said I am not sure it is working that is why I went with this method.

---

### Post by blaine12100 on 2018-02-10
Ok.I will try this out for a couple of days.If it works properly i shall accept this answer.Will that be ok?

---

### Post by jeremy31 on 2018-02-10
Here we use the thread tools menu near the top right of the page to "mark as solved"

---

### Post by wildmanne39 on 2018-02-10
Yes, that is okay.

---

### Post by wildmanne39 on 2018-02-10
Hi jeremy31, do you know if this driver is working with dkms without editing any files as of now?

I figure he meant mark as solved when he said accept the answer since I had posted about marking the thread as solved.

---

### Post by jeremy31 on 2018-02-10
Hi wildmanne39
I was not aware of any dkms issues with Mange's github, it should work

---

### Post by wildmanne39 on 2018-02-10
Thanks jeremy31, I will wait and see how his connection is working when he posts again.

---

### Post by blaine12100 on 2018-02-16
Hi

Have been using the updated drivers for the past 5 days.Working very smoothly with no signal drops and disconnects whatsoever.Have marked the answer as solved.

Could you look at another question of mine [https://ubuntuforums.org/showthread.php?t=2384741](https://ubuntuforums.org/showthread.php?t=2384741).

---

### Post by wildmanne39 on 2018-02-16
I am glad your wifi is working well and thanks for marking the thread solved!

I only work with wifi issues, jeremy31 works with bluetooth but I doubt it is a bluetooth issue, it sounds like a sound issue, so I am going to move your thread to the proper sub-forum.

---

