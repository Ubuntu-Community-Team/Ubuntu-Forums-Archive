---
title: "virtual box?"
date: 2010-12-06
forum: New to Ubuntu
---

### Post by gmenfan83 on 2010-12-06
I have read and understand his to use and installing virtual box. My only question is I am using dual boot for ubuntu 10.10 and windows vista
...now is there a way I can run virtual box using my windows partition inside ubuntu to eliminate having to reboot in order to run windows?

---

### Post by gradinaruvasile on 2010-12-06
I dont think you can do that directly in VirtualBox.

---

### Post by snowpine on 2010-12-06
No, you'll need to do a separate install of Vista inside the virtual machine (and you will need a 2nd Windows license).

---

### Post by gmenfan83 on 2010-12-06
Thank you guys for the help and replies

---

### Post by pricetech on 2010-12-06
Install Vista as a VM.  As far as licensing; using the number on the COA attached to your computer will work if it's an OEM install (usually).  You'll still need to remove the original Vista install though.

---

### Post by gmenfan83 on 2010-12-06
> **pricetech said:**
> Install Vista as a VM.  As far as licensing; using the number on the COA attached to your computer will work if it's an OEM install (usually).  You'll still need to remove the original Vista install though.

My only problem reinstalling vista as a vm is I no longer have the vista disc .....no biggie just thought it would be nice to not have to reboot...now I know I can reinstall ubuntu as the vm but then don't I lose memory or space since its not directly partitioned?or maybe I can just use wine but then I get worried using wine since I believe the major threat for virus and malware and spyware present themselves since they are window programs no?

---

### Post by anewguy on 2010-12-06
Actually, unless they have removed it, it is possible.  I did this with XP a few years ago.  But please don't - it's full of risks - big ones.  And, once you've booted it in virtualbox, you can't go back to just booting stand alone as it changes all kinds of the devices.  I didn't heed the advice of bodhi.zazen (one of the big gurus here) at the time and persisted in doing it anyway - it was not a good idea.  If you are determined to hose things up ( ;) ) then read the virtualbox help itself - particularly that on using the virtualbox command line (vbox something, I just don't remember now).

My suggestion is to find one of the programs that will build a Windows installation disk (an adjunct to slipstreaming) from your existing installation.  I've heard of them, but never used them.  Another alternative might be something like Macrium Reflect - build an image of your installation, then create a virtual machine.  Boot the machine using a Macrium Reflect recovery disk and restore the Windows image back into the virtual machine.  I use Macrium Reflect - just haven't ever tried using it this way, but I think it should work.

Dave ;)

---

### Post by snowpine on 2010-12-06
> **gmenfan83 said:**
> My only problem reinstalling vista as a vm is I no longer have the vista disc .....no biggie just thought it would be nice to not have to reboot...now I know I can reinstall ubuntu as the vm but then don't I lose memory or space since its not directly partitioned?or maybe I can just use wine but then I get worried using wine since I believe the major threat for virus and malware and spyware present themselves since they are window programs no?

I've never heard of anyone getting a virus by running a Windows app in Ubuntu using Wine; I wouldn't worry too much about it. :)

---

### Post by sp-1070 on 2010-12-06
If i where you.

Ditch vista get ubuntu 10.10 use entire disk,
start a Virtual Box and install windows xp or 7.

---

### Post by gmenfan83 on 2010-12-06
> **sp-1070 said:**
> If i where you.

Ditch vista get ubuntu 10.10 use entire disk,
start a Virtual Box and install windows xp or 7.

I would but I don't have a windows disk and can't really afford it at the time and am starting school next month and im going for computers and would like to at least keep dual boot in case I need windows ....if I had the funds for the dusk I would do just that then ...I guess I will run wine and dual boot for now if need be ...thank you all for the help

---

### Post by gradinaruvasile on 2010-12-06
You could try dd-ing the vista partition to an img file, create a larger-than-vista-partition virtual drive, boot with a live cd, and dd it to the created virtual drive. Something like that. You at least need twice the original partitions size free space for this though.

Maybe it will not crash completely (new "hardware" and all) at startup...

Anyone tried something like this?

---

### Post by pricetech on 2010-12-07
Haven't, but I might in my "spare time" since I have the spare hardware to tinker with.

If I do, I'll post the results.

---

