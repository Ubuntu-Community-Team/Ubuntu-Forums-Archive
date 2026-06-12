---
title: "DVD burner in WINE"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by jbrown96 on 2008-12-26
I have a program, ProShow Producer, that creates awesome video slideshows. My stepdad loves to use it to create family videos. I am switching him over to Ubuntu, but am having some problems with WINE. 

The program runs flawslessly in WINE, except for a warning about arial font at startup. 

The problem is that the program cannot create a disc image; it must output the video directly to a DVD. Is there a way to have the burner appear in WINE (I couldn't find out how to do it in winecfg, CD-ROM was the only option), or a way to trick the program into creating an .iso or .img by giving it a fake device?

Thanks for the help.

---

### Post by khelben1979 on 2008-12-26
If the program is not working correctly in Wine, I suspect that you need to change to another application.

Why not use a Linux burner application instead? That would be more reliable.

---

### Post by Jakey_TheSnake on 2008-12-26
```
sudo apt-get install msttcorefonts
```

Should solve the arial message. I believe, anyway. 

Can you not burn straight to a DVD using this program? I don't understand exactly what the problem is.

---

### Post by tylerspaska on 2008-12-26
I'm not sure about that particular application, but my burner programs work fine. You have to add the dvd/cd drive in the 'Wine configuration' (get there by typing winecfg in the terminal or by navigating there under the 'wine' menu). Then go to the 'Drives' tab and then you can add drives. Your dvd drive is probably /media/cdrom0, but could possibly be something else. I used 'autodetect' on mine and it recognized all my drives just fine.

---

### Post by jbrown96 on 2008-12-26
> **tylerspaska said:**
> I'm not sure about that particular application, but my burner programs work fine. You have to add the dvd/cd drive in the 'Wine configuration' (get there by typing winecfg in the terminal or by navigating there under the 'wine' menu). Then go to the 'Drives' tab and then you can add drives. Your dvd drive is probably /media/cdrom0, but could possibly be something else. I used 'autodetect' on mine and it recognized all my drives just fine.

I think this is more the problem. I'm using Fedora right now, and I don't have the link at /media/cdrom. I have tried /dev/cdrom, but that didn't work. 
It might be an error with the application itself. The error message I get is
> No functioning CD-R drives can be found. ProShow Producer was unable to detect your CD-R drive... 
You are using this computer as a non-administrator. Proshow Producer must be installed by an administrator to be able to write to CDs.
Could the bit about not being an administrator be causing the problems? Does anyone know of a free application that I could verify whether the drive is working?

Thanks for the replies.

---

### Post by carml on 2008-12-26
In my humble opinion ,if you have a lot of Windows programs you like to use under Ubuntu,and you can't get them working,you can make a installation of a Windows OS on your PC. :P

---

### Post by carml on 2008-12-26
I suggested that because not all the programs running under Windows run also under Ubuntu,and I don't know a thing about e.g. video editing under Ubuntu(I understood it was the reason you wanted that program to run under Ubuntu,if I'm not wrong :P).:(

---

