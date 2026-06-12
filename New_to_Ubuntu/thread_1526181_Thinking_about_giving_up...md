---
title: "Thinking about giving up..?"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by carbine83 on 2010-07-07
I've not been having a very good day with Ubuntu! Although I love its speed, applications etc, I'm having a few problems.

I tried to scan someone's hard disk today to clear it of malware they installed, on a USB caddy. KlamAV wouldn't work at all, saying /usr/klamav/something wasn't accessible. The 'update' button was greyed out, so that was useless to me. So I tried Avast! As I saw some good reviews for Linux users. That too just gave some cryptic error (syntax error illegal mount0!) or something similar, so that's not good as I couldn't achieve the solution to the problem, which was simply scanning a HDD for viruses.

I tried to install Wireshark and use it, and no NIC interfaces showed up.

Also, themes. Why am I having so many problems with them? I can't seem to get them to work properly, they tend to look terrible! With Compiz, GTK, Emerald, Emerald icon, 'Appearance', GNOME colour chooser, I'm finding it hard to make it look good, and to understand. Does the average user really want to faff with different themes, and learn all about the differences between window managers, theme mangers, decorators etc? I'm no newbie to I.T, I've been a server engineer in a data centre for years, but I'm struggling with making it look better than the standard orange / brown.

Data sync, are there any tools out there that are as good as synctoy? I tried Grsync gui, but that won't sync to a network share..

I don't want to go back to Windows, but these little niggles are starting to make me lose my enthusiasm for Ubuntu..  all of the above are easy in Windows. I know themes aren't a customisable, but at least I can go to one place and make all the changes I like!

Any hints or tips to fix these issues before I give up?

---

### Post by clhsharky on 2010-07-07
Sounds like you are still trying to run it like its MS.
If thats what you want to do, then I recommend paying the bill tax.

There are many HowTo's, Stickys, and ubuntu help at top of each page here in the forums.
[https://help.ubuntu.com/](https://help.ubuntu.com/)

Just ask for help if something doesn't work for you.
Did you learn windows in days?

Sharky

---

### Post by carbine83 on 2010-07-07
I didn't learn windows in days no, but..

Wireshark works in Windows
AVG, Avast!, McAffee, Norton etc work after installing
OSX, Windows, Blackberry, my PS3, my Creative Xen, even normal mobile phones have 'themes' in the same place, if you change a theme, it changes everything and doesn't have mouse pointers that refuse to change (known 10.04 bug) and windows that wrongly go translucent because some GTK+ theme isn't installed.

To me, swapping OS should be like changing your car. All the controls may be in a different place, the performance and handling may be totally different.. but I would not expect to have to open the choke, prime the carbs to start it, and then find the rear wiper is there for show, it doesn't actually work. Then because I think this isn't right, have someone tell me I don't know how to drive!

Don't get me wrong, I like Ubuntu a lot, I can just see where Linux may be losing a few points for people who aren't so technically minded.

However, I will have a troll through the rest of the forums to see if anyone else is having problems with AV, wireshark, themes and sync tools. Thanks -

---

### Post by jrothwell97 on 2010-07-07
Let's see...

I'm sorry Ubuntu's been a bit of a pain: sadly, it's not like changing cars. It's a bit like moving from a car to an intercity train: the principles are the same (get in, move from origin to destination, get out) but the architecture, operation and interface are wildly different.

However, the learning curve is worth it, so stick with it. :)

Anyway...


> **carbine83 said:**
> I tried to scan someone's hard disk today to clear it of malware they installed, on a USB caddy. KlamAV wouldn't work at all, saying /usr/klamav/something wasn't accessible. The 'update' button was greyed out, so that was useless to me. So I tried Avast! As I saw some good reviews for Linux users. That too just gave some cryptic error (syntax error illegal mount0!) or something similar, so that's not good as I couldn't achieve the solution to the problem, which was simply scanning a HDD for viruses.
How did you install KlamAV? It sounds like you tried to install it manually, which is a bit of a fudge and overcomplicating things - look in the Ubuntu Software Centre to install it otherwise.

My suggestion for Avast! is to first ensure that the drive you want to scan is *mounted*. Coming from a Windows background, the best way to describe this is ensuring that the drive has a mount point assigned. On Windows, drives are mounted as C:, D: etc. On Ubuntu, they're usually mounted under /media/*drivelabel*/. Then, try running Avast as the system administrator (*root*).

Logging in directly as *root* is highly inadvisable, and so it's disabled on Ubuntu by default. However, users with "administrative" privileges can "become" root for the purpose of running a certain application, by prepending an application's command with *sudo* (if it's a command line app), *gksudo* or *kdesudo* (for graphical apps on Ubuntu and Kubuntu respectively.) This asks for your password and then runs the app as root. This is just like UAC on Windows.

(Note: when you type in your password for *sudo*, nothing will appear as you type. This is normal, your password is still going in: just type and hit enter to finish.)

Finally, it's worth noting that Linux antivirus applications are generally not very good. The only reason to have them is to scan Windows drives for malware, and they're not even very good at this job: false positives and oversights are, sadly, the norm. My suggestion is that you should probably give this the once-over with a Windows anti-virus program before returning the hard drive to use (Microsoft Security Essentials is probably best here.)


> **carbine83 said:**
> I tried to install Wireshark and use it, and no NIC interfaces showed up.
Again, ensure you installed Wireshark using USC. Then follow [these instructions](http://ubuntuforums.org/showthread.php?p=8916343) which should do the trick.

> **carbine83 said:**
> Also, themes. Why am I having so many problems with them? I can't seem to get them to work properly, they tend to look terrible! With Compiz, GTK, Emerald, Emerald icon, 'Appearance', GNOME colour chooser, I'm finding it hard to make it look good, and to understand. Does the average user really want to faff with different themes, and learn all about the differences between window managers, theme mangers, decorators etc? I'm no newbie to I.T, I've been a server engineer in a data centre for years, but I'm struggling with making it look better than the standard orange / brown.
Theming is a bit of a victim of fragmentation.

Firstly, if you install a theme but get horrible Windows 95-style battleship grey oblongs, this is because the required "theme engine" hasn't been installed. You can usually do this through a program called Synaptic, which you can find in System/Administration/Synaptic Package Manager - the theme's documentation should tell you what engine it uses, so you can simply search for the engine's name, mark it for installation and install it.

The discrepancy with the different themable things (Metacity, GTK, Emerald, icons, etc.) means it's rather trial-and-error: it usually takes some degree of fiddling to build up a set that looks right. (This is another difference between Windows and Ubuntu: Ubuntu offers greater customisability out-of-the-box, at the penalty of fiddlyness when setting it up.)

> **carbine83 said:**
> Data sync, are there any tools out there that are as good as synctoy? I tried Grsync gui, but that won't sync to a network share..
There are various command-line solutions, but the most popular graphical solutions (assuming you mean file sync) are to use Dropbox or Ubuntu One.

Once again, I hope you'll stick at it: it'll pay off in the end. Good luck. :)

---

### Post by jerenept on 2010-07-07
Try restarting after installing KlamAV. It is highly recommended to install from Synaptic Package Manager or Ubuntu Software Center.

---

### Post by alphacrucis2 on 2010-07-07
I believe you need to run Wireshark as root to be able to capture interfaces as that is a privileged operation. Run wireshark this way:


```
gksu wireshark
```

---

### Post by uRock on 2010-07-07
Here is the fix for Wireshark;
> **Rubi1200 said:**
> <snip>
```
sudo apt-get install libcap2-bin wireshark
sudo chgrp admin /usr/bin/dumpcap
sudo chmod 750 /usr/bin/dumpcap
sudo setcap cap_net_raw,cap_net_admin+eip /usr/bin/dumpcap

```


You can use SAMBA or Filezilla for file sharing.

Themes are easy to change, just right-click on the desktop and choose "Change Desktop Background," then click on the themes tab.

---

### Post by vidasov on 2010-07-07
Calm down, pls.
the man told you right, do not try to use it as windoze. so you'll have to learn something and you will be glad after all ...

Wireshark is kind of special, so run it like root with typing:

```
$ sudo wireshark 
```

for now. 
Go to [http://ubuntuguide.org/wiki/Ubuntu:Lucid#Anti-virus]("http://ubuntuguide.org/wiki/Ubuntu:Lucid#Anti-virus") and find answer for AV.

When you are finish go back to home of above url and read carefully.

after that type:

```
$ man man
```

I can remember days when saying: "RTFM!" was quite usual to novice like you on the places like this. 
After some time you will find better solutions for this, every and any problem, so calm down and enjoy with your PC rebirth.

---

### Post by Lucky. on 2010-07-07
> However, the learning curve is worth it, so stick with it.

Bam!  Perfectly said.

During my conversion I've found some seriously annoying things about Linux as well.  But after powering through it, it's pretty much awesome.  Now I'm hitting the Microsoft forums going "Hey guys, how come you can't get this stuff working right like they do in the Linux world?"

Take a deep breath and chug at it here and there.  If it's no good right now, come on back in a year or so and see if things have gotten better.  Stick on the forums and ask for help or learn from others in your situation as well.

---

### Post by spydeyrch on 2010-07-07
Sorry to hear that you are having issues. I may have a few links that may be worth your while, maybe not.

> 
I'm sorry Ubuntu's been a bit of a pain: sadly, it's not like changing  cars. It's a bit like moving from a car to an intercity train: the  principles are the same (get in, move from origin to destination, get  out) but the architecture, operation and interface are wildly different.


That is very very true!! I always enjoy reading [Linux != Windows]("http://linux.oneandoneis2.org/LNW.htm") but please, take it with a grain of salt. I am not saying that you should leave windows nor linux. I just like the reading because it gives some very useful ideas and concepts about linux.

As far as the whole virus thing may go, here are a few ideas:

[http://www.howtogeek.com/howto/9283/superantispyware-portable-is-the-must-have-spyware-removal-tool-you-need/](http://www.howtogeek.com/howto/9283/superantispyware-portable-is-the-must-have-spyware-removal-tool-you-need/)

[http://portableapps.com/](http://portableapps.com/)

[http://www.howtogeek.com/howto/9487/how-to-remove-internet-security-2010-and-other-roguefake-antivirus-malware/](http://www.howtogeek.com/howto/9487/how-to-remove-internet-security-2010-and-other-roguefake-antivirus-malware/)
[URL="http://www.howtogeek.com/howto/8693/how-to-remove-antivirus-live-and-other-roguefake-antivirus-malware/"]
http://www.howtogeek.com/howto/8693/how-to-remove-antivirus-live-and-other-roguefake-antivirus-malware/[/URL]

[http://www.howtogeek.com/howto/9317/how-to-remove-advanced-virus-remover-and-other-roguefake-antivirus-malware/](http://www.howtogeek.com/howto/9317/how-to-remove-advanced-virus-remover-and-other-roguefake-antivirus-malware/)

[http://www.howtogeek.com/howto/14434/scan-a-windows-pc-for-viruses-from-a-ubuntu-live-cd/](http://www.howtogeek.com/howto/14434/scan-a-windows-pc-for-viruses-from-a-ubuntu-live-cd/)

I think that the last one there is probably going to be what you might need.

I had to use a combination of all of those above to clean a friend's computer. It took quite a while.

Hopefully you find something there that can help.

-Spydey :D

---

### Post by carbine83 on 2010-07-08
Thanks everyone, especially [jrothwell97]("http://ubuntuforums.org/member.php?u=72496") for the tips and the wireshark info from people.

I can't help but notice that people seem to take any criticism of Linux very personally and are quick to assume I only know how to use Windows..

Some said on here 'as a newbie' etc but I'm only a n00b to Ubuntu, I've been in I.T. for over 10 years now in data centre infrastructure. We use UNIX,AS/400, Windows Server 2003 / 2008, and have dabbled with OSX.

Now I understand that I may have overlooked the running as root for apps, that may help. 

I won't give up with Ubuntu just yet, but I really do think that some programs should work a bit better 'out of the box' for more normal users to get along with Ubuntu. I think that's my main point! Maybe that's the flaw with open source, too many distros that programmers have to make sure their apps works with everyone one?

And I know how to change themes in 'appearance' what I mean is to set a nice theme like a glassy effect, with nice fonts, pointers, sounds etc, you have to go into a bunch of different theme managers. I think [jrothwell97]("http://ubuntuforums.org/member.php?u=72496") eluded to the fact that this isn't great in Linux. 

Thanks to everyone who posted useful replies, hopefully I can solve these little issues to restore my faith in Ubuntu!

p.s. I am calm.. it's only a pile of silicon and plastic, with a bit of metal thrown in for fun :P

Right, time to fix a Windows 2003 print server that keeps locking and taking down terminal servers, oh the irony!

---

### Post by quinnten83 on 2010-07-08
> **carbine83 said:**
> I didn't learn windows in days no, but..

Wireshark works in Windows
AVG, Avast!, McAffee, Norton etc work after installing
OSX, Windows, Blackberry, my PS3, my Creative Xen, even normal mobile phones have 'themes' in the same place, if you change a theme, it changes everything and doesn't have mouse pointers that refuse to change (known 10.04 bug) and windows that wrongly go translucent because some GTK+ theme isn't installed.

To me, swapping OS should be like changing your car. All the controls may be in a different place, the performance and handling may be totally different.. but I would not expect to have to open the choke, prime the carbs to start it, and then find the rear wiper is there for show, it doesn't actually work. Then because I think this isn't right, have someone tell me I don't know how to drive!

Don't get me wrong, I like Ubuntu a lot, I can just see where Linux may be losing a few points for people who aren't so technically minded.

However, I will have a troll through the rest of the forums to see if anyone else is having problems with AV, wireshark, themes and sync tools. Thanks -

I happen to know that clamav and wireshark both need superuser rights to work properly. I believe wireshark tells you this at first start up!
try in terminal sudo wireshark /clamav, insert password. It should then work. And please don't say that a noob should be able to run this from get go, because we both know that a regular user would not even know what wireshark is.
Also strangely enough you seem to be one of the very few people who has problems with the themes. I'm just saying, maybe it just isn't Ubuntu....

---

### Post by quinnten83 on 2010-07-08
> **carbine83 said:**
> Thanks everyone, especially [jrothwell97]("http://ubuntuforums.org/member.php?u=72496") for the tips and the wireshark info from people.

I can't help but notice that people seem to take any criticism of Linux very personally and are quick to assume I only know how to use Windows..

Some said on here 'as a newbie' etc but I'm only a n00b to Ubuntu, I've been in I.T. for over 10 years now in data centre infrastructure. We use UNIX,AS/400, Windows Server 2003 / 2008, and have dabbled with OSX.

Now I understand that I may have overlooked the running as root for apps, that may help. 

I won't give up with Ubuntu just yet, but I really do think that some programs should work a bit better 'out of the box' for more normal users to get along with Ubuntu. I think that's my main point! Maybe that's the flaw with open source, too many distros that programmers have to make sure their apps works with everyone one?

And I know how to change themes in 'appearance' what I mean is to set a nice theme like a glassy effect, with nice fonts, pointers, sounds etc, you have to go into a bunch of different theme managers. I think [jrothwell97]("http://ubuntuforums.org/member.php?u=72496") eluded to the fact that this isn't great in Linux. 

Thanks to everyone who posted useful replies, hopefully I can solve these little issues to restore my faith in Ubuntu!

p.s. I am calm.. it's only a pile of silicon and plastic, with a bit of metal thrown in for fun :P

Right, time to fix a Windows 2003 print server that keeps locking and taking down terminal servers, oh the irony!

Sorry dude, 
It's not about taking it personally, but way too many people come in here pretending they know better how things should work and that because things don't work the way they think it should is the reason why Linux is losing market-share/ not gaining enough.
(Well thank you for coming in and bringing civilization to us IT savages)
The never take a moment to think that perhaps there are other ways of doing things and that their understanding of the workings of Linux might be limited/tainted/incomplete. It comes off as standoffish. And it crawls up people's butt, at least mine.
I don't mean to be rude, but really, there are some days when you just can't deal (and today is one of those days, so I apologize...)
other than that, Welcome to Ubuntu, there is a learning curve, but ask questions and you'll see that things will become clear to you in no time....

---

### Post by Paqman on 2010-07-08
> **carbine83 said:**
> 
Data sync, are there any tools out there that are as good as synctoy? I tried Grsync gui, but that won't sync to a network share..


Sure it will, if you have the share mounted to a folder locally. If you just browse to the share through Nautilus and connect that way you'll have trouble. But if you mount the share through an entry in /etc/fstab then it'll function exactly like a local folder.

Rsync is the best thing since sliced bread.

---

### Post by Grenage on 2010-07-08
> I can't help but notice that people seem to take any criticism of Linux very personally and are quick to assume I only know how to use Windows..

Generally speaking, that is the case;  I've met and worked with people who have been in IT for 20+ years, and I wouldn't let them anywhere near one of my machines.  I'm not saying that's you, I'm simply saying that X years spent with computers does not equate to a particular mindset.

That aside, Ubuntu is supposed to be easy to use.  Provided all of your devices are supported and you are lucky enough to dodge the bugs - it is.  When it comes to Linux, you'll either get on with it and battle though because you like the way the system works, or you'll go back to Windows/Mac et cetera.

There's nothing wrong with deciding you can't be bothered with yet another OS that probably won't be mainstream in your lifetime (or ever).

---

### Post by ECET on 2010-07-08
Hello, I would like to suggest you buy the book that I bought. Its called Ubuntu tip, tricks and hacks. Cost me 30 bucks, but it has a plethora of information in it. Got it at a local bookstore, and I think you can buy it here online as well. I am a very....very newbie to Linux an have been able to resolve some "sticky" issues ie wireless on my own with this book. So give er a try......and good luck to you..

---

### Post by Tholley on 2010-07-08
As for you visual issues, I have my Ubuntu looking way better that even Win7. It did take a little time to tweak it, but at least I can say "look what **I **did! Ain't it cool!"
 
Here are some links that have helped me out in the past...
 
[http://www.johannes-eva.net/index.php?page=2009_10_useful_ubuntu_guide_karmic](http://www.johannes-eva.net/index.php?page=2009_10_useful_ubuntu_guide_karmic)
 
[http://my.opera.com/ubuntunerd1/blog/](http://my.opera.com/ubuntunerd1/blog/)
 
[http://ubuntuguide.net/](http://ubuntuguide.net/)
 
hope these help! ;)

---

### Post by uRock on 2010-07-08
Check out this tutorial on themes. This gal has quite a few great tutorials for making the system look and run hot. [http://www.youtube.com/watch?v=gl-tmGfQrzs](http://www.youtube.com/watch?v=gl-tmGfQrzs)

---

### Post by 3rdalbum on 2010-07-08
Themes can be a bit confusing, but I learnt it through trial and error really.

You will really need to get used to the concept of 'root' and permissions, especially being in IT. All operating systems are moving toward restriction of privileges to ordinary users, for safety and security. That's why Wireshark needs to be run as root (it does very low-level things) and why ClamAV can't write an updated definitions file without being root (because /usr/klamav/ is a system directory, and your ordinary user account can't write to anything outside /home/username).

---

