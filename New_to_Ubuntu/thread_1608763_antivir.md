---
title: "antivir"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by m+m on 2010-10-29
I have been trying to install Antivir free unix v 3.1.3.4-1. It downloaded to the downloads folder and I extracted into that folder, ending with a folder called  antivir-workstation-pers-3.1.3.4-1.

Avira say it should have been downloaded to the tmp file so I copied the extracted file and placed it in tmp.

Using cd/ tmp/antivir-workstation-pers-3.1.3.4-1. I am told that neither the file or directory exist.

Ubuntu Compiling Software page suggests installing
sudo apt-get install build-essential 
  sudo apt-get install automake
sudo apt-get install checkinstall

This I did, the first was up to date, the other two were not found.

I am using 10.4 and am now perplexed as to the next move. Answers would be gratefully received but please note that I am very new to this system and need advice that is easily understood...........here's hoping

---

### Post by jfreak_ on 2010-10-29
Any specific reason on why you need a antivirus? Linux systems are not affected by viruses.

It is generally advisable to use only the software centre for installing programs. You shouldn't be installing programs manually especially if you are new to linux, otherwise you should need that program desperately.

---

### Post by m+m on 2010-10-29
hi.......thanks for the response. Web views seem to vary on whether or not viruses can be a problem and since I will be using the system for internet banking I thought I should be careful. Antivir has been splendid on windows and is only available as a manual install....m

---

### Post by kaldor on 2010-10-29
There is absolutely no need to use a virus scanner on Linux. If you do internet banking and want to make sure of security, I suggest doing the banking from a LiveCD. That way, even if (very remote chance) malware affects your computer, it'll be gone on reboot. 

Just pop in an Ubuntu CD, reboot, and "try ubuntu" instead of installing it. No information can be saved to the disc, meaning a secure way to bank online.

However, if you must use a Virus scanner, [_**ClamAV**_]("http://www.clamav.net/lang/en/download/packages/packages-linux/") is a good native Linux one.

Edit:

[This link]("http://forums.linuxmint.com/viewtopic.php?f=90&t=31723&start=0") from the LinuxMint forum is great for understanding more about malware on Linux. I suggest you take a read, as it applies to any Linux distro. :)

---

### Post by m+m on 2010-10-29
Many thanks Kaldor............I have tried live cd  but to avoid endless numbers I used casper-cw alongside it. Casper collapsed and I'm to naive to understand why that happened. I also looked at creating automatic persistence with reconstructor which was even more daunting than dealing with antivir. Thanks for the link to Clam AV.

---

### Post by kaldor on 2010-10-29
Not a problem. Post again if you run into trouble :)

---

### Post by kaldor on 2010-10-29
I should add that if you are using Firefox, you can also use some addons that may aid your security online:

-[Adblock Plus]("https://addons.mozilla.org/en-US/firefox/addon/1865/")

-[NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722/")

-[Ghostery]("https://addons.mozilla.org/en-US/firefox/addon/9609/")


Also, here's an article for you:

[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

---

### Post by m+m on 2010-10-30
Hi Kaldor and again thanks for the links. In the linuxmint piece the author states *" there are very few viruses you have to worry about as a Lynux user, and your firewall should protect you from them as long as you don't do anything careless"*.

Does firewall refer to iptales, or a package I should install. If the former I know I can use firestarter to monitor activity.

Like Av this is all in the background unseen and after 20 years of windows it is difficult to take on faith. As a final point does ubuntu monitor and log all internet connections that one can easily view.

Many thanks for the help and hoping this gets to you..........m+m

---

### Post by coffeecat on 2010-10-30
> **m+m said:**
> after 20 years of windows it is difficult to take on faith.

Don't worry - you are not alone.

Here's a useful guide by one of the forum admins on all aspects of security. It should answer many of your questions about the firewall and AV.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Gone fishing on 2010-10-30
looks like a typo

> Using cd/ tmp/antivir-workstation-pers-3.1.3.4-1. I am told that neither the file or directory exist

looks like a typo cd /tmp not cd/ tmp. Linux has an auto complete using the tab button that helps prevent typos. 

On the AV question I use Antivir on my sever to clean Windows profiles of viruses and it seems to do a good job. On a home PC you may not need an AV unless you share lots of files with Windows users and then only to stop you passing viruses from windows to windows rather that to protect your box.

Linux viruses are close to non existent.

---

### Post by m+m on 2010-10-30
thanks gone fishing, the typo is wrong in this thread, not when I tried installing.m+m

---

### Post by Gone fishing on 2010-10-30
When you install you are sudo? Perhaps a permissions problem? Try sudo -i then navigate to the folder?

---

### Post by Soul-Sing on 2010-10-30
The problem with avira is its difficulty making it run/work. you need the dazoku "module" first, compile it, etc.
please try bitdefender for unices, and its module to intregrate  it within nautilus, which is a great bonus. simple and clear install.

---

### Post by HermanAB on 2010-10-30
Howdy,

Forget about viruses.  Relax and enjoy your Linux system.

---

### Post by Gone fishing on 2010-10-30
The Dazuko is needed to get Antivir working with realtime protection I think you would need to very paranoid to feel you need that.

Antivir will install without that as a on demand scanner, which is how I use it on my server just a cron job that scans the Windows shares every day.

---

### Post by Gone fishing on 2010-10-30
If you want an AV that easy to install avast and AVG have Linux versions with deb files to download

[http://www.avast.com/linux-home-edition#tab4](http://www.avast.com/linux-home-edition#tab4)
[http://free.avg.com/us-en/download.prd-alf](http://free.avg.com/us-en/download.prd-alf)

Clam is in the repositories

---

### Post by lisati on 2010-10-30
Unless you're likely to share files with Windows users, I don't think you need to worry too much.

Some of the AV products I've looked at for my Linux machines over the last three years take a little bit of effort to get working, sometimes more effort than is justified by the results. At present, I only have clamav and spamassassin on my email server, which serve me well for alerting me to potential problems.

Good sense, together with being careful with what you allow on your computer, where you browse, and what you open will go a long way to helping you keep safe.

---

