---
title: "Please help: I accidentally wiped out all of my files"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by Old Jimma on 2011-01-25
Ubuntu Community:

I accidentally wiped out all of my files. 

I accidentally issued the following command:

rm -rf /home/WISDOM/philipsmith cp -Rv /home/philipsmith .

/home/WISDOM was my backup hard disk
/home/philipsmith was my home directory

I wanted to issue these commands separately:
First: 
                  rm -rf /home/WISDOM/philipsmith 
THis would have erased the philipsmith directory on my backup hard disk/

Next, I wanted to issue:
cp -Rv /home/philipsmith .
This would have coppied philipsmith on my hard drive to my backup hard drive.

Is there a way I can recover my files?

Thanks,
Phil Smith
Duluth, GA

---

### Post by AlphaLexman on 2011-01-25
> **Phil Smith said:**
> rm -rf /home/WISDOM/philipsmith cp -Rv /home/philipsmith .
You should have done the 'cp' command first, by 'rm' removing the files first, there is nothing to copy. I'm sorry but your files are most likely gone forever.

---

### Post by Old Jimma on 2011-01-25
Are you sure, or are they simply marked as free space now?

---

### Post by Old Jimma on 2011-01-25
The thread [http://ubuntuforums.org/showthread.php?t=1209260]("http://ubuntuforums.org/showthread.php?t=1209260") seems to suggest that it is possible to recover the lost files.

Can anyone advise on how to procedd?

Thanks,
Phil

---

### Post by matt_symes on 2011-01-25
Hi

If it's an extX drive you might have luck with

[http://extundelete.sourceforge.net/](http://extundelete.sourceforge.net/)

Otherwise have a look at photorec in TestDisk

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

In future change your backup strategy to Grandfather, Father and son or write a script that is bullet proof and only backup through that or use tar or use rsync or ..... (i.e don't use your current method. It's too error prone)

Just make sure you don't use the disk. LiveCD or USB only until you try your recovery method. 

Best of luck to you.

Kind regards

---

### Post by mikewhatever on 2011-01-25
You can undelete files on ext3/4 file system.
[http://distrowatch.com/weekly.php?issue=20100322#qa](http://distrowatch.com/weekly.php?issue=20100322#qa)

If the file system is not ext3/4, use testdisk.

---

### Post by Old Jimma on 2011-01-26
Hi Community:

I'm not sure what type of file system I had.. all that I know is that I was using lucid 10.04.

Can someone tell me what file system 10.04 installs?

THanks,
Phil

---

### Post by mikewhatever on 2011-01-26
Lucid uses ext4 by default.

---

### Post by Old Jimma on 2011-01-26
There are many files that I need to restore. It looks like testdisk is more suited to it...

But will it work on ext4? The documentation only talks about ext2/ext3.

Phil

---

### Post by matt_symes on 2011-01-27
Hi

> But will it work on ext4?

Yes

Kind regards

---

### Post by Old Jimma on 2011-01-29
Thank you, Matt. And thank you Ubuntu Community.

I've got 2 1Tb drives on order and will study this thread when they come in.

Many thanks for your reassurances and hope.

Phil Smith
duluth, GA

---

### Post by Old Jimma on 2011-02-06
Hi Ubuntu Community:

Here is what worked for me to recover lost files. My thanks to the Ubuntu forums and many Ubuntu friends in the Atlanta, GA area.

I must warn you that it is important for you to understand each of the following steps I list below before you try them. I'm an old man and it is possible that I typed something wrong, so verify each step I suggest on the forums before you do it, just to make sure.

The main thing is: You can recover your files. Just be careful, take your time, and you'll be successful.

Sincerely,
Phil Smith
Duluth, GA

Step 1: When you detect that you’ve lost files, TURN OFF YOUR COMPUTER IMMEDIATELY. Your files are still on you hard drive, they are just marked by the operating system as being available space. Turn off your computer so that you don’t overwrite them!

Have a cup off and relax. Take a day off. You’ve got a long road ahead of you, but each step is easy, and being careful, you can do it. You will be able to recover all of the files you want if you turned your computer off immediately. If you didn’t, you will probably cover everything you want the most, and perhaps everything.

By a paper notebook to take note of what you do and observe for each of the next steps.

I recommend doing 1 step per day or two so that you don’t rush and make any further unhappy mistakes. You’ll be glad you took your time.

Step 2: Buy 2 hard drives, each larger than the hard drive from which you deleted files. I bought 2 1Tb drives. My original hard drive was 250Gb.

Step 3: Find another computer and download ubuntu to its hard drive, then create a live CD by burning the iso to the cd. Do a sum check.

Step 4: Boot your ubuntu machine from the live CD.

When Ubuntu boots from the CD, choose the “TRY UBUNTU” option.  DO NOT CHOOSE THE “INSTALL UBUNTU” option. 

Applications > accessories > terminal …. They type sudo gparted

In the upper right hand corner you’ll see a pull down list of the drives that Ubuntu detcts. Note the drive that your removed files from and write down the logical name. Mine was /dev/sdb

Now, shut down Ubuntu.

Step 5: Install one of your new drives. Open up your case, slide in your new drive to one of the available bays, and attach the screws snuggly to keep it in there comfortably. Now attach a power cable and connect the SATA cable from the HD to the SATA junction box on your bother board. Be careful not to unloosen the other sata drive cables there. They are connecting your motherboard to the drive you want to recover files from!

Close your case.

Step 6: Boot from the live CD again like in step 4.

Applications > accessories > terminal …. They type sudo gparted

Now, go back up to the upper right hand corner pull down menu and  take not of the new logical devise that Ubuntu sees. It is the new drive you just installed. Mine was /dev/sda

Close gparted.


Step 7: Now take your time with this. You are going to do a bit-by-bit copy of your old hard drive so that if something goes wrong after this step, and you can always use the copy to start again.

If  you can’t understand this step and be certain you are doing the right thing and making no mistakes, you probably shouldn’t proceed further. Get someone to help you who knows Ubuntu to help you with the next steps.

This is a really, really important step. So get it right. If you don't feel comfortable with it get help. I'm not kidding. It will make the difference between feeling anguish because you may have trashed all of your family photos versus, spending a little more time, being a little more careful, and being certain that you are doing the right thing at each step, and finally recovering your photos and your memories.

**[COLOR="Red"]Maybe this is a good approach to life, in general, anyway.[/COLOR]**



Here is how to make your copy:

Applications > accessories > terminal

Now take your time and type:

Applications > accessories > terminal

dd if =[logical devise of old drive]  of=[logical device of new drive.]  bs=64k  cov=notrunc,noerror

Here substitute the logical devise name of your old drive for [logical devise of old drive], and the logical device of your new drive for [logical device of new drive.]

My dd looked like

dd if =/dev/sdb of=/dev/sda bs=64k  cov=notrunc,noerror

[B][COLOR="Red"]It is imperative that you get this right in the command liaste above “if” is the input file, and “of” is the output file. “if” is the old hard drive logical device name that holds the files you lost and “of” is the new drive logical device name where you will copy the entire contents of the old HD.

If you get this wrong, you will write over all of your old files. Take your time and get this right, post a question on the Ubuntu forums, just to check that you are doing the right thing. Don’t get this wrong.[/COLOR][/B]

Step 8: The red light on your computer case will flash furiously for a long, long time. After this step is done and the carrot is returned in the terminal window. Shut down Ubuntu and remove the new backup hard drive. Put it in a safe place. 

Detach the SATA cable from your old hard drive.

Next, install the second new hard drive in its place, attaching power and sata cable.

Step 9: **[COLOR="Red"]Now, as a precaution, detach the sata cable from your old hard disk. In this step you will format the new hd that you installed, and you don’t want to screw up and format the old hard drive that has the files you want to recover.  So, detach the SATA cable that connects your old hard drive to the motherboard before you proceed. NOTE WHICH SATA SOCKET YOU’VE DISCONECTED YOUR OLD DRIVE FROM. WHEN YOU RECONECT IT, PUT THE SATA CABLE INTO THAT SAME SOCKET.[/COLOR]**

Go and have a cup of tea.

Step 9: Reboot Ubuntu form the live CD. 

Applications > accessories > terminal window

At the terminal window: sudo gparted

In the upper right hand corner, pull down the list of logicial devices Ubuntu detects. If you see the name of your old logical device, you have not disconnected your old drive, as I suggested in step 9. In this case power down and go back to step 9. Follow the instructions.

If you don’t see the logical device of your old drive, look for a new name of a logical device. This is your new drive. It is the drive where you will be writing the files you want to save, and you have to format it before you can write onto it.

Go to [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive) and follow the directions, using gparted to format your entire hard drive into a single sector. The instructions there are a little old, so if you have questions, go to the forums and get specific instructions on how to use gparted to reformat your new HD.

Power down, and have a cup of tea.

Step 10. Open up your case, and re-attach the sata cable between your old HD and the same sata socket on the mobo from which you disconnected it.

Close your case. Reboot from the live CD.

Applications > accessories > terminal window

At the terminal window: sudo gparted

Now, you should see your old HD with the its old logical device name, and the new HD with  its new logical devise name. Write down the device name of your new HD. Mine was /dev/sda . If  you can’t understand this, you probably shouldn’t proceed further. Get someone to help you who knows what he is doing.

Step 11: Now with another computer print out and read: 
[http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive](http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive)

and

[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)


What you’ll learn from both of these is that you’ll install testdisk before using photorec to recover your files.

**[COLOR="Red"]However, photorec will by default write the saved files to the directory in which it is executed. So, you want to run it from a directory on your newly formatted hard drive to avoid writing over your old hard drive.[/COLOR]**

Step 12: Boot from the live CD

Step 13: Follow the instructions of psychocat up to the point where it is advise to: Prepare backup location

Step 14: You will mount your new hard drive in this step.


Applications > accessories > terminal window

At the carrot

sudo mkdir /var/recovery
sudo mount [logicl device name of new dirve]  /var/recovery

(mine was sudo mount /dev/sda /var/recovery

Step 15: At the terminal window:

cd   /var/recovery

Make sure you do this!!!


Steo 16. Now begin following the instructions at  
[http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive](http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive)

Start at: Recovery Steps.

If you read both links given above you’ll be able piece together some of the small ambiguities in both instructions. In general, you will want to follow photorec so that you’ll be sarching the old hard drive for the file types you will specify in photorec, and back them up to the /var/recovery directory.

If you aren’t sure you’ve done this, just x out of the termal window and start again until you are sure you’ve got it.

Step 17: Patience. It will take several days for photorec to work. So relax and just be patient. And let it work. While it is executing, photorec will imply that it may take 14 days. Just ignore it. It could take 14 days, but by searching a 250Gb drive, it only took 2 days in my case.

Good luck. Be patient, consult with other experts before you do anything. Write down a plan, and run it by the forums. You’ll succeed.

Phil Smith
Duluth, GA

---

### Post by hansolo4949 on 2011-02-06
Bravo! Excellent tutorial! I will definitely keep this in mind if/when I delete some critical files. Congrats on fixing it!

---

### Post by Old Jimma on 2011-02-06
Thanks, Hansolo4949.

It is all about giving back.

The forums showed me that.

Phil Smith
Duluth, GA

---

### Post by hansolo4949 on 2011-02-06
Yep, you couldn't be more right. Enjoy your recovered files!

---

### Post by Old Jimma on 2011-02-20
Folks:

When photorec completed recovering the files I wanted it put them into many directories and renamed the files. 

I programmed photorec to recover JPG, GZ, and PDF files.  Here is code I used to look thru each of those directories and then write JPG files to a directory called JPG, while renaming each file to account for the possibility that photorec recovered 2 files but named them the same file name and put them in different directories.

In doing its recovery, photorec put files in directories named recup_dir.1 ... recup_dir.91

I put those directories in /var/recovery/original.

See: [http://ubuntuforums.org/showthread.php?t=1691802]("http://ubuntuforums.org/showthread.php?t=1691802") for more details.

I hope this helps someone!

Phil Smith
Duluth, GA

```
clear
cd /var/recovery/original
# LOOP OVER THE DIRECTORIES
for i in recup_dir.*
do
echo $i
cd $i
DESTDIR=/var/recovery/original/JPG
for JPG in *.[jJ][pP][gG]
do
        if [ -f "$JPG" ] ; then
#                 echo cp -p "$JPG"  "${DESTDIR}/${i}_${JPG}"
               cp -p "$JPG"  "${DESTDIR}/${i}_${JPG}"
        fi
done
cd ..
done
# END LOOP OVER THE DIRECTORIES
```

---

