---
title: "Help. Wanna reinstall Ubuntu with all my softwares and folders intact.."
date: 2011-09-01
forum: New to Ubuntu
---

### Post by ahivarn on 2011-09-01
Hi friends

I am a regular user of Linux. I have installed Ubuntu but with time it has got some problems and shuts down abruptly.. I have been suggested to reinstall it. Is there any way to reinstall it without losing data and softwares installed.? Ubuntu is my only OS.

Thanks in advance..:P

---

### Post by sanderd17 on 2011-09-01
your data is in your /home directory, so back that up to another partition (preferably on another hard drive), and export your installed applications with synaptic.

That way, you can reinstall your applications without problems.

---

### Post by donkyhotay on 2011-09-01
Best option I can think of would be to back up your /home folder then install cleanly. You'd need to reinstall your software of course but if it's mostly from the repos thats usually not that difficult.

---

### Post by pius shililifa on 2011-09-01
have had the same question as well, would love to create a bootable image so that if something goes wrong with my machine i can easily restore it from the backup.Any way of doing this?

---

### Post by sanderd17 on 2011-09-02
> **pius shililifa said:**
> have had the same question as well, would love to create a bootable image so that if something goes wrong with my machine i can easily restore it from the backup.Any way of doing this?

You can do this with remastersys I suppose. But clonezilla is more appropriate to make backups of your disk.

---

### Post by tommpogg on 2011-09-02
> **sanderd17 said:**
>  export your installed applications with synaptic.

How can I export my installed applications?

Thanks

---

### Post by kyletstrand on 2011-09-02
Just curious. Have you been able to pinpoint what causes the abrupt shut downs?

---

### Post by sanderd17 on 2011-09-02
> **tommpogg said:**
> How can I export my installed applications?

Thanks

I have read it could, but I can't find how to do it.

Anyway, you can use the mint backup tool too: [http://community.linuxmint.com/tutorial/view/2](http://community.linuxmint.com/tutorial/view/2) (read part D1)

---

### Post by jocko on 2011-09-02
> **tommpogg said:**
> How can I export my installed applications?

Thanks

In synaptic: File-->"Save Markings as".
It saves a list of all the installed packages. Make sure you save this file somewhere that will not be lost during reinstall.
Then after reinstall, just open up synaptic and: File-->"Read Markings" and browse to where you saved the file.

It's a good idea to have a separate /home partition. That way you can keep all your files and user-specific settings even if you format the system partition. [See this page]("http://www.psychocats.net/ubuntu/separatehome") or [this page]("https://help.ubuntu.com/community/Partitioning/Home/Moving") for more on separate home partitions.

---

