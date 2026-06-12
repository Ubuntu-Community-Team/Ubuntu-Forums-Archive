---
title: "windows defrag. before installing Natty"
date: 2011-08-16
forum: New to Ubuntu
---

### Post by r2d211 on 2011-08-16
Please, a quick question: I've read somewhere here but can't remember where about modifying the virtual memory or paging in win XP before defragmentation and later bring it back. How should I do this?

---

### Post by skatinjj on 2011-08-16
"You may need to turn off the Windows swap file first (as this is normally at the end of the Windows partition. This can be found (for XP) under Settings-Control Panel-System-Advanced tab-Performance Settings button-Advanced tab. Change the Virtual Memory paging file to 'No Paging file'. Save this and reboot to make sure the settings are used. Next defrag the hard disk in Windows.
After you've resized Windows with Gparted, it may be worth booting Windows immediately afterwards, as it may complain and allow chkdsk to run to check the Windows partition integrity."

This was from:

[http://ubuntuforums.org/archive/index.php/t-1425497.html]("http://ubuntuforums.org/archive/index.php/t-1425497.html")

---

### Post by r2d211 on 2011-08-16
Oh, great! Thank you! And where should I find the Gparted?

---

### Post by corncob on 2011-08-16
> **r2d211 said:**
> Oh, great! Thank you! And where should I find the Gparted?

That info is in the 2nd post of the link skatinjj gave you.  I think though, somebody correct me if I'm wrong, that it will give you the opportunity to resize the partitions before it starts installation.  If not,
[HTML]sudo apt-get install gparted[/HTML]
typed into the terminal (ctrl-alt-t) after installation will install GParted.

---

### Post by r2d211 on 2011-08-16
Oh, I have to tell you that I don't have internet connection in Ubuntu. I use a Blackberry device for tethering in windows, but this is not possible in linux yet. So maybe give me a link to the packages to download them in windows.

---

### Post by r2d211 on 2011-08-16
Silly me, the link was provided above, sorry. I will try now to download the live Geparted cd. Is that okay?

---

### Post by corncob on 2011-08-17
> **r2d211 said:**
> Silly me, the link was provided above, sorry. I will try now to download the live Geparted cd. Is that okay?

I've been assuming that you have the Ubuntu install CD.  Why don't you use the GParted on that?  Actually, like I already said, I believe, on a simple duel boot install, it will suggest partition sizes and allow you to change them by simply dragging the line between them on the display.  Give it a try.  It will warn you when it is ready to write to the disk and you can abort the install any time before that.

---

### Post by r2d211 on 2011-08-17
So you suggest to simply use the ubuntu install cd which allows you to manage the partition space as you like. Well, that's why I started this thread because I've read that by simply using the live natty cd you may end up deleting some files on the windows partition and this is why I was trying now to download the Gparted cd. Anyway, the connection was so bad that I gave up for today. Okay, so I'll just use the natty cd. Is that correct?

---

### Post by Jesse Tustin on 2011-08-17
Sorry if this has been said before, it's defrag.exe

---

### Post by CatKiller on 2011-08-17
GParted is on the Ubuntu cd if you want to set up your partitions before you start the install process.

---

### Post by corncob on 2011-08-17
> **r2d211 said:**
> So you suggest to simply use the ubuntu install cd which allows you to manage the partition space as you like. Well, that's why I started this thread because I've read that by simply using the live natty cd you may end up deleting some files on the windows partition and this is why I was trying now to download the Gparted cd. Anyway, the connection was so bad that I gave up for today. Okay, so I'll just use the natty cd. Is that correct?

Yes, I'd just start the installation and let Ubuntu do the work.  If something seems odd or confusing you can abort the installation and go back to square one any time before it tells you its going to write to the disk.  If all you have on the drive now is WinXP it should be straight forward. You are planning a duel boot installation, not wubi?

---

### Post by r2d211 on 2011-08-17
Finally I decided to use Wubi being in the process of learning and trying out natty. So I just used wubi and let it manage the space by itself. My only BIG problem is now tethering my Blackberry in order to have internet access but I guess this is just another thread, isn't it?

---

### Post by r2d211 on 2011-08-17
CatKiller, thank you, I wasn't aware of Gparted being on ubuntu cd. Anyway I think I will use it when I'll finally decide for a dual boot. For now I'm trying wubi just to see how things work.

---

### Post by pi.boy.travis on 2011-08-17
The partition the installer uses is capable of intelligently rearranging blocks on the Windows partition such that no data will be lost, while it may be a good precautionary measure, it is not necessary to defragment your Windows partition before doing a dual-boot install.

---

### Post by akand074 on 2011-08-17
> **pi.boy.travis said:**
> The partition the installer uses is capable of intelligently rearranging blocks on the Windows partition such that no data will be lost, while it may be a good precautionary measure, it is not necessary to defragment your Windows partition before doing a dual-boot install.

This. I haven't defragged since Windows XP year back. And that's only because I thought it would make my super slow computer run faster. I've installed Ubuntu along side Windows probably over a dozen times without doing anything before hand and never had an issue.

---

### Post by r2d211 on 2011-08-18
Bad news! Reading some tutorials about installing Ubuntu, I saw that many recommend disabling the virtual memory before defragmentation.  I did it but now I lost my note about the amount. Any suggestion on how to revert it?

---

### Post by corncob on 2011-08-19
I too have never bothered defragmenting windows before installing Ubuntu let alone disabling virtual memory.  But then I don't care much about windows -- I just keep it because I was forced to pay for it.

---

### Post by pi.boy.travis on 2011-08-19
You don't need to defragment or disable virtual memory. UNIX style partitioners used to be unfriendly when resizing FAT32 and NTFS partitions, but here in 2011 the software is more than advanced enough to correctly resize your Windows partition.

---

### Post by r2d211 on 2011-08-21
Okay guys, I think I've got an idea about the issue, so marking the thread as solved. Thank you!

---

