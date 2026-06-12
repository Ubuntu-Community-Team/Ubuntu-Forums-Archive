---
title: "How to unpack downloaded driver?"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by wlamore on 2010-03-22
I just got a wireless card for my laptop that is supposed to work with linux.  I downloaded the driver as suggested and it said download successful.  I also opened the package manager but do not know how to unpack it so it is on the computer and accessible by the wireless card.   With windows xp you select the driver, select run or save and if saved you just click on it and it installs the program etc. automatically.  Is there a feature on ubuntu that will make this auto unpacking available?
 
Thanks 
wlamore.

---

### Post by patchwork on 2010-03-22
Is the driver package a .deb package?  .tar.gz?  .rpm?

---

### Post by gadolinio on 2010-03-22
> **patchwork said:**
> Is the driver package a .deb package?  .tar.gz?  .rpm?

+1.
Depending on what you have downloaded, you'll need to do stg different.
If the driver is a .deb, you just double click it to use it.
If it's a .zip, .tar.gz, .tar.bz or stg like that, you have to right-click the file, and choose "extract here". A folder containing the files will appear. Then look inside it; many times, it contains a readme file.

---

### Post by wlamore on 2010-03-22
It says off the ralink website it is a gzip archive or above ta...gz 

I right clicked and it said unzip so I created a new folder and I hope it unzipped it.  Now what click on the exe file?

wlamore

---

### Post by patchwork on 2010-03-22
Are you planning on using a windows driver wrapping program with this, or have you downloaded a native linux driver?  

What is the link to the file you've downloaded?  If you think you've downloaded a native driver for linux, it should not be a .exe format.  Providing the link to the driver from the website will help us answer a lot of questions.

---

### Post by Rayve on 2010-03-22
.exe are only executable files for Windows, not for Linux.

After you have extracted the driver, I believe (but am not positive) that you will need to configure, make, and install.

The steps should be here: [http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

Open a terminal window (Applications > Accessories > Terminal, or press Alt + F2 and then type "gnome-terminal" if you are using gnome) and change to the folder where you extracted the folder.

Something like ```
 cd /home/yourusername/Desktop 
``` perhaps if you extracted it to your Desktop, or wherever you placed it.  Exact spelling is important, as Linux is case sensitive.

Once you are in that folder, you will see your Terminal display change to the path so you are sure, then you can continue with commands.

Type ```
 ./configure 
``` and press Enter.  That's a period before the forward slash, which tells Linux to do the configure command on the current directory.

After that is done running, type ```
 make 
``` and press enter.  You'll see some text running across the screen.  

When that's done, if all is good (that is, you don't see any errors or it doesn't say failed/aborted, which it shouldn't) then you can finally enter ```
 make install 
``` and then press Enter.  After more text, the driver will install, and you'll be returned to the terminal prompt.

From there, you can type "exit" to close out the terminal window, but if you got any errors, you can highlight and copy/paste the sections here to the forums and folks can help you out.

Hope this helps!

---

### Post by wlamore on 2010-03-22
Here is the link and choose linux and the driver is below to download to ubuntu and get the wireless card operating. 
 
[http://eng.ralinktech.com.tw/support.php?s=2](http://eng.ralinktech.com.tw/support.php?s=2)
 
 
Linux wireless driver - RT2500-Linux-STA-1.4.6.6.ta..gz
 
wlamore

---

### Post by linuxman94 on 2010-03-22
Ok this is gonna be a bit complicated.

---

### Post by wojox on 2010-03-22
Go into the Module directory and read the readme file. It will tell you what you need to build and install it.

---

### Post by patchwork on 2010-03-22
> Go into the Module directory and read the readme file. It will tell you what you need to build and install it.

Aye, what you have downloaded is not a ready made driver, rather the source code to compile the driver for your system.  Following the directions in the readme will show you how to compile the driver.

It's going to seem a bit complicated for a new user, but if you are having trouble following the directions post back for help.  

Everything you need looks like it is there, just be thorough (read twice, execute once).

---

### Post by wlamore on 2010-03-23
So this is hard compared to windows.  I also went to the windows section of ralink and clicked the same driver and it downloaded right to the desktop and was setup.  
 
does anyone have an easy solution to pcmcia cards for my laptop that I can easily install and get working or is wireless out of the question?
 
wlamore  ](*,)

---

### Post by gadolinio on 2010-03-23
Have you extracted the content, and then tried the steps ./configure, make, sudo make install?

---

### Post by Mark Phelps on 2010-03-24
> **wlamore said:**
> So this is hard compared to windows.  I also went to the windows section of ralink and clicked the same driver and it downloaded right to the desktop and was setup.  
 
does anyone have an easy solution to pcmcia cards for my laptop that I can easily install and get working or is wireless out of the question?
 
wlamore  ](*,)

Linux is not Windows.  In Windows, you typically run an .exe file that installs drivers and other stuff.  In Linux, drivers are contained in modules that are loaded by the operating system kernel.  Drivers that are not distributed WITH the kernel have to be build from scratch.  That's the situation you are in.

The "solution" is what you've already been told -- to read the instructions contained in a text file about how to compile and build the drivers needed.

---

