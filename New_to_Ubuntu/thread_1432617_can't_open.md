---
title: "can't open"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by mamamac on 2010-03-18
O K  here I go again. I bought a HP Deskjet F2480. I found instructions on getting the drivers. I typed in the terninal:

robin@office:~$ cd Desktop
robin@office:~/Desktop$ sh hplip-3.10.2rcl.run

and got this:

sh: Can't open hplip-3.10.2rcl.run
robin@office:~/Desktop$ 

What do I need to do to get it open?  Keep it simple cause I'm stupid.

            Thanks

---

### Post by a.walker on 2010-03-18
> **mamamac said:**
> O K  here I go again. I bought a HP Deskjet F2480. I found instructions on getting the drivers. I typed in the terninal:

robin@office:~$ cd Desktop
robin@office:~/Desktop$ sh hplip-3.10.2rcl.run

and got this:

sh: Can't open hplip-3.10.2rcl.run
robin@office:~/Desktop$ 

What do I need to do to get it open?  Keep it simple cause I'm stupid.

            Thanks

Do you have the file "hplip-3.10.2rcl.run" on your desktop? Normally firefox places downloads in your "Downloads" folder. You get to this folder by opening the terminal and typing

"cd Downloads"

If you get stuck, you can check [this thread]("http://ubuntuforums.org/showthread.php?t=1293057") in the forum.

---

### Post by mamamac on 2010-03-18
yes, my downloads go on my desktop

 this is what happened 


robin@office:~$ cd Desktop
robin@office:~/Desktop$ sh hplip-3.10.2rcl.run
sh: Can't open hplip-3.10.2rcl.run
robin@office:~/Desktop$ cd Downloads
bash: cd: Downloads: No such file or directory
robin@office:~/Desktop$ 


now what?

---

### Post by dineshs on 2010-03-18
confirm that the file is on the desktop by typing ```
ls
```
after cd Desktop

---

### Post by a.walker on 2010-03-18
> **mamamac said:**
> yes, my downloads go on my desktop

 this is what happened 


robin@office:~$ cd Desktop
robin@office:~/Desktop$ sh hplip-3.10.2rcl.run
sh: Can't open hplip-3.10.2rcl.run
robin@office:~/Desktop$ cd Downloads
bash: cd: Downloads: No such file or directory
robin@office:~/Desktop$ 


now what?

You should check to see if you are typing in the same file name as the file you downloaded. The easiest way to do this will be to use the "tab" key to complete the line you are typing. i.e. in the terminal, navigate to the folder where the file is and type "sh hplip" and then press the tab key. It will automatically fill out the rest. 

The reason why I think that the name is wrong is because the name includes "rc1" which means release-candidate 1. I think the 3.10.2 driver is out of the release candidate stage and the instructions need to be updated. (The file name may now be "hplip-3.10.2.run")

Or if you wanted to be lazy you could just double-click on the file you downloaded.

---

### Post by mamamac on 2010-03-18
robin@office:~$ cd Desktop
robin@office:~/Desktop$ sh hplip-3.10.2rcl.run
sh: Can't open hplip-3.10.2rcl.run
robin@office:~/Desktop$ cd Downloads
bash: cd: Downloads: No such file or directory
robin@office:~/Desktop$ cd Desktop is
bash: cd: Desktop: No such file or directory
robin@office:~/Desktop$ cd Desktop ls
bash: cd: Desktop: No such file or directory
robin@office:~/Desktop$

---

### Post by mbzn on 2010-03-18
Try ls ~/Desktop

---

### Post by mamamac on 2010-03-18
It is on my desktop. I clicked it and got a yellow block with a red circle in it  The circle has a white horizontal stripe similar to a "do not enter' sign.

I copied this:

Could not open the file /home/robin/Desktop/hplip-3.10.2.run.

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

Character coding    Current Local (UTF-8)

The last line gives the option of   (Western ISO 8859-15)

---

### Post by mamamac on 2010-03-18
robin@office:~$ cd Desktop
robin@office:~/Desktop$ sh hplip-3.10.2rcl.run
sh: Can't open hplip-3.10.2rcl.run
robin@office:~/Desktop$ cd Downloads
bash: cd: Downloads: No such file or directory
robin@office:~/Desktop$ cd Desktop is
bash: cd: Desktop: No such file or directory
robin@office:~/Desktop$ cd Desktop ls
bash: cd: Desktop: No such file or directory
robin@office:~/Desktop$ ls ~/Desktop
27 & 30 domes
$300.00?
34 & 36 domes
40 domes
45 domes
48 domes
carbon fiber
hplip-3.10.2.run
Info.desktop
Malcolm in the Middle - 3x11-12 - Company Picnic.avi
Malcolm in the Middle - 3x13 - Reese Drives.avi
pompeii_oven_plans2.0.pdf.zip
resume shop skills.doc
resume shop skills.rtf
rmusic theory
series
surfmerchants.jobslingerplus.jobdinger.678bff81a6039956cab00811cb07fe45d5f13b96.1.desktop
robin@office:~/Desktop$

---

### Post by dineshs on 2010-03-18
try ```
sh hplip-3.10.2.run
```

---

### Post by brianfactors on 2010-03-18
Sounds like a permissions issue to me.

Right click on the file and under Properties > Permissions make sure that the box is checked that says "Allow executing file as a program."

Or, if you prefer command line:

```
chmod u+x hplip-3.10.2.run
```

Unless of course you were using the wrong name, which may be the whole problem.

Oh, and another thing: You can use the tab key to get help from the terminal to auto complete file names. So, just type hplip and hit tab, and it should fill in the rest.

Hope you get it figured out...

---

### Post by mamamac on 2010-03-18
BINGO...IT IS DOING STUFF NOW.  Letting it do it's thing.

              Thanks mucho grande.  

         Till I mess up again, 

        keep collecting beans.... and cups..... and grinders..... and coffee makers....

---

