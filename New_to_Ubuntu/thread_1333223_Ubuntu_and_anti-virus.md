---
title: "Ubuntu and anti-virus"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by loco5 on 2009-11-21
I am a new, but happy, convert from that other OS and afraid have all the bad habits you may expect! I am confused about virus protection and Ubuntu - is is necessary  and if so what software is recommended. I have read that anti-virus protection is not necessary using Linux OS, you see my problem from previous conditioning! Having loaded Ubuntu so easily onto my netbook I can not understand why I did not use it years ago. Still never too late to learn.

---

### Post by frenchn00b on 2009-11-21
follow these steps:

> apt-cache search clamav  

**apt-get install clamav**



add this to /etc/crontab 
 
> **10 1    * * 1-5 root    cd /root ; mkdir -p /home/clamav/virus ; clamscan -ri /home/ -l /root/virus.txt --move=/home/clamav/virus/ ; cp /root/virus.txt /home/clamav/**


it will in the night check and remove the virused-files
and you wont think never about trojan or viruses in your life ever.

Thank you Frenchn00b !:D

---

### Post by camaron1 on 2009-11-21
> **loco5 said:**
> I am a new, but happy, convert from that other OS and afraid have all the bad habits you may expect! I am confused about virus protection and Ubuntu - is is necessary  and if so what software is recommended. I have read that anti-virus protection is not necessary using Linux OS, you see my problem from previous conditioning! Having loaded Ubuntu so easily onto my netbook I can not understand why I did not use it years ago. Still never too late to learn.


You don't need one for Ubuntu but you may want to install **clamtk** if you are going to transfer files to a Windows machine (so you scan for Windows virus before you transfer files)

---

### Post by NoaHall on 2009-11-21
You don't need a anti-virus on Ubuntu at all. The ones on Linux only scan for WINDOWS-ONLY viruses anyway. O

---

### Post by OrangeCrate on 2009-11-21
> **loco5 said:**
> I am a new, but happy, convert from that other OS and afraid have all the bad habits you may expect! I am confused about virus protection and Ubuntu - is is necessary  and if so what software is recommended. I have read that anti-virus protection is not necessary using Linux OS, you see my problem from previous conditioning! Having loaded Ubuntu so easily onto my netbook I can not understand why I did not use it years ago. Still never too late to learn.

**The Truth About Linux and Viruses**

[http://www.linuxclues.com/articles/21.htm](http://www.linuxclues.com/articles/21.htm)

Welcome to the forums.

:)

---

### Post by frenchn00b on 2009-11-21
its better to remove the viruses. They are dirty, bringing dirt.
 
If you copy a file for a friend under windows... you dont want to ..

---

### Post by frenchn00b on 2009-11-21
> **OrangeCrate said:**
> **The Truth About Linux and Viruses**

[http://www.linuxclues.com/articles/21.htm](http://www.linuxclues.com/articles/21.htm)

Welcome to the forums.

:)

is f-prot installed into the local? 

```
 # crontab -e

This opens a file in Vi. (For more on the Vi editor, see The Vi Editor.) Just add this line in Vi:

0 4 * * * /usr/**local**/f-prot/tools/check-updates.pl -cron -quiet

Now cron will get the updates at 4:00AM every day, notifying you only if there was an error getting the signature files.

Installing and updating the software is good, but to protect your computer, you need to also perform virus scans on a regular basis. So let's create a cron job for that too.

0 5 * * * /usr/local/bin/f-prot / -report=/root/f-prot-report.txt
```

---

### Post by pbrane on 2009-11-21
I have been using GNU/Linux exclusively on my personal computers for about 11 years. I have never had a virus/trojan or any malware. I have been using F-Prot anti-virus as far back as 1994 when I too was using that other OS. I consider it to be one of the best anti-virus scanners on the planet. There is a Linux version available free for home use. Both 32 and 64 bit. I highly recommend it. My friends (who run that other OS) report that F-Prot doesn't bog down their computers like other anti-virus software and that it catches and disinfects ALL viruses and malware.

---

### Post by pbrane on 2009-11-21
frenchn00b:

the f-prot installer will add the proper crontab entry. you don't need to do it manually. f-prot is installed in my home directory on my laptop but you can install it anywhere you like. Note also that the f-prot binary is now called fpscan, not f-prot.

[http://www.f-prot.com]("http://www.f-prot.com")

---

### Post by OrangeCrate on 2009-11-21
> **frenchn00b said:**
> **is f-prot installed into the local?**

<snip>

The point of the article, is that you don't need an antivirus program in Linux. To answer your question directly, I don't know. The suggestion to use f-prot is just an afterthought added by the author, and may be outdated information, since the article was written a while back.

---

### Post by amygdala_man on 2009-11-21
> **loco5 said:**
> I am a new, but happy, convert from that other OS and afraid have all the bad habits you may expect! I am confused about virus protection and Ubuntu - is is necessary  and if so what software is recommended. I have read that anti-virus protection is not necessary using Linux OS, you see my problem from previous conditioning! Having loaded Ubuntu so easily onto my netbook I can not understand why I did not use it years ago. Still never too late to learn.

I too am a newbie with lots of bad habits, which caused me some headaches before I obtained the book Beginning Ubuntu Linux 4th Ed. by Keir Thomas and Andy Channelle with Jaime Sicam. Apress 2009. This edition has been updated for Ubuntu 9.04 (Jaunty Jackalope) and above.

In chapter 9 and elsewhere, it relates that the number of viruses affecting Linux is less than 1000 and that is since Linux was created and they die off/fail to propagate very quickly due to Linux security. Whereas, it states that the other OS has had/is having 140,000 viruses plus.

It recommends that we remain vigilant and as interaction with the other OS is common, our systems should not act as a carrier of other OS viruses and so it recommends the use of ClamTK and ClamAV, which can be installed through the Synaptic Package Manager. Together they form a graphical virus scanning facility.

---

### Post by loco5 on 2009-11-22
Thanks to all for their valuable advice, it appears all is very good news regarding virus control. You feel a lot more involved when others more knowledgeble and able are out their able and willing to help. However, security surely is an issue say when on the internet exchanging information with a bank? In such a situation you do not want people getting hold of details been passed. How is such a situation made secure using Ubuntu? What about installing firewall and anti-spy systems?

---

### Post by oldos2er on 2009-11-22
You might want to read [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

