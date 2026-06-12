---
title: "Virtualbox"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by loyaleagle on 2009-01-27
Just a question.... I got XP running within Virtualbox in Ubuntu. All is fine and working great. I had to do this because my work with a major hotel company, that will remain unnamed, requires that I use Windows and Internet Explorer. Ubuntu us a no go with them and their website is unavailable through Ubuntu Firefox.

Now for the question. Do I have to run a virus screener with XP that is running in Virtualbox. Or am I safe as is.

Thanks.

---

### Post by Orographic on 2009-01-27
You can still get a virus. Its just that it will be contained in that virtual machine, within the guest OS. It depends on how you use your guest OS. If you are using it to surf the net, then yes, install an antivirus. Avira Free is very good.

Check with others though, I am no expert on this. Make a copy of your virtual machine just after you install and activate it. That way, you at least have a file of your guest OS that is clean.

---

### Post by zero244 on 2009-01-27
The above advice is correct.
Ubuntu is safe but Windows isn't.
The only way I have found to protect Windows close to 100 percent is to use a third party program called DeepFreeze. Its only about 35 or 40 dollars. Its very easy to install and implement.

It will be the best money you've ever spent protecting Windows from itself.

The nice thing about the program, it doesn't bog your machine down at all that I can tell, unlike virus scanners that bring Windows down to a crawl most of the time.

Windows is the most insecure OS ever created.

I run XP in vmware player and keep deepfreeze turned on whenever Im surfing or doing anything on the net.
Good luck

---

### Post by HavocXphere on 2009-01-27
If you are *only* using the MS virtual OS to interact with this 1 site then there is little danger. If you also use it to visit dubious sites then you need a hardcore anti-virus and firewall.;)

---

### Post by talsemgeest on 2009-01-27
> **loyaleagle said:**
> Just a question.... I got XP running within Virtualbox in Ubuntu. All is fine and working great. I had to do this because my work with a major hotel company, that will remain unnamed, requires that I use Windows and Internet Explorer. Ubuntu us a no go with them and their website is unavailable through Ubuntu Firefox.

Now for the question. Do I have to run a virus screener with XP that is running in Virtualbox. Or am I safe as is.

Thanks.
If you don't care about some nasty, unsavory character getting their hands on whatever data you put into your xp vm, then there should be no need to install antivirus. However, if you work with things that should remain private, then secure your vm just as you would a normal xp installation.

---

### Post by MrWES on 2009-01-27
> **loyaleagle said:**
> Just a question.... I got XP running within Virtualbox in Ubuntu. All is fine and working great. I had to do this because my work with a major hotel company, that will remain unnamed, requires that I use Windows and Internet Explorer. Ubuntu us a no go with them and their website is unavailable through Ubuntu Firefox.

Now for the question. Do I have to run a virus screener with XP that is running in Virtualbox. Or am I safe as is.

Thanks.

Yes, you most certainly can, and probably will if you're connecting to the internet. Check out avast!, it's probably one of the best free versions around:

[http://www.avast.com/eng/avast_4_home.html]("http://www.avast.com/eng/avast_4_home.html")

Bill

---

### Post by dragon32078 on 2009-01-31
Hello Everyone,

I am a bit of an Ubuntu Noob, and I would like to know a couple of things. I have found VMWare player 2.5.1 for Linux (.rpm) but I am uncertain if Ubuntu is considered Linux.

Plus, I wanted to thank everyone for giving me the advice necessary to making Windows XP more secure. This is the primary reason I am switching over to Ubuntu because (and sorry for the crude metaphor) but Going on the INternet with no spyware detector or anti-virus is like sleeping with a new whore every day for 1 year without a condom.

Sincerely,

Kevin

---

### Post by mlentink on 2009-01-31
> **dragon32078 said:**
> Hello Everyone,Hello, and welcome!
> **dragon32078 said:**
> I am a bit of an Ubuntu Noob, and I would like to know a couple of things. I have found VMWare player 2.5.1 for Linux (.rpm) but I am uncertain if Ubuntu is considered Linux.
Ubuntu is a linux distribution, which means it is a Linux based operating systems packaged in a certain way, with a specific set of programs.
As such, Ubuntu does not use ´.rpm´-packages, but rather '.deb'-packages (short for Debian, upon which is Ubuntu is based). 
Save yourself a lot of trouble by browsing through the list of progams listed in the 'Add/Remove programs' options in your main menu. You will find VMWare there, as well as VirtualBox, which I personally like better. But you have a choice...

Welcome to the free world!

---

### Post by albinootje on 2009-01-31
> **dragon32078 said:**
>  I am a bit of an Ubuntu Noob, and I would like to know a couple of things. I have found VMWare player 2.5.1 for Linux (.rpm) but I am uncertain if Ubuntu is considered Linux.


You'll want the free-of-charge VMware server instead of VMware player, so that you can easily install your guest VMs.
But please consider using the latest VirtualBox. 
Personally I find VMware very annoying to work with, while VirtualBox is a breeze.

If you want usb in your VirtualBox guest VMs, then use the PUEL version :
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)
Otherwise install the OSE version of VirtualBox :
```

sudo apt-get install virtualbox-ose

```
And don't forget to install the Guest Additions.

---

### Post by pricetech on 2009-08-11
> **zero244 said:**
> The above advice is correct.
Ubuntu is safe but Windows isn't.
The only way I have found to protect Windows close to 100 percent is to use a third party program called DeepFreeze. Its only about 35 or 40 dollars. Its very easy to install and implement.

It will be the best money you've ever spent protecting Windows from itself.



We use Deep Freeze here on a herd of over a hundred boxen and we've never had a virus on any of them.  Messages may come up while the public is surfing, mostly the fake "click here to protect your computer" type stuff, but a quick reboot and it's back to the pristine state they were in when they were frozen.

MS has a product called Steady State which is free to users of Genuine winders.  I use it on a few computers that are off the network and one that's on a network not under our control.  It seems to do a good job also.

Avast is my pick of AntiVirus software by the way.

Happy Virtualization.

---

### Post by ubu_can on 2009-08-11
I would also prefer to use VirtualBox rather than VMware, but I found the network interfaces to be so troublesome, and even after setting them up to be not better than something like 10 Mbit. Does the newest version offer any improvement on that?

---

