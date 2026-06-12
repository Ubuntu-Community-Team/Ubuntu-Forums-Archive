---
title: "How do I setup ndiswrapper?"
date: 2006-08-15
forum: Networking &amp; Wireless
---

### Post by mengfei on 2006-08-15
OK, I've followed these instructions

[http://ubuntuguide.org/wiki/Dapper#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29)

for this section
"lsmod | grep acx
sudo rmmod acx (only if the module was found. It could also be acx_pci or similar)
modprobe ndiswrapper"

when I enter them in the terminal, I usually don't get anything, just another prompt. So I skipped that and continued on to the next batch of instructions.

It looks like I've got everything right... (although for some reason my wireless is listed as eth1).

I entered the SSID and the pass, but using iwconfig, it doesn't seem to show me connected at all.

Can anyone help me out?

Thanks so much.

:edit:
Oh, and the card I'm using uses the BCMWL5.inf driver.

---

### Post by Darkhack on 2006-08-15
Assuming "ndiswrapper -l" lists "Hardware Present" you should do the following.

"sudo iwconfig eth1 key restricted ABCDEF123456789" <-- Enter your WEP key where those letters/numbers are

"sudo iwconfig eth1 essid NAME" <-- Replace NAME with your essid

"sudo ifup eth1" <-- enjoy

---

### Post by mengfei on 2006-08-15
OK, I did what you told me.

and yes, ndiswrapper -l does list Hardware Present
however

when i put in "sudo ifup eth1"
it says something about it already being configured

and I still can't connect.

I tried using the Networking tool to try and activate eth1, which it did, but still no Internet.

I typed in "iwconfig"
and here's what I got.

mengfei@Delphinus:~$ iwconfig
lo        
no wireless extensions.

eth0      
no wireless extensions.

eth1      
IEEE 802.11b/g  ESSID:"LANG"  
Nickname:"Broadcom 4306"
          
Mode:Managed  Access Point: Invalid   
Bit Rate=1 Mb/s
RTS thr:off   
Fragment thr:off
          
Link Quality:0  
Signal level:0  
Noise level:0
          
Rx invalid nwid:0  
Rx invalid crypt:0  
Rx invalid frag:0
          
Tx excessive retries:0  
Invalid misc:0   
Missed beacon:0

sit0      
no wireless extensions.

mengfei@Delphinus:~$


What should I do?
Thanks

---

### Post by mengfei on 2006-08-15
Yess!!
Finally figured it out!
Used the guide for Broadcom wireless cards.

However, upon getting on the internet, using Firefox and Gaim, my first comparison between Windows XP and Ubuntu is, "Wow, why is Ubuntu so slow?!!"

Not to rip on you guys or anything, no offense intended. I think it might be because I only have 512mb RAM.

::edit::

I don't mean bandwidth wise it's slow. The applications are sluggish. And my computer's pretty fast... except for the small amount of RAM.

---

### Post by Darkhack on 2006-08-15
512 is NOT a small amount.  Ubuntu should run smoothly on 256mb of RAM and a lot of people have reported atleast semi-decent performance on 128.  If the applications are that much slower than on XP, it sounds like you somehow disabled DMA.

---

### Post by mengfei on 2006-08-15
I'm sorry, but what is DMA?

To further detail what the "sluggishness" is.

It's basically, when I alt-tab between windows, it takes a split second for the window to appear, not instantaneous like windows. Like... the border might form first. It's not too much of a lag. Still pretty quick. It's just enough to be noticeable.

Also, you know the new Yahoo webpage? How you hover your mouse over the mail icon and it gives you a small preview of your mail? Well, when I hover in Windows, it slides open smoothly, using Firefox. With Ubuntu and Firefox, it's has a really jerky animation, and is not smooth at all.

I'm currently running Automatix, installing a bunch of things (not while I was noticing the sluggishness though). I'm hoping after these installs, things will run more smoothly.

And, again, what is DMA, and how do I know if I disabled it?

Thanks

---

### Post by haiku99 on 2006-08-15
check out the installation instructions at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
that has worked well for me (so far, did it today) and I'm using the same drivers...

---

### Post by mengfei on 2006-08-16
OK, after updating everything, FireFox runs much more smoothly.

I guess I was just missing something?

---

