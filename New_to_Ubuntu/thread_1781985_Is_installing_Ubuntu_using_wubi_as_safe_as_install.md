---
title: "Is installing Ubuntu using wubi as safe as installing ubuntu on dedicated partition ?"
date: 2011-06-14
forum: New to Ubuntu
---

### Post by scrypt on 2011-06-14
Hello

I have questions about what is the safest way to install ubuntu.
Is it safer to install Ubuntu using the Dual Boot method ?
Or is it equally as safe to install ubuntu using the windows installer (wubi) Or does installing ubuntu using wubi. Offer less security than dual booting ubuntu on its own dedicated partition.

I have wondered this for some time.

I look forward to any replies.

Thnak-you

---

### Post by grahammechanical on 2011-06-14
How safe is your Windows installation?

This is my understanding. Wubi installs and runs Ubuntu inside Windows. The purpose of Wubi is to allow the Windows user to test Ubuntu without making physical changes (partitions) to the hard disc. It is not meant as a way of permanently using Ubuntu but as an easy in and an easy out option.

You ask what is the safest way to install? Then you speak of less security. This is two different issues. A dedicated Ubuntu installation in its own partition will always be more secure than using Ubuntu inside Windows. This is why I ask How safe is your Windows installation?

Regards.

P.S. I do not think that a Wubi install will wipe out your Windows OS but choose the wrong option when attempting a dual boot installation and the Windows OS will be deleted. This has happened to some. A person needs to know what they are doing.

---

### Post by TBABill on 2011-06-14
Your wording of "safest" is a bit confusing so I am going to answer on the assumption that by "safest" you mean "least possibility to harm the Windows partition".
 
Wubi is safer because it just puts Ubuntu onto a virtual partition, but you're not really using Ubuntu within its native environment so I cannot say your performance will reflect the same or not.
 
Putting Ubuntu on its own partition is relatively easy, but you will want to be sure YOU know what partition(s) Windows resides on. Keep in mind there are backup partitions for Windows as well so you need to know all of them. It's often recommended to defrag Windows and then use a Windows utility to shrink the Windows partition, then install Ubuntu. I have actually used the "Install Ubuntu side by side" feature before and things went perfectly, but they have also gone south on other installs. 
 
Don't risk your data. Backup whatever you need to keep onto USB or external HDD, then run what you feel is best. Personally I'd shrink my Win partition and leave empty space on the drive, then use the partition feature on the LiveCD of Ubuntu (gparted) to assign that space to a new partition and aim your install of Ubuntu there. Lots of options you can choose to get and use Ubuntu.

---

### Post by Mark Phelps on 2011-06-14
When folks ask about "safe" in PC terms, they usually mean safe from viruses or other malware.

Since Ubuntu is a Linux distro, whether you install it using Wubi (note: it does NOT run "inside Windows") or to a separate partition makes no difference from a malware perspective -- it's the same OS.

---

### Post by scrypt on 2011-06-25
hello

thanks all for your replies
all had helpful valid points that answered my question.

---

