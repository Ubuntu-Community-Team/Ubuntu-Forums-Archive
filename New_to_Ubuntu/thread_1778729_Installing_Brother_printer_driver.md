---
title: "Installing Brother printer driver"
date: 2011-06-09
forum: New to Ubuntu
---

### Post by rawbertb on 2011-06-09
Okay--I hate to keep bothering everyone with my questions, but this is driving me insane.  I have downloaded the printer driver from Brother, I have it in my Home Folder.  I have tried to write the command by pressing Alt+F2 and typing in what they say to, but when I hit enter, the command "disappears," for lack of a better term.  What am I doing wrong?  I love Ubuntu, but if I cannot get my printer to work, I will have to go back to Windows.  I am a graduate student and have way too much to print to constantly have to put everything on a flashdrive and go find another computer to print.

---

### Post by jerrrys on 2011-06-09
alt-f2 is your application launcher.  sounds like you need to be in terminal (Accessories>Terminal) to do this

---

### Post by rawbertb on 2011-06-09
Okay--how do I find Accessories?  I am REALLY new at this!

---

### Post by philinux on 2011-06-09
> **rawbertb said:**
> Okay--I hate to keep bothering everyone with my questions, but this is driving me insane.  I have downloaded the printer driver from Brother, I have it in my Home Folder.  I have tried to write the command by pressing Alt+F2 and typing in what they say to, but when I hit enter, the command "disappears," for lack of a better term.  What am I doing wrong?  I love Ubuntu, but if I cannot get my printer to work, I will have to go back to Windows.  I am a graduate student and have way too much to print to constantly have to put everything on a flashdrive and go find another computer to print.

It will be easier to help you if you post the info your following from Brother.

---

### Post by rawbertb on 2011-06-09
I'm finding it difficult to install the printer driver. 


We have created a tool to help you easily install the printer driver. Follow these instructions to download and use the tool:

Note:

Please note that this tool will install the printer driver automatically, changing the instructed directories, links and system settings without notice.

For USB Users:
Connect your Brother machine to the PC before starting to follow the instructions.



Click here to download the tool.(linux-brprinter-installer-1.0.3-1.gz, ver.1.0.3-1, 14 KB)
The tool will be downloaded into the default "Download" directory. (The directory location varies depending on your Linux distribution.)

e.g. /home/(LoginName)/Download


Open a terminal window and go to the directory you downloaded the file to in the last step.


Enter this command to extract the downloaded file:
Command: gunzip linux-brprinter-installer-1.0.0-1.gz


Get superuser authorization with the "su" command or "sudo su" command.


Run the tool:
Command: bash linux-brprinter-installer-1.0.0-1 Brother machine name


The driver installation will start. Follow the installation screen directions. 
When you see the message "Will you specify the DeviceURI ?",

For USB Users: Choose N(No)
For Network Users: Choose Y(Yes) and DeviceURI.

---

### Post by jerrrys on 2011-06-09
ok, nice to know.  now forget it :D.  go to your download folder and just double left click on the file.  should get you the same result as using terminal.  and accessories is in your main menu.  post back

---

### Post by rawbertb on 2011-06-09
Okay, I did that, and it popped up the Software Center which stated that the file is not a software package.

---

### Post by jerrrys on 2011-06-09
ok, thats different in 11o4.  back to terminal

---

### Post by rawbertb on 2011-06-09
I have the terminal open

---

### Post by wojox on 2011-06-09
What version of Brother printer do you have and did you download the cups and lpr drivers?

---

### Post by rewyllys on 2011-06-09
Hello, Rawbertb, and welcome to Ubuntu.  Here's the note that I have for myself to remind me how to install the driver for my Brother MFC8820D printer:[INDENT]Also, reinstall the printers.  For the Brother MFC-8820D, go to directory /home/ron/Dropbox/BrotherPrinter 
and open file 
/home/ron/Dropbox/BrotherPrinter/openprinting-ppds-postscript-brother_20090616-3lsb3.2_all.deb
using Ubuntu Software Center.
[/INDENT]Let me try to translate this to your situation.  If you have somewhere on your system the driver for your printer, it should look something like "brother_20090616....deb".  You will need to modify my note to myself to reflect the location on your system of this file.  If you don't already have this driver, go to:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

and download the Debian driver for your printer.  Store it somewhere on your system (e.g., like my folder, "BrotherPrinter") and then carry out steps analogous to mine above.

Good luck!

---

### Post by jerrrys on 2011-06-09
hold off on that.  looks like rewyllys knows

---

### Post by rawbertb on 2011-06-09
I have an HL-2240, and the two drivers refused to install.

---

### Post by Bucky Ball on 2011-06-09
Rawbertb's method does work. He is right, that is one way, and the Brother driver install tool is a good idea. The way I did it originally: I downloaded the appropriate driver for my printer, went to the directory it was in using the terminal, and it was as simple as:

```
sudo su
make
make install
```And I was done. I had to install the driver on four machines so I tried everyway. They both worked (at least for me).

---

### Post by rawbertb on 2011-06-09
Okay--nothing works.  I am not enough of a computer geek to understand anything.  I really like Ubuntu, but if I am too stupid to even download a driver, I guess I have no choice but to go back to Windows--as much as I hate Microsoft.  Sorry to have troubled you all.  Have a great one!

---

### Post by jerrrys on 2011-06-09
some computer companies support linux.  find out if yours will and go with the supported linux product.

---

### Post by wojox on 2011-06-09
Download the drivers [lpr and cups]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2240") here.

Make sure their in your Downloads folder.

Open a terminal and run:

```
cd Downloads
```

```
sudo mkdir /var/spool/lpd
```

```
sudo dpkg -i --force-all hl2240lpr-2.1.0-1.i386.deb
```

```
sudo mkdir /usr/share/cups/model
```

```
sudo dpkg -i --force-all cupswrapperHL2240-2.0.4-2.i386.deb
```

Now go to System > Administration > Printing

Delete the printer in there.
Click New and it should search for printers.

Now open the Network Printer and select the Brother MFC-845CW (Brother MFC-845CW)
Let it print a test page.

---

### Post by Talon2 on 2011-06-09
> **rawbertb said:**
> Okay--nothing works.  I am not enough of a computer geek to understand anything.

Just in case you didn't run off:  I've used Brother printers for years and have never had to install a driver.  Ubuntu comes with 1000's of printer drivers included.

System > Administration > Printing > Add

You can probably take it from there...and you only need to do this if there was an issue with autodetection or you are using a parallel cable.

---

### Post by rawbertb on 2011-06-09
Talon2, you are a lifesaver!  As usual, the simplest answer is the one that works!  I have no idea why I keep trying to make things more difficult than they have to be.  Thank you so very much!

---

### Post by Talon2 on 2011-06-09
> **rawbertb said:**
> Talon2, you are a lifesaver!  As usual, the simplest answer is the one that works!  I have no idea why I keep trying to make things more difficult than they have to be.  Thank you so very much!

rawberth, that is great!  The one thing it takes to be comfortable with Ubuntu is time.  

FYI:  My experience is almost exclusively with hp and Brother printers and both are superbly supported in Linux.  Unless you buy a bleeding edge, just released printer by hp or Brother, as long as you are using the latest Ubuntu, it is likely supported without you have to download anything.  My hl-5050 is autodetected and I don't even have to do "Add."  You are ready to print after a new installation as soon as you have something to print.

There are many ways to do things in most Linux distros.  Many users that are moving to Ubuntu have experience with Windows and use that experience as a starting point.  This results in the questions not always being the best here in the forums.  Here is what we see:

I downloaded such-n-such driver from the hp web site.  The instructions are confusing.  What do I do?

Now, it is easier for experienced people to help if we have the same problem posted like this:

I'm running Ubuntu 11.04 desktop and I bought a new hp 4579 printer that I have hooked up with a usb cable.  How to do get my new printer operating?

Regards.

---

### Post by ebozzz on 2011-08-10
> **Talon2 said:**
> rawberth, that is great!  The one thing it takes to be comfortable with Ubuntu is time.  

FYI:  My experience is almost exclusively with hp and Brother printers and both are superbly supported in Linux.  Unless you buy a bleeding edge, just released printer by hp or Brother, as long as you are using the latest Ubuntu, it is likely supported without you have to download anything.  My hl-5050 is autodetected and I don't even have to do "Add."  You are ready to print after a new installation as soon as you have something to print.

There are many ways to do things in most Linux distros.  Many users that are moving to Ubuntu have experience with Windows and use that experience as a starting point.  This results in the questions not always being the best here in the forums.  Here is what we see:

I downloaded such-n-such driver from the hp web site.  The instructions are confusing.  What do I do?

Now, it is easier for experienced people to help if we have the same problem posted like this:

I'm running Ubuntu 11.04 desktop and I bought a new hp 4579 printer that I have hooked up with a usb cable.  How to do get my new printer operating?

Regards.

Thanks for your insight. I just received a Brother MFC-790CW for free and was wondering how the support compared to HP devices. Like you, I have never had a problem with an HP printer but this will be my first Brother. I think I will go ahead and get it installed now.....

---

### Post by totallybeachin on 2011-08-28
I have been pulling my hair out trying to get my printer installed. This is what FINALLY worked for me. Thanks for posting. Just goes to show, no matter how old a post, it can still be useful to someone!
I'll add just for reference, the commands about mkdir didn't apply to me for whatever reason. I don't know enough to understand most of this, but after pasting the command, my terminal didn't show that anything was happening. I just kept going copying and pasting all the commands until the end. One other thing for me, when I went to System > Administration > Printing
My Brother printer was not listed there for me to delete. I hit the blue "refresh" arrow and then it appeared. I didn't delete it, just went to properties then print test page. Worked flawlessly!!
Thanks again.


> **wojox said:**
> Download the drivers [lpr and cups]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2240") here.

Make sure their in your Downloads folder.

Open a terminal and run:

```
cd Downloads
``````
sudo mkdir /var/spool/lpd
``````
sudo dpkg -i --force-all hl2240lpr-2.1.0-1.i386.deb
``````
sudo mkdir /usr/share/cups/model
``````
sudo dpkg -i --force-all cupswrapperHL2240-2.0.4-2.i386.deb
```Now go to System > Administration > Printing

Delete the printer in there.
Click New and it should search for printers.

Now open the Network Printer and select the Brother MFC-845CW (Brother MFC-845CW)
Let it print a test page.

---

