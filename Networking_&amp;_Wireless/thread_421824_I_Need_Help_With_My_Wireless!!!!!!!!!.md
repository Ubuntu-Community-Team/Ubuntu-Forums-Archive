---
title: "I Need Help With My Wireless!!!!!!!!!"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by Tiger658 on 2007-04-24
HI, I recently upgraded from 6.10 to 7.04. I love 7.04 but since I upgraded I cant get my wireless card to work. I had it working fine on 6.10 I'd apprechate any ideas that you have.

Thanks,
Tiger

---

### Post by Alekc on 2007-04-24
You should provide some more info, for example which network chipset are you using (you can find it by running lspci)

---

### Post by JerseyShoreComputer on 2007-04-24
At first, I had the same trouble. Go into network manager and enter in your security information and such. Then turn off ROAM mode and use manual network connection. This to did not work for me just yet. Remove the wireless card or turn it off, restart the computer, and then once you log in, insert it or turn it back on. Strange, but I did that and it worked.

If not, another option is to try WiFi radar.. I had good luck with it in the past.

---

### Post by Tiger658 on 2007-04-24
> **JerseyShoreComputer said:**
> At first, I had the same trouble. Go into network manager and enter in your security information and such. Then turn off ROAM mode and use manual network connection. This to did not work for me just yet. Remove the wireless card or turn it off, restart the computer, and then once you log in, insert it or turn it back on. Strange, but I did that and it worked.

If not, another option is to try WiFi radar.. I had good luck with it in the past.

That is just the problem I can't even get it to detect the card to put in any of the info, It just won't detect it even though it detected it right off in 6.10.

Also it is a Netgear MA521 pci card and I am running a Dell Latitude LS P3

---

### Post by Alekc on 2007-04-25
From Ndiswrapper Wiki:
```

Card: Netgear MA521

    * Chipset: RTL8180 FCC_ID: PY3MA521D
    * Driver: RTL8180L - Use the ndis5x-8180(xxx).zip driver. (NOT NETGEAR DRIVER! NETGEAR DRIVER UNSTABLE!! -- Seconded: The Netgear driver caused my machine to drop interrupts)
    * Other: Works well even with DHCP on SUSE 9.0 Pro. 128 bit wep, managed mode. Will be trying WPA/PEAP/MSCHAP v 2 sometime later on. Check [210] for information. Ubuntu Hoary: Working with Ndiswrapper 1.1 - see [211]. 

```
Download driver from  [Here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8180L")

You can try to use linux driver or windows with ndiswrapper. Reason for which i told you to run "lspci" in terminal is because you can see if ubuntu actualy see your card or not.

---

### Post by Rickmeister on 2007-04-25
Hey

Absolute new-by. Installed Ubuntu last week and still, after reading 100s of forums can't get internet!!!!!!!
I have got a D-Link DWL-G520+, which worked on windows flawlessly...

If u can help me it would be mostly appreciated, otherwise i'm going back to windows...

---

### Post by Tiger658 on 2007-04-25
I still have nothin, after running that command.

---

### Post by Tiger658 on 2007-04-25
Thanks I GOT IT!!!!!!! I went to the website and downloaded the stuff and now it works. Thanks!

Tiger

---

### Post by xbeaudet on 2007-04-25
i "downloaded the stuff" too, but when i try a "make", i've an error message.

Could you explain what you did whith the Realtek drivers, please ?

---

### Post by Tiger658 on 2007-04-25
> **xbeaudet said:**
> i "downloaded the stuff" too, but when i try a "make", i've an error message.

Could you explain what you did whith the Realtek drivers, please ?

I just downloaded the Windows Wireless Drivers GUI thing from Synaptic. Then download the Windows driver and add it into the Windows Wireless thing through it and Whala! It works.

Tiger

---

### Post by xbeaudet on 2007-04-26
tjhank's for this answer... But :
-i tried too hard (and mainly too late) to make it works : and finally, i stupidly deleted ndiswrapper kernel module...
-i had (even before deleting this module) error messages with ndiswrapper GUI : alias already present in modules... and it wasn't installing.

Do someone know what files are modified when you type ndiswrapper -m ? Can someone send me a ndiswrapper.ko and remember me where it has to be in modules tree ?

thank's

---

### Post by xbeaudet on 2007-04-26
Finally, it's solved :
-impossible to compile official driver,
-impossible to use blacklisted driver
-problems with ndsiwrapper GUI

The solution : ndiswrapper in text mode...

tnaks for all the help and advises provided...

---

