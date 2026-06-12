---
title: "AVG Installation Help"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by JumpForJoy on 2009-08-31
I have read this guid: [https://help.ubuntu.com/community/Antivirus/Avg](https://help.ubuntu.com/community/Antivirus/Avg), but I still can't manage to get AVG working on my new install on ubuntu.  I can download the package fine, and install it fine, but I can't find it after I do that.  The instructions say to look under Main Menu or run some commands, but I can't find it under Main Menu and the commands fail.

Thanks for any help,
Kiwi

BTW: I understand their are already some threads about this, but if you could point me to one that was solved I would greatly appreciate it.

---

### Post by sandyd on 2009-08-31
theirs not really any need for antivirus in ubuntu. really.

---

### Post by UbuntuNerd on 2009-08-31
can I ask the reason why you want to install AVG?

---

### Post by JumpForJoy on 2009-08-31
I thought you'd say that =)
I just want it for passing files on to windows machines, and for wine...
If it turns out I don't need it.  I can always just remove it.  :)

---

### Post by red_spyder on 2009-08-31
Here's a question relating to that: can a win32 virus have an effect on wine? Since windows programs run natively on it?

---

### Post by NoaHall on 2009-08-31
No, a Windows virus will not affect wine - it's only a compatibility layer.

Instead of avg, why not use ClamAV? (sudo apt-get install clamav)

---

### Post by JumpForJoy on 2009-08-31
I heard clamAV is slower and less efective, is that not the case?  I also think that the gui of AVG would be nice.  It is gui right?

---

### Post by SunnyRabbiera on 2009-08-31
> **JumpForJoy said:**
> I thought you'd say that =)
I just want it for passing files on to windows machines, and for wine...
If it turns out I don't need it.  I can always just remove it.  :)

> **red_spyder said:**
> Here's a question relating to that: can a win32 virus have an effect on wine? Since windows programs run natively on it?


No, Wine is not system wide.
Each wine program is only installed for a single user... there is no root (administrative) access for it.
Its near impossible for wine to catch a virus, its not tied into the web browsers all is fine...
Unless you want IE under linux or something.

> **JumpForJoy said:**
> I heard clamAV is slower and less efective, is that not the case?  I also think that the gui of AVG would be nice.  It is gui right?

Clam is actually quite fair, plus it does have GUI's

---

### Post by UbuntuNerd on 2009-08-31
> **NoaHall said:**
> No, a Windows virus will not affect wine - it's only a compatibility layer.

Instead of avg, why not use ClamAV? (sudo apt-get install clamav)

I second that :)

---

### Post by NoaHall on 2009-08-31
clamav is fast, quick, and powerful - more than enough for system that can't really get viruses anyway. It also has a gui, and in my experience, works better than AVG on linux.

---

### Post by JumpForJoy on 2009-08-31
> **NoaHall said:**
> clamav is fast, quick, and powerful - more than enough for system that can't really get viruses anyway. It also has a gui, and in my experience, works better than AVG on linux.

Ok, thanks.  I'll try that then.  What would be the best way to remove AVG completely though after installing it?  I'm kinda new getting back into linux and I want to keep things clean.
Thanks,
JumpForJoy

---

### Post by JumpForJoy on 2009-08-31
Sorry for the double post, but I was also wondering, what is a good firewall/gui firewall for Ubuntu.  Do I need one?

Thanks,
JumpForJoy

---

### Post by NoaHall on 2009-08-31
"sudo apt-get remove --purge avg" (or is it sudo apt-get remove --purge avg8.5free, can't remember, just type avg and use "tab" to find it out)

---

### Post by JumpForJoy on 2009-08-31
Thanks!

---

### Post by MelDJ on 2009-09-01
> **JumpForJoy said:**
> Sorry for the double post, but I was also wondering, what is a good firewall/gui firewall for Ubuntu.  Do I need one?

Thanks,
JumpForJoy

you could use firestarter sudo apt-get install firestarter

---

### Post by anujpathania on 2009-09-01
There is no need for an anti-virus in Linux dude.

If you still want for the sake of having one, then try clamAV but it also scans for only windows viruses. There are no viruses in Linux.

---

### Post by MelDJ on 2009-09-01
> **anujpathania said:**
> There is no need for an anti-virus in Linux dude.

If you still want for the sake of having one, then try clamAV but it also scans for only windows viruses. There are no viruses in Linux.

theoretically there are linux viruses for example bliss. but they dont pose a threat if  you have a strong password and do not run as root

---

### Post by lisati on 2009-09-01
The latest Ubuntu-friendly version of AVG free appears to be command-line only. You can download [http://www.avg.com/filedir/inst/avg85flx-r287-a2632.i386.deb](http://www.avg.com/filedir/inst/avg85flx-r287-a2632.i386.deb) from [here]("http://free.avg.com/download?prd=afl"). 
Once the download has completed, double-click on the downloaded file, and then click on the "Install" button.

From the command line (Applications->Accessories->Terminal) enter the following command:
```
sudo avgupdate
```
When you are ready to scan a file or folder you can use the avgscan command, e.g.```
sudo avgscan <file-name>
```

There are other options available, discoverable through the "man" pages for the two commands I've mentioned.

---

### Post by Sir Jasper on 2009-09-01
Hi,

I use Wine and Avast for Debian - after it has downloaded to your desktop just click on it and it will install automatically. It has a GUI for on demand scans.

It is significantly faster than Clam and performs much better than Clam in independent Windows tests. The only disadvantage is that the daily signature update is full (as opposed to incremental) so the daily download works much faster for those with Broadband.

I also use the Firewall which I configured using Firestarter (that was a 5 minute task after googling for advice - probably also described in the free Pocket Guide).

My regards

You could also try the a-squared Free USB version (just download and unzip to try it on a stick - Wine will recognize it). It works best with Wine-Doors and Internet Explorer. Alternatively, you could use it from your Desktop

---

### Post by 3rdalbum on 2009-09-01
AVG is command-line only. It's mystifying - they make the program for desktop users, but they don't provide a GUI? Madness! That's why it doesn't appear in your Applications menu.

As for the other poster's question, you should really be searching on the forums for an answer - there have been hundreds of threads previously on this. Linux comes with a firewall built-in, called Netfilter (also known as "IPtables"). On Ubuntu, by default, it doesn't block any incoming connections. This is because Ubuntu doesn't ship with anything that listens to incoming connections anyway.

You can get a GUI program to configure the Netfilter/IPtables firewall. Many people suggest Firestarter, but this program is not suitable for ordinary desktop users.* I suggest installing "gufw" - it's very easy to use.

Of course, if your internet router already has a firewall built-in, then you don't need to be running a personal firewall; it just makes more work for you, with no realistic security benefits. And if you use Samba, then having a firewall on the client computer will cause the client to not be able to detect the server unless you manually specify the server's IP address.

*There's not enough visual feedback in Firestarter - it's difficult to tell when it has its grubby hands on your firewall configuration. It has very verbose logging for system administrators, but this logging tends to scare new users who don't know what a firewall does. When new users see that they are occasionally getting incoming connections that have been denied, they go into panic mode and think that they're being attacked. Certain bugs in Firestarter have been around since the early days and not been fixed either, some of which also cause new users to worry.

In short, if you actually need a personal firewall (I don't, I have a firewall in my router and I trust my network traffic), then use gufw.

---

### Post by Sir Jasper on 2009-09-01
Hi,

As I said, I configured the Firewall very easily using Firestarter.

See page 117 (goto 135 as there are 18 preliminary pages) of the free Ubuntu Pocket Guide and Reference book (It is recommended in the sticky section above and was written by Keir Thomas, an acknowledged expert on Ubuntu).

GUFW may be, and probably is, the latest improvement but both it and Firestarter are configuration tools and the means to an end and I merely record that Firestarter did what I wanted.

My regards

---

### Post by 3rdalbum on 2009-09-01
> **Sir Jasper said:**
> GUFW may be, and probably is, the latest improvement but both it and Firestarter are configuration tools and the means to an end and I merely record that Firestarter did what I wanted.

My regards

Sorry, I wasn't actually directing my post at you, I was just drawing on my experiences as a former Firestarter user, and as someone who has to calm down a lot of new users who've seen their logs and think that the Russian Mafia is hacking into their computer. :-)

If Firestarter works for you, then use it, and be happy that you have a choice of firewall frontend. I for one am very happy that I can have no configured firewall and not get constant notifications that I'm "putting [my] system at risk", Windows-style :-D

---

### Post by Sir Jasper on 2009-09-01
Hi 3rdalbum,

Thanks for your reply. I used Firestarter just once to set things up. I haven´t looked at it since and I have never seen any message of the type you mention.

My regards

---

