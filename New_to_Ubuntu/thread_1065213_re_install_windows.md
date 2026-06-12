---
title: "re install windows"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by muldengold on 2009-02-09
Hi,
I've windowsxp and ubuntu (8.10) installed on separate partitions. I need to reinstall windows. My main concern is to do any harm to the ubuntu installation or to the grub loader. Is there anything to consider or just tell windows which partition I want to install it on?

Thanks!
Sandro

---

### Post by unplugged23 on 2009-02-09
I think im having trouble understanding what you want to do. you say you want to install windows but you also say you have it installed. would you please clarify? :confused:

EDIT: oh you want to reinstall it? why? where? how? sorry for the confusion

---

### Post by muldengold on 2009-02-09
yes, windows is installed already, however I need to install it newly

---

### Post by joey-elijah on 2009-02-09
It might kick up a fuss regarding not being a primary partition. If it doesn't, the only issue you'll likely have is GRUB MENU being over-written by the Windows Bootloader.

This is easily solved by simply reinstalling grub after installing Windows.

---

### Post by muldengold on 2009-02-09
windows does funny things since I installed SP3 (works extremely slowly), but may be coincidence. Uninatalling SP3 didn't help. Checked for viruses but there seems to be nothing. I thought simply reinstalling from scratch will fix it.
Thanks.

---

### Post by muldengold on 2009-02-09
Hi Joey, what do you mean by kick up a fuss?

---

### Post by kansasnoob on 2009-02-09
Well, of course you'll have to be careful to re-install Windows in the correct partition. That goes without saying and of course it's always wise to use whatever means you have at hand to back up anything you don't want to lose!

But, you'll also need to know how to reinstall GRUB (the GRand Unified Bootloader)! It's very simple really. Just boot any Ubuntu Live CD after checking out your fresh Win install and do the following:

> After booting up your live CD, open terminal (Applications -> Accessories -> Terminal). and type:

```
sudo grub
```

That will drop you into "grub mode"! Like this:

>        [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> 


Then type:

```
find /boot/grub/stage1
```

You'll get an output like "(hd0,1)", whatever that output is you'll want to use for the next command!

Like:

```
root (hd0,0)
```

Which assumes that Ubuntu is on drive #1, partition #1! Just replace "(hd0,0)" with whatever the output from "find /boot/grub/stage1" was!

Then run the command:

```
setup (hd0)
```

Of course that only works if Ubuntu is on drive #1! If the output of "find /boot/grub/stage1" said something like (hd1,0) then you'd enter (hd1) here!

Then finally type:

```
quit
```

Does that make sense to you?

---

### Post by unplugged23 on 2009-02-09
> **joey-elijah said:**
> It might kick up a fuss regarding not being a primary partition. If it doesn't, the only issue you'll likely have is GRUB MENU being over-written by the Windows Bootloader.

This is easily solved by simply reinstalling grub after installing Windows.

This post pretty much sums it up, although i have no idea how anyone could even be interested in windows afters using ubuntu for awhile

---

### Post by SunnyRabbiera on 2009-02-09
> **unplugged23 said:**
> This post pretty much sums it up, although i have no idea how anyone could even be interested in windows afters using ubuntu for awhile

well a dual boot is practice for many, especially gamers.

---

### Post by unplugged23 on 2009-02-09
> **SunnyRabbiera said:**
> well a dual boot is practice for many, especially gamers.

I used to game... 

Then i found ubuntu, lol

Once i got into ubuntu i became obsessed with learning shell script and programing etc.

I don't game much anymore :(

Thanks to ubuntu I've kicked my WoW habbit. Now if an OS can do that...

---

### Post by Ericyzfr1 on 2009-02-09
Save your Ubuntu partitions with G4l and after reinstalling windows restore the mbr from the ubuntu image file.
Acronis true image can do it too, easier to use but both will do the job fine.

---

### Post by kansasnoob on 2009-02-09
> **unplugged23 said:**
> This post pretty much sums it up, although i have no idea how anyone could even be interested in windows afters using ubuntu for awhile

Hey! It's tax time here and I do volunteer work. Only Windows is accepted! I hope that changes, but until it does ..............

---

### Post by unplugged23 on 2009-02-09
> **kansasnoob said:**
> Hey! It's tax time here and I do volunteer work. Only Windows is accepted! I hope that changes, but until it does ..............

Note how i said "interested" which you are clearly not. i can tell you wish you could use ubuntu :)

---

### Post by kansasnoob on 2009-02-09
> **unplugged23 said:**
> Note how i said "interested" which you are clearly not. i can tell you wish you could use ubuntu :)

Oh, I do use Ubuntu (and/or Linux Mint)! For almost everything! I seldom boot into Windows!

But the fact is that Windows still has the lions share of the market and not everyone is willing to play with Linux!

That's a fact we must deal with!

---

### Post by unplugged23 on 2009-02-09
Yea, awhile back Microsoft was facing court for being a monopoly company. I don't know whatever happened to that, but i think Microsoft came out of it O.K. which it pretty messed up in my opinion. Google could also be facing some similar issues soon.

---

### Post by muldengold on 2009-02-11
Thanks eveyone. It worked well and I didn't have to bother with any GRUB tinkering. 

Re for what do I need Windows: for not many things nowadays really. I still use a Video editing program in windows as kdenlive tends to come up with "fatal" errors and I don't like Cinelerra (is there any other option?). I still think that the nautilus file browser isn't as good as the windows explorer. I also play sometimes old fashioned Age of Empires just for fun (doesn't work well with wine). But that's it. 

Cheers,
Sandro

---

