---
title: "Using Linux to repair Windows"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by Rambar on 2009-10-31
Hello!. Yesterday, a friend gave me a pendrive with some photos and when I plugged it in I saw some weird executables files inside. Doing a little research, I found out they were viruses (thank god I use Windows no more). I want to help my friend, as his computer must be a real mess.

 I've thought maybe it could be a good idea to boot on a LiveCD and scan his drives, repair his registry and remove Spyware/Adware, but as I am a new Ubuntu user myself, I dont know if this could be possible, and how to boot the required apps from a LiveCD. 

 I'd like it if you could give me some hints and directions on this issue. Thanks a lot.

---

### Post by jrrader on 2009-10-31
Is Windows not running on his computer?  If it is, fix it from there.  Other than using the live CD to write over his Windows, I don't believe there is too much you can do to fix it from linux.  What you can do is get a pen drive OS running (I use crunchbang from a USB stick), boot it up on his computer.  Mount his windows partition and copy all his important files to the USB stick.  (So much for windows passwords... I don't think you even have to be root).  Once everything important is off, he can reinstall.  Watch out for viruses in the files you move, though, if he plans on going back to windows.

---

### Post by grizato on 2009-10-31
I use puppy for that, 100mb, how much is crunchbag?

---

### Post by HiImTye on 2009-10-31
good idea is to grab avast! for linux to do a scan of the files you want to copy over before you do and waste the effort redoing his computer (again)

---

### Post by drseuk on 2009-10-31
You certainly can do this.

Boot from an Ubuntu Live CD, mount the hard drive and manually fix what needs fixing in MS Windows then reboot after removing the Live CD.

The Ubuntu Live CD will also happily install software into RAM if you need extra tools.

---

### Post by mapes12 on 2009-10-31
[http://lmgtfy.com/?q=windows+live+cd](http://lmgtfy.com/?q=windows+live+cd)

---

### Post by HiImTye on 2009-10-31
> **mapes12 said:**
> [http://lmgtfy.com/?q=windows+live+cd](http://lmgtfy.com/?q=windows+live+cd)
lmfao

I love that website

---

### Post by jrrader on 2009-10-31
> **grizato said:**
> I use puppy for that, 100mb, how much is crunchbag?

500mb - basically just ubuntu with a light weight WM. I have a puppy USB as well but I stopped using it as much after finding crunchbang.

---

### Post by Mark Phelps on 2009-11-01
> **Rambar said:**
>  ...  I've thought maybe it could be a good idea to boot on a LiveCD and scan his drives, repair his registry and remove Spyware/Adware, but as I am a new Ubuntu user myself, I dont know if this could be possible, and how to boot the required apps from a LiveCD...

There are Antivirus products, one has already been mentioned, that you can run from a Linux boot to use to scan the MS Windows machine.  And that should be able to handle the removing spyware part.  Whether they'll remove adware depends on the product.

As to repairing the registry and/or repairing MS Windows apps -- NO.  That's not something you are going to be able to do from Linux.

All you can probably do at this point is clean up the infection on the machine to the point it can be rebooted into MS Windows and HOPE that there is a Restore Point you can use.

---

