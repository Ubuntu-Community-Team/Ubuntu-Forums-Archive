---
title: "wifi drops when I go on battery on my laptop"
date: 2016-07-17
forum: Networking &amp; Wireless
---

### Post by leon244 on 2016-07-17
I have an Asus C90S laptop with an Intel 4965AGN wireless card. When I remove the AC and go to battery the wifi drops and will not come back up without rebooting the computer. Just trying to connect again fails.

iwconfig wlan0 shows
```
Mode:Managed  Frequency:2.462 GHz  Access Point: 74:85:2A:C9:E2:C0   
          Bit Rate=43.3 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4526  Invalid misc:139   Missed beacon:0


```

I cannot find an answer on the net. I have Ubuntu 14.04 LTS as the OS. This happens every time I go on battery. 
Is there a command line command that I could try? 
Thanks

---

### Post by jeremy31 on 2016-07-17
Wow, you joined the site 5 years ago and this is your first post in a support subforum?
In that case, welcome to the forums and please visit the wireless script link in my signature and post your results

---

### Post by leon244 on 2016-07-18
jeremy31 thank you for the very quick reply
> **jeremy31 said:**
> Wow, you joined the site 5 years ago and this is your first post in a support subforum?

It's a long story. I first joined when I was trying out Ubuntu. I use other distro, but now have Ubuntu on my old laptop.

I have attached the file. I don't see anything off hand and  have not found anything online about the Intel 4695 that addresses the problem.
[ATTACH]270161[/ATTACH]

Thank you.

---

### Post by leon244 on 2016-07-18
Here's some additional info. I installed wicd and used it to try and sign on to the wifi after I had removed AC power and the returned to AC. When I had tried previously it just failed. Using the wicd app I get the feedback that the connection failed because of "Bad Password".  The password I had entered is correct and is the one that gets on to wifi when I first boot. Can this be a problem with the wifi card?

---

### Post by jeremy31 on 2016-07-18
It could be an issue with the wifi card or the connection to the motherboard.  I would disable IPv6 in WICD and change encryption on the wifi router to WPA2 only and see if that helps any

---

### Post by leon244 on 2016-07-18
Thank you.  I will try those when I next have a chance. On further searching, I found some mention that people were having trouble with the 4965 on the C90S laptop. I am going to get a new card and see if that makes things any better.  Appreciate your suggestions and I will get back and let you know the follow up, though it may take some time. New card won't arrive for about 2 weeks.

---

### Post by leon244 on 2016-07-28
I replaced the wifi card and the problem has disappeared. Thank you all
Leon

---

### Post by Skaperen on 2016-07-28
same model of wifi card (original unit is defective) or different model (original model or its driver is a bad design)?

---

### Post by leon244 on 2016-07-29
> **Skaperen said:**
> same model of wifi card (original unit is defective) or different model (original model or its driver is a bad design)?

Different model card. Original model or its driver did not work with the hardware.

---

