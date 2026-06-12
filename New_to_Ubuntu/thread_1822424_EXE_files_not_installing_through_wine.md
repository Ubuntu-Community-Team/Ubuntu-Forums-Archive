---
title: "EXE files not installing through wine"
date: 2011-08-10
forum: New to Ubuntu
---

### Post by 1ktmeadows on 2011-08-10
Hi Im new to ubuntu 11.04 and I have been trying to install three exe files and none of them been able to install. I download the application wine already and when I try to open the application through wine, the exe file will not open or install completely. The three exe files that I have been trying to is MP3 Rocket, Mixcraft 5, and Street of Rage Remake V5. I was wondering if anyone inform or give me some advice so that I can download these exe files.

---

### Post by TeoBigusGeekus on 2011-08-10
Open a terminal, give
```
wine /path/to/executable/filename.exe
```
and post us any error messages.

---

### Post by Daveth on 2011-08-10
they don't feature heavily in the Wine database....

[HTML]http://appdb.winehq.org/index.php[/HTML]

---

### Post by 1ktmeadows on 2011-08-10
I want to first say Thank You for responding back. I typed in the terminal, wine  /path/to/executable/mp3rocket.exe and the response that I got was wine: cannot find '/path/to/executable/mp3rocket.exe' and then I typed "wine /path/to/executable/mp3rocket.exe" and then the response was bash: wine /path/to/executable/mp3rocket.exe:  No such file or directory. I saved the mp3rocket.exe file in my Downloads. Is there something that I'm doing wrong?

---

### Post by corncob on 2011-08-10
> **TeoBigusGeekus said:**
> Open a terminal, give
```
wine /path/to/executable/filename.exe
```
and post us any error messages.

I often find this
```
/path/to/executable/filename.exe
```
formidable and just type wine (plus a space) into the terminal and drag in the exe file from the file browser.  That takes care of the path.  [CTRL][ALT][t] should open the terminal.
BTW, welcome to the forum!

---

### Post by anewguy on 2011-08-10
> **1ktmeadows said:**
> I want to first say Thank You for responding back. I typed in the terminal, wine  /path/to/executable/mp3rocket.exe and the response that I got was wine: cannot find '/path/to/executable/mp3rocket.exe' and then I typed "wine /path/to/executable/mp3rocket.exe" and then the response was bash: wine /path/to/executable/mp3rocket.exe:  No such file or directory. I saved the mp3rocket.exe file in my Downloads. Is there something that I'm doing wrong?

What they meant for you to do was to substitute the real path where it say /path/to/executable/mp3rocket.exe.

As an example, let's say you downloaded a package called mp3rocket and by default it went to your downloads folder.  Let's also say you unpacked that file and it created a mp3rocket subfolder and put the .exe there.  The statement would then look like this:

wine ~/Downloads/mp3rocket/mp3rocket.exe

---

### Post by 1ktmeadows on 2011-08-10
I tried typing /path/to/executable/mp3rocket.exe and the terminal respond with bash: /path/to/executable/mp3rocket.exe: No such file or directory then I tried wine /Download/mp3rocket/mp3rocket.exe and I got wine: cannot find '/Download/mp3rocket/mp3rocket.exe'.  Im not sure what Im doing wrong, do you think wine wont be able to open this mp3rocket.exe file? Is another way getting this file to work ?
Thank You again for responding back.

---

### Post by Paqman on 2011-08-10
> **1ktmeadows said:**
> Im not sure what Im doing wrong

You're entering the wrong path. Please carefully read anewguy's post above, or do what corncob suggested.

---

### Post by 1ktmeadows on 2011-08-10
I did what they said to type in the terminal, how Im suppose to type it in the terminal becasue I typed exactly what they said to type in the terminal.

---

### Post by Paqman on 2011-08-10
> **1ktmeadows said:**
> I did what they said to type in the terminal, how Im suppose to type it in the terminal becasue I typed exactly what they said to type in the terminal.

What you need to type into the terminal (or drag into it, as corncob suggested) is the path to YOUR file, which is not necessarily what they posted.

I suggest you follow corncob's advice, type:
```
wine 
```
then drag the file into the terminal. This will fill the correct path out for you automatically. Then post the error messages it spits out here (wrap them in [noparse]```

```[/noparse] tags, please)

---

### Post by 1ktmeadows on 2011-08-10
Im not trying to not to sound some much like a noob but this is the steps that I did:
1) Went into the terminal and type wine with a single space
2) Then I tried to drag the mp3rocket.exe file into the terminal but it would just go back into my Downloads
3) Next I just copied the file and paste it in the terminal so it came out to be, wine /path/to/executable/file:///home/owner/Downloads/mp3rocket.exe 
4) It said No such file or directory
5) Then I tried /path/to/executable/file:///home/owner/Downloads/mp3rocket.exe and it still said No such file or directory
Did I type this wrong in the terminal?

---

### Post by westie457 on 2011-08-10
> **1ktmeadows said:**
> Im not trying to not to sound some much like a noob but this is the steps that I did:
1) Went into the terminal and type wine with a single space
2) Then I tried to drag the mp3rocket.exe file into the terminal but it would just go back into my Downloads
3) Next I just copied the file and paste it in the terminal so it came out to be, wine /path/to/executable/file:///home/owner/Downloads/mp3rocket.exe 
4) It said No such file or directory
5) Then I tried /path/to/executable/file:///home/owner/Downloads/mp3rocket.exe and it still said No such file or directory
Did I type this wrong in the terminal?

Take a close look at the attached screenshot. The first attempt is after copying in file browser and pasting into terminal. The second attempt is after dragging from file browser into terminal. can you spot the differences between the two.

The second attempt works and the movie played.

Btw I did not know until I came across this thread that drag and drop to the terminal was possible.

---

### Post by HalfEmptyHero on 2011-08-10
Here's a brief intro on how the filesystem on Ubuntu (or linux in general) works. You have a root folder, which is / and the system files and programs are stored here. You need administrative, or root privileges to create/delete/edit files here. There are a bunch of folders in root, but you don't need to worry about those right now. The important one here is the home folder. Each user has it's own folder located in /home/username. So if your username is tom, your home folder would be /home/tom. Notice it is /home/tom and not home/tom, the two are very different. the home folder is in the root folder, which as I said before was designated by a "/" If you type in home/tom that would go to the folder home in the current directory and then the folder tom. so if you are already in /home/tom/Downloads and try to go to home/tom, it will try to go to /home/tom/Downloads/home/tom. This is why the command you typed in one of your previous posts did not work. Another thing to note is that typing in ~/ in the terminal is the same as typing in /home/username.

Using this information, if you downloaded mp3rocket.exe in your Downloads folder, you should be able to run it in wine using the following command:

wine ~/Downloads/mp3rocket.exe

I hope this helps.

---

### Post by GWBouge on 2011-08-10
Now we at least have enough info to give you the proper command:

```
wine /home/owner/Downloads/mp3rocket.exe
```

The '/path/to/executable' part wasn't meant to be typed directly, but was meant for you to fill in the actual path.  Nobody could have known where you have that file stored on your system, so we just use filler and assume you know to change that.  So, anytime someone types '/path/to/whatever' or the like, remember you'll have to change that part  =o)

They told you to drag the file from the file manager to the terminal so that you didn't have to type anything, and it should have pasted the text '/home/owner/Downloads/mp3rocket.exe' into the terminal.  But it doesn't actually move the file anywhere, so yeah, you'll still see it in Downloads.

Also note, not everything works with WINE.  And as was stated, the programs you're trying to install don't have a very good rating at [http://appdb.winehq.org/]("http://appdb.winehq.org/"), so even if you get them to install, they'll probably be awful buggy.

---

### Post by Ms_Angel_D on 2011-08-10
> **1ktmeadows said:**
> Im not trying to not to sound some much like a noob but this is the steps that I did:
1) Went into the terminal and type wine with a single space
2) Then I tried to drag the mp3rocket.exe file into the terminal but it would just go back into my Downloads
3) Next I just copied the file and paste it in the terminal so it came out to be, wine /path/to/executable/file:///home/owner/Downloads/mp3rocket.exe 
4) It said No such file or directory
5) Then I tried /path/to/executable/file:///home/owner/Downloads/mp3rocket.exe and it still said No such file or directory
Did I type this wrong in the terminal?

Look at what your typing. 

/path/to/executable/


is not supposed to be part of the equation it's just an example of what they are looking for.

if your file is in /home/owner/downloads then you would would enter

wine /home/owner/downloads/mp3rocket.exe

What you are typing in is the address to the file within your system. Unlike windows which looks for files with a drive letter such as

C:\Program Files

Ubuntu uses a directory name for everything so 

/ is the root of your system
/home is the home folder which resides in the root of your system
/home/owner is a folder which resides inside /home which resides within the root of your system.


Anyway welcome to Ubuntu and you might want to check out the Ubuntu Pocket Guide a free for download book to help persons whom like yourself have just begun using Ubuntu.
[http://ubuntupocketguide.com/](http://ubuntupocketguide.com/)

---

### Post by 1ktmeadows on 2011-08-10
Thank You, all of you, I was able to install the exe file and know I have to find the updated adobe flash player to use MP3rockets. You all know where I can find the updated adobe flash player?

---

### Post by corncob on 2011-08-11
> **1ktmeadows said:**
> I tried typing /path/to/executable/mp3rocket.exe and the terminal respond with bash: /path/to/executable/mp3rocket.exe: No such file or directory then I tried wine /Download/mp3rocket/mp3rocket.exe and I got wine: cannot find '/Download/mp3rocket/mp3rocket.exe'.  Im not sure what Im doing wrong, do you think wine wont be able to open this mp3rocket.exe file? Is another way getting this file to work ?
Thank You again for responding back.

It appears you ignored the ~ which is important as it represents your home directory.  Copy and paste into the terminal:
```
wine ~/Downloads/mp3rocket/mp3rocket.exe
```
We're only guessing at this path so if it doesn't work try finding mp3rocket.exe in the file browser and drag it into Terminal (after you put in wine plus a space.

---

### Post by corncob on 2011-08-11
> **corncob said:**
> I often find this
```
/path/to/executable/filename.exe
```
formidable and just type wine (plus a space) into the terminal and drag in the exe file from the file browser.  That takes care of the path.  [CTRL][ALT][t] should open the terminal.
BTW, welcome to the forum!

If you have problems locating mp3rocket.exe in the file browser, search for it and drag it into Terminal from there.  Although I used 11.04 for a while I dropped back to 10.04LTS so I can't tell you how to get to your search tool.  Mine is in the PLACES menu as "Search for files..."

---

### Post by 1ktmeadows on 2011-08-11
Im now having trouble When MP3rockets opened, the software said that I need an updated adobe flash player so I installed the Adobe Flash Plugin 10 and when I did that I got a java error saying that it could not creeate the Java Virtual Machine. So I unistalled MP3rockets and then reinstalled it and know I get in the terminal, wine: cannot find L"C:\\windows\\system32\javaw.exe. Im runnig java version "1.6.0_22" Im not sure what to do know

---

### Post by Mark Phelps on 2011-08-11
You're putting yourself through a lot of work -- and most probably, for NOTHING.

You were advised earlier to check out the WineHQ site -- advice you have apparently ignored.

I checked that site and the results are very discouraging in that MP3 Rocket isn't listed (meaning, it probably will NOT work), the versions you have of the other two are also NOT listed, and the older versions that are listed have very low ratings.

That site has information on what other folks did to try to get their versions working.  It's worth visiting.

---

### Post by 1ktmeadows on 2011-08-11
OK Thanks for the advice, Im have been playing around with ubuntu and is there an alternative music downloader (for example like bearshare, frostwire, or mp3rockets) that I can use for ubuntu.

---

### Post by Paddy Landau on 2011-08-11
There is a front-end to Wine, called PlayOnLinux. I strongly recommend that you install it and use it instead of Wine; it's much easier. See my signature for a how-to.

---

### Post by dFlyer on 2011-08-11
If you want to run exe files you need to really run windows. Wine works for some applications but not all. Before trying to install something with wine you should visit the wine web page to make sure the application will work with wine. You need to remember linux is not windows and doesn't work like windows. There are 1000's of applications that are free for linux just look and you shall find. A good place to start is the Ubuntu Software Center or synaptic or google. Do the research and you shall learn.

---

### Post by laithbsoul on 2011-08-11
You can get Frostwire for linux by typing this into the terminal
```
/sudo apt-get install frostwire
```
Before using windows software in wine you should find out if there is already an application for linux that does the same thing

---

### Post by Ms_Angel_D on 2011-08-11
> **1ktmeadows said:**
> Im now having trouble When MP3rockets opened, the software said that I need an updated adobe flash player so I installed the Adobe Flash Plugin 10 and when I did that I got a java error saying that it could not creeate the Java Virtual Machine. So I unistalled MP3rockets and then reinstalled it and know I get in the terminal, wine: cannot find L"C:\\windows\\system32\javaw.exe. Im runnig java version "1.6.0_22" Im not sure what to do know

Not trying to be rude or anything but I think you need to realize that ubuntu is not wine. Take a break from installing your Windows programs and actually explore what linux has to offer. Yes it's neat that we can run SOME windows programs thanks to wine but not everything will work in it, and if your not ready to give up some of your windows programs then maybe consider just installing wubi in your windows install or possibly installing Ubuntu in virtualbox on windows for now and getting to know Ubuntu.

Please read this: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

As far as flash and java not working for your wine programs...well it's not working because you didn't install flash or java in wine you installed them in Ubuntu.

---

### Post by anewguy on 2011-08-11
For now I'm giving a +1 to the "stick with Windows" idea and running Ubuntu either in a virtual machine, as dual boot or in worst case wubi.  Use Windows for the things you need to do, then go to Ubuntu to learn what it is you need to do there to get a similar result.  Once you've done that enough times, and get familiar with what Ubuntu is and how to use it, then consider switching but without wine.  It's obvious right now that it's not even an Ubuntu versus Windows thing - as we found out in this thread you don't seem to even know yet what the concept of a path is - and that's non-OS specific (syntax is specific, the concept isn't).

As mentioned by Ms_Angel_D, Ubuntu isn't Windows, wine isn't Windows.  You're never going to get everything you run in Windows to run in wine.  You are far better off looking through the package manager and trying packages that sound like they may do what you are wanting to do.

Dave ;)

---

### Post by Paddy Landau on 2011-08-11
> **anewguy said:**
>  Use Windows for the things you need to do, then go to Ubuntu to learn what it is you need to do there to get a similar result...
+1. That's exactly how I converted from Windows to Ubuntu.

Regarding WUBI, please note that WUBI is unstable and therefore only a short-term solution. Dual-boot works best, unless your machine is strong enough to handle a virtual machine.

---

