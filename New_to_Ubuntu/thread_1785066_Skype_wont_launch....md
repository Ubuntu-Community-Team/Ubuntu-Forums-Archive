---
title: "Skype wont launch..."
date: 2011-06-17
forum: New to Ubuntu
---

### Post by Proto Blaze on 2011-06-17
I just installed the Ubuntu 64 bit version from skypes website... but when I click the icon nothing happens... any ideas?

10.04

---

### Post by jtarin on 2011-06-17
Try starting it from the terminal with the command ```
skype
``` and then copy and paste the output here.

---

### Post by Proto Blaze on 2011-06-17
typed it in the terminal... absolutely nothing happened

michael@michael-desktop:~$ skype
michael@michael-desktop:~$

---

### Post by jtarin on 2011-06-17
Try again with ```
sudo skype
```

---

### Post by Laforge129 on 2011-06-17
Have you tried to install the 32 bit version of skype?  I've heard that there might be problems with 64 bit version with linux, just a thought!

---

### Post by Proto Blaze on 2011-06-17
michael@michael-desktop:~$ sudo skype
[sudo] password for michael: 
michael@michael-desktop:~$ 

No i have not tried the 32 bit.. i figured it would give me an error like the 32 bit avast gave me (only tested it for the lulz.... i know ubuntu doesnt need a virus scanner)

---

### Post by Laforge129 on 2011-06-17
> **Proto Blaze said:**
> michael@michael-desktop:~$ sudo skype
[sudo] password for michael: 
michael@michael-desktop:~$ 

No i have not tried the 32 bit.. i figured it would give me an error like the 32 bit avast gave me (only tested it for the lulz.... i know ubuntu doesnt need a virus scanner)

I don't know if it would give you an error or not since I haven't tried it myself.   Did you do:

```
Sudo apt-get install skype
```

or did you download it directly?

---

### Post by jtarin on 2011-06-17
> **Laforge129 said:**
> I don't know if it would give you an error or not since I haven't tried it myself.   Did you do:

```
Sudo apt-get install skype
```

or did you download it directly?:p That was going to be my next question.

---

### Post by Proto Blaze on 2011-06-17
got it off of skypes website

---

### Post by jtarin on 2011-06-17
What was the full name of the file you downloaded? The 32-bit for your Ubuntu version supposedly works.....
[skype-ubuntu_2.2.035-1_i386.deb]("http://www.skype.com/go/getskype-linux-beta-ubuntu-32")

---

### Post by Proto Blaze on 2011-06-17
> **jtarin said:**
> What was the full name of the file you downloaded? The 32-bit for your Ubuntu version supposedly works.....
[skype-ubuntu_2.2.035-1_i386.deb]("http://www.skype.com/go/getskype-linux-beta-ubuntu-32")

Error: Wrong architecture... :(

---

### Post by jtarin on 2011-06-17
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

---

### Post by Proto Blaze on 2011-06-17
> **jtarin said:**
> [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

yea.... doesnt help lol

i did install it before and it work, then i uninstalled and reinstalled and it never launched since

---

### Post by jtarin on 2011-06-17
Look in your /home/usrname directory for any folder or file related to skype. It might be a hidden folder. You will need to use the nautilus "view" menu and show hidden files and folders. [This forum topic]("http://www.linuxquestions.org/questions/debian-26/how-do-i-get-apt-get-to-completely-uninstall-a-package-237772/") will introduce you to tools needed to completely remove a package and its configs and dependencies from your install.I recommend you clean your system of all skype files and then try the reinstall as outlined on the link I gave you above.

---

### Post by Proto Blaze on 2011-06-17
got rid of my hidden folders for skype, uninstalled and reinstalled... nothing. idk what i did (something with trying to get the webcam to work in the past) but it ruined skypes ability to run. oh well I will do a reinstall on a future date. thanx anyways. im calling this quits for now. I will do a clean install so it runs flawless again

---

### Post by Muskegman on 2011-06-17
Go to your home directory, view hidden files and then go to .Skype, there is a file in there called shared.xml

Simply delete this, then restart Skype and it should work again.

---

### Post by Proto Blaze on 2011-06-17
i did but nothing happened...

---

### Post by jtarin on 2011-06-17
> **Proto Blaze said:**
> i did but nothing happened...You followed that link to "apt" tools to get rid of everything? Then one more thing after uninstalling.....try the command ```
sudo updatedb
``` let it run, when back to the prompt issue the command ```
locate skype
```

---

### Post by Laforge129 on 2011-06-17
Something I would also try:

```
Sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get check
```

I just love the command line! ;)  I wouldn't be surprised if that doesn't fix it!

---

### Post by jtarin on 2011-06-17
> **Laforge129 said:**
> Something I would also try:

```
Sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get check
```

I just love the command line! ;)  I wouldn't be surprised if that doesn't fix it!I do too.....that's why I linked to it in my[ post]("http://ubuntuforums.org/showpost.php?p=10952041&postcount=14").

---

### Post by Sergio.G on 2011-06-18
Hope I can be any help.

You could also try to run the Skype static version from their website, here is the link:
(if I'm not mistaken, or anyone correct me if I'm wrong, this version carry its own "copy" of library just for Skype's use)

[INDENT][http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/downloading.static]("http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/downloading.static")[/INDENT]


Follow the instructions from Posts #18, #19, #20 and also delete or rename .skype folder from your /home/

Once you have the file, copy it to /opt/

and then from the command line type this to untar the file

```
tar -xvjf skype_static-<version>.tar.bz2
```

```
cd skype_static-<version>
```

```
skype
```

Cheers

---

