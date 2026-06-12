---
title: "How can I get rid of Avast?"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by al.adab on 2009-12-01
Having installed Avast according to [http://www.ubuntugeek.com/avast-anti...u-desktop.html](http://www.ubuntugeek.com/avast-anti...u-desktop.html), (and having obtained the licence key) I can't now use it. 

If I click on the icon in start-menu, I get the following error message: 

*Deleted stale lock file '/home/daniele/.avast/lockfile-daniele'*

followed by the licence key window. If I enter the license key + click ok, the windows disappears, but nothing more happens. 

I tried launching it from terminal, and here's what I get (followed by the error message + license key window above): 

[I]~$ avastgui
test: 95: avastgui: unexpected operator

(process:7265): Gdk-WARNING **: locale not supported by Xlib

(process:7265): Gdk-WARNING **: can not set locale modifiers
Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
Segmentation fault[/I]

I don't seem to be able to uninstall it. *Avast* or *avastgui *
are not in Synaptics and do not respond under *sudo apt-get remove*. If there's no solution, can you please tell me how to get rid of the whole thing (and possibly recommend an alternative anti-virus - I've been advised to install one re: interaction with colleagues who're on Windows). 

Thanks.

---

### Post by al.adab on 2009-12-01
sorry I've just realised I've posted the wrong link: I installed Avast according to 

[http://www.ubuntugeek.com/avast-antivirus-for-ubuntu-desktop.html](http://www.ubuntugeek.com/avast-antivirus-for-ubuntu-desktop.html)

(link given in the first thread is broken)

---

### Post by Soul-Sing on 2009-12-01
```
sudo dpkg -r avast4workstation
```
and remove it from the user/share folder.

---

### Post by al.adab on 2009-12-01
Thanks leoquant
After running *sudo dpkg -r avast4workstation* Avast is then completely removed?

---

### Post by Astrals on 2010-01-05
> **leoquant said:**
> ```
sudo dpkg -r avast4workstation
```and remove it from the user/share folder.


Thanks again, removed as well.

Avast was working great then it just stopped working giving me an error:
"/usr/bin/avast: 178: /usr/lib/avast4workstation/bin/avast: not found"

Original install command for avast:
"sudo dpkg --force-architecture -i '/home/xxxx/Desktop/avast_v1.3.0-2_i386-deb/avast4workstation_1.3.0-2_i386.deb'

I use ubuntu-9.10-alternate-amd64.

I had to use this via command line which is no problem for me.

If anybody knows a fix for this your help will be appreciated.


I now need an antivirus for scanning files, is there an antivirus that works great on 64 bit architectures?

---

### Post by sliketymo on 2010-01-05
clamAV.

---

### Post by Astrals on 2010-01-15
I use ubuntu-9.10-alternate-amd64.


My original post:
[http://forum.avast.com/index.php?topic=53107.0](http://forum.avast.com/index.php?topic=53107.0)

Got it working again via command line.
It turned out that I needed to install ia32-libs.
Got the idea from:
[http://ubuntuforums.org/showthread.php?t=781251](http://ubuntuforums.org/showthread.php?t=781251)

That was all I installed, now works great once again via terminal.

Looks like it was an update that stopped it from working and not my fault. (good news for me).

Thank you everybody for your help with this it was much appreciated and as usual I posted my results for good news.


I put this here as well to help anybody out with the same issue.

---

### Post by warfacegod on 2010-01-16
So my question is this. Why are you guys using Avast on Linux? I believe Avast does active virus protection which is almost totally pointless in Linux. It's just slowing down your computers and internet connections. The only real reason to use anti-virus software in Linux would be to protect a Windows machine. +1 to  sliketymo for suggesting clamAV. It sits there and does nothing until you tell it which is the way it should be in Linux.

---

### Post by llamabr on 2010-01-16
> **warfacegod said:**
> So my question is this. Why are you guys using Avast on Linux? The only real reason to use anti-virus software in Linux would be to protect a Windows machine. 

I guess you answer your own question.  Some folks run the software on their linux box to protect their windows machine.  Even if a windows virus won't infect a linux computer, your ubuntu will certainly send it on to your windows computer, unless it's told not to.

Right?

---

### Post by warfacegod on 2010-01-16
> **llamabr said:**
> I guess you answer your own question.  Some folks run the software on their linux box to protect their windows machine.  Even if a windows virus won't infect a linux computer, your ubuntu will certainly send it on to your windows computer, unless it's told not to.

Right?

Yes that is true but in my opinion it never justifies the resource drain when the alternative is: click, check this thing here, it's okay?, click off. And then move the file. That's, what? fifteen seconds?

---

### Post by -kg- on 2010-01-16
> **warfacegod said:**
> So my question is this. Why are you guys using Avast on Linux? I believe Avast does active virus protection which is almost totally pointless in Linux. It's just slowing down your computers and internet connections. The only real reason to use anti-virus software in Linux would be to protect a Windows machine. +1 to  sliketymo for suggesting clamAV. It sits there and does nothing until you tell it which is the way it should be in Linux.

Ah, but the day is coming:

[URL="http://www.lockergnome.com/linux/2009/12/08/proof-of-linux-malware-in-action/?utm_source=feedburner&utm_medium=email&utm_campaign=Feed%3A+nexus%2Flinux+%28Linux+Fanatics%29"]
Proof Of Linux Malware In Action[/URL]

and:

[Even More Linux Malware!]("http://www.lockergnome.com/linux/2009/12/09/even-more-linux-malware/?utm_source=feedburner&utm_medium=email&utm_campaign=Feed%3A+nexus%2Flinux+%28Linux+Fanatics%29")

I don't know if A/V software like Avast or Clamav will catch these types of mailware, but other types of Badware can be written as well.  Linux is not immune to virus and other malware infection, it's only immune to virus and other malware that is written for Windows.

I've recently found malware (worms and trojans) in my mail files.  While I'm not overly worried about infection on my machine, I'd hate to think that I had forwarded it to a bunch of my friends who run Windows.

Another consideration: Over the years, Linux has been described as a "hackers OS," only to be used by the geeks and computer experts.  The Linux community has worked just as hard to show that "Linux is ready for the desktop."  Well, we have had some success.

More and more casual users are migrating over to Linux, many bringing their Windows habits with them.  Automatic virus scanning may not be such a bad idea, especially in the future.  The above is going to happen more and more...it's a foregone conclusion.

---

### Post by warfacegod on 2010-01-16
The day may be coming but it won't be for us. It will be for Windows converts that can't change their thinking. Linux is not Windows and unfortunately more and more users are coming over and their habits stay the same. What's this, click. What's that, click. Flashing stuff, click. Oh look [email]seedylookinglotsofnumbersinthenamelikeadvertisedonlatenighttv@giveusyourstuff.con[/email], click.

I have come to believe that the best AV software ever written is installed in the human brain.

---

### Post by Astrals on 2010-01-17
I don't mean to be rude but I do hate windows as much as anybody else here, but I don't want to be a a**hole and pass problems on to my friends, after all how would you like it if it was reversed.

Avast is not a drain either on my system, It is the linux version (of course) on only runs when I start the app via command line.

I have had enough problems when I used windows to last a couple of life times.

My motto:
 "Once you use linux, learn a few basics, you'll never go back to the windows darkness!"

Also I have found this forum to be very helpful, everybody here tries to help each other.

I hope this helps.

---

### Post by warfacegod on 2010-01-17
It is the Windows users themselves that have allowed the proliferation of viruses. Now that many of those users are switching to Linux, it stands to reason that the viruses will follow. Anti-virus by it's very nature can never be anything more than a reactive measure. The only truly active measure anyone can employ is their own common sense. I personally have no interest in having to take on a responsibility for, what is in essence, others foolishness and blatant stupidity.

---

### Post by Astrals on 2010-01-18
> **warfacegod said:**
> It is the Windows users themselves that have allowed the proliferation of viruses. Now that many of those users are switching to Linux, it stands to reason that the viruses will follow. Anti-virus by it's very nature can never be anything more than a reactive measure. The only truly active measure anyone can employ is their own common sense. I personally have no interest in having to take on a responsibility for, what is in essence, others foolishness and blatant stupidity.


That's a very fair call, I can respect your view.
Not everybody is has enough system management skills to keep that in mind, e.g my sister in nearly "computer illiterate" as it could be put, so I'm teching her the very basics of linux. She also has been doing basic computer courses and of ******* course they have to use microsoft office for it. hence virtualbox introduction next on the list for her..

---

### Post by warfacegod on 2010-01-18
> **Astrals said:**
> That's a very fair call, I can respect your view.
Not everybody is has enough system management skills to keep that in mind, e.g my sister in nearly "computer illiterate" as it could be put, so I'm teching her the very basics of linux. She also has been doing basic computer courses and of ******* course they have to use microsoft office for it. hence virtualbox introduction next on the list for her..

"Google" Microsoft Academy

Then.

"Google" Linux Academy

---

