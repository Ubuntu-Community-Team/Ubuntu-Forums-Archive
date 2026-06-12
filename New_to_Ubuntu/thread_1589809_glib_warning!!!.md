---
title: "glib warning!!!"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by DarinB on 2010-10-07
at boot after todays update I get a terminal 
tty login when i put my name in an hit enter it flashes this 
GLIB WARNING ** GLib - getpwuid_r(): failed due to unknown user id (0)
then jumps to gui....what the in the world is happening????

---

### Post by formaldehyde_spoon on 2010-10-07
I don't actually know what the problem is specifically, but: 
Your user name is associated with a user id (number).  
Default is 1000 for the first user, but it seems to be trying 0 for you, which is usually root, I think.

---

### Post by jtarin on 2010-10-07
Try it the second time and see if it stills exist.

---

### Post by DarinB on 2010-10-07
I appreciate the input but I have no idea what that really means or what to do about it. any solutions about this??? anybody? And here I was starting to relax that 10.04 based linux mint was doing so well...but this seems like an ubuntu issue since it happened today after an update

---

### Post by jtarin on 2010-10-07
Did you follow my above recommendation? What your are seeing is normal messages that for the largest percent of the time mean nothing of importance. Similar messages are generated with different processes in Windows. The difference being Windows hides them from the average user. Linux is more transparent about what goes on.

---

### Post by jtarin on 2010-10-07
Its a long long known upstream plymouth bug. Errors with Intel  chipset. Not only on Ubuntu, but with all distros I have tried to verify this, including Fedora and Arch, I get the same bug at the start of boot process. But unlike Arch, the Fedora and Ubuntu kernels are highly patched to suppress the warning output, so the user can only see them in the verbose boot mode.If it bothers you try upgrading to another kernel and maybe it is patched....it's harmless.

---

### Post by DarinB on 2010-10-07
yeah it comes up every time. 
But it happens after my grub menu.
I did try the app Barry for my blackberry but i removed it and its libs just in case that did it. 
it still comes up...every log in
this is freaking me out and it is extra stuff to do login twice on the black screen that comes up i put in my login then it comes up password i add my password then the glib comes up no other errors just a flash of the glib warning and it goes to my gui log in
not sure what the first line says other than tty .....login I tried just hitting enter but that did not work until i typed in my username then may password. 
could it have been todays update???

AHHHH help I really do hope it is not a big deal

---

### Post by DarinB on 2010-10-07
btw my post of appreciating more help was directed at formaldehy not jtarin>
Jtarin I appreciate your response thanks

---

### Post by DarinB on 2010-10-07
hmmm i have had real headaches with kernel upgrades in the past.
kind of above my skill level. do you know that it will help?
and why now after months and hundreds of boots???? 
what could have changed for this to come up now????
all i recall today is the update this morning with 17 updates, and the addition of barry and libs which i removed. 
I wonder i others have seen this today.

---

### Post by jtarin on 2010-10-07
Why are you logging in in a termial....why not GDM?

---

### Post by jtarin on 2010-10-07
Why are you logging in in a terminal....why not GDM?

---

### Post by jtarin on 2010-10-07
[Installing a new kernel]("http://beginlinux.com/twitter/1101-ubuntu-kernel").Then upon boot you will have a choice of more than one kernel. Try the new one.Don't like it...uninstall from the same location.

---

### Post by DarinB on 2010-10-07
I just saw your post this morning....
I have no choice to log in on terminal that is what comes up instead of the gui log in.
I did a recovery and chose fix broken packages. it updated my kernel an then i rebooted and it worked fine. a little slow but so far so good.

I still am not sure what happened.

---

### Post by DarinB on 2010-10-09
New event occurred 
I log into windows and later into my ubuntu partition and it went to terminal asked for login password then went to terminal logged in and then 
the glib warning user id (0) then showed a terminal and 
booted to gui???

any Ideas what has happened????

---

### Post by jtarin on 2010-10-09
First check your /etc/X11/default-display-manager
does it contain /usr/sbin/gdm ? If  not add it and try. Still no joy...try below.

command line```
gksudo gedit /etc/rc.local
``` Add the line```
gdm &
```
to the end of /etc/rc.local just before "exit 0", reboot

---

### Post by DarinB on 2010-10-09
before I got your last post I tried setting the auto log in and it did auto login to gui very slow but it did. but I remember i had other issues with the theme with auto log in. not sure I will post what you just asked be back in a moment

---

### Post by DarinB on 2010-10-09
it gave a warning can't find user...not sure if this is good but it did mess up my theme??? what did the change you recommended do???

---

### Post by jtarin on 2010-10-09
It's starts the Gnome Display manager at the init (run-level) you booting to.

---

### Post by jtarin on 2010-10-09
Try going to Main Menu System>Administration>Users and Groups and add your user to the "gdm" group.If it boots OK...the theme will have to be adjusted for the user now as it was installed under a different user (0).

---

### Post by DarinB on 2010-10-09
uh oh! i did not check the first part 
but added the gdm & anyway...silly mistake
> First check your /etc/X11/default-display-manager
does it contain /usr/sbin/gdm ? If not add it and try. Still no joy...try below.
and i just tried and get this response
> darin@darin-desktop ~ $ /etc/X11/default-display-manager
bash: /etc/X11/default-display-manager: Permission denie

sorry I am so lame about all this

---

### Post by jtarin on 2010-10-09
Sudo,sudo,sudo,sudo

---

### Post by DarinB on 2010-10-09
how to I add darin to the gdm group?

---

### Post by DarinB on 2010-10-09
darin@darin-desktop ~ $ sudo /etc/X11/default-display-manager
[sudo] password for darin: 
sudo: /etc/X11/default-display-manager: command not foun

thanks for your patience

---

### Post by jtarin on 2010-10-09
OK.....gksudo gedit /etc/X11/default-display-manager

---

### Post by jtarin on 2010-10-09
When you need to edit a text file you can use the command gksudo gedit. gksudo is the sudo command for an application that will open in a graphical user interface. Therefore gksudo gedit will open the Gnome editor in a root environment for you to edit files normally only allowed by root, This gives you temporary permisssion.

---

### Post by DarinB on 2010-10-09
ok now I see that Yes it does it contain /usr/sbin/gdm
so at least that is working and I just rebooted and it did boot properly 
I still did not add darin to gdm? 
should I ???
and what is going on is it related to booting into the windows partition?

---

### Post by jtarin on 2010-10-09
Yes add user to gdm group as I suggested.....it won't hurt.

---

### Post by DarinB on 2010-10-09
ok but when i go into the users and groups I can't figure out how to do it. 
I have to find a simple how to. 
also do you think this related to the windows partition boot??? and should I avoid using windows at all costs?

---

### Post by theozzlives on 2010-10-09
> **DarinB said:**
> ok but when i go into the users and groups I can't figure out how to do it. 
I have to find a simple how to. 
also do you think this related to the windows partition boot??? and should I avoid using windows at all costs?

Click on Manage Groups, find GDM, highlight it, click properties, put a check next to your name, click "OK". No the Windows install shouldn't be causing it.

---

### Post by jtarin on 2010-10-09
> and what is going on is it related to booting into the windows partition?Nothing

---

### Post by DarinB on 2010-10-09
ok I went to terminal and used groups darin and saw that I am a member of gdm so that is solved but I don't know what to do about using windows partition I need to to be able to use streaming netflix? what would you do in this case???

---

### Post by theozzlives on 2010-10-09
> **DarinB said:**
> ok I went to terminal and used groups darin and saw that I am a member of gdm so that is solved but I don't know what to do about using windows partition I need to to be able to use streaming netflix? what would you do in this case???

Just leave it Dual-Boot, it's not gonna hurt anything (besides taking up space). You'll be alright, I promise.

---

### Post by jtarin on 2010-10-09
> streaming netflix]If thats the only thing keeping you from ditching windows you might entertain the thought of using a virtual environment (virtualbox) to install windows in Linux to run your windows apps.

[Inside skinny]("http://jacksonh.tumblr.com/post/965806498/how-to-watch-netflix-streaming-movies-on-linux-with")

---

### Post by DarinB on 2010-10-09
it seems that netflix doesn't work in windows on virtual box. 
so wonder if the booting into windows is causing the problem and how is it the cause???

---

### Post by jtarin on 2010-10-09
> **DarinB said:**
> it seems that netflix doesn't work in windows on virtual box. 
so wonder if the booting into windows is causing the problem and how is it the cause???If you are dual booting Windows and it is on a separate partition there is no connection between something not working in one Operating System being caused by the other. How do you know Netflix will not run in a VirtualBox setup in Linux? Did you already try?

---

### Post by DarinB on 2010-10-10
i read it in the forums that netflix streaming won't work in virtualbox but I don't have a legitimate copy of xp and the vista i have from this box i can't get to load let alone install in virtual box...when i tried with my Illegitimate/corporate copy of xp it killed the grub and I ended up with I think a grub 17 error and had to reinstall Ubuntu. This morning I did get the glib error and then a message that id not found then it went to the gui log in. so that is ok, I guess... for Day one. I am sure I will keep you posted. therefore the use of windows was just coincidence, it booted fine about four times with the new kernel we did yesterday until I went to windows. but if you guys say it ain't so i will believe you.

---

### Post by jtarin on 2010-10-10
> **DarinB said:**
> i read it in the forums that netflix streaming won't work in virtualbox but I don't have a legitimate copy of xp and the vista i have from this box i can't get to load let alone install in virtual box...when i tried with my Illegitimate/corporate copy of xp it killed the grub and I ended up with I think a grub 17 error and had to reinstall Ubuntu. This morning I did get the glib error and then a message that id not found then it went to the gui log in. so that is ok, I guess... for Day one. I am sure I will keep you posted. therefore the use of windows was just coincidence, it booted fine about four times with the new kernel we did yesterday until I went to windows. but if you guys say it ain't so i will believe you.When you have the time look at my signature for the EasyBCD link.....optional way to dual boot.

---

### Post by barnestech on 2010-10-10
It looks like Darin B ran into the same issue that I had after an update.

1) I believe that I always had a glib warning before this update, (if I saw the console) but who cared as I never had to stare at it until now!

2) The console appears for quite a while (20 secs+) before continuing the boot process into gnome.  It shows a login just like it always would if we chose to look at the console during boot.  It would just flash by before....

I logged in as user in the console and "surprise"  GDM popped up.  When I fell for it the first time, I just rebooted and waited for GDM.

3) I downgraded GDM and am going to lock the version.  This appears to be most of the culprit.

4) Looks like it may be time for a bug report....

---

### Post by DarinB on 2010-10-10
how did you downgrade gdm and besides everything I did what is gdm?

---

### Post by jtarin on 2010-10-10
GDM is **[COLOR="Red"]G[/COLOR]**nome **[COLOR="red"]D[/COLOR]**isplay **[COLOR="red"]M[/COLOR]**anager. Do not downgrade yours. If yours works now leave it. His works because he reinstalled and it updated the files you configured by hand. Yours works because you repaired yours.

---

### Post by DarinB on 2010-10-10
Thanks for stopping me....greatly appreciated

---

### Post by jtarin on 2010-10-10
> **DarinB said:**
> Thanks for stopping me....greatly appreciated
You have learned you have the ability to repair your system. There are many things you can do in Linux yourself when you learn how. It's not all about re-installing all the time.

---

### Post by DarinB on 2010-10-11
I imagine so I did go to school on the side and got my microsoft certs but only use it for my own use. I find many of the problems I face with Ubuntu I lack the resources to resolve them myself. And at times lack the knowledge of how the system works. Maybe one day got get certified in it.
thanks so much

---

### Post by DarinB on 2010-10-13
my ubuntu locked up while using firefox. I tried control alt backspace to log out i got a system check every thing was ok but i had a gdm binary failure, now I can't reboot I get system disk error I am using a live cd any ideas what to do???

---

### Post by jtarin on 2010-10-13
> **DarinB said:**
> my ubuntu locked up while using firefox. I tried control alt backspace to log out i got a system check every thing was ok but i had a gdm binary failure, now I can't reboot I get system disk error I am using a live cd any ideas what to do???**system disk error**  can be caused by non-bootable media, wrong boot order in bios or bad harddrive.

[GDM Binary manpage]("http://manpages.unixforum.co.uk/man-pages/unix/solaris-10-11_06/1/gdm-binary-man-page.html")

You read my response to your PM?

---

### Post by barnestech on 2010-10-20
I didn't check back here very quickly...

I did NOT "reinstall" GDM, I've been using Ubuntu since 5.10 and I haven't done such a thing yet!
I simply downgraded the version via synaptic.
The offending version was "2.30.2.is.2.30.0-0ubuntu4" from the lucid-updates repo.
If this version is installed in this machine (and so far only this one-I am running several with lucid) It delays the boot process for over a minute and shows a CLI login before the GUI starts.

Synaptic>Package>force version>lock version

It worked for me on this machine in this case.

Your mileage may vary....:)

---

