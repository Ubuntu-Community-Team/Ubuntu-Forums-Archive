---
title: "linksys wireless g card help"
date: 2006-11-23
forum: Networking &amp; Wireless
---

### Post by nonpareilpearl on 2006-11-23
I am relatively new to Ubuntu, and I am trying to set up my [wireless card]("http://www.linksys.com/servlet/Satellite?c=L_Download_C2&childpagename=US%2FLayout&cid=1115417109934&packedargs=sku%3D1115416827132&pagename=Linksys%2FCommon%2FVisitorWrapper") using NdisWrapper. I used the [instructions]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation") for installation, after [seeing]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53") that this particular card is not compatible by default, and it seemed to install correctly (no errors).

Then I went [here]("http://www.kosmaczewski.net/blogs/tech/archives/2006/02/how_to_install_1.php") to figure out how to install the Windows driver for the card (which is already installed in my Windows XP section), but when I use the ndiswrapper -i command it gives me the following error:
> quintessence@Qubuntu:~$ ndiswrapper -i WPC54GS Setup Wizard 2.1/Driver/NT/LSBCMNDS.inf
bash: ndiswrapper: command not found

At first I thought maybe I used the "wrong version" (there are two, 9x and NT-I just assumed that the NT would work since it's XP compatible), but it looks like it's just not recognizing the command ndiswrapper. Then I thought it was because I wasn't in root, so I tried using sudo ndiswrapper -i (and etc.), but I received the same error. Help?

---

### Post by FrodoB on 2006-11-23
What do you get if you just type:

ndiswrapper 

at a terminal command prompt?



If there is no ndiswrapper you could install the latest:

**Prepare the Linux build environment**


You will need to install the essential build files to compile the driver:  
```

 user@ubuntu:~$ sudo apt-get update 
user@ubuntu:~$ sudo apt-get install build-essential

```Install the correct headers for your version of Ubuntu: (don't worry if it tells you that yours are up to date.)  

```

user@ubuntu:~$ sudo apt-get install linux-headers-`uname -r` 
user@ubuntu:~$ sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build

``` **Download the latest version of the ndiswrapper driver**

  Download the latest version of the ndiswrapper from sourceforge: 
 [[IMG]https://help.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] http://sourceforge.net/projects/ndiswrapper]("http://sourceforge.net/projects/ndiswrapper") 
 The latest at the time I am writing this is: 
 [[IMG]https://help.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.28.tar.gz?modtime=1162136432&big_mirror=0]("http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.28.tar.gz?modtime=1162136432&big_mirror=0") 
 It should be noted that as the ndiswrapper is further developed it could be the case that any particular NDIS driver compatibility could become broken for awhile. 
  [B]
Extract and install the ndiswrapper using make[/B]

  Using tar extract the archived driver and change directories into the build area.  
```

 user@ubuntu:~$ tar xvzf ndiswrapper-1.28.tar.gz 
user@ubuntu:~$ cd ndiswrapper-1.28

```Make the driver with the commands "make distclean", "make", and "make install":  

```

user@ubuntu:~/ndiswrapper-1.28$ make distclean
user@ubuntu:~/ndiswrapper-1.28$ make
user@ubuntu:~/ndiswrapper-1.28$ sudo make install

```The make process will take several minutes to complete. 
 You can now check the ndiswrapper to see that it is installed correctly. You should see something similar to:  

 user@ubuntu:~/ndiswrapper-1.28$ ndiswrapper -v
utils version: 1.9
driver version:        1.28
vermagic:       2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1


Now you should be able to return to the instructions that you were working on.

---

### Post by nonpareilpearl on 2006-11-23
That's what I did before, except I downloaded 1.29 because it said it was stable. I did notice that when I do the 'tar' command it gives me the following error:> quintessence@Qubuntu:~$ tar xvzf ndiswrapper-1.29.tar.gz
tar: ndiswrapper-1.29.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
Which is the same error it gave me last time. However if I just "tar" it then it seems to run through the installation process. When I cd to the ndiswrapper-1.29 directory it does exist, so I'm not sure what's going on :-/

Should I find 1.28 and try that instead?

---

### Post by FrodoB on 2006-11-23
It just seems to be saying that the tar archive is not in the present directory. Yes 1.28 was released sometime today, use it rather than 1.28 for sure.

---

### Post by nonpareilpearl on 2006-11-23
Well I downloaded the file/directory to the desktop, so should I be including some sort of filepath? I thought it wouldn't need it since it is in the same directory (isn't it?)

---

### Post by FrodoB on 2006-11-23
Open a terminal and paste this in.  It will move it from your Desktop to your home directory:

$   mv ~/Desktop/ndiswrapper-1.29.tar.gz ~

---

### Post by nonpareilpearl on 2006-11-23
When I entered the move command it gave me an error, so I looked in my home directory and it's there already.

---

### Post by FrodoB on 2006-11-23
Well you are on your way then.

---

### Post by nonpareilpearl on 2006-11-23
Well it's been in my home directory, but it still doesn't recognize the fact that it exists (i.e. it was in my home directory when I received the above tar error).

---

### Post by FrodoB on 2006-11-23
If it is really in there you can do this:

1) Open a command window

2) Run an ls command:

user@ubuntu:~$ ls

ndiswrapper-1.29.tar.gz

3) Start the command:

user@ubuntu:~$ tar xvzf ndis

Now press the Tab key and it will complete at least to:

user@ubuntu:~$ tar xvzf ndiswrapper-1.29

Now add a period at the end if it and press the Tab key again:

user@ubuntu:~$ tar xvzf ndiswrapper-1.29.

Tab:

user@ubuntu:~$ tar xvzf ndiswrapper-1.29.tar.gz 

If that does not work, it is not where you think it is.

---

### Post by nonpareilpearl on 2006-11-23
It worked (the tabs), well it completed to the period, and after that it didn't seem to want to continue.

---

### Post by wmatlock on 2006-11-23
I have been trying to set up a d-link card and I did find that it was easier to copy the drivers to my home directory. Then CD into that same directoy and run the following command.

mkdir <driver-dir>
cp /media/cdrom/<card-name> /home/<your login name>/<driver-dir>
cd $HOME/<driver.dir>
sudo ndiswrapper -i <driver.inf>
sudo depmod -a
sudo modprobe -a ndiswrapper

Then double check that you have and entry in /etc/network to find the card. I think that network manager should do all the hard work from there. Oh BTW what version of Ubuntu are your using. I have had problems in Edgy and went back to 6.06. Of course you must change your repositories and select every possible one and then make sure that Network Manager and ndiswrapper are installed.

---

### Post by FrodoB on 2006-11-24
> **nonpareilpearl said:**
> It worked (the tabs), well it completed to the period, and after that it didn't seem to want to continue.

That would say that you already have the ndiswrapper-1.29 directory in your home. So just use cd to change into it and continue your instructions for building ndiswrapper:

$ cd ndiswrapper-1.29

---

