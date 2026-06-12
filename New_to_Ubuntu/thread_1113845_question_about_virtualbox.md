---
title: "question about virtualbox"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by jaceh14 on 2009-04-02
i currently am running a dual boot with the pre-installed vista and ubuntu 8.10. i'm wanting to run solely on ubuntu while using virtualbox for my windows only programs (i own a zune). i just created my restore cd for vista because my laptop didn't come with one. my question is will i be able to install vista using this cd on virtualbox?

jace

---

### Post by Trebaruna on 2009-04-02
First of all: glad to see you're interested in running Ubuntu full time!

Now then: your preinstalled copy of Windows Vista most likely uses a special construction where your machine's BIOS contains a part of the license. I am not sure how well this works with virtualisation. In other words, I do not know whether you can just stick your copy in Virtualbox and have it work. VMs are cheap though: try it and see what happens.
If you need to manually activate, though, beware: do it too many times and Microsoft will require you to call them and promise them you're not installing it on 15 machines. All very degrading...

Secondly: if it does work, do not use the Open Source Edition of Virtualbox. Overall this version is great, but it does lack USB support: Windows will not actually see your device from within the VM. See virtualbox's website for more information, you should be able to use the closed-source version at no charge for non-commercial use.

Lastly: have you tried seeing whether there's software for Linux that duplicates the functionality you need with your Zune? Perhaps you do not need to keep a Windows VM around at all..!

---

### Post by Cybie257 on 2009-04-02
> **Trebaruna said:**
> 
Secondly: if it does work, do not use the Open Source Edition of Virtualbox. Overall this version is great, but it does lack USB support: Windows will not actually see your device from within the VM. See virtualbox's website for more information, you should be able to use the closed-source version at no charge for non-commercial use.



Interesting. I was about to comment on the idea of USB not working, but looking closer at the website, I have to say I never noticed the 2 different options. lol. I managed to just download the closed-source when I wanted to 'test things out' and compare it to VMWare Workstation. Nice that you pointed that out. 

The thing I like about Virtual Box vs VMWare is that it's a lot faster running on a Linux Platform. My XP VM runs about 2-2.5 times fast in VB then VMWare. But, as it is (and likely because VB is free), VMWare does have much more functionality. 

Example, I have Magic Jack and can only get half the unit to recognize via USB in VB. Works perfectly in VMWare. Before I decided to hook up and old computer to server just as a Magic Jack / Movie-Media center on my HDTV, I wanted to try to keep Magic Jack running while at the same time being able to run Linux as my main OS. 

The one problem I have run into, though, with Virtual Box is that installing the tools on a linux client, it breaks Xorg Server. At least with this setup:

HOST: Ubuntu 9.04 BETA (64bit)    CLIENT:Kubuntu 9.04 BETA (32bit)

-Cybie

---

### Post by tarps87 on 2009-04-02
> **Cybie257 said:**
> 
The one problem I have run into, though, with Virtual Box is that installing the tools on a linux client, it breaks Xorg Server. At least with this setup:

HOST: Ubuntu 9.04 BETA (64bit)    CLIENT:Kubuntu 9.04 BETA (32bit)


It would appear the Virtualbox additions are not computable with Ubuntu 9.04 BETA or any other variant, I discovered this on one of the early alphas. This should be fixed when Jaunty is officially released.

If you can get the recovery cd to work I suggest talking to the manufacture, you should be able to get a copy of the Vista cd and cd code. I most cases you have paid for the OS as well as the machine.

---

### Post by James_Lochhead on 2009-04-02
> **tarps87 said:**
> It would appear the Virtualbox additions are not computable with Ubuntu 9.04 BETA or any other variant, I discovered this on one of the early alphas. This should be fixed when Jaunty is officially released.


The additions work for me in the Jaunty beta.

---

### Post by tarps87 on 2009-04-02
> **James_Lochhead said:**
> The additions work for me in the Jaunty beta.

You broke it then :)
Do you have to do any other steps? I have just installed a clean beta version as a guest in Virtualbox so I'll give it a try

---

### Post by James_Lochhead on 2009-04-02
Think I just installed it. Might have been the closed source version though.

Removing now though as I just got VMware Workstation. :P

---

