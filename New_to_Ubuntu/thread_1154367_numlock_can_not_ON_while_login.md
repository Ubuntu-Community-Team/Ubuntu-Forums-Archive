---
title: "numlock can not ON while login"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by eagleboycn on 2009-05-09
Hi everyone,
I use ubuntu 9.04,but when login,the numlock can not be on automaticly.
After search in web,i find some solutions,but trouble remains after i installed numlockx,and modify /etc/gdm/Init/Default file. 

My hardware is as below:
CPU :Celeron D 2.8 G
Motherboard: ASUS P5GDC pro
Display card: ASUS EN76000GS

Is there anyone knows how to deal with it? Thanks a lot!

Remarks:
After login,in terminal,if i run "numlockx on" command, the numlock can be ON.

---

### Post by binbash on 2009-05-09
add that command to System > Preferences > Startup Applications if you want to run that command after log in.Or you can add that command to /etc/rc.local (add it before exit) if want to run it before GDM/login

---

### Post by 73ckn797 on 2009-05-09
Look for my post here: [http://ubuntuforums.org/showthread.php?p=7245203#post7245203](http://ubuntuforums.org/showthread.php?p=7245203#post7245203) and see if that can help. You will have to enable Configuration Editor which I explain there.

---

### Post by eagleboycn on 2009-05-10
To binbash:
 Thanks a lot for your suggestion. Now my trouble is Numlock can not be ON automaticlly while in login window,. After modify /etc/rc.local with add line "numlockx on" in the file before line "exit 0". But it still be off while login.

To 73ckn797:
   Thank you very much for your help. I have checked in the configure menu, the item "remember numlock state " is actived.

---

### Post by Wobblybob on 2009-05-20
Jaunty : Enabling NUM Lock at boot & after login

The Default behavior is for the NUM Lock key to be off at boot up, but if you wish to have it enabled for entering your login password, follow these instructions.

From Synaptic Package Manager, search for and install numlockx or, from the Terminal type or copy and paste:

martin@linux:~$ sudo apt-get install numlockx

To get it working, you now have to edit the appropriate startup file. First, make sure you have a working backup of the file, in a Terminal type or copy and paste:

martin@linux:~$ sudo cp /etc/gdm/Init/Default /etc/gdm/Init/Default.bak

Next, modify the gdm/Init file. In a Terminal type or copy and paste;

martin@linux:~$ gksudo gedit /etc/gdm/Init/Default

Scroll down to the end of the file, and above the line that says "exit 0" add the following:

if [ -x /usr/bin/numlockx ]; then
/usr/bin/numlockx on
fi

Save the file then, next time you reboot, your NUM LOCK should default to on for login but will then go off after login.

Keeping Num Lock on afetr login:
Open [System], [Preferences], Startup Applications], click on add type numlockx in the 1st box numlockx in the 2nd box and keeps Num Lock on after login in the 3rd box, then click on [Add]. now restart your PC.

---

### Post by eagleboycn on 2009-05-20
Thanks,Wobblybob.
I have fixed this trouble last night. 
In fact, i have do like you said before i come here. But i can not get the numlock on automaticlly when in login window. And the root cause is just my fault.
:o That is i missed a space when i modify the "/etc/gdm/Init/Default" file( a space before "-x /usr/bin/numlockx ];"
> 
if [ -x /usr/bin/numlockx ]; then
/usr/bin/numlockx on
fi


Thanks everyone here for your suggestion!

---

### Post by mlnease on 2009-07-22
> **Wobblybob said:**
> Jaunty : Enabling NUM Lock at boot & after login

The Default behavior is for the NUM Lock key to be off at boot up, but if you wish to have it enabled for entering your login password, follow these instructions.

From Synaptic Package Manager, search for and install numlockx or, from the Terminal type or copy and paste:

martin@linux:~$ sudo apt-get install numlockx



Thanks for this--my problem is that numlockx doesn't appear in repositories and when I try apt-get I recieve the following message:

E: Couldn't find package numlockx

Any suggestions?

Thanks,
mn

p.s.  Here are my repos--by the way, a number of other apps I expected to find don't seem to appear in these repositories.  Any ideas?

p.p.s.  Well, I've un- and re-checked all my repositories, reloaded and voila! numlockx is back and installed.  I edited /etc/gdm/Init/Default with Wobblybob's code (triple-checked) and still no numlock on login.  Any other ideas?

---

### Post by Wobblybob on 2009-07-27
Hi mlnease, did you do this bit

Keeping Num Lock on afetr login:
Open [System], [Preferences], Startup Applications], click on add type numlockx in the 1st box numlockx in the 2nd box and keeps Num Lock on after login in the 3rd box, then click on [Add]. now restart your PC.

---

### Post by mlnease on 2009-07-27
> **Wobblybob said:**
> Hi mlnease, did you do this bit

Keeping Num Lock on afetr login:
Open [System], [Preferences], Startup Applications], click on add type numlockx in the 1st box numlockx in the 2nd box and keeps Num Lock on after login in the 3rd box, then click on [Add]. now restart your PC.

Hi Bob,

Thanks for the response--I did, yes (screenshot attached).  Still no numlock at login!  A puzzler...

mike

---

### Post by dli8ilb on 2009-08-21
i just wanted to report that on my particular laptop (Compaq CQ60-211DX), this numlockx method works fine except it does not activate the num lock LED above the 10 key pad. it works fine, just no light indicating it's on.  not a big deal.  if i press the num lock button twice, the LED does come on though.

---

### Post by eagleboycn on 2009-08-24
> **mlnease said:**
> Hi Bob,

Thanks for the response--I did, yes (screenshot attached).  Still no numlock at login!  A puzzler...

mike
Hi mlnease,
I think you could test the numlockx in terminal window:
use command  "numlockx on" to turn Numlock ON
use command  "numlockx off" to turn Numlock Off.

If it get woking, numlockx is installed properly,you can checked the file "/etc/gdm/Init/Default" again. (On my desktop, there is no need to add this item to "startup application")
otherwise,numlockx is not installed properly,maybe you must installed again.
Hope this can be useful.

---

### Post by mlnease on 2009-08-24
> **eagleboycn said:**
> Hi mlnease,
I think you could test the numlockx in terminal window:
use command  "numlockx on" to turn Numlock ON
use command  "numlockx off" to turn Numlock Off.

If it get woking, numlockx is installed properly,you can checked the file "/etc/gdm/Init/Default" again. (On my desktop, there is no need to add this item to "startup application")
otherwise,numlockx is not installed properly,maybe you must installed again.
Hope this can be useful.

Hi eagleboycn,

Thanks for this.  I've actually got it working by putting together advice from here and a couple of other sources, to wit:

1. Enable universe and multiverse repositories;
2. sudo apt-get install numlockx;
3. In System > Administration > Startup Applications, add numlockx;
4. sudo gedit /etc/gdm/Init/Default;
5. look for the line that says, “exit 0” and above this line add these extra lines:

if [ -x /usr/bin/numlockx ]; then

/usr/bin/numlockx on

fi

6. Save the file and close gedit.

[http://ubuntuforums.org/showthread.php?t=153747](http://ubuntuforums.org/showthread.php?t=153747)
[https://bugs.launchpad.net/ubuntu/+source/numlockx/+bug/218202](https://bugs.launchpad.net/ubuntu/+source/numlockx/+bug/218202)

I'm no expert (by any means) so I don't suggest that anyone assume this to be harmless--it does seem to work for me though, on a Dell Optiplex GX270.

Thanks again to everyone.

mike

---

### Post by razor7 on 2009-11-10
Hello...since Karmic (Ubuntu 9.10) does not uses GDM anymore, what can I do to enable numlock at startup since login screen?

Thanks a lot!

---

### Post by mlnease on 2009-11-10
> **razor7 said:**
> Hello...since Karmic (Ubuntu 9.10) does not uses GDM anymore, what can I do to enable numlock at startup since login screen?

Thanks a lot!

Hi Razor,

I tried this (my earlier post) in Karmic out of the box and it seems to be working--have you tried it?

mike

p.s.  I do have GDM installed, by default?  Not sure--I don't remember installing it.  Anyway it is in the repos.  From Synaptic:

GNOME Display Manager

gdm provides the equivalent of a "login:" prompt for X displays- it
pops up a login window and starts an X session.

It provides all the functionality of xdm, including XDMCP support for
managing remote displays.

The greeting window is written using the GNOME libraries and hence
looks like a GNOME application- even to the extent of supporting
themes! By default, the greeter is run as an unprivileged user for
security.

Canonical provides critical updates for gdm until April 2011.

---

### Post by James7 on 2010-03-28
I've had this problem, and all the solutions out there I saw didn't seem to work.

I realised it was, for me at least, something different.

I went to System-->Preferences-->Keyboard-->Mouse Keys, and I turned off/unticked 'Computer can be controlled using the keyboard'. This fixed it for me. I hope that helps someone! :D

---

### Post by MrKenmore on 2010-04-28
James7-

That was the fix that worked for me!!!!

This has been driving me crazy for weeks!!!

Thanks.

:guitar:

---

### Post by Fiy on 2010-08-14
Thanks [mlnease]("http://ubuntuforums.org/member.php?u=188818"). I've been lookin all over for this.

---

