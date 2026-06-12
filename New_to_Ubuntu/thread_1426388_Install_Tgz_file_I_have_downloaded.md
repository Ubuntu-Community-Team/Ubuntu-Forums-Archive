---
title: "Install Tgz file I have downloaded"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by Revo99 on 2010-03-10
Hello All,

I have downloaded PS3 Media Server via terminal. The file is saved to 'pms-linux-1.10.5.tgz'.

Still a noob and have not downloaded a .tgz file yet. I undertsand they are like a Zip file is in windows. What code would I use to install this via terminal.

Thank you in advance for your help.

Cheers,

Revo99

---

### Post by BenAshton24 on 2010-03-10
With archives, the installation process varies. For PS3 Media server you need to extract the archive and then run PMS.sh, note that you will need to have already installed the Java runtime environment.

All of this information is in the README file in the archive.

Hope this helps,
Ben.

---

### Post by Revo99 on 2010-03-10
> **BenAshton24 said:**
> With archives, the installation process varies. For PS3 Media server you need to extract the archive and then run PMS.sh, note that you will need to have already installed the Java runtime environment.

All of this information is in the README file in the archive.

Hope this helps,
Ben.

Hello Ben or anyone else that can help me,

Thanks for your helps so far.

Still very new to this. I did manage to install Java runtime however. Which is obviously a step in the right direction.

The .tar file said saved to: pms-linux-1.10.5.tgz

Just going to clairfy on what I am not sure on

1. I am not sure how to extract it exactely.

2. Once I find out how to extract. should I direct the extract somewhere?

3. I do not know what pms.sh is?

Thanks Again,

Revo99

---

### Post by Peter09 on 2010-03-10
Have you tried double clicking, or right clicking on it?

---

### Post by hemimaniac on 2010-03-10
> **Revo99 said:**
> Hello Ben or anyone else that can help me,

Thanks for your helps so far.

Still very new to this. I did manage to install Java runtime however. Which is obviously a step in the right direction.

The .tar file said saved to: pms-linux-1.10.5.tgz

Just going to clairfy on what I am not sure on

1. I am not sure how to extract it exactely.

2. Once I find out how to extract. should I direct the extract somewhere?

3. I do not know what pms.sh is?



Thanks Again,

Revo99


1 - Right clicking the <filename>.tgz should give you an option to extract here.

2 - As a previous poster mentioned information in the README and INSTALL txt files will assist you.

3 - pms.sh will more then likely deal with the actual install.

most .sh files are bash/executables, and I imagine on the software home/support page there will be lots of help and tuts. for this and future software not obtained in the software manager or a .deb file

---

### Post by SkyNet2029 on 2010-03-10
Umm. actually, you could open a terminal, navigate to the directory holding the tar file you are using for the installation, and do
 
```
tar -xvzf /path/to/tar/file
```
 
that should extract it, then run your 
```
./configure
```
or the sh script that it came with to install it, which is more than likely the pms.sh
```
sh pms.sh
```

---

### Post by BenAshton24 on 2010-03-10
Hey,

1) click Applications -> Accessories -> Terminal
2) Once the terminal window has appeared, run the following command:
```
wget http://ps3mediaserver.googlecode.com/files/pms-linux-1.10.5.tgz; tar -xvzf pms-linux-1.10.5.tgz; cd pms-linux-1.10.5; gedit README & sh PMS.sh
```

What the above code does is it downloads the archive, extracts it, goes into the newly created directory, opens the README file and runs PMS.sh which is what the readme files tells you to run (I haven't actually used the program since I don't have a PS3, but as far as I can tell, this is what you're supposed to do :P). After this, the README file covers how to get your server up and running etc.

Good luck :)

---

### Post by Revo99 on 2010-03-10
Hello all,

Thanks. I managed to extract the file. So I am on track now. I will read the README file. Then hopefully start configuring.

Cheers,

Revo99

---

### Post by rogue_0111 on 2010-03-10
You could also try "[alien]("http://kitenet.net/%7Ejoey/code/alien/")"

It converts rpm, tgz to deb.

The how to:    [http://ubuntuforums.org/showthread.php?t=304335](http://ubuntuforums.org/showthread.php?t=304335)


Good luck

---

