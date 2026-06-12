---
title: "[SOLVED] Somebody help me please"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by GSI on 2009-01-05
Hello everybody,my name is Hristian I have two problems.
First I cant use the Shift button to type Main letters.
The second problem is that I updated my ubuntu today and now when I have to choose which system too boot I have two ubuntu's is there a way to remove the old one

---

### Post by cmnorton on 2009-01-05
Please consider using a more descriptive title, like Shift Key Does Not Work.

The two Ubuntu entries are probably different versions of the kernel. Which one did you try, the top or bottom one?

I would try the bottom entry (oldest).

Then, press CTRL+ALT+F1 to watch the boot, and see if there are any error messages.

---

### Post by capnthommo on 2009-01-05
hi GSI.  sorry i cant be more helpful but i remember seeing something that relates to the second of you questions.  apparently when the kernel updates it leaves the earlier version on the boot up screen (as a back-up i think)  no doubt somebody else will correct me if i am wrong but i believe this shouldn't cause you any problems.  just use the latest.  as i say, i am very new to this so i am not certain but i hope this helps.  i know that my boot up (grub?) screen shows ubuntu, ubuntu recovery mode, ubuntu (old), ubuntu (old) recovery mode, memtest and vista. even though vista has been removed entirely from the machine.  hope this helps
nigel

---

### Post by Lisa Y on 2009-01-05
If i am not mistake you have to re-partitions the harddrive. When you installed the "newer" version of ubuntu, it seems that you must have partitioned the hard drive space to keep both your new and old.

Remember installed of installing a completly formating your hard drive to obtain the newer version of ubuntu you can also do it from the comand line. Using this command

```
sudo apt-get dist-upgrade
```

Or go to the update manage to automatically update it to the lastest distro for you.

Inorder to fix your problem...you must boot into a live cd and re-partition your hard drive therem

---

### Post by cmnorton on 2009-01-05
> **GSI said:**
> Hello everybody,my name is Hristian I have two problems.
First I cant use the Shift button to type Main letters.
The second problem is that I updated my ubuntu today and now when I have to choose which system too boot I have two ubuntu's is there a way to remove the old one

I'm confused. Did you update or perform what you might have thought was an update by inserting installation media?

Lisa Y has probably isolated the cause of two "Ubuntus" -- two instances of Ubuntu -- if you performed an update from installation media

---

### Post by sadaruwan12 on 2009-01-05
> **GSI said:**
> Hello everybody,my name is Hristian I have two problems.
First I cant use the Shift button to type Main letters.
The second problem is that I updated my ubuntu today and now when I have to choose which system too boot I have two ubuntu's is there a way to remove the old one

First of all theres no problem using this title. I like to know what version of Ubuntu you're using to get the version information open up the terminal and type this code,

```
lsb_release -a
```

then post the out put here. And also is this a release update or a normal update. If it's a normal one I want to know is this the first time you've updated your Ubuntu. Please do reply so I can give you a good answer. :)

---

### Post by GSI on 2009-01-05
I really need some help for the Shift key.It was working 3 days ago but now it dosent I used the Shift key constantly in Windows and Linux so I really need some help


P.S I just updated ubnutu and the two ubuntu's dosent cause any problem its just annoying

---

### Post by mkvnmtr on 2009-01-05
It is likely the second Ubuntu you see listed is the old kernal that has been replaced. While youn can delete it in the boot menu you might consider leaving it. If you have problems later with your current Ubuntu you can always use that kernal to boot.

---

### Post by arpanaut on 2009-01-05
> **GSI said:**
> 
P.S I just updated ubnutu and the two ubuntu's dosent cause any problem its just annoying

Why annoying, I find it reassuring, in that if the new kernal has issues that I can boot to the "old" kernal and all will be well.

If after a period of time the new kernal is working properly the "old" can be edited out of your menu.lst and you are good to go.

To each his own ways. LOL I have about 20 stanza's in my grub options, but I have 4 different operating systems that are available on this machine...

---

### Post by GSI on 2009-01-05
Thank you for the decisions guys I will leave the two ubuntu's now.And btw I fixed the Shift problem.It was the effects.Some of them were using Shift as button to start so I disabled the options and its working now!

---

### Post by cmnorton on 2009-01-05
You may have to resort to booting into recovery mode; running 

dpkg-reconfigure xserver-xorg

answering all questions default; except where it comes to your keyboard. See if the reconfigure can detect it; else take the default answer.

Other than that, try the administrative configuration panel.

---

### Post by sadaruwan12 on 2009-01-05
> **GSI said:**
> I really need some help for the Shift key.It was working 3 days ago but now it dosent I used the Shift key constantly in Windows and Linux so I really need some help


P.S I just updated ubuntu and the two Ubuntu's dosent cause any problem its just annoying

It seems like you've just updated  ubuntu and it your kernel has been updated at the same time it's normal in any Linux distro to list it's old kernel versions for backward compatibility if you don't like it you could just remove it by editing the GRUB menu.lst file here's how to do that

Open the terminal and type
```
sudo gedit /boot/grub/menu.lst
```

Now you'll get the GRUB menu list configuration file scroll down and remove the old kernel listing then save it and reboot the PC to see to find only one kernel is listed.

OR

If you find this hard to do go to System -> Administration -> Synaptic Package Manager the search for Start Up Manager select it and install it on to your PC. Now go to System -> Administration -> StartUp-Manager you can use this to edit the menu.lst file go to the advanced tab and check the "Limit the number of kernels in the boot menu" and give how many number of kernels you like to see on the GRUB menu use this GUI front end to add a background image to grub to make it more attractive.

\\:D/

---

