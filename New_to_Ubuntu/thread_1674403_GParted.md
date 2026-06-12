---
title: "GParted"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by Angelbrand on 2011-01-23
hey guys hoping someone can help me. When setting up linux onto its own partition i didnt allocate enough memory, i have about 15gb of unallocated space which i want to give to the unbuntu partition so i have more memory as i have no space left and i keep getting warning messages. 
GParted of course wont let me allocate memory while im using the partition so i tried using the install disc i used to intall unbuntu. 
But everytime i put the dics in it will not load, i left it for 2 hours and still nothing. 
Is there any other way i can increase disc space or get my unbuntu disc to work?
I cannot burn a new one as i have tried twice in the past and wasted to disc. A friend burnt the the disc i have but i am no longer in touch which him.

anyone know how to allocate more memory?

---

### Post by presence1960 on 2011-01-23
You are going to have to use the Live Ubuntu from a CD or a bootable USB because you cannot use gparted from Ubuntu installation due to the fact you can not alter a mounted device.

Just to make communications more clear space on a hard disk is not "memory". Memory is RAM.

---

### Post by Angelbrand on 2011-01-23
when i say instillation disc i mean the live cd...

---

### Post by jfreak_ on 2011-01-23
This might seem stupid but did you boot your system from the cd or did you simply insert it after ubuntu had loaded?

---

### Post by Angelbrand on 2011-01-23
booth i tried booting from cd but it wouldnt stop loading after 2 hours i restarted the computer. 
i then tried seeing if it would work while i was already on unbuntu but it wont work like that.

---

### Post by antmenj on 2011-01-23
Can you read other CDs in that drive?

If not:
[http://www.sysresccd.org/Sysresccd-manual-en_How_to_install_SystemRescueCd_on_an_USB-stick]("http://www.sysresccd.org/Sysresccd-manual-en_How_to_install_SystemRescueCd_on_an_USB-stick")

It has GParted.

---

### Post by Angelbrand on 2011-01-23
yes my cd drive works perfectly

---

### Post by presence1960 on 2011-01-23
> **Angelbrand said:**
> when i say instillation disc i mean the live cd...

I understand that, however you are going to need a bootable CD/USB to alter your ubuntu partition as you can not do it from Ubuntu because the ubuntu partition will be mounted.

You will need to see if your BIOS is set correctly to boot CD before hard disk. if it is then your CD is no good. If that is the case you will need to create another bootable CD whether it be Ubuntu Live, gparted live, backtrack linux, systemrescue, parted magic hiren's boot cd. There is no way around the fact that you must use a bootable CD or a bootable USB to do this,

---

### Post by Angelbrand on 2011-01-23
is there a step by step guide then to burn iso images using ubuntu, as i have tried before but just wasted blank discs...

---

### Post by presence1960 on 2011-01-24
> **Angelbrand said:**
> is there a step by step guide then to burn iso images using ubuntu, as i have tried before but just wasted blank discs...

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

P.S. When you make a bootable CD you don't just "burn" the iso to the CD. You have to "write image to disk". The link above will give you detailed instructions.

---

### Post by Angelbrand on 2011-01-24
looks like il will have to buy a disc that was the process i followed last time that didnt work

---

### Post by presence1960 on 2011-01-24
> **Angelbrand said:**
> looks like il will have to buy a disc that was the process i followed last time that didnt work

Then maybe your CD/DVD drive isn't operating properly. But give it another try.

Just to confirm: you have your CD/DVD drive set to boot before the hard disk in BIOS correct? if it is set to boot after the hard disk the CD will never boot.

---

### Post by Angelbrand on 2011-01-24
i cant burn the iso image every time i burn the image it doesnt burn properly and its just a waste of a blank disc

---

### Post by Angelbrand on 2011-01-24
and yes the bios is setup right

---

### Post by migrate from windows on 2011-01-24
I had the same isuue but fixed it.....when you boot with the cd when you get the small keyborad and man logo hit enter ....you will get language options then hit f6 select nomodeset and then select try ubuntu ...then it will boot into desktop from cd.....then from systems > administration > chosse garted now u can change the partition size.....good luck

---

### Post by Angelbrand on 2011-01-24
> **migrate from windows said:**
> I had the same isuue but fixed it.....when you boot with the cd when you get the small keyborad and man logo hit enter ....you will get language options then hit f6 select nomodeset and then select try ubuntu ...then it will boot into desktop from cd.....then from systems > administration > chosse garted now u can change the partition size.....good luck


thanks il try that!

---

### Post by presence1960 on 2011-01-24
> **Angelbrand said:**
> i cant burn the iso image every time i burn the image it doesnt burn properly and its just a waste of a blank disc

exactly what do you mean by "it does not burn properly?" What happens, what errors if any do you get. You have to be more specific and detail oriented if you want us to be able to help. We are not there with you and thus can't see what is actually transpiring.

---

