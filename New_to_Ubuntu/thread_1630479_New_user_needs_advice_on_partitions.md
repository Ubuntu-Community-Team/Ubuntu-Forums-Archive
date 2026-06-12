---
title: "New user needs advice on partitions"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by solor on 2010-11-25
I'm absolutly new to the open source OS world and need some help with my first ever Ubuntu install. Firstly I have searched for answers to my questions but have not found any direct/helpful ones. So I'm hoping someone will give me some plain english help. Thanks in advance.

I'm running Windows XP SP3 on a Sony Vaio laptop, 2GHz processor, 2GB RAM. I'd like to set up a dual boot with Ubuntu 10.10. I need help working out what size partitions I need to make. My current set up is:

15GB partition (Windows OS)
15GB partition (blank, waiting for new Ubuntu OS)
60GB partition (personal work space)

Questions:
1 - Do I need any other partitions? I've read something about need more for something called "/" or "/home"? What are these?
2 - I've read that I might need a partition for something called Swap. What is that? Why do I need it?
3 - Do I need more then 15GB for Ubuntu?
4 - What disk format does the empty partition need to be for Ubuntu?
5 - How does dual booting actually work? Once I have both OSs in place how does the computer know which to boot on start up?

Sorry for the very newbie questions but I've never done this before.

Thanks.

---

### Post by aeiah on 2010-11-25
1. "/" is your root partition, where the OS goes. /home is your home folder. this can be a partition of its own or it can just be a folder in the root partition

2. the swap partition is useful for a couple of things. you've probably got enough ram not to ever use it as a ram substitute, but it may still be useful to have one. having a swap partition will enable you to hibernate your laptop. the swap partition will have to be at least as large as your RAM for this to work properly. just make it 2.1GB or something.

3. probably not, since you'll be storing your personal files in a shared partition

4. ext4, but it will be formatted at install time for you anyway

5. the ubuntu install will replace the windows boot manager with grub2. grub2 will add your windows operating system as a boot option. by default it'll boot into ubuntu but you can change this if you wish. it'll give you a 10 second window of opportunity at boot to select your operating system before it just loads your default (again, 10 seconds can be changed.. hell, this is linux, everything can be changed).

edit: oh, by the way... make sure you don't accidentally install ubuntu to your 15GB windows partition. with them both being the same size you should make sure you aren't wiping the wrong one. you should be able to tell which partition is windows because it'll be NTFS. your personal storage will be NTFS too of course, but this is 60GB.

---

### Post by Hippytaff on 2010-11-25
Also I would add that it is probably worth having a seperate /home partition so that if you upgrade 10.10 in the future or if anything goes wrong, your setting and any files you have there will not be lost :-)

---

### Post by sanderd17 on 2010-11-25
[LIST]
[*]if your 15 GB for ubuntu is left "unallocated", when you try to install ubuntu, it will be the default to install it there. So don't partition it, or you will have to choose your partition (and maybe make the wrong choice)

[*]for the dual boot: the mbr, that is the part of your HDD where the first command is, is currently pointing to windows. When you install ubuntu, the mbr will be pointing to a program called "grub", in grub, you can choose to load windows or ubuntu. But since grub is on the ubuntu partition, if you plan to remove ubuntu, grub will be removed and the mbr will find nothing.

Off coarse the mbr this can be fixed to point to windows and you won't lose data, it's just that you know.

[*]The partition size:
I used to have 2 linux installs, both on a partition of 30 GB and a home with the rest of my space. But since I noticed that ubuntu never got over 10 GB and my home was getting full, I changed them to 15 GB. So yes, 15 GB is enough

[*]about your data partition:

your data will come in the 60GB partition? well, that's good but the formatting gives some problems. 

If you use your 60GB as /home (so all document go in there by default), it has to be formatted as ext3 or ext4. And windows can't read ext3 or ext4. So you will have to install something in windows to read it. I know this is possible, but I don't know how stable it is because I never used it.

If you don't use your 60GB partition as /home, I know out experience that a lot of data will end up in your /home folder on the 15GB ubuntu partition. So that ubuntu will get full after a while. 

An advantage of using the 60GB as home is that you can install new versions of ubuntu without problems, your data and settings will never be changed, even not with a complete reinstall.

[*] swap is needed as adition to your RAM and to hibernate. If you choose not to make a swap partition, you won't be able to hibernate. The default installing will make a swap partition.
[/LIST]

Notes: if you hibernate windows and aftarwards you bootup ubuntu, change some things and start windows again, windows will start in the state like it was when you hibernated it. So it will restore the files to that point. So if you hibernate windows, you have to boot up in windows too.

The ubuntu native partitions need to be ext3 or ext4 because every files keeps aditional information: every file has an owner and the users have certain rights on the file (like read-write or execute rights), those rights are stored in the filesystem self. If you take another format as native partition (e.g. NTFS) Ubuntu will not be able to store the rights and the system will be more fragile.

---

### Post by solor on 2010-11-25
Thanks for the quick reply aeiah and Hippytaff. That helps clear up some points. I think I'll make up a new partition for /home. At what point do I make this partition? And how do I make it? Is it during the install that I can make it?

Thanks sanderd17. I think I'll partition that 60GB into two 30GB. One for Windows and one for Ubuntu. 

Another question: Is Ubuntu able to read and write to my external NTFS usb drives?

Thanks : )

---

### Post by solor on 2010-11-25
Deleted post.

---

### Post by sanderd17 on 2010-11-25
yes, ubuntu can read and write on about every partition format, it's just that ubuntu needs the features of ext3 and ext4 on its primary partitions.

---

### Post by solor on 2010-11-25
Thanks for all the help : )

---

