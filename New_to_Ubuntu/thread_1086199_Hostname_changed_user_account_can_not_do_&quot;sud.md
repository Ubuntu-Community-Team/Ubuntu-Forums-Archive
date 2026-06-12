---
title: "Hostname changed user account can not do &quot;sudo&quot; or no admin rights."
date: 2009-03-03
forum: New to Ubuntu
---

### Post by bullzeyes on 2009-03-03
Dear expert, my ubuntu was working perfectly for months. As a curious person, i try to changed the hostname of my ubuntu. It works fine. But few days later, i realize that my account can not do "sudo" or install software. No admin rights to do anything. Luckily, i am able to use it now to post at this forum. When i use sudo, it give out "bullz is not in the sudoers file.  This incident will be reported." Does anyone have the default password for root? I never changed the password of the root since i dont need it. Previous version of ubuntu i have no problem changing hostname and my account still work normally.  can anyone help me please. I use this machine for work and try to spread and encourage all my friends to use ubuntu. Thanks

regard,
bullz

---

### Post by stoogiebuncho on 2009-03-03
Found this on a related thread:
> Start your ubuntu in recovery mode. In this way you will be logged in as root, without the need to type a password. If the recovery mode is not available, use a live distribution, mount the root partition and manually add the user you want in /etc/group in the line for the admin group, like this
Code:

```

admin:x:106:youruser,anotheruserifyouneedanother,whynot,etc

```

Note: the number 106 can be different on your computer.

Good Luck !

Here's the thread if you want to check it out yourself: [http://ubuntuforums.org/showthread.php?t=162867]("http://ubuntuforums.org/showthread.php?t=162867")

---

### Post by bullzeyes on 2009-03-03
> **stoogiebuncho said:**
> Found this on a related thread:


Here's the thread if you want to check it out yourself: [http://ubuntuforums.org/showthread.php?t=162867]("http://ubuntuforums.org/showthread.php?t=162867")

Thanks. I love ubuntu. When problem arise, i learn things from fixing it. Minutes ago, i research and found info on sudoers and i add in my account to the list and now works. I dont know is that the correct way (security risk) but sudo command works now. I will check the thread that you post. Thank you for posting and thank you ubuntu for the great Distro. I will keep promoting ubuntu for others to use it, even install for them for free.
cheers!

---

### Post by asmoore82 on 2009-03-03
boot any liveCD, an Ubuntu install disk will work great, - there you will have root access -
mount your hard drive and make the settings in these files "gel" with each other:
/etc/hostname, /etc/hosts, /home/<your_user_name>/.gnome2/network-admin-locations/<all_net_profiles_in_here>

Remember that the locations of all these files will be relative to where you mount your hard disk:
For example, if it is mounted as **/media/disk**, /etc/hostname becomes **/media/disk**/etc/hostname

---

