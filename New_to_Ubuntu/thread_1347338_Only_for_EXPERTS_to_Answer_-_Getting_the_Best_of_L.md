---
title: "Only for EXPERTS to Answer - Getting the Best of Linux (and Windows)"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by hanzellean on 2009-12-06
Hi, I have the following situation and proposed solution:

_SITUATION_

I have a notebook computer. The manufacturer ships the hardware with a Windows OS (either XP Pro, Vista or Windows 7). They provide support only for a Windows OS.

Also, I am not sure how fuss-free it is to use any Linux distro on this notebook hardware, whether due to switchable graphics, device drivers, or trackball / trackpoint / trackpad issues/complications. 

Also, I have software such as MS Office 2007 and Adobe Acrobat which is meant for installation on Windows OS.

But, a Windows OS is vulnerable to virus/spy-ware/mal-ware/trojans/worms and other malicious code. (Is this true for Windows 7 too? I am presuming so). Also, the Windows registry degrades and corrupts over time, and coupled with the need for strong anti-virus software, would mean that the performance I get will deteriorate rapidly.


[U]PROPOSED SOLUTION

[/U]Therefore, to get the best of Linux (and Windows), I propose the following solution:

(1) have the Windows OS run as the base/host OS on the notebook hardware. So I don't have to deal with device drivers and other hardware issues, including support from manufacturer.

(2) Install virtualization software. (Not sure if Windows Virtual PC is good enough? Which is the best virtual machine software? (Classify into free and non-free virtualization software))

(3) Install a Linux distro within this virtual environment. (Which is the best Linux distro for installation within a virtual environment? Does Windows Virtual PC support such Linux guest OS installation? If no, which virtualization software should I use to be able to install a Linux guest OS)

(4) Work within the Windows OS ONLY when using MS Office 2007 or Adobe Acrobat (since they have to be installed in a Windows OS environment)

(5) _**ALWAYS**_ work within the Linux OS when connecting to the Internet. 

(6) Work within the Linux OS for other purposes.


_QUESTION:_

(A) Because I ONLY connect to the Internet from within the virtual environment running the Linux OS distro, does it mean that any malicious code/software (virus/malware/spyware/trojan/worm) coming from the Internet WILL **_NOT_** GET TO THE HOST/BASE Windows OS?

That is - is it the case that _**ALL**_ malicious stuff will be _**contained within/repelled by**_ the Linux environment, and therefore I will be safe?? =) ==))

(B) Will my Windows OS Registry still degrade, given that I am only using the Windows OS minimally for either Office 2007 or Adobe Acrobat only (Everything else is within the virtual Linux OS)?

=) ==)

You should get the drift of my query from the above. So you can post any other comments relating to getting the best out of the situation I have!!

Thank you!!!!!!

---

### Post by TeoBigusGeekus on 2009-12-06
(A) They WILL get to the virtual machine installation if you connect through the vm. If you connect through Linux you don't have to worry about it.

(B) Registry degrading will be very slow if don't install any new software on the vm installation and you don't browse the web through it.

Given that your needs are minimal (Office and Acrobat), I would suggest a complete Linux installation.

My 5 drachmas...

---

### Post by TeoBigusGeekus on 2009-12-06
What I mean is that if you open Internet Explorer through your vm installation, your windows installation will be vulnerable.

If you use Opera or Firefox through your linux system, your virtual machine will be OK.

---

### Post by Greenwidth on 2009-12-06
> **TeoBigusGeekus said:**
> Given that your needs are minimal (Office and Acrobat), I would suggest a complete Linux installation.

I agree, if you have any must have Win apps, you can dual boot or run Win virtual - Virtualbox is good, and free.
[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by quinnten83 on 2009-12-06
If you are runnnig Linux on a VM inside windows and you connect to the internet, you're connecting windows to the internet. How safe windows is, well it depends on your firewall, antivirus and such. It has been demonstrated that XP would get infected by simply connecting to the network, but that was unpatched and without protection.

If you need to do basic office application use, you might just as wel use open office and evince for reading PDF, both are default for Ubuntu.

I think in your case the best solution would be to install a persistant USB linux distro. See [www.pendrivelinux.com](www.pendrivelinux.com) on how to do it for Ubuntu. That way you don't have to actually install a dualboot and your warranty should be fine, but you get to use Linux when needed.

 Since you have to use the LiveCD anyway, you can check immediately if your hardware is supported. I don't know what you've heard, but hardware support in Linux is pretty good these days.

EDIT: I recommend virtualbox for installing virtual machines BTW: [www.virtualbox.org](www.virtualbox.org)

---

### Post by 3rdalbum on 2009-12-06
Teo: He's proposing using Windows as the host OS and Linux as the guest.

Hanzellean: I suggest taking Ubuntu for a test-drive directly on your hardware. Ubuntu comes as a live CD, which means you can boot off it and run the system from the CD. Additionally, you can actually install it to a USB flash drive (using the USB Startup Disk Creator program) which is better than the CD because you can install programs and stuff.

Chances are that all your hardware will be usable in Linux, but using the live CD/live USB will let you test it out and make sure.

If Windows can recieve packets from the Internet, then it can get viruses. When Windows is the host OS, it manages the internet connection. You will likely be safe against browser-based attacks because the browser will be running in the virtualised guest Linux, but roving worms will still get into your Windows. They might try to contact the VM but of course they won't be able to run within it.

Linux doesn't actually actively repel attacks, it's just not vulnerable to the sorts of things that are going around.

Virtual PC will not properly support Linux as a guest. Use Virtualbox if you want to go ahead with your proposal. Virtualbox is free.

So, to sum up: My advice is to try Ubuntu as a live USB. If it supports your hardware, then install it to your hard disk as a dual-boot setup; or let it take over your complete hard disk (make sure you've got a backup first!) and then install Windows within Virtualbox.

And remember: They put the tiger in a cage because it's a danger to others; it doesn't make sense to put you in a cage to protect you from the tiger :-)

---

### Post by hanzellean on 2009-12-06
Thank you TeoBigusGeekus.

Let me clarify part (A) of my post.

(A)
(i) I WILL NOT connect to the Internet via IE or Firefox from within the the base/host Windows OS)
(ii) I will ONLY connect to the Internet from within the virtual environment running a Linux OS distro. Additionally, I will use mainly Firefox, except where necessary (for school purposes) where I have to use  IE.

When you mentioned that "They WILL get to the virtual machine installation if you connect through the vm." - Can I rephrase to state that 'connecting to the internet ONLY from within the virtual environment Linux OS (mainly Firefox)' _**will still leave**_ my base/host Windows OS vulnerable to the internet' ?

(B) When you mentioned that "Registry degrading will be very slow if don't install any new software on the vm installation and you don't browse the web through it." - Can I rephrase to state that 'running most of my apps and connecting to the Internet from within the virtual Linux OS, and running only MS Office 2007 and Adobe Acrobat from within the base/host Windows OS will, largely NOT degrade the Windows registry' ?

---

### Post by quinnten83 on 2009-12-06
> **hanzellean said:**
> Thank you TeoBigusGeekus.

Let me clarify part (A) of my post.

(A)
(i) I WILL NOT connect to the Internet via IE or Firefox from within the the base/host Windows OS)
(ii) I will ONLY connect to the Internet from within the virtual environment running a Linux OS distro. Additionally, I will use mainly Firefox, except where necessary (for school purposes) where I have to use  IE.

When you mentioned that "They WILL get to the virtual machine installation if you connect through the vm." - Can I rephrase to state that 'connecting to the internet ONLY from within the virtual environment Linux OS (mainly Firefox)' _**will still leave**_ my base/host Windows OS vulnerable to the internet' ?

(B) When you mentioned that "Registry degrading will be very slow if don't install any new software on the vm installation and you don't browse the web through it." - Can I rephrase to state that 'running most of my apps and connecting to the Internet from within the virtual Linux OS, and running only MS Office 2007 and Adobe Acrobat from within the base/host Windows OS will, largely NOT degrade the Windows registry' ?

It's very simple, the more applications you run on windows, the quicker the registry will degrade, it simply gets used more often.
If you don't run many applications, the registry doesn't get used as often and therefore the registry degrades less quickly.
what is with the almost legalese?

---

### Post by hanzellean on 2009-12-06
Thank you all - [TeoBigusGeekus]("http://ubuntuforums.org/member.php?u=504094"), [Greenwidth]("http://ubuntuforums.org/member.php?u=628497"), [quinnten83]("http://ubuntuforums.org/member.php?u=291401"), [3rdalbum]("http://ubuntuforums.org/member.php?u=61044").

I will proceed as follows:

(1) Test-drive Linux on my hardware (using LiveCD / persistant USB linux distro) to ensure the notebook hardware works with Linux.

(2) Assume that (1) is not meant to be a permanent solution / not as fast as an actual hard-disk installation, and proceed to (3).

(3) Partition my harddisk (I assume this is necessary), so that I can dual-boot a Linux OS and Windows. Switch from the Linux OS to Windows and vice-versa only by doing a re-boot. There is no need for VirtualBox is such a dual-boot scenario.

(4) Alternatively, instead of (3), use a Linux OS as main/host OS. Install VirtualBox, and then install a Windows OS as a guest OS from within VirtualBox. Assuming that this allows me to cut and paste stuff seamlessly from within Windows OS to within Linux OS and vice versa, this will be better than (3). Also, I don't need to partition my harddisk and so better than (3)?

Regarding the Windows registry issue - I got the message - run as little from within Windows OS and the registry will not degrade rapidly.

---

### Post by ed-koala on 2009-12-06
I have to second quinnten83's suggestion. If Office and Acrobat are your main programs, a complete switch to Linux is probably something to consider and just ditch Windows.

Ask yourself this question. What exactly do I use these applications for? Then look into Open Office and other Linux alternatives. I think you'll find they'll do what you need, and reduce your risk from small to zero.

Duel booting becomes a pain. Running Windows within VirtualBox is nice, but it IS Windows, and as such is just as vulnerable to viruses and degradation as would be a regular installation.  The difference is it can't get to your Linux OS.

Good luck! Hope the testing with the Live CD goes well and all your hardware works flawlessly. :)

---

### Post by prenoob on 2009-12-06
This post first appeared some considerable time ago.  Now it all appears at the top of the list - odd?

---

