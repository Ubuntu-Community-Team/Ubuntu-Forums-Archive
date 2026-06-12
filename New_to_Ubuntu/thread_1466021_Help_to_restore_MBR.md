---
title: "Help to restore MBR"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by kittyhawk63 on 2010-04-29
I have deleted all Ubuntu partitions, but the GRUB is still there. It does not see Ubuntu and I presume therefore it freezes. I can do a soft reboot (ctrl+alt+delete) but still end back at the frozen GRUB. Now I have to use Super GRUB to boot into Windows 7. I need to delete GRUB so that I can boot directly into Windows 7. I'm fairly sure that GRUB is in MBR. I have tried a number of suggestions offered on Windows 7 forum. I tried to do a system recovery from a Windows 7 oem disk. I got to the system recovery part but was warned that I needed to remove any USB devices. I had none plugged in. It would not let me continue doing the system recovery. So, I have no partitions for Ubuntu. I have tried system recovery but was stopped. Does anyone have a solution other than doing a fresh install of Windows 7? Below is a conversation carried on by me and someone on Windows 7 forum. My comments are in the **bold type**.

...Just give a brief description that you removed Ubuntu and  need to reload the MBR and post the script. The script is run from a  live cd even the 6.10 will work I believe it will put the text from the  script on the desktop. 
**What script are you referring to?** **Do  you mean commands typed onto the command line such as sudo apt-get?**
The  best way to do the script download is to get  the script on the desktop then use the command given on the bootscript  page to run it and save the script readout to a thumb or just go to the  forums on the CD to post it. 
**I'm not sure what you mean by script  download or bootscript page. I am lost at this point. Maybe, at your  suggestion, I will pick this up when I post on UbuntuForum.com.**
Make  sure you have that recovery disc  burned and you should be set.
**Should I do the recovery disk before  this problem is fixed or after it is fixed?**

**Sorry for my  ignorance. It has been over 10 years since I worked with Linux. I have  forgotten most of the things I knew when I lost all my short-term memory  during a long illness. I am back to normal, but what I did know, I have  to learn all over again.**

I hope someone here on Ubuntuforum.com can help me resolve this problem. Ignore the information about the computer below. That is not the computer I am needing help with.

---

### Post by stmiller on 2010-04-29
Boot the windows CD. Enter recovery mode to a windows console.

```

fixmbr c:
fixboot c:

```


[http://www.google.com/search?hl=en&q=restore+MBR](http://www.google.com/search?hl=en&q=restore+MBR)

---

### Post by kittyhawk63 on 2010-04-29
> **stmiller said:**
> Boot the windows CD. Enter recovery mode to a windows console.

```

fixmbr c:
fixboot c:

```
[http://www.google.com/search?hl=en&q=restore+MBR](http://www.google.com/search?hl=en&q=restore+MBR)

How do I get to the recovery mode so I can enter the commands?

---

### Post by oldfred on 2010-04-29
I think stmiller posted XP style commands, the one's for Vista and & are slightly different. This is a full set incase you need them, you should only need fixMBR.

Vista or 7 repair
Always run chkdsk and run again until there are no errors, that may be all that is required
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe

You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

---

### Post by tmx84 on 2010-04-29
This should help...

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html]("http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html")

---

### Post by kittyhawk63 on 2010-04-29
[QUOTE=oldfred;9198388]I think stmiller posted XP style commands, the one's for Vista and & are slightly different. This is a full set incase you need them, you should only need fixMBR.

Vista or 7 repair
Always run chkdsk and run again until there are no errors, that may be all that is required
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe

You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section.** Exactly when do I hit the "R"?** You can then select the automatic boot repair tool, but it often will not do any good. **You're right. It did nothing for me when I tried it earlier today.**Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd[

**I will write these commands on a piece of paper and use them after you have answered my last questions.** /QUOTE]

These commands worked. Thank you for your help oldfred. All is back to NORMAL.

---

### Post by wilee-nilee on 2010-04-29
> **oldfred said:**
> I think stmiller posted XP style commands, the one's for Vista and & are slightly different. This is a full set incase you need them, you should only need fixMBR.

Vista or 7 repair
Always run chkdsk and run again until there are no errors, that may be all that is required
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe

You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

Hello kittyhawk63 this is the exact person I was hoping you would run into.
wee

oldfred I don't think they have a installation disc it is a oem so I have given them a link to the recovery disc at neosmart. We were working on this at the windows 7 forums and getting well nowhere so I directed here.

---

### Post by kittyhawk63 on 2010-04-30
> **wilee-nilee said:**
> Hello kittyhawk63 this is the exact person I was hoping you would run into.
wee

oldfred I don't think they have a installation disc it is a oem so I have given them a link to the recovery disc at neosmart. We were working on this at the windows 7 forums and getting well nowhere so I directed here.


Hi wee. Glad you're here. I think since you have been on this with me, it will help oldfred. I have a full Windows 7 install disk. I got it today. I think I have referred to it as an oem by mistake. I also have Windows 7 on the computer. I can do a fresh install without a disk.

---

### Post by wilee-nilee on 2010-04-30
> **kittyhawk63 said:**
> Hi wee. Glad you're here. I think since you have been on this with me, it will help oldfred. I have a full Windows 7 install disk. I got it today.

Awesome, so oldfred knows in case it is needed kittyhawk63 is aware of the bootscript, I feel veklempt, carry on.

---

### Post by tmx84 on 2010-04-30
Check out the link i posted, it gives you a word for word on how to fix this, with pictures.  If you would rather use the commands oldfred has posted, than you can also just use the link to get to command prompt.. Which is just booting to the cd, selecting language, than select "Use recovery tools" then select command prompt.. Than you can either continue with the link, or use oldfreds commands, they should both work...

---

### Post by kittyhawk63 on 2010-04-30
> **wilee-nilee said:**
> Awesome, so oldfred knows in case it is needed kittyhawk63 is aware of the bootscript, I feel veklempt, carry on.

wee, if you're there, can you answer my questions that I asked oldfred. He did not come back to answer them. Look up about 6 post back.

---

### Post by kittyhawk63 on 2010-04-30
> **tmx84 said:**
> Check out the link i posted, it gives you a word for word on how to fix this, with pictures.  If you would rather use the commands oldfred has posted, than you can also just use the link to get to command prompt.. Which is just booting to the cd, selecting language, than select "Use recovery tools" then select command prompt.. Than you can either continue with the link, or use oldfreds commands, they should both work...
Thanks tmx84. I will look at the link. Maybe after I see it I will go with it, if I think it is easier to use. Thanks again.

---

### Post by wilee-nilee on 2010-04-30
carry on

---

### Post by kittyhawk63 on 2010-04-30
> **tmx84 said:**
> This should help...

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Great! Very understandable, too. Thanks.

---

### Post by oldfred on 2010-04-30
I only run XP and never had to repair Vista or 7. Both my link to microsoft and kittyhawk63's link to 7forums have a little more instruction. I think it was #10 in kittyhawk63's link show the screen to select command line (last on page).

You should only have to run this one command but I gave the entire list just in case.

BootRec.exe /FixBoot

If all this does not work wilee-nilee know about boot script so we can see what else may be a problem, but it is late here and will not be back on until tomorrow afternoon Chicago time.

---

### Post by kittyhawk63 on 2010-04-30
Thank you OldFred.  Your command line statements worked. I am now back to booting directly into Windows 7. I want to thank everyone here that has helped resolve my problem with GRUB. 

Thanks **wee** for all your help today. You kept me encouraged that I would find an answer. 

[I see I need to update my computer information.]

---

### Post by wilee-nilee on 2010-04-30
> **oldfred said:**
> I only run XP and never had to repair Vista or 7. Both my link to microsoft and kittyhawk63's link to 7forums have a little more instruction. I think it was #10 in kittyhawk63's link show the screen to select command line (last on page).

You should only have to run this one command but I gave the entire list just in case.

BootRec.exe /FixBoot

If all this does not work wilee-nilee know about boot script so we can see what else may be a problem, but it is late here and will not be back on until tomorrow afternoon Chicago time.

That is the command that always works for me, I have reloaded the MS and grub bootloaders multiple times and that always works. But I started with systems running correctly to begin with. Thanks everybody for help here.

---

### Post by Babuloseo on 2010-04-30
1) Insert Windows repair cd..then run the mbr fix command
2) Reinstall Windows,, just make sure you save all your important documents not in the C FOLDER

---

### Post by wilee-nilee on 2010-04-30
n

---

### Post by wilee-nilee on 2010-04-30
> **kittyhawk63 said:**
> Thank you OldFred.  Your command line statements worked. I am now back to booting directly into Windows 7. I want to thank everyone here that has helped resolve my problem with GRUB. 

Thanks **wee** for all your help today. You kept me encouraged that I would find an answer. 

[I see I need to update my computer information.]

Awesome, my work is done. ;)

---

### Post by kittyhawk63 on 2010-04-30
> **wilee-nilee said:**
> Awesome, my work is done. ;)

**Your work is never done. Now get back to work. lol**

---

### Post by wilee-nilee on 2010-04-30
> **kittyhawk63 said:**
> **Your work is never done. Now get back to work. lol**

Hey I just bow to the ones who know like oldfred, and several others, I am not worthy, I am not worthy.

---

