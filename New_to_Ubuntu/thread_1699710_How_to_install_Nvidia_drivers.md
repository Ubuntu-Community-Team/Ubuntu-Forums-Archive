---
title: "How to install Nvidia drivers"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by Jon Anderson on 2011-03-04
I just downloaded Nvidia 6600gt drivers(260.19.36) from Nvidia, it is in my download file. Can I get them into the list of proprietary drivers in the" additional drivers" program, so that I can download them from there. I can do that but if it is much harder then that and I'm going to have problems, I'm two weeks old in linux(ubuntu 10.10). I'm looking for the easiest way to get these drivers installed. I'll take all the advice everyone has.

Thanks 
Jon

---

### Post by spook1980 on 2011-03-04
yeah just use the additional drivers program, it's always what i use to install the nvidia drivers.

---

### Post by seawolf167 on 2011-03-04
I'd install the drivers you downloaded from nVidia, they always seem to give me more functionality. Plus they have just been updated.

[x86 drivers]("http://www.nvidia.com/object/linux-display-ia32-260.19.36-driver.html")
[x86_64 drivers]("http://www.nvidia.com/object/linux-display-amd64-260.19.36-driver.html")

The downloads are a .run file, and by default they will be saved in your ~/Downloads folder, so run the following commands from a terminal (Applications -> Accessories -> Terminal). Note: remember tab-completion so you don't have to type everything!

```
cd ~/Downloads
sudo chmod +x *filenamehere.run*
./*filenamehere.run*
```

---

### Post by fooman on 2011-03-04
jon,  use the "current [recommended]" ones from: system > administration > additional drivers

i very much doubt you will see any better performance using the drivers from the nvidia site.  besides,  installing/uninstalling the drivers from nvidia will be more complicated,  and you will lose them with every kernel update.

just my 2 cents.

---

### Post by Jon Anderson on 2011-03-04
> **seawolf167 said:**
> I'd install the drivers you downloaded from nVidia, they always seem to give me more functionality. Plus they have just been updated.

[x86 drivers]("http://www.nvidia.com/object/linux-display-ia32-260.19.36-driver.html")
[x86_64 drivers]("http://www.nvidia.com/object/linux-display-amd64-260.19.36-driver.html")

The downloads are a .run file, and by default they will be saved in your ~/Downloads folder, so run the following commands from a terminal (Applications -> Accessories -> Terminal). Note: remember tab-completion so you don't have to type everything!

```
cd ~/Downloads
sudo chmod +x *filenamehere.run*
./*filenamehere.run*
```

I don't know what tab completion is, I'm looking it up. , so each one of the lines of code you gave me , I put in terminal and then hit return, Three differents copy and paste is that corect? also do I wright the word filename or do I replace it with the name of the file that I'm installing and if that is the case what is the file name.. Also does the word code and quote go into the terminal also. Sorry for the questions, I don't want to type it in wrong.

---

### Post by vivek.pandey on 2011-03-04
yeah three copy pastes
you need to write the name of the file
actually what we are doing here  changing our directory to the place where the downloaded file is present if it is under downloads then Downloads as mentioned..so first check that out 
next we are running the script so you need to write the file name..also you can check out the read me or the installation manual they often provide one
no code no quote

i have  a question for you why arent you installing the drivers from additional drivers option?

---

### Post by Jon Anderson on 2011-03-04
> **fooman said:**
> jon,  use the "current [recommended]" ones from: system > administration > additional drivers

i very much doubt you will see any better performance using the drivers from the nvidia site.  besides,  installing/uninstalling the drivers from nvidia will be more complicated,  and you will lose them with every kernel update.

just my 2 cents.
 Thanks fooman, I went to additional drivers and downloaded the recommended drivers (there was 3 choices) And my mouse still froze so I'm downloading the drivers from Nvidia (260.19.36)

---

### Post by Jon Anderson on 2011-03-04
Yesterday I just left click over the Nvidia driver download file in firefox and I got a message saying that it wouldn't download. Today I did the same thing and this came up in my text editor--------
#
# /home/jbander/Downloads/NVIDIA-Linux-x86-260.19.36.run
#
# Configuration file for nvidia-settings - the NVIDIA X Server Settings utility
# Generated on Fri Mar  4 01:20:46 2011
#

# ConfigProperties:

RcFileLocale = C
ToolTips = Yes
DisplayStatusBar = Yes
SliderTextEntries = Yes
IncludeDisplayNameInConfigFile = No
ShowQuitDialog = Yes

# Attributes:
 Ok, does that means it is loaded?
I also tried to download it from the download file with seawolfs suggestion
cd ~/Downloads
sudo chmod +x *filenamehere.run*
./*filenamehere.run*
 I got a message saying there was no such file. When it put this in the terminal=
sudo chmod +x nvidia-linux-x86-260.19.36.run. So the terminal addressed the="cd ~/" but I couldn't get past the =sudo chmod +x nvidia-linux-x86-260.19.36.run



The download file in firefox is that the download  file the script is talking about because that is were it is at.

---

### Post by seawolf167 on 2011-03-04
Just about everything is case-sensitive in *nix systems, so you'll need to take that into account

```
cd ~/Downloads
sudo chmod +x NVIDIA-Linux-x86-260.19.36.run
./NVIDIA-Linux-x86-260.19.36.run
```Tab completion means you can hit the [tab] key and your system will try to auto complete your command/file name/etc.

An example, you can type (when in the /home/*yourusername*/Downloads folder)

```
./NVID
```then hit tab, and it'll auto complete the rest for you. Note: if you have more than one command/file name/etc. with the same letters as you typed in, hit [tab] twice and it'll give you a list of possible auto completes

---

### Post by Jon Anderson on 2011-03-04
jbander@ubuntujon:~$ cd ~/Downloads
jbander@ubuntujon:~/Downloads$ sudo chmod +x NVIDIA-Linux-x86-260.19.36.run
jbander@ubuntujon:~/Downloads$ ./NVIDIA-Linux-x86-260.19.36.run
./NVIDIA-Linux-x86-260.19.36.run: line 10: RcFileLocale: command not found
./NVIDIA-Linux-x86-260.19.36.run: line 11: ToolTips: command not found
./NVIDIA-Linux-x86-260.19.36.run: line 12: DisplayStatusBar: command not found
./NVIDIA-Linux-x86-260.19.36.run: line 13: SliderTextEntries: command not found
./NVIDIA-Linux-x86-260.19.36.run: line 14: IncludeDisplayNameInConfigFile: command not found
./NVIDIA-Linux-x86-260.19.36.run: line 15: ShowQuitDialog: command not found
jbander@ubuntujon:~/Downloads$ 

Well this doesn't look like it is working, can you see something or any suggestions

---

### Post by coolmego on 2011-03-04
for installing the nVidia driver just go to system > administration > additional drivers...the thread will automatically recognises the addituional drivers needed for your system...this is the most easiest way to get the drivers..click update according to your choice...thats it...have fun....

---

### Post by Jon Anderson on 2011-03-05
> **spook1980 said:**
> yeah just use the additional drivers program, it's always what i use to install the nvidia drivers. 

Thanks for the response, I have loaded the drivers that are in additional driver program but they don't work ,so I loaded the drivers directly from NVIDIA and I want to know how to install them,they are not in the additional driver program

---

### Post by gnarlygnarlingtons on 2011-03-21
I tried to use the additional drivers program to install the nvidia accelerated graphics driver and got this message:

SystemError: Failed to lock /var/cache/apt/archives/lock

What gives? How can I fix this? I can't watch videos or upgrade the visual effects on my computer without it.

---

### Post by vivek.pandey on 2011-03-21
> **gnarlygnarlingtons said:**
> I tried to use the additional drivers program to install the nvidia accelerated graphics driver and got this message:

SystemError: Failed to lock /var/cache/apt/archives/lock

What gives? How can I fix this? I can't watch videos or upgrade the visual effects on my computer without it.

it seems you are running two programs or applications which require your password, simultaneously. viz any two or more of these..additional drivers,symnaptic , software center or you have a sudo running on terminal..close all the rest whic are running except additional drivers ad try again

---

