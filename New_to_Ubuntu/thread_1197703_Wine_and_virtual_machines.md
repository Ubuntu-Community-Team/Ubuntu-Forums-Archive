---
title: "Wine and virtual machines"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by A_M_S on 2009-06-26
Hi.

Is wine a virtual machine application?.
What is the best choice to run windows apps under Ubuntu? 
Is there any advantages on using wine instead of virtual box? 

Tnx!

---

### Post by nandemonai on 2009-06-26
wine is a compatibility layer to allow some native Windows applications to run under Linux. It is not a VM application.

Best is subjective, both are good for certain uses.

Virtual machines are exactly that, the OS running on a VM thinks it's on a real computer so much more software works. That said there is a serious lack of 3D support for virtual machines as yet.
They also use more resources than Wine.

Wine however, will not run all Windows programs, truth be told, not a lot runs without problems.

My advice is this. If you have the hardware and don't need 3D then use virtualbox. If you're trying to get Windows games to run then try your luck with wine.

---

### Post by Zzl1xndd on 2009-06-26
> **nandemonai said:**
> wine is a compatibility layer to allow some native Windows applications to run under Linux. It is not a VM application.

Best is subjective, both are good for certain uses.



Nandemonai is right on both counts, It might be useful if we knew what apps you wanted to run.

---

### Post by A_M_S on 2009-06-26
> **tweakedenigma said:**
> Nandemonai is right on both counts, It might be useful if we knew what apps you wanted to run.

Probably CAD.

I have some experience with VM under windows, (that's how i started using Ubuntu) but since i need 3D, i will try wine. 


Tnx for your replies! :)

---

### Post by nandemonai on 2009-06-26
> **A_M_S said:**
> Probably CAD.

I have some experience with VM under windows, (that's how i started using Ubuntu) but since i need 3D, i will try wine. 


Tnx for your replies! :)

I've heard of some success with running CAD under both virtualbox and wine but you'd need to search around a bit here on the forums and [http://appdb.winehq.org/](http://appdb.winehq.org/).

---

### Post by SunnyRabbiera on 2009-06-26
Wine is not a virtual install, its more or less a emulator though the very name of Wine stands for Wine is not a emulator, one of the dozens of recursive acronyms you see with linux.
Anyhow both VM's and Wine are good choices, a VM might perform better in most cases but personally I have have yet to see a mission critical issue with Wine from what I have seen.

---

