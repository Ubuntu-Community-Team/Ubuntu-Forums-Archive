---
title: "Separate /home partition help with command"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by funky_uncle on 2009-02-04
I was following the instructions on [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) to the dot, and everything goes fine until I copy and paste the command ```
sudo cp /old/etc/fstab /old/etc/fstab_backup
```
which only gives me ```
cp: cannot stat `/old/etc/fstab': No such file or directory
```

Again, I did *everything exactly* as described on the tutorial, and didn't get *any* error messages until this one.

I guess I could fix it myself if I had any idea what the commands mean, but I don't :/

---

### Post by funky_uncle on 2009-02-04
I was following the instructions on [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) to the dot, and everything goes fine until I copy and paste the command ```
sudo cp /old/etc/fstab /old/etc/fstab_backup
```
which only gives me ```
cp: cannot stat `/old/etc/fstab': No such file or directory
```

Again, I did *everything exactly* as described on the tutorial, and didn't get *any* error messages until this one.

I guess I could fix it myself if I had any idea what the commands mean, but I don't :/

---

### Post by Thelasko on 2009-02-04
> **funky_uncle said:**
> I was following the instructions on [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) to the dot, and everything goes fine until I copy and paste the command ```
sudo cp /old/etc/fstab /old/etc/fstab_backup
```
which only gives me ```
cp: cannot stat `/old/etc/fstab': No such file or directory
```

Again, I did *everything exactly* as described on the tutorial, and didn't get *any* error messages until this one.

I guess I could fix it myself if I had any idea what the commands mean, but I don't :/

"cp" is copy.  It looks like you are trying to copy a file from one directory to another, but the original file doesn't exist, or is in a different location.

For help with commands, [try reading this]("http://en.wikibooks.org/wiki/Guide_to_Unix/Commands/File_System_Utilities#cp").

I recommend printing those guides out in case something goes wrong.

---

### Post by handydan918 on 2009-02-04
Well, do you HAVE a file named /old/etc/fstab?

Most people don't...

---

### Post by funky_uncle on 2009-02-04
I do have an /old directory, but it doesn't contain any /etc.

Here are all the commands I copied and pasted from [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) :

```
sudo mkdir /old
sudo mount -t ext3 /dev/sda1 /old
sudo mkdir /new
sudo mount -t ext3 /dev/sda3 /new

cd /old/home
find . -depth -print0 | cpio --null --sparse -pvd /new/
sudo mv /old/home /old/home_backup
sudo mkdir /old/home
```

---

### Post by handydan918 on 2009-02-04
My point being that copying and pasting commands that name fiels that don't exist on your system is not gonna work, no matter how much we talk about it.
Better if you figure out what files you need to copy, and use the tutorial to give you guidance on the general syntax used with cp, or whatever commands you end up using...

---

### Post by avtolle on 2009-02-04
> **handydan918 said:**
> My point being that copying and pasting commands that name fiels that don't exist on your system is not gonna work, no matter how much we talk about it.
Better if you figure out what files you need to copy, and use the tutorial to give you guidance on the general syntax used with cp, or whatever commands you end up using...
Be sure that your partitions are correctly identified. The psychocats tutorial makes assumptions as to the location of the existing install, which is shown in italics in the example.

---

### Post by funky_uncle on 2009-02-04
> **handydan918 said:**
> My point being that copying and pasting commands that name fiels that don't exist on your system is not gonna work, no matter how much we talk about it.Of course, I just need to know where the problem lies, i.e. is the guide faulty?

Anyway, I find an /etc folder on the root (not under /old) so I edited the commands accordingly (*sudo cp /etc/fstab /old/etc/fstab_backup* instead of *sudo cp /old/etc/fstab /old/etc/fstab_backup*) and I'm not getting any error message this time. I've also edited the fstab file like the tutorial says. I'll try to reboot now and see if it works.

---

### Post by avtolle on 2009-02-04
I've used that guide three times to create a separate home partition, and there's nothing that I know of that is wrong with the guide. Good luck with your progress, and let us know what happens.

---

### Post by nothingspecial on 2009-02-04
> **funky_uncle said:**
> I was following the instructions on [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) to the dot, and everything goes fine until I copy and paste the command ```
sudo cp /old/etc/fstab /old/etc/fstab_backup
```
which only gives me ```
cp: cannot stat `/old/etc/fstab': No such file or directory
```/

Again, I did *everything exactly* as described on the tutorial, and didn't get *any* error messages until this one.

I guess I could fix it myself if I had any idea what the commands mean, but I don't :/

Do you have a directory named /old/etc/fstab?

---

### Post by avtolle on 2009-02-04
I've a feeling that the OP's system is mounted on a partition other than /dev/sda1, and thus his copy/paste of the commands didn't do what was expected. Although, in reviewing the commands, his ```
mkdir /old/home
```appears "out of order".

---

### Post by ugm6hr on 2009-02-04
You did boot from the LiveCD before starting, didn't you?

---

### Post by funky_uncle on 2009-02-04
> **avtolle said:**
> I've used that guide three times to create a separate home partition, and there's nothing that I know of that is wrong with the guide. Good luck with your progress, and let us know what happens.I just restarted, I now find both partitions listed in Nautilus.

sda1 has the directories /home (empty), /lost+found, and /home_backup/funky (which contains all my music etc (the stuff I'm trying to save)).

sda3 has lost+found and /funky

I guess I should proceed with the tutorial and run ```
sudo rm -rf /home_backup
```

Or should I try to install Ubuntu right away?

(I know I'm probably not making much sense here.)

---

### Post by funky_uncle on 2009-02-04
> **ugm6hr said:**
> You did boot from the LiveCD before starting, didn't you?Yes, I can't boot from the HD anyway, Mint is broken.

---

### Post by avtolle on 2009-02-04
Unless you have a typo, you don't have a new /home on /dev/sda3; you do have /funky. You might want to look in /funky to be sure all your stuff is there before moving on, just in case. I presume that if it is there, you will do a new install of Mint or whatever on /dev/sda1, and change the mount point of /funky in /dev/sda3 to /home.

---

### Post by funky_uncle on 2009-02-04
> **avtolle said:**
> Unless you have a typo, you don't have a new /home on /dev/sda3; you do have /funky.Correct. I don't know why /funky stands by itself and not under /home though. Anyway, all the files are there :)

> **avtolle said:**
> I presume that if it is there, you will do a new install of Mint or whatever on /dev/sda1, and change the mount point of /funky in /dev/sda3 to /home.Would be so kind as to tell me how to do that?

---

### Post by avtolle on 2009-02-04
During the installation, when you arrive at the partitioning stage, select manual partitioning. On /dev/sda1, mark it for formatting, with a mount point of /. On /dev/sda3, select mount point /home (do not format) and for /dev/sda2, be sure it has a mount point of /swap. Then proceed with the installation. Hope this helps, and good luck.

---

### Post by funky_uncle on 2009-02-04
Didn't work. Did a clean install. But thanks for the help anyway.

---

### Post by Thelasko on 2009-02-05
> **funky_uncle said:**
> Yes, I can't boot from the HD anyway, Mint is broken.

Wait... you're doing this on Mint?

---

### Post by funky_uncle on 2009-02-05
> **Thelasko said:**
> Wait... you're doing this on Mint?I used to run Mint, it crashed to the point where I couldn't get anything but a blank screen. Since then I've been doing everything from an Ubuntu Live CD.

---

### Post by Thelasko on 2009-02-05
> **funky_uncle said:**
> I used to run Mint, it crashed to the point where I couldn't get anything but a blank screen. Since then I've been doing everything from an Ubuntu Live CD.

So, you're trying to move your home folder from your Mint install to it's own partition, so you can install Ubuntu/reinstall Mint?

I don't know that much about Mint, but it may be the reason you are having trouble.  It should still be doable, but I don't know if the commands will be exactly the same.

I think you need help from someone that knows more about Mint.

---

### Post by funky_uncle on 2009-02-05
> **Thelasko said:**
> So, you're trying to move your home folder from your Mint install to it's own partition, so you can install Ubuntu/reinstall Mint?Yeah, that was the plan. Didn't succeed, but it looks like it's definitely doable. Anyway, I've installed Ubuntu 8.10 now and it looks very good :)

And as a bonus, I managed to make a separate /home partition, so it'll be easier to (re)install different distros later if I want to.

---

### Post by Thelasko on 2009-02-06
> **funky_uncle said:**
> Yeah, that was the plan. Didn't succeed, but it looks like it's definitely doable. Anyway, I've installed Ubuntu 8.10 now and it looks very good :)

And as a bonus, I managed to make a separate /home partition, so it'll be easier to (re)install different distros later if I want to.

Well, I hope you were at least able to save your documents, etc.

---

