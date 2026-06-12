---
title: "I don't know how to install a tar.gz!!!"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by DizzyEwok on 2008-12-12
I have recently downloaded a *.tar.gz file off the internet. I have extracted it using Archive Manager but I do not know what to do from now onwards. I am used to using sudo apt-get install but it is not available for this program!
PLz could someone give me step-by-step instructions on how to install the program...
Thanks in advance!

---

### Post by Perfect Storm on 2008-12-12
Can you tell us what you're trying to install. Their might be a .deb version.

---

### Post by tszanon on 2008-12-12
> **DizzyEwok said:**
> I have recently downloaded a *.tar.gz file off the internet. I have extracted it using Archive Manager but I do not know what to do from now onwards. I am used to using sudo apt-get install but it is not available for this program!
PLz could someone give me step-by-step instructions on how to install the program...
Thanks in advance!
It's usually this way. Go to the folder where you extracted the files and type these commands:
```
./configure
make
make install
```
Both **configure** and **make** may take some minutes to finish.

---

### Post by kansasnoob on 2008-12-12
> **Artificial Intelligence said:**
> Can you tell us what you're trying to install. Their might be a .deb version.

+1. Also tar.gz's are individually different.

---

### Post by Duck2006 on 2008-12-12
As "Artificial Intelligence" posted it is better to install it from a *.deb file but if it's not found in a deb file this may help.

[http://www.psychocats.net/ubuntu/installingsoftware#lastresorts](http://www.psychocats.net/ubuntu/installingsoftware#lastresorts)

---

### Post by Therion on 2008-12-12
Best answer I can give you...

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

Compiling from source is, I'm convinced, 50% Science and 62% Dark Art.

---

### Post by DizzyEwok on 2008-12-12
> **tszanon said:**
> It's usually this way. Go to the folder where you extracted the files and type these commands:
```
./configure
make
make install
```
Both **configure** and **make** may take some minutes to finish.
I have tried but I do not know exactly what I need to type???!!!
The folder I am trying to install is called john-1.7.2
Could you now edit the code so it is exactly what I have to type in??
Thanks

p.s. I am a bit of a beginner!

---

### Post by gandaran on 2008-12-12
> **DizzyEwok said:**
> I have recently downloaded a *.tar.gz file off the internet. I have extracted it using Archive Manager but I do not know what to do from now onwards. I am used to using sudo apt-get install but it is not available for this program!
PLz could someone give me step-by-step instructions on how to install the program...
Thanks in advance!
read the readme file for instructions and you'll need to install **build-essential** package (apt-get or synaptic) for compiling

---

### Post by Perfect Storm on 2008-12-12
Which version of Ubuntu do you use? In Ubuntu 8.10 John 1.7.2 is available.

Note: I hope you're not going to use it for malicious activity. We do not welcome that here on the board or people that do such stuff.

---

### Post by Duck2006 on 2008-12-12
> **DizzyEwok said:**
> I have tried but I do not know exactly what I need to type???!!!
The folder I am trying to install is called john-1.7.2
Could you now edit the code so it is exactly what I have to type in??
Thanks

p.s. I am a bit of a beginner!

Did you cd to where the file is. If the file is on the Desktop,

cd ~/Desktop

Then do the commands.

---

### Post by Dedoimedo on 2008-12-12
Hello,

You do it like this:

1. Extract the archive, either right-clicking on it via Nautilis, the file manager or via the command line:

```

tar zxvf archive.tar.gz

```

2. Navigate into the extracted folder and READ:

Makefile
Readme

And other text files that actually explain how to configure the package and install it.

3. Install, usually the sequence of these three commands:

```

./configure
make
make install

```

Lastly - or rather, firstly - to compile you will need the build-essential package installed, which contains the gcc, make, kernel-source, and kernel headers.

```

sudo apt-get install build-essential

```

You may want to read:
[http://www.dedoimedo.com/computers/linux_commands.html](http://www.dedoimedo.com/computers/linux_commands.html)

Especially the section Compilation (from sources).

Cheers,
Dedoimedo

---

### Post by DizzyEwok on 2008-12-12
I am using 8.10, what do you mean it is available???
When you say type```
./configure
```
What do I actually type because if I type that then it says ```
bash: ./configure: No such file or directory

```!!!

---

### Post by Perfect Storm on 2008-12-12
It's available through synaptic Package Manager.

---

### Post by Paqman on 2008-12-12
> **Artificial Intelligence said:**
> It's available through synaptic Package Manager.

+1 

Always, always check Synaptic before downloading software from the net. It's by far the safest and easiest way to install things.

---

### Post by DizzyEwok on 2008-12-12
Thankyou, I didn't realise!

---

### Post by donkyhotay on 2008-12-12
It might also help if we knew what was within the tar.gz file. As you've probably seen by the all posts there is no one way to 'install' this type of file. A tar.gz file is simply a compressed file format (like a .zip file on windows). Within the compressed file can be almost anything. Usually when you recieve a tar.gz to install it has source code within it that needs to be installed (this is what the make commands everyone else mentioned is about). Problem is although this is the most common type of file to install within a tar.gz it isn't the only one. It is possible to have a .deb file within a tar.gz or even a pre-compile binary. It's also possible to use another system for compiling such as scons rather then makefile. You're probably better off going to the website you downloaded the tar.gz is from and look for installation instructions. Either that or look for a README file within the tar.gz file for installation instructions. If you really have problems post a link of the site you got the file from so we can take a look and find out what is inside in order for us to give you instructions specific to that program.

Oh and yes, if it's in the repos always use that first.

---

