---
title: "Getting an inf file from a netgear driver exe"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by laurencemulchrone on 2008-04-24
Hey guys.

i have read so many posts about getting inf files from exe's but i just cannot seem to do it....
i have unzip installed as well as cabextract installed.
the file is called wg111t_2_0_setup.exe and it is saved on my desktop

could anyone help me, how can i get the inf, im afraid i am still not good with the terminal, i am even unsure how to navigate to a file!

appreciate it!

---

### Post by dstew on 2008-04-24
Where is the .exe file? Is it in your home directory, or on the desktop? To navigate using the command line, open a terminal window (Applications --> Accessories) and the command line should tell you what directory you are currently in. If you are unsure, you can enter the command```
pwd
```which stands for "Print Working Directory", and it will tell you where you are. To change your directory, use the command **cd**. For example, to change to the Desktop directory, if you are in your current home directory, the command would be```
cd Desktop
```You can list the current directory with the **ls** command. To get a detailed listing, use```
ls -l
```There are some commonly used shortcuts. Your home directory is **~**, so from anywhere you can get to your home directory with```
cd ~
```The directory just above your current directory is **..**, so to go up one directory level you use```
cd ..
```That's all there is to basic command-line navigation.

Now, if your .exe file is on the Desktop, which is just a folder in your home directory, you can get to it from anywhere with```
cd ~/Desktop
```File names and directory names are case-sensitive, so Desktop is different from desktop. To try to get the drivers out of the .exe file, using cabextract, enter the command```
cabextract wg111t_2_0_setup.exe
```

---

### Post by prshah on 2008-04-24
> **laurencemulchrone said:**
> Hey guys.

the file is called wg111t_2_0_setup.exe and it is saved on my desktop


If it actually a driver zip file, you can just rename it (F2, or right click then rename) from .exe to .zip and then double click to open it, then choose extract.

However, I doubt that it is a self-extracting compressed file; all the NetGear stuff I have insist on installing the NetGear SmartWizard and even the CDs don't carry the drivers out in the open. 

If you are dualbooting, you can copy the INF and related files from your Windows/INF/WG311v3 (or whatever model) folder.

Once you get the INF files, if you need any installation help, refer to my (solved) NetGear thread at [http://ubuntuforums.org/showthread.php?t=756260&highlight=WG311v3](http://ubuntuforums.org/showthread.php?t=756260&highlight=WG311v3)

EDIT: Confirmed. wg111t_2_0_setup.exe this is not a compressed file that you can use cabextract on. It is a windows SmartWizard installation file. You can neither use cabextract not work with the rename it to .zip trick. So you need to get the driver files from the Windows/INF directory (folder).

---

