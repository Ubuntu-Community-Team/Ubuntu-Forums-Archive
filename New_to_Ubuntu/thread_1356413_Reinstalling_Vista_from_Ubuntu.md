---
title: "Reinstalling Vista from Ubuntu"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by denn!s on 2009-12-16
Hello, I have a Dell Inspiron 1545 with the Karmic Koala edition of Ubuntu installed.  I dislike the operating system due to incompatibility issues.  So I've decided to reinstall Windows Vista that was issued with my laptop.  I've tried to perform a clean install but the drives were incompatible as Ubuntu reformatted them.  So my question is, how do I fix this format issue and reinstall Vista?  Will I have any other reinstall issues?  I have little experience, so careful instruction would be appreciated.  Many thanks, and Happy Holidays.
                                                                                                 ~Dennis

---

### Post by 3rdalbum on 2009-12-16
What incompatibility issues are you talking about? I notice this is your first post - maybe we can answer your underlying problem if you ask.

Vista's partitioner should be able to see your hard disk as a hard disk and reformat it, regardless of the filesystem on it.

If it doesn't, then you may need to format it yourself using Gparted on the Ubuntu live CD. Format it to NTFS.

If this doesn't work, then you might need to load SATA drivers into the Windows installer so it can recognise your SATA chipset and see your hard disk. This procedure is beyond the scope of this forum. (not to mention, completely untested by myself).

---

### Post by steveneddy on 2009-12-16
I agree that the Vista CD should format your drives correctly. Watch the Windows installer closely and choose the reformat drives option when it appears.

What was incompatible about Karmic?

Did you try any earlier versions like Intrepid 8.10?

---

### Post by Cuco3 on 2009-12-16
nvm

---

### Post by denn!s on 2009-12-16
Thanks for the responses, though I haven't had success with the advice. I tried to once again reinstall Vista, but the boot cd requires the partitioned drives to be formatted as NTFS. The problem is that the reformat option does not work, as I recieve the error message 0x80004005.
 
The compability issues that I earlier spoke of, were that of Ubuntu not playing DVDs, youtube videos, netflix streaming videos, etc. There was a lot of issues with just basic usage. I understand that these issues could be fixed with plugins, but I really don't want to get involved in all of that work.
 
So, again thanks for the responses and happy holidays. I will look into the SATA driver solution. but if anyone has any other ideas, please post with solutions.
 
~Dennis

---

### Post by houseworkshy on 2009-12-16
I'm in a similar position.   The problem for me is that my system won't boot from the vista cd or the mother board driver cd even though it will boot from any linux distro I've tried.

---

### Post by llawwehttam on 2009-12-16
I don't know what you mean by 'it won't play dvd's, youtube videos or netflix streaming videos'  Mine plays music, dvds, games and pretty much everything windows does. 

if you've just installed it and expect it to do everything instantly your expecting a bit muc. Even windows need codecs installed to watch dvd's and you need to install the adobe-flash plugin in windows too so why are you complaining so much? Try opening the add/remove programs menu and installing the package  ubuntu-restricted-extras than packages such as ffmpeg which you will need to play music. 

You will need to install libdvdread and libdvdcss for dvd's to play just as you need to install codecs in windows.

This might getyou to play dvd's and similar. 
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

You will still need to go to add/remove programs and search for 'codecs' and install the relevent packages.

These are all in the documentation for ubuntu so if you haven't read this then please do before you give up.


If you really are giving up completely to format the drive to NTFS boot from the ubuntu live disk, go to system>Administration>Partitioner  and delete all partitions and then create a new NTFS one that covers the drive. You have to press the start button or similar or it does nothing.

---

### Post by mastablasta on 2009-12-16
> **denn!s said:**
> 
The compability issues that I earlier spoke of, were that of Ubuntu not playing DVDs, youtube videos, netflix streaming videos, etc. There was a lot of issues with just basic usage. I understand that these issues could be fixed with plugins, but I really don't want to get involved in all of that work.
 
 
~Dennis
 
Those are not incompatibilities. You just need to install the necessary programmes and codecs.
 
You can try Linux Mint 8 - it's based on ubuntu and it has all these things already preisntalled for you (try a live CD first). Though it does look a bit different than Ubuntu and has a couple of things done differently (to me a bit less intuitive). Anyway i tried the Mint live CD on my computer and can watch you tube there, also tried some movies...
 
The real incomaptibility of Linux is that for example that i can not use it in E-banking or E-administration, because both of these require MS windows for processing (one uses some ecryption that only Windows can read, the other one uses ActiveX and needs IE 7 or 8).

---

### Post by denn!s on 2009-12-16
So, thanks for all the great advice.  I've reviewed some of what has been said, and I realized that reinstalling Vista wasn't really necessary.  While Netflix doesn't support Ubuntu, I can now view youtube, and with the right "codecs" I should be able to watch DVD's.  Again, thanks for all the help, though some posts seemed rather judgemental.  Happy Holidays.

~Dennis

---

