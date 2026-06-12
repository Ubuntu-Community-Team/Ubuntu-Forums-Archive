---
title: "Broadcom firmware for BCM4312"
date: 2011-02-18
forum: New to Ubuntu
---

### Post by CoriolanusReturns on 2011-02-18
Hi, I've just switched from XP to Ubuntu on my dell Mini 10 and it's binned my wifi firmware. I've downloaded (via USB) b42-fwcutter and broadcom-wl-4.123.10.5 firmware on to my desktop but now i'm stuck. 
 
I've had a look at other postings but they assume a certain level of knowledge about Terminal, whereas I'm now on hour 4 of Linux usage so I am not at the level whereby I can run consequtiv commands or get the system to find the files I've put on my desktop. :(
 
Can anybody help me get fw-cutter up and running and install my broadcom firmware?

---

### Post by seawolf167 on 2011-02-18
Before you start working around with that stuff, can you see if you have any entries in System -> Administration -> Hardware Drivers? I used to have to do what you were starting too, but now there are some available drivers that work alright.

---

### Post by snowpine on 2011-02-18
Welcome to the forums!

You'll find detailed Broadcom wireless instructions on the Ubuntu website:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

A couple of pointers:

1. If you need to use terminal commands (I don't think you do in this case) they are actually are easy. Simply go to Applications->Accessories->Terminal. Copy & paste the commands from the instructions to the terminal. If you get error messages and need to follow up, simply copy & paste the terminal output back into a forum post. Easy. :)

2. b43 and sta/wl are actually two different drivers and will conflict with each other. You need to figure out which is correct for your specific card. The help page I linked to above walks you through the steps.

Good luck!

---

### Post by TBABill on 2011-02-18
The BCM4312 can work with the b43 but from most any post you will find the STA (also called the "wl" driver because that's the kernel module name it uses) to be both more reliable and more stable. I have several computers with the BCM4312 and in every one of them I have tried both, with the STA outperforming b43 in speed and reliability. 
 
When you go to System>>Administration>>Additional Hardware, if you are offered the b43 and the STA drivers to choose from, I'd recommend trying the STA first. The system will take care of firmware and driver for you, just follow the prompts. If something fails, you get errors or it still will not work, post back with as much info about what you did and where the process stopped and any on-screen errors.

---

