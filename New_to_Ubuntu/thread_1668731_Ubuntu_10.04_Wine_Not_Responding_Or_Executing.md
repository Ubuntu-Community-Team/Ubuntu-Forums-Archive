---
title: "Ubuntu 10.04 Wine Not Responding Or Executing"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by Isoroth321 on 2011-01-16
[FONT=Book Antiqua][SIZE=2]Hello,

I have been using Ubuntu for about  7 months now.  I mostly use Ubuntu for web browsing, downloading software and playing games provided via Ubuntu Software Center.  I have a fair amount of basic computer knowledge, but clearly not enough to fix this issue that I have.

I had Wine for quite some time. Until 1 day, Wine no longer responded.  This was because, some time ago, I wanted to play this game that required me to tweak the settings on wine. I did so correctly as instructed. And now, Wine will no longer execute windows software or anything of that nature.  I have tried to delete and reinstall Wine, but it still continues to repeat this bizarre phenomenon. I have also tried to configure Wine to correct this problem, but it will not respond.  

When trying to execute a Windows file, I right-click the icon, click on "Open with Windows Program Loader". Then it will pop-up an error due to the fact that the file does not have executable permission. So, I marked it as executable, repeated the process, the cursor turns into a loading circle, turns back to the cursor and nothing happens.  I have tried to wait for about half an hour and still nothing appears to happen. However, I can still browse through the C: Drive just fine.  

I have searched far & wide for people on the forums with this same problem, and to my surprise, no one else that I know of appears to have this problem. 
If you could tell this nub how to get my Wine up & going again, that would be greatly appreciated.  Just tell me in....slow & easy-to-understand words. :PP

Thanks a dozen.

 
[/SIZE][/FONT]

---

### Post by robsoles on 2011-01-17
Welcome to UF.

The first thing to do is to apply the exact opposite of the instructions you followed which borked your Wine installation - this does mean start with the last instruction and remove or restore whatever that instruction involved.

Just because you followed their instructions exactly doesn't make their instructions worth following - plenty of dodgy instructions all over the internet!

If that fails to fix it then you can purge Wine and it's settings, if you want to hang on to the contents of ~/.wine/drive_c then you probably want to preserve the *.reg files as well - hanging onto the *.reg files may hold the emulation system down (make it so it still can't work!) - to hang on to them for sure through the following commands, move them (open nautilus, press [CTRL]+[H] to show hidden files if not on display already) to your ~/Documents or other folder, like ~/Documents, in your home (~/) folder, when finished just move them back to .wine folder before firing up the emulator.

```

sudo apt-get purge wine
sudo apt-get install wine

```If you retain ~/.wine/c_drive and ~/.wine/*.reg and run those commands in terminal and Wine still doesn't fire up a Windows emulation for you then move all the contents of ~/.wine away (or delete them) and then try to start Windows programs again.

---

### Post by mastablasta on 2011-01-17
> **Isoroth321 said:**
> [SIZE=2][FONT=Book Antiqua]When trying to execute a Windows file, I right-click the icon, click on "Open with Windows Program Loader". Then it will pop-up an error due to the fact that the file does not have executable permission. So, I marked it as executable, repeated the process, the cursor turns into a loading circle, turns back to the cursor and nothing happens. I have tried to wait for about half an hour and still nothing appears to happen. However, I can still browse through the C: Drive just fine. [/FONT][/SIZE]

 
I would just like to add to what was already said in the previous thread. You can open terminal and then run the programme through command 
 
wine [programme name]
 
This will give you output on what's happening and also any errors report. you can post those here or better maybe on wine forums to see what they mean. then again it might just run the programme fine as it happened to me... :-O

---

### Post by Isoroth321 on 2011-01-18
[FONT=Book Antiqua][SIZE=2]I thank you both for both suggestions and I will try them out...but apparently my  [/SIZE][/FONT][SIZE=2]package installer was/just broke when I tried to type that purge command.
Here's what I got:[/SIZE]

@Linux-desktop:~$ sudo apt-get purge wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  openjdk-6-jre-headless: Depends: java-common (>= 0.28) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

[SIZE=2]So apparently, because of that Java thing I was trying to install, it broke my package manager (Fan-freaking-tastic) so now I get to get that resolved on top of my wine problem >.<

& yes, I take all the blame, it was my dumb, noobie fault for trying to play MC on here...-slams head on desktop-[/SIZE][SIZE=2] So, any pointers before I get my head bashed-in by the Ubuntu pros face-palming to my fail?[/SIZE]

---

### Post by Isoroth321 on 2011-01-18
[SIZE=2]Also if I may add, when I say the configuration menu will not respond, it will not open at all.  Similar to that of the Windows Programs. Also, I got my package installer fixed and up and running now.

I have discovered what I did wrong. I added a...something to the library & enabled that something and disabled everything else that was in there originally.  & just what is that something?  Do you really expect me to remember from a small task I did about 6 months ago?  Anyway, I think it for that reason that Wine is broke. However, I cannot fix it because I cannot access the configuration menu.  So there must be a way to get wine back to the way it is.
AND, I do not know where exactly the .reg files I hear so much about is located.

Thanks
[/SIZE]

---

### Post by robsoles on 2011-01-18
> ... ```
...
Package wine is not installed, so not removed
...
```...

That says that Wine is not installed on your system. Please try```
sudo apt-get -f install wine
```then try to access Wine Configuration again and then, if it fails in the familar way, press through my first set of suggestions again.



Ps. I indicated the location of *.reg files in my first post in this thread:```
cd ~/.wine
ls -al
```If they are not listed for the 'ls' command with the '-al' switch (should be listed for plain 'ls' alone but...) then please say so.

---

