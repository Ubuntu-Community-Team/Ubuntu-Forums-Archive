---
title: "Stuck..."
date: 2010-01-27
forum: New to Ubuntu
---

### Post by kennewickrockerguy on 2010-01-27
[FONT="Courier New"][SIZE="2"]
Keep in mind I am a complete noob when it comes to any OS other than Microsoft platforms, however I am computer literate. Last night, I decided I needed a different "everyday" OS since Vista is a ramhog and my daily activity usually consists of some web surfing and email checking. However, Open Office doesn't seem to support my work headers for .doc files. After much debate, I chose ubuntu over U-Lite OS since the U-Lite formus mentioned there were WPA issues I was not willing to deal with. Please remember, I know nothing about Linux scripts, I have experience with DOS and Windows registry editing.

The build was an old laptop hard drive I use as an old external, so if my problem requires reformatting, it's no problem, it was formatted for the install.

After installation, I booted up and was prompted to do 214 updates, so I did. I made no changes other than th updates, was prompted to restart, so I did. 

After my restart, I can not get ubuntu to load. And I know NOTHING about the recovery tool (safe mode?).

Here is what is happening:
Turn computer on, get the circular loading screen, the 1st error that pops us comes with a black screen and the mouse icon is a round loading icon. And I get this error (screenshot >> [http://i46.tinypic.com/f1a452.jpg](http://i46.tinypic.com/f1a452.jpg) )

After clicking OK (the only option), I get sent to this error (screenshot >> [http://i47.tinypic.com/33li140.jpg](http://i47.tinypic.com/33li140.jpg) )


After clicking OK (again, the only option), the orange factory background loads and the following screen popped up (screenshot >> [http://i45.tinypic.com/30a6sqt.jpg](http://i45.tinypic.com/30a6sqt.jpg) )

Then, it prompts me to copy a high security password for recovery (screenshot >> [http://i47.tinypic.com/epit86.jpg](http://i47.tinypic.com/epit86.jpg) ). I clicked "Run this action now" and what looked like a windows notepad popped up asking me for my password, I entered the password I usually log in with and it generated a password I copied. Sorry, didn't get screen shot of the password page, figured it wasn't needed.

After I clicked OK and closed out the "Record your encryption passphrase" the screen stays at the orange background, nothing runs just the background and the only way I can shut down is Ctrl + Alt + Del and shut down from there.

I have tried a few remedies, tried waiting at all error screens to see if it just needed to finalize the updates like Windows, tried rebooting in "recovery mode" and was lost as hell, tried searching forums for solutions and nothing. Have tried waiting and rebooting and am kinda frustrated. Before the updates, everything seemed fine. I pulled up google to lookup my pharmacy just to test the web and it ran, until i updated and restarted. My computer is running well over the minimum requirements for ubuntu. 2GB RAM, Pentium 2.0, over 100GB hard drive I formatted just for the OS. One other problem I have is during installing OS, I entered the correct time zone and it must have reset BIOS back hours. Keep in mind the only "changes I made were the requires setup questions and install the security updates. No 3rd party software.


Any help would be amazing.

Thanks
MGL

PS: Sorry I posted so much info, I see so many "My computer won't run, why?" threads all over and hate when details are not given.
[/SIZE][/FONT]

---

### Post by Psumi on 2010-01-27
Was the doc saved with the newest version of MS Office?

Also, encrypting your home directory will make your machine much slower, and "can" cause issues at times for when a system application wants to do something with your home dir.

I've never, ever, encrypted my home directory when I found out my 3 GHz dual core machine took almost 5-10 minutes to load crypto services.

---

### Post by nothingspecial on 2010-01-27
Don`t know if this will help but, in recovery mode > root maintanence shell
```

 chown -R username:username /home/username
```

```
chmod 644 /home/username/.ICEauthority
```

change username for your actual username.

---

### Post by Hospadar on 2010-01-27
> **nothingspecial said:**
> Don`t know if this will help but, in recovery mode > root maintanence shell
```

 chown -R username:username /home/username
``````
chmod 644 /home/username/.ICEauthority
```change username for your actual username.

In case you are curios, chmod changes permissions, and chown changes ownership.  you can do 'man chmod' and 'man chown' to learn more.  it might also be a good idea to read up on the internet about unix permissions.  they are logical and make sense, but quite different from a windows system.  In general, it might be good to learn a little about the linux filesystem structure, and some command-line basics.  There are tons of great tutorials on the google machine.

I also suspect your problem has to do with the encryption.  I'd just do everything unencrypted, the only thing hard disk encryption prevents against is when someone physically steals the drive, which, since this sounds like a desktop machine at home would maybe help if you were burgled.  I suppose it is a real concern, but I've always felt that if I got burgled, having them get my credit card numbers would probably be a pretty minor annoyance in the face of all my things being gone.  If you have no idea what is going on with this encryption business, you probably accidentally checked it during the install process.  somewhere during the install there is an option to encrypt your home directory which you probably don't want.

So long story short, I'd re-install and don't encrypt your home directory.

---

### Post by kennewickrockerguy on 2010-01-27
Thanks everyone,

I did some searching and found a solution on the web at 6AM (about my bedtime, I'm a night owl). Here Are the steps I took to fix it (please excuse the format, it's a copypasta job :)



[I]boot into recovery mode

drop to root shell prompt

type:
login

you will get this prompt:
<name>-desktop login: enter you user account name
password: enter your password (NOTE: you will not see the characters that you type here)

at the next prompt type:
startx

This will log you into your normal user account. The Login Screen menu item will be accessable at this point but, it will not work.

in a terminal window enter this command:
sudo gedit

enter your password when prompted. This will open gedit with root permissions.

in gedit click open then under file system browse to /ect/gdm/custom.conf

you should see a file that looks like this: 

[daemon]
TimedLoginEnable=false
AutomaticLoginEnable=true
TimedLogin=username
AutomaticLogin=username
TimedLoginDelay=30

simply change AutomaticLoginEnable=true to =false

shutdown as normal. this will drop you back into the recovery mode. Close out from that and restart. From there everything should be good.[/I]


Still having issues. The time corrected itself, however the audio was not working to begin with. To fix it, i used:
System > Administration > System Testing
Ran the audio tests and it is now working. One other thing I noticed is while I was typing, the screen went black (as in dead, no backlighting at all). I hit the space bar and it took me straight to login (in other words, the computer was asleep, it didn't just die). I logged in and chrome said it crashed.

I do have 2 questions. You mentioned that HDD encryption causes issues, how about the security risks involved with not encrypting it.  Is it possible to change that now, or does it require a fresh install (no problem if it does)? Is there a linux version of "task manager"? I'd like to compare the resource usage to Vista. I can already tell a huge speed difference. The only other tiny problem i can tell is when booted into Ubuntu the wifi on light on my computer does not come on, it works fine but for some reason the light just doesn't come on.

---

### Post by JKyleOKC on 2010-01-27
> **kennewickrockerguy said:**
> Is there a linux version of "task manager"? I'd like to compare the resource usage to Vista. I can already tell a huge speed difference.Sorta; however it's broken up into several different commands. Go to a command line prompt (terminal from the applications menu), type "top" and hit enter. You'll get a list of running processes. They can be sorted in a variety of ways; hit the "?" key to get a help page. I usually sort by upper-case "P" to see the CPU usage but you can also sort by memory use which sometimes is what you may want to see.

The overall resource usage is summarized at the top of the display.

To get back to the command line prompt, hit "q" (note well that unlike Windows, Linux is case-sensitive just about everywhere, so "p" won't work to sort by CPU usage and "Q" won't work to quit).

To kill an errant process, the "kill" command is used, together with the process-ID of the process to be killed. I use "top" to get the process-ID, then type "sudo kill xxx" where xxx is the ID number, enter my password, and the process dies. The "sudo" isn't necessary if you own the process, but it doesn't hurt either. Be cautious in using this, though. It's quite easy to accidentally shut down your system without flushing disk buffers out, and that can leave you with a borked system!

Back to resource usage: there's one huge difference in philosophy between Windows and Linux with regard to memory. While Windows tries to use as little as it can get by with and complains if you get near total capacity, Linux tries to use it all and fills as much of it that's not taken up by programs and data with disk cache buffers (that go away automatically if a program needs the space). This can lead you to believe that Linux is a memory hog, when it's usually just the opposite. This intensive cacheing is one of the reasons for the noticeable improvement in speed!

---

### Post by Paqman on 2010-01-27
> **kennewickrockerguy said:**
> Is there a linux version of "task manager"? I'd like to compare the resource usage to Vista.


Sure. Go to System > Admin > System Monitor. There's a panel applet for that too, just right-click on a panel and "add to panel".

---

### Post by kennewickrockerguy on 2010-01-27
> **JKyleOKC said:**
> Sorta; however it's broken up into several different commands. Go to a command line prompt (terminal from the applications menu), type "top" and hit enter. You'll get a list of running processes. They can be sorted in a variety of ways; hit the "?" key to get a help page. I usually sort by upper-case "P" to see the CPU usage but you can also sort by memory use which sometimes is what you may want to see.

The overall resource usage is summarized at the top of the display.

To get back to the command line prompt, hit "q" (note well that unlike Windows, Linux is case-sensitive just about everywhere, so "p" won't work to sort by CPU usage and "Q" won't work to quit).

To kill an errant process, the "kill" command is used, together with the process-ID of the process to be killed. I use "top" to get the process-ID, then type "sudo kill xxx" where xxx is the ID number, enter my password, and the process dies. The "sudo" isn't necessary if you own the process, but it doesn't hurt either. Be cautious in using this, though. It's quite easy to accidentally shut down your system without flushing disk buffers out, and that can leave you with a borked system!

Back to resource usage: there's one huge difference in philosophy between Windows and Linux with regard to memory. While Windows tries to use as little as it can get by with and complains if you get near total capacity, Linux tries to use it all and fills as much of it that's not taken up by programs and data with disk cache buffers (that go away automatically if a program needs the space). This can lead you to believe that Linux is a memory hog, when it's usually just the opposite. This intensive cacheing is one of the reasons for the noticeable improvement in speed!

> **Paqman said:**
> Sure. Go to System > Admin > System Monitor. There's a panel applet for that too, just right-click on a panel and "add to panel".

Thanks everyone!!!

I am glad so many people are so helpful here. Switching to Ubuntu from Windows can be frustrating if you don't know linux. On to my next thread here about security. I hope this might help anyone else having the same issue(s).

Regards,
Ubuntu Noob

---

