---
title: "block updates via terminal"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by 007casper on 2011-07-27
how do I block updates via terminal?

I want to do a manual update, and dont want to receive even a slight reminder for an update?

How can I do this via terminal?

recent, update screwed up my nvidia driver set up, and it took me a day and half to be able to fix it.

thank you.

---

### Post by StephanG on 2011-07-27
Unfortunately I don't know how to do it from the terminal, but you should be able to set the computer to never check for updates from the software sources settings.

But that would only mean that it doesn't check for updates.  If you want to 'block' specific packages from updating, I'm not sure how to do that.  All I know is that the default package manager in Kubuntu 11.10 might have that feature.

---

### Post by gigenieks on 2011-07-27
Why you want so strongly to do that via terminal? :confused:

I have Kubuntu.
Why can't you do it easy way --->

KPackageKit > Settings > Automatically install: None.
And [COLOR="DarkRed"]**uncheck**[/COLOR] box "Notify when updates are available".

Fast and easy!

---

### Post by 007casper on 2011-07-28
thank you.  I figure I can block specific updates maybe.

@gigenieks - there was a kernel update and that was the end for my old nvidia drive set up.

supposedly kernel had a bug, so does grub, and also intel wants to think that it is communicating with windows.  Whatever the reason is... it took me a day and half to fix the situation.

Then, I found out I am not alone in my misery.  A lot of people with nvidia had these issues.  The good part there was a fix.  The bad part, if there is going to be any conflict with updates and nvidia usage, there should be a warning.  Maybe even revert back the system to previous version before the update, so you can fix the situation on a split second and automate.  

If there is a simple solution, please let us all know.

It is frustrating.  This has been going on for a while.

---

### Post by mastablasta on 2011-07-28
> **007casper said:**
> thank you. I figure I can block specific updates maybe.
 
@gigenieks - there was a kernel update and that was the end for my old nvidia drive set up.
 
supposedly kernel had a bug, so does grub, and also intel wants to think that it is communicating with windows. Whatever the reason is... it took me a day and half to fix the situation.
 .
 
Heh so much for testing and "stability"...
 
> 
Then, I found out I am not alone in my misery. A lot of people with nvidia had these issues. The good part there was a fix. The bad part, if there is going to be any conflict with updates and nvidia usage, there should be a warning. Maybe even revert back the system to previous version before the update, so you can fix the situation on a split second and automate. 
 
If there is a simple solution, please let us all know.
 
It is frustrating. This has been going on for a while.
 
you can select older kernel in grub menu. thta should give you the old settings back.
 
i think Mint has a better definition of safe updates.

---

### Post by Paqman on 2011-07-28
Blocking all updates is a bad idea, some are important security updates. Ignoring them leaves you vulnerable.

---

### Post by Wim Sturkenboom on 2011-07-28
@007casper

It's supposedly common knowledge that if you use the drivers from nvidia, each kernel update is an issue. So if that's what you're using, you have to learn to live with it.

I know as I use one; I haven't managed to get the Ubuntu ones working with my nvidia 8400 based card. Takes me (nowadays) about 5 minutes to get it going again.

If it was because of a kernel bug, that is always the risk; any update can basically break something. I've applied every kernel update in the past 6 months or so and did not experience the problem (10.04 LTS 64 bit).

Not applying updates is in general not a good thing. As said, any update can break something. One of the best options to limit the risks is to install a second Ubuntu on the same system (or on a duplicate system) and test updates in it before applying the updates to the first one; note that it must be (from a software and hardware perspective) an exact copy.

---

### Post by gigenieks on 2011-07-28
I still don't understand what [COLOR="DarkRed"]**the problem**[/COLOR] is...
(English is not my native language)
And if I don't understand what you meant (what is the issue) probably others did not too :frown:

[quote=007casper]
end for my old nvidia drive set up.
[/quote]
"nvidia drive", what is that? :o I know there is "hard drive", but nvidia.. (Or did you mean "driver" or maybe "videocard")
Moreover, word "end" is not specific detail.. That is we **cannot** really tell what you meant with "end"

How exactly "end" your "nvidia drive" set up?

> 
The bad part, if there is going to be any conflict with updates and nvidia usage, there should be a warning.  

"conflict with updates and nvida usage" - Again not specific (at least for me) all updates? or only updates which influence your nVida videocard?

What kind of warning exactly?
> 
Don't install x updates because it could mess up your nvida drivers!

Something like that?

> 
Maybe even revert back the system to previous version before the update, so you can fix the situation on a split second and automate.

Now I am **really confused** :biggrin:

So, to clarify all --->
You found "fix" and you did fix your system (all is fine _now_) BUT in order it to stay "fine" you CAN'T install any updates related to nvida (meaning ANYTHING?) 

[COLOR="Navy"]**If that is the case, why can't use my suggested solution?**[/COLOR]
Just regulary (or so) check your updates and _read description_ which is important (security etc) and which are "nvidia related" and install accordingly.
Why can't this be done?



As for "revert back the system" don't know about this, but isn't in (K)Ubuntu something similar as System Restore in Windows?
(there must be)

And _mastablasta_ pointed also "select older kernel version from GRUB" why can't you do this? Just use old kernel?


[QUOTE=Wim Sturkenboom]
One of the best options to limit the risks is to install a second Ubuntu on the same system (or on a duplicate system) and test updates in it before applying the updates to the first one
[/QUOTE]
Am new and etc, but your suggestion is to install "sedond Ubuntu". If the goal is **testing**, shouldn't be more useful to use Virtualisation (Virtual Box, for example) there you could test those "suspicious" updates and if something goes wrong according to Virtual Box I am reading now (I will soon try for 1st time Virtual Box) it says following:

> 
[COLOR="Purple"]**Testing and disaster recovery.**[/COLOR] 

Once installed, a virtual machine and its virtual hard disks
can be considered a “container” that can be arbitrarily frozen, woken up, copied, backed up, and transported between hosts.

On top of that, with the use of another VirtualBox feature called [COLOR="DarkRed"]**“snapshots”, one can save a particular state of a virtual machine and revert back to that state, if necessary.**[/COLOR] 

This way, **one can freely experiment with a computing environment.** If something goes wrong (e.g. after installing misbehaving software or infecting the guest with a virus), one [COLOR="rgb(139, 0, 0)"]**can easily switch back**[/COLOR] to a previous snapshot and avoid the need of frequent backups and restores.

Any number of snapshots can be created, allowing you to travel back and forward in virtual machine time. You can delete snapshots while a VM is running to reclaim disk space.


---

### Post by 007casper on 2011-07-28
@Wim Sturkenboom - I have thought of the same thing.  And I do have the two computer that are two of a kind :)

when I was reading your post, it just came to mind that you can most likely test it via flash drive.

I guess you can always boot the latest version via usb stick and test drive it on the system.  If all goes well, you can then update the computer.

I am pretty sure, when you get used to hick ups with updates and nvidia, you just go for the hunt and try to fix the issue.  After a while, maybe it even becomes second nature.  Overall, it just becomes part of the experience.  However, for me it wasnt efficient at all.  It was one ting after another.  It is the grub, no -the kernel, no intel... wait, all of the above and on and on...

@mastablasta - thank you.  I found that while I was fixing it.  I wish it was apparent for me at the time.

thats why I was thinking if there was a warning, or some gui to revert back from the beginning.  It will be awesome. I am pretty sure most up coming users wont know that they can revert back the system. 

When you update your screen resolution, and change its settings it gives you 60 seconds to apply, then it times out and reverts back.  I just wish something like that happened... especially, when it is known that if you have nvidia, there could be issues, and the system recognizes it and gives you option to revert back or apply.

---

### Post by Wim Sturkenboom on 2011-07-28
> **007casper said:**
> I am pretty sure, when you get used to hick ups with updates and nvidia, you just go for the hunt and try to fix the issue. After a while, maybe it even becomes second nature. Overall, it just becomes part of the experience. However, for me it wasnt efficient at all. It was one ting after another. It is the grub, no -the kernel, no intel... wait, all of the above and on and on...

Don't worry; it took me a similar time when I replaced one nVidia based video card by another nVidia based card. Nothing should have been easier. Not with the f.ck.ng nouveau driver however :( After having taking that hurdle, I did not manage to get the drivers from the repository working (as mentioned erlier). So I ended up using a driver from the nvidia website.

Even Windows XP survived the excercise without giving me grief (fell back to some safe resolution or driver and allowed me to install new driver and I was good to go); this was unexpected.

One learns from it and with that comes the experience. Next time it only takes you an hour and eventually an annoying 5 minutes.

---

