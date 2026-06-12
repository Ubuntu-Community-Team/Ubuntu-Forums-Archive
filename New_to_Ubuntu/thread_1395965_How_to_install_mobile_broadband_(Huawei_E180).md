---
title: "How to install mobile broadband (Huawei E180)"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by radaudiodesigns on 2010-02-01
Hi Guys, 

I have been trying for weeks now to install Meteor mobile broadband onto a Dell Mini 10v with Ubuntu.

I am a complete newbie to Ubuntu and have been trying to follow the guides online. I dont really understand the terms as im a windows user.

I would really appreciate if there was a step by step guide to getting this set up and installed. Im really at a loss! I know that many people have managed to get this working!

Thanks for your time and look forward to hearing from you!

Cheers
Ryan ;)

---

### Post by QIII on 2010-02-01
It might be helpful to post the URL of one of the guides you have tried to use.

Then someone might be able to go through it and help you understand the terms and what you need to do.

---

### Post by lemmy999 on 2010-02-01
Most Huawei dongles seem to be supported ootb in Ubuntu using network-manager. 

Left-click the network manager applet and you should see an option for mobile broadband. A small wizard is activated where you specify which country you are in, what sort of mobile broadband you are using ( PAYG/contract) and voila- it works.

The research I have done seems to correlate with my own experiences with mobile broadband and Huawei dongles - see here ([http://www.jason-roe.com/blog/meteor-broadband-working-on-ubuntu/](http://www.jason-roe.com/blog/meteor-broadband-working-on-ubuntu/)) or here ([http://www.davidmcgettigan.com/?p=386](http://www.davidmcgettigan.com/?p=386))

BTW which version of Ubuntu are you using? anything after 9.04 should work without a problem.

---

### Post by cbabbage on 2010-02-01
There are issues with some Huawei dongles. There is a bug in 9.10 which prevents some from working ootb; I believe the bug will be gone in the next version.

Here is what I had to do to get my e169 working in 9.10:

------------------------------------------------------------------

sudo modprobe -r option

sudo modprobe -r usbserial

sudo modprobe usbserial vendor=0x12d1 product=0x1001(or 1003 if not working)

and it should work. but every time you reboot or take modem of cumputer you have to do the same steps, you can do a script to make things easy.

make new document like "internet.sh"
and write:
#!/bin/bash
sudo modprobe -r option
sudo modprobe -r usbserial
sudo modprobe usbserial vendor=0x12d1 product=0x1001

open konsole and write:
chmod +x internet.sh

now when you power on your machine you just have to plug in your modem, rightclick on it and "safely remove" and run the script you've created. done.

how-to by: LdrGilberto and ruiguedes from [http://forum.pplware.com](http://forum.pplware.com)
---------------------------------------------------------------

This enabled me to get onto the internet, and then I upgraded my kernel to the next version and that seemed to fix the problem for good.

I don't know if this will be of any use to you with an E180, but good luck.

---

### Post by radaudiodesigns on 2010-02-03
Thanks for the reply's guys - Below is the link ive been trying to work off.

I dont understand what modprobe means or how to write scripts - imagine me as someone who really doesnt understand at all!

[http://www.jason-roe.com/blog/meteor-broadband-working-on-ubuntu/](http://www.jason-roe.com/blog/meteor-broadband-working-on-ubuntu/)

If you could give me any further direction, id really appreciate it!

Cheers
Ryan ;)

---

### Post by cbabbage on 2010-02-03
Okay, according to the Jason-Roe site, you need usb-modeswitch. I used this when I had the e169 on 8.04 to get it working. First, click on the link on his site which says usb-modeswitch and then click on the link to download   usb-modeswitch-1.1.0.tar.bz2. This should download the package onto your desktop. 
The next step will involve a bit of mucking around with a terminal. Do you know what a terminal is, how to open it and issue basic commands?
Oh and you still haven't said which Ubuntu you're using.

---

### Post by radaudiodesigns on 2010-02-04
thanks cbabbage!

I have no idea what a terminal is im afraid :oops:

We have downloaded the USB modeswitch, just not sure how to open or use it!

---

### Post by anaconda on 2010-02-04
terminal can be found from Applications>Accessories>terminal
or by typing Alt-F2 and typing gnome-terminal in there...

---

### Post by cbabbage on 2010-02-04
Okay, the usb_modeswitch download is an archive file which needs to be extracted. I'm assuming it downloaded to your desktop. So right click on the file - you will see a menu item saying Extract Here; click on that. This will unpack the archive and you will see another folder next to it with the same name minus the .bz2 suffix.

Next, open a terminal via Applications > Accessories > Terminal. The window which opens is for entering commands on a command line. Some basic commands are:
pwd - Print working directory. This prints out whatever folder you're currently in.
cd - Change directory. Enables you to shift to a different working directory.
ls - List. Lists the files in the current working directory.

Now we need to change directory in the terminal to the folder containing the extracted usb_modeswitch files. If the folder is on your desktop, the file path should be:

/home/your_profile_name/Desktop/usb_modeswitch-1.1.0

Where it says your_profile_name, substitute whatever name you log in as on your computer. So if you issue the command:

cd /home/your_profile_name/Desktop/usb_modeswitch-1.1.0

this should be your working directory, test by issuing

pwd

Next we need to check that a dependency called tcl is available. Issue the command

tcl

if the command prompt changes to a %, then it is installed, so just type 

exit

If it isn't installed then go no further - it will have to be installed before the next step.

The next command to issue is

sudo make install

Note that sudo will ask you for your password. If this command runs without any error messages, then usb_modeswitch will now be correctly installed on your system. Let me know if you get this far with no problems.

---

### Post by radaudiodesigns on 2010-02-07
Thanks for all your help so far mate. Im stuck at the tcl part. Ive typed tcl in the terminal window, but it says "command not found". I tried to download and install the package and it asks for administrator password. There was no password ever set on this machine - is there a generic password for this?

---

### Post by cbabbage on 2010-02-07
There are two ways of installing tcl, either from the terminal:

sudo apt-get install tcl

or via the Symaptic Package Manager:

from the top menu; System > Administration > Synaptic Package Manager.
After you put in your password, find the Search window in the top right hand corner, enter tcl, and it will search for the package. You will then just have to tick the tcl box, mark for installation then Apply and it will do it all for you.

Both sudo and Synaptic will ask you for your password. If you are the owner of the computer and the sole user, it will be the password you use to login. I'm surprised you say no password was ever set for the machine - there must have been at least one set during installation. There is no generic password.

---

### Post by radaudiodesigns on 2010-02-08
thanks again - my sister couldnt remember the password she started with so we reinstalled ubuntu 9.1 for netbooks and its just worked from the ubuntu menu now! Happy days - 

however - We need to install the meteor software now which is an .exe file - ive installed something called wine after a quick google search. No idea how to use it.

Certainly becoming more familiar with ubuntu! thanks for all your time so far!

---

### Post by alexfish on 2010-02-08
> **radaudiodesigns said:**
> thanks again - my sister couldnt remember the password she started with so we reinstalled ubuntu 9.1 for netbooks and its just worked from the ubuntu menu now! Happy days - 

however - We need to install the meteor software now which is an .exe file - ive installed something called wine after a quick google search. No idea how to use it.

Certainly becoming more familiar with ubuntu! thanks for all your time so far!

Hi

there is a topic for wine you could try posting here


[IMG]http://ubuntuforums.org/images/statusicon/subforum_new.gif[/IMG] [Wine]("http://ubuntuforums.org/forumdisplay.php?f=313")

---

### Post by cbabbage on 2010-02-08
Okay, so by now you should have usb_modeswitch installed. According to the Jason Roe blog, you will now need to run the following commands:

sudo /sbin/usb_modeswitch.sh
sudo lsusb
sudo /sbin/modeprobe usbserial vendor=0x12d1 product=0x1003

after which your computer should now recognize your broadband device. It may take a couple of minutes to do so.

The next thing is to right click on the Network Manager applet in the top right hand of the screen. If your device is now being recognized, it should show up as Meteor Broadband or something like that under either point-to-point networks, or mobile broadband.

If it is there, then click on it and then click the Edit button. Another window will open, where you will need to put in your username and password for the broadband device. Jason Roe mentions a couple of other edits, but I would just put these two in first.

Close the network manager, and then if you left click on it, it should show your Meteor Broadband as an available connection, which you will just click on in order to connect. A message should come up saying that the connection is established, at which point you can open up Firefox and off you go.

It shouldn't be necessary to use the windows software via wine, although, thinking about it, it might work. I haven't tried it so can't help you in this regard.

So try the above and refer back to the Jason Roe website and hopefully you should be able to finally get the thing working.

---

### Post by 3rdalbum on 2010-02-08
Whoa, whoa, whoa. Ubuntu 9.10 supports the E180 out-of-the-box. Just add a new connection in Network Manager to get started. USB modeswitch and the command-line are ONLY necessary if you're using an ancient version of Ubuntu like 8.04 or earlier.

There are a couple of reliability problems with mobile broadband in 9.10, which is why I advise either using 9.04 or the currently-in-development 10.04.

Ubuntu 8.04 users, please refrain from advising about setting up mobile broadband if the other person is using 8.10 or later!

---

### Post by cbabbage on 2010-02-09
Re: the last post. Ubuntu 9.10 does NOT support all Huawei dongles ootb - I know this for a definite fact from using my e169. I have been attempting to help this person to the best of my ability, given that I don't use an E180 on Meteor broadband, and the chap only just recently stated he was using 9.10. 

So, 3rdalbum, if you actually have experience in using a Huawei E180 in 9.10 and are fully across all of the problems, then feel free to take over from me trying to help. If not, then don't be so quick to criticise.

---

### Post by Silvertones on 2010-02-09
Guys don't fight read. He said in his last post that they had to reinstall 9.1 and it worked ootb

---

### Post by radaudiodesigns on 2010-02-09
Thanks again for all the help guys - really appreciate it.

So at the moment, we have the broadband modem working and discoverable. However we need to install the software exe file to be able to top it up!

We tried to open this in Wine - however, the setup started and then just stopped. Am i doing something wrong here?

We are so close to having this working!! Your help so far has been invaluble. If you can help me get over the final hurdle, i will be eternally grateful! :)

---

### Post by alexfish on 2010-02-10
hi

The wine software will not work with these devices;

Most service providers have a facility to top up on line;

If the device is preloaded , go to your service providers accounts page and follow their instructions

If the device is Not  preloaded then , open up the browser , sometimes the browser will automatically take you to the appropriate web page

If this does not happen contact your service provider

Alternate method ; there is a programme called VMC , available from Betavine , the latest version is supposed to work with Ubuntu 9.10 , but I can't confirm this

Regards

alexfish

---

