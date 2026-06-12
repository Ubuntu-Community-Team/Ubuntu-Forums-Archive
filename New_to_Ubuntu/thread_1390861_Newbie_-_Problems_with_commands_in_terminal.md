---
title: "Newbie - Problems with commands in terminal"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by cdi_sue on 2010-01-26
Hi,

I'm new here and to Ubuntu/Linux.  Have used Windows for years and my laptop got hit by a trojan and a friend recommended Linux.  I loaded it last night and have so far found it relatively OK with some great features.

I bought the Linux complete manual and Ubuntu 9.10 and am in the process of setting up my security which is where I am having a problem.  I have followed the instructions in the book regarding downloading of Bitdefender.  It downloads then it advises the following:
[COLOR=DarkSlateBlue][I]
"Once downloaded, click on Accessoies......go to Terminal.  Enter the following command:
cd /Desktop

Now enter the following (noting the capital B of Bit), but instead of clicking Return, press the tab key.  This will fill in the long file name for the downloaded BitDefender package:

sudo sh Bit

Hit Return and you'll be asked for your password.  Enter it and the Bit Defender licence agreement appears........


[/I][/COLOR]My problem is that the tab key does nothing in this program.  I've tried many combinations and can't get anywhere with it.  Any suggestions or does someone know where I can locate the file name for BitDefender?  Any help would be great.

Many thanks

Sue

---

### Post by MarcDam on 2010-01-26
Try "cd /folder/where/you/downloaded/the/file" instead of "cd /Desktop"

---

### Post by chewearn on 2010-01-26
First off, BitDefender appeared to be an anti-virus for Windows?  Unless you want to scan for viruses in a Windows' harddrive from Ubuntu, there is very little use for it.  It would be better to scan Windows' viruses while running Windows?

I have been running Ubuntu for many years without anti-virus (as does many other people) and have not once been infected.  Really, there no known Linux virus in the wild.

But, if you insist, then the filename can be seen by running:
```
ls
```

That's the command to list the content of a directory.

---

### Post by benfindlay on 2010-01-26
Just a thought, ```
cd /Desktop
``` probably won't work as the / indicates the root of the hard disc. It should be ```
cd Desktop
```It would also be worth checking the file name to be 100% sure by looking at the file; if it is indeed sitting on your desktop there will be an icon with the filename beneath it.

Hope this helps, and welcome to ubuntu!

---

### Post by KeLa on 2010-01-26
In ubuntu 9.10 it's in Downloads directory.
So try this in terminal
```
cd ~/Downloads
```
Note that if you try cd /Desktop or cd /Something it will try to go to directory under root or your disk and for example Desktop and Downloads directories are in your home directory.
You can always substitute /home/yourusename with single ~ character.

---

### Post by cdi_sue on 2010-01-26
Have now located the file, and have got into the right directory in terminal but it won't run the BitDefender program. The sudo sh Bit 

sue@sue-laptop:~/Downloads$ sudo sh BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb
sh: Can't open BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb
sue@sue-laptop:~/Downloads$  
sue@sue-laptop:~/Downloads$ dir
BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb(2).run
BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run
sue@sue-laptop:~/Downloads$ 

Did dir command (it's about all I can remember from pre windows days of Dos) and it shows it is there but I don't know how to make it work, tried run but it doesn't work. 

I will write all this down after so i don't come back hassling again for the same thing

Thanks

---

### Post by benfindlay on 2010-01-26
It's a deb file, so you should try ```
sudo dpkg -i [filename]
```instead, and you can use the tab completion function again with the first few letters, to save typing in the long file name.

Hope this helps

---

### Post by cdi_sue on 2010-01-26
Thanks for that, still no joy now getting

sue@sue-laptop:~/Downloads$ sudo dpkg -i BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb
dpkg: error processing BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb
sue@sue-laptop:~/Downloads$ 

should I just give up?? if anti-virus is so unnecessary is it worth the agro

---

### Post by KeLa on 2010-01-26
Just read about install procedure of BitDefender and it's so complicated that i have not seen many so complicated packages.
If you need virus protection there are many to select that has easier to install.
Like AVG and Avast Antivirus etc...

---

### Post by MarcDam on 2010-01-26
Try "sudo sh BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run"

---

