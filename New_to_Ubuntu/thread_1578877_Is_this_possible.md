---
title: "Is this possible ?"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by Veren on 2010-09-21
Hello, I've just been wondering about this...I know there are not many linux virii and that is the main reason I'm using it as my working platform. I dualboot it with Windows, which I use for games only. I´m using a proper internet security suite on Win, but none on Ubuntu (is there any ?) I was wondering if it is possible to get a virus while using Ubuntu (I NEVER even browse web on Windows), that would take effect on Windows, since I can't scan the /user Ubuntu uses from Windows. Thanks.

---

### Post by jtarin on 2010-09-21
Not to worry on Ubuntu,but if you share files with Windows the possibility exist to transfer a virus to Windows.I would have a folder in Windows to isolate or better a seperate partition, to always transfer files to and scan it on first boot of Windows after a transfer that is suspect.

---

### Post by 3rdalbum on 2010-09-21
Do not run untrusted executables on any OS. The virus won't "automatically activate" as soon as Windows starts, so just make sure you don't run one.

And Ubuntu won't run the virus code either.

---

### Post by Ahava591 on 2010-09-21
I will leave it to others to determine whether or not malware could harm another partition on the same HDD.

However, I recommend using anti-malware for your Ubuntu partition if you will be transferring absolutely anything to Windows. The last time I checked, most of the scanners for Linux will only find malware, (and the same weaknesses for Windows anti-malware software apply, see: zero-day exploit, etc.) and will not remove it.

If you are not playing online video games, I recommend you simply disconnect from your network while you use Windows.
-Anybody who thinks this is paranoid or ineffectual, please let me know either here or in a PM, I'd like to have this explained to me more.

Good luck.

---

### Post by zealibib slaughter on 2010-09-21
Although very unlikely that you could get a virus on any linux build it is possible.  There are viruses for unix so there are viruses for linux.  The main reason linux is safe is file permissions and restriction of the root account.  Ubuntu comes with a firewall built in and there are gui's for it or you can use the command line to manipulate it. Code "man ufw" for commands to work with the firewall.  There are a few anti-virus programs for linux the most popular is clam-av which you can get from synaptic.  Avira also has a linux version of their home free edition and I've always recommended the Windows version for family and friends because it is as good or better than any paid AV software on the market. But like I said before it is very unlikely to get a virus on a linux box since you would usually have to give it permission to write/modify the file system as root for it to do any harm. The main concern a linux user should have is the possibility of passing on a virus to a windows machine by accident since its possible to have a virus which cant affect your system but still be there.

---

### Post by Veren on 2010-09-21
Thanks

---

### Post by mastablasta on 2010-09-21
> **zealibib slaughter said:**
> Avira also has a linux version of their home free edition and I've always recommended the Windows version for family and friends because it is as good or better than any paid AV software on the market. 
 
this is not entirely true. It is actually a medium quality AV software (anumber of test online will confirm this), however considering it's free and together with a reasonable firewall (maybe comodo or zone alarm) it really is a good protection.
 
Anyway viruses are so 90's. Today people have to be more afraid of social engineering, worms, trojans and such malware which are mostly stopped by firewall. but even that won't help if user runs them and then gives them permission to access the net...

---

### Post by lisati on 2010-09-21
AV products are only a tool. Your best defense against [malware]("http://lisati.homelinux.com/wiki/index.php/Malware") begins with being smart with what you allow onto your computer. 
> **mastablasta said:**
> 
Anyway viruses are so 90's. Today people have to be more afraid of social engineering, worms, trojans and such malware which are mostly stopped by firewall. but even that won't help if user runs them and then gives them permission to access the net...

.... almost. A [trojan]("http://en.wikipedia.org/wiki/Trojan_horse_%28computing%29"), named after a famous [Trojan Horse]("http://en.wikipedia.org/wiki/Trojan_Horse"), is software that masquerades as something useful. It doesn't need to do stuff through a network connection to do its mischief.

---

### Post by 3rdalbum on 2010-09-21
You don't need a firewall unless you run server software on your computer and you don't already have a NAT router.

---

