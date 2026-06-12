---
title: "Help on WUSB11 on new Wubi install [ NOOB OP ]"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by daviiiiiid on 2008-07-08
Hi. My friend suggested me to try out Ubuntu just for the fun of it and told me about Wubi. It was perfect, easiest installation. Was all good until that point.

Then I realized.. "How do I get my internet working??"

I read so many forums and everybody uses terms and names that I really cannot follow.. 

I have a WUSB11 USB v2.8 network adapter.. and a fresh Wubi installation from yesterday with Ubuntu.. so I don't really know what version it is.. ?

I tried going on terminal and typing in a few lines that were on the forums but without any success...

At some point I did see the available wireless networks and when I tried to connect with my wep key, it just attempts to connect and asks me to enter the WEP key again.. and just does not work. After restarting my computer.. no more available networks seen anywhere.. 

So if anybody is willing to give me a step-by-step (or even IM support), with some comprehensible newbie language is welcome.


On another matter.. why is it that when I type something on linux.. it often just repeats the letters i type like thiiiiiiiiiiiiiiiiiiiis. 


Thank you.

---

### Post by daviiiiiid on 2008-07-08
I have followed the wiki tutorial on :
[https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB11](https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB11)

**BOLD** means HELP!
*ITALIC* means Done.

> 
[SIZE="1"][I]1) Go to a computer that has internet access. 

2) Copy this page into a .txt file (using any text editor, like notepad in windows or Applications+Accesories+Text editor in Ubuntu.

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
[/I][/SIZE]
13) Type (always ignore the " "): "sudo apt-get install build-essential linux-headers-`uname -r`". (Note the backticks surrounding uname -r.)This will upgrade some stuff. You will be asked to insert your Ubuntu boot disk, put your password when prompted, and voila. If you have already updated it, a message saying "you have the newest version" will appear: OK so far.

** HERE IS WHERE I GET THE PROBLEM. I GET CANNOT ... BUILD-ESSENTIAL.. but if I have to add the boot disk.. Where do I find the disk? everything was done automatically with WUBI..**

14) Type: "sudo apt-get install cvs". This will install something called CVS. You will be asked to insert your Ubuntu boot disk, put your password when prompted, and voila. If you have already updated it, a message saying "you have the newest version" will appear: OK so far.

15) Get the Ubuntu cd out of your tray. Put some music to avoid rage or despair in the case things don't go as planned :).

16) Now, if you have put the downloaded file in your desktop, the location of the file will be /home/YOURUSERNAME/Desktop. If you don't know your username, right click the downloaded file, go to properties and check the location of the file. Mine is /home/sargonx/Desktop, so my username is "sargonx". From now on, I will type the commands using my username; REMEMBER TO REPLACE IT WITH YOURS. It is easier if you modify it manually in the .txt file and then copy-paste it into the terminal to avoid misspellings.

17) Type: "cd /home/sargonx/Desktop". This will get you into the desktop directory.

18) Type: "tar xzvf at76c503a-cvsroot.tar.gz". This will extract the files within the compressed file you downloaded into a new folder on your desktop, named "at76c503a".

19) Type: "mv at76c503a CVS". This, as it took me some time to ascertain (way low Linux IQ here, guys), renames the folder you just created as "CVS".

20) Type: "cvs -d /home/sargonx/Desktop/CVS co at76c503a". This will create a copy of the "CVS" folder into the desktop, folder which is named "at76c503a".

21) Type: "cd at76c503a". This will get you into the new folder.

22) Type: "make". This step is essential, as it is some kind of pre installation or installation. Some lines will run through the terminal. Wait till it's over.

23) Type: "sudo make install". Wait till its over. This should just about make it.

24) Plug in your wireless adapter.

25) Restart Ubuntu.

25) Go to System+Administration+Networking. Type your password.

26) Select "Wireless Connection", click on properties.

27) Enter a network name, select your key type and your WEP key (that you should know, your network may have a WEP key, which is a password; type it in the "WEP key" field. Select DHCP or Fixed IP, depending on your network configuration. Hit OK.

28) Restart and try Firefox. Does internet work now? Hope it does!

If $#@& still not works:

1) Spot errors you get in the terminal and search for it in the forums, or post a question.

2) Upgrade the firmware: go to a computer with internet access and upgrade the firmware (firmware is the software of the device itself): go to [www.linksys.com/support](www.linksys.com/support),

3) Reinstall your ubuntu. If all alternatives are exhausted, and you got nothing to lose, you may try this... specially if you played around with the sudo command in the terminal without knowing what you were doing.

Best of luck.

---

### Post by daviiiiiid on 2008-07-08
Anybody know any solutions for this?

---

