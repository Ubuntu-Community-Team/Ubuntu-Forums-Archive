---
title: "Wireless problem with rtl8187b net work card"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by sadaruwan12 on 2010-05-05
Well I installed 10.04 UNE on my netbook which has a rtl8187b chipset based network card.

Ubuntu detects my card and it also list's all the available wireless networks in the area but my problem is when try to one it just try pairing with wireless router get disconnected.

But when I checked the signals strength the wireless network manager shows good strength.

So put a wireless router very near to my Netbook and tried then it got paired and started to work but when I moved just to small distance it got disconnected.

I don't know why this is happening is there any thing I can do to get connected.

---

### Post by mosse-r on 2010-05-05
same problem here with that driver on lucid Desktop edition 32 bit, I have tried ndiswrapper but no luck, wifi works perfectly just beside the router but no further than a few meters and its unuseable, it drops the connection every couple of minutes when you are lucky enough to be able to connect. 

That same laptop running windows has no problems (its not mine i swear :razz:), also my own laptop also running lucid 10.04 has no trouble. please help

here is iwconfig for the connection when it is away from the router:

```

IEEE 802.11bg  ESSID:"MAGNET-6868"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:03:6F:95:2E:5A   
          Bit Rate=12 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

also I set the rate to 12M myself but it didn't help it was at 1M


any help would be greatly appreciated

---

### Post by sadaruwan12 on 2010-05-05
is there any kind of a solution please help.

And I like to invite all the people who have wireless problems to post to this thread.

Thank you

---

### Post by sadaruwan12 on 2010-05-05
Are there's no solution for this please help.

And I like to invite all the people who have wireless problems to post to this thread.

Thank you

---

### Post by steve161 on 2010-05-05
Have the same card and my wireless was not recognized.  After some googling, ran "sudo modprobe rtl8187" (without quotes) in terminal, and now have wireless.  So simple, I have my doubts it will work for everyone's problem, but it is worth a try.

You may need to reboot (I, however, didn't)

**Edit**:  I should read these posts more carefully.  I had no wireless connection before I ran the above command, so it seems to be a different issue.  I was going to delete my post, but I'll leave it as it may just work anyway or help someone with the same issue I had.  Carry on.

---

### Post by sadaruwan12 on 2010-05-07
My card gets detected and all the wireless network signals are show in the list but when I try to connect what happens is my card doesn't get connected but when go right under the accesses point it gets connected but when I move from that lace the wireless network goes down.

Y don't any one have a solution and I tried ndiswrapper but with the same kind of results. But the signal strengths are very low I don't know what to do please help me.

---

### Post by sadaruwan12 on 2010-05-07
bump

---

### Post by sadaruwan12 on 2010-05-08
I'm writing this to a moderator, I'm not getting any help in here please some can move this thread to a place where I can get help theres nothing for days for me and I'm suffering.

---

### Post by mosse-r on 2010-05-09
[left]bump!!
[/left]

---

### Post by sadaruwan12 on 2010-05-09
> **mosse-r said:**
> [left]bump!!
[/left]

bump again

---

### Post by Crio on 2010-05-10
See if that helps: [http://ubuntuforums.org/showthread.php?p=9272125#post9272125](http://ubuntuforums.org/showthread.php?p=9272125#post9272125)

---

### Post by mosse-r on 2010-05-10
This solution almost works for me, the driver installs fine and network manager shows a list of wireless networks however it wont connect it fails and prompts for the password again, after trying to connect about 20 times it finally did connect and was perfect!! but i restarted and I was back to square one any ideas?

---

### Post by mosse-r on 2010-05-12
Bump

---

### Post by mosse-r on 2010-05-13
Bump, Please guys help me out here im so close but the wifi is not useable. ndiswrapper works fine when it does connect but it is impossble to get to connect it takes half an hour of restarting and enableing and disableing the wifi to get it to work what can I do? HELP!!!!!!

---

### Post by mdhurst on 2010-08-11
I'm having the same problem. Recently installed Ubuntu 10.04 on my old Toshiba Equium A200 laptop. Network manager detects networks and I can connect if close to the router but if I move a short distance away I repeatedly get disconnected and have to re-enter the password. Did you find a fix to this?

**EDIT**

[http://ubuntuforums.org/showthread.p...25#post9272125](http://ubuntuforums.org/showthread.p...25#post9272125)
worked great for me, thanks so much Crio!

---

### Post by .dave on 2010-11-24
> **mdhurst said:**
> I'm having the same problem. Recently installed Ubuntu 10.04 on my old Toshiba Equium A200 laptop. Network manager detects networks and I can connect if close to the router but if I move a short distance away I repeatedly get disconnected and have to re-enter the password. Did you find a fix to this?

**EDIT**

[http://ubuntuforums.org/showthread.p...25#post9272125](http://ubuntuforums.org/showthread.p...25#post9272125)
worked great for me, thanks so much Crio!


That thread seems to be unavailable and I need answers.

Literally everyone is suffering wireless problems and there doesn't seem to be a fix. Could you please relocate that thread for me or quote the fix. THanks

---

