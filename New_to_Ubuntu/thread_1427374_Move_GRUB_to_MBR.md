---
title: "Move GRUB to MBR"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by bj218 on 2010-03-11
How do i move GRUB to WinXP MBR?

---

### Post by psusi on 2010-03-11
Your question does not make sense.  Windows does not have an MBR, hard disks have an MBR, which is where grub goes when it's installed.

---

### Post by ajgreeny on 2010-03-11
If WinXP is on sda, which is the usual situation, you can boot to ubuntu and then simply use the command ```
sudo grub-install /dev/sda
``` which will put grub where you want it.  If the system boots to another hard disk, or you have added another disk, it may be a different /dev/sdx needed, but the only way to be sure is to know where your OSs are.  Use ```
sudo fdisk -l
``` to find out what is where.

---

### Post by bj218 on 2010-03-11
WinXP is on /dev/sda & Ubuntu is on /dev/sdb

---

### Post by ajgreeny on 2010-03-11
> **bj218 said:**
> WinXP is on /dev/sda & Ubuntu is on /dev/sdb
OK, so run ```
sudo grub-install /dev/sda
```as I said, that will do it as long as sda is first in your bios boot priority.

---

### Post by bj218 on 2010-03-11
Is there a way that i can see that grub is installed in the win mbr?

---

### Post by lisati on 2010-03-11
> **bj218 said:**
> Is there a way that i can that grub is installed in the win mbr?

Are you sure it's the MBR you want to change? There's usually only one per disk drive, which is why it's called the MASTER boot record.


Edit: Suggested reading: [http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by audiomick on 2010-03-11
> **bj218 said:**
> Is there a way that i can see that grub is installed in the win mbr?
A good way to see what is what is the boot info script that meirfra wrote.
Follow the instructions here
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
to run it and have a look at the result.txt file it generates. Post the file here if you want some help understanding it. Use the # button in the post window to put code tags around it. It is a lot of text.

---

### Post by bj218 on 2010-03-21
> **audiomick said:**
> A good way to see what is what is the boot info script that meirfra wrote.
Follow the instructions here
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
to run it and have a look at the result.txt file it generates. Post the file here if you want some help understanding it. Use the # button in the post window to put code tags around it. It is a lot of text.

sudo bash ~/Desktop/boot_info_script*.sh when I do this I get "no such file or directory"

---

### Post by bj218 on 2010-03-21
> **ajgreeny said:**
> OK, so run ```
sudo grub-install /dev/sda
```as I said, that will do it as long as sda is first in your bios boot priority.

I tried this but I still get an opening screen that say's "grub loading"
which takes a long time before I get a screen which allows me to open one
one of my operating systems.
(hd0)	/dev/sda
(hd1)	/dev/sdb
bill@bill-desktop:~$ 
this is what was returned when I ran "sudo grub-install /dev/sda

---

### Post by lisati on 2010-03-21
> **bj218 said:**
> I tried this but I still get an opening screen that say's "grub loading"
which takes a long time before I get a screen which allows me to open one
one of my operating systems.

I sometimes get a similar effect when I have a disk in my CD/DVD drive, while grub has a look to figure out what's on the device. Removing the disk usually fixes the problem.

---

### Post by bj218 on 2010-03-23
> **ajgreeny said:**
> OK, so run ```
sudo grub-install /dev/sda
```as I said, that will do it as long as sda is first in your bios boot priority.

When I run the above CODE I get the following. bill@bill-desktop:~$ sudo grub-install /dev/sda
[sudo] password for bill: 
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
(hd1)	/dev/sdb
bill@bill-desktop:~$ 

I don't understand the above response!! However when I restart I still
get Grub loading which takes a very long time before I get a list of my operating systems.

---

### Post by louieb on 2010-03-23
> **bj218 said:**
> sudo bash ~/Desktop/boot_info_script*.sh when I do this I get "no such file or directory"

Then change the _**/Desktop**_ part to wherever you have your download directory. If you don't know - in Firefox look at Edit>Preferences>General tab.

---

### Post by bj218 on 2010-03-29
> **louieb said:**
> Then change the _**/Desktop**_ part to wherever you have your download directory. If you don't know - in Firefox look at Edit>Preferences>General tab.


I downloaded “Boot Info Script” from Source Forge then I went to terminal & pasted 
“ sudo bash ~/Desktop/boot_info_script*.sh” this returned the following. 

“bill@bill-desktop:~$ sudo bash ~/Desktop/boot_info_script*.sh 
[sudo] password for bill: 
bash: /home/bill/Desktop/boot_info_script*.sh: No such file or directory 
bill@bill-desktop:~$ “

In the above  their was a folder on my desktop named Downloads that contained the words “boot_info_script*.sh”

Today I put the contents of this folder on my desktop ie “boot_info_script055.sh” I then went to terminal & typed the following

bill@bill-desktop:~$ sudo bash ~/desktop/boot_info_script055.sh
[sudo] password for bill: 
bash: /home/bill/desktop/boot_info_script055.sh: No such file or directory
bill@bill-desktop:~$ 
I think that I must be doing something wrong!! HELP












What do I do now?

---

### Post by oldfred on 2010-03-29
I just run it from downloads, if you use tab you do not have to type the entire boot_info_script055.sh:

```
fred@fred-desktop:~$ cd Downloads
fred@fred-desktop:~/Downloads$ ls boo*
boot_info_script055.sh

boot:
grub  para_hacer.txt  readme.txt  sgd  USB_readme.txt
fred@fred-desktop:~/Downloads$ sudo bash boot_info_script055.sh 
[sudo] password for fred: 
Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Computing Partition Table of /dev/sdc...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda4 for information... 
Searching sdb1 for information... 
Searching sdb2 for information... 
Searching sdb5 for information... 
Searching sdc1 for information... 
Searching sdc2 for information... 
Searching sdc4 for information... 
Searching sdc5 for information... 
Searching sdc6 for information... 
Searching sdc7 for information... 
Searching sdc8 for information... 
Searching sdc9 for information... 
Searching sdc10 for information... 
Searching sdc11 for information... 
Finished. The results are in the file RESULTS7.txt located in /home/fred
fred@fred-desktop:~/Downloads$ 

```

eidt:
My results.txt goes into /home since my downloads is a linked location, yours should be in downloads.

---

### Post by theozzlives on 2010-03-29
> **bj218 said:**
> I downloaded &#8220;Boot Info Script&#8221; from Source Forge then I went to terminal & pasted 
&#8220; sudo bash ~/Desktop/boot_info_script*.sh&#8221; this returned the following. 

&#8220;bill@bill-desktop:~$ sudo bash ~/Desktop/boot_info_script*.sh 
[sudo] password for bill: 
bash: /home/bill/Desktop/boot_info_script*.sh: No such file or directory 
bill@bill-desktop:~$ &#8220;

In the above  their was a folder on my desktop named Downloads that contained the words &#8220;boot_info_script*.sh&#8221;

Today I put the contents of this folder on my desktop ie &#8220;boot_info_script055.sh&#8221; I then went to terminal & typed the following

bill@bill-desktop:~$ sudo bash ~/desktop/boot_info_script055.sh
[sudo] password for bill: 
bash: /home/bill/desktop/boot_info_script055.sh: No such file or directory
bill@bill-desktop:~$ 
I think that I must be doing something wrong!! HELP












What do I do now?

desktop is Desktop in Linux there's a difference.
Should be able to do:
```
chmod +x /home/bill/Desktop/boot_info_script055.sh
./home/bill/Desktop/boot_info_script055.sh
```

---

### Post by bj218 on 2010-03-29
When I do this I get the following

bill@bill-desktop:~$ cd Downloads
bill@bill-desktop:~/Downloads$ ls boo*
boot_info_script055.sh
bill@bill-desktop:~/Downloads$

---

### Post by oldfred on 2010-03-29
Then you type this and it works:

fred@fred-desktop:~/Downloads$ sudo bash boot_info_script055.sh

---

### Post by bj218 on 2010-03-29
> **oldfred said:**
> Then you type this and it works:

fred@fred-desktop:~/Downloads$ sudo bash boot_info_script055.sh

bill@bill-desktop:~$ cd Downloads
bill@bill-desktop:~/Downloads$ sudo bash boot_info__script055.sh
[sudo] password for bill: 
bash: boot_info__script055.sh: No such file or directory
bill@bill-desktop:~/Downloads$ 
What do I do now?
This is a copy "/home/bill/Desktop/Downloads" of where my D L folder is.

---

### Post by louieb on 2010-03-29
Linux is case sensitive. desktop and Desktop are not the same. Make sure your using caps where caps are needed.

---

### Post by oldfred on 2010-03-29
I suggested you use tab to complete the command as it helps avoid the typos.

 sudo bash boot_info__script055.sh
sudo bash boot_info_script055.sh

only one _ for each separator.

You can also copy the command from here, right click copy and in the terminal right click paste or with terminal only - control shift v (all three) is the paste command.

---

### Post by bj218 on 2010-03-30
> **oldfred said:**
> I suggested you use tab to complete the command as it helps avoid the typos.

 sudo bash boot_info__script055.sh
sudo bash boot_info_script055.sh

only one _ for each separator.

You can also copy the command from here, right click copy and in the terminal right click paste or with terminal only - control shift v (all three) is the paste command.

Thank you Thank you I think I now have it what an ordeal. I rely appreciate
you'r patience with me!!

bill@bill-desktop:~$ cd Downloads
bill@bill-desktop:~/Downloads$ sudo bash boot_info_script055.sh
[sudo] password for bill: 
Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda7 for information... 
Searching sdb1 for information... 
Searching sdb2 for information... 
Searching sdb5 for information... 
Searching sdb6 for information... 
Searching sdb7 for information... 
Searching sdb8 for information... 
Searching sdb9 for information... 
Searching sdb3 for information... 
Searching sdb4 for information... 
Finished. The results are in the file RESULTS.txt located in /home/bill/Downloads
bill@bill-desktop:~/Downloads$

If GRUB was installed in the MBR would it show here?

---

### Post by oldfred on 2010-03-30
The very first entries are what is installed in the MBR of each drive.

You are supposed to post it, highlight then entire results.txt and use the code tag (# in right side panel above as you are posting) to put it in a scrolling box.

---

