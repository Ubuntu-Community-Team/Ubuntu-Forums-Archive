---
title: "Firefox not Updating"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by Little Pony on 2011-08-14
I am still running firefox 3.6.18.  It is never included in the updates.  Thunderbird updates, but firefox won't.

My brother looked it up in the ubuntu software center on my computer and in synaptic and both say only 3.6.18 is available.

What should I do to update it?

---

### Post by philinux on 2011-08-14
Hi and welcome.

What version of ubuntu are you running.

---

### Post by raja.genupula on 2011-08-14
```
sudo add-apt-repository ppa:mozillateam/firefox-next
sudo apt-get update
sudo apt-get install firefox
```

---

### Post by SoFl W on 2011-08-14
Firefox 3.x.x is no longer supported or suppose to receive updates.

You need to upgrade to Firefox 5.


**EDIT:**
Please add the FireFox** stable** releases to your software center:
```
sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install firefox
```See this thread: [http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247)

---

### Post by SoFl W on 2011-08-14
> **raja.genupula said:**
> sudo add-apt-repository ppa:mozillateam/firefox**-next**
sudo apt-get update
sudo apt-get install firefox

This is for beta versions, NOT stable versions.  It is more for experienced users.

---

### Post by lovinglinux on 2011-08-15
> **SoFl W said:**
> Firefox 3.x.x is no longer supported or suppose to receive updates.

You need to upgrade to Firefox 5.

Although I recommend the upgrade, Firefox 3.6.x is still supported and receives updates.

---

### Post by SoFl W on 2011-08-15
YOU SIR are correct, I misunderstood what I read on the original link.  The wording made me think that the 3.xx series would no longer receive updates as of August.  I see a [3.6.20 ]("https://wiki.mozilla.org/Releases/Firefox_3.6.20")is schedualed for release on August 16.

I updated to FF5 because I thought 3.xx was finished being supported.

---

### Post by lovinglinux on 2011-08-15
> **SoFl W said:**
> YOU SIR are correct, I misunderstood what I read on the original link.  The wording made me think that the 3.xx series would no longer receive updates as of August.  I see a [3.6.20 ]("https://wiki.mozilla.org/Releases/Firefox_3.6.20")is schedualed for release on August 16.

I updated to FF5 because I thought 3.xx was finished being supported.

Mozilla hasn't decided yet when they will stop providing support for 3.6.x. Only version 3.6.19 was initially planned, but they are extending the support for a little while, probably because of corporate users.

Nevertheless, they are encouraging the upgrade to Firefox 5. 

BTW, Firefox 6 will be released tomorrow, which essentially retires Firefox 5.

---

### Post by Wim Sturkenboom on 2011-08-15
> **Little Pony said:**
> I am still running firefox 3.6.18.  It is never included in the updates. Thunderbird updates, but firefox won't.

My brother looked it up in the ubuntu software center on my computer and in synaptic and both say only 3.6.18 is available.

Ubuntu will provide security updates; not necessarily upgrades to newer versions.

Having said that, the below is stated for the firefox entry in synaptic in 10.04.
> 
Canonical provides critical updates for firefox till april 2013
So if firefox ceases to exist tomorrow, Canonical will still provide the security updates ;)

---

### Post by lovinglinux on 2011-08-15
> **Wim Sturkenboom said:**
> Ubuntu will provide security updates; not necessarily upgrades to newer versions.

Having said that, the below is stated for the firefox entry in synaptic in 10.04.
So if firefox ceases to exist tomorrow, Canonical will still provide the security updates ;)

Canonical doesn't patch Firefox on their own, so when Firefox 3.6.x becomes unsupported by Mozilla, they will upgrade to Firefox 6.

---

### Post by ofnuts on 2011-08-15
> **Little Pony said:**
> I am still running firefox 3.6.18.  It is never included in the updates.  Thunderbird updates, but firefox won't.

My brother looked it up in the ubuntu software center on my computer and in synaptic and both say only 3.6.18 is available.

What should I do to update it?
Unless I am mistaken, the general philosophy of Ubuntu is that in a given Ubuntu release, the software is never upgraded, only maintained. If you want a newer version of your software, either you install it independently, or you switch to a more recent version of Ubuntu.

---

### Post by lovinglinux on 2011-08-15
> **ofnuts said:**
> Unless I am mistaken, the general philosophy of Ubuntu is that in a given Ubuntu release, the software is never upgraded, only maintained. If you want a newer version of your software, either you install it independently, or you switch to a more recent version of Ubuntu.

Yes, that's true. But there are special circumstances related to Firefox development. See [Firefox 4, 5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247").

---

### Post by Wim Sturkenboom on 2011-08-16
> **lovinglinux said:**
> Canonical doesn't patch Firefox on their own, so when Firefox 3.6.x becomes unsupported by Mozilla, they will upgrade to Firefox 6.I stated 'if firefox ceases to exist', not 'if firefox no longer supports version whatever' ;)

Yep I know, they will remove firefox from the repo and replace it with something else.

---

### Post by lovinglinux on 2011-08-16
> **Wim Sturkenboom said:**
> I stated 'if firefox ceases to exist', not 'if firefox no longer supports version whatever' ;)

Yep I know, they will remove firefox from the repo and replace it with something else.

Well, I presume if Mozilla ceases to exists, there will be plenty of Firefox forks to replace it, but I doubt Canonical and Ubuntu developers would continue to provide patches on their own.

---

### Post by Kellemora on 2011-08-16
I keep a perfectly WORKING copy of FireFox in my archives, namely version 3.6.3 as all versions after that have a serious memory leak when used with any Flash player release.

As an aside: The current new release of Flash has a serious BUG in it too.

I downloaded the previous version from the Adobe web site, but installing it so it works on all the different browsers I use is beyond my skills.  With over 6 million complaints hitting their desk on the day of the upgrade release, perhaps they might think about fixing it, but don't hold your breath, it's been a week already and they have not rolled back to the known working version and they have not released a bug fix for the current version.  NOT the way to win friends and influence users, that's for sure!

TTUL
Gary

---

### Post by Little Pony on 2011-08-16
Post deleted by Little Pony

---

### Post by Little Pony on 2011-08-16
> **ofnuts said:**
> Unless I am mistaken, the general philosophy of Ubuntu is that in a given Ubuntu release, the software is never upgraded, only maintained. If you want a newer version of your software, either you install it independently, or you switch to a more recent version of Ubuntu.

> posted by Wim Sturkemboom  Ubuntu will provide security updates; not necessarily upgrades to newer versions.That explains it.  I guess when I thought Thunderbird was updating it was only installing security updates.

Thanks everyone for the help.

---

### Post by flyfishingphil on 2011-08-16
Just did a clean install of 11.04 and it comes with Firefox 5. Don't upgrade to that if you don't have to. Lots of sites that don't work right in the Firefox 5. Looking at going back to 3.6.3 and see if that works better in 11.04.

If anybody has suggestions on doing that I'll gladly listen.

---

### Post by lovinglinux on 2011-08-16
> **flyfishingphil said:**
> Just did a clean install of 11.04 and it comes with Firefox 5. Don't upgrade to that if you don't have to. Lots of sites that don't work right in the Firefox 5. Looking at going back to 3.6.3 and see if that works better in 11.04.

If anybody has suggestions on doing that I'll gladly listen.

Please provide links so we can look at those sites. I haven't found any site that doesn't work with FF 5.

BTW, Firefox 6 was released yesterday and should be in the repositories soon.

---

### Post by flyfishingphil on 2011-08-17
Hey lovinglinux, hadn't heard from you for a while. I did a little checking on other threads, using "Pogo", and figured out what it was.

One that I had read. following the installation, said all of the java needs were covered with what came with 11.04. It was wrong apparently. The thread I found gave info on doing the Sun Java-6 install. Followed those directions, installed, and now no problems with any of the ones I had trouble with. Guess the java replacement, in 11.04, doesn't quite hit the full coverage needed.

The only problem I'm seeing now is with Google Earth. The global side is crystal clear, even views closer than before, but the print side is really poor. Looks like something we saw on what we worked on in the Army 40 years ago. Not easily read with older appearing, blocky letters and poorly shown. Still looking in the setting to see if there is a way to change that, but haven't found any yet.

---

### Post by P38Lightning on 2011-08-17
> **SoFl W said:**
> 


**EDIT:**
Please add the FireFox** stable** releases to your software center:
```
sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install firefox
```See this thread: [http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247)

Hi,

I ran that command and it changed nothing in the software center.  What did I do wrong?
BTW, Little Pony is my sister.
I went ahead and downloaded Firefox from Mozilla's site as a zip file, how do I replace her existing Firefox with that one?

Thanks.

---

### Post by lovinglinux on 2011-08-17
> **P38Lightning said:**
> Hi,

I ran that command and it changed nothing in the software center.  What did I do wrong?
BTW, Little Pony is my sister.
I went ahead and downloaded Firefox from Mozilla's site as a zip file, how do I replace her existing Firefox with that one?

Thanks.


Please post the contents of *firefox-report.txt* file generated in your desktop after running the commands below:

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

If you want to install Firefox downloaded from Mozilla, see [http://www.webgapps.org/tutorials/firefox/general/installing-other-versions](http://www.webgapps.org/tutorials/firefox/general/installing-other-versions)

---

