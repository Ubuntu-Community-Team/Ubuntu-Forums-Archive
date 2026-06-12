---
title: "Updated driver r8712u ---&gt; r92su?"
date: 2014-03-20
forum: Networking &amp; Wireless
---

### Post by scollar1971 on 2014-03-20
I read that r92su(old as dirt) was to be replaced by r92su so I have been trying this because my chipset was said to be listed when I attempt this update I get this from dmesg any help would be greatly apreciated

[  608.083589] r92su: module verification failed: signature and/or required key missing - tainting kernel
[  608.084503] usbcore: registered new interface driver r92su

---

### Post by chili555 on 2014-03-21
That is a completely harmless warning. Did the driver otherwise work? Please tell us a few things from the terminal:```
lsusb
lsb_release -d
```Thanks.

---

### Post by scollar1971 on 2014-03-21
root@sean-Dimension-4700:/home/sean# lsb_release -d
Description:    Ubuntu 13.10


Bus 001 Device 005: ID 050d:945a Belkin Components F7D1101 v1 Basic Wireless Adapter [Realtek RTL8188SU]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

dmesg 

[33091.272632] r8712u 1-8:1.0 wlan0: r8712_got_addbareq_event_callback: mac = 04:a1:51:1b:61:1c, seq = 2832, tid = 0

What is this?

Driver did not trying to retrace my steps so I can give you some more useful info

One more question I have is why lsusb diplays device as 
Bus 001 Device 005: ID 050d:945a Belkin Components F7D1101 v1 Basic Wireless Adapter [Realtek RTL8188SU]

when in reality it is f9l1001v1 ?

---

### Post by varunendra on 2014-03-21
Please keep all your questions/outputs in a single post. Multiple posting when a single post could do makes the thread unnecessarily longer and causes unnecessary bumps which may be frowned upon here.

---

### Post by chili555 on 2014-03-21
> **scollar1971 said:**
> One more question I have is why lsusb diplays device as 
Bus 001 Device 005: ID 050d:945a Belkin Components F7D1101 v1 Basic Wireless Adapter [Realtek RTL8188SU]

when in reality it is f9l1001v1 ?Because *lsusb* doesn't read the cardboard box; it reads the details coded into the chip. I suspect that Belkin may have added some trivial software feature to their CD and called it an F9L1001v1 instead of the previous F7D1101v1. I also suspect they charged another few dollars for it.> so I have been trying this because my chipset was said to be listedIn fact, r92su does cover your device. In order to use it, you'll need to blacklist r8712u. Did you? Which one or ones are actually loading?```
lsmod | grep -e r92 -e r8712u
```

---

### Post by scollar1971 on 2014-03-21
grep -e r92 -e r8712u responds

r92su                  50498  0 
cfg80211              401762  1 r92su
r8712u                158706  0 

Which means I am currently using it correct? And I have read about blacklisting however I have not performed this operation                          personally

Subsiquently f9l1001v1 was gotten from the label adhered to device

---

### Post by chili555 on 2014-03-21
> **scollar1971 said:**
> grep -e r92 -e r8712u responds

r92su                  50498  0 
cfg80211              401762  1 r92su
r8712u                158706  0 

Which means I am currently using it correct? And I have read about blacklisting however I have not performed this operation    	 	 	 	   personallyIt means your system is loading and trying to use *both!* Let's blacklist r8712u and see if performance improves, degrades or is the same:```
sudo -i
echo "blacklist r8712u"  >>  /etc/modprobe.d/blacklist.conf
modprobe -r r8712u
exit
```Now try again:```
lsmod | grep -e r92 -e r8712u  
```Ideally, only r92su is loaded. How is performance?

---

### Post by scollar1971 on 2014-03-21
Performance is fine my goal was hopefully enabling monitor mode and possibly packet injection which I haven't been able to accomplish. By the way this is solely for pentesting the integrity of the LAN at my small automotive repair shop and only to ensure the security of my customers ... plus I enjoy learning

Ok appear to have lost my wlan0 ..... hmmmm

I have lost wlan0

---

### Post by chili555 on 2014-03-21
Did you try a reboot? Are there any clues as to the problem?```
dmesg | grep -e r92 -e rtl
```

---

### Post by scollar1971 on 2014-03-21
I have rebooted twice once with adapter installed and once without and then installed


dmesg | grep -e r92 -e rtl - no response

lsusb shows device present dmesg doesn't show me anything different I now have no connectivity

---

### Post by scollar1971 on 2014-03-21
Wondering if anyone can help me regain my wireless connection blacklisted driver and now I have no wireless networking

---

### Post by chili555 on 2014-03-21
What version of r92su did you compile? If you know that r8712u drives your device correctly, load it manually until we do additional troubleshooting:```
sudo modprobe r8712u
```

---

### Post by chili555 on 2014-03-21
Please return to your original post and continue there.

---

### Post by QIII on 2014-03-21
Threads merged, several posts merged.

Please do not create extraneous posts.  Please do not start new threads on the same subject.

Thanks.

---

### Post by scollar1971 on 2014-03-21
sudo modprobe r8712u responds

FATAL:Module 8712 not found

---

### Post by chili555 on 2014-03-21
> FATAL:Module 8712 not foundAre you quite certain it was typed correctly?```
sudo modprobe[COLOR="#FF0000"] r[/COLOR]8712[COLOR="#FF0000"]u[/COLOR]
```We know it exists in your system because we saw it here:> grep -e r92 -e r8712u responds

```
r92su 50498 0
cfg80211 401762 1 r92su
r8712u 158706 0

```
Which means I am currently using it correct? And I have read about blacklisting however I have not performed this operation personally

---

### Post by scollar1971 on 2014-03-21
Thank you I'm back to where started from and slightly more educated too have any insight as to what happened?

---

### Post by chili555 on 2014-03-21
> **scollar1971 said:**
> Thank you I'm back to where started from and slightly more educated too have any insight as to what happened?First, let's remove the r8712u blacklist. Please do:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Find the line that we added that says:```
blacklist r8712u
```Comment it out so it no longer loads:```
**#**blacklist r8712u
```We comment it out so we can re-use it again when we need it. Proofread, save and close gedit.

I suspect what went wrong is that the version of r92su you compiled doesn't actually claim your device. Check:```
modinfo r92su | grep 945A
```If you draw a blank, then the version you compiled is too old. I have a version on my machine that does and we can compile it if needed:```
$ modinfo Desktop/Forum/rtl8192su-master/r92su/r92su.ko | grep 945A
alias:          usb:v[COLOR="#FF0000"]050D[/COLOR]p[COLOR="#FF0000"]945A[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*
```There is your device:> ID [COLOR="#FF0000"]050d:945a[/COLOR] Belkin Components F7D1101 v1 Basic Wireless Adapter [Realtek RTL8188SU]We'll proceed when we have more information.

---

### Post by scollar1971 on 2014-03-21
Your prosumption correct 
modinfo r92su | grep 945A responds

ERROR: Module r92su not found.

Got mine from [https://github.com/chunkeey/rtl8192su/tree/master/r92su](https://github.com/chunkeey/rtl8192su/tree/master/r92su)

---

### Post by chili555 on 2014-03-21
Did you type it correctly? We know it's there:> grep -e r92 -e r8712u responds

```
r92su 50498 0
cfg80211 401762 1 r92su
r8712u 158706 0
``` 

---

### Post by scollar1971 on 2014-03-21
It was a typo as suspected

---

### Post by scollar1971 on 2014-03-21
Ok now I'm learning this forum a little better sorry for making a mess out of this thread and the 'bumps' I've created but moving forward ...

Commented out 
**#**blacklist r8712u

now what would be my proper procedure for compiling the correct version of r92su ?

---

### Post by chili555 on 2014-03-21
First, I'd remove the one you have now so we don't create a conflict. Repeat the process you followed previously:```
cd ~/Desktop/rtl8192su_files
```Or wherever you extracted the original files. Substitute the exact name of the file you extracted and compiled. Be very careful of typos. Now do:```
sudo make uninstall
```I can't quite give you much guidance here because I don't know what you installed or where you got it.

Now, let's install the new one:```
sudo apt-get install git 
sudo apt-get install --reinstall linux-headers-generic
sudo apt-get install --reinstall build-essential
git clone https://github.com/chunkeey/rtl8192su.git
cd rtl8192su
make
sudo make install
```You may safely copy and paste those commands into the terminal. Note and post any errors. Now go back and un-comment the blacklist. If everything goes well, reboot and enjoy.

DISCLAIMER: I know nothing about packet injection, aircrack, airhack or any of that. I don't want to know. I can help you install a driver but then you are on your own.

---

### Post by scollar1971 on 2014-03-21
I admire your 'DISCLAIMER:' and understand fully just would like it known my intentions are genuine and if anyone has doubts please let me know how to ease their minds

---

### Post by QIII on 2014-03-21
We would not condone any discussion of pen testing anyway and would close the thread.

So long as it's just about the driver, play on.

---

### Post by scollar1971 on 2014-03-21
That makes sense to me

---

### Post by scollar1971 on 2014-03-21
I appear to have made a mess in my fumbling around I am having difficulty removing the files I am trying 
sudo make uninstall (not in Desktop) so I replaced Desktop with the loaction I had extracted the original files to that didn't work

responds
make: *** No rule to make target `install'.  Stop.

---

### Post by chili555 on 2014-03-21
Where is it? Downloads?```
cd ~/Downloads
```Now list the contents:```
ls
```Is the rtlwhatever drivers file in there? Change directories to the rtl drivers file, whatever it is actually named:```
cd rtlwhatever
```List the contents:```
ls
```Do you see Makefile? Awesome!```
sudo make uninstall
```

---

### Post by scollar1971 on 2014-03-21
Well now I really feel foolish but I cannot seem to get this to work .... I've double checked using history command and realize mistakes I've made now being quite green and misguided by others I created a directory and extracted to that directory the file I downloaded yes I see makefile there

    	 	 	 	> sean@sean-Dimension-4700:~/rtl8192su-master/rtl8192su-master$ ls
eeproms    Makefile  README.md  rtlwifi  TODO
firmwares  r92su     rtl8192su  staging
sean@sean-Dimension-4700:~/rtl8192su-master/rtl8192su-master$ sudo make uninstall
make: *** No rule to make target `uninstall'.  Stop.
sean@sean-Dimension-4700:~/rtl8192su-master/rtl8192su-master$ 

---

### Post by chili555 on 2014-03-22
Don't feel foolish. I went to the trouble to find this file and read the Makefile. There is, remarkably, no 'uninstall' process defined! Let's use the brute force method; that is, a bigger hammer!```
modinfo r92su | grep filename
```You will see something approximately but not exactly like */lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/rtlblah/r92su.ko*. Of course, substitute the exact location and name you found.

We are going to manually delete the thing you just found. Either copy and paste or type carefully and, as I do always, proofread carefully twice.```
sudo rm /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/rtlblah/r92su.ko
```Again, proofread carefully before you press the Enter key, there are no oopsies.

Now proceed to install the later package as I outlined above.

---

