---
title: "How do i install stuff?? @#@&amp;^$@&gt;!!!!"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by Kangaji on 2011-05-06
(Ok. Let's try to work this out calmly... Breathe... Phew...)

So,  I got ubuntu on my computer, and I really like it. Problem is, whenever  I try to install something (Skype, EVE Online, RealPlayer), my computer  keeps telling me "unable to locate package".

WHY IS THIS?! WHY CAN'T I INSTALL ANYTHING?? CAN SOMEONE PLEASE PLEASE HELP ME?!

---

### Post by dronubu on 2011-05-06
Do you have internet connection? And what programme did you use?

---

### Post by alphacrucis2 on 2011-05-06
> **Kangaji said:**
> (Ok. Let's try to work this out calmly... Breathe... Phew...)

So,  I got ubuntu on my computer, and I really like it. Problem is, whenever  I try to install something (Skype, EVE Online, RealPlayer), my computer  keeps telling me "unable to locate package".

WHY IS THIS?! WHY CAN'T I INSTALL ANYTHING?? CAN SOMEONE PLEASE PLEASE HELP ME?!

Do you have the Canonical Partner repo enabled? That is the easiest place to install skype from. No idea why on Earth anyone would want realplayer but try this:

[https://help.ubuntu.com/community/RealPlayerInstallationMethods]("https://help.ubuntu.com/community/RealPlayerInstallationMethods")

I prefer vlc myself.

---

### Post by Kangaji on 2011-05-06
Yes. I have a working internet connection. I use the terminal to install programs. It's funny: Things from the Ubuntu Software Center will install. But if I need to install something outside of the software center it won't install...

---

### Post by StarZtorm on 2011-05-06
how do you try to install programs with the terminal? what commands do you use? whats the name of the file you are trying to install?

---

### Post by alphacrucis2 on 2011-05-06
> **Kangaji said:**
> Yes. I have a working internet connection. I use the terminal to install programs. It's funny: Things from the Ubuntu Software Center will install. But if I need to install something outside of the software center it won't install...

As I said for Skype, enable the partner repo. 

Read this [https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

See especially the section 5.1 Adding Canonical Partner Repositories.

---

### Post by Kangaji on 2011-05-06
> **StarZtorm said:**
> how do you try to install programs with the terminal? what commands do you use? whats the name of the file you are trying to install?


I'll generally use the command:
sudo apt-get install "name of file"

I'll generally download the file from the internet. For example, I'll download Realplayer (I need it for homework), or Skype. Recently, I also downloaded a game called Toribash, which has a version designed specifically for linux

---

### Post by Elfy on 2011-05-06
If you download a .deb from the internet you can't use apt-get install. You could right click it and I think the option now is to open with the software centre. You could install gdebi to do so as well.

If you've downloaded a tarball usually there is a readme inside the archive. 

If possible it is best to use the repos first, often you can find a PPA which once installed allows you to use apt-get.

The link from alphacrucis2 above needs to be read. 

Also - [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

### Post by alphacrucis2 on 2011-05-06
> **Kangaji said:**
> I'll generally use the command:
sudo apt-get install "name of file"

I'll generally download the file from the internet. For example, I'll download Realplayer (I need it for homework), or Skype. Recently, I also downloaded a game called Toribash, which has a version designed specifically for linux

I had a look at the Toribash site. There are two download options you can use. Either download the deb file - Debian Direct Download. (Ubuntu is a Debian based system). Double click the deb file after you have downloaded it to install. Or follow the instructions under the APT link.

---

### Post by Kangaji on 2011-05-06
> **alphacrucis2 said:**
> I had a look at the Toribash site. There are two download options you can use. Either download the deb file - Debian Direct Download. (Ubuntu is a Debian based system). Double click the deb file after you have downloaded it to install. Or follow the instructions under the APT link.


     Thanks for the information. That makes a lot more sense now. But I have a question. I tried to install Toribash using the method you explained. But when the software center opens, the install button is unclickable, and I see a description that reads "Wrong architecture i386". The same thing happens when I try to install Skype or Realplayer (I use Realplayer for homework). Do you happen to know what this means?

---

### Post by 3rdalbum on 2011-05-06
> **Kangaji said:**
> I'll generally use the command:
sudo apt-get install "name of file"

I'll generally download the file from the internet. For example, I'll download Realplayer (I need it for homework), or Skype. Recently, I also downloaded a game called Toribash, which has a version designed specifically for linux

If you've downloaded the file "from the internet", then apt-get is not what you want to do. Apt-get will look ONLY in the repositories.

I doubt you need Realplayer; as long as you have the non-free-codecs package from Medibuntu, you can play all Realplayer content. For instructions on how to add the Medibuntu repository and install the non-free-codecs package, see [www.medibuntu.org](www.medibuntu.org).

Instead of downloading the file from the Internet, see if there's a repository or PPA you can use. Skype is in the Canonical Partner repository, which the other posters have already mentioned. Enable this repository and you can just do "sudo apt-get install skype", or use Software Center.

If there's no repository you can add, then see if there's a Debian package (.deb). You can download it and then double-click it, and it will install.

If there's no Debian package and no repository/PPA, then you need to follow the instructions given on the program's website.

---

### Post by Kangaji on 2011-05-06
> **3rdalbum said:**
> If you've downloaded the file "from the internet", then apt-get is not what you want to do. Apt-get will look ONLY in the repositories.

I doubt you need Realplayer; as long as you have the non-free-codecs package from Medibuntu, you can play all Realplayer content. For instructions on how to add the Medibuntu repository and install the non-free-codecs package, see [www.medibuntu.org]("http://www.medibuntu.org").

Instead of downloading the file from the Internet, see if there's a repository or PPA you can use. Skype is in the Canonical Partner repository, which the other posters have already mentioned. Enable this repository and you can just do "sudo apt-get install skype", or use Software Center.

If there's no repository you can add, then see if there's a Debian package (.deb). You can download it and then double-click it, and it will install.

If there's no Debian package and no repository/PPA, then you need to follow the instructions given on the program's website.

Alright, I have a question for you though. I tried to get around some of these problems using WINE. But WINE doesn't seem to work either. It keeps saying that the file I'm using is not marked as executable, even though it is a .exe file. And I can't figure out how to mark it as executable. Any thoughts?
(Besides maybe the thought that I'm a complete idiot. Sorry, I'm normally pretty good with computers, but I've never learned Linux.)

---

### Post by alphacrucis2 on 2011-05-06
> **Kangaji said:**
> Thanks for the information. That makes a lot more sense now. But I have a question. I tried to install Toribash using the method you explained. But when the software center opens, the install button is unclickable, and I see a description that reads "Wrong architecture i386". The same thing happens when I try to install Skype or Realplayer (I use Realplayer for homework). Do you happen to know what this means?

If you are running 64 bit Ubuntu you will need the 64bit version (2nd section on the Toribash Download page. Could be the same issue with Skype. 
(ie 32 bit versus 64)

---

### Post by Kangaji on 2011-05-06
> **alphacrucis2 said:**
> If you are running 64 bit Ubuntu you will need the 64bit version (2nd section on the Toribash Download page. Could be the same issue with Skype. 
(ie 32 bit versus 64)


Nope. Already checked that one out. I'm running the 32-bit version of Ubuntu, and I tried installing BOTH versions just in case there was some sort of error on my part. Still doesn't work.

---

### Post by ExileAmongYou on 2011-05-06
To mark a file as executable, you right click on it, go to the "Permissions" tab, then tick the box that says "Allow executing file as program".

But you shouldn't have to use Wine to get Skype to work, or to play RealPlayer videos. Open the Software Center, go to Edit->Software Sources. Go to the Other Software tab, and tick the box next to "Canonical Partners". Then you should be able to search for and install Skype in the Software Center. It's always better to use Linux versions when they're available than to try to install the windows version through wine.

What happens right now when you click on a realplayer video file?

---

### Post by alphacrucis2 on 2011-05-06
> **Kangaji said:**
> Nope. Already checked that one out. I'm running the 32-bit version of Ubuntu, and I tried installing BOTH versions just in case there was some sort of error on my part. Still doesn't work.

Try this:

```
cd Downloads
sudo dpkg -i <the name of the deb file>
```

Don't type the < > just the file name including the .deb on the end

If it doesn't work then copy and paste the error message back here.

---

### Post by 3rdalbum on 2011-05-06
> **Kangaji said:**
> Alright, I have a question for you though. I tried to get around some of these problems using WINE.

Wine is a last-ditch effort to get some Windows programs to run on linux; it's not really appropriate to use Wine when you don't really need to. Use the PPAs, repositories and Deb packages for native Linux software wherever possible. But go on...

> But WINE doesn't seem to work either. It keeps saying that the file I'm using is not marked as executable, even though it is a .exe file. And I can't figure out how to mark it as executable. Any thoughts?

Linux's security system. All software must be marked with the executable flag. It's to stop people from downloading files named "kate-middleton-nude.jpg.exe" and double-clicking it and getting infected with a virus that's pretended to be a picture. You need to right-click the program, go to Properties, and then go to Permissions tab and check "Allow executing as a program".

Alternatively, open a terminal and type 'wine ' (with the space, but without the quotes) and then drag the Windows program in there. It will run without needing to be marked as executable.

However, DON'T use Wine when there's a native Linux version. Not only is it less likely to work through Wine, but it also won't integrate into your desktop, and it won't stay up-to-date with security patches.

---

### Post by Kangaji on 2011-05-06
> **ExileAmongYou said:**
> To mark a file as executable, you right click on it, go to the "Permissions" tab, then tick the box that says "Allow executing file as program".

But you shouldn't have to use Wine to get Skype to work, or to play RealPlayer videos. Open the Software Center, go to Edit->Software Sources. Go to the Other Software tab, and tick the box next to "Canonical Partners". Then you should be able to search for and install Skype in the Software Center. It's always better to use Linux versions when they're available than to try to install the windows version through wine.

What happens right now when you click on a realplayer video file?


Thanks a lot! This is good. At least, WINE is working anyway. :P
When I click on a realplayer file, the file will open with Movie Player. I'll use Movie Player, but sometimes I still need to use RealPlayer for some stuff. When I try to install RealPlayer through the software center, I still get the same "Wrong architecture i386" message.

---

### Post by ExileAmongYou on 2011-05-06
What other stuff do you need to use Realplayer for? It's possible there's another program in the Software Center that will do what you need. 

Also, like 3rdalbum said, please don't use Wine to install a Windows program when there's a Linux version available. I know it can seem like people are harassing you to do things in the Proper Linux Way, but we mean well. The Linux version will be much easier to use in the long run. Install Skype through the Software Center.

---

### Post by Kangaji on 2011-05-10
> **ExileAmongYou said:**
> What other stuff do you need to use Realplayer for? It's possible there's another program in the Software Center that will do what you need. 

Also, like 3rdalbum said, please don't use Wine to install a Windows program when there's a Linux version available. I know it can seem like people are harassing you to do things in the Proper Linux Way, but we mean well. The Linux version will be much easier to use in the long run. Install Skype through the Software Center.


Hey guys, sorry about that -- we just finished with finals and I just decided to boot Windows for a bit to finish my projects until I could finally figure out how to get this system to work. I really prefer it, you know. ~_^

Yes, I've tried to avoid WINE like the plague, in large part because it doesn't work for me that well. However, after trying all the stuff you guys told me to do, I STILL can't get it to work... I get this error message that says, "bash: syntax error near unexpected token `newline'". Any ideas?....
T_T

---

### Post by Jagoly on 2011-05-10
What command gives this?

Ok. What exactly, do you want in the end? eg, skype installed, video's played, Realplayer installed specifically (there is not a single format that it supports that is not supported by vlc, or movie player with extras)

to play pretty much any file, just type into a terminal:
```
sudo apt-get install ubuntu-restricted-extras
```
or
```
sudo apt-get install vlc
```

both of these are in the software center also.

The only real purpose for wine that I have found is gaming. Everything else has an often superior native linux alternative.

keep trying. you'll get the hang of it. I did.

---

### Post by wildmanne39 on 2011-05-10
Also I have found that if I must use a windows app which I almost never do, I use it in virtualbox so I can make windows do what I want it to do.:)

---

### Post by Jagoly on 2011-05-10
> **wildmanne39 said:**
> Also I have found that if I must use a windows app which I almost never do, I use it in virtualbox so I can make windows do what I want it to do.:)

not much good for gamers, though. But it is fun taking a snapshot of the system and then purposely install as many viruses as possible:popcorn:

---

