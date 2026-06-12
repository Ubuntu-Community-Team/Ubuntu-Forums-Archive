---
title: "Installing .BIN files"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by marlan on 2009-01-10
I have downloaded a file with the extension .bin, when I try to install it I get a message "There is no application installed for this file type" can you tell me how to install a .bin file.:confused:

---

### Post by taurus on 2009-01-10
You have to install it from a terminal.  Assuming you have saved it to your desktop, open a terminal and run

Applications -> Accessories -> Terminal
```
cd ~/Desktop
chmod +x filename.bin
sudo ./filename.bin
```
Be sure that is what you really want because if you install it, there might not be a way to remove it if you don't want it anymore.

---

### Post by marlan on 2009-01-10
Taurus, Thak you very much, worked perfectly first time.:P

---

### Post by jimjutte on 2009-01-12
Thank you Taurus, 

That was absolutely perfect. It also worked for me first time for the Adobe AIR bin file.

---

### Post by Leonasha on 2009-02-04
Hi, I am having the same problem.  When I run the code you suggested, I get "command not found". do I run the code just as is? sorry I'm a bit of a noob.

---

### Post by jerome1232 on 2009-02-04
> **Leonasha said:**
> Hi, I am having the same problem.  When I run the code you suggested, I get "command not found". do I run the code just as is? sorry I'm a bit of a noob.

No, you have to use the name of the file, if the file is named greatprogram.bin then you would copy the file to your desktop then execute that above code replacing filename.bin with greatprogram.bin

---

### Post by Leonasha on 2009-02-04
thank you! I'm up and running!

---

### Post by slr242 on 2009-02-18
Hi. Newbie here. I've followed the instructions above, but am still having probs getting my .bin file to execute.

I've actually set the permissions on the file to 777, just to see if it made any diff. It didn't. The file is sitting in my home folder.

From the GUI, the error I get is 'there is no application installed for this file type'.

From the terminal, I type 'sudo ./AdobeAIRInstaller.bin' in my home folder. It asks for my password, which I respond to. The error 'sudo: unable to execute ./AdobeAIRInstaller.bin: No such file or directory' gets displayed.

If I type ls -l *.bin, I can see that the file is there and that the perms are set to 777.

Any ideas? Many, many thanks.

---

### Post by oldos2er on 2009-02-18
First run "chmod a+x AdobeAIRInstaller.bin". Then retry "sudo ./AdobeAIRInstaller.bin"

---

### Post by slr242 on 2009-02-19
well, whadya know, it worked. :-)

thanks very much.

I don't understand why, given all that I'd done before. But... progress!

---

### Post by stidmatt on 2009-05-02
Perfect advice for someone (like me) who only understands a little bit of Konsole. Simple, to the point, thank you.

---

### Post by powerwatt on 2011-06-19
> **oldos2er said:**
> First run "chmod a+x AdobeAIRInstaller.bin". Then retry "sudo ./AdobeAIRInstaller.bin"

Brilliant Worker for me perfectly

---

