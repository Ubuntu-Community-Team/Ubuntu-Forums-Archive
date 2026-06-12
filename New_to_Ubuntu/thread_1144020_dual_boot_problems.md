---
title: "dual boot problems"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by paulstenlund on 2009-04-30
Help!

Situation: 2pc's ---- home office PC dual boot XP & 8.10 Xubuntu.  Shop pc running Xbuntu 8.04 and EMC2.

I tried KDE, ubuntu etc on the office PC and then went back to Xubuntu 8.10. The other Gui's left a lot of stuff on the installation Kedit, Kterminal, etc. Plus I screwed up my tool bar and couldn't seem to fix it. So I thought I'd put the live EMC cd in and replace 8.10 with 8.04 which I like just as well. I started the install and when the partitioning screen came up it said "Replace 8.10 (Xgig) with 8.04 (Ygig) (not a direct quote but that was the jist of it)  exactly what I wanted to do. Started the install, went and watched some tube, returned and restarted, no more dual boot - goes right to 8.04..... it sure looked like it was just going to replae 8.10 and leave the XP partition alone.

How can I get the dual boot option back??? Please help there are some applications (CAD in particular) that I must have XP for

Thanks
Paul Stenlund

---

### Post by paulstenlund on 2009-04-30
Help!

Situation: 2pc's ---- home office PC dual boot XP & 8.10 Xubuntu.  Shop pc running Xbuntu 8.04 and EMC2.

I tried KDE, ubuntu etc on the office PC and then went back to Xubuntu 8.10. The other Gui's left a lot of stuff on the installation Kedit, Kterminal, etc. Plus I screwed up my tool bar and couldn't seem to fix it. So I thought I'd put the live EMC cd in and replace 8.10 with 8.04 which I like just as well. I started the install and when the partitioning screen came up it said "Replace 8.10 (Xgig) with 8.04 (Ygig) (not a direct quote but that was the jist of it)  exactly what I wanted to do. Started the install, went and watched some tube, returned and restarted, no more dual boot - goes right to 8.04..... it sure looked like it was just going to replae 8.10 and leave the XP partition alone.

How can I get the dual boot option back??? Please help there are some applications (CAD in particular) that I must have XP for

Thanks
Paul Stenlund

Sorry about the double post -- New guy will be more patient in future

---

### Post by Didius Falco on 2009-04-30
Hi Paul,

I haven't used the EMC2 live cd, so I'm unfamiliar with it. The first thing you need to do is check your partitions layout and see what is what.

Boot into the Live cd, open a Terminal shell and type in ```
sudo fdisk -l
```

and post the output here. What that finds is going to determine what you'll need to do next.

BTW, don't do anything else in 8.04 until you get this information. Stick with the live CD.

---

### Post by paulstenlund on 2009-04-30
Thank you Didius

I'm at work now, will do that tonight and get back to you tommorow

Thanks
Paul

---

### Post by NightwishFan on 2009-04-30
Inside Ubuntu, run this command and post the result.

```

sudo fdisk -l

```

This will tell us if you still have the Windows partition available. If you already know that it is still there, please skip that and just tell us.

If the partition is not there, it means you somehow deleted Windows.

---

### Post by caljohnsmith on 2009-04-30
I think it would help to first get a clearer picture of your setup to see what might have happened to your Windows partition, so how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

John

P.S. Please try not to start duplicate threads of the same subject/problem in the future--I've merged the two that you started. :)

---

### Post by paulstenlund on 2009-05-02
well guys the fdisk command tells me my NTFS partition is gone, I've been meaning to clean that up anyway. What Ive done is install another hard drive(2nd Drive) with xp on it, I've read that Grub will look and find other operating systems. Grub isn't seeing the new drive - dell setup sees it - linux can mount it. I see that you can edit grub but I don't know the commands to use. Please help
Paul

---

