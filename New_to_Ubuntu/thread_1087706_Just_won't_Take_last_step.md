---
title: "Just won't Take last step"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by hollowtd on 2009-03-05
I've got a Dell 2500 with Windows ME and 318 of ram. I've tried Ubunut, xubunut and linux mint and none of them will take the last cm step to finishing install. The bars stop right before it's finished and freezes up. The computer is not connected to the internet. (I installed Ubuntu on another dell and the inet was not needed.) Is there something wrong? It should def take xubuntu, right? Cheers as always for your help.

---

### Post by ptn107 on 2009-03-05
You are correct where Xubuntu would be the correct choice given your system specs.  In your case I would try the alternate CD which will use a text-based installer as opposed to a graphical one.  It will still ask the same questions.

_[Xubuntu 8.10 32-bit]("http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/8.10/release/xubuntu-8.10-alternate-i386.iso")_
_[Xubuntu 8.10 64-bit]("http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/8.10/release/xubuntu-8.10-alternate-amd64.iso")_

---

### Post by torgrot on 2009-03-05
Can you get XUbuntu to run from a live cd?  That would be my starting point.  I know my Dell requires some command line switches to run.  It has a problem with power management not being implemented correctly.  

torgrot

---

### Post by hollowtd on 2009-03-05
Will the onscreen layout (GUI I guess) be the same then too? I should go with 32 bit you think?

---

### Post by linuxuser21 on 2009-03-05
Are you sure it's froze?  I've made the mistake of thinking it's froze and then find out it was just taking a long time.

---

### Post by hollowtd on 2009-03-05
It does take a really long time though. How much time should I give it?

---

### Post by hollowtd on 2009-03-05
"Can you get XUbuntu to run from a live cd? That would be my starting point. I know my Dell requires some command line switches to run. It has a problem with power management not being implemented correctly." 

torgrot
_____

I'll try that now with the live cd (iso burned) and see what happens. I tested it yesterday to no avail. Thanks

---

### Post by hollowtd on 2009-03-05
I chose "try xubuntu without changes to your computer" is this right to test it?

---

### Post by torgrot on 2009-03-05
Yes that is what you should try.

torgrot

---

### Post by hollowtd on 2009-03-05
> **hollowtd said:**
> I chose "try xubuntu without changes to your computer" is this right to test it?

It's still "freezing" on the live CD too (without installing). Is it power management? Is there a way to change this? (help this?)

---

### Post by hollowtd on 2009-03-05
> **torgrot said:**
> Can you get XUbuntu to run from a live cd?  That would be my starting point.  I know my Dell requires some command line switches to run.  It has a problem with power management not being implemented correctly.  

torgrot

It seems to be "freezing" even with this?

---

### Post by hollowtd on 2009-03-05
Does anyone know how to fix "power managment" issues on my dell 2500 trying to load xubuntu. It just freezes even when I try to just run the life install cd. thanks

---

### Post by torgrot on 2009-03-05
Try adding this to as an option to the command line of the live CD 
acpi=off
 
torgrot

---

### Post by bu2971x on 2009-03-05
get a new computer. old laptops are just going to be a hassle always. move 
up or skip it.

---

### Post by hollowtd on 2009-03-05
This particular computer is for a school in Morocco. It is not for me. I have two good ones, but I collect these from donation for schools. These are considered "good" computers for there. I put Linux on them just in case Windows quits in the middle of no where. They can still "use" it then. So now that you understand you can help me. Thanks

---

### Post by hollowtd on 2009-03-05
> **torgrot said:**
> Try adding this to as an option to the command line of the live CD 
acpi=off
 
torgrot

I will try that. (Once it boots?)

---

### Post by avtolle on 2009-03-05
No, before it boots. See [https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20During%20Install]("https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20During%20Install") for information on how to do it.

EDIT: Sorry, misunderstood your question. Once you boot from the Live CD, before proceeding, see the linked piece as to how to put the boot option in the boot line. Good luck.

---

### Post by hollowtd on 2009-03-05
Thanks I'll look into that.

---

### Post by metal1dragon on 2009-03-05
I've been seeing the same thing.

---

### Post by tarps87 on 2009-03-05
> **hollowtd said:**
> Will the onscreen layout (GUI I guess) be the same then too? I should go with 32 bit you think?

With the alternate cd there is not GUI (as such), it follows the same steps and is just as easy as the live cd based installer. It is less memory intensive which may be what is causing it to freeze.

You should use the 32bit version (the default version) as the CPU is 32bit, the 64bit version won't play

> **torgrot said:**
> Try adding this to as an option to the command line of the live CD 
acpi=off
 
torgrot

If this does not solve it try the alternate cd, I could just be down to low specs

> **bu2971x said:**
> get a new computer. old laptops are just going to be a hassle always. move 
up or skip it.

Not very helpful.
I have installed Ubuntu 8.04(Gnome) on a lower spec machine and haven't had a problem, I did use the alternative cd though

---

### Post by chamber on 2009-03-05
Try using CrunchBang, PuppyLinux, Damn Small Linux or a minimal install of Ubuntu.  While xubuntu is "lighter" I believe you would get better results from either of the ones I mentioned.

My laptop would freeze when trying to load a live version of Ubuntu but ran like a dream with crunchbang.

---

### Post by hollowtd on 2009-03-05
I'll try all of these and let you know what works. Thanks for the helpful hints. I should think that this could work. The computer isn't that bad or slow, well a little...

---

### Post by Yed Ied on 2009-03-21
I've had the same problem with an EMachine.  It ejects the disk asks for "user name" and "password" goes to a tan screen and then goes to a black screen.  I know the CD is golden, I've made several successful downloads and am using two of them personally.  Let me know if you can figure it out.  I think it has something to do with the chipset, but I'm not that bright.

---

