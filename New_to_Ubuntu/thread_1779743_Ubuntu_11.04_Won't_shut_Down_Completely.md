---
title: "Ubuntu 11.04 Won't shut Down Completely"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by canfu on 2011-06-10
Hello to anyone, I'm kind of new to Linux, never used a lot of it. I freshly installed Ubuntu 11.04. After a few hours using it without any problems, installed the updates and installed some programs. I clicked the shut down option and it stay on. Keyboard and mouse shut down but the computer itself y is still powered on and in the monitor stays a purple splash screen of ubuntu. The only way is hitting the power button for fully shutting down.
I searched and only found older post for version 10.10. I'd tried in the terminal command ¨sudo halt¨ once and everything powered off, powered up to tried it again and didn't work for the second time.

Its really strange because it stop powering the keyboard and mouse but the tower itself is still powered and giving a splash screen.


UPDATE: Is shutting down completely if I press the power button and clic in the option for shutting down. First time some text massage really fast, second time splash screen powering off normally. But somtines do not complete the shut down.

UPDATE2: Reinstalled ubuntu completely. Tested shutting down and almost did it, the 5 little circle under the ubuntu logo only 4 was filled and get stuck in the fifth. Downloaded updates and the shut down was fully normal. Installed the nvidia driver and the shut down is back with problem. It could be the video card?

---

### Post by dFlyer on 2011-06-10
Did you check the md5sum before you burned the iso to cd? In the 15+ years I've been using linux I've never had that happen. Hope some one can help ya. I find the linux kernel very stable. Is this the 32bit or 64bit version? One other thing I can suggest is to check you BIOs to see if it's set to auto restart on shutdown.

---

### Post by canfu on 2011-06-10
Thanks for the reply. I always check and test the iso in many ways. The 11.04 installed is 32 bits. A few years ago I tested others linux and Ubuntu, i think it was version 7.04 back then in the same computer and nothing of this problems happened. I checked the BIOS if some settings where changed but are normal. But I searched in the internet and in forum and some have problem for shutting down normally and all was version 10.10 but they resolved back then with updates that was released in that time.

---

### Post by C3rb3rus33 on 2011-06-12
I am also having this issue with 32 bit install. help!!!

---

### Post by dFlyer on 2011-06-12
> **canfu said:**
> Thanks for the reply. I always check and test the iso in many ways. The 11.04 installed is 32 bits. A few years ago I tested others linux and Ubuntu, i think it was version 7.04 back then in the same computer and nothing of this problems happened. I checked the BIOS if some settings where changed but are normal. But I searched in the internet and in forum and some have problem for shutting down normally and all was version 10.10 but they resolved back then with updates that was released in that time.

Lets hope they get a fix out soon for ya. Have you filed a bug report?

---

### Post by VOT Productions on 2011-06-12
What video cards do you all have?

---

### Post by C3rb3rus33 on 2011-06-12
nvidia geforce 8200m G - with the latest drivers installed.

---

### Post by Harpoon on 2011-06-13
I had a similar situation with a different graphics card.  In my case, I needed to get to the shutdown messages (I think cntl-alt-del worked, or by running sudo shutdown -h now in a terminal).  The freeze involved an exim4 file that supposedly had a non-zero size, and some mention of a possible update pending (not true).

The fix was to locate the file and delete it (as sudo).  On odd occasions the problem would reappear though.

I don't know if this is what you are experiencing, but it is worth a look.

Good luck ...

---

### Post by C3rb3rus33 on 2011-06-13
Well other than the shutdown/restart/hybernate issue, I love the OS. I've always been partial to any linux distro. I wish there was a fix out there for this. I hate to go back to windows.  I am a network engineer and I just love running Linux.

---

### Post by jtarin on 2011-06-13
Logout>switch over to another virtual terminal and issue the shutdown command and watch for any errors or hangs. Nothing? Login and issue the command ```
cat /var/log/syslog
``` see if anything stands out......note the times when you shutdown when referring to syslog.

---

### Post by C3rb3rus33 on 2011-06-14
I have done that, it still hangs in the terminal after like the third process. I have a .jpeg i took with my phone that shows what state my console was in when it hung. When I manually rebooted and checked the syslog it seems to only show the startup data. It did not seem to go far back enough to where the shutdown command was issued.

---

### Post by jtarin on 2011-06-14
Post the .jpeg

---

### Post by C3rb3rus33 on 2011-06-14
It wont let me here. So I put it on my facebook page, its public oyu should be able to view it here

---

### Post by jtarin on 2011-06-14
tail -100 /var/log/messages

and that will show the last 100 lines of the system log. Shutdown and startup console messages will be there.

---

### Post by jtarin on 2011-06-14
Are you using speech-dispatcher? No....why not uninstall it. If your not using it that is one less thing in the mix during shutdown.

---

### Post by psn_Barthezz on 2011-06-16
Im also having the same issue, i have Ubuntu 11.04 64bit installed on my macbook air (late 2010), i tried uninstalling, and reinstalling using Wubi (through my Windows 7 in bootcamp).

every single time i restart/shutdown, it doesnt fully shutdown, i usually end up with the following:


```

Init: dbus main process (943) killed by term signal
Init disconnected from system bus
```

and it just sits there until i hit the power button for 5 secs to force shutdown (btw, the process number isnt always the same, sometimes its 7XX or 5XX), however yesterday, the keyboard was completely powered down... the _ was blinking still and being a macbook air... i couldnt hit the shutdown button cuz the keyboard was off lol.... had to wait for 6 hours until the battery died, and now im scared to even boot back to ubuntu T_T been looking around and nothing seems to be of any help T_T

NOTE: i very very rarely end up at the screen with ubuntu and 5 dots underneath it, however it stops there too...

---

### Post by luigibmth on 2011-06-17
same problem here with 64bit Ubuntu 11.04 both restart and shutdown wont work

well would you believe it? first time just now it shut down correctly :)

---

### Post by wjcunning on 2011-07-14
I fought the 11.04 shutdown problem for two solid days...tried everything in all the forums, no joy. Finally stumbled across the solution....my graphics card, which was a shock because it seemed to be working perfectly. I swapped it out for an older Nvidia card and the shutdown problem stopped immediately. This is a tough problem, I wish you all luck.

---

### Post by rbenning on 2011-09-23
I have had this same problem and discovered that it was caused by setting the BIOS variable "Limit cpuid MaxVal" to 'enabled'. I can consistently reproduce the problem when this variable is 'enabled', and then resolve it by setting it to 'disabled'. (Making no other changes). I'm not very brave when it comes to playing with BIOS settings and I can't explain why this works, but will attempt to do some googling to find out more about this value and how it impacts Ubuntu. I'm currently running Ubuntu 11.04 and it's been a dream, I'm very happy I discovered this last issue which has plagued me for a long time! :D

---

### Post by Shenachie on 2011-09-24
I have the same problem with 11.10. It hangs then asks me for the password. I enter it correctly and it still hangs. 

My cure?

The wall switch.

Shen

---

### Post by blackjack23 on 2011-09-30
anyone solved this yet? I have this problem on my Asus K40AB as well, it happens around 85% of the time.. and its very annoying. I just recently upgraded to 11.04 from 10.10 where I never have any of these problem, I considered upgrading to the 11.10 beta or going back to 10.10, but my internet connection isnt very good, and i dont want to download all the drivers/codecs all over again...

here is a pic where it hangs:
[ATTACH]203218[/ATTACH]

p.s.:Sorry the attachment exceeded the maximum resolution, im worried the text would be unreadable..

---

### Post by okanagansage on 2011-12-21
I just had this problem of an incomplete shutdown on a new install of lubuntu 10.04 on old hardware (AMD-K6 processor). At shutdown I'd get to a frozen (splash?) screen with the dots below the word "lubuntu". The mouse and keyboard were powered down but the tower was not. I searched for the answer and then remembered that it had happened a year or so ago with a different distribution (either ubuntu or xubuntu). This works with distributions that use grub2. I wasn't sure if it'd work because I'm not even dual-booting this time, but it made no difference. Shows how much I know. I had found the fix in these forums and wrote it down. This fix worked for me before and it just worked again. This involves editing a file from the terminal. 
........................
1. You may want to make a backup of the file first but since the change is small so you could skip this step and just change it back after if it doesn't work. This is the only step I'm not 100% sure about. I think to make a backup you enter this:

sudo cp etc/default/grub etc/default/grub.backup

A copy of that grub file should appear in the directory with the name grub.backup. If you want to see what the command cp is then type "man cp" into the terminal and it'll show a description of that command.
...........................
2. Open the file in a terminal text editor by typing in the terminal:

sudo nano /etc/default/grub
.............................
3. Change the line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"

The mouse didn't help me at this point so I had to use the arrow keys to navigate the cursor to the right spot. I exited the text editor by pressing the CONTROL and X buttons at the same time (it displayed this at the bottom of the editor). And then I think I pressed enter to confirm, which brings you back to the normal terminal.
.....................................
4. Then update grub with the command:
sudo update-grub2
.....................................
5. Restart. The change will not work on the first shutdown. After restarting shutdown the computer to test if it worked. 
.................................
If that didn't work for you then it's easy enough to take out the two words and update grub2 again. I wish I would have saved the link to the thread where I found this fix because I'm sure (s)he explained this better than me.

---

### Post by drfox on 2011-12-22
Worked like a charm! I used "sudo update-grub" and it worked on the first shutdown. Not sure that there's a difference between update-grub and update-grub2.
Thank you Okanagansage!
Larry

---

