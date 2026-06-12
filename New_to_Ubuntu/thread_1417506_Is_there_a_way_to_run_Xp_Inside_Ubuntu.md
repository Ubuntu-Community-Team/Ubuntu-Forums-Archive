---
title: "Is there a way to run Xp Inside Ubuntu?"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by Joe_Ib on 2010-02-27
Hi I was just curious on how someone might go about running Xp inside Ubuntu (if possible).

---

### Post by spiderbatdad on 2010-02-27
virtualbox or vmware
you will need an xp installation cd and valid product key.

---

### Post by Vaphell on 2010-02-27
some flavor of virtual machine software, virtualbox being one of them. There is open source version in repos but version downloaded from its website has more features.

it creates a file which is an image of system partition, you install xp on it just like on real hardware.
You install few addons that make experience more pleasant (integration with ubuntu desktop, etc)
any time you want to run xp you launch virtualbox, select XP image to run, voila.

---

### Post by s.fox on 2010-02-27
Hello,

[This]("https://help.ubuntu.com/community/Virtualisation") Community Wiki page should be of some use to you.

I prefer Virtualbox :D

-Silver Fox

---

### Post by theophiles on 2010-02-27
I use virtualbox OSE for the rare times I NEED windows and it runs great. I used to run the non-free virtualbox and it kept needing reset.

---

### Post by underquark on 2010-02-27
I'd definitely give VirtualBox a try.

- My setup has XP Pro 32-bit running in a 10Gb virtual machine.  This allows plenty of space for installing Windows programs and also some space for temporary files.  10Gb sounds a lot but if you have room on your hard disk it's worth it rather than finding the file too small and trying to change it later.
- I have Guest Add-ons installed to allow fuller use of the machine including access to USB ports.
- I have a separate shared folder on my "real" machine that is a sub-folder of my Home folder.  I use this to copy across data files that I will be working on in Windows and I also have a sub-folder with the setup programs for various small Windows programs.

I run the following with this setup:
Google Sketchup (simple CAD program)
VideReDo TV Suite (for editing DVB-T TV programs)
Logitech Vid (Windows alternative to Skype - even though I don't use a Logitech webcam)
TFRecEdit - for editing headers of digital broadcasts for Topfield PVR
DVDShrink - OK, ubuntu has alternatives but I still sometimes use this
DVDFab - ditto
SUPER© - A very powerful audio/video conversion program.

I even sometimes play old games running in a DosBox running in a virtual XP machine.  Performance is not an issue with these old games.

---

### Post by Joe_Ib on 2010-02-27
Thanks for the information guys.

---

### Post by rewyllys on 2010-02-28
> **underquark said:**
> I'd definitely give VirtualBox a try.

- My setup has XP Pro 32-bit running in a 10Gb virtual machine.  This allows plenty of space for installing Windows programs and also some space for temporary files.  10Gb sounds a lot but if you have room on your hard disk it's worth it rather than finding the file too small and trying to change it later.
- I have Guest Add-ons installed to allow fuller use of the machine including access to USB ports.
- I have a separate shared folder on my "real" machine that is a sub-folder of my Home folder.  I use this to copy across data files that I will be working on in Windows and I also have a sub-folder with the setup programs for various small Windows programs.

I second underquark's comments.  My XP setup is almost exactly the same as his, except that I've given VirtualBox a 20GB volume to work in (and why not be generous?--my Ubuntu setup resides on a 1.5TB hard drive, most of which is a separate partition allocated to /home).  

I find it convenient and satisfactory to run XP this way.  In particular, it works much faster and more satisfactorily for me than the analogous running of Ubuntu in Microsoft's VirtualPC under Windows Vista.  For me at least, VirtualBox seems much better than VirtualPC. 

One of the applications that I use via XP-in-VirtualBox is my sadly essential (for a US citizen) income-tax-return program (H&R Block At Home), a Windows program for which there is no Linux equivalent and, it seems to me, little likelihood that there ever will be.  The annual necessity of preparing an income-tax return is the primary reason why I set up the XP-in-VBox installation.  

My other main reason for needing Windows is to run WordPerfect X4.  I've liked WordPerfect ever since I starting using it under PC-DOS in 1983; I've always found it superior to MS Windows, and I was much saddened by the discontinuance of WordPerfect for Linux.  

Although now I use OpenOffice Writer for routine writing tasks, I continue to use WordPerfect for a specific task at which it surpasses all other current wordprocessors: grammar checking.  MS Word's grammar checking is much inferior to that of WordPerfect, and OO Writer's grammar checking is practically non-existent, so far as I can tell.

From time to time, I have occasion to write in French and Spanish, and I'm currently studying German.  I write my German (or French or Spanish) efforts in WordPerfect, run its grammar checker over my sentences, and see highlighted the errors I've made, along with suggestions for correcting them.  That's very useful to me!  The WordPerfect grammar checker is not perfect--no grammar checker is, or could be--but it's definitely helpful.

---

