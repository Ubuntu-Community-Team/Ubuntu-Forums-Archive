---
title: "Impossible to get Ubuntu Distro files AFTER Windows 7 64"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by nitoplayer on 2010-12-16
You heard it right there, folks.  If you install Windows 7 64 after your Ubuntu install you will have on ability to use GRUB even after you associated it with your Ubuntu partition. 

I want to get my old files to do a clean install but of course I don't have permission for some 1,200 files.  I installed grub via the looong tutorial we have here and it was successful.  Still there is no GRUB and I can never ever get to my files.

---

### Post by CharlesA on 2010-12-16
Er what? What is happening exactly?

After you install Windows (any version) after Ubuntu, you need to reinstall Grub.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by akand074 on 2010-12-16
Yeah I'm a little confused too. It is well known that installing Windows after Ubuntu causes it to overwrite grub. Reinstalling grub is a two step job once your booted in a live cd. The link from the poster above explains how to do it.

---

### Post by nitoplayer on 2010-12-16
Under copying from the installed partition (Method 2) it resulted in a positive outcome, but GRUB still did not show up on restart.

Under Copy Grub 2 Files from Live CD (Method 1) (9.04+) I get 
"install_device not specified."

This is what I was getting at in the first post.

---

### Post by CharlesA on 2010-12-16
What version of Ubuntu are you running on the main install?

---

### Post by oldfred on 2010-12-16
Lets see what is installed and where it is, lyou can run this from liveCD:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

