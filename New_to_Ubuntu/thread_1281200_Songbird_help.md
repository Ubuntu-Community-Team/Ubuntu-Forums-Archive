---
title: "Songbird help?"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by xFlowx on 2009-10-03
**EDIT: Please stop telling me about the deb files. They are not working, and now I can't get songbird to even open up properly. I try to open it, and it appears on my..task-bar type thing, but then it dissapears. So now whenever I try to open it, I have to restart my computer. The Tar file didn't work, either.**


Okay, so I've had songbird before, but then my computer crashed and I lost everything...I had to go back and re-install ubuntu on my computer, and now I'm trying to get Songbird to work.

I've had a similar problem to this ome before, and it was answered. This is the old thread of it: [http://ubuntuforums.org/showthread.php?t=1221584](http://ubuntuforums.org/showthread.php?t=1221584)

But I've gone back and did what fixed it last time, but now it won't work. I accidentally downloaded and installed the 64 bit of it when I needed the 32 bit, so I think that's confusing my computer.

Anyway, when I fallow this: [https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird) , it doesn't work. It tells me the same error I had before.

Now, when I'm doing things in the terminal...this is what I get: A popup box that says "You appear to have an x86 architecture. Do you want to install the i686 version of songbird?" with the potions of Cancel and Okay.

Then, I paste the second thing the instructions say: ```
flow@flow-desktop:~$ cd ~/Desktop
flow@flow-desktop:~/Desktop$ chmod +x installsongbird.sh
flow@flow-desktop:~/Desktop$ ./installsongbird.sh
0
--2009-10-02 23:53:42--  http://www.xs4all.nl/~mgj1/Songbird/32.bit
Resolving www.xs4all.nl... 194.109.6.92
Connecting to www.xs4all.nl|194.109.6.92|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-10-02 23:53:42 ERROR 404: Not Found.

head: cannot open `32.bit' for reading: No such file or directory
head: cannot open `32.bit' for reading: No such file or directory
rm: cannot remove `32.bit': No such file or directory
tar: : Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
mv:                                                                                                                                                                                                                                                            cannot stat `Songbird': No such file or directory
                                                                                                                                                                                                             rm: cannot remove `Songbird*.tar.gz': No such file or directory
rm: cannot remove `/usr/bin/Songbird': No such file or directoryflow@flow-desktoflow@flow-desktop:~/Desktop$ 

```Please help! I have no idea on what to do... This is frustrating and I really like the program D:

Thank you for any and all help...!

**Edit: it's still not working, and it won't open. It keeps telling me that I have to close the songbird to open it...Dx**

---

### Post by starcannon on 2009-10-03
Go here:
[http://www.getsongbird.com/download/](http://www.getsongbird.com/download/)

Download the Linux version that equates to the Ubuntu version your using 
"Linux i686"==32bit and "Linux x86_64"==64bit.

Go to the location that the file downloaded to, default is ~/Desktop
R-click and choose "Extract Here"
Open the Songbird folder that appears after extraction is done.
Double click on the file named "Songbird"
Click on "Run"
Enjoy Songbird.

---

### Post by oboedad55 on 2009-10-03
> **starcannon said:**
> Go here:
[http://www.getsongbird.com/download/](http://www.getsongbird.com/download/)

Download the Linux version that equates to the Ubuntu version your using 
"Linux i686"==32bit and "Linux x86_64"==64bit.

Go to the location that the file downloaded to, default is ~/Desktop
R-click and choose "Extract Here"
Open the Songbird folder that appears after extraction is done.
Double click on the file named "Songbird"
Click on "Run"
Enjoy Songbird.

Or you could download a .deb here: [http://www.getdeb.net/search.php?keywords=songbird](http://www.getdeb.net/search.php?keywords=songbird)

---

### Post by xFlowx on 2009-10-03
> **starcannon said:**
> Go here:
[http://www.getsongbird.com/download/](http://www.getsongbird.com/download/)

Download the Linux version that equates to the Ubuntu version your using 
"Linux i686"==32bit and "Linux x86_64"==64bit.

Go to the location that the file downloaded to, default is ~/Desktop
R-click and choose "Extract Here"
Open the Songbird folder that appears after extraction is done.
Double click on the file named "Songbird"
Click on "Run"
Enjoy Songbird.

Thanks!
That helped a little bit, but I got another error message. This time, it says "Could not launch 'Songbird' Failed to execute child process ' 'Songbird' '(No such file or directory)"

Any ideas? D:

---

### Post by ubuntu27 on 2009-10-03
You can download Songbird deb file for Ubuntu at GetDeb.net:

[http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird)

---

### Post by xFlowx on 2009-10-03
> **ubuntu27 said:**
> You can download Songbird deb file for Ubuntu at GetDeb.net:

[http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird)
 
I already have like two .debs downloaded from there...

---

### Post by ubuntu27 on 2009-10-05
> **xFlowx said:**
> I already have like two .debs downloaded from there...

Why are you trying to compile then? Did the debs not work for you?

---

### Post by khelben1979 on 2009-10-05
> **starcannon said:**
> Go here:
[http://www.getsongbird.com/download/](http://www.getsongbird.com/download/)

Download the Linux version that equates to the Ubuntu version your using 
"Linux i686"==32bit and "Linux x86_64"==64bit.

Go to the location that the file downloaded to, default is ~/Desktop
R-click and choose "Extract Here"
Open the Songbird folder that appears after extraction is done.
Double click on the file named "Songbird"
Click on "Run"
Enjoy Songbird.

I agree on this one. Good advice.

---

### Post by misfitpierce on 2009-10-05
[http://www.getdeb.net](http://www.getdeb.net) is the place to go for songbird and tons of other .deb app's.

---

### Post by pmlxuser on 2009-10-05
why not just download the  tar.gz file found on the songbird site. extract and run it.

you can easily creat a script for launching it easily etc. thats what i did when the normal debs gave me alot of problems...

---

### Post by xFlowx on 2009-10-07
> **ubuntu27 said:**
> Why are you trying to compile then? Did the debs not work for you?

I'm not trying to compile them...No, the debs did not work. That's why I'm asking. I already downloaded like two or three versions, and each time it keeps giving me a different error message. This is so frustrating.

---

### Post by xFlowx on 2009-10-07
> **ubuntu27 said:**
> You can download Songbird deb file for Ubuntu at GetDeb.net:

[http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird)

I already downloaded a deb three times from there.

---

### Post by xFlowx on 2009-10-07
> **pmlxuser said:**
> why not just download the  tar.gz file found on the songbird site. extract and run it.

you can easily creat a script for launching it easily etc. thats what i did when the normal debs gave me alot of problems...
That didn't work, it's not running...

---

### Post by oboedad55 on 2009-10-07
On my system to get songbird to work I need to go into synaptic and uninstall libvisuals-0.4-plugins. Otherwise it will start to open and then hang.

---

### Post by starcannon on 2009-10-07
> **xFlowx said:**
> That didn't work, it's not running...
Try running it from a terminal, and it may spit out the error code.
```
cd ~/location/of/songbird
./songbird

```
Then copy paste the contents of the terminal output into a code box back here on this thread.

GL

---

### Post by xFlowx on 2009-10-07
> **oboedad55 said:**
> On my system to get songbird to work I need to go into synaptic and uninstall libvisuals-0.4-plugins. Otherwise it will start to open and then hang.

That fixed it, thank you.

---

### Post by oboedad55 on 2009-10-07
> **xFlowx said:**
> That fixed it, thank you.

No sweat, glad it worked.

---

