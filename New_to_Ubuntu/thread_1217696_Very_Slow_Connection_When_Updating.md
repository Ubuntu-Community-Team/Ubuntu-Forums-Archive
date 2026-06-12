---
title: "Very Slow Connection When Updating"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by Tyrsius on 2009-07-19
I am not sure what the source of this problem is. I am working with a laptop that I just ubuntu on, but ran into some problems during installation. I am hoping one of these problems resulted in a bad NIC driver, and that this can be easily resolved.

I just ran a test from Speedtest.net and got a 9/mbs down, 1.5/mbs up, 34ms ping. I tried this same test on two other computers on the network and got 2x better results.

When updating Ubuntu from the repositories I get an average connection speed of 9/kbs. Absolutely terrible. When downloading from download.com I got an average of 30/kbs, but for the first 10 seconds the connection was above 200/kbs.

I may be diagnosing the issue incorrectly, which is why I supplied all that information. However, to me it looks like a problem with this laptops network card, since no other computer on this network is having this issue. I have never had to change hardware drivers with Ubuntu, they have always just worked, so I don´t know how to updatethe drivers. If you think I am wrong about the source please let me know what you think. If you agree that its the network card driver please let me know how to update/change the driver.

---

### Post by Sitix on 2009-07-19
I suppose you don't have Windows installed next to your Ubuntu, so you can compare the results? And what happens when you use a cable on your laptop, does it still work slower or does it work fine again?

For what I know the driver used for cable connections is a different one from the wireless, so if you can get a faster result with the cable it may be a driver problem. But it also depends on the wireless capabilities of your network and your laptop.

It is a known thing that you have a short period of high internet speed at the beginning, the peak is not the actual speed you can constantly maintain. So you won't need to worry about that, pretty much everyone has it.

---

### Post by Tyrsius on 2009-07-19
No, I don't have windows next to it on the laptop having the issue, but it already is wired. This is not a wireless problem.

I am aware that you are given a boost during the beginning of a connection, but the reason I brought it up was to show that the network card was capable of using that speed, even if only for a short time.

---

### Post by pastalavista on 2009-07-19
Go to System > Administration > Software Souces and on the line it says "Download from" click the drop-down select "other" and then choose "Select Best Server"

---

### Post by Tyrsius on 2009-07-19
I tried that, and it did improve things, but not by much. Im am now averaging 18/kbs, instead of 9/kbs, but thats still pretty bad. Also, another Ubuntu machine on the network is not having this trouble, and it's still connecting to the default.

---

### Post by pastalavista on 2009-07-20
well, it just might be the driver. make sure all the third-party repositories are enabled and run apt-get update and check System > Administration > Hardware Drivers to see if there may be a better driver for your hardware.

---

