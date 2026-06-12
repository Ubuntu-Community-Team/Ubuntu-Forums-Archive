---
title: "Adobe reader Installation"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by BioVirtual on 2009-12-18
I downloaded Adobe Reader form Adobe site as a .bin file how to install it? I don't want to use any other software or similar ... 

Thanks,

---

### Post by Darce on 2009-12-18
DAMN quick ! Self serve ?  :lolflag:

---

### Post by NESFreak on 2009-12-18
[http://www.ubuntugeek.com/install-acrobat-reader-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/install-acrobat-reader-in-ubuntu-9-10-karmic.html)

---

### Post by unmole on 2009-12-18
Just out of curiosity....Why do you want to install adobe reader when you already have envince. If I remember correctly, the adobe reader for Linux was a serious resource hog ad was quite buggy.

---

### Post by BioVirtual on 2009-12-18
independency! :guitar:   :wink:

[http://blogs.adobe.com/acroread/2009/05/installer_formats_for_adobe_re.html](http://blogs.adobe.com/acroread/2009/05/installer_formats_for_adobe_re.html)

---

### Post by philinux on 2009-12-18
> **unmole said:**
> Just out of curiosity....Why do you want to install adobe reader when you already have envince. If I remember correctly, the adobe reader for Linux was a serious resource hog ad was quite buggy.

Someone might want to because...

1. Evince has no firefox plugin.

2. It cant handle large/complicated pdf's very well.

3. Adobe reader 9 is pretty solid and the memory leak thing has been fixed for ages and it comes with a FF plugin.

4. It can handle all pdfs

---

### Post by unmole on 2009-12-18
> **philinux said:**
> Someone might want to because...

1. Evince has no firefox plugin.

2. It cant handle large/complicated pdf's very well.

3. Adobe reader 9 is pretty solid and the memory leak thing has been fixed for ages and it comes with a FF plugin.

4. It can handle all pdfs

Oh well. I stand corrected then. But I have been using envince to load really large files without any glitches and I'm standing by it. :guitar:

[CENTER][U]In the end Linux is supposed to be about choices right ?
[/U][/CENTER]

---

### Post by BioVirtual on 2009-12-18
Yeah, and it's about not to be prejudiced. Be open as the source is! When something is better, well it's better!

---

### Post by lavinog on 2009-12-18
You should be able to install it from synaptic.  You just need to enable the multiverse repos.  This way you get the updates when they come out.

---

### Post by mrboojive on 2009-12-18
> **lavinog said:**
> You should be able to install it from synaptic.  You just need to enable the multiverse repos.  This way you get the updates when they come out.

Yes, installing from Synaptic is the best way to go. Acrobat Reader is actually in the partner repo though.

---

### Post by BioVirtual on 2009-12-18
What is "multiverse repos" ?!

---

### Post by joes7 on 2009-12-18
Applications->Add/Remove-> search for 'adobe reader'

---

### Post by lavinog on 2009-12-19
> **mrboojive said:**
> Yes, installing from Synaptic is the best way to go. Acrobat Reader is actually in the partner repo though.

my mistake.
Does anyone know the apt url line to add the partner repo?

---

### Post by lavinog on 2009-12-19
> **BioVirtual said:**
> What is "multiverse repos" ?!

[What are Repositories?](https://help.ubuntu.com/community/Repositories/Ubuntu)

enable the partner repository
System>Admin>Software Sources>Other Software (Tab)
enable [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
(assuming you are using karmic)
click ok, then reload on next dialog

then install acroread
[click here to install acroread](apt:acroread)

---

