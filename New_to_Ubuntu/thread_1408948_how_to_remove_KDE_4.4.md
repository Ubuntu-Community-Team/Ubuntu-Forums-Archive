---
title: "how to remove KDE 4.4 ?"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by MBG1987 on 2010-02-17
i just installed KDE 4.4 on my ubuntu 9.10 system using this guide [http://news.softpedia.com/news/How-to-Install-KDE-SC-4-4-on-Ubuntu-9-10-134546.shtml](http://news.softpedia.com/news/How-to-Install-KDE-SC-4-4-on-Ubuntu-9-10-134546.shtml)

the new environment does not like to me very much,i love GNOME and i will use it alone,
so how to remove KDE with all the the packages and settings??
 thanks

---

### Post by ankspo71 on 2010-02-17
Hi,
If you use the command in this article, it will remove all kde apps from your system and leave you with gnome. It also reinstalls ubuntu-desktop to make sure nothing is missing.
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
PS. You probably won't need the kubuntu/kde repository anymore.
Hope this helps.

---

### Post by lovinglinux on 2010-02-17
I see a potential problem on that tutorial. It suggests to enable the karmic-backports repository (see image below), in addition to adding **ppa:kubuntu-ppa/backports**. I don't think that is necessary, since the ppa repository itself will take care of updating kde to 4.4. Additionally this will provide backports to all Ubuntu packages (if available) not only the kde packages.

I could be wrong, but if you followed every step of that tutorial, you might have to take additional steps to revert the changes.

[IMG]http://news.softpedia.com/images/extra/LINUX/small/kde44ubuntu910-small_003.png[/IMG]

---

