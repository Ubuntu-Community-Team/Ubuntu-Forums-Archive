---
title: "When an installer is NOT in the &quot;Ubuntu Software Center&quot;, what is the recommended way"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by rocksockdoc on 2011-04-24
What is the recommended method of installing a program that is NOT in the Ubuntu Software Center?

For example, "Truecrypt" is not, to my knowledge, in the Ubuntu Software Center.

Therefore, for newbies such as myself, what is the recommended method of installing such programs?

Of course, I googled, and found various installation methods (e.g., see quoted text below for just one of many); but the question is **what is the RECOMMENDED method of installing such programs.**

> 
 				 				**Re: installing truecrypt** 			
 			 			 		   		 		 		**Step 1**
Go to the [TrueCrypt download page]("http://www.truecrypt.org/downloads") and scroll down until you get to the part where you select your Linux distribution and hardware platform.

**Step 2**
From the dropdown menu, select *Ubuntu - x86 .deb* (unless you're absolutely sure you install 64-bit Ubuntu, in which case you should get the x64 one).

**Step 3**
Click *Download*

**Step 4**
Right-click on *truecrypt-6.3a-ubuntu-x86.tar.gz* and select *Extract here*

**Step 5**
Double-click *truecrypt-6.3a-setup-ubuntu-x86*

**Step 6**
Select *Run*

**Step 7**
Select *Install TrueCrypt* and accept the license agreement

**Step 8**
This should launch GDebi (also called *Package Installer*). Click *Install Package*

Now if you go to Applications > Other > TrueCrypt, it should be in the menu.



[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189854&stc=1&d=1303624429[/IMG]

---

### Post by georgemc on 2011-04-24
Truecrypt 7-0a-1 is in synaptic.  Check synaptic first.

George

---

### Post by lisati on 2011-04-24
Is this a support request or a tutorial?

If this is a tutorial, it should be in "[Tutorials and tips]("http://ubuntuforums.org/forumdisplay.php?f=100")" but please read the stickies first.

---

### Post by earthpigg on 2011-04-24
if it isn't in synaptic (system -> admin -> synaptic) **or** software center;

go to the project's official website, google around, and see if ***you*** trust the project itself. Ubuntu users are not in the "trust every website and count on my antivirus to have the power of Jesus" paradigm. 

follow the project's website's directions and documentation. 

some projects advise the PPA route, some advice the click-here-to-download-.deb route. if you trust the project, than you ought to trust that advice for that project. for some types of a projects, a ppa makes the most sense and for others a .deb makes the most sense.

if you can't trust a project's documentation not to damage your computer, there's a good chance you cant trust the software they provide either. 

linux malware does exist, and has hurt people before. a gnome theme comes to mine - a .deb was the installer, and it damaged systems. that is why i say that it is up to ***you*** to decide if you trust the project.

that is my general opinion on the matter :)

---

### Post by rocksockdoc on 2011-04-24
> **georgemc said:**
> Truecrypt 7-0a-1 is in synaptic.  Check synaptic first

Hi George,
Thanks for the advice. I'll look up what 'synaptic' means. OK. I found what it means:
>  System -> Administration -> Synaptic Package Manager

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189859&stc=1&d=1303627382[/IMG]

Unfortunately, Truecrypt is NOT in either the "Ubuntu Software Center" nor in the "Synaptic Package Manager"; but that isn't the point. The question is what is the "process" for installing applications.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189860&stc=1&d=1303627385[/IMG]

So, Synaptic is yet another step toward the answer of the newbie question; but it's not the 'final' answer of what steps to take in what order to 'properly' install a desired program.  :(

QUESTION: In what order should we look for package installers:

[LIST=1]
[*]Applications -> Ubuntu Software Center
[*]System -> Administration -> Synaptic Package Manager
[*]What then?
[/LIST]

---

### Post by rocksockdoc on 2011-04-24
> **lisati said:**
> Is this a support request or a tutorial? 

While the way I ask questions is designed not only to get the answer but also to serve as a reference for others in the future (including myself), this is NOT a tutorial. How can it be when I don't even know the answer myself. 

So, it's definitely a question.

The question is how is a newbie "supposed" to install programs, especially when, as in this case, the program to be installed is NOT in the Ubuntu 10.04 "Ubuntu Software Center" or in the "Synaptics Package Manager".

Another related example, BTW, is I'm trying to install the [Sourceforge "ScramDisk 4 Linux]("http://sd4l.sourceforge.net/")" utility, which is also not in either of those two repositories. 

So, the question is what is the NEXT step in installing software when the first two fail?

[LIST=1]
[*]Applications -> Ubuntu Software Center
[*]System -> Administration -> Synaptic Package Manager
[*]Are you then forced to go to [the web page of the software developer]("http://sd4l.sourceforge.net/")?
[LIST]
[*]And, if so, what FORMAT is the recommended format
[*](and how do you keep a record of it and uninstall when necessary?)
[/LIST]
[/LIST]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189861&stc=1&d=1303628126[/IMG]

---

### Post by rocksockdoc on 2011-04-24
> **earthpigg said:**
> if it isn't in synaptic (system -> admin -> synaptic) **or** software center;
go to the project's official website ... follow the project's website's directions and documentation. 

OK. I guess it's a three-step process:

[LIST=1]
[*]Applications -> Ubuntu Software Center
[*]System -> Administration -> Synaptic Package Manager
[*]Software Developer Website -> Follow Directions of the Developer
[/LIST]
 > **earthpigg said:**
> some projects advise the PPA route, some advice the click-here-to-download-.deb route. if you trust the project, than you ought to trust that advice for that project

OK. The Truecrypt web site advised a tar.gz file, which then extracted to an installer executable which then ran its own setup script. Who knows what it does or how it works but, I guess I trust it; so I ran it and it installed somehow into /usr/bin/truecrypt.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189862&stc=1&d=1303628707[/IMG]

> **earthpigg said:**
> linux malware does exist, and has hurt people before. a gnome theme comes to mine - a .deb was the installer, and it damaged systems

Interestingly, when trying the same procedure for ["ScramDisk for Linux]("http://sd4l.sourceforge.net/")", which was on Sourceforge, this time an SD4l "*.deb" file was downloaded (whatever that is), which then failed to install anyway. :(

Here's a screenshot of what the SD4L developers decided to provide:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189865&stc=1&d=1303629215[/IMG]

And, here's what happened when that "*.deb" file was executed in Ubuntu 10.04:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189866&stc=1&d=1303629217[/IMG]

---

### Post by cotcot on 2011-04-24
Gdebi package installer is fine. Just click OK and the installer will install the package.
It is one of the methods that erathpigg mentioned.

---

### Post by earthpigg on 2011-04-24
if you have to download the installer from the developer then they would, ideally, provide an Ubuntu .deb file. ProjectName_VersionNumber.deb is our version of the ubiquitous ProjectName_Setup.exe for windows.

The error message you saw, "Depend not satisfiable: Linux 2.6.35-28", is interesting. My Ubuntu system is about a week out of date, and I'm at 2.6.35-2_**7**_.

Is this beta or testing software you are attempting to install?

---

### Post by ivanovnegro on 2011-04-24
If you ask me, a newbie can install first from the Software Center and thats all. :D
Of course that cannot be the solution every time, so the next step would be the Synaptic Package Manager but attention with it as you can see all details there and you can mess it up if you remove something that is needed for another program (dependencies), happens all the time here on the forums. But both contain the same apps.
The next step would be to go for a [PPA]("https://launchpad.net/ubuntu/+ppas"), you can add it to your sources list and it will pop up in the Software Center and in Synaptic. In addition to it you could use a Deb file that will install the program on your system like an Exe file of Windows.

I think thats all.

The last thing and thats what I do if I want to use the latest and greatest because Im testing the product, filing the bugs, improving the application, playing with the new features etc, is compiling myself from source. 

So, there is no real order, if you want to stay really in the right order of Ubuntu, then maybe the Software Center is all (including Synaptic). The rest is additional.

---

### Post by rocksockdoc on 2011-04-24
> **earthpigg said:**
>  "Depend not satisfiable: Linux 2.6.35-28", is interesting. My Ubuntu system is about a week out of date, and I'm at 2.6.35-2_**7**_. Is this beta or testing software you are attempting to install?

I just installed Ubuntu 10.04 a week ago (due to Ubuntu pulling the Windoze trick of chewing itself up) and then the package update ran so I'm not sure how to tell how old my Ubuntu is, but, it's an almost pristine 10.04 Lucid version.

As for the software I'm trying to install, it's merely the recommended Truecrypt alternative according to the advice provided to me in this recent thread (I know no more than that about the versions):
[Absolute Beginner Talk]("http://ubuntuforums.org/forumdisplay.php?f=326") -> [Ubuntu 10.04 Truecrypt 7.0 Where is the auto-dismount on screensaver option?]("http://ubuntuforums.org/showthread.php?t=1567703")

See [post #3 in that thread]("http://ubuntuforums.org/showpost.php?p=9820291&postcount=3") which advised installing "ScramDisk 4 Linux" but which doesn't provide a path to the installation program so that's one reason why I ask here what is the PROPER way to find such an installer.

> **rotave said:**
> You could try  "ScramDisk 4 Linux". It supports truecrypt drives up to version 6.3a. It  gives you the option of setting a container inactivity timeout option  where it will auto dismount after a user set period of  inactivity.
- 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189875&stc=1&d=1303632164[/IMG]

---

### Post by rocksockdoc on 2011-04-24
Since this is a new Ubuntu 10.04 installation, another related question is where are we "supposed" to get our video-playing codecs?

There seem to be multiple places for the 'proper' place to obtain multi-media codecs, e.g., 

[LIST=1]
[*]The Ubuntu Software Center seems to have some codecs
[*]The Synaptic Package Manager seems to have some codecs
[*]I wonder if there is a canonical site for all the codecs?
[LIST]
[*](such as the complete "[K-Lite Codec Pack]("http://www.codecguide.com/download_kl.htm")" for Windows)
[/LIST]
 
[/LIST]
So, which is the 'proper' place to obtain necessary multi-media codecs?

For example, here are the codecs available in the Ubuntu Software Center:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189877&stc=1&d=1303635717[/IMG]

Yet, when I click on various movie files, the Synaptics Package Manager seems to run in batch mode (but look at what it installs).
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189879&stc=1&d=1303636211[/IMG]

Keeping track of what the automatic Synaptics Package Manager installed for codecs, it seemed to get:

[LIST]
[*]- gstreamer0.10-ffmpeg MPEG-1 Layer 3 (MP3) decoder
[*]- gstreamer0.10-fluendo-mp3 MPEG-1 Layer 3 (MP3) decoder
[*]- gstreamer.10-plugins-ugly MPEG-1 Layer 3 (MP3) decoder
[*]- gstreamer0.10-plugins-ugly Advanced Streaming Format (ASF) demuxer
[*]- gstreamer0.10-ffmpeg Windows Media Video 8,9 decoder
[*]- gstreamer0.10-plugins-bad MPEG-4 AAC decoder
[*]etc. (each package above can have a score of associated files)
[/LIST]
Yikes! Look at those file names! 

So, my question on codecs is similar to that for installation files.

Q: What is the "proper" (i.e., recommended) way to install (and keep track of to uninstall) codecs on Ubuntu?

---

### Post by el_koraco on 2011-04-24
The easiest way is to install the metapackage ubuntu-restricted-extras, which will pull all the gstreamer plugins needed to play files. It would probably be wise to do it through synaptic or the terminal, and make a note of all the packages installed, in case you need to uninstall them.

---

### Post by LewRockwellFAN on 2011-04-24
> **georgemc said:**
> Truecrypt 7-0a-1 is in synaptic.  Check synaptic first.

George
Not in MY synaptic. It it is in yours perhaps you have added reposititory. Or maybe it just doesn't show for lucid. I doubt that though. There are 2 programs in the repositories that claim to have some degree of truecrypt compatibility though. I think you can get a deb for Truecrypt.

---

### Post by ivanovnegro on 2011-04-24
@OP: Yeah, just install the Deb and for the codecs like mentioned, add the restricted extras repository, there is no reason to complicate it. If a newbie would read this thread he would not understand what is going on here IMO.

In general to install apps:

1. Software Center/Synaptic 
2. Third party (PPA/Deb file)
3. Sourcecode (compiling)

---

### Post by rocksockdoc on 2011-04-24
> **LewRockwellFAN said:**
> Not in MY synaptic....There are 2 programs in the repositories that claim to have some degree of truecrypt compatibility though. I think you can get a deb for Truecrypt.

Not in mine either (Ubuntu 10.04 Lucid).

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189860&stc=1&d=1303627385[/IMG]

---

### Post by rocksockdoc on 2011-04-24
> **ivanovnegro said:**
> 
1. Software Center/Synaptic 
2. Third party (PPA/Deb file)
3. Sourcecode (compiling)

OK. I don't know what PPA means ... searching here, I get "parallel port adapter" but that can't be right. Adding more search terms, I find it has something to do with repositories:
- [Easy Way to Add PPA Repositories in Ubuntu Linux : apt-add-repository]("http://shibuvarkala.blogspot.com/2010/02/easy-way-to-add-ppa-repositories-in.html")
- [**SOLVED: adding ppa to software center**]("http://ubuntuforums.org/showthread.php?t=1738169&highlight=ppa")
- [ubuntu: **Repository error**]("http://ubuntuforums.org/showthread.php?t=1736999&highlight=ppa")

But none of these say what a PPA actually is (nor what the letters stand for). 

Widening the search (e.g.,  "What does Ubuntu PPA mean"), I find it's a development 'service':
- [[FONT=Arial,Helvetica][SIZE=2]Launchpad PPA Service: Software [COLOR=darkgreen]_[COLOR=darkgreen][/COLOR]_[/COLOR]Development the Ubuntu Way[/SIZE][/FONT]]("http://desktoplinux.com/news/NS5056230026.html")

> [FONT=Arial,Helvetica][SIZE=3]During the Ubuntu Live Conference  in Portland, Ore., Canonical announced the beta release of its Launchpad  PPA (Personal Package Archive) service, a new way for developers to  build and publish packages of their code, documentation, artwork, themes  and other contributions to free software. [/SIZE][/FONT]

Reading further to find out what the practical implications of a "Personal Package Archive" service is to me, as a user, I find not much by way of explanation since it seems to clearly be aimed at developers' beta-testing needs:
> [FONT=Arial,Helvetica][SIZE=3]Matt Zimmerman, CTO of Canonical  claimed that PPAs' also make it easy for developers to test new and  experimental software builds.  ... [/SIZE][/FONT][FONT=Arial,Helvetica][SIZE=3]The PPA service allows anyone to publish a package without having to ask permission or join the Ubuntu project as a developer.[/SIZE][/FONT]

Anyway ... I'll add PPA (whatever the practical implications to a user) to what we already have.

**How does 'this' look for the 'proper' sequence for installing packages (preference items on top):**

[LIST=1]
[*]Applications -> Ubuntu Software Center
[*]System -> Administration -> Synaptic Package Manager
[*]Software Developer Website -> Follow Directions of the Developer
[LIST]
[*]Deb
[*]PPA
[*]Source code compile
[/LIST]
[/LIST]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189920&stc=1&d=1303666220[/IMG]

---

### Post by ivanovnegro on 2011-04-24
Yes, you answered it yourself.
Thats the easiest way to install third party apps that are not yet in the official repositories of Ubuntu and this is also an advantage of Ubuntu in general, but that does not mean that other OSs dont have something similar.
Its not only for developers and testers, there is a bunch of stable PPAs you can add to your repository to be able to use them or to have an app up-to-date, e.g. VLC. VLC is always in the offcial repos but is not updated to a newer version until the next release. So, if you want to have a newer version in the meantime you can remove VLC and add the VLC PPA to your sources list and this way it will also stay up-to-date because it will recieve new updates and it is indeed a stable package, not experimental. Also there are dev PPAs for testers. It is very flexible.
In the Software Center you can read e.g. the description of an app and in case of VLC you can see, "this program wont recieve updates, a newer version is instead available from the community", something like this, just try it, search for apps in the Software Center.

---

