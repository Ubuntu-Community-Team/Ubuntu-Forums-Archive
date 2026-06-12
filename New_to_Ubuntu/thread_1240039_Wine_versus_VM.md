---
title: "Wine versus VM"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by BobJam on 2009-08-14
I've been reading a lot about Wine lately, and the Wine page specifically states that it's easier on resources . . . flat out easier all around . . . than a VM.

Now that may be a lot of marketing hype or a case of the fox guarding the chickens . . . I really don't know.  Which is why I'm asking the question here.  I'm hoping that posters will give me a more unbiased list of pluses and minuses to each.

I'm tethered to Windows by virtue of Quicken and my on line banking.  (I've looked at all the Ubuntu financial managers, and there is not one that does what I want . . . so I'm bound to Quicken.)

Currently I have a VM ("Sun Virtual Box") with XP on it, and I have loaded Quicken on it . . . and it works nicely.  (Have the Guest Additions installed too, so it is seamless).

However, with all I've been reading about Wine, it may be a better way to go than the VM I am using.  Don't know . . . which is again why I'm asking the question here.

My sense is that there are a lot of Wine users here that will give me their side, and there are a lot of VM users that will give me their side.  With input like that, I'll be better able to decide which way to go for good.

One last note:  I'm **NOT** a gamer.  I say that because it seems like Wine is focused on gaming software, though I've seen that it certainly runs other software (Quicken is on it's **Gold** list).  My only reason for using it would be Quicken.

I'm inclined to follow the truism "If it ain't broke, don't fix it".  My VM runs fine and I can do my on line banking within it.  But I want to take a look at what Wine may offer above a VM . . . if it does, that is.

---

### Post by aeiah on 2009-08-14
i think as a rule, if wine works for the applications you use then it'll offer better performance and better productivity, but if you have several applications that dont work in wine then a single VM with everything in will make life easier

---

### Post by howefield on 2009-08-14
Running it in wine means you have instant access via your applications menu to start it up, without first starting and waiting for your vm to load.

And as Quicken is on the "Gold" list, then that would seal it for me.

I use both Wine and Virtualbox to run windows programs, but would always pick wine first for any app which works really well with it.

---

### Post by scorp123 on 2009-08-14
> **BobJam said:**
>  Currently I have a VM ("Sun Virtual Box") with XP on it, and I have loaded Quicken on it . . . and it works nicely.  (Have the Guest Additions installed too, so it is seamless). Is it broken? No. So don't fix it then.

There are valid reasons for both WINE and/or using a VM. But if the VM you already have works tip top for you ... why bother?

I'd leave everything "as is".

---

### Post by 3rdalbum on 2009-08-14
> **howefield said:**
> Running it in wine means you have instant access via your applications menu to start it up, without first starting and waiting for your vm to load.

Snapshots in your VM load almost instantly.

Wine doesn't have the overhead of a second operating system.

---

### Post by dawynn on 2009-08-14
> Now that may be a lot of marketing hype or a case of the fox guarding the chickens . . .
Honestly, what does Wine have to protect?  Their market share?  Its a free product!  They really have no gain whether you use Wine or not!

Wine tries to interpret all of the binary bitcodes from your Windows program and convert them to Linux calls.  They have had some success with this, but everything is not perfect yet.  But honestly, Wine is not focused on games.  Cedega is focused on games.  But that's getting off-topic.

Your VM cuts out a chunk of resources that you can then load another system on.  Its as if you had a smaller computer inside your computer.  You can then load a true copy of full branded Windows inside your VM, then run your software (Quicken in this case).

The VM is going to be more resource hungry because you'll have two entire operating systems running -- Linux and Windows -- in addition to the software that you want to run.  If your computer can handle the extra load, you'll find that running Windows in a VM mode should provide an accurate Windows experience.  Running your software in Wine, while lighter on resources, is an estimation, and depending on whether the Wine coders have coded all the right calls correctly, may or may not provide an accurate experience.

---

### Post by BobJam on 2009-08-18
> **scorp123 said:**
> Is it broken? No. So don't fix it then.

There are valid reasons for both WINE and/or using a VM. But if the VM you already have works tip top for you ... why bother?

I'd leave everything "as is".

You're probably pretty much right.

WINE seems a bit cranky.  And I downloaded the latest version from the WINE repository.

I'm having trouble getting IE to work, plus Quicken, 7Zip, and explorer too.  Sometimes they work completely, sometimes not, sometimes partially.  Is premature to report the glitches to the WINE app database just yet.

I expect WINE needs a little tweaking to get these things working consistently, or else I need to learn my way around WINE better.

But the VM I'm using works flawlessly all the time.  While WINE may reduce the overhead, I'm not so sure all the effort is going to be productive.

Will continue to mess with WINE, primarily because I like doing that sort of thing.  But in the meantime, I have the VM and can use that for "serious" work.

---

