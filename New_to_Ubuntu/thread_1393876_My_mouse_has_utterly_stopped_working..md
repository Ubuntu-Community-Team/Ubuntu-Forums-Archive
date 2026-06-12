---
title: "My mouse has utterly stopped working."
date: 2010-01-29
forum: New to Ubuntu
---

### Post by HunterjWizard on 2010-01-29
All right, being the linux novice that I am I have basically nowhere to start with this one. I have here a system running Ubuntu 9.10(just installed) and the mouse has just completely quit on me.
 
The mouse is a Microsoft Scroll Mouse hooked up through a USB-to-PS2 adapter that runs through a KVM switch into the system. I can't tell for sure if it stopped working when I switched the KVM to another computer, but I have since rebooted the machine twice and still no mouse.
 
I was also working with Virtual Box at the time it quite, I had 2 virtual machines running and the mouse was freaking out a bit on one.
 
Any ideas? This is really frustrating.

---

### Post by drzoo2 on 2010-01-29
> **HunterjWizard said:**
> All right, being the linux novice that I am I have basically nowhere to start with this one. I have here a system running Ubuntu 9.10(just installed) and the mouse has just completely quit on me.
 
The mouse is a Microsoft Scroll Mouse hooked up through a USB-to-PS2 adapter that runs through a KVM switch into the system. I can't tell for sure if it stopped working when I switched the KVM to another computer, but I have since rebooted the machine twice and still no mouse.
 
I was also working with Virtual Box at the time it quite, I had 2 virtual machines running and the mouse was freaking out a bit on one.
 
Any ideas? This is really frustrating.

Have you tried bypassing the KVM and going directly into the computer? With and without the adapter?

---

### Post by HunterjWizard on 2010-01-29
Well I tried plugging in a second USB mouse and turning the system back on, and to my surprise both mice began working. So I switched over to a few other computers on the KVM and then went back to Ubuntu, mouse still working. Then I turned on Virtual Box and discovered that having the mouse captured in the guest OS makes the KVM not work, but releasing it lets me switch and switch back and low and behold the mouse still works. 
 
So Im not sure if just plugging in a USB mouse fixed it or if it fixed itself, but it seems to be working again and I cannot duplicate the problem.
 
Thankyou for your assistance.

---

### Post by Son of William on 2010-01-30
@HunterjWizard:

I have a similar setup - Microsoft USB scroll trackball hooked up through a PS2 adapter to a 2 port Belkin KVM switch.  It is common for me to get random mouse actions when I switch back to an Ubuntu machine.  This can be as innocent as switching workspaces, to something more annoying such as creating a new file folder on the desktop, or sometimes as harmful as deleting a gnome panel. 

You have already found out that Virtualbox will capture your mouse unless you have  installed the guest additions.  Even if you have installed the guess additions, however, it can temporarily freeze the mouse on a KVM "switch back."  

In fact, that is often my method for "parking" the mouse pointer so it does no harm during the KVM switching.  After I switch back to my Ubuntu machine I alt-tab to the Virtualbox virtual machine and I get my mouse back.

---

### Post by chillicampari on 2010-01-30
@Son of William, I have a similar setup too, and the trackball would go nuts when using the switch. This helped:[http://www.idevelopment.info/data/Unix/Linux/LINUX_ErraticMouseBehaviorwithMouseFedoraandBelkinKVM.shtml](http://www.idevelopment.info/data/Unix/Linux/LINUX_ErraticMouseBehaviorwithMouseFedoraandBelkinKVM.shtml)

---

### Post by rabau on 2010-02-14
Hi All,

This is happening to me too. One day in January my PS2 mouse completely stopped working. If I connect a USB mouse that works, but I have a PS2 KVM switch so I don't want to go USB.

Does anyone have any suggestions on how I can resolve this?

Cheers,
RAB

---

