---
title: "No Grub Menu Present"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by StunnerAlpha on 2009-01-06
Ey guys, I just recently reformatted my Windows partition and now the Grub menu that asks for which Operating system you want to use does not show at all... the system just boots into Windows XP. I know that I did not nuke the ubuntu partition because it shows up as a separate disc when using Acronis True Image to backup my XP system once I got all the drivers installed. Any idea of how to fix this? Any help much appreciated, thanks!

---

### Post by caljohnsmith on 2009-01-06
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. If you don't have internet connectivity when using the Live CD, you can instead right-click [this link]("http://home.comcast.net/~ubuntu_grub/boot_info_script.txt") to the script in your web browser, choose "Save link as...", save the "boot_info_script.txt" file, transfer it to your Ubuntu desktop on the Live CD via USB stick, floppy, or however you want to do it, and then do the following in a terminal:
```
sudo bash ~/Desktop/boot_info_script.txt
```
The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by ajmorris on 2009-01-06
> **StunnerAlpha said:**
> Ey guys, I just recently reformatted my Windows partition and now the Grub menu that asks for which Operating system you want to use does not show at all... the system just boots into Windows XP. I know that I did not nuke the ubuntu partition because it shows up as a separate disc when using Acronis True Image to backup my XP system once I got all the drivers installed. Any idea of how to fix this? Any help much appreciated, thanks!

hi there,
This is very normal. The installation of your Windows XP system, re-installs the XP bootloader into your MBR, and replaces GRUB. All that is required, is a re-install of grub.

So, boot up any linux media you have, i.e an ubuntu live cd etc, and do the following:

```
1) sudo grub
```
```
2) find /boot/grub/stage1
```
```
3) root (hd#,#)
```(where #,# are the numbers that step 2) spits out

```
4) setup (hd0)
```
```
5) quit
```
```
6) sudo reboot
```

Then when you reboot, you should be good to go. GRUB will be back in your MBR.


AJ

---

### Post by drubin on 2009-01-06
> **caljohnsmith said:**
> In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```

I do not like the idea of telling users to downloads scripts off your (being any one) personal home PC. :(

They are untrusted sources that not every one would be able to comment on with out first downloading that script...

/me goes to look at the script

---

### Post by drubin on 2009-01-06
> **drubin said:**
> /me goes to look at the script

I don't know enough about bash to understand most of that code. What I do know is it is exceptionally long to be doing a basic grub fix.... 

Personally I would not run that script with out verifying its contents from a 3rd party. It is often easy to hide stuff in a long script with out knowing what it does.

/me still shivers at the thought of downloading scripts off other peoples pc's.

@OP : That first command
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```

Downloads that script to your desktop. Then executes it. So what ever information it downloaded from what ever cache server would be executed and run on your local machine as root.

---

### Post by caljohnsmith on 2009-01-06
> **drubin said:**
> I don't know enough about bash to understand most of that code. What I do know is it is exceptionally long to be doing a basic grub fix.... 

Personally I would not run that script with out verifying its contents from a 3rd party. It is often easy to hide stuff in a long script with out knowing what it does.

/me still shivers at the thought of downloading scripts off other peoples pc's.

@OP : That first command
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```

Downloads that script to your desktop. Then executes it. So what ever information it downloaded from what ever cache server would be executed and run on your local machine as root.
I can understand your hesitation to run the script, but I would like to point out that we have been using that script for a couple of weeks now in the forums with no problems. If you would like to see some examples, how about looking at:

[http://ubuntuforums.org/showthread.php?t=1031506](http://ubuntuforums.org/showthread.php?t=1031506)
[http://ubuntuforums.org/showthread.php?t=1031534](http://ubuntuforums.org/showthread.php?t=1031534)
[http://ubuntuforums.org/showthread.php?t=1031444](http://ubuntuforums.org/showthread.php?t=1031444)
[http://ubuntuforums.org/showthread.php?t=1030765](http://ubuntuforums.org/showthread.php?t=1030765)
[http://ubuntuforums.org/showthread.php?t=1031257](http://ubuntuforums.org/showthread.php?t=1031257)
[http://ubuntuforums.org/showthread.php?t=1026778](http://ubuntuforums.org/showthread.php?t=1026778)
...etc. 

So I don't think there is any reason to think that I have any malicious intentions by asking a person to download and run that script.

---

### Post by drubin on 2009-01-06
> **caljohnsmith said:**
> I can understand your hesitation to run the script, but I would like to point out that we have been using that script for a couple of weeks now in the forums with no problems. If you would like to see some examples, how about looking at:

[http://ubuntuforums.org/showthread.php?t=1031506](http://ubuntuforums.org/showthread.php?t=1031506)
[http://ubuntuforums.org/showthread.php?t=1031534](http://ubuntuforums.org/showthread.php?t=1031534)
[http://ubuntuforums.org/showthread.php?t=1031444](http://ubuntuforums.org/showthread.php?t=1031444)
[http://ubuntuforums.org/showthread.php?t=1030765](http://ubuntuforums.org/showthread.php?t=1030765)
[http://ubuntuforums.org/showthread.php?t=1031257](http://ubuntuforums.org/showthread.php?t=1031257)
[http://ubuntuforums.org/showthread.php?t=1026778](http://ubuntuforums.org/showthread.php?t=1026778)
...etc. 

So I don't think there is any reason to think that I have any malicious intentions by asking a person to download and run that script.


The issue is not *this* bash script it is where it comes from...  it is your localmachine ie you *could* choose to change that script at any time and no one would know unless we re-read it every time.

It also worries me that your command you give users, downloads and runs the file as root in one step.. It might be simpilar to do it in one command for the users but teaches them bad security here is a fill download and run in one step.

My suggest is explaining how it works maybe write a tutorial and "upload" this script to the forum and just link to your tutorial.

---

### Post by Tim Sharitt on 2009-01-06
> **caljohnsmith said:**
> I can understand your hesitation to run the script, but I would like to point out that we have been using that script for a couple of weeks now in the forums with no problems. If you would like to see some examples, how about looking at:

[http://ubuntuforums.org/showthread.php?t=1031506](http://ubuntuforums.org/showthread.php?t=1031506)
[http://ubuntuforums.org/showthread.php?t=1031534](http://ubuntuforums.org/showthread.php?t=1031534)
[http://ubuntuforums.org/showthread.php?t=1031444](http://ubuntuforums.org/showthread.php?t=1031444)
[http://ubuntuforums.org/showthread.php?t=1030765](http://ubuntuforums.org/showthread.php?t=1030765)
[http://ubuntuforums.org/showthread.php?t=1031257](http://ubuntuforums.org/showthread.php?t=1031257)
[http://ubuntuforums.org/showthread.php?t=1026778](http://ubuntuforums.org/showthread.php?t=1026778)
...etc. 

So I don't think there is any reason to think that I have any malicious intentions by asking a person to download and run that script.

I have to agree with drubin. The problem isn't with your script, it seems innocent enough, but you could easily change the script to damage a users system.
Also, I have looked over several of your posts, and most of the time the solution to the op's problem is quite simple, meaning that running your script is merely a waste of the users time. (This thread is an example of that.)

---

### Post by Tim Sharitt on 2009-01-06
> **drubin said:**
> 
my suggest is explaining how it works maybe write a tutorial and "upload" this script to the forum and just link to your tutorial.

+1

---

### Post by meierfra. on 2009-01-06
drubin:  Thanks for bringing up the security issue.  The script started out  as a one line code  about four weeks ago  and we did not really consider any security  issues. But it has has been growing ever since.  I  agree with you, asking people to download a script from a random place and run it with "sudo"  is not the ideal solution. Of course that is the most convenient way for us and the user, but as you said, it teaches the user very bad security habits.

caljohnsmith  has asked the moderators for [input]("http://ubuntuforums.org/showthread.php?t=1032265"). Also I like your idea to post a tutorial explaining the script. In fact caljohnsmith has suggested this to me a while ago, but I have spent all all my spare time (and more) developing the script. 

> you *could* choose to change that script at any time
That is the fundamental problem.  My ability to change the script at any time  is  a  serious risk for the user. But without  this ability  I would not have been able to write the script. Almost every day in the last few weeks  I spent some time looking at the cases where the script was used. And very often I would get an idea how to improve the script. So indeed this script has been changed numerous times by now.

---

### Post by StunnerAlpha on 2009-01-06
Thanks guys! I followed ajmorris's method and it worked beautifully. I opted out of the script thing because it seemed to be a bit much work. Thanks again!

---

### Post by drubin on 2009-01-06
> **meierfra. said:**
> That is the fundamental problem.  My ability to change the script at any time  is  a  serious risk for the user. But without  this ability  I would not have been able to write the script. Almost every day in the last few weeks  I spent some time looking at the cases where the script was used. And very often I would get an idea how to improve the script. So indeed this script has been changed numerous times by now.

My suggestion is make a tutorial in the tutorial section. do not attache the script but rather include it in code tags with comments so wany one can see.

The go through it line by line/commands and explain what each does. and list the steps to setting it up. 

Having a script that people download and run doesn't help any one learn what it does.

also instead of having to copy and paste your standard replies you guys could just post a link that why when you change your tutorial it will always remain correct. Saves those electrons. 

IMHO this is the way forums are expected to work.

---

### Post by drubin on 2009-01-06
> **StunnerAlpha said:**
> Thanks guys! I followed ajmorris's method and it worked beautifully. I opted out of the script thing because it seemed to be a bit much work. Thanks again!

Glad you got sorted out and every thing was solved in the end.

Sorry for "high-jacking" your thread.

---

### Post by pyromanic123boom on 2009-01-06
Run the live CD, and open a terminal.
```

sudo grub

root (hd0,0)             -------> or whichever ubuntu is installed on

setup (hd0) 

quit

exit

```

exit live cd, go into ubuntu, and edit your /boot/grub/menu.lst

you can read about it here (re-instating grub loader) [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5).  I used this guide, works like a charm.

---

