---
title: "[SOLVED] I am not able to create folders or do any editing to files on my second hard"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by robond8 on 2008-12-31
Hello,

I have two internal hard drives. One of them is fully partitioned for Ubuntu 8.10 and Ubuntu runs off it too. The second one used to run Windows XP. I did not remove the XP drive properly so I was told to reformat the drive from ntfs (or nfts or something like that) to ext3. After doing this though the drive is still basically useless. It won't let me add documents or folders or anything to the drive. I went to the partition editor and saw that there is a small amount (like 700 MB) of the drive I am not able to partition to Ubuntu. I believe that XP is still on that section of the drive and if I were to be able to partition the WHOLE drive I could just delete those files and have full access to the drive for adding/removing files. 

PLEASE HELP! 

note: THE DRIVE IS INTERNAL NOT EXTERNAL! I ALSO AM NOT FAMILIAR WITH USING THE COMMAND TERMINAL SO IF YOU ARE GOING TO GIVE ME SOME COMMANDS TO TRY THEN PLEAS MAKE SURE TO TYPE OUT THE FULL COMMAND I NEED TO PUT INTO THE TERMINAL. THANKS!

---

### Post by damis648 on 2008-12-31
Okay, first unmount any partitions for that drive (right click them on the desktop>unmount). Then open a terminal and input:
```
sudo apt-get install gparted
```
when that is done close the terminal and head to System>Administration>Partition Manager. Select the disk from then menu on the right hand side. Click on each partition and delete them. Then, right click the gray 'Unallocated Space' and click new partition. In the dialog, choose for it to be Ext3 and then click OK, followed by 'Apply' at the top. Now when that is done, close gParted and go to Places>[Disk Name]. You should be able to write to it now. If not, open a terminal again and enter in:
```
sudo chmod -R 777 /media/disk
```

---

### Post by robond8 on 2008-12-31
Thank you damis648, here is what happens when I do the steps:

After re-partitioning the drive the way you said, the drive does not show up in My Computer. So I typed in the second command you gave me and it says that no such file or directory exists?

What did I do wrong? Thanks

---

### Post by balloooza on 2008-12-31
can you tell me what is on your desktop as far as harddrives

---

### Post by 45acp on 2008-12-31
Are you looking at the drive from Windows or Ubuntu? Yon mentioned My computer. That leads me to think Windows. If you reformatted the drive to Ext3 Windows will no be able to use it because Windows uses a ntfs file system. You should be able to see the drive from Ubuntu with Gparted. If you can, you probably just need to change permissions as the previous poster suggested.

---

### Post by robond8 on 2008-12-31
answer to 45acp: I am on Ubuntu 8.10, I accidentally said "My Computer" to refer to "Computer" under Places. 

Also

answer to balloooza: when I go to Places>Desktop nothing shows up. I don't have any desktop icons. But you may be referring to Places>Computer . If so, the only things that show up there are "filesystem" (my hard drive with Ubuntu on it, it works fine) and CD-RW Drive (that's my CD drive). 

My second hard drive (the one I am trying to get to work, please refer to my other posts) DOES NOT SHOW UP after following the steps recommended by damis648. 

Thanks

---

### Post by balloooza on 2008-12-31
try manuly mounting it
```
sudo mkdir /media/2ndhrd
```
then run
```
sudo mount /dev/sdb1 /media/2ndhrd
```

then run
```
sudo nautilus /media/2ndhrd
```
too see it now

also post the results of
```
ls -l /bin/mount
```

---

### Post by robond8 on 2008-12-31
answer to balloooza: After typing in the first command ( sudo mkdir /media/2ndhrd ) The terminal says this: 

robert@Rob's Machine:~$ sudo mkdir /media/2ndhrd
sudo: unable to resolve host Rob's Machine
mkdir: cannot create directory `/media/2ndhrd': File exists
robert@Rob's Machine:~$ 

And when I type the Command: ls -l /bin/mount , the terminal says this:

robert@Rob's Machine:~$ ls -l /bin/mount
-rwsr-xr-x 1 root root 92584 2008-09-25 07:08 /bin/mount
robert@Rob's Machine:~$

---

### Post by balloooza on 2008-12-31
can you forst run the other commands (all of them,even if they fail) then tell me the results of
```
ls -l /media
```
and include all the other messages

---

### Post by robond8 on 2008-12-31
answer to  balloooza: here is the what the terminal says after I type all of those commands (minus the last one that you said to do if the others failed):

robert@Rob's Machine:~$ sudo mkdir /media/2ndhrd
sudo: unable to resolve host Rob's Machine
mkdir: cannot create directory `/media/2ndhrd': File exists
robert@Rob's Machine:~$ sudo mount /dev/sdb1 /media/2ndhrd
sudo: unable to resolve host Rob's Machine
robert@Rob's Machine:~$ sudo nautilus /media/2ndhrd
sudo: unable to resolve host Rob's Machine
seahorse nautilus module initialized
Initializing nautilus-share extension

** (nautilus:9141): WARNING **: Unable to add monitor: Operation not supported


After doing that the drive (called : 2ndhrd ) appears to be functioning fine. BUT after doing that command a desktop icon appears called "40 GB Media" (My second drive I presume) and when I click that I am able to see what's on the drive but am unable to add/remove files from it (like at the beginning, refer to my earlier posts). 

So is there a way I can make things so I will be able to access the drive without typing in all those commands again? 

Should I run that last command you gave me?

---

### Post by robond8 on 2008-12-31
Also:

when I run the code: ls -l /media


I get:

robert@Rob's Machine:~$ ls -l /media
total 12
drwxr-xr-x 4 root root 4096 2008-12-31 14:25 2ndhrd
lrwxrwxrwx 1 root root    6 2008-12-30 07:00 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2008-12-30 07:00 cdrom0
drwxr-xr-x 2 root root 4096 2008-12-30 07:00 cdrom1
robert@Rob's Machine:~$

---

### Post by balloooza on 2008-12-31
I will write a script to run to do this, this will take a while, but keep watching after I get the script up, bucause you should be able to change the permissions, that is the perminate fix.

---

### Post by balloooza on 2008-12-31
run
```
sudo cp -p /etc/fstab /etc/fstab.v1
```
to make a backup
run
```
sudo sh -c "echo '/dev/sdb1 /media/2ndhrd ext3 default 0 2' >> /ext/fstab"
```
run 
```
sudo mount /media/2ndhrd
```
run
```
sudo chown robert-robert /media/2ndhrd
```
this will mount the disk, and every time you restart the disk will automatically be mounted. You do not need to run any more commands, and if something goes horribly wrong, I will be available still. the disk should be in the sidebar, but if it is not, drag /media/2ndhrd to the places sidebar.

---

### Post by robond8 on 2008-12-31
Many thanks ballooza for your help thus far! Okay so here is what happend when I typed in your last commands you gave me:

robert@Rob's Machine:~$ sudo cp -p /etc/fstab /etc/fstab.v1
sudo: unable to resolve host Rob's Machine
robert@Rob's Machine:~$ sudo sh -c "echo '/dev/sdb1 /media/2ndhrd ext3 default 0 2' >> /ext/fstab"
sudo: unable to resolve host Rob's Machine
sh: cannot create /ext/fstab: Directory nonexistent
robert@Rob's Machine:~$ sudo mount /media/2ndhrd
sudo: unable to resolve host Rob's Machine
mount: /dev/sdb1 already mounted or /media/2ndhrd busy
mount: according to mtab, /dev/sdb1 is already mounted on /media/2ndhrd
robert@Rob's Machine:~$ sudo chown robert-robert /media/2ndhrd
sudo: unable to resolve host Rob's Machine
chown: invalid user: `robert-robert'
robert@Rob's Machine:~$ 

The drive appears (Places>40 GB Drive) but I still am unable to add/remove files! 

I know for sure that I typed all the commands correctly (I did it a few times :-)!).

What should I try next!? Thanks again!

---

### Post by balloooza on 2008-12-31
You have an even bigger problem, your computer name is bad. IT CAN ONLY BE ONE WORD
I will find hoow to fix it, as for the other stuff, I made some typos (the unable to resolv thing is a result of the two worded name)

You cannot use 's either, you might consider
```
rob-desktop
```
once I  figure out how to change it.

---

### Post by robond8 on 2008-12-31
Okay,

Now that I remember, there was some error thing when I set up Ubuntu due to the name for the Computer I chose. It was weird because when I did the name it said "invalid name cannot contain 's etc" but then it wouldn't let me re-name it in the set up process. 

Thanks for catching that, I'd already written it off as a non issue!

---

### Post by balloooza on 2008-12-31
I am on instant message with the expert, he may be able to help change the name

---

### Post by balloooza on 2008-12-31
run :
```
sudo sed -i "s/[' ]//g" /etc/hostname
```
then reboot

---

### Post by robond8 on 2008-12-31
Okay I did what you said, what now? Thanks!

---

### Post by balloooza on 2008-12-31
also run
```
sed -i "s/Rob's Machine/RobsMachine/" /etc/hosts
```
you don't need to restart after this one. Then run these corrected commands
in this order
```
sudo cp -p /etc/fstab /etc/fstab.v1
```
```
udo sh -c "echo '/dev/sdb1 /media/2ndhrd ext3 default 0 2' >> /etc/fstab"
```
```
sudo mount /media/2ndhrd
```
```
sudo chown robert:robert /media/2ndhrd
```
then you should be able to use your hard drive, and it will AUTOMATICLY come up after booting, thankyou for your patience,it helps on delayed communication.

---

### Post by robond8 on 2008-12-31
Haha, don't worry about it! You're the one who's like doing this all just to help me out! 

So this is what the terminal says after typing in those commands:

robert@RobsMachine:~$ sudo cp -p /etc/fstab /etc/fstab.v1
sudo: unable to resolve host RobsMachine
[sudo] password for robert: 
robert@RobsMachine:~$ udo sh -c "echo '/dev/sdb1 /media/2ndhrd ext3 default 0 2' >> /etc/fstab"
The program 'udo' is currently not installed.  You can install it by typing:
sudo apt-get install udo
bash: udo: command not found
robert@RobsMachine:~$ sudo mount /media/2ndhrd
sudo: unable to resolve host RobsMachine
mount: can't find /media/2ndhrd in /etc/fstab or /etc/mtab
robert@RobsMachine:~$ sudo chown robert:robert /media/2ndhrd
sudo: unable to resolve host RobsMachine
robert@RobsMachine:~$ 

The only thing it changed for me was the name of hard drive. It's know named "disk" instead of "40 GB Media". I am still unable to add/remove files on it! 

Next step? Thanks!

---

### Post by balloooza on 2008-12-31
We still have a problem, but try the command With udo is not currently installed and replace "udo" with sudo, typo, and the name thing is still a mystery. But also tell me the output of

```
ls -l /etc/fstab*
```
and
```
cat /etc/hostname
```

---

### Post by robond8 on 2008-12-31
Hey

Here is the outcome that I got after changing "udo" to "sudo":

robert@RobsMachine:~$ sudo cp -p /etc/fstab /etc/fstab.v1
sudo: unable to resolve host RobsMachine
robert@RobsMachine:~$ sudo sh -c "echo '/dev/sdb1 /media/2ndhrd ext3 default 0 2' >> /etc/fstab"
sudo: unable to resolve host RobsMachine
robert@RobsMachine:~$ sudo mount /media/2ndhrd
sudo: unable to resolve host RobsMachine
robert@RobsMachine:~$ sudo chown robert:robert /media/2ndhrd
sudo: unable to resolve host RobsMachine
robert@RobsMachine:~$ 

(Note: I checked the Hard drive again and nothing had changed)

Here is the outcome of the first of the last two commands you gave me:

robert@RobsMachine:~$ ls -l /etc/fstab*
-rw-r--r-- 1 root root 445 2008-12-31 16:59 /etc/fstab
-rw-r--r-- 1 root root 404 2008-12-30 07:15 /etc/fstab.v1
robert@RobsMachine:~$ 


And the second:

robert@RobsMachine:~$ cat /etc/hostname
RobsMachine
robert@RobsMachine:~$ 


I am starting to get pretty good at entering commands in the terminal now!:P

So what should I do now? Thanks again!

---

### Post by balloooza on 2008-12-31
This is getting to a point where I would go for a reinstall, tell me about how long yyou have been using the computer and what you have done and how many files. A reinstall is not that bad of an option, unless you have been coustomizing your desktop for a while.
If you do do the reinstall tell me when you are done, and I can help you with the harddrive thing (it should work right when you boot up, if you reinstall and name your desktop 
```
rob-desktop
```
I would recomend this because I normaly use somthing like it.
This is worse than my rookie mistake of not making a password. THAT IS BAD
I would recomend doing the reinstall, seing that you have very little other option. But as for others having this problem, besides robond8 the instructions should be straight forward to make the disk mount on boot.

also robond8, a few tips on the command line, sudo means run as root, root is the ststem admnistrator.
If you hit the tab key it will finish the command for you if there is only one possible option left, EX synap (press tab) and synaptic comes up
If there are more that one possibility left hit tab a few times. EX 
mark@mark-laptop:~$ syn (hit tab a few times)
synaptic   sync       synclient  syndaemon(and you get that)  
also as for copying and pasting, CTRL  + SHIFT + C is copy. 
And a simple middle click will past whatever is selected, or past

---

### Post by mbzn on 2008-12-31
Try
sudo chmod -R 777 /media/2ndhd

---

### Post by balloooza on 2008-12-31
mbzn, his problem is that he has a bad name. And that is not a good fix, because then even if the disk was not mounted, he could still write to the /media/2ndhrd, His problem was he used illegal characters in his hostname

---

### Post by Miljet on 2008-12-31
There is a way to fix this without a re-install. I had the same problem when my hard drive failed and I replaced it with another used drive. It was a very simple fix. Let me think about it for a few minutes.

---

### Post by Miljet on 2008-12-31
OK, I remember it now. The machine names must match in both /etc/hosts file and /etc/hostname file. Post the output of

```
cat /etc/hosts
```

and

```
cat /etc/hostname
```

---

### Post by robond8 on 2009-01-01
Okay,

I do have another drive that I will try to replace the bad one with. But, the bad drive is in the Master Port on the motherboard. the drive that is running Ubuntu is in the Slave Port. 

The drive I would use as a replacement runs Windows. So if I put the replacement drive in the Master Port wouldn't it boot into windows? Or will Grub still give me the option for either OS?

This is deep water for me! But I have yet to find something I couldn't fix on a computer! Thanks everyone for the help thus far! Happy New Year!

---

### Post by robond8 on 2009-01-01
here is the outcome of command: cat /etc/hosts

robert@RobsMachine:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	Rob's Machine

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
robert@RobsMachine:~$ 


and here's the output of the cat /etc/hostname command:




robert@RobsMachine:~$ cat /etc/hostname
RobsMachine
robert@RobsMachine:~$

---

### Post by balloooza on 2009-01-01
I think I found the problem
```
sed -i "s/Rob's Machine/RobsMachine/" /etc/hosts
```
was run right, if not run it, and if you are sure you ran it (use the up arrow to view older commands) it dosn't hurt to run
```
sudo sed -i "s/Rob's Machine/RobsMachine/" /etc/hosts
```
then check
```
cat /etc/hosts
```
if it still has ```
Rob's Machine
``` in it, reboot, but this time boot into recovery mode, and drop to root shell, then run
```
sed -i "s/Rob's Machine/RobsMachine/" /etc/hosts
```
 (you will have to write it down, the clipboard will not work) then type 
```
poweroff
```
so now you changed the computer name, turn on the computer, run
```
cat /etc/hosts
```to see that the name is indeed changed tell me when you are done.

after this I will help you set up the drive so it "mounts" at bootup, so there are no commands to type,

---

### Post by zika on 2009-01-01
to [B]baloooza:

[/B]I thought I was a patient man but You made me blush! great work! it's a privilege to see someone so sharing to do this so wholeheartedly ... have a very good 2009!

this is just what "ubuntu" stands for ...

---

### Post by robond8 on 2009-01-01
Okay,

I ran the code: sudo sed -i "s/Rob's Machine/RobsMachine/" /etc/hosts


outcome:


robert@RobsMachine:~$ sudo sed -i "s/Rob's Machine/RobsMachine/" /etc/hosts
sudo: unable to resolve host RobsMachine
[sudo] password for robert: 
robert@RobsMachine:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	RobsMachine

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
robert@RobsMachine:~$ 

I didn't see the " 's " in there so I haven't done the reboot step.

Should I still do it?

---

### Post by balloooza on 2009-01-01
robond8 and I figured it out over google talk, it was getting hard over this.

our solution (if your hostname has no 's or spaces)
NOTE: THIS IS FOR AN INTERNAL DRIVE, DO NOT USE THIS ON AN EXTERNAL

first, make a backup copy of /etc/fstab
```
sudo cp -p /etc/fstab /etc/fstab.v1
```
Then you add a line to fstab, to make the disk automaticly come at startup.
```
sudo sh -c "echo '/dev/sdb1 /media/2ndhrd ext3 defaults 0 2' >> /etc/fstab"
```
NOTE: MAKE SURE YOUR DISK IS /dev/sdb1, this is standered, but to check, run
```
sudo mount /dev/sdv1 /media
```
too see if it is the dik that you want.
NOTE, this only works if the filesystem is EXT3, not NTFS. if this is the case, you should post before continuing.

then run
```
sudo mount /media/2ndhrd
```
if you get any errors, stop, run
```
sudo cp /etc/fstab.v1 /etc/fstab
```
to restore the backup, and seek further instruction

then you need to be able to change the files, run:
```
sudo chown yourusername:yourusername /media/2ndhrd
```
replace yourusername with Your User Name

then you are DONE!!!

---

### Post by antonehenry on 2009-01-11
Hi there.  

I had the same problem as rob.

I have successfully gotten the drive to mount when I do it manually, but I need to know how to make it mount everytime i start up the computer.

thanks!

---

### Post by robond8 on 2009-01-11
Hello antonehenry,

We were able to solve the problem (getting the hard drive to mount on boot, every time) by following the steps in balloooza's last post on this thread. I hope that works for you! I was a total noob to the Terminal and Ubuntu itself and I was able to follow those steps with success. 

Good luck, Robond8

---

### Post by antonehenry on 2009-01-15
Oh I did, but I missed the "NOTE, this only works if the filesystem is EXT3, not NTFS. if this is the case, you should post before continuing."

My filesystem is NTFS... =[

---

### Post by antonehenry on 2009-01-17
Alright, I have gotten my drive mounted.  But I can only create directories in terminal and I cannot put any files in the folders.


help?

---

