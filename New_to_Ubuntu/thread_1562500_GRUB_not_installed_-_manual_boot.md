---
title: "GRUB not installed - manual boot???"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by ketisfolk on 2010-08-27
So I'm a complete noob, hence why I'm writing here. Have spent half of today trying to do a clean install of Ubuntu LL. The desktop version I downloaded and burnt to cd didn't work, so I got another version from [http://cdimage.ubuntu.com/lucid/daily/current/](http://cdimage.ubuntu.com/lucid/daily/current/) which initially didn't work and then did, except for the rather crucial part of the GRUB bootstrap loader. It allowed me skip past while giving me the following message:

boot manually with the /vmlinuz kernal on partition /dev/sda1 and root=/dev/sda1 passed as a kernal argument

I have no idea how to instigate this, and now when I turn the laptop on, it comes up with the boot screen, a few lines of text that it always came up with and then the blinking cursor.

Anybody to help me?

---

### Post by ketisfolk on 2010-08-27
OK, put the CD pack in, it got to the GRUB boot loader part and noticed ubuntu was the only installed system and so put in a loader (so I think). It's now coming up with mmc0: unknown controller version (16). You may experience problems. I can't input anything here, there is just a blinking cursor.

Once again, help!

---

### Post by 29732 on 2010-08-27
try popping in the cd again and then type in the terminal:
sudo apt-get purge grub
then
sudo apt-get install grub
it should work then :/

---

### Post by coffeecat on 2010-08-27
> **29732 said:**
> try popping in the cd again and then type in the terminal:
sudo apt-get purge grub
then
sudo apt-get install grub
it should work then :/

Will that work?. The OP is using the alternate CD, and I don't remember being able to get to a terminal in the alternate CD. Also - if you purge and install grub in the live CD session, you merely purge and install grub in the live OS, not on the HD. **Edit:** And 'grub' is the package for legacy grub. The OP is using 10.04-1 which would have grub2.

@ketisfolk, since the live desktop CD won't work for you, we need to get you booted into your hard drive Ubuntu to repair grub. Have a look here, Supergrubdisk2:

[http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/)

Download that, burn it to CD, boot with it and see if you can boot into Ubuntu with it.

Once in Ubuntu, open a terminal and:

```
sudo grub-install /dev/sda
sudo update-grub
```If you get an error that suggests the grub packages are not installed, make sure you are connected to the internet and do:

```
sudo apt-get install grub-pc
```Then follow that with the two commands as above.

---

### Post by ketisfolk on 2010-08-27
@Coffeecat

I've done what you've suggested but it's not helped. It can sense that there is a linux system installed, and that the GRUB is there (I did the 1st and 2nd options), which makes me think  the GRUB is actually fairly properly installed now. It runs through a pile of code and then there seems to be another issue causing me to keep getting the same message, **[COLOR=Black]"mmc0: unknown controller version (16). You may experience problems.",[/COLOR]** preceded by a number which is always different. Then there is a blinking cursor and I cannot input anything through the keyboard, and the only way to turn the laptop off is to pull the power cord.

---

### Post by jtarin on 2010-08-27
try removing your SD card if you have one, the proceed.

---

### Post by ketisfolk on 2010-08-27
There is absolutely no SD card in the slot, and there hasn't been throughout all of this.

---

### Post by jtarin on 2010-08-27
> **ketisfolk said:**
> There is absolutely no SD card in the slot, and there hasn't been throughout all of this.
There is documentation about this error all over google and the only fix I have come across is a reinstallation. If you can boot from the CD/DVD you might open a terminal and give us the output of ```
dmesg
```

---

### Post by coffeecat on 2010-08-28
I'd like to go back to this:

> **ketisfolk said:**
>  The desktop version I downloaded and burnt to cd didn't work

How exactly didn't it work? Would it not boot into the live desktop? Did you check the md5sum of the downloaded ISO? Did you check the integrity of the burnt CD? Have a look here:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

The reason I ask it that it is much easier to troubleshoot problems with the live desktop CD, rather than the alternate CD that you are using. I'm hoping that the live CD you used was a bad burn and that if you try again you may be successful.

---

### Post by ketisfolk on 2010-08-28
The MD5SUM is fine, it's the same anyway. When I ran it before it said it couldn't mount, or something to that effect. I have however, discovered this, which is to do with the type of laptop I have: [http://ubuntuforums.org/showthread.php?t=1316848&highlight=freevents](http://ubuntuforums.org/showthread.php?t=1316848&highlight=freevents). I don't understand at all what it involves but if it needed me to do something while still running xp then it's not going to happen, I just can't recover it, and I'm really trying to, but the disc I have when running the setup says it can't find any hard disk drives :confused:. The unbuntu has now installed the GRUB loader, but it is still making complaints about the unknown controller version (16). Beginning to think I'm going to have find someone with a lot more technical expertise than me to try and restore it to some original point. Turns out that the laptop still has a service agreement until late October, so might be able to get it fixed for free if it comes to that.

---

### Post by 29732 on 2010-08-28
maybe the disk was corrupted, try burning it again and then tell us what happens (that also means downloading it again)

---

### Post by ketisfolk on 2010-08-28
I have now managed to install ubuntu within windows on my sony vaio PC, and it's working fine (except it won't recognise my wireless mouse and there is no way of installing a normal one, no socket for it), with the first disk of 10.04 desktop that I burnt all that time ago, which suggests that disk is fine. However, put it into the laptop, and after a while of the inital ubuntu purple loading screen and the dots lighting up it freezes, with nothing to do but pull the power. I think the laptop is being severely difficult now so I think there will soon be a trip for me, the laptop and my service agreement to PC World, the joys, unless anyone has any other suggestions. I'm taking them all seriously.

---

### Post by 29732 on 2010-08-28
ill have a suggestion in a min soon

---

### Post by ketisfolk on 2010-08-28
OK, that would be great if you do, however I'm beginning to think I was on a hiding to nothing from the start, given my research around the webs, it seems these philips laptops often have bug problems with ubuntu.

---

### Post by 29732 on 2010-08-28
ok quick question: what sony vaio do you have? the modeel will be fine

---

### Post by ketisfolk on 2010-08-28
Sony Vaio VGC-LN1M

---

### Post by 29732 on 2010-08-28
mmk ill look at it gimme a moment

---

### Post by 29732 on 2010-08-28
ok from what i se on the desktop, it should work for ubuntu i still am thinking that the disk is somehow interrupted, and wubi is the only way that ubuntu works since i dont think it really needs grub :/

---

### Post by Zirts on 2010-08-28
Had a similar problem too when I first installed Ubuntu on my computer. I got it fixed by just downloading a new .ISO and then instead of burning it on a CD I decided to put it on a 2GB USB stick, worked like wonder.

---

### Post by 29732 on 2010-08-28
> **Zirts said:**
> Had a similar problem too when I first installed Ubuntu on my computer. I got it fixed by just downloading a new .ISO and then instead of burning it on a CD I decided to put it on a 2GB USB stick, worked like wonder.
yeah, i kept thinking that

---

### Post by 29732 on 2010-08-28
burning OSs is serious business, burn it at the slowest speed so it will have a better chance of not screwing up

---

### Post by ketisfolk on 2010-08-28
I have now used a slow burnt (4x) iso disk and a usb installer, and they work fine except that I cannot move the cursor at all, which is kind of crucial. I'm on the verge of giving up here.

---

### Post by oldfred on 2010-08-28
If mouse & keyboard do not work it often is a setting in BIOS. Not sure if it applies to portables since they are internally wired. But see if your BIOS has a USB mouse & keyboard setting.

---

### Post by coffeecat on 2010-08-28
@ketisfolk, from that link you posted, it does seen to be a BIOS issue in your laptop. Some BIOS's seem to be simply hostile to Linux. Probably due to bugs in the BIOS. If it works with Windows, then the manufacturers are not interested in any further bug-hunting.

Not that that helps you much, but here's something which might just do the trick:

[https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)

Try those options under the heading "What parameters to use?" It tells you how to apply them.

---

### Post by ketisfolk on 2010-08-28
Thanks coffeecat but the laptop isn't even giving me that first screen of options any more when I put the disk in, and I know the disk is fine because it worked with my pc, asides from the cursor thing of course. I think laptop is well and truly.... I'll see if I can get it fixed, but does anyone know if it'll screw my service agreement if I tell them I was trying to install a new OS?

---

### Post by coffeecat on 2010-08-28
> **ketisfolk said:**
> I'll see if I can get it fixed, but does anyone know if it'll screw my service agreement if I tell them I was trying to install a new OS?

Be very careful. You mentioned PC World. There are some intelligent assistants in some branches and you might be lucky. But there have been some stories coming out, if I remember correctly, where PC World has argued that the warranty or service contract is invalidated by using Linux. They might even try to argue that installing Linux has caused the problem!

If you think there is a hardware issue, you might want to think about re-installing Windows from the recovery partition (if it exists) or your restore DVDs (if they exist) and putting the machine back to its factory condition so that they won't see the Linux partition(s). {**Edit:** or simply delete the Linux partitions with the Windows partitioning tool (you are using Vista or W7? That won't work with XP.) and re-expand the C: partition back to its original size.} But if you are trying to argue that the machine is faulty because it won't run Linux then I think you are on shaky ground. Caveat: I am not a lawyer! My understanding is that if you try to use something for what it was not intended, then consumer law won't support you. PC World would probably argue (correctly in a legal sense) that the laptop was not designed to run Ubuntu.

---

### Post by 29732 on 2010-08-28
> **coffeecat said:**
> Be very careful. You mentioned PC World. There are some intelligent assistants in some branches and you might be lucky. But there have been some stories coming out, if I remember correctly, where PC World has argued that the warranty or service contract is invalidated by using Linux. They might even try to argue that installing Linux has caused the problem!



that is why i unsubscribed to them, they are of no help

---

### Post by ketisfolk on 2010-08-28
Yeah, that's my suspicion about pc world, but I can't even recover windows xp, and I've tried. I got a boot loader thing, I found a windows xp cd that's actually my dad's, because I don't have one, I tried loading from another section, none of which worked. Had I realised before all this that this particular brand of laptop was so ubuntu unfriendly, I wouldn't have bothered probably. At least before it did something. Thinking of ways to get round this, cause if it is badly damaged enough in the right way, they should replace it.

---

### Post by coffeecat on 2010-08-28
Well - you may be lucky to get someone in PCWorld who is sympathetic. I've come across 2 Linux users among the staff of my local PC World! :shock:

I'm out of ideas, except:

Try some other distros. You might just find one that can cope with that laptop's BIOS. Opensuse, Fedora, Mandriva, PCLinuxOS and Mepis all do live CDs so at least you can try out the desktop CD before committing yourself. Don't bother with Mint, an excellent distro but too heavily based on Ubuntu.

---

### Post by 29732 on 2010-08-28
sdkjlflkjashdlfkj;hsadkjl
i cant think of anything
maybe he can try linux mint? i mean it just might work

---

