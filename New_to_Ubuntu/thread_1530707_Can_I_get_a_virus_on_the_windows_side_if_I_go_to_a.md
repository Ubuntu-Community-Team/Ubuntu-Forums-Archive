---
title: "Can I get a virus on the windows side if I go to an infected website in ubuntu?"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by organikeith on 2010-07-14
Just curious as all of my computers these days are dual boot linux and windows.  
I have one where ubuntu is installed inside windows via wubi and am concerned about malware 'seeing' windows files on my system (while I am logged into ubuntu) and installing themselves. 

Thanks for the help in advance.
-K

---

### Post by lisati on 2010-07-14
IMO, it's unlikely that a virus would find its way from Ubuntu to your Windows partition(s), unless you specifically move it there, or you are running something like Wine and have allowed it access to your file system.

---

### Post by xsinsx on 2010-07-14
This post is where i found the answer to your question. 

[http://ubuntuforums.org/showthread.php?t=561013](http://ubuntuforums.org/showthread.php?t=561013) 

> 
To answer you question more precisely:
NO, Windows cannot get infected when you are running Linux because Windows is on a separate partition than Linux. To get infected, you would have to manually move or copy a malicious file onto your Windows partition and then execute (run) the program.

The only places these files could exist on the Linux partition are the browser cache or a downloads directory. And most all Windows malware gets installed via ActiveX controls (which don't run in Linux browsers). Windows rootkits can't install on Linux, so no need to be concerned with them.

Also, even if you somehow end up w/ malicious files on your Windows partition, they can do absolutely no harm until YOU execute the file. (execute also implies opening email attachments)

Malware & viruses on Windows MUST be executed else they can do no harm, they typically excute at boot via a registry key or other "sister" program set to execute at boot.

You can test this & prove it out to be true. You can run Linux (or even Windows itself) and download any virus or malware and save it to disk. It can do nothing until YOU manually execute the file.

I have not used automatic (autoprotect) antivirus on Windows for 7 years. If I have any doubt about a file I manually scan it.



---

### Post by bodhi.zazen on 2010-07-14
> **organikeith said:**
> Just curious as all of my computers these days are dual boot linux and windows.  
I have one where ubuntu is installed inside windows via wubi and am concerned about malware 'seeing' windows files on my system (while I am logged into ubuntu) and installing themselves. 

Thanks for the help in advance.
-K

In theory it is possible. As long as your computer is turned on and connected to the internet many bad things are possible.

In practice there are no known active viruses for Linux of any significance at this time and the kind of behaviour you are asking about has, to my knowledge, never been described for any Linux virus. You can run some limited Windows viruses with wine, and only then the damage is limited to your home directory unless you are running wine as root.

I suggest you read the Security Sticky - [Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by techunit on 2010-07-14
Yes you can but it is very unlikely... the major problems with viruses moving from a linux partition to a windows partition is that unless Windows has a way to access the files containing the virus it can't activate in linux in most likely hood.

---

### Post by M1ke on 2010-07-14
I notice the OP mentioned this particular Ubuntu installation is a wubi setup, not dual boot. Does the advice regarding infections not moving across separate partitions still apply in that case? I was under the impression wubi installs were different by virtue of being "within" Windows rather than fully installed in a separate partition.

---

### Post by ST3ALTHPSYCH0 on 2010-07-14
Wubi still has its own patition... it just happens to be virtual, much like a VM's harddrive. In order to access it via Windows you would have to have EXT drivers and map it as a network share... And I'm not sure that possbile with WUBI, but I know it is via VM.

---

### Post by tzarskielit on 2010-07-14
Actually xsinsx gave the most precise explanation via the quote.
The quote misses only one thing, if you are careless enough to download a windows virus in linux,
you have to

0. Actually, you won't be able to download it, since, as pointed, the virus starts itself in the ActiveX controls, which are for most of the PCs automatically run by the browsers. It has to be in an e-mail attachment for easier download.
1. Move it manually to a windows partition
2. Reboot and boot into Microsoft Windows and then
3. Manually run the virus

In order to function.

PS. You can try it out on any XXX site :D

---

### Post by bodhi.zazen on 2010-07-14
> **tzarskielit said:**
> Actually xsinsx gave the most precise explanation via the quote.
The quote misses only one thing, if you are careless enough to download a windows virus in linux,
you have to

0. Actually, you won't be able to download it, since, as pointed, the virus starts itself in the ActiveX controls, which are for most of the PCs automatically run by the browsers. It has to be in an e-mail attachment for easier download.
1. Move it manually to a windows partition
2. Reboot and boot into Microsoft Windows and then
3. Manually run the virus

In order to function.

PS. You can try it out on any XXX site :D

What you say is true of known viruses, however, the OP is posting a theoretical question.

1. Wubi is dual booting with a loop mounted file system. The file is stored on a NTFS partition and the windows root system is mounted by default.

See : [http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

[http://wubi-installer.org/faq.php#internals](http://wubi-installer.org/faq.php#internals)

2. As I indicated in my previous post, some windows viruses can run in wine.

So, in theory, one could pass a virus from Ubuntu -> Windows. See my previous post.

---

### Post by organikeith on 2010-07-15
Thanks for the information! 
Glad to know there is such a great knowledge base here..Hopefully this can help others too... 
I don't plan on using wine much in Ubuntu (unless I am going to pour myself a nice glass of petite sirah to drink while computing).. so good to know that i would have to go out of my way to get my windows side infected. Recently dealt with a rootkit on a windows machine which has made me a bigger ubuntu/linux fan.

Cheers!

---

