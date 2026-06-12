---
title: "8,10 Newbie: ATI Radeon Graphics Q."
date: 2009-02-26
forum: New to Ubuntu
---

### Post by Foreseer on 2009-02-26
Alas another newb question from yours truely.

I recently found out what my initial issues were;
That I was installing this "Ati/amd proprietary FGLRX graphics driver" on the Hardware installation menu. After installing it would take me to a bios screen; So I've formatted for the 5th time now.

My question being; What would be the best way to install my video drivers...

I use:
Asus A8r32-mvp deluxe motherboard ATI Crossfire Enabled
ATI Radeon X1300 Pro PCIE 256m 
ATI Radeon X1300 Pro PCIE 256m

I'm new to Ubuntu & Linux in general.
As big lines of script tend to scare the bajesus out of me....
I ask here for before I try anything that I've found myself.

Also how do I check the current drivers installed. Thx-

---

### Post by myromance123 on 2009-02-26
Mmm my problem with 8.10 was that after installing fglrx graphics driver, after login it would hang. 
 I spent an entire day (restarting and reformating) to see what was wrong. After searching some forums it seemed as though theres a bad bug for ATi on 8.10 and it hadn't been solved forcing me to go back to 8.04 .

  I use ATi x1650 and x550.

Arguably it seems as though installing fglrx driver as compared to installing the binary from the ATi website is definitely safer.

 It looks very challenging to get it going. But those who can, have no problems or so it seems.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

Have you checked that out yet?
 It should give you a proper overview of the binary install method.

Sorry I don't know how to check for current installed drivers. I'm quite the newbie too :)

Hope something there helps.

---

### Post by Foreseer on 2009-02-26
Any reply is better then none :3
It's all so confusing >.>

When I ran the fglrx and reboot it would take me to terminal screen w/ Login & password; attempting to use startx command would result in some sort of error, so using it would be a no :(

btw: I'm running amd x86 64
My processor being: amd athlon(tm) 64 x2 4600 2.4ghz

---

### Post by 3rdalbum on 2009-02-26
I have heard that the Crossfire support on the ATI drivers is really quite shocking, and it might be causing your problem. Is it imperative that you have 3D support? Could you take one card out, or remove the Crossfire bridge to check?

---

### Post by Foreseer on 2009-02-26
I may try that this weekend. It's already 5 hours past time I sleep.
Really wish I could get past trying to setup these basics. My time = gone :<

I shouldn't need to remove a card. Thanks for feedback; BB here tomorrow.

---

### Post by 3rdalbum on 2009-02-26
> **Foreseer said:**
> I shouldn't need to remove a card.

If that ends off being the problem, then tell it to ATI - it looks like everything is working with open-source drivers :-D

---

### Post by Foreseer on 2009-02-27
Wondering if anyone has any suggestions for me before I go trying anything.

---

### Post by Foreseer on 2009-02-27
So I guess my driver is installed; Unsure how FGLRX works. I did a manual install; How do I get my second monitor to work >.<

---

