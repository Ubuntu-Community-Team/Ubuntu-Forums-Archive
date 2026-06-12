---
title: "solved presario c304nr ndiswrapper driver, alternative to non-functioning hp download"
date: 2006-12-20
forum: Networking &amp; Wireless
---

### Post by bvmou on 2006-12-20
I could have used a few of these pointers 30 hours ago; I have seen a number of related or identical problems. 

The hp.com driver in the product information list did not work with my machine; using ndiswrapper produced a "bad magic" error message and NDIS seemed to be expecting a 32-bit driver rather than the 64 bit provided by the manufacturer.

This Dell driver -- ftp.us.dell.com/network/R115321.EXE -- worked a charm.

I also found that I was better off not installing NDISWrapper from synaptic; apparently conflicting modules resulted from whatever sequence I (mis) used.  I loaded a script -- [bcm4318.all.tar.gz]("http://ubuntuforums.org/showthread.php?t=197102") -- provided by a community member for a slightly different driver.  I did not expect that driver to work but it has an apt-get command that targets whatever ndiswrapper-utils I was abusing.  Then, with sudo ndiswrapper -e bcml5, i removed the imprecise driver, and replaced it with the Dell driver.

The sequence was: Install Ubuntu [and upgrade to Edgy] - Get Dell executable - Run bcm4318.all.tar.gz - Replace the installed 4318 NDISwrapper driver with the Dell 4311 (bcmwl.inf) driver - Install gnome Network Manager.  

Experienced users please advise if this is appropriate form/content/forum.  Thanks to the many posters who enabled me to take care of this.

---

### Post by manishk on 2007-02-26
Finally, a tutorial on NDISWrapper that worked (for me). All credits and thanks to bvmou :) 

My system is a HP Compaq nx6325 which comes with a bcm4311 wireless card.

After following the *conventional* approach stated in many HowTos about using NDISWrapper with the HP Windows driver I got a 'Bad Magic' error that shows during boot up as posted here [http://www.ubuntuforums.org/showthread.php?t=353447](http://www.ubuntuforums.org/showthread.php?t=353447)

But thanks to bvmou, now its up and running.

Heres what I did:
(Assuming that the following are already installed
**ndisgtk 		                v0.6-0ubuntu1**
ndiswrapper-common 	v1.18-1ubuntu2
ndiswrapper-utils 	        v1.1-5
ndiswrapper-utils-1.1 	     v1.1-5
ndiswrapper-utils-1.8 	     v1.18-1ubuntu2)

1. Downloaded the DELL driver as stated above and 'goto' to that folder.

2. Blacklist bcm43xx, as stated above.

3. In terminal:
```
$cabextract r115321.exe
```

For some strange reason it did NOT work. It gave me this error
[I]r115321.exe: no valid cabinets found

All done, errors in processing 1 file(s)[/I] 

3. Lucilky I had Wine. So I did
```
$wine r115321.exe

```
 I had to select a folder to extract the files before the actual installation started. Of course, the actual installation gave an error saying that the hardware wasn't found.

4. Then just used ndisgtk (the GUI) to load the .inf file. *Settings>Adminstartion>Windows Wireless Drivers*

The Wi-Fi indicator light on the keyboard came up immediately!!!

5. Restarted.


Note: I didn't run the script because I did not have an option of wired net connection.

---

### Post by manishk on 2007-04-27
Just tried it on Feisty and it works like a charm in that too!

---

### Post by mehdymehdy on 2007-08-25
hello , i have a compaq presario c304nr . i'm new to lunix . i followed many how to's but in each of them i fail to understand what the instruction is saying to me . please if there is any good thread on how to install the ndiswrapper which works with the dell wireless driver. or a clean instruction on how to do this step by step. also what does it mean when they say . IN THE TERMINAL GO TO DIRCTORY WHERE YOU EXTRACTED THE NDISWRAPPER.  i mean is there a code to do that . and if there is why don't they say so.

---

### Post by manishk on 2007-08-25
I guess the above method should work for you too!

First, please tell me if you have access to wired net connection...if so the steps become a lot easier.

---

### Post by mehdymehdy on 2007-08-26
thank you, yes i do have wired connection. I'm trying to understand how to do this but up to this moment it didn't work .  i installed the dell driver in a file and named it ndiswrapper , i tried installeig nidiswrapper 1.47 but i get errors. i installed the bcmwl5.inf and when i check it , it says it's allready installed . so i don't know how i need to start. and how i should do this .thanks for your help.

---

### Post by manishk on 2007-08-31
Whoa...thats a lot of confusion!! 

You say that you couldn't install NDISWrapper, right? Then how can bcmwl5.inf be installed.

Open a terminal and type *ndis* and then press tab. Tell me what the output is.

Also open Synaptic, search and tell me what all packages are installed starting with *ndis*

---

