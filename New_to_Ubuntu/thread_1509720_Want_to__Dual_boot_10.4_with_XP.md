---
title: "Want to  Dual boot 10.4 with XP"
date: 2010-06-14
forum: New to Ubuntu
---

### Post by Sandy.1 on 2010-06-14
I have a cd with Ubuntu 10.4 in my lap top which is already loaded with XP.

I have Got to the Ubuntu welcome page and selected language and am continuing with 'Install Ubuntu 10.4 LTS'

I have the 'Where are you?' page and have selected Belgium. Time is 2 hours out but I shall worry about that later.

Forward to Step 3 of 7 and select UK keyboard.   - International (with ????) and check that the @ is where I expect it to be

Forward to Step 4 of 7

_**Prepare Disk Space**_ 

I am told that my computer has several operating systems ???

And I have XP Home (/dev/sda1) with 73.8GB and another 6.3 GB partition for NT or 2000 or XP

Where do I want to put Ubuntu 10.4 LTS. Erase and use the entire disk is suggested but **NO** I don't want to do that.

The object is to have Ubuntu and XP dual booting.

So I appear to be invited to specify partitions manually.

[COLOR=Red]This is starting to look less than easy but let's go forward.[COLOR=Black]

Forward to Step 5 and Step % still appears to have the option of backing out of all this procedure so let's go on.

So I fill in name and password and a name for the computer and move on to Step 7 of 7


[COLOR=Red]And this is where the problem starts.

I am told that if I continue all data on partitions that are going to be formatted are going to be destroyed.


[COLOR=Black]No mention of arranging partitions for dual booting so let's back out of here.



So is there a way of safely loading Ubunti 10.04 LTS onto a laptop which is already loaded with XP?
[/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by mapes12 on 2010-06-14
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by spiky001 on 2010-06-14
ok it would be best to load the live cd option without change to pc then use Gparted which is on cd to shrink xp patition to the size you want, then make a new partition for Ubuntu

---

### Post by gunfyter on 2010-06-14
Check out these two sites


[http://wubi-installer.org/](http://wubi-installer.org/)

[Dual-boot with Windows]("http://www.psychocats.net/ubuntu/wubi")

---

### Post by SaintDanBert on 2010-06-14
Ubuntu Lucid (v10.04) uses "grub-2" that does almost everything in a new and different way.  There is a known problem where on reboot during the install, you do not see your "other OS" options.  To fix your situation, all you need to do is ...

... run the grub-2 commands using sudo to force it to rethink all of the boot options.  Search for "lucid" "10.4" "grub" "grub-2" and "dual boot" and I'm sure you will find detailed instructions.  I wish I could spout the syntax for you, but I don't remember the details.

I think the command you need is this:
```

user@host:/path/ $ sudo update-grub

```

I found these links:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1371717](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1371717)
[http://ubuntulinuxhowtos.blogspot.com/2010/01/how-to-reinstall-grub-2-after.html](http://ubuntulinuxhowtos.blogspot.com/2010/01/how-to-reinstall-grub-2-after.html)

~~~ 0;-Dan

---

### Post by nysnsweet on 2011-06-24
> **spiky001 said:**
> ok it would be best to load the live cd option without change to pc then use Gparted which is on cd to shrink xp patition to the size you want, then make a new partition for Ubuntu

I'm having the same problem as the original poster.

I would really like to know more about how to do this.  How do you make the new partition for Ubuntu and what do you to continue installation?

Thanks

---

### Post by oldfred on 2011-06-24
@nysnsweet

Please start your own thread with details on where you are at. This is an older thread. 

Did you follow any of the links posted. Herman's site in post #2 is very detailed with screenshots to walk you thru the process. several of the others also are helpful.

---

