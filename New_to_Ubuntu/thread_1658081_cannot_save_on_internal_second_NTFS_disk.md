---
title: "cannot save on internal second NTFS disk"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by grimpeur on 2011-01-02
Hi I am using Ubuntu since a couple of years as a basic user.
 

 My PC is equipped with a second internal HD, NTFS partition, where I store data only (ubuntu and Win are installed in another HD). With Ubuntu 8.04 LTS I used to save fles in the second HD without problems. **Now with Ubuntu 10.04 I am compelled to save files on the desktop and then moving them to the NTFS disk**.
 

 In detail:
 

 - by saving MHT, JPEG or PDF on NTFS disk, I find there empty files and I get a message like that (translated from italian) “you do not have permission to write to this file” or “impossibile to save the file” or “...cannot be saved as you are not allowed to modify the content in the destination folder”
- Openoffice Write saved in the NTFS disk ODT files but not DOC
- Openoffice Calc saves in the NTFS disk XLS files without problems
- Openoffice presentations are saved in NTFS either PPT or ODP

On preferences menu disk settings seem OK (writing cache enabled). Hereattached screenshot from disk manager menu, if useful
[http://img94.imageshack.us/img94/6818/schermatadiscofissoda32.png](http://img94.imageshack.us/img94/6818/schermatadiscofissoda32.png)
 

 Which may be the reason? Please simple instruction, I am not so skilled and I am not english native
 

 many thanks.

---

### Post by kimberlite on 2011-01-02
Try to use "ntfs-config" tool. You can install it via synaptic package manager or from a terminal window by issuing the following command:

```
sudo apt-get install ntfs-config
```

After that you can use it from "System -> Admin -> NTFS-config tool" menu. Make sure that at the "Advanced Configuration" tab the writeable option is selected. Also "Enable write support for internal device" should be enabled. Cheers.

---

### Post by grimpeur on 2011-01-02
Thanks, I thought the my NTFS conf. tool was OK, but probably not  

[[IMG]http://img225.imageshack.us/img225/1650/schermatastrumentodicon.png[/IMG]]("http://img225.imageshack.us/i/schermatastrumentodicon.png/")

Now I can save also DOC, then all Openoffice files are OK

I still have problems with

- MHT, but probably it depends on an add-on I have, i.e. unMHT. 
- PDF, when they are opened on the browser and I try to save them, I receive a message "you do not have permission to write to this file". They are not protected, as I manage to save in the desktop

---

### Post by coffeecat on 2011-01-02
NTFS, being a Microsoft filesystem, does not support the Linux system of permissions and ownership. Permissions are set globally for all files when the filesystem is mounted. So it is strange that you have problems with some types of files and not with others.

The program ntfs-config was a good idea but has not been maintained and can do some unfortunate things sometimes. It will have set your mount options in /etc/fstab so please post the contents of /etc/fstab so we can see what those options are. Please post the contents of fstab in [noparse]```

```[/noparse] tags for clarity.

Had you already used ntfs-config for setting up your NTFS partitions, or did you do this only after kimberlite suggested it?

---

### Post by grimpeur on 2011-01-02
[COLOR=DarkSlateGray]Yes, before asking help on the forum I checked everything whihc may seem a disk manager and in NTFS partition manager flags for writing were enabled. After kimberlite's suggestion I included also sda1 (not necessary) and pressed OK. Now Doc file is allowed, I don't know why as data disk is sdb1, but it works. MHT and PDF still not 


I opened the file fstab in etc and this is the content..I don't know if it is what you need[/COLOR]  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    defaults    0    0
#Entry for /dev/sda4 :
UUID=92ad3b14-650b-44f7-890a-b0b97c4d4f2e    /    ext3    relatime,errors=remount-ro    0    1
#Entry for /dev/sda2 :
UUID=e057cc85-c37f-408d-8ae4-dd5db292c5e9    /boot    ext3    relatime    0    2
#Entry for /dev/sdb1 :
UUID=4FF9089B4F7C352C    /media/disco-dati    ntfs-3g    defaults,locale=it_IT.utf8    0    0
#Entry for /dev/sda1 :
UUID=3E60BD1F60BCDF39    /media/sda1    ntfs-3g    defaults,locale=it_IT.utf8    0    0
#Entry for /dev/sda3 :
UUID=ea40adcf-e9da-4f5a-80f0-735e8ee2a00c    none    swap    sw    0    0
/dev/scd0    /media/cdrom0    udf,iso9660    user,noauto,exec,utf8    0    0
/dev/fd0    /media/floppy0    auto    rw,user,noauto,exec,utf8    0    0

---

### Post by coffeecat on 2011-01-02
Your mount options look OK, so if you are still having problems with saving certain types of files you will have to look at the particular application or the file itself. You say you can save a pdf to the desktop but not to sdb1? At the moment I can't think of any reason why that should be.

---

### Post by pharbar on 2011-01-07
Hi, I occasionally experience exactly the same problem when clicking a link to download a .pdf from certain websites. Instead of downloading, it opens in a new (Firefox) browser tab, from where I can ONLY save it to my home partition, NOT to my NTFS partitions. My permissions are correct, I believe, and I also have ntfs-config installed which seems to be set right.

I am guessing that it might be a Firefox issue (a browser issue, anyway). In Firefox, I discovered that under 'Preferences/Applications', there are two entries for 'PDF document':

PDF document (application/asp-unknown), set to "Save file" (which behaves as expected)
PDF document (application/asp-pdf), set to "Use Adobe Reader 9.4 (in Firefox)" (behaves as expected, but is then unable to write file to NTFS)

Whatever the reason for the strange permissions error, a workaround in my case would seem to be to set the second type to another action: "Use Adobe Reader 9 (default)", "Always ask" or "Save file".

I cannot test it yet, since the government website I just had this problem with (always the same government site, problem occurring every 3 months) curiously insists on downloading as asked when I attempt to download the file a second time.

I would be interested to know if this solves the problem for you. It doesn't explain the permissions error, but it might get the job done. Personally, I hate pdfs opening in a browser window in any case!

Peter

Ubuntu 10.10
Firefox 3.6.13
Adobe Reader 9.4.1

---

### Post by grimpeur on 2011-08-10
Sorry I didn't check again the post and gave up... now, in holidays,  after a century, I am reconsidering this bug.

In Firefox' preferences I have several PDF applications listed as content types. The preset action is "always ask" for them all.

I fear there is another reason why I can save PDF only in homepage and not in the NTFS partition.

---

