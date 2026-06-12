---
title: "dual boot no longer works after reinstall xp"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by spiepie on 2009-03-30
Hi
AAAAHHH:( had a dual boot system set up and ok except that XP had probs so installed XP again
now i cant boot into Ubuntu is there anyway to remedy this except for reinstall of ubuntu. I have personalised a lot in ubuntu so would like to try a method with less work.
yeh I know get rid of XP i can hear you yell but ...i need it for work

thanks for your time
Si

---

### Post by albandy on 2009-03-30
boot with the ubuntu alternate CD, in the menu select rescue system, then select a root session and do:
grub-install /dev/sda

---

### Post by leonardo_neo on 2009-03-30
> **spiepie said:**
> Hi
AAAAHHH:( had a dual boot system set up and ok except that XP had probs so installed XP again
now i cant boot into Ubuntu is there anyway to remedy this except for reinstall of ubuntu. I have personalised a lot in ubuntu so would like to try a method with less work.
yeh I know get rid of XP i can hear you yell but ...i need it for work

thanks for your time
Si

The MBR must be in Xp partition. So when you formatted the Xp partition, it erases the GRUB as well. Be careful when doing something like this.

Try to install grub again as mentioned above, and redirect your Linux partition in GRUB list.

---

### Post by James_Lochhead on 2009-03-30
Try [this.]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

Takes about 5 minutes to restore the boot loader. It is a common problem.

---

### Post by necronwarrior on 2009-03-30
"Recovering Ubuntu after windows install"-------> Google it!!!
You'll find the solution to your problem instantly!!!!!!
here's the link to the official ubuntu version of the repair---->
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
 
TIP: Always google your problem before posting it on the forums............most solutions are found instantly!!!!!!!!

---

### Post by spiepie on 2009-03-30
thanks 
is the ubuntu alternate CD the same as the install? as i dont remember the option rescue system option

---

### Post by kansasnoob on 2009-03-30
I'd boot the Ubuntu Live CD and go to terminal in the live session. Then type:

```
sudo grub
```

Which will drop you into "grub mode" like this:

> [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> 


Then type:

```
find /boot/grub/stage1
```

That will return something like "(hd0,0)" which in that case means hard drive #1, partition #1. Whatever that output is you'll want to use in the next step. Type:

```
root (hd0,0)
```

Of course you'll replace (hd0,0) with whatever the "find" command said (and btw those are zeros). Then type:

```
setup (hd0)
```

Which indicates hard drive #1. It's the first digit in (hd**0**,0), so if you're output was (hd1,0) you'd sub (hd1).

Then finally type:

```
quit
```

After rebooting you should have GRUB back!

---

### Post by leonardo_neo on 2009-03-30
> **spiepie said:**
> thanks 
is the ubuntu alternate CD the same as the install? as i dont remember the option rescue system option

No, its not the same.

Try James_lochhead's or Necrowarrior's fix first. That fix will work with your live CD.

---

### Post by spiepie on 2009-03-30
hi thanks guys
tried the fix
got into grub but option comes up with error 17 cannot mount selected partition
?
si

---

