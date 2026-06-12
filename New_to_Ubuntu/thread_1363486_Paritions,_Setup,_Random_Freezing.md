---
title: "Paritions, Setup, Random Freezing"
date: 2009-12-24
forum: New to Ubuntu
---

### Post by jmine83 on 2009-12-24
- Background Description -
 
 ( ! ) Skip ahead to **bold** statements to address my direct questions/concerns.
 
 I recently decided to jump on-board with trying Ubuntu and officially installing the O/S as part of my computer setup. I am currently a college junior, but recently just finished my first freshman semester of computer science related courses. I also have a relatively new notebook PC I purchased last July before the fall 2009 semester began. During the course of my IT 1100 class, I got to know more about LINUX and its uses and such, and now I am thinking I should have Ubuntu installed with Windows on my notebook PC to gain well-rounded knowledge and experience in the functions and use of LINUX. And in class, Ubuntu was the specific O/S that the instructor had us all install on a virtual machine server. So now naturally as I am explaining, I want to install Ubuntu on my notebook PC.
 
 First, I downloaded the ISO disc image file of "Ubuntu 9.10 64-bit" and burned that to a disc. Then I booted the disc from boot-up and proceeded with the Ubuntu installation as I would a new Windows installation that I've done countless times before. The Ubuntu installation process and prompts were fairly easy and self-explanatory, until I got to the partition setup screen of the installation process. Need-less-to-say, I tried two of the different partition setup options, but didn't really feel like I understood completely what Ubuntu was doing for partitioning. I was able to get into the Ubuntu GUI at any rate, but then ran into random freezing where the screen would completely lock-up; i.e. mouse cursor freezes, keyboard input disabled, no animation on screen. After a lot of grief, I decided to discard the idea of installing Ubuntu on my notebook PC at all until I did some more research. Trying to do a clean remove of Ubuntu was a major pain because GRUB modified the MBR and I could no longer even get back into Windows 7. But I did manage to figure out how to fix the MBR and return control back to Windows.
 
 Anyways, I have some direction questions/comments I wish to pose now in performing the proper setup of my partition structure that I desire; as well as understanding what partitions Ubuntu needs to function.
 
 - Partition Structure Description -
 
 I read through the Ubuntu online documentation to educate myself on how to perform a dual-boot setup configuration between Windows and Ubuntu. I see now that I should have chosen the option to manually define my Ubuntu partition(s). I initially figured Ubuntu was dynamic and savvy enough to know what I wanted to do, but apparently not.
 
 Currently, my partition structure is such that, the first portion of my hard drive space is allocated to a special hidden RECOVERY partition that came with my new notebook PC that when used as and I understand it, will restore the whole machine back to its factory default condition, running Windows Vista. This RECOVERY partition takes up the first 11 GB of space or so, and naturally I do not want to mess with this partition at all. I am glad its there and I will not tamper with it.
 
 
 Next, I have my Windows 7 system partition allocating the next 25 GB of hard drive space. I specifically sized this partition to the size specified, and I rather not change it because I think it's perfect and appropriate.
 
 Finally, the rest of the available computer hard drive space is not allocated and therefore free space. Specifically, I have approximately somewhere between 260 GB to 290 GB I believe of the free space in question. Now, these are the ideal conditions I am looking to satisfy with my partition setup:
 
 One, that Ubuntu generates only "one" essential partition; i.e. the root Ubuntu system partition. And as per Ubuntu documentation instruction, I understand this system partition should be at least 4GB right? More appropriately, probably at least double that amount to be safe? I will probably make the Ubuntu system partition 10 GB in size.
 
 But also as the Ubuntu documentation instructs, apparently Ubuntu needs a "home" and "swap" partition as well? Based on the description, I roughly understand what the "swap" partition is and if I "need" to implement that partition to make this work, I will. The "swap" partition will be set to 8 GB in size since my notebook PC natively has 4 GB of RAM installed. But what about this "home" partition business?
 
 In regards to the function of this "home" partition, I can understand it's purpose, but I need to know a few things first before I feel comfortable implementing it:
 
 Traditionally, with just a Windows setup, I will have two Windows partitions that I will label SYSTEM and DATA. The SYSTEM partition is dedicated to the Windows O/S files of course, while the DATA partition is an NTFS type Windows partition that has all my personal files stored there. And as I understand it, the function of this Ubuntu "home" partition is similar. However, this is what I wish to specifically accomplish in my desired setup:
 
 **A "shared" personal files partition that Windows 7 and Ubuntu can both use. How do I do this?** So for example, music files in a Music directory can be played and edited both in Windows 7 and Ubuntu. Under Windows 7, I can specify the location of the following directories to anywhere on the hard drive: Documents, Pictures, Music, Video, Downloads, and maybe some others. And I believe Ubuntu is the same right? I don't want copies of these files separately generated between Windows and Ubuntu via syncing or importing. They should be the "same" files shared between both operating systems. The size of this partition would simply be all the available remaining hard drive space that remains.
 
 If someone could instruct me what I need to know and do to create this "personal files" partition, I would greatly appreciate it.
 
 - Random Freezing -
 
 As I described earlier, when I am able to get into the Ubuntu GUI and login to my user account and such, the system will freeze at any random point for no easily overt reason or discernible pattern. I can't even get the Ubuntu GUI to stay not frozen long enough to run system updates. After searching through the forums for similar cases, the common comment was that freezing is due to a hardware driver complications or failure. That quite possibly, my new notebook PC is maybe "too new" and therefore is not yet supported by Ubuntu. The notebook PC I am using is the ASUS F70SL. The following link is the official product page of my notebook PC through the manufacturer's website:
 
 [ASUS F70SL]("http://www.asus.com/product.aspx?P_ID=maLt0AYq6ITIyJyB")
 
 **Please let me know what I can do to resolve these random freezing issues.**

---

### Post by cariboo on 2009-12-24
You're going to run into problems if you try to share the directories you specified, you would have to use an ntfs partition as Windows doesn't natively know anything about partitions not created by Windows, ntfs doesn't support permissions needed by a linux based system. 

Fortunately there is a work around by using sym-links, you can link the directories in your home directory to the directories on an ntfs partition. You can use something like:

```
sudo ln -s /windows/partition/Music /home/user/Music
```

For more info, as I can't give you exact instructions as I don't know you partition layout see:

```
[list]
[*] man symlink
[*] man ln
[*] man link
[/list] 
```

---

### Post by QLee on 2009-12-24
Very detailed request, hope there is enough detail in my reply, I assume there is for a computer science major.


> **jmine83] Now, these are the ideal conditions I am looking to satisfy with my partition setup:
 
 One, that Ubuntu generates only "one" essential partition said:**
> 

It should work with 10G. Unless you install an extremely large number of desktop managers or extra software or save data on it (i.e. have your home on it) or not clean the package cache as binaries are upgraded (i.e. security upgrades).
 
[QUOTE=jmine83] But also as the Ubuntu documentation instructs, apparently Ubuntu needs a "home" and "swap" partition as well? Based on the description, I roughly understand what the "swap" partition is and if I "need" to implement that partition to make this work, I will. The "swap" partition will be set to 8 GB in size since my notebook PC natively has 4 GB of RAM installed. But what about this "home" partition business?

If you do not specify a separate partition for home, home will be created in the filesystem on that 10G partition. Would work fine that way, could get filled (to be avoided) if you save a bunch of big files (i.e. music or movies etc.).

Since it's a laptop, you want a swap large enough to hold the contents of RAM so you can hibernate (suspend to disk). It is possible to create a swap file if you absolutely don't want to use a separate partition. You can investigate that if your requirements are that strict.
Edit: 8G is too much if you have 4G RAM, you'll probably never hit swap in normal use.
 
[QUOTE=jmine83] In regards to the function of this "home" partition, I can understand it's purpose, but I need to know a few things first before I feel comfortable implementing it:
 
 Traditionally, with just a Windows setup, I will have two Windows partitions that I will label SYSTEM and DATA. The SYSTEM partition is dedicated to the Windows O/S files of course, while the DATA partition is an NTFS type Windows partition that has all my personal files stored there. And as I understand it, the function of this Ubuntu "home" partition is similar. However, this is what I wish to specifically accomplish in my desired setup:
 
 **A "shared" personal files partition that Windows 7 and Ubuntu can both use. How do I do this?** So for example, music files in a Music directory can be played and edited both in Windows 7 and Ubuntu. Under Windows 7, I can specify the location of the following directories to anywhere on the hard drive: Documents, Pictures, Music, Video, Downloads, and maybe some others. And I believe Ubuntu is the same right? I don't want copies of these files separately generated between Windows and Ubuntu via syncing or importing. They should be the "same" files shared between both operating systems. The size of this partition would simply be all the available remaining hard drive space that remains.
 
 If someone could instruct me what I need to know and do to create this "personal files" partition, I would greatly appreciate it.[/QUOTE]

You can mount those Windows folders in the filesystem in your home folder something like, /home/<username>/Music or you could mount somewhere else and symlink to them.

This should help with "mounting":
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
 
[QUOTE=jmine83] - Random Freezing -[/QUOTE]

This might have to wait for someone with that hardware for a definitive answer.

If it isn't getting hot and random freezing you might want to verify that the correct video driver is being used.

You might look through the log dmesg to see if any failure of a driver is noted.

Pipe the output of the command dmesg through more, dmesg|more.

---

### Post by gsmanners on 2009-12-24
About the random freezing: Were you using the nVidia driver or were you using the default driver that comes with Ubuntu? There are a few things (like fan settings) that nVidia likes to trigger in their driver that aren't supported in the Xorg driver.

For swap, you only need as much space as you have physical RAM, and only if you plan to use the Hibernate function. Otherwise, I would limit the size of that to under 1 GB.

Unless you have a specific format (Reiser or XFS or something like that) there's no need to make seperate partitions for the other parts of a Linux system. I would just use ext4 and one partition for everything.

---

### Post by jmine83 on 2009-12-28
First of all, I want to express my gratitude and thankfulness for the technical insights and direction I received from all your responses. I played around a bit more with custom installing Ubuntu while following the directions I have received from this thread. I am happy to report that Ubuntu appears to be working smoothly on simply one Ubuntu system partition that I specified to be 10 GB in size.
 
As for the random freezing, however, ...
 
I am happy to report that at the very least, I believe I have isolated the source cause of the random freezing. The source of the problem being, my wireless network adapter or some sort of related network function. What I found was that as soon as I was able to successfully connect to the Internet with WiFi, the system would consistently freeze when connected to the Internet. Before, I did not think to simply turn off the wireless network adapter, and when I did turn it off, the system was perfectly stable for prolonged periods of time.
 
So now the concern becomes, how can I operate the Ubuntu operating system under stable conditions while connected to the Internet? Is my particular piece of wireless netwok adapter hardware not supported by Ubuntu?
 
My wireless network adapter hardware: Atheros AR928X Wireless Network Adapter.
 
A Google seach reveals that the official Atheros company site does not have a support section for downloading drivers or software. But I did find the following site:
 
[http://www.atheros.cz/](http://www.atheros.cz/)
 
The site mentioned does carry a Linux driver for my particular wireless network hardware, which then forwards me to a program called MADWIFI (madwifi-0.9.4.tar.gz). I am about to try this program out and see if it fixes the freezing, but before I do, I would like any insight to see if other people agree or not if this MADWIFI program will fix my problem or not.

---

