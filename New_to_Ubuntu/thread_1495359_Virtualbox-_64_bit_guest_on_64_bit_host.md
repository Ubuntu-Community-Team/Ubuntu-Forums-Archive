---
title: "Virtualbox- 64 bit guest on 64 bit host"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by SwatKat on 2010-05-28
Hi all,
I'm unable to run a 64 bit guest os on virtualbox. I get the message shown in the screenshot. 
But I couldn't find anything like VT-x/AMD-V in the BIOS. However, I did did find an option called virtualization which I enabled. But apparently, its not enough. I know that my cpu supports AMD-v virtualization since I get the svm flag when I do

```
grep --color svm /proc/cpuinfo
```What am I missing?

---

### Post by cariboo on 2010-05-28
I don't know if it makes any difference, but are you running a 32-bit version?

---

### Post by CharlesA on 2010-05-28
If you created the VM with VT turned on, turn it off and see what it does.

---

### Post by sandyd on 2010-05-28
> **SwatKat said:**
> Hi all,
I'm unable to run a 64 bit guest os on virtualbox. I get the message shown in the screenshot. 
But I couldn't find anything like VT-x/AMD-V in the BIOS. However, I did did find an option called virtualization which I enabled. But apparently, its not enough. I know that my cpu supports AMD-v virtualization since I get the svm flag when I do

```
grep --color svm /proc/cpuinfo
```What am I missing?
This may sound stupid, but have you enabled VT-x/AMD-V in the virtualbox settings?

p.s. some manufacturers don't show the option to turn it on/off in the bils.

p.p.s. : can you run
```

lsmod | grep vbox

```

---

### Post by SwatKat on 2010-05-28
> **cariboo907 said:**
> I don't know if it makes any difference, but are you running a 32-bit version?

Do you mean 32 bit version of vbox? No, its a 64 bit version. I'm trying to run a 64 bit guest on a 64 bit host using 64 bit vbox.

[QUOTE=CharlesA] If you created the VM with VT turned on, turn it off and see what it  does[/QUOTE]I first got that message with VT turned off. Then I created the VM after turning it on but got the same message again:(

 [QUOTE=carlee]have you enabled VT-x/AMD-V in the virtualbox settings[/QUOTE]Oh yes, its definitely enabled.

 > some manufacturers don't show the option to turn it on/off in the bilsIs there a way to check whether its enabled and enable it if its not from ubuntu? I couldn't find anything by googling

> can you run
lsmod | grep vbox
 Here you go

vboxnetadp              5171  0 
vboxnetflt     15064  0 
vboxdrv              1792375  2 vboxnetadp,vboxnetflt

I can run a 32 bit guest os without any problems. 
I really appreciate the help, everyone :)

---

### Post by WinterRain on 2010-05-28
> **SwatKat said:**
> 
I can run a 32 bit guest os without any problems. 
I really appreciate the help, everyone :)
Same here, but after much research, if your BIOS does not have VT-x/AMD-V settings, then you are out of luck. Besides, there's not much point in running 64bit OS in vbox unless you are specifically testing something that requires 64bit.

---

### Post by BugBuster on 2010-05-28
Hi SwatKat, I too had exactly the same issue with my MSI K9AGM4-L mobo. Then I wrote about the issue to the MSI tech-support and they provided me with a custom BIOS that had an option to enable or disable SVM. Before I had no such option in the BIOS.

Also lately in their latest standard BIOS for this motherboard they have included that option as well.

So I would suggest you write to your motherboard vendor as this seems like a BIOS issue.

I may be entirely wrong and you may find a better solution from others here, but the symptoms/events you have mentioned in your post were too familiar to resist posting my case:)

---

### Post by SwatKat on 2010-05-29
So I have to either write to tech support and get a custom BIOS or just be happy with running 32 bit guest oses ? Well thats a bummer. Anyways, thanks for the help guys.

---

