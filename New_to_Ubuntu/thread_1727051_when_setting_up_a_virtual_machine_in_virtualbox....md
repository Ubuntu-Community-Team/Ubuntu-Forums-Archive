---
title: "when setting up a virtual machine in virtualbox..."
date: 2011-04-12
forum: New to Ubuntu
---

### Post by RememberWhenItRained on 2011-04-12
"Enter a name for the new virtual machine and select the type of the guest operating system you plan to install onto the virtual machine."
I want to virtually run my Win 7 through Linux.. would the guest OS be Win 7 or  Ubuntu?

---

### Post by squaregoldfish on 2011-04-12
As the message says, the guest OS is the one that will be installed in the virtual machine. In your case this is Win7.

Steve.

---

### Post by RememberWhenItRained on 2011-04-12
> **squaregoldfish said:**
> As the message says, the guest OS is the one that will be installed in the virtual machine. In your case this is Win7

Steve.
upon reading more about virtual box, it's pretty useless for people who already dual boot, correct? an easier solution would to be access my Win7 through Remote Desktop? Or do i have it all wrong?

My end goal is to access/use iTunes from my Win7 while still in Ubuntu.

---

### Post by RememberWhenItRained on 2011-05-26
I did not think of this until actually trying to set up Virtualbox, and  going through my stuff, but apparently if you buy laptops preloaded with  Win OS, they do not give you the disc with the OS as well.
Which is a  problem if i want to run win7 with VB... can i find a file on my HD  that i can use instead of the disc? I probably wouldn't have an iso of  the OS, but is there something comparable for VB?
Really i'd love to  just use my existing win7 OS inside linux. while i want to keep the dual  boot, i hate having to restart to get into windows and then restart  again to get back to ubuntu. 

Any suggestions?

Thanks.

---

### Post by BrandonC19 on 2011-05-26
If you're concerned about legality, you can use Magic Jelly bean to recover your product key, remove your Win 7 installation from the hdd, and use a torrented win7 cd with YOUR license number.

---

### Post by RememberWhenItRained on 2011-05-26
> **BrandonC19 said:**
> If you're concerned about legality, you can use Magic Jelly bean to recover your product key, remove your Win 7 installation from the hdd, and use a torrented win7 cd with YOUR license number.
i don't want to remove my existing win though.

nice sig.

---

### Post by JKyleOKC on 2011-05-26
It's possible to use an existing hard disk partition as the virtual disk when creating a VM in VirtualBox, but the manual repeatedly warns that it's quite dangerous to do so because it's very easy to accidentally destroy the data. In addition, the virtual hardware environment in which the VM runs is quite different from the actual hardware environment in which your Win7 is installed, so in all probability it would not run properly -- and changing the Win7 setup to be compatible with the VM's environment would make it impossible to boot to it outside the VM.

To achieve what you are asking for, the most reliable way would be to copy off everything you want to save from the existing Win7 Installation, then replace it with a full Ubuntu system including a VM, and finally re-install Win7 into the VM using a newly purchased Win7 package.

---

### Post by wildmanne39 on 2011-05-26
Hi, I agree with JKyleOKC I have been running virtualbox for about 4 years and I attempted to make vista that was already installed into a vm but I had no luck and it would not play games well in a vm, everything else works great though.

---

### Post by RememberWhenItRained on 2011-05-26
> **JKyleOKC said:**
> It's possible to use an existing hard disk partition as the virtual disk when creating a VM in VirtualBox, but the manual repeatedly warns that it's quite dangerous to do so because it's very easy to accidentally destroy the data. In addition, the virtual hardware environment in which the VM runs is quite different from the actual hardware environment in which your Win7 is installed, so in all probability it would not run properly -- and changing the Win7 setup to be compatible with the VM's environment would make it impossible to boot to it outside the VM.

To achieve what you are asking for, the most reliable way would be to copy off everything you want to save from the existing Win7 Installation, then replace it with a full Ubuntu system including a VM, and finally re-install Win7 into the VM using a newly purchased Win7 package.
hmm. okay. no way to run my existing win7 in a window of ubuntu, much like an RDC would look?

---

### Post by crispy_420 on 2011-05-27
What about if you opted for the VMWare route and used their ["P to V"]("http://www.vmware.com/products/converter/") converter?

---

### Post by RememberWhenItRained on 2011-05-30
> **crispy_420 said:**
> What about if you opted for the VMWare route and used their ["P to V"]("http://www.vmware.com/products/converter/") converter?
how would that work/how do I set that up?

boot from win7 and launch the executable...does it have a wizard?

---

### Post by RememberWhenItRained on 2011-06-02
> **crispy_420 said:**
> What about if you opted for the VMWare route and used their ["P to V"]("http://www.vmware.com/products/converter/") converter?
P to V won't delete the OS that I'm converting to virtual will it?

---

### Post by RememberWhenItRained on 2011-09-21
> **BrandonC19 said:**
> If you're concerned about legality, you can use Magic Jelly bean to recover your product key, remove your Win 7 installation from the hdd, and use a torrented win7 cd with YOUR license number.

> **JKyleOKC said:**
> It's possible to use an existing hard disk partition as the virtual disk when creating a VM in VirtualBox, but the manual repeatedly warns that it's quite dangerous to do so because it's very easy to accidentally destroy the data. In addition, the virtual hardware environment in which the VM runs is quite different from the actual hardware environment in which your Win7 is installed, so in all probability it would not run properly -- and changing the Win7 setup to be compatible with the VM's environment would make it impossible to boot to it outside the VM.

To achieve what you are asking for, the most reliable way would be to copy off everything you want to save from the existing Win7 Installation, then replace it with a full Ubuntu system including a VM, and finally re-install Win7 into the VM using a newly purchased Win7 package.


can i combine these two methods? Copy everything off, after retrieving my product key, and put win7 in VM?

There's no way to put all my existing files & settings onto one file is there? I remember in High School working as a Lab Tech. reimaging windows computers... does that only work for the OS or is there a way I could save an image of everything (programs, settings, etc.?)
I have this horrendous vision of having to save everything on like 10 DVDs :D

help?
thanks in advance. Y'all are awesome.

P.S. - After becoming an Ubuntu convert for some, maybe 4-5 months, I find that I get annoyed having to boot in or use Windows, that I find it has slow load time compared to Ubuntu (or any Linux, for that matter (I previously thought Win7 was fast), and wishing I had a terminal and sudo aptitude in windows :)

---

### Post by JKyleOKC on 2011-09-21
> **RememberWhenItRained said:**
> can i combine these two methods? Copy everything off, after retrieving my product key, and put win7 in VM?

There's no way to put all my existing files & settings onto one file is there? I remember in High School working as a Lab Tech. reimaging windows computers... does that only work for the OS or is there a way I could save an image of everything (programs, settings, etc.?)
I have this horrendous vision of having to save everything on like 10 DVDsYou might be able to do this, but remember that the VM's "hardware" is going to be quite different from the actual hardware and this may easily prevent the copied Win7 from even booting, much less running properly. Getting the VM's version running properly is why I suggested installing a new purchased copy rather than trying to re-use the original.

An additional reason is that many OEM versions of Windows are locked into the original hardware on which they are installed and refuse to work at all if moved to other hardware. The "Windows Genuine Advantage" activation scheme used as far back as WinXP specifically prevents the activation from staying valid after major hardware changes such as replacing a motherboard or hard drive.

Trying to use 10 DVDs to copy your files off is a recipe for disaster. External hard drives that connect via USB can be had for under $100 USD and are far more reliable. You can also use one for backup purposes after you complete the changeover, too.

---

### Post by RememberWhenItRained on 2011-09-21
> **JKyleOKC said:**
> You might be able to do this, but remember that the VM's "hardware" is going to be quite different from the actual hardware and this may easily prevent the copied Win7 from even booting, much less running properly. Getting the VM's version running properly is why I suggested installing a new purchased copy rather than trying to re-use the original.

An additional reason is that many OEM versions of Windows are locked into the original hardware on which they are installed and refuse to work at all if moved to other hardware. The "Windows Genuine Advantage" activation scheme used as far back as WinXP specifically prevents the activation from staying valid after major hardware changes such as replacing a motherboard or hard drive.

Trying to use 10 DVDs to copy your files off is a recipe for disaster. External hard drives that connect via USB can be had for under $100 USD and are far more reliable. You can also use one for backup purposes after you complete the changeover, too.

you bring up good points. I'd rather not do something unstable. but i don't want to purchase a brand new copy of Win7 especially since I already have one. Dual-booting it is I guess. 

Windows Genuine Advantage - that's so lame... guess they're not much for encouraging others to mod their computers lol.

Yeah, 10 DVDs was just an exaggeration - I know an external drive would be the way to go; that would be really handy too, but I am but a broke college student, so buying an external HD or a new win7 is not exactly the best idea for me :)

thanks for your help though.

---

