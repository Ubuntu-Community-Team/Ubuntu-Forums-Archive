---
title: "Ubuntu 10.10 upgrade: Update Manager won't UPDATE!"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by phubert28 on 2010-10-11
64 bit Ubuntu 10.10 - JUST upgraded from 10.4!

Update Manager identifies items to be updated, but when I click ON "Install" NOTHING happens.

Restarted and tried again with same results!

---

### Post by Hippytaff on 2010-10-11
have you tried 

```

sudo apt-get update && sudo apt-get upgrade

```
instead?

---

### Post by phubert28 on 2010-10-11
Am doing so now at your suggestion, but why would the GUI app fail???

---

### Post by Hippytaff on 2010-10-11
lord only knows...and someone else here might also...I just know computers are fairly annoying for those of us why want to know why :-)

---

### Post by phubert28 on 2010-10-11
:-)

Well, thanks for the response, Hippytaff. It went into my Tomboy notes. Hope I didn't ALREADY HAVE it there!

Having programmed on and supported mainframes and mini's for almost 40 years, I fully understand! Tho in the mainframe days, I usually ARRIVED AT answers... something that seems far more elusive in today's more layered environments!

---

### Post by cgroza on 2010-10-11
Until you fix it use this.

Mark it as executable.

---

### Post by Hippytaff on 2010-10-11
> **phubert28 said:**
> :-)

Well, thanks for the response, Hippytaff. It went into my Tomboy notes. Hope I didn't ALREADY HAVE it there!

Having programmed on and supported mainframes and mini's for almost 40 years, I fully understand! Tho in the mainframe days, I usually ARRIVED AT answers... something that seems far more elusive in today's more layered environments!

there is a possitive correlation between layers elusiveness and annoyance :-)

still want to work out how and why though...like proding a sore tooth with my tongue :-D

---

### Post by phubert28 on 2010-10-11
cgroza, I know this will sound stupid, but I should LOOK for that file and make it executable then use that instead of Update Manager???

From what I've seen of 10.10 following the upgrade, however, I LOVE it!

I went 64 bit with 10.4 against the Ubuntu 'recommendation' for 32 bit because I really can't see why all OSes haven't pushed toward 64 bit already.

After all, how many CPUs still running ARE only 32 bit?????

AND we see they seem to be PUSHING the 64 bit version of Windows 7.

**

Of course I'm HOPING Update Manager 'fixes itself' ... or, at least, that whatever caused the problem might have been transient - though the restart SHOULD have fixed anything of that sort.

---

### Post by phubert28 on 2010-10-12
Update Manager "Install" function STILL doesn't work!

---

### Post by judedawson on 2010-10-12
Hi All,

Update Manager on my desktop is - for the first time - giving me problems. 

I'm running 10.04LTS Desktop edition. When I click on 'Check', the app shows the usual checking of files but stops during the process and displays an error message (pls. see attachment). 

From what I can understand from the error message, it could be a network problem. I've checked my internet connection and it's working fine. I also checked & confirmed the same internet settings are applied system-wide.

Any ideas as to what the cause of the problem might be?

Thanks, all.

PS: I'm relatively new to Ubuntu - so please be gentle :)

---

### Post by judedawson on 2010-10-15
Update Manager is working O.K now. I'm not sure of it 100% as there are so far no updated files to install. 

Still, I'll consider this issue CLOSED.

Thanks, all.

---

### Post by phubert28 on 2010-10-15
Well, MY Update Manager STILL does NOTHING when I click on "Install" ... every time.

And I've had plenty of modules ready for update.

So I keep doing it manually.

Do I post a new thread because someone else considers this solved?

Any way to post BUGS TO Canonical?????

---

### Post by rmadams1 on 2010-10-15
I had a similar problem phubert but I was running behind the company firewall and had to adjust proxy settings. Any chance that could be the issue, or are you running it sans firewall?

---

### Post by Hippytaff on 2010-10-15
Might it be worth uninstalling and reinstalling update manager?

---

### Post by DexterP17 on 2010-10-15
Thanks this worked for my computer.

---

### Post by phubert28 on 2010-10-15
So, do I Mark for Removal, Mark for COMPLETE Removal? Or??

I tried "Reinstall" and THAT didn't help.

---

### Post by TBABill on 2010-10-15
Best bet is probably complete removal, then right back into Synaptic, mark for installation and apply.

---

### Post by phubert28 on 2010-10-15
Did that. As before, the "Install Updates" button doesn't even 'highlight' as does the "Check" button when I mouseover. But it's not going to kill me to do the installs manually.

---

### Post by zer010 on 2010-10-15
> **phubert28 said:**
> 

I went 64 bit with 10.4 against the Ubuntu 'recommendation' for 32 bit because I really can't see why all OSes haven't pushed toward 64 bit already.

After all, how many CPUs still running ARE only 32 bit?????

AND we see they seem to be PUSHING the 64 bit version of Windows 7.



As you can see in my sig, I still use a 32 bit system, and happily so! :guitar:

---

### Post by phubert28 on 2010-10-15
'Happy with 32' doesn't answer my question about why 64 bit cpus **should** be running 32 bit software.

---

