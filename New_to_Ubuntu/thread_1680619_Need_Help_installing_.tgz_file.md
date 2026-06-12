---
title: "Need Help installing .tgz file"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by rfjfj on 2011-02-02
hello, I am new to Ubuntu and don't know how to install downloaded programs made for linux.

I downloaded zimbra (email client) for linux.

file name is: 

zdesktop_2_0_1_b10659_linux_i686.tgz

its saved on my desktop.

when I double click it (like windows), there is no .exe file its just lots of folders within folders and files.

Help.

---

### Post by steveneddy on 2011-02-02
1. What version of Ubuntu are you using? Is it the server version?

2. Did you Google for "How to install .tgz file in Ubuntu?

3. Have you unzipped, or extracted the file? If so, is there a "Read Me" file there? If so, what does it say?

 ** Just trying to establish how much you may have already done **

To extract to the Desktop, right click and select "Extract Here" - or something to that effect.

also - look here - 
[http://wiki.zimbra.com/wiki/Zimbra_Desktop_2](http://wiki.zimbra.com/wiki/Zimbra_Desktop_2)

---

### Post by 3rdalbum on 2011-02-02
> **rfjfj said:**
> hello, I am new to Ubuntu and don't know how to install downloaded programs made for linux.

I downloaded zimbra (email client) for linux.

file name is: 

zdesktop_2_0_1_b10659_linux_i686.tgz

its saved on my desktop.

when I double click it (like windows), there is no .exe file its just lots of folders within folders and files.

Help.

Did you try reading the instructions provided with the package, or on the web page where you downloaded the file from? From what I can find out with Google, there's a shell script inside that you must run as root; it should be like "install_zimbra_client.sh" or something similar.

Open up a terminal (Applications > Accessories > Terminal) and type:

```
sudo sh
```

press the spacebar to add a space, and then drag the shell script to the terminal. Bring the terminal to the front again and press Enter.

Note, however, that for simple e-mail there is already an e-mail client preinstalled with Ubuntu - it's called Evolution and it's in the menus. Also, normally with Linux you don't just download a file from a website when you want to install software - you should ideally use the Ubuntu Software Center to find and install software. Zimbra is not available in USC, nor is there a PPA repository to add it to USC, which is why I've given you these instructions. But normally most of what you will want will be in the Software Center.

---

### Post by rfjfj on 2011-02-03
i extracted it. From there there is a install.pl file which i can run in terminal.  It asks me to continue with isntallation and where to save it.

now this is where i get suck.  Coming from windows 7, i am looking for folder such as program files but there is no such thing, so where should i save this file?

sorry, i am total noob to ubuntu, not sure how terminal works.

detailed help would be helpful.

I am running ubuntu 10.10

---

### Post by TechWiz2100 on 2011-02-03
They usually have a default installation directory. Try just pressing enter without a directory and see if it continues anyway with the default. Typical install directories are /usr/bin/, /opt/ or /bin/

Since this is probably an entire client you could probably make a folder in /opt/ and toss the entire thing in there.

---

### Post by rfjfj on 2011-02-03
sorry, try pressing enter but cannot continue like that

when I go in terminal, it ask to press enter to continue>>type A to accept terms then it asks for this:


Choose the folder where you would like to install Zimbra Desktop's application files [/opt/zimbra/zdesktop]: 


i try typing opt/zimbradesktop it worked.


Choose the folder where you would like to install Zimbra Desktop's application files [/opt/zimbra/zdesktop]: opt/zimbradesktop


Installing application files...done

You have finished installing application files.

Would you like to continue to install data files for user: nilay?
------------------------------
(Y)es or (N)o [Y]: Y

after I press enter, terminal window closes.

Now, i see the folder I extracted initially on the desktop has a new folder named opt>zimbradesktop>data, db, jetty, lib, linux (all folders) and License.rtf, README.txt

under linux, there is jre (folder), prism (folder), user-install.pl and zimbra Desktop.  When I double click zimbra desktop it gives me this error:

There was an error launching the application.
Details: Failed to execute child process "@install.app.root@/linux/prism/zdclient" (No such file or directory)

double clicking user-install.pl, it gives me option to run in terminal there it shows this message:


Choose the folder where you would like to install Zimbra Desktop's user data files [/home/nilay/zdesktop]: 

now, i am totally stuck!!!

help?

---

### Post by TechWiz2100 on 2011-02-03
You see those things in the brackets at the end of each line asking for your input? Those are the defaults for the script and are supposed to be what is used if you do not type in anything.

To run the application in terminal try 
```

cd /opt/zimbradesktop/
ls

```

and try running whatever executable you see there (they are normally highlighted in green) with 
```

./<filename>

```

I think the one its trying to run is
```

./linux/prism/zdclient

```

---

### Post by rfjfj on 2011-02-03
when i try to install it from the beginning and just press enter when it prompts:


hoose the folder where you would like to install Zimbra Desktop's application files [/opt/zimbra/zdesktop]: 


I just press enter and terminal windows closes and goes away.  I go to opt folder but zimbra folder is not there.

---

### Post by cariboo on 2011-02-03
id you use sudo to install the appliation?

```
sudo  ./install.pl
```

---

### Post by rfjfj on 2011-02-03
i don't know what sudo is, can you tell me exactly what to type in terminal (brand new to ubuntu). i am not sure what you mean cariboo907

---

### Post by damispyderbyte on 2011-02-03
> i don't know what sudo is, can you tell me exactly what to type in terminal (brand new to ubuntu). i am not sure what you mean cariboo907

Sudo grants superuser privileges,
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Its like having an admin account on windows.
Sudo in the terminal is giving the following command root (admin) privileges.

Ty

---

### Post by Thetherumcompound on 2011-02-03
Alright, let me explain some things so you understand what's going on. When software is installed in Linux, basically a bunch of files are installed in various directories(folders) in the filesystem. The installer is actually asking where you would like them installed. Luckily, the installer has defaults so if you aren't sure where to install them, it will put them in a place that's most likely right for you. That's what the paths in brackets were. Ex.
"Choose the folder where you would like to install Zimbra Desktop's application files [/opt/zimbra/zdesktop]:"
If you were to press enter, it would just install it in /opt/zimbra/zdesktop
The defaults in the script are most likely right.
Good luck with the install.

---

### Post by wep940 on 2011-02-03
As already mentioned, there are 2 things at work here:
 
1. The process requires root priviledges in order to install the software due to ownership of certain directories. In Ubuntu, we don't give you access to just logon as root, since it can allow a newbie who doesn't know much yet to really mess things up. Instead, Ubuntu provides the command "sudo" which says "run the following as if I was root" - it temporarily gives root access to you.
 
2. The script is showing default directories, which you should use.
 
 
So, you should go back to the install.pl file as follows:
 
in the terminal window, type:
 
sudo ./install.pl ( or perhaps just sudo install.pl??)
 
Everywhere that it asks for a directory/folder name, just press enter to let it take the default.
 
Let us know how it goes from there.
 
As hard as it is, particularly when you are new to Linux, don't try to think Windows, its' folder hierarchy, etc.. Linux is a very different animal from that. There really is nothing that even equates to "Program Files" since there is no common folder where everything installs to.
 
I also suspect you would be better served to extract the original tar file to somewhere other than your desktop.  I usually create a directory/folder named to reflect each tar file I decompress, then "cd" to that folder and follow the readme or the installation procedure.

---

### Post by rfjfj on 2011-02-04
Alright, I made progress with all of your guys' wonderful advice.

this is where i am at (after doing sudo ./install.pl)
PS: i have this folder in "Documents" since it will not allow me to put it under bin or opt.


Welcome to Zimbra Desktop setup wizard. This will install Zimbra Desktop on you computer.
------------------------------
Press enter to continue: 


PLEASE READ THIS AGREEMENT CAREFULLY BEFORE USING THE SOFTWARE. VMWARE INC. WILL ONLY LICENSE THIS SOFTWARE TO YOU IF YOU FIRST ACCEPT THE TERMS OF THIS AGREEMENT. BY DOWNLOADING OR INSTALLING THE SOFTWARE, OR USING THE PRODUCT, YOU ARE CONSENTING TO BE BOUND BY THIS AGREEMENT. IF YOU DO NOT AGREE TO ALL OF THE TERMS OF THIS AGREEMENT, THEN DO NOT DOWNLOAD, INSTALL OR USE THE PRODUCT.

License Terms for this Zimbra Collaboration Suite Software: [http://www.zimbra.com/license/zimbra_public_eula_2.1.html](http://www.zimbra.com/license/zimbra_public_eula_2.1.html)

------------------------------
(A)ccept or (D)ecline [A]: A


------------------------------
Choose the folder where you would like to install Zimbra Desktop's application files [/opt/zimbra/zdesktop]: 


Installing application files...done

You have finished installing application files.

Would you like to continue to install data files for user: root?
------------------------------
(Y)es or (N)o [N]: Y


------------------------------
Choose the folder where you would like to install Zimbra Desktop's user data files [/home/nilay/zdesktop]: 


------------------------------
Choose the folder where you would like to create desktop icon [/home/nilay/Desktop]: 



Installing user data files...done
Initializing user data...done
Creating desktop icon...done
mv: cannot stat `/home/nilay/zdesktop.tmp/index/*': No such file or directory
mv: cannot stat `/home/nilay/zdesktop.tmp/store/*': No such file or directory
mv: cannot stat `/home/nilay/zdesktop.tmp/sqlite/*': No such file or directory
mv: cannot stat `/home/nilay/zdesktop.tmp/log/*': No such file or directory
mv: cannot stat `/home/nilay/zdesktop.tmp/zimlets-deployed/*': No such file or directory
Zimbra Desktop has been installed successfully for user root.

You can start Zimbra Desktop by double-clicking the desktop icon or by running the following command:
"/opt/zimbra/zdesktop/linux/prism/zdclient" -webapp "/home/nilay/zdesktop/zdesktop.webapp" -override "/home/nilay/zdesktop/zdesktop.webapp/override.ini" -profile "/home/nilay/zdesktop/profile"

Press "Enter" to launch Zimbra Desktop; Press "Ctrl-c" to exit: 


now, on the desktop, I do see an icon for "zimbra desktop" but it doesn't open when i double click it or right click>open.  I also notice that icon for "zimbra desktop" is white sheet with a small lock on right-hand side top corner, not sure if that means anything.

now what?

---

### Post by Zill on 2011-02-04
rfjfj:  FWIW I really think you are doing things the hard way ;-)  If all you want is a simple email client then just use Evolution as suggested earlier - it should already be installed.

If you *do* want to install additional software then the recommended method is to use the Ubuntu Software Centre.  Alternatively, use the Synaptic Package Manager.  Both these methods allow simple installation of complete packages, including all dependencies, with a couple of clicks.  You do not need to worry about where to put things as this is all done automatically.

See [Installing Software in Ubuntu]("http://www.psychocats.net/ubuntu/installingsoftware") and other Ubuntu documentation, such as the "stickies" at the top of this forum section, for more info.

---

### Post by rfjfj on 2011-02-04
lol, i love my Yahoo Account and I don't wanna pay premium.  Zimbra is the only email client which will configure with my basic yahoo account without things like YPOPS and other stuff.

---

### Post by TechWiz2100 on 2011-02-04
try running sudo zdesktop from terminal or cd ~/Desktop then ./<name of shortcut>

---

### Post by Zill on 2011-02-04
> **rfjfj said:**
> lol, i love my Yahoo Account and I don't wanna pay premium.  Zimbra is the only email client which will configure with my basic yahoo account without things like YPOPS and other stuff.
I don't use Yahoo so can't give first hand info but a quick websearch reveals that Yahoo Mail should work OK with Evolution if you configure the account for IMAP.

If you prefer to use POP3 rather than IMAP then it seems that whether Yahoo Mail is free or not depends on the country you live in :confused:

See ["Connecting Yahoo mail with Evolution"]("http://askubuntu.com/questions/20075/connecting-yahoo-mail-with-evolution") for more info.

---

### Post by rfjfj on 2011-02-05
OMG, simple solution to a big problem.  Thanks for suggesting IMAP.

it works like charm.  Only problem is that when I make a message "read", it doesn't change the status of that message on my main email server.  WHen I log into yahoo mail using web, it still shows "unread" messages.

Any suggestions?

---

### Post by jakslev on 2011-02-16
This is really not good enough nerds :o))

Of course ZIMBRA has to be able to function. 

I get the same problem - it wont do a thing unless I am root and use the sudo install.pl thingy. Then I suppose I can afterwards change the relevant folders to being owned by my normal user account - which is what I will do now. Does anyone know if this will have any influence on security? I will start with the zdesk-zimbra thingy in my user folder with chown.

---

### Post by jakslev on 2011-02-16
Okay I got it to working by chowning the directory in opt and the directory plus short-cut on my desktop now it all works. However I am not sure if that is healthy? in particular the folders in opt?

Anyone knows?

---

### Post by TechWiz2100 on 2011-02-16
> **jakslev said:**
> This is really not good enough nerds :o))

Of course ZIMBRA has to be able to function. 

I get the same problem - it wont do a thing unless I am root and use the sudo install.pl thingy. Then I suppose I can afterwards change the relevant folders to being owned by my normal user account - which is what I will do now. Does anyone know if this will have any influence on security? I will start with the zdesk-zimbra thingy in my user folder with chown.

sudo probably has to be used because the default location /opt/zimbra is owned by root. You might be able to get away with running the installer out of sudo by doing ```
chmod +x install.pl
``` but I can't guarantee it will install in the opt folder properly

---

### Post by TechWiz2100 on 2011-02-17
> **jakslev said:**
> Okay I got it to working by chowning the directory in opt and the directory plus short-cut on my desktop now it all works. However I am not sure if that is healthy? in particular the folders in opt?

Anyone knows?

opt rarely has anything mission critical in it however I would recommend keeping /opt itself owned to root and just change zimbra's folder (folders don't have to inherit permissions) just for the sake of Ubuntu's sanity.

---

### Post by Hansoff on 2012-01-07
My input - I've had some good ideas from the forum so hope to help.

1) extracted the downloaded .tgz  to downloads.
2) used terminal to get to Downloads/theextracteddirectory and then
sudo ./install.pl
3) answered questions or pressed enter, did not do the root bit whereupon it all went blank.
4) could not find desktop Zimbra, could not use synaptic or software centre to do anything (why?).
5) Looked at Zimbra website where it said to right click on zimbra desktop - but I found this in the installed directory /opt/wherever by doing a search for zimbra in filesystem (lots of files came back).
6) Right-clicked on the file user-install.pl which appeared in /opt/zimbra/zdesktop/linux
7) followed instructions.
8) Found an icon on my desktop 'Zimbra' zd.desktop
9) clicked on it
10) started the set up process but will now leave that for another day as it came up with an error but was not very helpful. So it is installed. Back to Zimbra FAQ.

Evolution seems slow and has lost some of my folders when I upgraded from Ubuntu 10.04 to 10.10. The messages are still on my ntlworld account so not too bad a problem.
Installed Thunderbird as it seemed that this is the way forward (?) and had difficulty finding the right Lightning download. Done it now.
While I am here, I also have difficulty installing the latest release of seamonkey - Ubuntu software only has 2.1.

Running a wubi ubuntu with xp over there somewhere. Occasional use like when the 10.10 upgrade wouldn't let me back into ubuntu with the message Try Hd(0:0) NTFS5 and error file not found ...
For somereason I am back into ubuntu but haven't switched off since - should I upgrade to 11.04?

Have fun. Good system otherwise.:P

---

