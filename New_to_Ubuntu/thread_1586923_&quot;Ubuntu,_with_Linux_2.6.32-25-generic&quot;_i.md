---
title: "&quot;Ubuntu, with Linux 2.6.32-25-generic&quot; in GRUB2 - Ubuntu 10.04"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by amjjawad on 2010-10-02
Hi everyone,

1- I installed Ubuntu 10.04 today (had Fedora 13 before that).
2- I got the package manager and it asked me to update so I "updated" Ubuntu by downloading the necessary updates. Actually, I chose all and there were 84 or 86 items.
3- Download done, restart done.
4- Upon rebooting, I got black screen so had to restart again and it worked.
5- While I'm on GRUB2, I noticed that I have:

Ubuntu, with Linux 2.6.32-25-generic
Ubuntu, with Linux 2.6.32-25-generic - Rescue mode
Ubuntu, with Linux 2.6.32-24-generic
Ubuntu, with Linux 2.6.32-24-generic - Rescue mode
Memory test .... (something)
Memory test .... (something)
Windows 2000/XP


Now, my questions are:

A) what does "Ubuntu, with Linux 2.6.32-25-generic" mean?

B) Why do I have two entries? why it kept the old one anyway after the update?

C) Shall I get another entry after another update?

D) Is there any way to edit that? in case I'll get more entires every time I update Ubuntu?


That's all for now :)

Please note that what I did was "update" not upgrade as I do have the latest version/edition of Ubuntu 10.04.

I might be not that smart question but I'd like to understand each and every single thing in Ubuntu/Linux :)

Thanks!

---

### Post by drs305 on 2010-10-02
There are various 'flavors' of the kernel, such as "rt" (real time). You have the 'generic' kernel. Someone else can probably provide more details.

Each time a kernel is added it will be added to the Grub menu. You can shorten the menu by physically removing the kernel from the machine or hide them by altering the Grub scripts.

The intro section of the "G2-Tweaks" explains how to remove the kernels, and section 2 gives you a way to tweak a script so only X number are displayed (caution: geek alert).

The "SUM" link is generally about StartUp-Manager, but I'd recommend Ubuntu-Tweak for physically removing older kernels. See the section on Removing Older Kernels near the end of the "SUM" post.

---

### Post by DougieFresh4U on 2010-10-02
> **amjjawad said:**
> 


Now, my questions are:

A) what does "Ubuntu, with Linux 2.6.32-25-generic" mean?

B) Why do I have two entries? why it kept the old one anyway after the update?

C) Shall I get another entry after another update?

D) Is there any way to edit that? in case I'll get more entires every time I update Ubuntu?


T

A) means you are using the 'generic kernel'
B) when kernel is updated, it will reboot to the latest kernel unless you arrow down in grub
C) yes, new kernels will enter automatically
D) you can open Synaptic Package Manager and look for linux image and linux headers and you will see whats installed and you can remove the linux image from there.

If you need more detailed info, you can always ask again :)

---

### Post by Old_Grey_Wolf on 2010-10-02
> **drs305 said:**
> The intro section of the "G2-Tweaks" explains how to remove the kernels, and section 2 gives you a way to tweak a script so only X number are displayed (caution: geek alert).

You should have given a hyperlink. Here is a link to G2-Tweaks [http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602).

Edit: I see it is in your signature.:oops:

---

### Post by drs305 on 2010-10-02
All the links are in my signature line. Since I mentioned the SUM link I figured he/she would see the other as well.  

Sometimes I'm just less energenic than others. I'll try harder. ;-)

---

### Post by Old_Grey_Wolf on 2010-10-02
> **drs305 said:**
> All the links are in my signature line. Since I mentioned the SUM link I figured he/she would see the other as well.  

Sometimes I'm just less energenic than others. I'll try harder. ;-)

I was embarrassed when I read your signature. I generally don't read signatures anymore. I know people don't read mine.
:lolflag:

---

### Post by drs305 on 2010-10-02
> **Old_Gray_Wolf said:**
> I was embarrassed when I read your signature. I generally don't read signatures anymore. I know people don't read mine.
:lolflag:

No problem. There are actually benefits to posting the link in the body, which I normally do. If I change my signature line in the future the link would no longer be available, and I didn't give the full title either. So your effort wasn't in vain.

---

### Post by amjjawad on 2010-10-02
When you say "flavor", does that mean "theme"? sorry, I need sometime to get used on such terms :oops:

I'll look into these links later because my battery is very low now, I mean my human battery :P THANKS :)

---

### Post by amjjawad on 2010-10-02
> **DougieFresh4U said:**
> A) means you are using the 'generic kernel'
B) when kernel is updated, it will reboot to the latest kernel unless you arrow down in grub
C) yes, new kernels will enter automatically
D) you can open Synaptic Package Manager and look for linux image and linux headers and you will see whats installed and you can remove the linux image from there.

If you need more detailed info, you can always ask again :)

Thanks, DougieFresh4U :)

A) I can tell from your reply and drs305's reply that there are some other kernels but the question is what's the difference?

B) Yes and that's not the issue but I was wondering why it's added anyway? is it kind of restore? I mean, in case something goes wrong with the latest, can I go back to the previous? there must be a reason of having the latest and the previous ones :)


C) Sigh, then I need to keep tweaking :)

D) It looks easier than what drs305 suggested but does it work that way too? so I have two options: either by removing it as drs305 posted or uninstall it from Synaptic Package Manager, right?


Thank you :)__

---

### Post by drs305 on 2010-10-02
> **drs305 said:**
> 

When you say "flavor", does that mean "theme"? sorry, I need sometime to get used on such terms :oops:

I'll look into these links later because my battery is very low now, I mean my human battery :P THANKS :)

I am not a hardware person and shouldn't use terms that are technically incomprehensible - don't worry yourself about 'flavor'!  ;-)

Kernels can be built specifically to optimize a particular processor/hardware. The 'generic' kernel is built in a way that it can accommodate a wider range of hardware and choose the optimizations suited for a specific type of processor. So in most cases with a modern processor, the generic kernel is a good choice for most users.

---

### Post by DougieFresh4U on 2010-10-02
> **amjjawad said:**
> Thanks, DougieFresh4U :)

A) I can tell from your reply and drs305's reply that there are some other kernels but the question is what's the difference?

B) Yes and that's not the issue but I was wondering why it's added anyway? is it kind of restore? I mean, in case something goes wrong with the latest, can I go back to the previous? there must be a reason of having the latest and the previous ones :)


C) Sigh, then I need to keep tweaking :)

D) It looks easier than what drs305 suggested but does it work that way too? so I have two options: either by removing it as drs305 posted or uninstall it from Synaptic Package Manager, right?


Thank you :)__
A)different hardware but 'generic' pretty much covers most

B) it's nice to have one or two other kernels in grub as you may need to boot into one of them when something goes wrong in the newest kernel

C) I always run **sudo update-grub2** after each kernel upgrade. Kind of 'tidies' things up for ya

D) I use Synaptic to remove older kernels. I just look in Synaptic at the linux-image and linux-header and you can pretty much see the difference, being the numbers and just tick them  and 'aaply'

---

### Post by amjjawad on 2010-10-03
> **drs305 said:**
> I am not a hardware person and shouldn't use terms that are technically incomprehensible - don't worry yourself about 'flavor'!  ;-)

Kernels can be built specifically to optimize a particular processor/hardware. The 'generic' kernel is built in a way that it can accommodate a wider range of hardware and choose the optimizations suited for a specific type of processor. So in most cases with a modern processor, the generic kernel is a good choice for most users.

That makes sense now, thanks drs305 :)

Now, I have a little question ... I didn't choose "generic kernel" so does it mean there are other kernels but the installation did not install them because for example I have Intel CPU (processor) or certain Hardwares that only generic works with them?
I downloaded ubuntu 10.04 32-bit from Ubuntu's website and burned the image (.iso) to a CD. From what you posted, I can tell there are some other kernels in that CD but all what my PC needs is generic.

---

### Post by amjjawad on 2010-10-03
> **DougieFresh4U said:**
> A)different hardware but 'generic' pretty much covers most

B) it's nice to have one or two other kernels in grub as you may need to boot into one of them when something goes wrong in the newest kernel

C) I always run **sudo update-grub2** after each kernel upgrade. Kind of 'tidies' things up for ya

D) I use Synaptic to remove older kernels. I just look in Synaptic at the linux-image and linux-header and you can pretty much see the difference, being the numbers and just tick them  and 'aaply'

A) Yes, it makes sense now :)

B) So as I said, it's kind of restore thing just in case something wrong might happen. Good :)

C) Hmmm, is it safe to run "**sudo update-grub2**" after each upgrade/update? I have dual boot with XP but grub2 is on a separate external HDD. Is that commend used to update grub2 in general?

D) During the update, I noticed something called "linux-image" but didn't search for it yet on Synaptic. I think I have to do that when I'll get more entries :)

Thank you :)

---

### Post by drs305 on 2010-10-03
1. The generic kernel should suit your needs, but for a bit of explanation:

To see the kernels that are currently available to you from the Ubuntu standard repositories, open Synaptic and type "linux-image" in the top right search box.

You can highlight each "linux-image......" and in the lower right window you can read a little about the kernel. On my installation, I have kernels available for *generic, server, ec2 and virtual*. The "linux-image" listing is the generic kernel, so installing just "linux-image" with no additions to the name will install the current generic kernel.

2. The command "update-grub2" is a stub for "update-grub", so you can just use "update-grub" if you wish. "update-grub" is itself actually a 'stub' for the longer command 'grub-mkconfig -o /boot/grub/grub.cfg'.

3. The system will automatically run update-grub when it is necessary to update the grub.cfg file, such as the introduction of a new kernel or an update to the grub package itself. It runs the scripts in the */etc/grub.d/* folder and generates a new /boot/grub/grub.cfg file. If your external drive was not connected at the time the update was made, your computer should still use and boot the old grub.cfg.

You can manually run "sudo update-grub" but normally would do this only after making a change to the */etc/default/grub* file, which includes settings for things such as the menu timeout and default OS. You might also manually run it if you want Grub2 to search for another OS that isn't displaying, have made changes to another OS that would effect its boot or that you have just added. As I said, though, normally you don't have to run the update manually.



Since you already have a working

---

### Post by amjjawad on 2010-10-03
> **drs305 said:**
> 1. The generic kernel should suit your needs, but for a bit of explanation:

To see the kernels that are currently available to you from the Ubuntu standard repositories, open Synaptic and type "linux-image" in the top right search box.

You can highlight each "linux-image......" and in the lower right window you can read a little about the kernel. On my installation, I have kernels available for *generic, server, ec2 and virtual*. The "linux-image" listing is the generic kernel, so installing just "linux-image" with no additions to the name will install the current generic kernel.

2. The command "update-grub2" is a stub for "update-grub", so you can just use "update-grub" if you wish. "update-grub" is itself actually a 'stub' for the longer command 'grub-mkconfig -o /boot/grub/grub.cfg'.

3. The system will automatically run update-grub when it is necessary to update the grub.cfg file, such as the introduction of a new kernel or an update to the grub package itself. It runs the scripts in the */etc/grub.d/* folder and generates a new /boot/grub/grub.cfg file. If your external drive was not connected at the time the update was made, your computer should still use and boot the old grub.cfg.

You can manually run "sudo update-grub" but normally would do this only after making a change to the */etc/default/grub* file, which includes settings for things such as the menu timeout and default OS. You might also manually run it if you want Grub2 to search for another OS that isn't displaying, have made changes to another OS that would effect its boot or that you have just added. As I said, though, normally you don't have to run the update manually.



Since you already have a working

1- I checked "Linux-image" in Synaptic and I have the same as what you have. Now, I understand that Ubuntu install the kernel that suits my PC's needs or my needs. Of course I won't have "server" as long as I don't have it :)

2- Good to know that. Thank you :)

3- "If your external drive was not connected at the time the update was made, your computer should still use and boot the old grub.cfg." << I didn't understand this part. Ubuntu is installed on my external HDD and I can't run Ubuntu unless that external drive is connected.

So, there's no need to run:

```
sudo update-grub
``` as long as the system will do it automatically.
On the other hand, I can run it when:

1- After making a change to the */etc/default/grub* file, which includes settings for things such as the menu timeout and default OS.

2- Grub2 to search for another OS that isn't displaying, have made changes to another OS that would effect its boot or that you have just added.

Thanks a lot for all this :)

The next update, I'll have 3 entries so guess I have to remove one and keep only 2 entries.

---

### Post by drs305 on 2010-10-03
> **amjjawad said:**
> 3- "If your external drive was not connected at the time the update was made, your computer should still use and boot the old grub.cfg." << I didn't understand this part. Ubuntu is installed on my external HDD and I can't run Ubuntu unless that external drive is connected.

If the OS is installed on your external, the above is only academic. What I was trying to say was that if the grub.cfg file didn't get updated it would just use the old one, which would still work as long as the default kernel wasn't removed.

---

### Post by amjjawad on 2010-10-03
> **drs305 said:**
> If the OS is installed on your external, the above is only academic. What I was trying to say was that if the grub.cfg file didn't get updated it would just use the old one, which would still work as long as the default kernel wasn't removed.

Thanks a lot for the explanation :)
I'll never remove the first kernel and will always keep two entries :)
I don't mind that at all. Perhaps when I'll understand more about Linux/Ubuntu, I'll play around with the GRUB. Honestly, I read many articles about GRUB but I feel I'm still far away from it. Maybe because I'm still new to this.

You know? I regret that I spent 10 years with Windows :(

---

### Post by amjjawad on 2010-10-17
I didn't mark this thread as SOLVED because I thought I would be able to tweak GRUB2 but I have entirely different setup at the moment.

I'll mark it as SOLVED at the moment.

Thanks everyone :)

---

