---
title: "Odd Intel LAN problem (no Internet)"
date: 2014-02-06
forum: Networking &amp; Wireless
---

### Post by evilkillerwhale on 2014-02-06
I have an ASRock Z87 Extreme4 motherboard with an Intel 1217-v gigabit LAN adapter. During install of Ubuntu, I was given an error saying my router probably wasn't using DHCP. It is, and with my previous motherboard, Ubuntu (from the same USB installer of 13.10 server) connected to the Internet fine. The only change is that I've swapped motherboards and processors. Router did not go offline, etc. 

I figured, maybe the problem was just limited to install. But of course, once I'm in Ubuntu, I can see the adapter fine, but cannot connect to the Internet. I cannot even see the router. I wondered if e1000e was out of date, but due to the inability to get to the Internet, I can't even make the installer for Intel's e1000e ver. 2.5.4, as downloaded from the website as the proper Linux driver for that LAN chipset. 

I'm pretty much at a loss here. Should I try to download the packages for "make" and get those installed so that I can try updating the LAN driver? 

Also, this is my first shot with Ubuntu, and I've never been great with Linux. I haven't used Linux other than when I needed Knoppix for hard drive recovery or when I installed the original Fedora Core as a test bed one time. Go easy on my ignorance :P

---

### Post by varunendra on 2014-02-06
Welcome to the forums evilkillerwhale!

The driver for e1000e adapters already exists in the kernel, you shouldn't need to compile one (unless your adapter is a very new variant of these chips).

Please open a terminal (Ctrl-Alt-T) and run the following command in it-
```
sudo lshw -numeric -C network
```
..and post back its entire output here. You may copy-paste the output using your mouse cursor from terminal to a text file, then either attach this file into your next post, or copy-paste its contents here. If you have to open the file in windows, make sure to choose "Line Ending" to "Windows" while saving it, otherwise its text would appear all messed up in windows.

While posting the output, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

