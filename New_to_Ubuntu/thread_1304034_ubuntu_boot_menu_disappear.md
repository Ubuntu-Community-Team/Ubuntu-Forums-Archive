---
title: "ubuntu boot menu disappear"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by nayeem007 on 2009-10-28
Hi
I used windows vista and ubuntu 9.04. After I upgrade my vista to windows 7 the boot menu which gave me options to select ubuntu or vista are not available. What can I do?

---

### Post by theozzlives on 2009-10-28
[http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore]("http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore")

---

### Post by lavinog on 2009-10-28
> **nayeem007 said:**
> Hi
I used windows vista and ubuntu 9.04. After I upgrade my vista to windows 7 the boot menu which gave me options to select ubuntu or vista are not available. What can I do?

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by nakama85 on 2009-10-28
> **nayeem007 said:**
> Hi
I used windows vista and ubuntu 9.04. After I upgrade my vista to windows 7 the boot menu which gave me options to select ubuntu or vista are not available. What can I do?

yup windoze destroys grub and installs its own boot menu. The thread provided should get you back on track

---

### Post by nayeem007 on 2009-10-28
I ve tried this method
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hdx,y)".

6. Type "setup (hdx,y)"

but failed .What can i do?

---

### Post by nakama85 on 2009-10-28
> **nayeem007 said:**
> I ve tried this method
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hdx,y)".

6. Type "setup (hdx,y)"

but failed .What can i do?

Thats because Grub is basically not in use anymore. You should reinstall grub.
there are several ways to do so but the one I like to tell people is to boot from live cd and go through install process (be sure to leave all your partitions alone DONT FORMAT. When it finishes grub will be automatically reinstalled in the correct part of the hdd (replacing windows boot menu)

---

### Post by nayeem007 on 2009-10-28
when selecting the linux partition it says ....has not been marked for formatting....directories containing system files will be deleted ....

Im afraid whether I would lost my data,..

---

### Post by lavinog on 2009-10-28
> **nayeem007 said:**
> when selecting the linux partition it says ....has not been marked for formatting....directories containing system files will be deleted ....

Im afraid whether I would lost my data,..
What is saying this? Windows?

---

### Post by nayeem007 on 2009-10-28
No. I was go through the ubuntu install process without formatting as per instruction given. But it warns that I'll lose my data

---

### Post by lavinog on 2009-10-28
> **nayeem007 said:**
> No. I was go through the ubuntu install process without formatting as per instruction given. But it warns that I'll lose my data

I have heard that the live cd will repair if you reinstall too, but I have not seen anything official about it.

I would backup my data to be safe.

---

### Post by g160689 on 2009-10-28
[FONT=monospace]originally posted by catlett:
[/FONT]**How to restore Grub from a live Ubuntu        cd.** 
               This will restore grub        if you already had grub installed but lost it to a windows install or some        other occurence that erased/changed your MBR so that grub no longer        appears at start up or it returns an error.

(This how to is written        for Ubuntu but should work on other systems. The only thing to take note        of, when you see "sudo" that will mean to you that the following command        should be entered at a root terminal.)

Boot into the live Ubuntu        cd. This can be the live installer cd or the older live session Ubuntu        cds.

When you get to the desktop open a terminal and enter. (I am        going to give you the commands and then I will explain them later)

             Code:
sudo grub
This        will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter        these commands

             Code:
find /boot/grub/stage1
This        will return a location. If you have more than one, select the installation        that you want to provide the grub files.
Next, THIS IS IMPORTANT,        whatever was returned for the find command use it in the next line (you        are still at grub>. when you enter the next 3 commands)

             Code:
root (hd?,?)
Again        use the value from the find command i.e. if find returned (hd0,1) then you        would enter root (hd0,1)

Next enter the command to install grub to        the mbr

             Code:
setup (hd0)
Finally        exit the grub shell
             Code:
quit
That        is it. Grub will be installed to the mbr.
When you reboot, you will        have the grub menu at startup.

Now the explanation.
Sudo grub        gets you the grub shell.
Find /boot/grub/stage1 has grub locate the        file stage1. What this does is tell us where grub's files are. Only a        small part of grub is located on the mbr, the rest of grub is in your boot        folder. Grub needs those files to run the setup. So you find the files and        then you tell grub where to locate the files it will need for setup.
So        root (hd?,?) tells grub it's files are on that partition.
Finally setup        (hd0) tells grub to setup on hd0. When you give grub the parameter hd0        with no following value for a partition, grub will use the mbr. hd0 is the        grub label for the first drive's mbr.
Quit will exit you from the grub        shell.

---

### Post by uberg on 2009-10-28
> **nayeem007 said:**
> No. I was go through the ubuntu install process without formatting as per instruction given. But it warns that I'll lose my data

It's warning you because you are about to start the partition manager and from the partition manager you can delete a partition thus destroying the data or reformat the partition thus destroying the data.  Don't check or format any of the boxes and you should be alright.  BACK UP YOUR DATA.

---

