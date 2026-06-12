---
title: "Printer driver install"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by SungSean on 2010-11-26
I am trying to install my printer driver tar.gz file in Xubuntu.
I extracted the file. These are instructions to install. But I don't understand what '#' means.
What should I put in place of '#' sign? 

[Unified Linux Driver Install Guide] 
3. Download and extract the driver.
   [root@localhost root]#tar xzf [Downloaded File Name(XXXX.tar.gz)] 

4. The driver will be extracted as ''cdroot'' folder in current path. 

5. Execute installation program. 
   [root@localhost root]#./cdroot/autorun

---

### Post by s1baker on 2010-11-26
I am a noob, and have only been using Ubuntu about 2 weeks, so I am a novice, but being that nobody has replied yet, I will tell you what I think it is, but wait for one of the experts to post before doing anything. When you install any programs on Linux use must have root privileges, meaning you must enter the administrator password to get root privileges. After you do that you will see a # after the terminal prompt, signifying that you have these rights.

---

### Post by anewguy on 2010-11-26
> **SungSean said:**
> I am trying to install my printer driver tar.gz file in Xubuntu.
I extracted the file. These are instructions to install. But I don't understand what '#' means.
What should I put in place of '#' sign? 

[Unified Linux Driver Install Guide] 
3. Download and extract the driver.
   [root@localhost root]#tar xzf [Downloaded File Name(XXXX.tar.gz)] 

4. The driver will be extracted as ''cdroot'' folder in current path. 

5. Execute installation program. 
   [root@localhost root]#./cdroot/autorun

This:

> [root@localhost root]#wherever it appears, is just the prompt the person creating the instructions got from their system.  Yours will be different, and will incluse your userid.  So, I would do the following:

- open a terminal window (Applications/Accessories/Terminal)

- if indeed you already extracted the files (tar xzf [Downloaded File Name(XXXX.tar.gz)]), be sure it created the "cdroot" folder (try ls)

- just type:

sudo ./cdroot/autorun <press enter>

It's possible that you may get an error about not being executable.  If so:

cd cdroot
sudo chmod +x autorun

then just  sudo ./autorun

Dave ;)

BTW - yes, they were running as root and hence the prompt, but Ubuntu tries to avoid just logging in as root in Ubuntu we use "sudo " instead.

---

### Post by oldsoundguy on 2010-11-26
Most of the time your driver is already in cups.
Go to system> administration> printing.
Click on it then add printer and follow the directions .. find your printer and install it.

No need to run and external program unless you have a Fred Flintstone printer.

---

### Post by SungSean on 2010-11-26
My printer driver wasn't found in the cups. This is why I went to manufacturer's website and downloaded the driver. 
The commands given gave me these results:

seanc@seanc-desktop:~$ sudo ./cdroot/autorun
[sudo] password for seanc: 
sudo: ./cdroot/autorun: command not found
seanc@seanc-desktop:~$ cd cdroot
bash: cd: cdroot: No such file or directory
seanc@seanc-desktop:~$ sudo chmod +xautorun
chmod: missing operand after `+xautorun'
Try `chmod --help' for more information.
seanc@seanc-desktop:~$ 
 
I have root previilages and have password to execute install commands.
Thanks for your help.

---

### Post by JustinR on 2010-11-26
> **SungSean said:**
> My printer driver wasn't found in the cups. This is why I went to manufacturer's website and downloaded the driver. 
The commands given gave me these results:

seanc@seanc-desktop:~$ sudo ./cdroot/autorun
[sudo] password for seanc: 
sudo: ./cdroot/autorun: command not found
seanc@seanc-desktop:~$ cd cdroot
bash: cd: cdroot: No such file or directory
seanc@seanc-desktop:~$ sudo chmod +xautorun
chmod: missing operand after `+xautorun'
Try `chmod --help' for more information.
seanc@seanc-desktop:~$ 
 
I have root previilages and have password to execute install commands.
Thanks for your help.

Hi, you typed a command line wrong:
```

chmod +X autorun

```

---

### Post by SungSean on 2010-11-26
Sorry. No difference though.

seanc@seanc-desktop:~$ chmod +X autorun
chmod: cannot access `autorun': No such file or directory

---

### Post by jtarin on 2010-11-27
If you can see the mentioned file right-click on it and choose properties and then make it executable by clicking the permissions tab and marking it as such. Have you tried the CUPS interface to install your driver?
[http://localhost:631](http://localhost:631) in your web browser.

---

### Post by anewguy on 2010-11-27
Are you sure you untar'd the file?  It looks to me like the entire cdroot folder isn't there at all.  Where did you untar the file to?

Dave

---

### Post by SungSean on 2010-11-27
I downloaded the driver to Downloads folder, then rightclick, and selected 'Extract Here'. So the extracted file is in my 'Downloads' folder.
Regarding Jtarin's comments, I do not understand how to do what you told me. I went as far as to the 'Permissions' tab. But I don't know how to make the change you suggested. Thanks.

---

### Post by anewguy on 2010-11-27
What is the path to all of the files in your Downloads folder?  Is it Downloads/cdroot?  There should be several files and possibly folders that got extracted.

If the files are in Downloads/cdroot, then you need to log in to a terminal window, cd Downloads/cdroot, sudo chmod +x autorun (note the spacing) then ./autorun.

Keep in mind that what ever the link is you are following, it apparently thinks you untar'd the file based on your user home folder, hence cdroot just being off of your home folder.  But since you apparently did it based on the Downloads folder, you need to be sure you are in that folder before you try to do anything.  Everything you have posted here says you are trying all of this based on your home folder (the default when you log in to a terminal window).  Keep in mind if you extract to another location you must go to that location first before any of the command will work.

Dave

---

### Post by SungSean on 2010-11-28
Thank you for quick reply. I am sorry since I am very new to Xubuntu, I am not sure how to follow your instructions. Thank you for detailed explanations.  Do I put 'cd Downloads/cdroot, sudo chmod +x autorun ./autorun' like this exactly? Or am I wrong? Please correct me if you will.

---

### Post by SungSean on 2010-11-28
My tar.gz printer driver was extracted in the 'Downloads' folder. the extracted folder's name is cdroot. When I extracted the tar.gz driver, it became 'cdroot' folder. Thank you.

---

### Post by SungSean on 2010-11-28
My 'Downloads' folder is in 'seanc' folder. seanc folder has a house image inside it. The 'Downloads' folder is in 'seanc' folder with Desktop, Documents, Music, etc folders.

---

### Post by anewguy on 2010-11-29
Try this:

- open a terminal window (Applications/Accessories/Terminal)

- type:

cd Downloads/cdroot <press enter>

sudo chmod +x autorun <press enter>

./autorun <press enter>

---

### Post by SungSean on 2010-12-02
seanc@seanc-desktop:~$ cd Downloads/cdroot
seanc@seanc-desktop:~/Downloads/cdroot$ sudo chmod +x autorun
[sudo] password for seanc: 
seanc@seanc-desktop:~/Downloads/cdroot$ ./autorun
libstdc++.so.5 (gcc 3.0.x .. 3.3.x) not found, install ... /sbin/ldconfig.real: Can't create temporary cache file /etc/ld.so.cache~: Permission denied
done
libtiff.so.3 not found, install ... /sbin/ldconfig.real: Can't create temporary cache file /etc/ld.so.cache~: Permission denied
done
****  It seems Qt library is not installed, or X display is not accessible.
****  Custom Qt library will be configured for use with this package.
GUI mode installer execution failed, proceeding in text mode
ERROR: Root priviliges required, execution aborted
seanc@seanc-desktop:~/Downloads/cdroot$ **sudo** ./autorun
libstdc++.so.5 (gcc 3.0.x .. 3.3.x) not found, install ... done
libtiff.so.3 not found, install ... done
****  It seems Qt library is not installed, or X display is not accessible.
****  Custom Qt library will be configured for use with this package.

After these messages, GUI window appeared for installing the printer driver. After following the installation procedures, it said printer driver was installed. Then I tried printing 'Test Page' option, some webpages, document pages, but it either didn't print at all or just printed out these messages:
' Internal Error - Incomplete session by time out
  Position : 0xe272 (57970)
  System : h6fwsim_snipe/os_hook
  Line : 1060
  Version : SPL 5.07 06-27-2006'

---

### Post by jtarin on 2010-12-02
Can you give the make and model of your printer? Can you post the link where you downloaded the driver from? Let's take a look at the file and see if we can determine what's going on.

---

### Post by SungSean on 2010-12-02
My printer is Samsung ML-2240 Laser Monochrome printer.
The link where I downloaded the driver from is [http://www.samsung.com/ca/support/detail/supportPrdDetail.do?menu=SP01&prd_mdl_cd=ML-2240%2FXAA&prd_mdl_name=ML-2240&prd_ia_sub_class_cd=P](http://www.samsung.com/ca/support/detail/supportPrdDetail.do?menu=SP01&prd_mdl_cd=ML-2240%2FXAA&prd_mdl_name=ML-2240&prd_ia_sub_class_cd=P)
Thank you for your help.

---

### Post by anewguy on 2010-12-02
```
seanc@seanc-desktop:~/Downloads/cdroot$ sudo ./autorun
libstdc++.so.5 (gcc 3.0.x .. 3.3.x) not found, install ... done
libtiff.so.3 not found, install ... done
****  It seems Qt library is not installed, or X display is not accessible.
****  Custom Qt library will be configured for use with this package.
```

Be sure the build-essential package is installed.  Then check to be sure the 2 libs are installed (via Synaptic Package Manager).  It appears that the QT development lib might be needed as well so check to be sure it is installed.

You may want to check the site you downloaded this driver tar file from and see if they list what the dependecies are.  If possible, contact them via email and tell them the problems shown in your last attempt, explain to them the version of xubuntu you are using, and ask for their input - it is their driver, so they should try to make it work for you.

After you have tried installing build-essential and the 2 libs, and after contacting them, post back and we can try to go from there.

Dave ;)

---

### Post by anewguy on 2010-12-02
I downloaded your driver tar file and extracted everything.  I then went into Synaptic Package Manager and installed:

QT and the QT development lib (this actually installs quite a bit of stuff)

libstdc++ 

libtiff -> but couldn't find the version match

build-essential (since reinstalling 10.10 on a new PC I hadn't installed it again yet)

I then ran the autorun script.  I got 1 error about temp space, but it ran anyway.  Went through what I could of the configurator, but since I don't have your printer it didn't do much good.

So, in order to see if it does you any good, you need to do the following:

- start up Synaptic Package Manager

- put libqt in the search string

- be sure libqt3-headers, libqt3-mt, libqt3-mt-dev are marked and installed
- be sure build-essential is marked and installed
- be sure libtiffxx0c2 and libtiif4-dev are marked and installed
- be sure libstdc++5 package is marked and installed

Then try your autorun (remember to use sudo) file again.  When it goes through again and you install your printer, let us know what happens.

Dave ;)

---

### Post by jtarin on 2010-12-02
I have several Samsung printers that I have set up successfully without using Samsung drivers. I am not at home on my Ubuntu machine so I can't give you explicit details. If you want to continue with your present attempt please proceed as it could be successful. At the point in time you feel like its not worth the time PM me and maybe I can help you at then. I don't want to horn in here after so much work and help has progressed.
Or you could follow [these generic instructions for your printer]("http://www.patrickmin.com/linux/tip.php?name=ml2240"). You must have CUPS installed. Look in Synaptic package manager and do a search for CUPS.

---

### Post by anewguy on 2010-12-03
> **jtarin said:**
> I have several Samsung printers that I have set up successfully without using Samsung drivers. I am not at home on my Ubuntu machine so I can't give you explicit details. If you want to continue with your present attempt please proceed as it could be successful. At the point in time you feel like its not worth the time PM me and maybe I can help you at then. I don't want to horn in here after so much work and help has progressed.
Or you could follow [these generic instructions for your printer]("http://www.patrickmin.com/linux/tip.php?name=ml2240"). You must have CUPS installed. Look in Synaptic package manager and do a search for CUPS.

Feel free to horn in!!  I would be interested to see if the present effort works after going to the trouble to work through what I did, but that's not important - what's important is finding the easiest solution for the OP and others.  So please, feel free to post here!!

Dave ;)

---

### Post by anewguy on 2010-12-03
=== post text removed === 

It was in response to what turned out to be a spam message.

---

### Post by The Cog on 2010-12-03
> Nice simple guide for WINDOWS, but most people know how to read instructions for WINDOWS.It was signature spam. It's gone now. I suggest you edit your post and remove the quote.

---

### Post by anewguy on 2010-12-03
> **The Cog said:**
> It was signature spam. It's gone now. I suggest you edit your post and remove the quote.

Done deal .....  thanks!

BTW - Still love the Cray running ubuntu! :)

---

### Post by SungSean on 2010-12-03
I installed every file you mentioned and reinstallation was successful. I did not get notice for missing files. However I get this mysterious window asking me for passwords. It did appeared after the previous first installation but I didn't mention. The window's title is 'Authentication.' The content says, 'Authentication required for printing document 'How to install ..... files'(job 12).' Then an empty block with blinking cursor for my input beside a word 'none'. I don't know what it is asking for. I tried my log on password. I have no other password.

---

### Post by SungSean on 2010-12-03
I keep clicking 'OK' button. The window just keeps reappearing.

---

### Post by anewguy on 2010-12-03
Since I don't have your printer, I've done as much testing with the driver as I can.  I noticed the documentation at the Samsung site - have you checked it?  Also, see if there is a forum on the Samsung site and ask there.

Beyond that, I've gone as far as I can without buying a printer like yours.  Perhaps someone else can help you further, or perhaps jtarin can help you as he has suggested.  You might want to try PM'ing him, but try to keep everything in the thread so when you get it to work you can mark as Solved and others will know what to do.

Sorry I can't help you beyond this!

Dave ;)

---

### Post by oldsoundguy on 2010-12-03
A note:  See this over and over again with bargain basement printers .. the el Cheapos sold in a pile at the local super market or drug store for 25 bucks.  People expect them to work well in Linux .. Sorry, they don't even work well in WINDOWS for any period of time.

The solution to the problem is to get a real printer and it will work. (suggest an  HP .. almost always work out of the box in all operating systems.)

When you figure the hours wasted tweaking and adjusting and playing with and fixing a 25 buck printer, it is no longer a 25 buck printer.

---

### Post by anewguy on 2010-12-03
On the flip side, if $25 is as much to you as it is to me, you'll do any amount of work and go through a lot of frustration to get it working!

You are right, though.  I've stuck with HP or Brother and haven't had a problem.  I don't know if the OP has a choice, and it would be nice to see it work since it's so close.

I'm wondering if the password thing has anything to do with groups (like lp or something) that the OP isn't a member of but needs to be.  I just can't go any further since I don't own one of the printers.

Dave ;)

---

### Post by jtarin on 2010-12-04
> **SungSean said:**
> I installed every file you mentioned and reinstallation was successful. I did not get notice for missing files. However I get this mysterious window asking me for passwords. It did appeared after the previous first installation but I didn't mention. The window's title is 'Authentication.' The content says, 'Authentication required for printing document 'How to install ..... files'(job 12).' Then an empty block with blinking cursor for my input beside a word 'none'. I don't know what it is asking for. I tried my log on password. I have no other password.Possibly the document you are trying to print is password protected as in .pdf or MSWord documents.

---

### Post by anewguy on 2010-12-04
Have you gone through everything in the Universal Print Driver Guide from the website? [http://downloadcenter.samsung.com/content/UM/201004/20100407120019125/UPD_Guide_EN.pdf]("http://downloadcenter.samsung.com/content/UM/201004/20100407120019125/UPD_Guide_EN.pdf")
I noticed that after installing the driver, there are still several things they do on the screen to set up using the printer.

So, did you go through all of that and set up your printer?  The printer was found during setup?  Try just creating some junk document and printing it.

Did you ever do anything with users/groups in the installation process?  I don't remember seeing any reference to that, but just in case.....


Dave ;)

---

### Post by SungSean on 2010-12-04
The Guide link you gave shows different graphic interface and information than when I installed the driver. My printer model was found during setup. It specifically showed my printer model. I tried creating some junk files in Abiword and print it but the 'Authentication' window asking for something keeps appearing. It keeps preventing me from printing. I remember seeing some 'user/groups' options to click during setup but I did not click anything for it.

---

### Post by SungSean on 2010-12-04
My desktop icons disappeared by themselves. The desktop image has disapeared and it is just black color. System shutdown and restart do not work; when I shutdown or restart, Caps Lock and Scroll Lock lights keeps blinking and I have to hard shutdown everytime 
- -;.

---

### Post by anewguy on 2010-12-04
As I mentioned, since I don't own your printer, I can't really do much more testing here.  I would suspect the user/group stuff you saw is probably what is generating the request - it probably wanted to make your userid the member of some group the driver uses, but without a printer like yours I can't get that far.

As far as your current problem, I have no idea.  Do you see anything on the screen?  It almost sounds like a hardware problem to me.

I think I am at the end of what I can do to try to help you.  I hope someone comes along who can help you.  If worse comes to worse, you could ask one of the moderators of the forum to change the title Samsung ML-2240 Laser printer driver help needed.

I'm sorry I could not be of further help.  I would also strongly suggest you do a net search using:

linux samsung ml-2240

as the search string - a lot of entries are returned and somewhere in one of those may be the key to fixing your driver problem.

Best of luck!

Dave

---

### Post by SungSean on 2010-12-10
Just wanted to say, "Thank you very much" for helping me. Specially to Mr. anewguy.

---

