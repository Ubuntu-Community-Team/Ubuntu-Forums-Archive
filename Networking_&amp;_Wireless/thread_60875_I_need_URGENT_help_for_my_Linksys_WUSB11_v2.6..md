---
title: "I need URGENT help for my Linksys WUSB11 v2.6."
date: 2005-08-29
forum: Networking &amp; Wireless
---

### Post by bttfpromo on 2005-08-29
Okay, I really want to run Apache, and Apache on Windows sucks. Please help me.

---

### Post by az on 2005-08-29
What is the problem?  Your device is not recognised?  If this is the card that I think it is, it is reasyto compile the drivers for it.  They are included out-of-the-box in Breezy.

However, it would just be simpler to use ndiswrapper to get it to work.

Install ndiswrapper-utils and find the windows driver for the device and copy the files to your desktop.  Then, from a terminal, run

cd Desktop
sudo ndiswrapper -i (filename.INF)
sudo modprobe ndiswrapper
sudo ndiswrapper -l (to list the dinstalled deviec and see if it is working)

Then, go to the Networking utility and configure your connection.

---

### Post by bttfpromo on 2005-08-29
IIRC, it reconizes the hardware, but not what it is. I ordered a pack of Ubuntu CDs back in Febuary and using that. I'll try Breezy.

---

### Post by asimon623 on 2005-09-07
do a search for wusb11 on this site

my thread has all the answers

---

### Post by sargonx on 2005-10-12
Here a linux newbie, with freshly installed Ubuntu breezy and accesing internet through a WUSB11 Linksys adapter... mine got recognized automatically out of the box. Yet, for those whose adapters didn't work right out, I kind of compiled all the help posted in this thread into annoyingly simple steps for those who (like me) know barely anything beyond point and click.

So, you have a WUSB11 that is NOT recognized in System+Networking in Ubuntu, or it is recognized but won't work anyway (check your config, I spent hours messing up with Ubuntu until I discovered my problem was that I hadn't enabled DHCP).

1) Go to a computer that has internet access.

2) Copy this post into a .txt file (using any text editor, like notepad in windows or Applications+Accesories+Text editor in Ubuntu. 

3) Go to [http://at76c503a.berlios.de/cvs.html](http://at76c503a.berlios.de/cvs.html)

4) Click the 'snapshot of the cvs repository link' and save to a disk, another partition, or by using a different method of internet access.

5) Log in to your Ubuntu and copy the downloaded file (most probably named "at76c503a-cvsroot.tar.gz") to your desktop. Also copy the .txt with the instructions to the desktop and open it while you work, it may be handy for copy-pasting into the terminal.

6) Deactivate Wireless Networking in System+Administration+Networking (if it appears).

7) Unplug the Wireless Adapter

8) Restart the system

9) Open the terminal: Applications+System Tools+Terminal

10) Mind the following: In almost all applications (namely Ubuntu desktop and the text editors), after selecting a text, typing Ctrl+X will CUT the text, Ctrl+C will COPY the text, and Ctrl+V will PASTE a text previously cut or copied. So you can cut, copy or paste into a .txt using these commands.

11) Mind the following: In the terminal, to CUT you need to type Ctrl+Shift+X, to COPY you need to type Ctrl+Shift+C and to paste you need to type Ctrl+Shift+V. So you can cut, copy or paste into the terminal using these commands.

12) Mind the following: The terminal is CASE SENSITIVE, which means that it matters, for example, whether you typed "Desktop" or "desktop". Beware of the case spelling of every path you type.

13) Type (always ignore the " "): "sudo apt-get install build-essential linux-headers-`uname -r`". This will upgrade some stuff. You will be asked to insert your Ubuntu boot disk, put your password when prompted, and voila. If you have already updated it, a message saying "you have the newest version" will appear: OK so far.

14) Type: "sudo apt-get install cvs". This will install something called CVS. You will be asked to insert your Ubuntu boot disk, put your password when prompted, and voila. If you have already updated it, a message saying "you have the newest version" will appear: OK so far.

15) Get the Ubuntu cd out of your tray. Put some music to avoid rage or despair in the case things don't go as planned :).

16) Now, if you have put the downloaded file in your desktop, the location of the file will be /home/YOURUSERNAME/Desktop. If you don't know your username, right click the downloaded file, go to properties and check the location of the file. Mine is /home/sargonx/Desktop, so my username is "sargonx". From now on, I will type the commands using my username; REMEMBER TO REPLACE IT WITH YOURS. It is easier if you modify it manually in the .txt file and then copy-paste it into the terminal to avoid misspellings.

17) Type: "cd /home/sargonx/Desktop". This will get you into the desktop directory.

18) Type: "tar xzvf at76c503a-cvsroot.tar.gz". This will extract the files within the compressed file you downloaded into a new folder on your desktop, named "at76c503a".

19) Type: "mv at76c503a CVS". This, as it took me some time to ascertain (way low Linux IQ here, guys), renames the folder you just created as "CVS".

20) Type: "cvs -d /home/sargonx/Desktop/CVS co at76c503a". This will create a copy of the "CVS" folder into the desktop, folder which is named "at76c503a".

21) Type: "cd at76c503a". This will get you into the new folder.

22) Type: "sudo make". This step is essential, as it is some kind of pre installation or installation. Some lines will run through the terminal. Wait till it's over.

23) Type: "sudo make install". Wait till its over. This should just about make it.

24) Plug in your wireless adapter.

25) Restart Ubuntu.

25) Go to System+Administration+Networking. Type your password.

26) Select "Wireless Connection", click on properties.

27) Enter a network name, select your key type and your WEP key (that you should know, your network may have a WEP key, which is a password; type it in the "WEP key" field. Select DHCP or Fixed IP, depending on your network configuration. Hit OK.

26) Activate the Wireless connection. Wait, it will take long.

27) Restart Ubuntu.

28) Try Firefox. Does internet work now? Hope it does!

If $#@& still not works:

1) Spot errors you get in the terminal and search for it in the forums, or post a question.

2) Upgrade the firmware: go to a computer with internet access and upgrade the firmware (firmware is the software of the device itself): go to [www.linksys.com/support](www.linksys.com/support),

3) Reinstall your ubuntu. If all alternatives are exhausted, and you got nothing to lose, you may try this... specially if you played around with the sudo command in the terminal without knowing what you were doing (my experience, again :).

Best of luck.

---

### Post by Moezzie on 2005-10-16
Realy good guide Sargonx, i love it.

It worked just fine untill the "sudo make part". I allways get an error telling me that i dont got anny "lib/modules/2.6.10-5-386/build".

How can i solve this problem?

Keep up the good work!

---

### Post by sargonx on 2005-10-16
Well, I'm a real newbie so I can't make a precise diagnostic... yet I think it is a version problem (you have a new version of something and thus the folder names are changed). The thing is, on my lib/modules folder I have folders starting with "2.6.12", instead of "2.6.10", you probably will have the same folders too. What I'd recommend you is to search the forums a bit for that kind of problem, or check if there will be new updates to the atmel driver. Alternatively, you could make a new post on networking, explaining the problem in detail and copy-pasting your full errors from the terminal into the post. The solution is probably simple, but it eludes me. I'm sorry.

Best of luck

---

### Post by Moezzie on 2005-10-16
its a good ider but i dont think its the vertion because i there is no "build" folder in the "2.watever" folder. 

I have had thise broblems before with other programs that need this folder or the containings.
So it would be realy nice to get that problem solved.

---

### Post by sargonx on 2005-10-17
I think it is serious stuff. If you are at a dead end, maybe you could reinstall the whole thing. It worked for me.

---

### Post by bsj on 2005-10-19
Howto worked perfectly. Thanks.

---

### Post by phazon. on 2006-06-15
sargonx, great guide that worked perfectly for me (a complete newbie in linux). Just one thing - with you being a newbie at the time, how did you find all that out?!

Could someone possibly explain what it did and why it worked as it would be great for my learning process?

Many thanks.

---

### Post by Jrabbit05 on 2006-08-12
Worked well for me also.
Thanks alot,
~Jack

---

