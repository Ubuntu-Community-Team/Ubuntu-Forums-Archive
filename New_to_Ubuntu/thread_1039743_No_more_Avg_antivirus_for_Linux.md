---
title: "No more Avg antivirus for Linux?"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by lance bermudez on 2009-01-14
I was told that avg antivirus 7.5 Basic antivirus protection for Linux/FreeBSD support for commercial AVG 7.5 products will be
discontinued at the end of April 2009. Does anyboby know if their will be a new verson of avg? Does any body know of any other antivirus programs that will work on windows and linux? I use mine to keep both my linux and windows working clean. I need a gui for my antivirus.

---

### Post by 2hot6ft2 on 2009-01-14
avast from avast.com has both linux and windows versions.
For the linux version and other ideas check the link below.
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

And while I don't know of a windows version of clamav it can scan windows from linux which is nice that way the bugs have nowhere to run and clamav is already installed in ubuntu. If you want a gui for it use ```
sudo apt-get install clamtk
``` in a terminal and then it will be in
Applications>System Tools>Virus Scanner

---

### Post by handydan918 on 2009-01-14
> **lance bermudez said:**
>  Does any body know of any other antivirus programs that will work on windows and linux? I use mine to keep both my linux and windows working clean. I need a gui for my antivirus.

Just use it on your windows install. Linux doesn't need it. If you ever find a viable, working. malicious Linux virus, send it to me. I'd love to see one, just once. 

In ten years, I never have.

---

### Post by coolbrook on 2009-01-14
If you really feel it's necessary then consider [Avira Antivir](http://free-av.com/en/download/download_servers.php).  I use it on my Windows machine.

---

### Post by NewJack on 2009-01-14
> **handydan918 said:**
> Just use it on your windows install. Linux doesn't need it. If you ever find a viable, working. malicious Linux virus, send it to me. I'd love to see one, just once. 

In ten years, I never have.

Although there are no Linux viruses in the wild at this point in time, if you tend to share files with Windows users (or even if you use Windows on another partition) I would install an A/V just to check files before passing them along.  

I know some people don't feel the same way.  Some feel, well if it's not a Linux virus it's not my responsibility to check the files.  I just think it's neighborly (sp?) or proactive (especially if you use the same files on your own Win partition).

Just my .02 bits

---

### Post by crjackson on 2009-01-14
> **coolbrook said:**
> If you really feel it's necessary then consider [Avira Antivir](http://free-av.com/en/download/download_servers.php).  I use it on my Windows machine.

Just curious. Is this a GUI package?

Can it remove infected (windows) files from an NTFS partition and somehow clean the virus from a windows installation from Linux?

Other packages basically do nothing more than scan and report, I would like to see a package that could be used under linux to disinfect a windows system.

---

### Post by crjackson on 2009-01-14
> **NewJack said:**
> Although there are no Linux viruses in the wild at this point in time, if you tend to share files with Windows users (or even if you use Windows on another partition) I would install an A/V just to check files before passing them along.  

I know some people don't feel the same way.  Some feel, well if it's not a Linux virus it's not my responsibility to check the files.  I just think it's neighborly (sp?) or proactive (especially if you use the same files on your own Win partition).

Just my .02 bits


+1, Sopt On! Old Chap.

---

### Post by spcwingo on 2009-01-14
> **2hot6ft2 said:**
> avast from avast.com has both linux and windows versions.
For the linux version and other ideas check the link below.
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

+1 for avast.  My only remaining Windows box uses it and has never had virus problems.

> **2hot6ft2 said:**
> I don't know of a windows version of clamav

There is a Windows version of clamav.  It's called clamwin, but it doesn't offer real-time scanning like Avast does.

---

### Post by lance bermudez on 2009-01-17
thank you for all your help. does anyone know of a sypware or adware remover that will work on linux to check my windows box? I know that i dont need if for linux i just want it to work from linux so that i can check my windows.

---

### Post by seagullplayer77 on 2009-01-17
> **handydan918 said:**
> Just use it on your windows install. Linux doesn't need it. If you ever find a viable, working. malicious Linux virus, send it to me. I'd love to see one, just once. 

In ten years, I never have.

I would agree. Viruses aren't something you need to worry about when using Linux. I wouldn't bother installing an anti-virus---it'd just be an unnecessary use of resources.

---

### Post by Hendrixski on 2009-01-17
> **lance bermudez said:**
> thank you for all your help. does anyone know of a sypware or adware remover that will work on linux to check my windows box? I know that i dont need if for linux i just want it to work from linux so that i can check my windows.

Best anti-virus that I know of is the "format entire drive" option in the Ubuntu installer.
:guitar:

---

### Post by oldsoundguy on 2009-01-17
F-Prot has had and will continue to have a free version of their excellent Anti-Virus program that can run under a Linux build to protect your WINDOWS partition or VM or whatever.  I used the paid version for years before I took my Windows machines off line.

IF you have a stand alone Windows machine and still need an AV ... AVG still offers a free version!  (just disable the link scanner as it really will slow your browser down!)
[http://free.avg.com/](http://free.avg.com/)
(this is what is now on my Windows computers.)
Be sure and update the MOMENT your install completes!

---

### Post by llamabr on 2009-04-26
[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)

[http://www.cyberciti.biz/tips/debunking-the-linux-is-virus-free-myth.html](http://www.cyberciti.biz/tips/debunking-the-linux-is-virus-free-myth.html)

---

### Post by presence1960 on 2009-04-26
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by steve101101 on 2009-04-26
+1 another great benefit of linux. :KS

---

### Post by Didius Falco on 2009-04-26
I'd dump AVG on Windows and go with either Avast or Avira. AVG used to be pretty good, but it's turned into yet another piece of Bloatware.

The only reason you'd need an antivirus  app on linux would be if you email attachments to people using using Windows, to protect them.

---

### Post by steve101101 on 2009-04-26
> **Hendrixski said:**
> Best anti-virus that I know of is the "format entire drive" option in the Ubuntu installer.
:guitar:

+1. thats what you have to do in windows when uneducated users download everything.

---

### Post by m_2009 on 2009-04-26
AVG released version 8.5 for linux on 23rd April. You can get it at the following link:

[http://free.avg.com/download?prd=afl](http://free.avg.com/download?prd=afl)

This is the free version.

---

