---
title: "segmentation faults all over the place"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by Runtime.Tech on 2008-12-15
He folks - thanks so much for all you contributions to us newbies!

I'm having a hard time with my Ubuntu 8.04 build. Ubuntu runs great, but about since I upgraded from 7.something I've been getting segmentation faults all over the place. Thanks to some previous thread writers for that piece of knowledge, btw. 

I'm getting frustrated ... I really don't know much about the inner workings of this whole thing and I could use a little direction. I've heard tell through a thread that my RAM could be damaged and causing this problem? I'm going to test that now. Any other suggestions or understanding would be greatly appreciated! Thank you.

---

### Post by Ender41 on 2008-12-15
> **Runtime.Tech said:**
> He folks - thanks so much for all you contributions to us newbies!

I'm having a hard time with my Ubuntu 8.04 build. Ubuntu runs great, but about since I upgraded from 7.something I've been getting segmentation faults all over the place. Thanks to some previous thread writers for that piece of knowledge, btw. 

I'm getting frustrated ... I really don't know much about the inner workings of this whole thing and I could use a little direction. I've heard tell through a thread that my RAM could be damaged and causing this problem? I'm going to test that now. Any other suggestions or understanding would be greatly appreciated! Thank you.

  Segfaults are caused by an app trying to access a memory area that doesn't exist or it doesn't have permission to. So yes it could be ram it could also be the hdd swap area.

This article gives a good idea of what a segfault is

[http://linuxpoison.blogspot.com/2007/12/what-is-segmentation-fault.html](http://linuxpoison.blogspot.com/2007/12/what-is-segmentation-fault.html)

Ender

---

### Post by Runtime.Tech on 2008-12-16
Thanks Ender, that does help further my understanding. I've checked me memory with metest86+ to find no errors. HDD swap area? meaning: faulty HDD sectors in swap area? 

This segfault problem started with one program (QDevelop) quiting very consistantly. Now SCREEM is hopping out on me all the time, too. ANy ideas how I could check my swap area?

---

### Post by Runtime.Tech on 2008-12-16
update: checked my swap area and saw priority was set to -3 ... found out that was bad, set to 0.

---

### Post by Runtime.Tech on 2008-12-17
I'm still losing a ton of productivity to these seg faults ... checked my RAM, OK - checked what I could for my swap area, OK. Now I'm really not sure what to do. Any suggestions would be greatly appreciated. Thank you.

---

### Post by Runtime.Tech on 2008-12-17
Screem seg faults with this output:

joshua@Martin:~$ screem

(screem:9061): Gtk-WARNING **: Refusing to add non-unique action 'cancel drag' to action group 'ScreemActions'

(screem:9061): screem-CRITICAL **: screem_page_is_feature: assertion `SCREEM_IS_PAGE( page )' failed

(screem:9061): screem-CRITICAL **: screem_page_is_xml: assertion `SCREEM_IS_PAGE( page )' failed

(screem:9061): Gtk-CRITICAL **: gtk_window_resize: assertion `width > 0' failed
parsing error: 127:1:could not recognize next production
parsing error: 127:1:could not recognize next production
Segmentation fault

qdevelop seg faults with this output:

joshua@Martin:~$ qdevelop
Segmentation fault

Thank you for your help .....

---

### Post by starcannon on 2008-12-17
I would recommend booting from the liveCD and reformatting the swap partition; at least this is where I would start, it only takes a few minutes. If this did not fix the problem then I would download the hard disk drive manufactures diagnostics utility from there website and run a full diagnostic on the hard disk drive.

You will likely need a DOS boot disk for most of these:
[Free DOS boot disk]("http://www.bootdisk.com/bootdisk.htm")
[Seagate]("http://www.seagate.com/www/en-us/support/downloads/seatools/")
[Maxtor]("http://www.maxtor.com/en/main/support.html")
[Western Digital]("http://support.wdc.com/product/download.asp")
[Samsung]("http://www.samsung.com/us/support/download/supportDownMain.do?group=computersperipherals&type=harddiskdrives&subtype=&model_nm=&prd_ia_cd=&disp_nm=&vType=R")
[IBM]("http://www.ibm.com/support/in/en/")
[Fujitsu]("http://www.fujitsu.com/global/support/")

Heres a better list of Software Links for fixing/repairing hard disks errors:
[http://www.tacktech.com/display.cfm?ttid=287](http://www.tacktech.com/display.cfm?ttid=287)

Some of the OEM disk management software will require windows to run. In those cases I would recommend pulling the drive and slaving it in a windows machine if that option is available, and then running the software.

GL and be sure to back up important data asap.

---

