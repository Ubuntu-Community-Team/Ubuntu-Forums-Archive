---
title: "Ubuntu Mate 16.04"
date: 2016-05-31
forum: Networking &amp; Wireless
---

### Post by misswham2 on 2016-05-31
Hi there, I just downloaded Ubuntu Mate and put it on a flash drive.  I booted on my laptop and it looks wonderful but the problem is, the wifi doesnt show up or come thru.  It only shows Ethernet and I tinkered with it and put it on wifi but its asking me questions that I have no clue how to answer.  I have been testing linux distros and installing for years via flash drive and I the wifi icon always shows up immediately.  Why has it not on this distro and how do I change that?

---

### Post by oldrocker99 on 2016-05-31
What is your wireless card? Please post the results of ```
lspci | grep Network
```

I use Ubuntu MATE and have had zero wireless problems myself. What questions are you being asked?

---

### Post by howefield on 2016-06-01
Thread moved to the "*Networking & Wireless*" forum.

---

### Post by misswham2 on 2016-06-01
Here's the results from the terminal

14:00.0 Ethernet controller: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)

It's not giving me the wireless icon in the toolbar at the top when I try to use it with the flash drive.  It is not installed so I am not on the internet when I am using the flash drive.

---

### Post by X-RED_Tech on 2016-06-03
Atheros are well supported and should work OOTB. It will not if turned off by hardware switch or BIOS/UEFI setting.

And...
I don't know Mate but I suppose it uses the same network indicator as the rest of the Ubuntu flavors except Kubuntu. There should be no specific icon/indicator for wireless networks - please correct me if I'm wrong regarding Mate -, all network devices should be listed under the same network indicator. If the wireless one doesn't show up it's probably off.

---

### Post by VideoRoy on 2016-06-04
> **X-RED_Tech said:**
> Atheros are well supported and should work OOTB. It will not if turned off by hardware switch or BIOS/UEFI setting.

And...
I don't know Mate but I suppose it uses the same network indicator as the rest of the Ubuntu flavors except Kubuntu. There should be no specific icon/indicator for wireless networks - please correct me if I'm wrong regarding Mate -, all network devices should be listed under the same network indicator. If the wireless one doesn't show up it's probably off.

I have been using Mate for while after many other distros and the indicators are the same as others.  I think I am having the same problem after my recent update to 16.04.  The wifi indicator does not show any longer but the regular ethernet icon shows in its place.  Very strange and turning off wifi in HW and back on does not fix.  

The difference for me is that I am actually connected to WiFi and it works.  Sorry if this is not the same problem but you may actually be connected if you could enter your credentials.

---

### Post by misswham2 on 2016-06-06
Thats what's going on with the live version, no indiciator but the ethernet indicator is there.  I thought I might be connected and I tried to access the interent through firefox and it says not connected and I have no clue how to connect wifi or be able to enter my code to my wifi.

---

### Post by wildmanne39 on 2016-06-06
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

