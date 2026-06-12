---
title: "Input/output error with samba share in Edgy Eft"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by mauripop on 2006-11-29
After migrating from another distro, I used the same syntax to mount my samba shares on fstab, so I added the following line to my fstab:

//winserver/MRE /mnt/mre smbfs ip=192.168.0.2,username=x,password=x,workgroup=RAE,uid=mre,gid=mre 0 0

I don't get any error messages but after boot any requests to /mnt/mre result in an Input/Output error after a looooooooooong delay. 

Now here is what is strangest (to me). I do a sudo umount /mnt/mre, which succeeds after another loooong wait (seems like a minute or more). Then I try a sudo mount -a which suceeds immediately. My /mnt/mre mount then works perfectly and speedily for all read and write operations. 

I am positive the syntax I use in fstab is OK, otherwise mount -a would return me some error, right? I have read and reread the samba guide on this ubuntu forums and I can't find anything wrong with what I am doing. So why doesn't the smbfs mount work after boot, but only after I unmount and do a mount -a ????

---

### Post by mauripop on 2006-11-30
I resolved this problem by skipping fstab and finding an alternate solution. I put the necessary mount commands in a script and made it run at boot by following [these]("http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/") instructions. 

Now the script runs at boot and all my window shares mount and work flawlessly. 

I still can't explain why a script works but the corresponding mount commands in fstab don't.

---

### Post by sweiss on 2007-04-04
Hello.
I just wanted to say that I am running Ubuntu Feisty, fully updated, and the issue is still present.

I have 2 samba mount points, one of each occasionally ends up with an "Input/Output error" when accessed. The other share I'm having, however, has never suffered such issues.

If anyone has any new insights on this, I'd be very much interested in hearing them.

Thank you.

---

### Post by SlayerMan on 2007-04-04
Did you already file a bug on launchpad about this?

---

### Post by sweiss on 2007-04-05
I've just checked launchpad, it seems that a similar bug has already been reported, though is unconfirmed.

I've commented on that bug, hope it helps.

---

### Post by jdmpike on 2007-04-10
I can also confirm that this problem still occurs in Feisty.

I have tried to remove the mount point, but I sudo can't even do that! I get scared when this sort of thing happens...

I believe it relates to how I have the line in /etc/fstab set up...

What do you guys think? 

```

//luckyseven/garage1 /media/garage1 smbfs credentials=/etc/samba/user,rw,uid=jordan 0 2

```

Obviously, the /etc/samba/user does contain the correct credentials.

Thanks,

jdmpike

---

### Post by R%&amp;92GH&amp; on 2007-04-11
Exactly the same problem.

I'll try to use the script method

thnx

---

