---
title: "HDD partition corruption? /  gets stuck on GRUB &quot;Error 25&quot;"
date: 2011-04-13
forum: New to Ubuntu
---

### Post by greenewbie on 2011-04-13
My HDD using Lucid 10.04 (referred to as **HIT HDD1** from now on, to distinguish it from a backup HDD which is working fine on the SAME computer) refuses to boot up: it gets stuck at the GRUB loading stage; I've restarted it on dozens of occasions and each time I get:
[COLOR=#0000ff]“[/COLOR][COLOR=#0000ff][I]GRUB Loading stage1.5. 
GRUB loading, please wait...
Error 25”[/I][/COLOR]

I don't know if it was a coincidence but my HIT HDD1 (most unusually) crashed within seconds of my automatic Update Manager coming through, telling me there were updates to make (which I didn't have chance to do).
I made several postings in the **HOWTO: Purge and Reinstall Grub 2 from the Live CD thread. Here are their** **links:**
[**http://ubuntuforums.org/showthread.php?t=1581099&page=10**]("http://ubuntuforums.org/showthread.php?t=1581099&page=10")

[**http://ubuntuforums.org/showthread.php?t=1581099&page=15**]("http://ubuntuforums.org/showthread.php?t=1581099&page=15")

However,**drs305 **(a Forum Staff member), believes that the problem arises from the partition s**etup **rather than a Grub problem. 

> **drs305 said:**
> greenewbie,

I don't think you are having a grub problem. Your system is having a  problem reading the partitions. There is corruption of some sort, and  the files aren't being read. It could be the filesystem, partition  table, or something else. 

The mount command normally wouldn't require you to add the file type for  a linux partition, which just further confirms the problem (unless sda1  isn't a linux partition and you are trying to mount a non-linux  partition).

I am not an expert on recovery issues. Since your post is in the Grub2  thread there's a good chance that those who are will not see it.

You might start a new thread in Absolute Beginners or General and  explain what's happening. You might get help that will restore your  current setup. Best of luck either way.

And there does indeed seem to be something odd going on, detailed below, which I'm hoping you guys can help me with. [SIZE=2][COLOR=DarkOrchid]I'm a complete tech-dummy so I apologise for any of my layman's language below not expressed in Linux Lingo![/COLOR][/SIZE]

In my latest efforts, I've used the Ubuntu Secured Remix 10.10 Live CD (as recommended by [YannBuntu]("http://ubuntuforums.org/member.php?u=485559") in the above thread) to give access to my problem **HIT HDD1**, the ONLY HDD connected up at this point. [COLOR=#ff0000]Although there are several partitions on HIT HDD1, they are ALL Ubuntu and this HDD has NEVER, EVER had anything other than Ubuntu on it, NOT Windows NOR any other OE. [/COLOR]My HIT HDD1 is worth the trouble saving, I think, [COLOR=#000000]as it's less than two years old. Perhaps it's important to mention at this point that I've never defragmented HIT HDD1 (as it's never had Windows on it), as I've never heard anything about defragmenting Linux disks. So I'd like to check with you guys right now that you don't or can't defragment Linux disks? (I've been meaning to pose this question for several years now!).[/COLOR]

So I opened the [COLOR=#ff6309]“[/COLOR][COLOR=#ff6309]**Boot Repair”**[/COLOR] tool (in the System menu of my Live CD) and the dialog box said: “[COLOR=#0000ff]Error: No OS have been found on this computer”[/COLOR]! WHY?! 

I then opened the [COLOR=#ff6309]“[/COLOR][COLOR=#ff6309]**disk utility”**[/COLOR] application for a partition analysis of HIT HDD1. You can see from the screenshot attached below that the [COLOR=#ff6309]“[/COLOR][COLOR=#ff6309]**SMART Status”**[/COLOR] (which I don't really understand) stipulates that [COLOR=#ff0000][SIZE=4]the disk has a few bad sectors [/SIZE][/COLOR](ie written next to the green dot).

  [COLOR=#2e8b57]_Attachment_: Shot Disk Utility HIT HDD1 Free Partition.png[/COLOR]

You can also see that the first partition highlighted in orange above ( 100 GB labelled as being [COLOR=#0000ff]“Free”[/COLOR]) gives ONLY the following information:

**USAGE**  [COLOR=#0000ff]Unallocated space[/COLOR]             **DEVICE **[COLOR=#0000ff]/dev/sda               [/COLOR]**CAPACITY**                                                           [COLOR=#0000ff]100 GB[/COLOR]
                                                                               
                                                               In this partition above, **PARTITION TYPE** is blank (other than the hyphen [COLOR=#0000ff]**- **[/COLOR]) and “**Type”** is totally omitted in the information, [COLOR=#ff0000]in contrast to[/COLOR] the other (logical) partitions listed below (ie under the 220 GB Extended [COLOR=#ff0000](/dev/sda2)[/COLOR] bar) under the next screenshot, of /dev/sda2 highlighted in orange:

 [COLOR=#2e8b57]_Attachment_: [/COLOR][COLOR=#2e8b57]Shot Disk Utility HIT HDD1 Extended Partition.png
[/COLOR]
I clicked in turn on each of the logical partitions (ie all four of them as appearing in the chart above) and noted all the information in the table I've made below:

[COLOR=SeaGreen][I](Sorry, I can't get this data below to line up correctly in columns.  So I'm going to have to send it in another post to this thread as an attachment (I've already used my limit of 5), I adjust it and then it just reverts back to how you see it)
[/I][/COLOR]
**PARTITION name     USAGE**            **PARTITION TYPE            **    **TYPE                    **                       **DEVICE**                 **CAPACITY**
**(as per table)**


[COLOR=#0000ff]“100 GB Ext3”                Filesystem              Linux (0 × 83)                   Ext3 (version 1.0)            /dev/sda6                       100 GB[/COLOR]
[COLOR=#0000ff]“60 GB Ext3”                     Filesystem              Linux (0 × 83)                   Ext3 (version 1.0)             /dev/sda7                       60 GB[/COLOR]
[COLOR=#0000ff]“59 GB Ext3”                     Filesystem             Linux (0 × 83)                    Ext3 (version 1.0)            /dev/sda8                       59 GB[/COLOR]
[COLOR=#0000ff]“1.2 GB Swap”               Swap Space        Linux Swap (0 × 82)      [/COLOR](heading omitted)[COLOR=#0000ff]             /dev/sda5                     1.2 GB[/COLOR]

To finish off here: sda6, sda7 and sda8 say [COLOR=#ff0000]“NOT MOUNTED”[/COLOR] under the entry [COLOR=#0000ff]“Mount Point”[/COLOR]; whilst sda5 the swap partition doesn't show that information.

[SIZE=4]_**Some big queries: **_[/SIZE]

Does device [COLOR=#ff0000]/dev/sda[/COLOR] labelled as such in the first screenshot above perhaps mean [COLOR=#ff0000]**/dev/sda1**[/COLOR]? 
Do you think that I have all my stuff and programs saved in [COLOR=#ff0000]/dev/sda1[/COLOR]? (NB **I've never used any of the other partitions,** this was for a future project and BTW nobody else uses my computer).
Is the reason why I can't boot up my HIT HDD1 because sda or sda1 [COLOR=#ff0000]isn't mounted?[/COLOR] Here I'm confused because as I've already pointed out above, the first 100GB partition (labelled as being [COLOR=#0000ff]“Free” [/COLOR]and having [COLOR=#0000ff]“unallocated usage”[/COLOR]in the first screenshot) simply [COLOR=#ff0000]doesn't give any information about the mounting[/COLOR].

My confusion concerning /dev/sda1 deepens when I compare the results above with the following screenshots of:
    - first, the **sudo fdisk -l **command entered into a Terminal. [COLOR=#ff0000]Here sda1 is clearly listed, with the boot asterisk next to it:[/COLOR]

 [COLOR=#2e8b57]_Attachment_: [/COLOR][COLOR=#2e8b57]Shot sudo fdisk -l HIT HDD1[/COLOR].[COLOR=SeaGreen]png[/COLOR] 

    - second, just for comparison purposes, a disk utility analysis of an entirely separate, backup HDD (it's most annoying, this tiny 6.4 GB one has been in use for donkey's years but apparently still going strong!). In contrast to HIT HDD1, this one clearly labels [COLOR=#ff0000]/dev/sda1[/COLOR] in the first partition in the table and shows the mount point as being MOUNTED AT[COLOR=#ff0000]**/ **[/COLOR]. [COLOR=#ff0000]The root slash [/COLOR][COLOR=#ff0000]**/ **[/COLOR][COLOR=#ff0000]is completely missing in the analysis of HIT HDD1[/COLOR].

 [COLOR=#2e8b57]_Attachment_: [/COLOR][COLOR=#2e8b57]Screenshot Disc Utility partitions SEA HDD2.png[/COLOR]

[SIZE=4]_**OTHER OBSERVATIONS ON USING “DISK UTILITY” PROGRAM on HIT HDD1**_[/SIZE]

- I mounted [COLOR=#ff0000]sda6[/COLOR] and restarted my computer, several times, (I thought maybe my stuff has got moved to a different partition or something) but no, I got the same Grub loading problem as before.

- I did individual [COLOR=#0000ff]“File system checks”[/COLOR] on sda6, sda7 and sda8 which all reported as [COLOR=#0000ff]“Clean”[/COLOR]. This option wasn't available for the first partition (sda or sda1 whichever it is), so is this evidence that it's got nothing on it?
- I clicked on [COLOR=#0000ff]“View Smart Data & runself-tests”[/COLOR]. The “SMART” data in the screenshot attached below shows that HIT HDD1 has [COLOR=#0000ff]**3 “bad sectors”**[/COLOR]. Of the **17** ID / attributes appearing in the results of this test, **seven** were assessed as [COLOR=#0000ff]GOOD[/COLOR]; **nine **as [COLOR=#0000ff]N/A[/COLOR] and **one** with the **ID197** [COLOR=#ff0000][SIZE=4]warning[/SIZE][/COLOR] highlighted below.

 [COLOR=#2e8b57]_Attachment_: [/COLOR][COLOR=#2e8b57]Shot Disk Utility HIT HDD1 Warning Data.png[/COLOR]

- I then clicked on the [COLOR=#0000ff]“Run self-test – check the disk surface for errors”[/COLOR] tool (selecting the [COLOR=#0000ff]“Extended”[/COLOR] option). Unfortunately this self-test seems to get stuck, I suspect on the [COLOR=#0000ff]“Current Pending Sector Count”[/COLOR] in orange above, as the progress bar (in the top right hand corner) stops a few millimetres (so to speak!) before the end of this bar. This self-test doesn't seem to detect anything, even when left in its “stuck position” for 12 hours!

- I clicked on [COLOR=#0000ff]“ Read Benchmark”[/COLOR] (to measure the drive performance) but it failed, the details saying:
[COLOR=#0000ff]“Error benchmarking: helper exited with exit code 1: Error reading 104857600 bytes at 104857600 from /dev/sda when guesstimating buffer size: Input/output error ”[/COLOR]

In short I'm wondering if there's a quick solution to this boot-up problem! If you guys think it would be too complicated for a novice, am I right in thinking that a fresh install would automatically correct the problem? Or do you think that there really is a hardware problem with the disk itself? :confused:

And as an aside, (looking at the technical details in the fdisk -l screenshot above etc), do you think my Hitachi HDD1 is really obsolete for sound transmission on Skype (video transmission is less important to me)? I mention this as I'll shortly be writing posts on my frustration at not being able to get it to work properly on Ubuntu.
Many thanks in advance for any help!

---

### Post by greenewbie on 2011-04-13
Things didn't go according to plan in my first post above.  I wrote everything in a text document, then planned to paste it all in my post.  But it wouldn't take the screenshots and doesn't like lining things up in columns!  As I've gone beyond my limit of 5 attachments,  for good measure I attach the spreadsheet showing the logical partitions of my HIT HDD1 (that appear in my first post above but just refuse to line up!)

Thanks again for any help!

---

### Post by Hedgehog1 on 2011-04-14
greenewbie,

Now THAT is a post!  Wow!

First, a reality check:  The HIT HDD1 with 'a few bad sectors' will begin to get more bad sectors and eventually fail on you.  So 'saving' the drive itself is not advised. Saving the data from the drive is a worthwhile exercise ***if you do not already have it backed up elsewhere***.

Also - where those 'few bad sectors' are located can be critical even now.  If they happen in areas that cannot be re-located, things are toast.

I know 2 years is not as long as the drive should last, but the reality is that Hard Drives are consumables.  I have had them fail in 10 months of heavy use, or last 8 years of heavy use.  I buy the best to make them last longer, but I work them hard.

So - is there data you don't have backup up on HIT HDD1?  If so an attempt to get that data off the drive and on to another one can be made.

In any case, you are going to be buying a new drive shortly.  


***The Hedge***

:KS

---

### Post by K_45 on 2011-04-14
You should get a medal for that post! Your HDD is dying. To confirm, run Hitachi's DFT test:  [http://www.hitachigst.com/support/downloads/](http://www.hitachigst.com/support/downloads/)  You want the Drive Fitness Test test .iso. Boot from it. I expect your HDD to fail those tests. It seems that those sectors broke sda1.

---

### Post by greenewbie on 2011-05-18
> **K_45 said:**
> You should get a medal for that post! Your HDD is dying. To confirm, run Hitachi's DFT test:  [http://www.hitachigst.com/support/downloads/](http://www.hitachigst.com/support/downloads/)  You want the Drive Fitness Test test .iso. Boot from it. I expect your HDD to fail those tests. It seems that those sectors broke sda1.

> **Hedgehog1 said:**
> greenewbie,

Now THAT is a post!  Wow!

First, a reality check:  The HIT HDD1 with 'a few bad sectors' will  begin to get more bad sectors and eventually fail on you.  So 'saving'  the drive itself is not advised. Saving the data from the drive is a  worthwhile exercise ***if you do not already have it backed up elsewhere***.

Also - where those 'few bad sectors' are located can be critical even  now.  If they happen in areas that cannot be re-located, things are  toast.

I know 2 years is not as long as the drive should last, but the reality  is that Hard Drives are consumables.  I have had them fail in 10 months  of heavy use, or last 8 years of heavy use.  I buy the best to make them  last longer, but I work them hard.
***The Hedge***

:KS

Thanks very much for your help guys......BTW when I've got something in my sights I don't take prisoners! :)
I'm DELIGHTED to tell you that my HDD seems to have made a full recovery and has been behaving impeccably for a month, since I did the Hitachi [COLOR=#0000ff]“Drive Fitness Test”[/COLOR], That was a GREAT tip of yours, thanks again** K_45**! I ran the test from the file burnt on to a CD (NB in the instructions on this site, they appear to stipulate that you MUST do the test via a floppy disk; if so, this isn't true, a CD is fine (I tried but it seems that my floppy drive is now dead!). The  test told me that my HDD was fine.  So I then installed 10.10 Maverick; In the Disk Utility I did the [COLOR=#0000ff]“[/COLOR][COLOR=#0000ff]Run [/COLOR][COLOR=#0000ff]self-test –[/COLOR][COLOR=#0000ff] check the disk surface for errors[/COLOR][COLOR=#0000ff]”[/COLOR] again (selecting the [COLOR=#0000ff]“Extended”[/COLOR] option).  The self-test said it had “completed OK” and the disk is [COLOR=#ff0000]HEALTHY[/COLOR].
 I've done this several times over the last month and so I'm going to keep my fingers crossed my HDD continues to behave!


I'm so enthralled by this Drive Fitness Test, I'm going to shortly try to do the same on another old HDD if I can find the equivalent: the label on it says it's an IBM Deskstar. I'll report back on that.


:guitar:

---

