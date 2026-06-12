---
title: "ClamAV:  Update of Antivirus Engine"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by tb75252 on 2011-02-10
I am using Ubuntu 10.10 (32-bit) with the GNOME desktop.

My ClamTk GUI indicates that it is time to update the antivirus engine of ClamAV.  (Right now, I have v. 0.96.5)  How do I do that?

Note:  Many people hold the belief that it is not necessary to run an antivirus application in the Linux environment.  I am fully aware of that line of thought.  **Nevertheless, to be on the safe side, I still prefer running an antivirus and I have chosen ClamAV for it!**

---

### Post by Legeril on 2011-02-10
If you check the preferences there should be a checked box saying GUI and engine update automatically, mine are checked but I still have the the same versions you will. As long as your virus definitions are up to date you are set, I have only ever found a virus on things my friends have given me never on my own machine

---

### Post by tb75252 on 2011-02-11
> **Legeril said:**
> If you check the preferences there should be a checked box saying GUI and engine update automatically, mine are checked but I still have the the same versions you will. As long as your virus definitions are up to date you are set, I have only ever found a virus on things my friends have given me never on my own machine

Yes, I have all that checked but I figure that if ClamTk is warning me about having an outdated antivirus engine there must be a reason and, more importantly, there must be a way to remedy that...

---

### Post by M4rotku on 2011-02-11
It seems as though ClamAV comes out with updates to the engine rather frequently; I have yet to use it and not have it tell me that a newer version was out.  Ubuntu can't keep updating it's repository every time a new one comes out, so they opt to just update it per every few releases, or something like that.  As stated above, as long as your virus definitions are up to date, it should work fine.  I don't know how to do this via the gui, but if you run "freshclam" in your terminal, then it should update to the newest definitions.

---

### Post by sydbat on 2011-02-11
Clam (or any other "Linux anti-virus") only looks for Windows malware. Unless you are running a mail server for Windows machines, or you feel that the people that run Windows boxes need you to protect them from Windows malware, you are only wasting your resources by running any "anti-virus" software.

However, if you insist on running Clam, then you have to update via the terminal (Applications > Accessories > Terminal). ```
sudo freshclam

```More info [here]("https://help.ubuntu.com/community/ClamAV#Update%20Virus%20Definitions").

---

### Post by lisati on 2011-02-11
I'm not using the latest version of ClamAV on my server, and I'm not particularly worried. When I run freshclam, it points me here: [http://www.clamav.net/lang/en/support/faq/](http://www.clamav.net/lang/en/support/faq/)

---

### Post by tb75252 on 2011-02-11
> **sydbat said:**
> Clam (or any other "Linux anti-virus") only looks for Windows malware. Unless you are running a mail server for Windows machines, or you feel that the people that run Windows boxes need you to protect them from Windows malware, you are only wasting your resources by running any "anti-virus" software.
 
However, if you insist on running Clam, then you have to update via the terminal (Applications > Accessories > Terminal). ```
sudo freshclam

```More info [here]("https://help.ubuntu.com/community/ClamAV#Update%20Virus%20Definitions").
 
I am not at my computer, so I cannot test your suggestion to run "sudo freshclam" and really see what happens.  Nevertheless, based on the link you gave in your reply, it would appear that "sudo freshclam" updates the virus _definitions_ file. What I was saying in my original post is that ClamTk is reporting that my ClamAV antivirus _engine_ file is outdated.  I could of course be wrong (I am a newbie!), but the two terms do not appear to be synomyms to me...  We'll see what happens this evening when I run "sudo fleshclam", though.
 
Yes, I concede that I am most likely wasting my time by running ClamAV or any other Linux antivirus software.  But I just want to be on the safe side!  One never knows...

---

### Post by sydbat on 2011-02-11
> **tb75252 said:**
> Yes, I concede that I am most likely wasting my time by running ClamAV or any other Linux antivirus software.  But I just want to be on the safe side!  One never knows...[This]("http://ubuntuforums.org/showthread.php?t=510812") will help you far more.

---

### Post by tb75252 on 2011-02-12
> **tb75252 said:**
> I am not at my computer, so I cannot test your suggestion to run "sudo freshclam" and really see what happens.  Nevertheless, based on the link you gave in your reply, it would appear that "sudo freshclam" updates the virus _definitions_ file. What I was saying in my original post is that ClamTk is reporting that my ClamAV antivirus _engine_ file is outdated.  I could of course be wrong (I am a newbie!), but the two terms do not appear to be synomyms to me...  We'll see what happens this evening when I run "sudo fleshclam", though.
 
Yes, I concede that I am most likely wasting my time by running ClamAV or any other Linux antivirus software.  But I just want to be on the safe side!  One never knows...

"sudo freshclam" definitely does not update the antivirus engine.

---

### Post by Paqman on 2011-02-12
> **tb75252 said:**
> I still prefer running an antivirus and I have chosen ClamAV for it![/B]

Is there any particular reason you're running ClamAV? There are much better antivirus packages available for Linux. ClamAV is a very poor performer.

---

### Post by tb75252 on 2011-02-12
> **Paqman said:**
> Is there any particular reason you're running ClamAV? There are much better antivirus packages available for Linux. ClamAV is a very poor performer.
 
No particular reason...   I saw an article (Secure Your Ubuntu) on [www.linuxidentity.com/]("http://www.linuxidentity.com/") that recommended ClamAV, and so I ended up using that.
 
In the Microsoft Windows world there are magazines, such as PC Magazine or PC World, that test, rate, and recommend antivirus/antispyware software.  I am having a hard time finding something similar in the Linux world.  [Of course now everyone following this thread is going to remind me again that since there (allegedly) are no viruses for the Linux OS running around, there is no need for such software, etc., etc...]
 
Anyhow, do you have a recommendation for antivirus software?

---

### Post by thefasterblueone on 2011-02-12
If you are interested in security for Ubuntu then look here.

[http://ubuntuforums.org/showthread.php?t=510812]("http://ubuntuforums.org/showthread.php?t=510812")



edit: sorry already been posted.

---

### Post by Paqman on 2011-02-12
> **tb75252 said:**
> No particular reason...   I saw an article (Secure Your Ubuntu) on [www.linuxidentity.com/]("http://www.linuxidentity.com/") that recommended ClamAV, and so I ended up using that.
 
In the Microsoft Windows world there are magazines, such as PC Magazine or PC World, that test, rate, and recommend antivirus/antispyware software.


Interesting point. Why don't you drop a line to one of the Linux magazines like Linux Format and ask them to do an article on effectiveness of Linux AV packages?

For some links detailing the performance of ClamAV, check the references on its [Wikipedia article]("http://en.wikipedia.org/wiki/Clam_AntiVirus#Effectiveness").

> [Of course now everyone following this thread is going to remind me again that since there (allegedly) are no viruses for the Linux OS running around, there is no need for such software, etc., etc...]

They say this because its true. The vast majority of desktop Linux users don't use a third party AV suite, and have no significant problem with malware. The threats that we do face tend to be through things like social enginerring, which an AV package won't protect you from anyway.
 
> 
Anyhow, do you have a recommendation for antivirus software?

AVG and Avast both do a Linux version. I've not used either, but people seem to like them.

---

### Post by kgr132 on 2011-02-27
If someone followed this thread really looking to update the ClamAV package, you need to have software updates via "backport" enabled.

Go to System... Software Sources... Updates (tab)... then check the box for 'Unsupported Updates (<your version>-backports)'. After that, run the update manager and it will find the ClamAV update.

As always, Good Luck and Don't Panic.

---

### Post by tb75252 on 2011-02-28
> **kgr132 said:**
> If someone followed this thread really looking to update the ClamAV package, you need to have software updates via "backport" enabled.

Go to System... Software Sources... Updates (tab)... then check the box for 'Unsupported Updates (<your version>-backports)'. After that, run the update manager and it will find the ClamAV update.

As always, Good Luck and Don't Panic.

Well, It does not work for me...

FYI with my version of Ubuntu (10.10) I have to do the following:  **System -> Administration -> Update Manager -> Settings -> Updates** tab and put a check mark for **Unsupported Updates (maverick-backports)**.

But unfortunately no update for ClamAV shows up!

---

### Post by Frogs Hair on 2011-02-28
Two alternatives to Clam . I have used Avast with Windows , but both are highly rated free programs.

[http://www.avast.com/linux-home-edition](http://www.avast.com/linux-home-edition)

[http://free.avg.com/us-en/download.prd-alf](http://free.avg.com/us-en/download.prd-alf)

---

### Post by stmiller on 2011-02-28
[http://i.imgur.com/IrauJ.png](http://i.imgur.com/IrauJ.png)

^Yep this is normal

Ubuntu and Debian package maintainers maintain a frozen version of clamav (as like other software packages) in a given distro release.

Any security vulnerabilities found in a newer version of clam are patched in and updated. As just happened recently, for instance:

[http://www.ubuntu.com/usn/usn-1076-1](http://www.ubuntu.com/usn/usn-1076-1)

You can safely disregard that clamav warning. :)

And to further PS what has been said: clamav scans for Windows viruses (only). It's rather more used on mail servers to scan email attachments.

---

### Post by tb75252 on 2011-03-01
I went to this link: [http://free.avg.com/us-en/download.prd-alf](http://free.avg.com/us-en/download.prd-alf) and downloaded AVG (the .deb file).

I doubleclicked on the file and  clicked on the **Install** button. The program should reside in **Applications -> Accessories**, but I cannot locate it there --or anywhere else!

Ubuntu Software Center cannot locate the program.  (I did a search for "avg" under **Installed Software**)

I doubleclicked on the .deb file again, hit the **Reinstall** button.  The software was reinstalled but I still cannot locate the program anywhere under the **Applications** menu.

So... what am I doing wrong?  How do I correctly install AVG?

---

### Post by tb75252 on 2011-03-01
> **tb75252 said:**
> I went to this link: [http://free.avg.com/us-en/download.prd-alf](http://free.avg.com/us-en/download.prd-alf) and downloaded AVG (the .deb file).

I doubleclicked on the file and  clicked on the **Install** button. The program should reside in **Applications -> Accessories**, but I cannot locate it there --or anywhere else!

Ubuntu Software Center cannot locate the program.  (I did a search for "avg" under **Installed Software**)

I doubleclicked on the .deb file again, hit the **Reinstall** button.  The software was reinstalled but I still cannot locate the program anywhere under the **Applications** menu.

So... what am I doing wrong?  How do I correctly install AVG?

Cancel this!  I just discovered that AVG Free 8.5 for Linux has no official GUI.  The program is fully managed through the command line...

I am marking this thread as solved.

---

