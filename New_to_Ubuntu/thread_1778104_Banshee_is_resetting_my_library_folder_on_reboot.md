---
title: "Banshee is resetting my library folder on reboot"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by Manhippo on 2011-06-08
Hi Folks. Anyone got any wisdom on this:

I am running regular ubuntu 11.04 on a toshiba laptop. I have one drive partitioned between Windows 7 and Ubuntu (Windows for running all my music production software, Ubuntu for everything else). I also have a secondary 'data' drive, Ntfs formatted, on which I keep large amounts of data, such as recorded audio and my MP3 collection.

So here is the thing. I load up banshee, point it at my MP3 folder on the data drive and it happily plays files from said drive. Then I reboot the computer, and when I reload Banshee, all the album artwork is still there, but nothing will play. When I go into settings, I notice that it has reset its source folder to 'music'. 

It does this every time, without fail. 

Is banshee only capable of reading reliably from folders on the ubuntu install drive? Is there a way to lock it to the folder on my data drive? I saw one thread suggesting that naming the second drive would help it mount reliably and thus not throw banshee off, but mine is named and it doesn't seem to make any difference.

Any thoughts? All help warmly appreciated.

---

### Post by coffeecat on 2011-06-08
How are you "pointing" Banshee to your data partition?

What I do is, from the Banshee menu, Media > Import Media > Import from Folders > Choose Folders > navigate to the folder with the album you want to import and then click on the Import button. That way Banshee remembers the album when you next start it.

Beware one thing. I was copying albums purchased from my Ubuntu One Music store hidden folder to the Music folder on my shared data drive and then importing them to Banshee as above. What I didn't realise was that Banshee was automatically scanning the ~/.ubuntuone folder and I was getting double entries for each track in each Ubuntu One album. This might also happen if you have an album in your home Music folder as well as "imported" from the data partition. Worth watching for.

---

### Post by Manhippo on 2011-06-08
Thanks Coffeecat. I'll give that a go. I was previously using the preferences menu to set the folder. I'll see if this works.

Ps I like unity too.

---

### Post by Manhippo on 2011-06-10
nope, unfortunately that doesn't seem to solve anything. The problem is still that Banshee needs to be redirected to my secondary drive every time i restart the computer. The only way to make it play stuff from my library is go to edit>preferences>source specific and set the music folder to the one where I keep all my music. 

When I reboot the computer and go check the music folder setting, it has always been reset to ubuntu's internal music folder.

Any idea how to stop that happening? I don't know if there is a setting I should be changing somewhere else, but it seems odd that there would even be the option to change the library folder if banshee is actually referring to a system default when it goes looking for music. Seems more likely that it is looking for the records before the system has mounted the second drive and then resetting because it can't find them. No idea how to solve this though.

---

### Post by coffeecat on 2011-06-10
How are you mounting your "secondary" drive? By clicking on the partition in the Places left pane of a Nautilus window or on bootup with a line in /etc/fstab?

I have no problems with what you are trying to achieve with my music on my sdb1 partition, but this is mounted on bootup via fstab. I think this may be your problem. If you want help editing fstab, post the terminal output of:

```
cat /etc/fstab
sudo blkid
sudo fdisk -lu
```Sorry to throw terminal stuff at you. There are GUI apps to add entries to fstab but I wouldn't touch any of them with the proverbial bargepole. From what I've discovered from threads I've been involved in they seem to cause a lot of problems.

To make it easier to post that output, remember that you can copy terminal output into the clipboard for pasting into your post by highlighting the output with the mouse and right-clicking > copy. Please also enclose the output between [noparse]```
 and 
```[/noparse] tags. It is difficult to read otherwise. You can click on the [IMG]http://ubuntuforums.org/images/editor/code.gif[/IMG] icon in the message toolbar for this.

---

### Post by Manhippo on 2011-07-07
Hey thar,

Sorry, only just noticed your further reply

The terminal output is

/dev/sda1: LABEL="SYSTEM" UUID="16FC9AE1FC9ABA87" TYPE="ntfs" 
/dev/sda2: LABEL="WINDOWS" UUID="E8B69E8EB69E5D3E" TYPE="ntfs" 
/dev/sda3: LABEL="Data" UUID="387EA0857EA03E0E" TYPE="ntfs" 
/dev/sda5: UUID="a462d08a-da1a-4c67-855d-90681b2ec27e" TYPE="ext4" 
/dev/sda6: UUID="24ef2758-670f-4fd1-971e-ca566292e67f" TYPE="swap" 

Does that make any sense?

---

### Post by coffeecat on 2011-07-07
> **Manhippo said:**
> The terminal output is

/dev/sda1: LABEL="SYSTEM" UUID="16FC9AE1FC9ABA87" TYPE="ntfs" 
/dev/sda2: LABEL="WINDOWS" UUID="E8B69E8EB69E5D3E" TYPE="ntfs" 
/dev/sda3: LABEL="Data" UUID="387EA0857EA03E0E" TYPE="ntfs" 
/dev/sda5: UUID="a462d08a-da1a-4c67-855d-90681b2ec27e" TYPE="ext4" 
/dev/sda6: UUID="24ef2758-670f-4fd1-971e-ca566292e67f" TYPE="swap" 

Does that make any sense?

Nope. Not without the output of the other two commands I asked you to run. :wink:

By the way:

> **coffeecat said:**
> Please also enclose the output between [noparse]```
 and 
```[/noparse] tags. It is difficult to read otherwise. You can click on the [IMG]http://ubuntuforums.org/images/editor/code.gif[/IMG] icon in the message toolbar for this.

That is important.

---

### Post by burrap on 2011-10-13
I had the same problem, but in 10.04 . The ntfs partition DATA was automounted but in banshee I had to re-add media to the library every time. 
Thanks to this thread I managed to solve it. The DATA partition wasn't in fstab, which can be seen with:

```
cat /etc/fstab
```[FONT=Courier New]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=a2880cda-49df-4a70-b4c6-0948a620cc47 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=b4587e21-d42d-409e-9619-1ddb34733799 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=87559632-5768-4c15-acbd-1ff71da380b7 none            swap    sw              0       0
[/FONT]


To get the UUID:

```
sudo /blkid
```[FONT=Courier New]/dev/sda1: LABEL="SYSTEM_DRV" UUID="D074EE7D74EE6626" TYPE="ntfs" 
/dev/sda2: LABEL="Windows7_OS" UUID="5C32F47932F4598A" TYPE="ntfs" 
/dev/sda4: LABEL="Lenovo_Recovery" UUID="A00CFB260CFAF5DE" TYPE="ntfs" 
/dev/sda5: LABEL="DATA" UUID="A06ECCE66ECCB676" TYPE="ntfs" 
/dev/sda6: UUID="a2880cda-49df-4a70-b4c6-0948a620cc47" TYPE="ext4" 
/dev/sda7: UUID="87559632-5768-4c15-acbd-1ff71da380b7" TYPE="swap" 
/dev/sda8: UUID="b4587e21-d42d-409e-9619-1ddb34733799" TYPE="ext4" 
[/FONT]

In System > Administration > Disk Utility I confirmed that it was mounted on /media/DATA
So I added a new line in fstab:
sudo gedit fstab
And adding this line at the bottom: UUID=A06ECCE66ECCB676 /media/DATA ntfs defaults 0 2

"deafaults 0 2" I found information about here: [HTML]https://help.ubuntu.com/community/Fstab[/HTML]Thank you guys for your help!

---

